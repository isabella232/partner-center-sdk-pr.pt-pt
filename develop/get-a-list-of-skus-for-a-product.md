---
title: Obter uma lista de SKUs para um produto (por país)
description: Você pode obter e filtrar uma coleção de SKUs por país para um produto usando as APIs do Partner Center.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 27a2391a22a9439461fb53764b87c1cafa68b875
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873892"
---
# <a name="get-a-list-of-skus-for-a-product-by-country"></a><span data-ttu-id="0efd6-103">Obter uma lista de SKUs para um produto (por país)</span><span class="sxs-lookup"><span data-stu-id="0efd6-103">Get a list of SKUs for a product (by country)</span></span>

<span data-ttu-id="0efd6-104">Você pode obter uma coleção de SKUs disponíveis em um país para um produto específico usando APIs partner Center.</span><span class="sxs-lookup"><span data-stu-id="0efd6-104">You can get a collection of SKUs available in a country for a specific product using Partner Center APIs.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0efd6-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0efd6-105">Prerequisites</span></span>

- <span data-ttu-id="0efd6-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0efd6-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0efd6-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="0efd6-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="0efd6-108">Um identificador de produto.</span><span class="sxs-lookup"><span data-stu-id="0efd6-108">A product identifier.</span></span>

## <a name="c"></a><span data-ttu-id="0efd6-109">C\#</span><span class="sxs-lookup"><span data-stu-id="0efd6-109">C\#</span></span>

<span data-ttu-id="0efd6-110">Para obter a lista de SKUs para um produto:</span><span class="sxs-lookup"><span data-stu-id="0efd6-110">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="0efd6-111">Obtenha uma interface para as operações de um produto específico seguindo os passos em [Obter um produto por ID](get-a-product-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="0efd6-111">Get an interface for a specific product's operations by following the steps in [Get a product by ID](get-a-product-by-id.md).</span></span>

2. <span data-ttu-id="0efd6-112">A partir da interface, selecione a propriedade **Skus** para obter uma interface com as operações disponíveis para SKUs.</span><span class="sxs-lookup"><span data-stu-id="0efd6-112">From the interface, select the **Skus** property to obtain an interface with the available operations for SKUs.</span></span>

3. <span data-ttu-id="0efd6-113">Ligue para o método **Get()** ou **GetAsync()** para recuperar uma coleção dos SKUs disponíveis para o produto.</span><span class="sxs-lookup"><span data-stu-id="0efd6-113">Call the **Get()** or **GetAsync()** method to retrieve a collection of the available SKUs for the product.</span></span>

4. <span data-ttu-id="0efd6-114">(Opcional) Selecione o âmbito de reserva utilizando o método **ByReservationScope().**</span><span class="sxs-lookup"><span data-stu-id="0efd6-114">(Optional) Select the reservation scope using the **ByReservationScope()** method.</span></span>

5. <span data-ttu-id="0efd6-115">(Opcional) Utilize o método **ByTargetSegment()** para filtrar os SKUs pelo segmento alvo antes de chamar **Get()** ou **GetAsync()**.</span><span class="sxs-lookup"><span data-stu-id="0efd6-115">(Optional) Use the **ByTargetSegment()** method to filter the SKUs by target segment before calling **Get()** or **GetAsync()**.</span></span>

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

## <a name="java"></a><span data-ttu-id="0efd6-116">Java</span><span class="sxs-lookup"><span data-stu-id="0efd6-116">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="0efd6-117">Para obter a lista de SKUs para um produto:</span><span class="sxs-lookup"><span data-stu-id="0efd6-117">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="0efd6-118">Obtenha uma interface para as operações de um produto específico seguindo os passos em [Obter um produto por ID](get-a-product-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="0efd6-118">Get an interface for a specific product's operations by following the steps in [Get a product by ID](get-a-product-by-id.md).</span></span>

2. <span data-ttu-id="0efd6-119">A partir da interface, selecione a função **getSkus** para obter uma interface com as operações disponíveis para SKUs.</span><span class="sxs-lookup"><span data-stu-id="0efd6-119">From the interface, select the **getSkus** function to obtain an interface with the available operations for SKUs.</span></span>

3. <span data-ttu-id="0efd6-120">Ligue para a função **get()** para recuperar uma coleção dos SKUs disponíveis para o produto.</span><span class="sxs-lookup"><span data-stu-id="0efd6-120">Call the **get()** function to retrieve a collection of the available SKUs for the product.</span></span>

4. <span data-ttu-id="0efd6-121">(Opcional) Utilize a função **byTargetSegment()** para filtrar os SKUs pelo segmento alvo antes de chamar a função **get().**</span><span class="sxs-lookup"><span data-stu-id="0efd6-121">(Optional) Use the **byTargetSegment()** function to filter the SKUs by target segment before calling the **get()** function.</span></span>

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

## <a name="powershell"></a><span data-ttu-id="0efd6-122">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0efd6-122">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="0efd6-123">Para obter a lista de SKUs para um produto:</span><span class="sxs-lookup"><span data-stu-id="0efd6-123">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="0efd6-124">Execute o comando [**Get-PartnerProductSku.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductSku.md)</span><span class="sxs-lookup"><span data-stu-id="0efd6-124">Execute the [**Get-PartnerProductSku**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductSku.md) command.</span></span>

2. <span data-ttu-id="0efd6-125">(Opcional) Especifique o parâmetro **segmento** para filtrar os SKUs por segmento alvo.</span><span class="sxs-lookup"><span data-stu-id="0efd6-125">(Optional) Specify the **Segment** parameter to filter the SKUs by target segment.</span></span>

```powershell
# $productId
# $targetSegment

# Get the available SKUs.
Get-PartnerProductSku -ProductId $productId

# Get the available SKUs, filtered by target segment.
Get-PartnerProductSku -ProductId $productId -Segment $targetSegment
```

## <a name="rest-request"></a><span data-ttu-id="0efd6-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="0efd6-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0efd6-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="0efd6-127">Request syntax</span></span>

| <span data-ttu-id="0efd6-128">Método</span><span class="sxs-lookup"><span data-stu-id="0efd6-128">Method</span></span>  | <span data-ttu-id="0efd6-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="0efd6-129">Request URI</span></span>                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0efd6-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="0efd6-130">**GET**</span></span> | <span data-ttu-id="0efd6-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus?country-code}&targetSegment={target-segment} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0efd6-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="0efd6-132">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="0efd6-132">URI parameters</span></span>

<span data-ttu-id="0efd6-133">Utilize os seguintes parâmetros de percurso e consulta para obter uma lista de SKUs para um produto.</span><span class="sxs-lookup"><span data-stu-id="0efd6-133">Use the following path and query parameters to get a list of SKUs for a product.</span></span>

| <span data-ttu-id="0efd6-134">Nome</span><span class="sxs-lookup"><span data-stu-id="0efd6-134">Name</span></span>                   | <span data-ttu-id="0efd6-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="0efd6-135">Type</span></span>     | <span data-ttu-id="0efd6-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="0efd6-136">Required</span></span> | <span data-ttu-id="0efd6-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="0efd6-137">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="0efd6-138">id produto</span><span class="sxs-lookup"><span data-stu-id="0efd6-138">product-id</span></span>             | <span data-ttu-id="0efd6-139">string</span><span class="sxs-lookup"><span data-stu-id="0efd6-139">string</span></span>   | <span data-ttu-id="0efd6-140">Yes</span><span class="sxs-lookup"><span data-stu-id="0efd6-140">Yes</span></span>      | <span data-ttu-id="0efd6-141">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="0efd6-141">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="0efd6-142">código de país</span><span class="sxs-lookup"><span data-stu-id="0efd6-142">country-code</span></span>           | <span data-ttu-id="0efd6-143">string</span><span class="sxs-lookup"><span data-stu-id="0efd6-143">string</span></span>   | <span data-ttu-id="0efd6-144">Yes</span><span class="sxs-lookup"><span data-stu-id="0efd6-144">Yes</span></span>      | <span data-ttu-id="0efd6-145">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="0efd6-145">A country/region ID.</span></span>                                            |
| <span data-ttu-id="0efd6-146">segmento-alvo</span><span class="sxs-lookup"><span data-stu-id="0efd6-146">target-segment</span></span>         | <span data-ttu-id="0efd6-147">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="0efd6-147">string</span></span>   | <span data-ttu-id="0efd6-148">No</span><span class="sxs-lookup"><span data-stu-id="0efd6-148">No</span></span>       | <span data-ttu-id="0efd6-149">Uma corda que identifica o segmento alvo utilizado para a filtragem.</span><span class="sxs-lookup"><span data-stu-id="0efd6-149">A string that identifies the target segment used for filtering.</span></span> |
| <span data-ttu-id="0efd6-150">reservationScope</span><span class="sxs-lookup"><span data-stu-id="0efd6-150">reservationScope</span></span> | <span data-ttu-id="0efd6-151">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="0efd6-151">string</span></span>   | <span data-ttu-id="0efd6-152">No</span><span class="sxs-lookup"><span data-stu-id="0efd6-152">No</span></span> | <span data-ttu-id="0efd6-153">Ao consultar uma lista de SKUs para um produto Azure Reservation, especifique `reservationScope=AzurePlan` para obter uma lista de SKUs que são aplicáveis ao AzurePlan.</span><span class="sxs-lookup"><span data-stu-id="0efd6-153">When querying for a list of SKUs for an Azure Reservation product, specify `reservationScope=AzurePlan` to get a list of SKUs that are applicable to AzurePlan.</span></span> <span data-ttu-id="0efd6-154">Exclua este parâmetro para obter uma lista de SKUs para produtos Azure Reservation que são aplicáveis às assinaturas Microsoft Azure (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="0efd6-154">Exclude this parameter to get a list of SKUs for Azure Reservation products that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="0efd6-155">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="0efd6-155">Request headers</span></span>

<span data-ttu-id="0efd6-156">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="0efd6-156">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0efd6-157">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="0efd6-157">Request body</span></span>

<span data-ttu-id="0efd6-158">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0efd6-158">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="0efd6-159">Solicitar exemplos</span><span class="sxs-lookup"><span data-stu-id="0efd6-159">Request examples</span></span>

<span data-ttu-id="0efd6-160">Obtenha uma lista de SKUs para um determinado produto:</span><span class="sxs-lookup"><span data-stu-id="0efd6-160">Get a list of SKUs for a given product:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BPS6/skus?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

<span data-ttu-id="0efd6-161">Obtenha uma lista de SKUs para um produto Azure Reservation.</span><span class="sxs-lookup"><span data-stu-id="0efd6-161">Get a list of SKUs for an Azure Reservation product.</span></span> <span data-ttu-id="0efd6-162">Apenas incluem as SKUs aplicáveis aos planos Azure e não Microsoft Azure (MS-AZR-0145P) subscrições:</span><span class="sxs-lookup"><span data-stu-id="0efd6-162">Only include the SKUs that are applicable to Azure plans and not Microsoft Azure (MS-AZR-0145P) subscriptions:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ5S/skus?country=US&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

<span data-ttu-id="0efd6-163">Obtenha uma lista de SKUs para um produto Azure Reservation.</span><span class="sxs-lookup"><span data-stu-id="0efd6-163">Get a list of SKUs for an Azure Reservation product.</span></span> <span data-ttu-id="0efd6-164">Apenas incluem os SKUs aplicáveis às assinaturas Microsoft Azure (MS-AZR-0145P) e não planos Azure:</span><span class="sxs-lookup"><span data-stu-id="0efd6-164">Only include the SKUs that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions and not Azure plans:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ5S/skus?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

## <a name="rest-response"></a><span data-ttu-id="0efd6-165">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="0efd6-165">REST response</span></span>

<span data-ttu-id="0efd6-166">Se for bem sucedido, o corpo de resposta contém uma coleção de recursos [SKU.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="0efd6-166">If successful, the response body contains a collection of [SKU](product-resources.md#sku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0efd6-167">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="0efd6-167">Response success and error codes</span></span>

<span data-ttu-id="0efd6-168">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="0efd6-168">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0efd6-169">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="0efd6-169">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0efd6-170">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="0efd6-170">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="0efd6-171">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="0efd6-171">This method returns the following error codes:</span></span>

| <span data-ttu-id="0efd6-172">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="0efd6-172">HTTP Status Code</span></span>     | <span data-ttu-id="0efd6-173">Código de erro</span><span class="sxs-lookup"><span data-stu-id="0efd6-173">Error code</span></span>   | <span data-ttu-id="0efd6-174">Description</span><span class="sxs-lookup"><span data-stu-id="0efd6-174">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0efd6-175">403</span><span class="sxs-lookup"><span data-stu-id="0efd6-175">403</span></span>                  | <span data-ttu-id="0efd6-176">400030</span><span class="sxs-lookup"><span data-stu-id="0efd6-176">400030</span></span>       | <span data-ttu-id="0efd6-177">Não é permitido o acesso ao objetivo solicitado.</span><span class="sxs-lookup"><span data-stu-id="0efd6-177">Access to the requested targetSegment is not allowed.</span></span>                                                     |
| <span data-ttu-id="0efd6-178">404</span><span class="sxs-lookup"><span data-stu-id="0efd6-178">404</span></span>                  | <span data-ttu-id="0efd6-179">400013</span><span class="sxs-lookup"><span data-stu-id="0efd6-179">400013</span></span>       | <span data-ttu-id="0efd6-180">O produto-mãe não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="0efd6-180">The parent product was not found.</span></span>                                                                         |

### <a name="response-example"></a><span data-ttu-id="0efd6-181">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="0efd6-181">Response example</span></span>

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
