---
title: Obter uma lista de ofertas para um mercado
description: Recebe uma coleção que contém todas as ofertas para um mercado específico.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 6f4fd821879545db4e781fe3202c8ee11f167615
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874249"
---
# <a name="get-a-list-of-offers-for-a-market"></a><span data-ttu-id="94efd-103">Obter uma lista de ofertas para um mercado</span><span class="sxs-lookup"><span data-stu-id="94efd-103">Get a list of offers for a market</span></span>

<span data-ttu-id="94efd-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="94efd-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="94efd-105">Recebe uma coleção que contém todas as ofertas para um mercado específico.</span><span class="sxs-lookup"><span data-stu-id="94efd-105">Gets a collection that contains all the offers for a specific market.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94efd-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="94efd-106">Prerequisites</span></span>

- <span data-ttu-id="94efd-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="94efd-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="94efd-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="94efd-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="94efd-109">C\#</span><span class="sxs-lookup"><span data-stu-id="94efd-109">C\#</span></span>

<span data-ttu-id="94efd-110">Para obter uma lista de ofertas num dado mercado, use a sua coleção **IAggregatePartner.Offers,** selecione o mercado por país e ligue para o método **Get()** ou **Get Async().**</span><span class="sxs-lookup"><span data-stu-id="94efd-110">To get a list of offers in a given market, use your **IAggregatePartner.Offers** collection, select the market by country, and call the **Get()** or **Get Async()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

ResourceCollection<Offer> offers = partnerOperations.Offers.ByCountry("US").Get();
```

<span data-ttu-id="94efd-111">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="94efd-111">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="94efd-112">**Project**: PartnerSDK.FeatureSample **Class**: Ofertas.cs</span><span class="sxs-lookup"><span data-stu-id="94efd-112">**Project**: PartnerSDK.FeatureSample **Class**: Offers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="94efd-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="94efd-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="94efd-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="94efd-114">Request syntax</span></span>

| <span data-ttu-id="94efd-115">Método</span><span class="sxs-lookup"><span data-stu-id="94efd-115">Method</span></span>  | <span data-ttu-id="94efd-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="94efd-116">Request URI</span></span>                                                                          |
|---------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="94efd-117">**Obter**</span><span class="sxs-lookup"><span data-stu-id="94efd-117">**GET**</span></span> | <span data-ttu-id="94efd-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers?country={country-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="94efd-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers?country={country-id} HTTP/1.1</span></span>   |

### <a name="uri-parameter"></a><span data-ttu-id="94efd-119">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="94efd-119">URI parameter</span></span>

<span data-ttu-id="94efd-120">Esta tabela lista os parâmetros de consulta necessários para obter as ofertas.</span><span class="sxs-lookup"><span data-stu-id="94efd-120">This table lists the required query parameters to get the offers.</span></span>

| <span data-ttu-id="94efd-121">Nome</span><span class="sxs-lookup"><span data-stu-id="94efd-121">Name</span></span>           | <span data-ttu-id="94efd-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="94efd-122">Type</span></span>       | <span data-ttu-id="94efd-123">Necessário</span><span class="sxs-lookup"><span data-stu-id="94efd-123">Required</span></span> | <span data-ttu-id="94efd-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="94efd-124">Description</span></span>            |
|----------------|------------|----------|------------------------|
| <span data-ttu-id="94efd-125">**país id**</span><span class="sxs-lookup"><span data-stu-id="94efd-125">**country-id**</span></span> | <span data-ttu-id="94efd-126">**string**</span><span class="sxs-lookup"><span data-stu-id="94efd-126">**string**</span></span> | <span data-ttu-id="94efd-127">Y</span><span class="sxs-lookup"><span data-stu-id="94efd-127">Y</span></span>        | <span data-ttu-id="94efd-128">O ID do país/região.</span><span class="sxs-lookup"><span data-stu-id="94efd-128">The country/region ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="94efd-129">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="94efd-129">Request headers</span></span>

- <span data-ttu-id="94efd-130">É necessário **um local formatoformado** como uma corda.</span><span class="sxs-lookup"><span data-stu-id="94efd-130">A **locale-id** formatted as a string is required.</span></span>
<span data-ttu-id="94efd-131">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="94efd-131">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="94efd-132">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="94efd-132">Request body</span></span>

<span data-ttu-id="94efd-133">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="94efd-133">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="94efd-134">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="94efd-134">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offers?country=<country-id> HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
X-Locale: <locale-id>
```

## <a name="rest-response"></a><span data-ttu-id="94efd-135">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="94efd-135">REST response</span></span>

<span data-ttu-id="94efd-136">Se for bem sucedido, este método devolve uma coleção de recursos de **Oferta** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="94efd-136">If successful, this method returns a collection of **Offer** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="94efd-137">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="94efd-137">Response success and error codes</span></span>

<span data-ttu-id="94efd-138">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="94efd-138">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="94efd-139">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="94efd-139">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="94efd-140">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="94efd-140">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="94efd-141">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="94efd-141">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 26584
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
Date: Mon, 23 Nov 2015 23:20:44 GMT

{
    "totalCount":12,"items":[{
        "id":"E60E0348-1710-484B-992A-32B294D4CDE1",
        "name":"Azure Rights Management Premium (Government Pricing)",
        "description":"Microsoft Azure Rights Management Premium helps you protect confidential documents and email with strong encryption.
                       Control the use of your information by specifying who can view, edit, print, save and share your data.
                       Simple to use and integrated with Microsoft Office, SharePoint and Exchange.",
        "minimumQuantity":1,
        "maximumQuantity":10000000,
        "rank":5,
        "uri":"/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/E60E0348-1710-484B-992A-32B294D4CDE1",
        "locale":"EN-US",
        "country":"US",
        "category":{
            "id":"Government_Key",
            "name":"Government",
            "rank":40,
            "locale":"en-us",
            "country":"US",
            "attributes":{
                "objectType":"OfferCategory"
            }
        },
        "prerequisiteOffers":[],
        "isAddOn":false,
        "isAvailableForPurchase":true,
        "billing":"license",
        "isAutoRenewable":true,
        "product":{
            "id":"c52ea49f-fe5d-4e95-93ba-1de91d380f89",
            "name":"Azure Rights Management Premium",
            "unit":"Licenses"
        },
        "unitType":"Licenses",
        "links":{
            "learnMore":{
                "uri":"http://g.microsoftonline.com/0BXPS00en/0000",
                "method":"GET",
                "headers":[]
            },
            "self":{
                "uri":"/offers/E60E0348-1710-484B-992A-32B294D4CDE1",
                "method":"GET",
                "headers":[]
            }
        },
        "attributes":{
            "objectType":"Offer"
        }
    },
    "links":{
        "self":{
            "uri":"/v1/offers?country={country-id}",
            "method":"GET",
            "headers":[]
        },
        "previous":{
            "uri":"/v1/offers?country={country-id}",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"Collection"
    }
}
```
