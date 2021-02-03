---
title: Obter uma lista de ofertas para um mercado
description: Recebe uma coleção que contém todas as ofertas para um mercado específico.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 3a004f6f8f8de8cd398d82c300793e4f196efaaa
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769109"
---
# <a name="get-a-list-of-offers-for-a-market"></a><span data-ttu-id="60ed3-103">Obter uma lista de ofertas para um mercado</span><span class="sxs-lookup"><span data-stu-id="60ed3-103">Get a list of offers for a market</span></span>

<span data-ttu-id="60ed3-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="60ed3-104">**Applies To**</span></span>

- <span data-ttu-id="60ed3-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="60ed3-105">Partner Center</span></span>
- <span data-ttu-id="60ed3-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="60ed3-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="60ed3-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="60ed3-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="60ed3-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="60ed3-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="60ed3-109">Recebe uma coleção que contém todas as ofertas para um mercado específico.</span><span class="sxs-lookup"><span data-stu-id="60ed3-109">Gets a collection that contains all the offers for a specific market.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="60ed3-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="60ed3-110">Prerequisites</span></span>

- <span data-ttu-id="60ed3-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="60ed3-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="60ed3-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="60ed3-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="60ed3-113">C\#</span><span class="sxs-lookup"><span data-stu-id="60ed3-113">C\#</span></span>

<span data-ttu-id="60ed3-114">Para obter uma lista de ofertas num dado mercado, use a sua coleção **IAggregatePartner.Offers,** selecione o mercado por país e ligue para o método **Get()** ou **Get Async().**</span><span class="sxs-lookup"><span data-stu-id="60ed3-114">To get a list of offers in a given market, use your **IAggregatePartner.Offers** collection, select the market by country, and call the **Get()** or **Get Async()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

ResourceCollection<Offer> offers = partnerOperations.Offers.ByCountry("US").Get();
```

<span data-ttu-id="60ed3-115">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="60ed3-115">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="60ed3-116">**Projeto**: PartnerSDK.FeatureSample **Class**: Offers.cs</span><span class="sxs-lookup"><span data-stu-id="60ed3-116">**Project**: PartnerSDK.FeatureSample **Class**: Offers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="60ed3-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="60ed3-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="60ed3-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="60ed3-118">Request syntax</span></span>

| <span data-ttu-id="60ed3-119">Método</span><span class="sxs-lookup"><span data-stu-id="60ed3-119">Method</span></span>  | <span data-ttu-id="60ed3-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="60ed3-120">Request URI</span></span>                                                                          |
|---------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="60ed3-121">**Obter**</span><span class="sxs-lookup"><span data-stu-id="60ed3-121">**GET**</span></span> | <span data-ttu-id="60ed3-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers?country={country-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="60ed3-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers?country={country-id} HTTP/1.1</span></span>   |

### <a name="uri-parameter"></a><span data-ttu-id="60ed3-123">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="60ed3-123">URI parameter</span></span>

<span data-ttu-id="60ed3-124">Esta tabela lista os parâmetros de consulta necessários para obter as ofertas.</span><span class="sxs-lookup"><span data-stu-id="60ed3-124">This table lists the required query parameters to get the offers.</span></span>

| <span data-ttu-id="60ed3-125">Nome</span><span class="sxs-lookup"><span data-stu-id="60ed3-125">Name</span></span>           | <span data-ttu-id="60ed3-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="60ed3-126">Type</span></span>       | <span data-ttu-id="60ed3-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="60ed3-127">Required</span></span> | <span data-ttu-id="60ed3-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="60ed3-128">Description</span></span>            |
|----------------|------------|----------|------------------------|
| <span data-ttu-id="60ed3-129">**país id**</span><span class="sxs-lookup"><span data-stu-id="60ed3-129">**country-id**</span></span> | <span data-ttu-id="60ed3-130">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="60ed3-130">**string**</span></span> | <span data-ttu-id="60ed3-131">Y</span><span class="sxs-lookup"><span data-stu-id="60ed3-131">Y</span></span>        | <span data-ttu-id="60ed3-132">O ID do país/região.</span><span class="sxs-lookup"><span data-stu-id="60ed3-132">The country/region ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="60ed3-133">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="60ed3-133">Request headers</span></span>

- <span data-ttu-id="60ed3-134">É necessário **um local formatoformado** como uma corda.</span><span class="sxs-lookup"><span data-stu-id="60ed3-134">A **locale-id** formatted as a string is required.</span></span>
<span data-ttu-id="60ed3-135">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="60ed3-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="60ed3-136">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="60ed3-136">Request body</span></span>

<span data-ttu-id="60ed3-137">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="60ed3-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="60ed3-138">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="60ed3-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offers?country=<country-id> HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
X-Locale: <locale-id>
```

## <a name="rest-response"></a><span data-ttu-id="60ed3-139">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="60ed3-139">REST response</span></span>

<span data-ttu-id="60ed3-140">Se for bem sucedido, este método devolve uma coleção de recursos de **Oferta** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="60ed3-140">If successful, this method returns a collection of **Offer** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="60ed3-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="60ed3-141">Response success and error codes</span></span>

<span data-ttu-id="60ed3-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="60ed3-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="60ed3-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="60ed3-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="60ed3-144">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="60ed3-144">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="60ed3-145">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="60ed3-145">Response example</span></span>

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
