---
title: Obter ligações de estimativa da fatura
description: Você pode obter uma coleção de links de estimativa para consultar detalhes da linha de reconciliação.
ms.date: 09/24/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.assetid: ''
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 10801cdb1f9d4f50a1f8fc86c2d0eaf8610ed68c
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769019"
---
# <a name="get-invoice-estimate-links"></a><span data-ttu-id="06b66-103">Obter ligações de estimativa da fatura</span><span class="sxs-lookup"><span data-stu-id="06b66-103">Get invoice estimate links</span></span>

<span data-ttu-id="06b66-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="06b66-104">**Applies to:**</span></span>

- <span data-ttu-id="06b66-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="06b66-105">Partner Center</span></span>
- <span data-ttu-id="06b66-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="06b66-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="06b66-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="06b66-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="06b66-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="06b66-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="06b66-109">Você pode obter links de estimativa para ajudar a consultar detalhes para itens de linha de reconciliação não faturados.</span><span class="sxs-lookup"><span data-stu-id="06b66-109">You can get estimate links to help query details for unbilled reconciliation line items.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="06b66-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="06b66-110">Prerequisites</span></span>

- <span data-ttu-id="06b66-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="06b66-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="06b66-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="06b66-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="06b66-113">Um identificador de fatura.</span><span class="sxs-lookup"><span data-stu-id="06b66-113">An invoice identifier.</span></span> <span data-ttu-id="06b66-114">Isto identifica a fatura para a recuperação dos itens de linha.</span><span class="sxs-lookup"><span data-stu-id="06b66-114">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="06b66-115">C\#</span><span class="sxs-lookup"><span data-stu-id="06b66-115">C\#</span></span>

<span data-ttu-id="06b66-116">O código de exemplo a seguir mostra como pode obter as ligações de estimativa para consultar itens de linha não bico para uma determinada moeda.</span><span class="sxs-lookup"><span data-stu-id="06b66-116">The following example code shows how you can get the estimate links to query unbilled line items for a given currency.</span></span> <span data-ttu-id="06b66-117">A resposta contém as ligações de estimativa para cada período (por exemplo, o mês atual e anterior).</span><span class="sxs-lookup"><span data-stu-id="06b66-117">The response contains the estimate links for each period (for example, the current and previous month).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string curencyCode;

 // all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
 IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// read estimate links for currencycode
var estimateLinks = scopedPartnerOperations.Invoices.Estimates.Links.ByCurrency(curencyCode).Get();
```

<span data-ttu-id="06b66-118">Para um exemplo semelhante, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="06b66-118">For a similar example, see the following:</span></span>

- <span data-ttu-id="06b66-119">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="06b66-119">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="06b66-120">Projeto: **Partner Center SDK Samples**</span><span class="sxs-lookup"><span data-stu-id="06b66-120">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="06b66-121">Classe: **GetEstimatesLinks.cs**</span><span class="sxs-lookup"><span data-stu-id="06b66-121">Class: **GetEstimatesLinks.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="06b66-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="06b66-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="06b66-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="06b66-123">Request syntax</span></span>

| <span data-ttu-id="06b66-124">Método</span><span class="sxs-lookup"><span data-stu-id="06b66-124">Method</span></span>  | <span data-ttu-id="06b66-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="06b66-125">Request URI</span></span>                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="06b66-126">**Obter**</span><span class="sxs-lookup"><span data-stu-id="06b66-126">**GET**</span></span> | <span data-ttu-id="06b66-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/estimativas/links?currencycode={currencycode} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="06b66-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/estimates/links?currencycode={currencycode} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="06b66-128">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="06b66-128">URI parameters</span></span>

<span data-ttu-id="06b66-129">Utilize o seguinte URI e parâmetro de consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="06b66-129">Use the following URI and query parameter when creating the request.</span></span>

| <span data-ttu-id="06b66-130">Nome</span><span class="sxs-lookup"><span data-stu-id="06b66-130">Name</span></span>                   | <span data-ttu-id="06b66-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="06b66-131">Type</span></span>   | <span data-ttu-id="06b66-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="06b66-132">Required</span></span> | <span data-ttu-id="06b66-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="06b66-133">Description</span></span>                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| <span data-ttu-id="06b66-134">currencyCode</span><span class="sxs-lookup"><span data-stu-id="06b66-134">currencyCode</span></span>           | <span data-ttu-id="06b66-135">string</span><span class="sxs-lookup"><span data-stu-id="06b66-135">string</span></span> | <span data-ttu-id="06b66-136">Sim</span><span class="sxs-lookup"><span data-stu-id="06b66-136">Yes</span></span>      | <span data-ttu-id="06b66-137">O código cambial para os itens de linha não bico.</span><span class="sxs-lookup"><span data-stu-id="06b66-137">The currency code for the unbilled line items.</span></span>                    |

### <a name="request-headers"></a><span data-ttu-id="06b66-138">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="06b66-138">Request headers</span></span>

<span data-ttu-id="06b66-139">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="06b66-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="06b66-140">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="06b66-140">Request body</span></span>

<span data-ttu-id="06b66-141">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="06b66-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="06b66-142">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="06b66-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/estimates/links?currencycode=usd HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="06b66-143">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="06b66-143">REST response</span></span>

<span data-ttu-id="06b66-144">Se for bem sucedida, a resposta contém os links para recuperar estimativas não mediadas.</span><span class="sxs-lookup"><span data-stu-id="06b66-144">If successful, the response contains the links to retrieve unbilled estimates.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="06b66-145">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="06b66-145">Response success and error codes</span></span>

<span data-ttu-id="06b66-146">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="06b66-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="06b66-147">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="06b66-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="06b66-148">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="06b66-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="06b66-149">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="06b66-149">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 80EAA055-B5D3-4D88-BFE8-924A3F706462
MS-RequestId: 1b18689e-3fe3-4fdb-d09e-39d13941390b
X-Locale: en-US
X-SourceFiles: =?UTF-8?B?RDpcU291cmNlc1xSUEUuUGFydG5lci5TZXJ2aWNlLkJpbGxpbmdTZXJ2aWNlXHYxLjFcV2ViQXBpc1xCaWxsaW5nU2VydmljZS5WMi5XZWJcdjFcaW52b2ljZXNcZXN0aW1hdGVzXGxpbmtz?=
X-Powered-By: ASP.NET
Date: Thu, 14 Mar 2019 18:15:06 GMT
Content-Length: 1857

{
  "totalCount": 4,
  "items": [
    {
      "type": "daily_rated_usage",
      "title": "Daily rated usage unbilled",
      "description": "This invoice line items includes unbilled consumption based data only.",
      "period": "Current",
      "link": {
        "uri": "/invoices/unbilled/lineitems?provider=Marketplace&invoicelineitemtype=UsageLineItems&currencycode=USD&period=current&size=2000",
        "method": "GET",
        "headers": []
      }
    },
    {
      "type": "daily_rated_usage",
      "title": "Daily rated usage unbilled",
      "description": "This invoice line items includes unbilled consumption based data only.",
      "period": "Previous",
      "link": {
        "uri": "/invoices/unbilled/lineitems?provider=Marketplace&invoicelineitemtype=UsageLineItems&currencycode=USD&period=previous&size=2000",
        "method": "GET",
        "headers": []
      }
    },
    {
      "type": "non_consumption",
      "title": "Unbilled reconciliation line items",
      "description": "This includes reconciliation line items for unbilled data only.",
      "period": "Current",
      "link": {
        "uri": "/invoices/unbilled/lineitems?provider=all&invoicelineitemtype=billinglineitems&currencycode=USD&period=current&size=2000",
        "method": "GET",
        "headers": []
      }
    },
    {
      "type": "non_consumption",
      "title": "Unbilled reconciliation line items",
      "description": "This includes reconciliation line items for unbilled data only.",
      "period": "Previous",
      "link": {
        "uri": "/invoices/unbilled/lineitems?provider=all&invoicelineitemtype=billinglineitems&currencycode=USD&period=previous&size=2000",
        "method": "GET",
        "headers": []
      }
    }
  ],
  "attributes": {
    "objectType": "Collection"
 }
}
```
