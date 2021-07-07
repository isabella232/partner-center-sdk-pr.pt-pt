---
title: Obtenha a disponibilidade por ID
description: Obtém a disponibilidade para o produto especificado e SKU usando um ID de disponibilidade.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: c31bc12d8d484cc8042f36aa865145600d9e6738
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760203"
---
# <a name="get-the-availability-by-id"></a><span data-ttu-id="62692-103">Obtenha a disponibilidade por ID</span><span class="sxs-lookup"><span data-stu-id="62692-103">Get the availability by ID</span></span>

<span data-ttu-id="62692-104">Obtém a disponibilidade para o produto especificado e SKU usando um ID de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="62692-104">Gets the availability for the specified product and SKU using an availability ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="62692-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="62692-105">Prerequisites</span></span>

- <span data-ttu-id="62692-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="62692-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="62692-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="62692-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="62692-108">Uma identificação de produto.</span><span class="sxs-lookup"><span data-stu-id="62692-108">A product ID.</span></span>

- <span data-ttu-id="62692-109">Um SKU ID.</span><span class="sxs-lookup"><span data-stu-id="62692-109">A SKU ID.</span></span>

- <span data-ttu-id="62692-110">Uma identificação de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="62692-110">An availability ID.</span></span>

## <a name="c"></a><span data-ttu-id="62692-111">C\#</span><span class="sxs-lookup"><span data-stu-id="62692-111">C\#</span></span>

<span data-ttu-id="62692-112">Para obter detalhes de uma [disponibilidade](product-resources.md#availability)específica, comece por usar os passos em [Get a SKU by ID](get-a-sku-by-id.md) para obter a interface para uma determinada [sku's](product-resources.md#sku) operations.</span><span class="sxs-lookup"><span data-stu-id="62692-112">To get details of a specific [availability](product-resources.md#availability), start by using the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific [SKU's](product-resources.md#sku) operations.</span></span> <span data-ttu-id="62692-113">A partir da interface resultante, selecione a propriedade **Availabilities** para obter uma interface com as operações disponíveis para Disponibilidades.</span><span class="sxs-lookup"><span data-stu-id="62692-113">From the resulting interface, select the **Availabilities** property to obtain an interface with the available operations for Availabilities.</span></span> <span data-ttu-id="62692-114">Depois disso, passe o ID de disponibilidade para o método **ById()** para obter as operações para essa disponibilidade específica e, em seguida, ligue para **Get()** ou **GetAsync()** para recuperar os detalhes da disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="62692-114">After that, pass the availability ID to the **ById()** method to get the operations for that specific availability and then call **Get()** or **GetAsync()** to retrieve the availability details.</span></span>

```csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string availabilityId;

// Get the availability details.
var availability = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.ById(availabilityId).Get();
```

## <a name="java"></a><span data-ttu-id="62692-115">Java</span><span class="sxs-lookup"><span data-stu-id="62692-115">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="62692-116">Para obter detalhes de uma [disponibilidade](product-resources.md#availability)específica, comece por usar os passos em [Get a SKU by ID](get-a-sku-by-id.md) para obter a interface para uma determinada [sku's](product-resources.md#sku) operations.</span><span class="sxs-lookup"><span data-stu-id="62692-116">To get details of a specific [availability](product-resources.md#availability), start by using the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific [SKU's](product-resources.md#sku) operations.</span></span> <span data-ttu-id="62692-117">A partir da interface resultante, selecione a função **getAvailabilities** para obter uma interface com as operações disponíveis para Disponibilidades.</span><span class="sxs-lookup"><span data-stu-id="62692-117">From the resulting interface, select the **getAvailabilities** function to obtain an interface with the available operations for Availabilities.</span></span> <span data-ttu-id="62692-118">Depois disso, passe o ID de disponibilidade para a função **byId()** para obter as operações para essa disponibilidade específica e, em seguida, ligue para a função **get()** para recuperar os detalhes da disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="62692-118">After that, pass the availability ID to the **byId()** function to get the operations for that specific availability and then call the **get()** function to retrieve the availability details.</span></span>

```java
IAggregatePartner partnerOperations;
String countryCode;
String productId;
String skuId;
String availabilityId;

// Get the availability details.
Availability availability = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().byId(skuId).getAvailabilities().byId(availabilityId).get();
```

## <a name="powershell"></a><span data-ttu-id="62692-119">PowerShell</span><span class="sxs-lookup"><span data-stu-id="62692-119">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="62692-120">Para obter detalhes de uma [disponibilidade](product-resources.md#availability)específica, execute a [**Oferta de Produtos de Produtos de Parceiros**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) e especifique os parâmetros **AvailabilityId**, **CountryCode,** **ProductId** e **SkuId** para recuperar os detalhes da disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="62692-120">To get details of a specific [availability](product-resources.md#availability), execute the [**Get-PartnerProductAvailability**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) and specify the **AvailabilityId**, **CountryCode**, **ProductId**, and **SkuId** parameters to retrieve the availability details.</span></span>

```powershell
Get-PartnerProductAvailability -Product $productId -SkuId $skuId -AvailabilityId $availabilityId
```

## <a name="rest-request"></a><span data-ttu-id="62692-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="62692-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="62692-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="62692-122">Request syntax</span></span>

| <span data-ttu-id="62692-123">Método</span><span class="sxs-lookup"><span data-stu-id="62692-123">Method</span></span>  | <span data-ttu-id="62692-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="62692-124">Request URI</span></span> |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="62692-125">**Obter**</span><span class="sxs-lookup"><span data-stu-id="62692-125">**GET**</span></span> | <span data-ttu-id="62692-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="62692-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code} HTTP/1.1</span></span>         |

### <a name="uri-parameter"></a><span data-ttu-id="62692-127">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="62692-127">URI parameter</span></span>

<span data-ttu-id="62692-128">Use os seguintes parâmetros de caminho e consulta para obter uma disponibilidade específica usando um ID de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="62692-128">Use the following path and query parameters to get a specific availability using an availability ID.</span></span>

| <span data-ttu-id="62692-129">Nome</span><span class="sxs-lookup"><span data-stu-id="62692-129">Name</span></span>                   | <span data-ttu-id="62692-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="62692-130">Type</span></span>     | <span data-ttu-id="62692-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="62692-131">Required</span></span> | <span data-ttu-id="62692-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="62692-132">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="62692-133">id produto</span><span class="sxs-lookup"><span data-stu-id="62692-133">product-id</span></span>             | <span data-ttu-id="62692-134">string</span><span class="sxs-lookup"><span data-stu-id="62692-134">string</span></span>   | <span data-ttu-id="62692-135">Yes</span><span class="sxs-lookup"><span data-stu-id="62692-135">Yes</span></span>      | <span data-ttu-id="62692-136">Uma corda formatada GUID que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="62692-136">A GUID formatted string that identifies the product.</span></span>            |
| <span data-ttu-id="62692-137">sku-id</span><span class="sxs-lookup"><span data-stu-id="62692-137">sku-id</span></span>                 | <span data-ttu-id="62692-138">string</span><span class="sxs-lookup"><span data-stu-id="62692-138">string</span></span>   | <span data-ttu-id="62692-139">Yes</span><span class="sxs-lookup"><span data-stu-id="62692-139">Yes</span></span>      | <span data-ttu-id="62692-140">Uma corda formatada GUID que identifica o SKU.</span><span class="sxs-lookup"><span data-stu-id="62692-140">A GUID formatted string that identifies the SKU.</span></span>                |
| <span data-ttu-id="62692-141">disponibilidade id</span><span class="sxs-lookup"><span data-stu-id="62692-141">availability-id</span></span>        | <span data-ttu-id="62692-142">string</span><span class="sxs-lookup"><span data-stu-id="62692-142">string</span></span>   | <span data-ttu-id="62692-143">Yes</span><span class="sxs-lookup"><span data-stu-id="62692-143">Yes</span></span>      | <span data-ttu-id="62692-144">Uma cadeia formatada GUID que identifica a disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="62692-144">A GUID formatted string that identifies the availability.</span></span>       |
| <span data-ttu-id="62692-145">código de país</span><span class="sxs-lookup"><span data-stu-id="62692-145">country-code</span></span>           | <span data-ttu-id="62692-146">string</span><span class="sxs-lookup"><span data-stu-id="62692-146">string</span></span>   | <span data-ttu-id="62692-147">Yes</span><span class="sxs-lookup"><span data-stu-id="62692-147">Yes</span></span>      | <span data-ttu-id="62692-148">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="62692-148">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="62692-149">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="62692-149">Request headers</span></span>

<span data-ttu-id="62692-150">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="62692-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="62692-151">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="62692-151">Request body</span></span>

<span data-ttu-id="62692-152">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="62692-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="62692-153">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="62692-153">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="62692-154">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="62692-154">REST response</span></span>

<span data-ttu-id="62692-155">Se for bem sucedido, o organismo de resposta contém um recurso [Availability.](product-resources.md#availability)</span><span class="sxs-lookup"><span data-stu-id="62692-155">If successful, the response body contains an [Availability](product-resources.md#availability) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="62692-156">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="62692-156">Response success and error codes</span></span>

<span data-ttu-id="62692-157">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="62692-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="62692-158">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="62692-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="62692-159">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="62692-159">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="62692-160">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="62692-160">This method returns the following error codes:</span></span>

| <span data-ttu-id="62692-161">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="62692-161">HTTP Status Code</span></span>     | <span data-ttu-id="62692-162">Código de erro</span><span class="sxs-lookup"><span data-stu-id="62692-162">Error code</span></span>   | <span data-ttu-id="62692-163">Description</span><span class="sxs-lookup"><span data-stu-id="62692-163">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="62692-164">404</span><span class="sxs-lookup"><span data-stu-id="62692-164">404</span></span>                  | <span data-ttu-id="62692-165">400013</span><span class="sxs-lookup"><span data-stu-id="62692-165">400013</span></span>       | <span data-ttu-id="62692-166">O produto não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="62692-166">Product was not found.</span></span>                                                                                    |
| <span data-ttu-id="62692-167">404</span><span class="sxs-lookup"><span data-stu-id="62692-167">404</span></span>                  | <span data-ttu-id="62692-168">400018</span><span class="sxs-lookup"><span data-stu-id="62692-168">400018</span></span>       | <span data-ttu-id="62692-169">O SKU não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="62692-169">SKU was not found.</span></span>                                                                                        |
| <span data-ttu-id="62692-170">404</span><span class="sxs-lookup"><span data-stu-id="62692-170">404</span></span>                  | <span data-ttu-id="62692-171">400019</span><span class="sxs-lookup"><span data-stu-id="62692-171">400019</span></span>       | <span data-ttu-id="62692-172">Disponibilidade não encontrada.</span><span class="sxs-lookup"><span data-stu-id="62692-172">Availability not found.</span></span>                                                                                   |

### <a name="response-example"></a><span data-ttu-id="62692-173">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="62692-173">Response example</span></span>

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
