---
title: Obtenha a disponibilidade por ID
description: Obtém a disponibilidade para o produto especificado e SKU usando um ID de disponibilidade.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 824303d40e1dcb0405246c8e29562c4527d147fd
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768761"
---
# <a name="get-the-availability-by-id"></a><span data-ttu-id="7104a-103">Obtenha a disponibilidade por ID</span><span class="sxs-lookup"><span data-stu-id="7104a-103">Get the availability by ID</span></span>

<span data-ttu-id="7104a-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="7104a-104">**Applies To**</span></span>

- <span data-ttu-id="7104a-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="7104a-105">Partner Center</span></span>

<span data-ttu-id="7104a-106">Obtém a disponibilidade para o produto especificado e SKU usando um ID de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="7104a-106">Gets the availability for the specified product and SKU using an availability ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7104a-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7104a-107">Prerequisites</span></span>

- <span data-ttu-id="7104a-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7104a-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7104a-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="7104a-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="7104a-110">Uma identificação de produto.</span><span class="sxs-lookup"><span data-stu-id="7104a-110">A product ID.</span></span>

- <span data-ttu-id="7104a-111">Um SKU ID.</span><span class="sxs-lookup"><span data-stu-id="7104a-111">A SKU ID.</span></span>

- <span data-ttu-id="7104a-112">Uma identificação de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="7104a-112">An availability ID.</span></span>

## <a name="c"></a><span data-ttu-id="7104a-113">C\#</span><span class="sxs-lookup"><span data-stu-id="7104a-113">C\#</span></span>

<span data-ttu-id="7104a-114">Para obter detalhes de uma [disponibilidade](product-resources.md#availability)específica, comece por usar os passos em [Get a SKU by ID](get-a-sku-by-id.md) para obter a interface para uma determinada [sku's](product-resources.md#sku) operations.</span><span class="sxs-lookup"><span data-stu-id="7104a-114">To get details of a specific [availability](product-resources.md#availability), start by using the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific [SKU's](product-resources.md#sku) operations.</span></span> <span data-ttu-id="7104a-115">A partir da interface resultante, selecione a propriedade **Availabilities** para obter uma interface com as operações disponíveis para Disponibilidades.</span><span class="sxs-lookup"><span data-stu-id="7104a-115">From the resulting interface, select the **Availabilities** property to obtain an interface with the available operations for Availabilities.</span></span> <span data-ttu-id="7104a-116">Depois disso, passe o ID de disponibilidade para o método **ById()** para obter as operações para essa disponibilidade específica e, em seguida, ligue para **Get()** ou **GetAsync()** para recuperar os detalhes da disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="7104a-116">After that, pass the availability ID to the **ById()** method to get the operations for that specific availability and then call **Get()** or **GetAsync()** to retrieve the availability details.</span></span>

```csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string availabilityId;

// Get the availability details.
var availability = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.ById(availabilityId).Get();
```

## <a name="java"></a><span data-ttu-id="7104a-117">Java</span><span class="sxs-lookup"><span data-stu-id="7104a-117">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="7104a-118">Para obter detalhes de uma [disponibilidade](product-resources.md#availability)específica, comece por usar os passos em [Get a SKU by ID](get-a-sku-by-id.md) para obter a interface para uma determinada [sku's](product-resources.md#sku) operations.</span><span class="sxs-lookup"><span data-stu-id="7104a-118">To get details of a specific [availability](product-resources.md#availability), start by using the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific [SKU's](product-resources.md#sku) operations.</span></span> <span data-ttu-id="7104a-119">A partir da interface resultante, selecione a função **getAvailabilities** para obter uma interface com as operações disponíveis para Disponibilidades.</span><span class="sxs-lookup"><span data-stu-id="7104a-119">From the resulting interface, select the **getAvailabilities** function to obtain an interface with the available operations for Availabilities.</span></span> <span data-ttu-id="7104a-120">Depois disso, passe o ID de disponibilidade para a função **byId()** para obter as operações para essa disponibilidade específica e, em seguida, ligue para a função **get()** para recuperar os detalhes da disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="7104a-120">After that, pass the availability ID to the **byId()** function to get the operations for that specific availability and then call the **get()** function to retrieve the availability details.</span></span>

```java
IAggregatePartner partnerOperations;
String countryCode;
String productId;
String skuId;
String availabilityId;

// Get the availability details.
Availability availability = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().byId(skuId).getAvailabilities().byId(availabilityId).get();
```

## <a name="powershell"></a><span data-ttu-id="7104a-121">PowerShell</span><span class="sxs-lookup"><span data-stu-id="7104a-121">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="7104a-122">Para obter detalhes de uma [disponibilidade](product-resources.md#availability)específica, execute a [**Oferta de Produtos de Produtos de Parceiros**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) e especifique os parâmetros **AvailabilityId**, **CountryCode,** **ProductId** e **SkuId** para recuperar os detalhes da disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="7104a-122">To get details of a specific [availability](product-resources.md#availability), execute the [**Get-PartnerProductAvailability**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) and specify the **AvailabilityId**, **CountryCode**, **ProductId**, and **SkuId** parameters to retrieve the availability details.</span></span>

```powershell
Get-PartnerProductAvailability -Product $productId -SkuId $skuId -AvailabilityId $availabilityId
```

## <a name="rest-request"></a><span data-ttu-id="7104a-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="7104a-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7104a-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="7104a-124">Request syntax</span></span>

| <span data-ttu-id="7104a-125">Método</span><span class="sxs-lookup"><span data-stu-id="7104a-125">Method</span></span>  | <span data-ttu-id="7104a-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="7104a-126">Request URI</span></span> |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7104a-127">**Obter**</span><span class="sxs-lookup"><span data-stu-id="7104a-127">**GET**</span></span> | <span data-ttu-id="7104a-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7104a-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code} HTTP/1.1</span></span>         |

### <a name="uri-parameter"></a><span data-ttu-id="7104a-129">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="7104a-129">URI parameter</span></span>

<span data-ttu-id="7104a-130">Use os seguintes parâmetros de caminho e consulta para obter uma disponibilidade específica usando um ID de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="7104a-130">Use the following path and query parameters to get a specific availability using an availability ID.</span></span>

| <span data-ttu-id="7104a-131">Nome</span><span class="sxs-lookup"><span data-stu-id="7104a-131">Name</span></span>                   | <span data-ttu-id="7104a-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="7104a-132">Type</span></span>     | <span data-ttu-id="7104a-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="7104a-133">Required</span></span> | <span data-ttu-id="7104a-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="7104a-134">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="7104a-135">id produto</span><span class="sxs-lookup"><span data-stu-id="7104a-135">product-id</span></span>             | <span data-ttu-id="7104a-136">string</span><span class="sxs-lookup"><span data-stu-id="7104a-136">string</span></span>   | <span data-ttu-id="7104a-137">Sim</span><span class="sxs-lookup"><span data-stu-id="7104a-137">Yes</span></span>      | <span data-ttu-id="7104a-138">Uma corda formatada GUID que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="7104a-138">A GUID formatted string that identifies the product.</span></span>            |
| <span data-ttu-id="7104a-139">sku-id</span><span class="sxs-lookup"><span data-stu-id="7104a-139">sku-id</span></span>                 | <span data-ttu-id="7104a-140">string</span><span class="sxs-lookup"><span data-stu-id="7104a-140">string</span></span>   | <span data-ttu-id="7104a-141">Sim</span><span class="sxs-lookup"><span data-stu-id="7104a-141">Yes</span></span>      | <span data-ttu-id="7104a-142">Uma corda formatada GUID que identifica o SKU.</span><span class="sxs-lookup"><span data-stu-id="7104a-142">A GUID formatted string that identifies the SKU.</span></span>                |
| <span data-ttu-id="7104a-143">disponibilidade id</span><span class="sxs-lookup"><span data-stu-id="7104a-143">availability-id</span></span>        | <span data-ttu-id="7104a-144">string</span><span class="sxs-lookup"><span data-stu-id="7104a-144">string</span></span>   | <span data-ttu-id="7104a-145">Sim</span><span class="sxs-lookup"><span data-stu-id="7104a-145">Yes</span></span>      | <span data-ttu-id="7104a-146">Uma cadeia formatada GUID que identifica a disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="7104a-146">A GUID formatted string that identifies the availability.</span></span>       |
| <span data-ttu-id="7104a-147">código de país</span><span class="sxs-lookup"><span data-stu-id="7104a-147">country-code</span></span>           | <span data-ttu-id="7104a-148">string</span><span class="sxs-lookup"><span data-stu-id="7104a-148">string</span></span>   | <span data-ttu-id="7104a-149">Sim</span><span class="sxs-lookup"><span data-stu-id="7104a-149">Yes</span></span>      | <span data-ttu-id="7104a-150">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="7104a-150">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="7104a-151">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="7104a-151">Request headers</span></span>

<span data-ttu-id="7104a-152">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7104a-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7104a-153">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="7104a-153">Request body</span></span>

<span data-ttu-id="7104a-154">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7104a-154">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7104a-155">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="7104a-155">Request example</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318XZXPHL?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 2e12a576-ded5-437e-a5ec-dbfbcbd1624c
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="7104a-156">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="7104a-156">REST response</span></span>

<span data-ttu-id="7104a-157">Se for bem sucedido, o organismo de resposta contém um recurso [Availability.](product-resources.md#availability)</span><span class="sxs-lookup"><span data-stu-id="7104a-157">If successful, the response body contains an [Availability](product-resources.md#availability) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7104a-158">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="7104a-158">Response success and error codes</span></span>

<span data-ttu-id="7104a-159">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="7104a-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7104a-160">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="7104a-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7104a-161">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="7104a-161">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="7104a-162">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="7104a-162">This method returns the following error codes:</span></span>

| <span data-ttu-id="7104a-163">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="7104a-163">HTTP Status Code</span></span>     | <span data-ttu-id="7104a-164">Código de erro</span><span class="sxs-lookup"><span data-stu-id="7104a-164">Error code</span></span>   | <span data-ttu-id="7104a-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="7104a-165">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7104a-166">404</span><span class="sxs-lookup"><span data-stu-id="7104a-166">404</span></span>                  | <span data-ttu-id="7104a-167">400013</span><span class="sxs-lookup"><span data-stu-id="7104a-167">400013</span></span>       | <span data-ttu-id="7104a-168">O produto não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="7104a-168">Product was not found.</span></span>                                                                                    |
| <span data-ttu-id="7104a-169">404</span><span class="sxs-lookup"><span data-stu-id="7104a-169">404</span></span>                  | <span data-ttu-id="7104a-170">400018</span><span class="sxs-lookup"><span data-stu-id="7104a-170">400018</span></span>       | <span data-ttu-id="7104a-171">Sku não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="7104a-171">Sku was not found.</span></span>                                                                                        |
| <span data-ttu-id="7104a-172">404</span><span class="sxs-lookup"><span data-stu-id="7104a-172">404</span></span>                  | <span data-ttu-id="7104a-173">400019</span><span class="sxs-lookup"><span data-stu-id="7104a-173">400019</span></span>       | <span data-ttu-id="7104a-174">Disponibilidade não encontrada.</span><span class="sxs-lookup"><span data-stu-id="7104a-174">Availability not found.</span></span>                                                                                   |

### <a name="response-example"></a><span data-ttu-id="7104a-175">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="7104a-175">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58,83b644b5-e54a-4bdc-b354-f96c525b3c58
MS-RequestId: 2e12a576-ded5-437e-a5ec-dbfbcbd1624c,2e12a576-ded5-437e-a5ec-dbfbcbd1624c
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNRXHNrdXNcMDAwMVxhdmFpbGFiaWxpdGllc1xEWkgzMThaMEhNS1E=?=
X-Powered-By: ASP.NET
Date: Wed, 14 Mar 2018 22:19:43 GMT
Content-Length: 440

{
    "id": "DZH318XZXPHL",
    "productId": "DZH318Z0BQ3Q",
    "skuId": "0001",
    "catalogItemId": "DZH318Z0BQ3Q:0001:DZH318XZXPHL",
    "defaultCurrency": {
        "code": "USD",
        "symbol": "$"
    },
    "segment": "commercial",
    "country": "US",
    "isPurchasable": true,
    "isRenewable": false,
    "terms": [{
        "duration": "P1Y",
        "description": "1 Year Prepaid"
    }],
    "product": { ... },
    "sku": { ... },
    "links": {
        "self": {
            "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318XZXPHL?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
