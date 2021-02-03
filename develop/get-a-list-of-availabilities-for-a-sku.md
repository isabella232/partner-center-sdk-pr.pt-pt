---
title: Obter uma lista de disponibilidade para um SKU (por país)
description: Como obter uma coleção de disponibilidades para o produto especificado e SKU por país de cliente.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b97a4ce85b5edd9de1301a577988f8c54096ebeb
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769122"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-country"></a><span data-ttu-id="3150f-103">Obter uma lista de disponibilidade para um SKU (por país)</span><span class="sxs-lookup"><span data-stu-id="3150f-103">Get a list of availabilities for a SKU (by country)</span></span>

<span data-ttu-id="3150f-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="3150f-104">**Applies to:**</span></span>

- <span data-ttu-id="3150f-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="3150f-105">Partner Center</span></span>

<span data-ttu-id="3150f-106">Este artigo descreve como obter uma coleção de disponibilidades em um determinado país para um produto especificado e SKU.</span><span class="sxs-lookup"><span data-stu-id="3150f-106">This article describes how to get a collection of availabilities in a particular country for a specified product and SKU.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3150f-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3150f-107">Prerequisites</span></span>

- <span data-ttu-id="3150f-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3150f-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3150f-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="3150f-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="3150f-110">Um identificador de produto.</span><span class="sxs-lookup"><span data-stu-id="3150f-110">A product identifier.</span></span>

- <span data-ttu-id="3150f-111">Um identificador SKU.</span><span class="sxs-lookup"><span data-stu-id="3150f-111">A SKU identifier.</span></span>

- <span data-ttu-id="3150f-112">Um país.</span><span class="sxs-lookup"><span data-stu-id="3150f-112">A country.</span></span>

## <a name="c"></a><span data-ttu-id="3150f-113">C\#</span><span class="sxs-lookup"><span data-stu-id="3150f-113">C\#</span></span>

<span data-ttu-id="3150f-114">Para obter a lista de [disponibilidades](product-resources.md#availability) para um [SKU:](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="3150f-114">To get the list of [availabilities](product-resources.md#availability) for a [SKU](product-resources.md#sku):</span></span>

1. <span data-ttu-id="3150f-115">Siga os passos em [Get a SKU by ID](get-a-sku-by-id.md) para obter a interface para uma determinada sku's operations.</span><span class="sxs-lookup"><span data-stu-id="3150f-115">Follow the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific SKU's operations.</span></span>

2. <span data-ttu-id="3150f-116">A partir da interface SKU, selecione a propriedade **Availabilities** para obter uma interface com as operações para disponibilidades.</span><span class="sxs-lookup"><span data-stu-id="3150f-116">From the SKU interface, select the **Availabilities** property to get an interface with the operations for availabilities.</span></span>

3. <span data-ttu-id="3150f-117">(Opcional) Utilize o método **ByTargetSegment()** para filtrar as disponibilidades por segmento alvo.</span><span class="sxs-lookup"><span data-stu-id="3150f-117">(Optional) Use the **ByTargetSegment()** method to filter the availabilities by target segment.</span></span>

4. <span data-ttu-id="3150f-118">Ligue **para Get()** ou **GetAsync para** recuperar uma coleção das disponibilidades para este SKU.</span><span class="sxs-lookup"><span data-stu-id="3150f-118">Call **Get()** or **GetAsync()** to retrieve a collection of the availabilities for this SKU.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="3150f-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="3150f-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3150f-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="3150f-120">Request syntax</span></span>

| <span data-ttu-id="3150f-121">Método</span><span class="sxs-lookup"><span data-stu-id="3150f-121">Method</span></span>  | <span data-ttu-id="3150f-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="3150f-122">Request URI</span></span>                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3150f-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="3150f-123">**GET**</span></span> | <span data-ttu-id="3150f-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="3150f-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment} HTTP/1.1</span></span>     |

### <a name="uri-parameters"></a><span data-ttu-id="3150f-125">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="3150f-125">URI parameters</span></span>

<span data-ttu-id="3150f-126">Use os seguintes parâmetros de caminho e consulta para obter uma lista de disponibilidades para um SKU.</span><span class="sxs-lookup"><span data-stu-id="3150f-126">Use the following path and query parameters to get a list of availabilities for a SKU.</span></span>

| <span data-ttu-id="3150f-127">Nome</span><span class="sxs-lookup"><span data-stu-id="3150f-127">Name</span></span>                   | <span data-ttu-id="3150f-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="3150f-128">Type</span></span>     | <span data-ttu-id="3150f-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="3150f-129">Required</span></span> | <span data-ttu-id="3150f-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="3150f-130">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="3150f-131">id produto</span><span class="sxs-lookup"><span data-stu-id="3150f-131">product-id</span></span>             | <span data-ttu-id="3150f-132">string</span><span class="sxs-lookup"><span data-stu-id="3150f-132">string</span></span>   | <span data-ttu-id="3150f-133">Sim</span><span class="sxs-lookup"><span data-stu-id="3150f-133">Yes</span></span>      | <span data-ttu-id="3150f-134">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="3150f-134">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="3150f-135">sku-id</span><span class="sxs-lookup"><span data-stu-id="3150f-135">sku-id</span></span>                 | <span data-ttu-id="3150f-136">string</span><span class="sxs-lookup"><span data-stu-id="3150f-136">string</span></span>   | <span data-ttu-id="3150f-137">Sim</span><span class="sxs-lookup"><span data-stu-id="3150f-137">Yes</span></span>      | <span data-ttu-id="3150f-138">Uma corda que identifica o SKU.</span><span class="sxs-lookup"><span data-stu-id="3150f-138">A string that identifies the SKU.</span></span>                               |
| <span data-ttu-id="3150f-139">código de país</span><span class="sxs-lookup"><span data-stu-id="3150f-139">country-code</span></span>           | <span data-ttu-id="3150f-140">string</span><span class="sxs-lookup"><span data-stu-id="3150f-140">string</span></span>   | <span data-ttu-id="3150f-141">Sim</span><span class="sxs-lookup"><span data-stu-id="3150f-141">Yes</span></span>      | <span data-ttu-id="3150f-142">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="3150f-142">A country/region ID.</span></span>                                            |
| <span data-ttu-id="3150f-143">segmento-alvo</span><span class="sxs-lookup"><span data-stu-id="3150f-143">target-segment</span></span>         | <span data-ttu-id="3150f-144">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="3150f-144">string</span></span>   | <span data-ttu-id="3150f-145">No</span><span class="sxs-lookup"><span data-stu-id="3150f-145">No</span></span>       | <span data-ttu-id="3150f-146">Uma corda que identifica o segmento alvo utilizado para a filtragem.</span><span class="sxs-lookup"><span data-stu-id="3150f-146">A string that identifies the target segment used for filtering.</span></span> |
| <span data-ttu-id="3150f-147">reservationScope</span><span class="sxs-lookup"><span data-stu-id="3150f-147">reservationScope</span></span> | <span data-ttu-id="3150f-148">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="3150f-148">string</span></span>   | <span data-ttu-id="3150f-149">No</span><span class="sxs-lookup"><span data-stu-id="3150f-149">No</span></span> | <span data-ttu-id="3150f-150">Ao consultar uma lista de disponibilidades para um SKU de Reserva Azure, especifique `reservationScope=AzurePlan` para obter uma lista de disponibilidades aplicáveis ao AzurePlan.</span><span class="sxs-lookup"><span data-stu-id="3150f-150">When querying for a list of availabilities for an Azure Reservation SKU, specify `reservationScope=AzurePlan` to get a list of availabilities which are applicable to AzurePlan.</span></span> <span data-ttu-id="3150f-151">Exclua este parâmetro para obter uma lista de disponibilidades aplicáveis às subscrições do Microsoft Azure (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="3150f-151">Exclude this parameter to get a list of availabilities which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="3150f-152">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="3150f-152">Request headers</span></span>

<span data-ttu-id="3150f-153">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3150f-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3150f-154">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="3150f-154">Request body</span></span>

<span data-ttu-id="3150f-155">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3150f-155">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="3150f-156">Solicitar exemplos</span><span class="sxs-lookup"><span data-stu-id="3150f-156">Request examples</span></span>

#### <a name="availabilities-for-sku-by-country"></a><span data-ttu-id="3150f-157">Disponibilidades para SKU por país</span><span class="sxs-lookup"><span data-stu-id="3150f-157">Availabilities for SKU by country</span></span>

<span data-ttu-id="3150f-158">Siga este exemplo para obter uma lista de disponibilidades para um dado SKU por país:</span><span class="sxs-lookup"><span data-stu-id="3150f-158">Follow this example to get a list of availabilities for a given SKU by country:</span></span>

```http
GET http:// api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
```

#### <a name="availabilities-for-vm-reservations-azure-plan"></a><span data-ttu-id="3150f-159">Disponibilidades para reservas VM (plano Azure)</span><span class="sxs-lookup"><span data-stu-id="3150f-159">Availabilities for VM reservations (Azure plan)</span></span>

<span data-ttu-id="3150f-160">Siga este exemplo para obter uma lista de disponibilidades por país para Azure VM reserva SKUs.</span><span class="sxs-lookup"><span data-stu-id="3150f-160">Follow this example to get a list of availabilities by country for Azure VM reservation SKUs.</span></span> <span data-ttu-id="3150f-161">Este exemplo é para os SKUs que se aplicam aos planos Azure:</span><span class="sxs-lookup"><span data-stu-id="3150f-161">This example is for SKUs that apply to Azure plans:</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="availabilities-for-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="3150f-162">Disponibilidades para reservas VM para subscrições microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="3150f-162">Availabilities for VM reservations for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="3150f-163">Siga este exemplo para obter uma lista de disponibilidades por país para reservas Azure VM que são aplicáveis às subscrições do Microsoft Azure (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="3150f-163">Follow this example to get a list of availabilities by country for Azure VM reservations that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/productsDZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureAzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="3150f-164">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="3150f-164">REST response</span></span>

<span data-ttu-id="3150f-165">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [**de Disponibilidade.**](product-resources.md#availability)</span><span class="sxs-lookup"><span data-stu-id="3150f-165">If successful, the response body contains a collection of [**Availability**](product-resources.md#availability) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3150f-166">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="3150f-166">Response success and error codes</span></span>

<span data-ttu-id="3150f-167">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="3150f-167">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3150f-168">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="3150f-168">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3150f-169">Para obter uma lista completa, consulte [os códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="3150f-169">For a full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="3150f-170">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="3150f-170">This method returns the following error codes:</span></span>

| <span data-ttu-id="3150f-171">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="3150f-171">HTTP Status Code</span></span>     | <span data-ttu-id="3150f-172">Código de erro</span><span class="sxs-lookup"><span data-stu-id="3150f-172">Error code</span></span>   | <span data-ttu-id="3150f-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="3150f-173">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3150f-174">403</span><span class="sxs-lookup"><span data-stu-id="3150f-174">403</span></span>                  | <span data-ttu-id="3150f-175">400030</span><span class="sxs-lookup"><span data-stu-id="3150f-175">400030</span></span>       | <span data-ttu-id="3150f-176">Não é permitido o acesso ao **objetivo solicitado.**</span><span class="sxs-lookup"><span data-stu-id="3150f-176">Access to the requested **targetSegment** is not allowed.</span></span>                                                     |

### <a name="response-example"></a><span data-ttu-id="3150f-177">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="3150f-177">Response example</span></span>

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
