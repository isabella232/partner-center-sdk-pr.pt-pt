---
title: Obter um SKU por ID
description: Obtém um SKU para o produto especificado utilizando o ID SKU especificado.
ms.date: 01/08/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 54ef72413d2d2b9e7154e82e4bbdd7427a79a2dd
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769091"
---
# <a name="get-a-sku-by-id"></a><span data-ttu-id="aeadf-103">Obter um SKU por ID</span><span class="sxs-lookup"><span data-stu-id="aeadf-103">Get a SKU by ID</span></span>

<span data-ttu-id="aeadf-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="aeadf-104">**Applies To**</span></span>

- <span data-ttu-id="aeadf-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="aeadf-105">Partner Center</span></span>

<span data-ttu-id="aeadf-106">Obtém um SKU para o produto especificado utilizando o ID SKU especificado.</span><span class="sxs-lookup"><span data-stu-id="aeadf-106">Gets a SKU for the specified product using the specified SKU ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aeadf-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="aeadf-107">Prerequisites</span></span>

- <span data-ttu-id="aeadf-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="aeadf-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="aeadf-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="aeadf-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="aeadf-110">Uma identificação de produto.</span><span class="sxs-lookup"><span data-stu-id="aeadf-110">A product ID.</span></span>

- <span data-ttu-id="aeadf-111">Um SKU ID.</span><span class="sxs-lookup"><span data-stu-id="aeadf-111">A SKU ID.</span></span>

## <a name="c"></a><span data-ttu-id="aeadf-112">C\#</span><span class="sxs-lookup"><span data-stu-id="aeadf-112">C\#</span></span>

<span data-ttu-id="aeadf-113">Para obter os detalhes de um SKU específico, comece por seguir os passos em [Obter um produto por ID](get-a-product-by-id.md) para obter a interface para as operações de um produto específico.</span><span class="sxs-lookup"><span data-stu-id="aeadf-113">To get the details of a specific SKU, start by following the steps in [Get a product by ID](get-a-product-by-id.md) to get the interface for a specific product's operations.</span></span> <span data-ttu-id="aeadf-114">A partir da interface resultante, selecione a propriedade **Skus** para obter uma interface com as operações disponíveis para SKUs.</span><span class="sxs-lookup"><span data-stu-id="aeadf-114">From the resulting interface, select the **Skus** property to obtain an interface with the available operations for SKUs.</span></span> <span data-ttu-id="aeadf-115">Passe o ID SKU para o método **ById()** e ligue para **Get()** ou **GetAsync()** para recuperar os detalhes do SKU.</span><span class="sxs-lookup"><span data-stu-id="aeadf-115">Pass the SKU ID to the **ById()** method, and call **Get()** or **GetAsync()** to retrieve the SKU details.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;

// Get the SKU details.
var sku = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Get();
```

## <a name="rest-request"></a><span data-ttu-id="aeadf-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="aeadf-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="aeadf-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="aeadf-117">Request syntax</span></span>

| <span data-ttu-id="aeadf-118">Método</span><span class="sxs-lookup"><span data-stu-id="aeadf-118">Method</span></span>  | <span data-ttu-id="aeadf-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="aeadf-119">Request URI</span></span>                                                                                                         |
|---------|---------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="aeadf-120">**Obter**</span><span class="sxs-lookup"><span data-stu-id="aeadf-120">**GET**</span></span> | <span data-ttu-id="aeadf-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}?country={country-code} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="aeadf-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}?country={country-code} HTTP/1.1</span></span>   |

### <a name="uri-parameter"></a><span data-ttu-id="aeadf-122">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="aeadf-122">URI parameter</span></span>

<span data-ttu-id="aeadf-123">Utilize os seguintes parâmetros de percurso e consulta para obter um SKU para o produto especificado utilizando o ID SKU especificado.</span><span class="sxs-lookup"><span data-stu-id="aeadf-123">Use the following path and query parameters to get a SKU for the specified product using the specified SKU ID.</span></span>

| <span data-ttu-id="aeadf-124">Nome</span><span class="sxs-lookup"><span data-stu-id="aeadf-124">Name</span></span>                   | <span data-ttu-id="aeadf-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="aeadf-125">Type</span></span>     | <span data-ttu-id="aeadf-126">Necessário</span><span class="sxs-lookup"><span data-stu-id="aeadf-126">Required</span></span> | <span data-ttu-id="aeadf-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="aeadf-127">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="aeadf-128">id produto</span><span class="sxs-lookup"><span data-stu-id="aeadf-128">product-id</span></span>             | <span data-ttu-id="aeadf-129">string</span><span class="sxs-lookup"><span data-stu-id="aeadf-129">string</span></span>   | <span data-ttu-id="aeadf-130">Sim</span><span class="sxs-lookup"><span data-stu-id="aeadf-130">Yes</span></span>      | <span data-ttu-id="aeadf-131">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="aeadf-131">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="aeadf-132">sku-id</span><span class="sxs-lookup"><span data-stu-id="aeadf-132">sku-id</span></span>                 | <span data-ttu-id="aeadf-133">string</span><span class="sxs-lookup"><span data-stu-id="aeadf-133">string</span></span>   | <span data-ttu-id="aeadf-134">Sim</span><span class="sxs-lookup"><span data-stu-id="aeadf-134">Yes</span></span>      | <span data-ttu-id="aeadf-135">Uma corda que identifica o SKU.</span><span class="sxs-lookup"><span data-stu-id="aeadf-135">A string that identifies the SKU.</span></span>                               |
| <span data-ttu-id="aeadf-136">código de país</span><span class="sxs-lookup"><span data-stu-id="aeadf-136">country-code</span></span>           | <span data-ttu-id="aeadf-137">string</span><span class="sxs-lookup"><span data-stu-id="aeadf-137">string</span></span>   | <span data-ttu-id="aeadf-138">Sim</span><span class="sxs-lookup"><span data-stu-id="aeadf-138">Yes</span></span>      | <span data-ttu-id="aeadf-139">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="aeadf-139">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="aeadf-140">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="aeadf-140">Request headers</span></span>

<span data-ttu-id="aeadf-141">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="aeadf-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="aeadf-142">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="aeadf-142">Request body</span></span>

<span data-ttu-id="aeadf-143">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="aeadf-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="aeadf-144">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="aeadf-144">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="aeadf-145">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="aeadf-145">REST response</span></span>

<span data-ttu-id="aeadf-146">Se for bem sucedido, o corpo de resposta contém um recurso [SKU.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="aeadf-146">If successful, the response body contains a [SKU](product-resources.md#sku) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="aeadf-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="aeadf-147">Response success and error codes</span></span>

<span data-ttu-id="aeadf-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="aeadf-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="aeadf-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="aeadf-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="aeadf-150">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="aeadf-150">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="aeadf-151">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="aeadf-151">This method returns the following error codes:</span></span>

| <span data-ttu-id="aeadf-152">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="aeadf-152">HTTP Status Code</span></span>     | <span data-ttu-id="aeadf-153">Código de erro</span><span class="sxs-lookup"><span data-stu-id="aeadf-153">Error code</span></span>   | <span data-ttu-id="aeadf-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="aeadf-154">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="aeadf-155">404</span><span class="sxs-lookup"><span data-stu-id="aeadf-155">404</span></span>                  | <span data-ttu-id="aeadf-156">400013</span><span class="sxs-lookup"><span data-stu-id="aeadf-156">400013</span></span>       | <span data-ttu-id="aeadf-157">O produto não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="aeadf-157">Product was not found.</span></span>                                                                                    |
| <span data-ttu-id="aeadf-158">404</span><span class="sxs-lookup"><span data-stu-id="aeadf-158">404</span></span>                  | <span data-ttu-id="aeadf-159">400018</span><span class="sxs-lookup"><span data-stu-id="aeadf-159">400018</span></span>       | <span data-ttu-id="aeadf-160">Sku não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="aeadf-160">Sku was not found.</span></span>                                                                                        |

### <a name="response-example"></a><span data-ttu-id="aeadf-161">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="aeadf-161">Response example</span></span>

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
