---
title: Obter um SKU por ID
description: Obtém um SKU para o produto especificado utilizando o ID SKU especificado.
ms.date: 01/08/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 9516a87a438a0a84a6f6069c1f9b2a2e97e90fba
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873858"
---
# <a name="get-a-sku-by-id"></a><span data-ttu-id="b0c13-103">Obter um SKU por ID</span><span class="sxs-lookup"><span data-stu-id="b0c13-103">Get a SKU by ID</span></span>

<span data-ttu-id="b0c13-104">Obtém um SKU para o produto especificado utilizando o ID SKU especificado.</span><span class="sxs-lookup"><span data-stu-id="b0c13-104">Gets a SKU for the specified product using the specified SKU ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0c13-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b0c13-105">Prerequisites</span></span>

- <span data-ttu-id="b0c13-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b0c13-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b0c13-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="b0c13-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="b0c13-108">Uma identificação de produto.</span><span class="sxs-lookup"><span data-stu-id="b0c13-108">A product ID.</span></span>

- <span data-ttu-id="b0c13-109">Um SKU ID.</span><span class="sxs-lookup"><span data-stu-id="b0c13-109">A SKU ID.</span></span>

## <a name="c"></a><span data-ttu-id="b0c13-110">C\#</span><span class="sxs-lookup"><span data-stu-id="b0c13-110">C\#</span></span>

<span data-ttu-id="b0c13-111">Para obter os detalhes de um SKU específico, comece por seguir os passos em [Obter um produto por ID](get-a-product-by-id.md) para obter a interface para as operações de um produto específico.</span><span class="sxs-lookup"><span data-stu-id="b0c13-111">To get the details of a specific SKU, start by following the steps in [Get a product by ID](get-a-product-by-id.md) to get the interface for a specific product's operations.</span></span> <span data-ttu-id="b0c13-112">A partir da interface resultante, selecione a propriedade **Skus** para obter uma interface com as operações disponíveis para SKUs.</span><span class="sxs-lookup"><span data-stu-id="b0c13-112">From the resulting interface, select the **Skus** property to obtain an interface with the available operations for SKUs.</span></span> <span data-ttu-id="b0c13-113">Passe o ID SKU para o método **ById()** e ligue para **Get()** ou **GetAsync()** para recuperar os detalhes do SKU.</span><span class="sxs-lookup"><span data-stu-id="b0c13-113">Pass the SKU ID to the **ById()** method, and call **Get()** or **GetAsync()** to retrieve the SKU details.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;

// Get the SKU details.
var sku = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Get();
```

## <a name="rest-request"></a><span data-ttu-id="b0c13-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b0c13-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b0c13-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0c13-115">Request syntax</span></span>

| <span data-ttu-id="b0c13-116">Método</span><span class="sxs-lookup"><span data-stu-id="b0c13-116">Method</span></span>  | <span data-ttu-id="b0c13-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b0c13-117">Request URI</span></span>                                                                                                         |
|---------|---------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b0c13-118">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b0c13-118">**GET**</span></span> | <span data-ttu-id="b0c13-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}?country={country-code} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b0c13-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}?country={country-code} HTTP/1.1</span></span>   |

### <a name="uri-parameter"></a><span data-ttu-id="b0c13-120">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="b0c13-120">URI parameter</span></span>

<span data-ttu-id="b0c13-121">Utilize os seguintes parâmetros de percurso e consulta para obter um SKU para o produto especificado utilizando o ID SKU especificado.</span><span class="sxs-lookup"><span data-stu-id="b0c13-121">Use the following path and query parameters to get a SKU for the specified product using the specified SKU ID.</span></span>

| <span data-ttu-id="b0c13-122">Nome</span><span class="sxs-lookup"><span data-stu-id="b0c13-122">Name</span></span>                   | <span data-ttu-id="b0c13-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="b0c13-123">Type</span></span>     | <span data-ttu-id="b0c13-124">Necessário</span><span class="sxs-lookup"><span data-stu-id="b0c13-124">Required</span></span> | <span data-ttu-id="b0c13-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0c13-125">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="b0c13-126">id produto</span><span class="sxs-lookup"><span data-stu-id="b0c13-126">product-id</span></span>             | <span data-ttu-id="b0c13-127">string</span><span class="sxs-lookup"><span data-stu-id="b0c13-127">string</span></span>   | <span data-ttu-id="b0c13-128">Yes</span><span class="sxs-lookup"><span data-stu-id="b0c13-128">Yes</span></span>      | <span data-ttu-id="b0c13-129">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="b0c13-129">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="b0c13-130">sku-id</span><span class="sxs-lookup"><span data-stu-id="b0c13-130">sku-id</span></span>                 | <span data-ttu-id="b0c13-131">string</span><span class="sxs-lookup"><span data-stu-id="b0c13-131">string</span></span>   | <span data-ttu-id="b0c13-132">Yes</span><span class="sxs-lookup"><span data-stu-id="b0c13-132">Yes</span></span>      | <span data-ttu-id="b0c13-133">Uma corda que identifica o SKU.</span><span class="sxs-lookup"><span data-stu-id="b0c13-133">A string that identifies the SKU.</span></span>                               |
| <span data-ttu-id="b0c13-134">código de país</span><span class="sxs-lookup"><span data-stu-id="b0c13-134">country-code</span></span>           | <span data-ttu-id="b0c13-135">string</span><span class="sxs-lookup"><span data-stu-id="b0c13-135">string</span></span>   | <span data-ttu-id="b0c13-136">Yes</span><span class="sxs-lookup"><span data-stu-id="b0c13-136">Yes</span></span>      | <span data-ttu-id="b0c13-137">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="b0c13-137">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="b0c13-138">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b0c13-138">Request headers</span></span>

<span data-ttu-id="b0c13-139">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b0c13-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b0c13-140">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b0c13-140">Request body</span></span>

<span data-ttu-id="b0c13-141">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b0c13-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b0c13-142">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b0c13-142">Request example</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3V/skus/00G1?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e0ae69a5-6322-4d7e-809d-59e02b51d71f
MS-CorrelationId: 956eae17-7650-4470-94d2-4f61b9b02a23
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="b0c13-143">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b0c13-143">REST response</span></span>

<span data-ttu-id="b0c13-144">Se for bem sucedido, o corpo de resposta contém um recurso [SKU.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="b0c13-144">If successful, the response body contains a [SKU](product-resources.md#sku) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b0c13-145">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b0c13-145">Response success and error codes</span></span>

<span data-ttu-id="b0c13-146">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b0c13-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b0c13-147">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b0c13-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b0c13-148">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b0c13-148">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="b0c13-149">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="b0c13-149">This method returns the following error codes:</span></span>

| <span data-ttu-id="b0c13-150">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="b0c13-150">HTTP Status Code</span></span>     | <span data-ttu-id="b0c13-151">Código de erro</span><span class="sxs-lookup"><span data-stu-id="b0c13-151">Error code</span></span>   | <span data-ttu-id="b0c13-152">Description</span><span class="sxs-lookup"><span data-stu-id="b0c13-152">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b0c13-153">404</span><span class="sxs-lookup"><span data-stu-id="b0c13-153">404</span></span>                  | <span data-ttu-id="b0c13-154">400013</span><span class="sxs-lookup"><span data-stu-id="b0c13-154">400013</span></span>       | <span data-ttu-id="b0c13-155">O produto não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="b0c13-155">Product was not found.</span></span>                                                                                    |
| <span data-ttu-id="b0c13-156">404</span><span class="sxs-lookup"><span data-stu-id="b0c13-156">404</span></span>                  | <span data-ttu-id="b0c13-157">400018</span><span class="sxs-lookup"><span data-stu-id="b0c13-157">400018</span></span>       | <span data-ttu-id="b0c13-158">Sku não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="b0c13-158">Sku was not found.</span></span>                                                                                        |

### <a name="response-example"></a><span data-ttu-id="b0c13-159">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b0c13-159">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 956eae17-7650-4470-94d2-4f61b9b02a23,956eae17-7650-4470-94d2-4f61b9b02a23
MS-RequestId: e0ae69a5-6322-4d7e-809d-59e02b51d71f,e0ae69a5-6322-4d7e-809d-59e02b51d71f
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNWXHNrdXNcMDBHMQ==?=
X-Powered-By: ASP.NET
Date: Thu, 15 Mar 2018 17:43:25 GMT
Content-Length: 1108

{
    "id": "00G1",
    "productId": "DZH318Z0BQ3V",
    "title": "Reserved VM Instance, Standard_D32s_v3, US West 2, 3 Years",
    "description": "Reserved Virtual Machines Instance, Standard_D32s_v3, US West 2, 3 Years",
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
    "inventoryVariables": [
        "CustomerId",
        "AzureSubscriptionId"
    ],
    "provisioningVariables": [
        "Scope",
        "SubscriptionId"
    ],
    "dynamicAttributes": {
        "armSkuName": "Standard_D32s_v3",
        "cores": "32",
        "ram": "128",
        "skuDisplayName": "D32s v3",
        "category": "General purpose",
        "armRegionName": "westus2",
        "duration": "3Years",
        "region": "US West 2",
        "diskType": "Ssd"
    },
    "links": {
        "availabilities": {
            "uri": "/products/DZH318Z0BQ3V/skus/00G1/availabilities?country=us",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BQ3V/skus/00G1?country=us",
            "method": "GET",
            "headers": []
        }
    }
}
```
