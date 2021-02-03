---
title: Obter uma lista de SKUs para um produto (por país)
description: Você pode obter e filtrar uma coleção de SKUs por país para um produto usando as APIs do Partner Center.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 9d5ec9172ed92d33e6ff291eafd523cbc13bfbbd
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769092"
---
# <a name="get-a-list-of-skus-for-a-product-by-country"></a><span data-ttu-id="2f715-103">Obter uma lista de SKUs para um produto (por país)</span><span class="sxs-lookup"><span data-stu-id="2f715-103">Get a list of SKUs for a product (by country)</span></span>

<span data-ttu-id="2f715-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="2f715-104">**Applies to:**</span></span>

- <span data-ttu-id="2f715-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="2f715-105">Partner Center</span></span>

<span data-ttu-id="2f715-106">Você pode obter uma coleção de SKUs disponíveis em um país para um produto específico usando APIs partner Center.</span><span class="sxs-lookup"><span data-stu-id="2f715-106">You can get a collection of SKUs available in a country for a specific product using Partner Center APIs.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f715-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2f715-107">Prerequisites</span></span>

- <span data-ttu-id="2f715-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2f715-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2f715-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="2f715-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="2f715-110">Um identificador de produto.</span><span class="sxs-lookup"><span data-stu-id="2f715-110">A product identifier.</span></span>

## <a name="c"></a><span data-ttu-id="2f715-111">C\#</span><span class="sxs-lookup"><span data-stu-id="2f715-111">C\#</span></span>

<span data-ttu-id="2f715-112">Para obter a lista de SKUs para um produto:</span><span class="sxs-lookup"><span data-stu-id="2f715-112">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="2f715-113">Obtenha uma interface para as operações de um produto específico seguindo os passos em [Obter um produto por ID](get-a-product-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="2f715-113">Get an interface for a specific product's operations by following the steps in [Get a product by ID](get-a-product-by-id.md).</span></span>

2. <span data-ttu-id="2f715-114">A partir da interface, selecione a propriedade **Skus** para obter uma interface com as operações disponíveis para SKUs.</span><span class="sxs-lookup"><span data-stu-id="2f715-114">From the interface, select the **Skus** property to obtain an interface with the available operations for SKUs.</span></span>

3. <span data-ttu-id="2f715-115">Ligue para o método **Get()** ou **GetAsync()** para recuperar uma coleção dos SKUs disponíveis para o produto.</span><span class="sxs-lookup"><span data-stu-id="2f715-115">Call the **Get()** or **GetAsync()** method to retrieve a collection of the available SKUs for the product.</span></span>

4. <span data-ttu-id="2f715-116">(Opcional) Selecione o âmbito de reserva utilizando o método **ByReservationScope().**</span><span class="sxs-lookup"><span data-stu-id="2f715-116">(Optional) Select the reservation scope using the **ByReservationScope()** method.</span></span>

5. <span data-ttu-id="2f715-117">(Opcional) Utilize o método **ByTargetSegment()** para filtrar os SKUs pelo segmento alvo antes de chamar **Get()** ou **GetAsync()**.</span><span class="sxs-lookup"><span data-stu-id="2f715-117">(Optional) Use the **ByTargetSegment()** method to filter the SKUs by target segment before calling **Get()** or **GetAsync()**.</span></span>

``` csharp
IAggregatePartner partnerOperations;

string countryCode;
string productId;
string productIdForAzureReservation;
string targetSegment;

// Get the available SKUs.
var skus = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.Get();

// Get the available SKUs, filtered by target segment.
var segmentSkus = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ByTargetSegment(targetSegment).Get();

// Get the skus for an Azure reservation product which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
var skus = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.Get();

// Get the skus for an Azure reservation product which are applicable to Azure plans only.
var skus = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ByReservationScope("AzurePlan").Get();

```

## <a name="java"></a><span data-ttu-id="2f715-118">Java</span><span class="sxs-lookup"><span data-stu-id="2f715-118">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="2f715-119">Para obter a lista de SKUs para um produto:</span><span class="sxs-lookup"><span data-stu-id="2f715-119">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="2f715-120">Obtenha uma interface para as operações de um produto específico seguindo os passos em [Obter um produto por ID](get-a-product-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="2f715-120">Get an interface for a specific product's operations by following the steps in [Get a product by ID](get-a-product-by-id.md).</span></span>

2. <span data-ttu-id="2f715-121">A partir da interface, selecione a função **getSkus** para obter uma interface com as operações disponíveis para SKUs.</span><span class="sxs-lookup"><span data-stu-id="2f715-121">From the interface, select the **getSkus** function to obtain an interface with the available operations for SKUs.</span></span>

3. <span data-ttu-id="2f715-122">Ligue para a função **get()** para recuperar uma coleção dos SKUs disponíveis para o produto.</span><span class="sxs-lookup"><span data-stu-id="2f715-122">Call the **get()** function to retrieve a collection of the available SKUs for the product.</span></span>

4. <span data-ttu-id="2f715-123">(Opcional) Utilize a função **byTargetSegment()** para filtrar os SKUs pelo segmento alvo antes de chamar a função **get().**</span><span class="sxs-lookup"><span data-stu-id="2f715-123">(Optional) Use the **byTargetSegment()** function to filter the SKUs by target segment before calling the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;

// String countryCode;
// String productId;
// String targetSegment;

// Get the available SKUs.
ResourceCollection<Sku> skus = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().get();

// Get the available SKUs, filtered by target segment.
var segmentSkus = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().byTargetSegment(targetSegment).get();
```

## <a name="powershell"></a><span data-ttu-id="2f715-124">PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f715-124">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="2f715-125">Para obter a lista de SKUs para um produto:</span><span class="sxs-lookup"><span data-stu-id="2f715-125">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="2f715-126">Execute o comando [**Get-PartnerProductSku.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductSku.md)</span><span class="sxs-lookup"><span data-stu-id="2f715-126">Execute the [**Get-PartnerProductSku**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductSku.md) command.</span></span>

2. <span data-ttu-id="2f715-127">(Opcional) Especifique o parâmetro **segmento** para filtrar os SKUs por segmento alvo.</span><span class="sxs-lookup"><span data-stu-id="2f715-127">(Optional) Specify the **Segment** parameter to filter the SKUs by target segment.</span></span>

```powershell
# $productId
# $targetSegment

# Get the available SKUs.
Get-PartnerProductSku -ProductId $productId

# Get the available SKUs, filtered by target segment.
Get-PartnerProductSku -ProductId $productId -Segment $targetSegment
```

## <a name="rest-request"></a><span data-ttu-id="2f715-128">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2f715-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2f715-129">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f715-129">Request syntax</span></span>

| <span data-ttu-id="2f715-130">Método</span><span class="sxs-lookup"><span data-stu-id="2f715-130">Method</span></span>  | <span data-ttu-id="2f715-131">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2f715-131">Request URI</span></span>                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2f715-132">**Obter**</span><span class="sxs-lookup"><span data-stu-id="2f715-132">**GET**</span></span> | <span data-ttu-id="2f715-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus?country-code}&targetSegment={target-segment} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2f715-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="2f715-134">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="2f715-134">URI parameters</span></span>

<span data-ttu-id="2f715-135">Utilize os seguintes parâmetros de percurso e consulta para obter uma lista de SKUs para um produto.</span><span class="sxs-lookup"><span data-stu-id="2f715-135">Use the following path and query parameters to get a list of SKUs for a product.</span></span>

| <span data-ttu-id="2f715-136">Nome</span><span class="sxs-lookup"><span data-stu-id="2f715-136">Name</span></span>                   | <span data-ttu-id="2f715-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="2f715-137">Type</span></span>     | <span data-ttu-id="2f715-138">Necessário</span><span class="sxs-lookup"><span data-stu-id="2f715-138">Required</span></span> | <span data-ttu-id="2f715-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f715-139">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="2f715-140">id produto</span><span class="sxs-lookup"><span data-stu-id="2f715-140">product-id</span></span>             | <span data-ttu-id="2f715-141">string</span><span class="sxs-lookup"><span data-stu-id="2f715-141">string</span></span>   | <span data-ttu-id="2f715-142">Sim</span><span class="sxs-lookup"><span data-stu-id="2f715-142">Yes</span></span>      | <span data-ttu-id="2f715-143">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="2f715-143">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="2f715-144">código de país</span><span class="sxs-lookup"><span data-stu-id="2f715-144">country-code</span></span>           | <span data-ttu-id="2f715-145">string</span><span class="sxs-lookup"><span data-stu-id="2f715-145">string</span></span>   | <span data-ttu-id="2f715-146">Sim</span><span class="sxs-lookup"><span data-stu-id="2f715-146">Yes</span></span>      | <span data-ttu-id="2f715-147">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="2f715-147">A country/region ID.</span></span>                                            |
| <span data-ttu-id="2f715-148">segmento-alvo</span><span class="sxs-lookup"><span data-stu-id="2f715-148">target-segment</span></span>         | <span data-ttu-id="2f715-149">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="2f715-149">string</span></span>   | <span data-ttu-id="2f715-150">No</span><span class="sxs-lookup"><span data-stu-id="2f715-150">No</span></span>       | <span data-ttu-id="2f715-151">Uma corda que identifica o segmento alvo utilizado para a filtragem.</span><span class="sxs-lookup"><span data-stu-id="2f715-151">A string that identifies the target segment used for filtering.</span></span> |
| <span data-ttu-id="2f715-152">reservationScope</span><span class="sxs-lookup"><span data-stu-id="2f715-152">reservationScope</span></span> | <span data-ttu-id="2f715-153">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="2f715-153">string</span></span>   | <span data-ttu-id="2f715-154">No</span><span class="sxs-lookup"><span data-stu-id="2f715-154">No</span></span> | <span data-ttu-id="2f715-155">Ao consultar uma lista de SKUs para um produto de Reserva Azure, especifique `reservationScope=AzurePlan` para obter uma lista de SKUs que são aplicáveis ao AzurePlan.</span><span class="sxs-lookup"><span data-stu-id="2f715-155">When querying for a list of SKUs for an Azure Reservation product, specify `reservationScope=AzurePlan` to get a list of SKUs which are applicable to AzurePlan.</span></span> <span data-ttu-id="2f715-156">Exclua este parâmetro para obter uma lista de SKUs para um produto Azure Reservation que são aplicáveis às subscrições do Microsoft Azure (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="2f715-156">Exclude this parameter to get a list of SKUs for an Azure Reservation products which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="2f715-157">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2f715-157">Request headers</span></span>

<span data-ttu-id="2f715-158">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2f715-158">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2f715-159">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="2f715-159">Request body</span></span>

<span data-ttu-id="2f715-160">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2f715-160">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="2f715-161">Solicitar exemplos</span><span class="sxs-lookup"><span data-stu-id="2f715-161">Request examples</span></span>

<span data-ttu-id="2f715-162">Obtenha uma lista de SKUs para um determinado produto:</span><span class="sxs-lookup"><span data-stu-id="2f715-162">Get a list of SKUs for a given product:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BPS6/skus?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

<span data-ttu-id="2f715-163">Obtenha uma lista de SKUs para um produto Azure Reservation.</span><span class="sxs-lookup"><span data-stu-id="2f715-163">Get a list of SKUs for an Azure Reservation product.</span></span> <span data-ttu-id="2f715-164">Apenas incluem as SKUs aplicáveis aos planos Azure e não as subscrições da Microsoft Azure (MS-AZR-0145P):</span><span class="sxs-lookup"><span data-stu-id="2f715-164">Only include the SKUs which are applicable to Azure plans and not Microsoft Azure (MS-AZR-0145P) subscriptions:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ5S/skus?country=US&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

<span data-ttu-id="2f715-165">Obtenha uma lista de SKUs para um produto Azure Reservation.</span><span class="sxs-lookup"><span data-stu-id="2f715-165">Get a list of SKUs for an Azure Reservation product.</span></span> <span data-ttu-id="2f715-166">Apenas incluem os SKUs aplicáveis às subscrições do Microsoft Azure (MS-AZR-0145P) e não os planos Azure:</span><span class="sxs-lookup"><span data-stu-id="2f715-166">Only include the SKUs which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions and not Azure plans:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ5S/skus?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

## <a name="rest-response"></a><span data-ttu-id="2f715-167">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2f715-167">REST response</span></span>

<span data-ttu-id="2f715-168">Se for bem sucedido, o corpo de resposta contém uma coleção de recursos [SKU.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="2f715-168">If successful, the response body contains a collection of [SKU](product-resources.md#sku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2f715-169">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2f715-169">Response success and error codes</span></span>

<span data-ttu-id="2f715-170">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2f715-170">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2f715-171">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2f715-171">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2f715-172">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2f715-172">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="2f715-173">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="2f715-173">This method returns the following error codes:</span></span>

| <span data-ttu-id="2f715-174">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="2f715-174">HTTP Status Code</span></span>     | <span data-ttu-id="2f715-175">Código de erro</span><span class="sxs-lookup"><span data-stu-id="2f715-175">Error code</span></span>   | <span data-ttu-id="2f715-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f715-176">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2f715-177">403</span><span class="sxs-lookup"><span data-stu-id="2f715-177">403</span></span>                  | <span data-ttu-id="2f715-178">400030</span><span class="sxs-lookup"><span data-stu-id="2f715-178">400030</span></span>       | <span data-ttu-id="2f715-179">Não é permitido o acesso ao objetivo solicitado.</span><span class="sxs-lookup"><span data-stu-id="2f715-179">Access to the requested targetSegment is not allowed.</span></span>                                                     |
| <span data-ttu-id="2f715-180">404</span><span class="sxs-lookup"><span data-stu-id="2f715-180">404</span></span>                  | <span data-ttu-id="2f715-181">400013</span><span class="sxs-lookup"><span data-stu-id="2f715-181">400013</span></span>       | <span data-ttu-id="2f715-182">O produto-mãe não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="2f715-182">The parent product was not found.</span></span>                                                                         |

### <a name="response-example"></a><span data-ttu-id="2f715-183">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="2f715-183">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51,e75c1060-852e-4b49-92b0-cd15167a0d51
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d,18b41adf-29b5-48eb-b14f-c9683a4e5b7d
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTVTXHNrdXM=?=
X-Powered-By: ASP.NET
Date: Thu, 15 Mar 2018 21:06:03 GMT
Content-Length: 50917

{
    "totalCount": 40,
    "items": [
        {
            "id": "0001",
            "productId": "DZH318Z0BQ5S",
            "title": "Reserved VM Instance, Standard_ND12s, US West 2, 1 Year",
            "description": "Reserved Virtual Machines Instance, Standard_ND12s, US West 2, 1 Year",
            "minimumQuantity": 1,
            "maximumQuantity": 999999999,
            "isTrial": false,
            "supportedBillingCycles": [
                "one_time"
            ],
            "purchasePrerequisites": [
                "AzureSubscriptionRegistration",
                "InventoryCheck"
            ],
            "provisioningVariables": [
                "Scope",
                "SubscriptionId"
            ],
            "dynamicAttributes": {
                "armSkuName": "Standard_ND12s",
                "cores": "12",
                "ram": "224",
                "skuDisplayName": "ND12",
                "category": "GPU",
                "armRegionName": "westus2",
                "duration": "1Year",
                "region": "US West 2",
                "diskType": "Hdd"
            },
            "links": {
                "availabilities": {
                    "uri": "/products/DZH318Z0BQ5S/skus/0001/availabilities?country=US",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/DZH318Z0BQ5S/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        {
            "id": "0002",
            "productId": "DZH318Z0BQ5S",
            "title": "Reserved VM Instance, Standard_ND6s, US West 2, 1 Year",
            "description": "Reserved Virtual Machines Instance, Standard_ND6s, US West 2, 1 Year",
            "minimumQuantity": 1,
            "maximumQuantity": 999999999,
            "isTrial": false,
            "supportedBillingCycles": [
                "one_time"
            ],
            "purchasePrerequisites": [
                "AzureSubscriptionRegistration",
                "InventoryCheck"
            ],
            "provisioningVariables": [
                "Scope",
                "SubscriptionId"
            ],
            "dynamicAttributes": {
                "armSkuName": "Standard_ND6s",
                "cores": "6",
                "ram": "112",
                "skuDisplayName": "ND6",
                "category": "GPU",
                "armRegionName": "westus2",
                "duration": "1Year",
                "region": "US West 2",
                "diskType": "Hdd"
            },
            "links": {
                "availabilities": {
                    "uri": "/products/DZH318Z0BQ5S/skus/0002/availabilities?country=US",
                    "method": "GET",
                    "headers": []
                },
            "self": {
                    "uri": "/products/DZH318Z0BQ5S/skus/0002?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
        [...]
    ],
    "links": {
        "self": {
            "uri": "/products/DZH318Z0BQ5S/skus?country=US",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
