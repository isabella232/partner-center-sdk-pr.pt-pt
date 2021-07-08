---
title: Obter uma lista de disponibilidade para um SKU (por país)
description: Como obter uma coleção de disponibilidades para o produto especificado e SKU por país de cliente.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b29c005e74ad8a4da547a888b78e4599e74ebd02
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874538"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-country"></a><span data-ttu-id="1ae74-103">Obter uma lista de disponibilidade para um SKU (por país)</span><span class="sxs-lookup"><span data-stu-id="1ae74-103">Get a list of availabilities for a SKU (by country)</span></span>

<span data-ttu-id="1ae74-104">Este artigo descreve como obter uma coleção de disponibilidades em um determinado país para um produto especificado e SKU.</span><span class="sxs-lookup"><span data-stu-id="1ae74-104">This article describes how to get a collection of availabilities in a particular country for a specified product and SKU.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ae74-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1ae74-105">Prerequisites</span></span>

- <span data-ttu-id="1ae74-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1ae74-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1ae74-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="1ae74-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="1ae74-108">Um identificador de produto.</span><span class="sxs-lookup"><span data-stu-id="1ae74-108">A product identifier.</span></span>

- <span data-ttu-id="1ae74-109">Um identificador SKU.</span><span class="sxs-lookup"><span data-stu-id="1ae74-109">A SKU identifier.</span></span>

- <span data-ttu-id="1ae74-110">Um país.</span><span class="sxs-lookup"><span data-stu-id="1ae74-110">A country.</span></span>

## <a name="c"></a><span data-ttu-id="1ae74-111">C\#</span><span class="sxs-lookup"><span data-stu-id="1ae74-111">C\#</span></span>

<span data-ttu-id="1ae74-112">Para obter a lista de [disponibilidades](product-resources.md#availability) para um [SKU:](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="1ae74-112">To get the list of [availabilities](product-resources.md#availability) for a [SKU](product-resources.md#sku):</span></span>

1. <span data-ttu-id="1ae74-113">Siga os passos em [Get a SKU by ID](get-a-sku-by-id.md) para obter a interface para uma determinada sku's operations.</span><span class="sxs-lookup"><span data-stu-id="1ae74-113">Follow the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific SKU's operations.</span></span>

2. <span data-ttu-id="1ae74-114">A partir da interface SKU, selecione a propriedade **Availabilities** para obter uma interface com as operações para disponibilidades.</span><span class="sxs-lookup"><span data-stu-id="1ae74-114">From the SKU interface, select the **Availabilities** property to get an interface with the operations for availabilities.</span></span>

3. <span data-ttu-id="1ae74-115">(Opcional) Utilize o método **ByTargetSegment()** para filtrar as disponibilidades por segmento alvo.</span><span class="sxs-lookup"><span data-stu-id="1ae74-115">(Optional) Use the **ByTargetSegment()** method to filter the availabilities by target segment.</span></span>

4. <span data-ttu-id="1ae74-116">Ligue **para Get()** ou **GetAsync para** recuperar uma coleção das disponibilidades para este SKU.</span><span class="sxs-lookup"><span data-stu-id="1ae74-116">Call **Get()** or **GetAsync()** to retrieve a collection of the availabilities for this SKU.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string targetSegment;
string productIdForAzureReservation;
string skuIdForAzureReservation;

// Get the availabilities.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.Get();

// Get the availabilities, filtered by target segment.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.BySegment(targetSegment).Get();

// Get the availabilities for an Azure reservation product and sku which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ById(skuIdForAzureReservation).Availabilities.ByReservationScope("AzurePlan").Get();

// Get the availabilities for an Azure reservation product and sku which are applicable to Azure plans only.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ById(skuIdForAzureReservation).Availabilities.Get();

```

## <a name="rest-request"></a><span data-ttu-id="1ae74-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="1ae74-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1ae74-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ae74-118">Request syntax</span></span>

| <span data-ttu-id="1ae74-119">Método</span><span class="sxs-lookup"><span data-stu-id="1ae74-119">Method</span></span>  | <span data-ttu-id="1ae74-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="1ae74-120">Request URI</span></span>                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1ae74-121">**Obter**</span><span class="sxs-lookup"><span data-stu-id="1ae74-121">**GET**</span></span> | <span data-ttu-id="1ae74-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1ae74-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment} HTTP/1.1</span></span>     |

### <a name="uri-parameters"></a><span data-ttu-id="1ae74-123">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="1ae74-123">URI parameters</span></span>

<span data-ttu-id="1ae74-124">Use os seguintes parâmetros de caminho e consulta para obter uma lista de disponibilidades para um SKU.</span><span class="sxs-lookup"><span data-stu-id="1ae74-124">Use the following path and query parameters to get a list of availabilities for a SKU.</span></span>

| <span data-ttu-id="1ae74-125">Nome</span><span class="sxs-lookup"><span data-stu-id="1ae74-125">Name</span></span>                   | <span data-ttu-id="1ae74-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="1ae74-126">Type</span></span>     | <span data-ttu-id="1ae74-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="1ae74-127">Required</span></span> | <span data-ttu-id="1ae74-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ae74-128">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="1ae74-129">id produto</span><span class="sxs-lookup"><span data-stu-id="1ae74-129">product-id</span></span>             | <span data-ttu-id="1ae74-130">string</span><span class="sxs-lookup"><span data-stu-id="1ae74-130">string</span></span>   | <span data-ttu-id="1ae74-131">Yes</span><span class="sxs-lookup"><span data-stu-id="1ae74-131">Yes</span></span>      | <span data-ttu-id="1ae74-132">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="1ae74-132">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="1ae74-133">sku-id</span><span class="sxs-lookup"><span data-stu-id="1ae74-133">sku-id</span></span>                 | <span data-ttu-id="1ae74-134">string</span><span class="sxs-lookup"><span data-stu-id="1ae74-134">string</span></span>   | <span data-ttu-id="1ae74-135">Yes</span><span class="sxs-lookup"><span data-stu-id="1ae74-135">Yes</span></span>      | <span data-ttu-id="1ae74-136">Uma corda que identifica o SKU.</span><span class="sxs-lookup"><span data-stu-id="1ae74-136">A string that identifies the SKU.</span></span>                               |
| <span data-ttu-id="1ae74-137">código de país</span><span class="sxs-lookup"><span data-stu-id="1ae74-137">country-code</span></span>           | <span data-ttu-id="1ae74-138">string</span><span class="sxs-lookup"><span data-stu-id="1ae74-138">string</span></span>   | <span data-ttu-id="1ae74-139">Yes</span><span class="sxs-lookup"><span data-stu-id="1ae74-139">Yes</span></span>      | <span data-ttu-id="1ae74-140">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="1ae74-140">A country/region ID.</span></span>                                            |
| <span data-ttu-id="1ae74-141">segmento-alvo</span><span class="sxs-lookup"><span data-stu-id="1ae74-141">target-segment</span></span>         | <span data-ttu-id="1ae74-142">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="1ae74-142">string</span></span>   | <span data-ttu-id="1ae74-143">No</span><span class="sxs-lookup"><span data-stu-id="1ae74-143">No</span></span>       | <span data-ttu-id="1ae74-144">Uma corda que identifica o segmento alvo utilizado para a filtragem.</span><span class="sxs-lookup"><span data-stu-id="1ae74-144">A string that identifies the target segment used for filtering.</span></span> |
| <span data-ttu-id="1ae74-145">reservationScope</span><span class="sxs-lookup"><span data-stu-id="1ae74-145">reservationScope</span></span> | <span data-ttu-id="1ae74-146">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="1ae74-146">string</span></span>   | <span data-ttu-id="1ae74-147">No</span><span class="sxs-lookup"><span data-stu-id="1ae74-147">No</span></span> | <span data-ttu-id="1ae74-148">Ao consultar uma lista de disponibilidades para um SKU de Reserva Azure, especifique `reservationScope=AzurePlan` para obter uma lista de disponibilidades que sejam aplicáveis ao AzurePlan.</span><span class="sxs-lookup"><span data-stu-id="1ae74-148">When querying for a list of availabilities for an Azure Reservation SKU, specify `reservationScope=AzurePlan` to get a list of availabilities that are applicable to AzurePlan.</span></span> <span data-ttu-id="1ae74-149">Exclua este parâmetro para obter uma lista de disponibilidades aplicáveis às assinaturas Microsoft Azure (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="1ae74-149">Exclude this parameter to get a list of availabilities that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="1ae74-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="1ae74-150">Request headers</span></span>

<span data-ttu-id="1ae74-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1ae74-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1ae74-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="1ae74-152">Request body</span></span>

<span data-ttu-id="1ae74-153">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1ae74-153">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="1ae74-154">Solicitar exemplos</span><span class="sxs-lookup"><span data-stu-id="1ae74-154">Request examples</span></span>

#### <a name="availabilities-for-sku-by-country"></a><span data-ttu-id="1ae74-155">Disponibilidades para SKU por país</span><span class="sxs-lookup"><span data-stu-id="1ae74-155">Availabilities for SKU by country</span></span>

<span data-ttu-id="1ae74-156">Siga este exemplo para obter uma lista de disponibilidades para um dado SKU por país:</span><span class="sxs-lookup"><span data-stu-id="1ae74-156">Follow this example to get a list of availabilities for a given SKU by country:</span></span>

```http
GET http:// api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
```

#### <a name="availabilities-for-vm-reservations-azure-plan"></a><span data-ttu-id="1ae74-157">Disponibilidades para reservas VM (plano Azure)</span><span class="sxs-lookup"><span data-stu-id="1ae74-157">Availabilities for VM reservations (Azure plan)</span></span>

<span data-ttu-id="1ae74-158">Siga este exemplo para obter uma lista de disponibilidades por país para Azure VM reserva SKUs.</span><span class="sxs-lookup"><span data-stu-id="1ae74-158">Follow this example to get a list of availabilities by country for Azure VM reservation SKUs.</span></span> <span data-ttu-id="1ae74-159">Este exemplo é para os SKUs que se aplicam aos planos Azure:</span><span class="sxs-lookup"><span data-stu-id="1ae74-159">This example is for SKUs that apply to Azure plans:</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="availabilities-for-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="1ae74-160">Disponibilidades para reservas VM para subscrições de Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="1ae74-160">Availabilities for VM reservations for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="1ae74-161">Siga este exemplo para obter uma lista de disponibilidades por país para reservas Azure VM que são aplicáveis a Microsoft Azure (MS-AZR-0145P) subscrições.</span><span class="sxs-lookup"><span data-stu-id="1ae74-161">Follow this example to get a list of availabilities by country for Azure VM reservations that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/productsDZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureAzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="1ae74-162">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="1ae74-162">REST response</span></span>

<span data-ttu-id="1ae74-163">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [**de Disponibilidade.**](product-resources.md#availability)</span><span class="sxs-lookup"><span data-stu-id="1ae74-163">If successful, the response body contains a collection of [**Availability**](product-resources.md#availability) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1ae74-164">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="1ae74-164">Response success and error codes</span></span>

<span data-ttu-id="1ae74-165">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="1ae74-165">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1ae74-166">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="1ae74-166">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1ae74-167">Para obter uma lista completa, consulte [os códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="1ae74-167">For a full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="1ae74-168">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="1ae74-168">This method returns the following error codes:</span></span>

| <span data-ttu-id="1ae74-169">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="1ae74-169">HTTP Status Code</span></span>     | <span data-ttu-id="1ae74-170">Código de erro</span><span class="sxs-lookup"><span data-stu-id="1ae74-170">Error code</span></span>   | <span data-ttu-id="1ae74-171">Description</span><span class="sxs-lookup"><span data-stu-id="1ae74-171">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1ae74-172">403</span><span class="sxs-lookup"><span data-stu-id="1ae74-172">403</span></span>                  | <span data-ttu-id="1ae74-173">400030</span><span class="sxs-lookup"><span data-stu-id="1ae74-173">400030</span></span>       | <span data-ttu-id="1ae74-174">Não é permitido o acesso ao **objetivo solicitado.**</span><span class="sxs-lookup"><span data-stu-id="1ae74-174">Access to the requested **targetSegment** is not allowed.</span></span>                                                     |

### <a name="response-example"></a><span data-ttu-id="1ae74-175">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="1ae74-175">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58,83b644b5-e54a-4bdc-b354-f96c525b3c58
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02,70324727-62d8-4195-8f99-70ea25058d02
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNRXHNrdXNcMDAwMVxhdmFpbGFiaWxpdGllcw==?=
X-Powered-By: ASP.NET
Date: Wed, 14 Mar 2018 22:19:37 GMT
Content-Length: 808

{
    "totalCount": 1,
    "items": [
        {
            "id": "DZH318XZXVNF",
            "productId": "DZH318Z0BQ3Q",
            "skuId": "0001",
            "catalogItemId": "DZH318Z0BQ3Q:0001:DZH318XZXVNF",
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
                    "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318Z0HMKQ?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetSegment=commercial",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
