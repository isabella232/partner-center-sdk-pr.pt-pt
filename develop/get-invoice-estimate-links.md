---
title: Obter ligações de estimativa da fatura
description: Você pode obter uma coleção de links de estimativa para consultar detalhes da linha de reconciliação.
ms.date: 09/24/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.assetid: ''
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 719becd3fac5605c4ad48ab86d483ba7903d65d8
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549149"
---
# <a name="get-invoice-estimate-links"></a><span data-ttu-id="66faa-103">Obter ligações de estimativa da fatura</span><span class="sxs-lookup"><span data-stu-id="66faa-103">Get invoice estimate links</span></span>

<span data-ttu-id="66faa-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="66faa-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="66faa-105">Você pode obter links de estimativa para ajudar a consultar detalhes para itens de linha de reconciliação não faturados.</span><span class="sxs-lookup"><span data-stu-id="66faa-105">You can get estimate links to help query details for unbilled reconciliation line items.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="66faa-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="66faa-106">Prerequisites</span></span>

- <span data-ttu-id="66faa-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="66faa-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="66faa-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="66faa-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="66faa-109">Um identificador de fatura.</span><span class="sxs-lookup"><span data-stu-id="66faa-109">An invoice identifier.</span></span> <span data-ttu-id="66faa-110">Isto identifica a fatura para a recuperação dos itens de linha.</span><span class="sxs-lookup"><span data-stu-id="66faa-110">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="66faa-111">C\#</span><span class="sxs-lookup"><span data-stu-id="66faa-111">C\#</span></span>

<span data-ttu-id="66faa-112">O código de exemplo a seguir mostra como pode obter as ligações de estimativa para consultar itens de linha não bico para uma determinada moeda.</span><span class="sxs-lookup"><span data-stu-id="66faa-112">The following example code shows how you can get the estimate links to query unbilled line items for a given currency.</span></span> <span data-ttu-id="66faa-113">A resposta contém as ligações de estimativa para cada período (por exemplo, o mês atual e anterior).</span><span class="sxs-lookup"><span data-stu-id="66faa-113">The response contains the estimate links for each period (for example, the current and previous month).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string curencyCode;

 // all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
 IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// read estimate links for currencycode
var estimateLinks = scopedPartnerOperations.Invoices.Estimates.Links.ByCurrency(curencyCode).Get();
```

<span data-ttu-id="66faa-114">Para um exemplo semelhante, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="66faa-114">For a similar example, see the following:</span></span>

- <span data-ttu-id="66faa-115">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="66faa-115">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="66faa-116">Project: **Amostras SDK do Centro Parceiro**</span><span class="sxs-lookup"><span data-stu-id="66faa-116">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="66faa-117">Classe: **GetEstimatesLinks.cs**</span><span class="sxs-lookup"><span data-stu-id="66faa-117">Class: **GetEstimatesLinks.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="66faa-118">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="66faa-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="66faa-119">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="66faa-119">Request syntax</span></span>

| <span data-ttu-id="66faa-120">Método</span><span class="sxs-lookup"><span data-stu-id="66faa-120">Method</span></span>  | <span data-ttu-id="66faa-121">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="66faa-121">Request URI</span></span>                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="66faa-122">**Obter**</span><span class="sxs-lookup"><span data-stu-id="66faa-122">**GET**</span></span> | <span data-ttu-id="66faa-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/estimativas/links?currencycode={currencycode} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="66faa-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/estimates/links?currencycode={currencycode} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="66faa-124">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="66faa-124">URI parameters</span></span>

<span data-ttu-id="66faa-125">Utilize o seguinte URI e parâmetro de consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="66faa-125">Use the following URI and query parameter when creating the request.</span></span>

| <span data-ttu-id="66faa-126">Nome</span><span class="sxs-lookup"><span data-stu-id="66faa-126">Name</span></span>                   | <span data-ttu-id="66faa-127">Tipo</span><span class="sxs-lookup"><span data-stu-id="66faa-127">Type</span></span>   | <span data-ttu-id="66faa-128">Necessário</span><span class="sxs-lookup"><span data-stu-id="66faa-128">Required</span></span> | <span data-ttu-id="66faa-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="66faa-129">Description</span></span>                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| <span data-ttu-id="66faa-130">currencyCode</span><span class="sxs-lookup"><span data-stu-id="66faa-130">currencyCode</span></span>           | <span data-ttu-id="66faa-131">string</span><span class="sxs-lookup"><span data-stu-id="66faa-131">string</span></span> | <span data-ttu-id="66faa-132">Yes</span><span class="sxs-lookup"><span data-stu-id="66faa-132">Yes</span></span>      | <span data-ttu-id="66faa-133">O código cambial para os itens de linha não bico.</span><span class="sxs-lookup"><span data-stu-id="66faa-133">The currency code for the unbilled line items.</span></span>                    |

### <a name="request-headers"></a><span data-ttu-id="66faa-134">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="66faa-134">Request headers</span></span>

<span data-ttu-id="66faa-135">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="66faa-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="66faa-136">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="66faa-136">Request body</span></span>

<span data-ttu-id="66faa-137">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="66faa-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="66faa-138">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="66faa-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/estimates/links?currencycode=usd HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="66faa-139">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="66faa-139">REST response</span></span>

<span data-ttu-id="66faa-140">Se for bem sucedida, a resposta contém os links para recuperar estimativas não mediadas.</span><span class="sxs-lookup"><span data-stu-id="66faa-140">If successful, the response contains the links to retrieve unbilled estimates.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="66faa-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="66faa-141">Response success and error codes</span></span>

<span data-ttu-id="66faa-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="66faa-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="66faa-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="66faa-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="66faa-144">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="66faa-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="66faa-145">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="66faa-145">Response example</span></span>

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
