---
title: Obter uma lista de categorias de ofertas por mercado
description: Saiba como obter uma coleção que contenha todas as categorias de oferta num dado país/região e local para todas as Microsoft Clouds.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: e699355f07dda3941eafed32f5f635d94000abd1
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874283"
---
# <a name="get-a-list-of-offer-categories-by-market"></a><span data-ttu-id="c942e-103">Obter uma lista de categorias de ofertas por mercado</span><span class="sxs-lookup"><span data-stu-id="c942e-103">Get a list of offer categories by market</span></span>

<span data-ttu-id="c942e-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c942e-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c942e-105">Este artigo descreve como obter uma coleção que contenha todas as categorias de oferta num determinado país/região e localidade.</span><span class="sxs-lookup"><span data-stu-id="c942e-105">This article describes how to get a collection that contains all the offer categories in a given country/region and locale.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c942e-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c942e-106">Prerequisites</span></span>

- <span data-ttu-id="c942e-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c942e-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c942e-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="c942e-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="c942e-109">C\#</span><span class="sxs-lookup"><span data-stu-id="c942e-109">C\#</span></span>

<span data-ttu-id="c942e-110">Para obter uma lista de categorias de ofertas num determinado país/região e local:</span><span class="sxs-lookup"><span data-stu-id="c942e-110">To get a list of offer categories in a given country/region and locale:</span></span>

1. <span data-ttu-id="c942e-111">Utilize a sua coleção [**IAggregatePartner.Operations**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) para ligar para o método [**With num**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner.with) determinado contexto.</span><span class="sxs-lookup"><span data-stu-id="c942e-111">Use your [**IAggregatePartner.Operations**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) collection to call the [**With()**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner.with) method on a given context.</span></span>

2. <span data-ttu-id="c942e-112">Inspecione a propriedade do objeto resultante da [**OfertaCategories.**](/dotnet/api/microsoft.store.partnercenter.ipartner.offercategories)</span><span class="sxs-lookup"><span data-stu-id="c942e-112">Inspect the [**OfferCategories**](/dotnet/api/microsoft.store.partnercenter.ipartner.offercategories) property of the resulting object.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

ResourceCollection<OfferCategory> offerCategoryResults = partnerOperations.With(RequestContextFactory.Instance.Create()).OfferCategories.ByCountry("US").Get();
```

<span data-ttu-id="c942e-113">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c942e-113">For an example, see the following:</span></span>

- <span data-ttu-id="c942e-114">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="c942e-114">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="c942e-115">Project: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="c942e-115">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="c942e-116">Classe: **partnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="c942e-116">Class: **PartnerSDK.FeatureSample**</span></span>

## <a name="rest-request"></a><span data-ttu-id="c942e-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c942e-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c942e-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c942e-118">Request syntax</span></span>

| <span data-ttu-id="c942e-119">Método</span><span class="sxs-lookup"><span data-stu-id="c942e-119">Method</span></span>  | <span data-ttu-id="c942e-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c942e-120">Request URI</span></span>                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="c942e-121">**Obter**</span><span class="sxs-lookup"><span data-stu-id="c942e-121">**GET**</span></span> | <span data-ttu-id="c942e-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/offercategorias?country={country-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c942e-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/offercategories?country={country-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="c942e-123">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="c942e-123">URI parameter</span></span>

<span data-ttu-id="c942e-124">Esta tabela lista os parâmetros de consulta necessários para obter as categorias de oferta.</span><span class="sxs-lookup"><span data-stu-id="c942e-124">This table lists the required query parameters to get the offer categories.</span></span>

| <span data-ttu-id="c942e-125">Nome</span><span class="sxs-lookup"><span data-stu-id="c942e-125">Name</span></span>           | <span data-ttu-id="c942e-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="c942e-126">Type</span></span>       | <span data-ttu-id="c942e-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="c942e-127">Required</span></span> | <span data-ttu-id="c942e-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="c942e-128">Description</span></span>            |
|----------------|------------|----------|------------------------|
| <span data-ttu-id="c942e-129">**país id**</span><span class="sxs-lookup"><span data-stu-id="c942e-129">**country-id**</span></span> | <span data-ttu-id="c942e-130">**string**</span><span class="sxs-lookup"><span data-stu-id="c942e-130">**string**</span></span> | <span data-ttu-id="c942e-131">Y</span><span class="sxs-lookup"><span data-stu-id="c942e-131">Y</span></span>        | <span data-ttu-id="c942e-132">O ID do país/região.</span><span class="sxs-lookup"><span data-stu-id="c942e-132">The country/region ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c942e-133">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c942e-133">Request headers</span></span>

<span data-ttu-id="c942e-134">É necessário **um local formatoformado** como uma corda.</span><span class="sxs-lookup"><span data-stu-id="c942e-134">A **locale-id** formatted as a string is required.</span></span>

<span data-ttu-id="c942e-135">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c942e-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c942e-136">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="c942e-136">Request body</span></span>

<span data-ttu-id="c942e-137">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c942e-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c942e-138">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c942e-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offercategories?country=<country-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fb54bd5-a4c3-4fac-955f-9b6e3436d606
MS-CorrelationId: 47882653-eaed-4a2e-a552-1070a3fa1089
X-Locale: <locale-id>
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="c942e-139">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c942e-139">REST response</span></span>

<span data-ttu-id="c942e-140">Se for bem sucedido, este método devolve uma coleção de recursos **da OfferCategory** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="c942e-140">If successful, this method returns a collection of **OfferCategory** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c942e-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c942e-141">Response success and error codes</span></span>

<span data-ttu-id="c942e-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c942e-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c942e-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c942e-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c942e-144">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c942e-144">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c942e-145">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="c942e-145">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1184
Content-Type: application/json
MS-CorrelationId: 47882653-eaed-4a2e-a552-1070a3fa1089
MS-RequestId: 4fb54bd5-a4c3-4fac-955f-9b6e3436d606
Date: Thu, 26 Nov 2015 00:07:10 GMT

{
    "totalCount": 4,
    "items": [{
        "id": "Enterprise_Key",
        "name": "Enterprise",
        "rank": 20,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    {
        "id": "SmallBusiness_Key",
        "name": "SmallBusiness",
        "rank": 30,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    {
        "id": "Government_Key",
        "name": "Government",
        "rank": 40,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    {
        "id": "Internal_Key",
        "name": "Internal",
        "rank": 100,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
