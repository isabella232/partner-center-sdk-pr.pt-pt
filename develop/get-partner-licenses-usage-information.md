---
title: Obter informações de utilização de licenças do parceiro
description: Como obter licenças de parceiros informações de utilização agregadas para incluir todos os clientes.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f3d05d61ac4f2c90b0d8a4bfd93fe24e94bd5c1b
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445600"
---
# <a name="get-partner-licenses-usage-information"></a><span data-ttu-id="3abd6-103">Obter informações de utilização de licenças do parceiro</span><span class="sxs-lookup"><span data-stu-id="3abd6-103">Get partner licenses usage information</span></span>

<span data-ttu-id="3abd6-104">Como obter licenças de parceiros informações de utilização agregadas para incluir todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="3abd6-104">How to get partner licenses usage information aggregated to include all customers.</span></span>

> [!NOTE]
> <span data-ttu-id="3abd6-105">Este cenário é substituído pela [Obter informações de utilização de licenças](get-licenses-usage-information.md).</span><span class="sxs-lookup"><span data-stu-id="3abd6-105">This scenario is superceded by [Get licenses usage information](get-licenses-usage-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3abd6-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3abd6-106">Prerequisites</span></span>

<span data-ttu-id="3abd6-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3abd6-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3abd6-108">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="3abd6-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="3abd6-109">C\#</span><span class="sxs-lookup"><span data-stu-id="3abd6-109">C\#</span></span>

<span data-ttu-id="3abd6-110">Para obter dados agregados na implementação de licenças, primeiro obtenha uma interface para operações de recolha de análise de nível de parceiro a partir da propriedade [**IAggregatePartner.Analytics.**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics)</span><span class="sxs-lookup"><span data-stu-id="3abd6-110">To retrieve aggregated data on licenses deployment, first get an interface to partner level analytics collection operations from the [**IAggregatePartner.Analytics**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) property.</span></span> <span data-ttu-id="3abd6-111">Em seguida, recupere uma interface para o nível de parceiro licenças de recolha de análise a partir da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses)</span><span class="sxs-lookup"><span data-stu-id="3abd6-111">Then retrieve an interface to the partner level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) property.</span></span> <span data-ttu-id="3abd6-112">Por fim, ligue para o método [**Usage.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) para obter os dados agregados sobre o uso das licenças.</span><span class="sxs-lookup"><span data-stu-id="3abd6-112">Finally, call the [**Usage.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses usage.</span></span> <span data-ttu-id="3abd6-113">Se o método for bem sucedido, obterá uma coleção de [**objetos PartnerLicensesUsageInsights.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesusageinsights)</span><span class="sxs-lookup"><span data-stu-id="3abd6-113">If the method succeeds, you'll get a collection of [**PartnerLicensesUsageInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesusageinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var partnerLicensesUsageAnalytics = partnerOperations.Analytics.Licenses.Usage.Get();
```

## <a name="rest-request"></a><span data-ttu-id="3abd6-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="3abd6-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3abd6-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="3abd6-115">Request syntax</span></span>

| <span data-ttu-id="3abd6-116">Método</span><span class="sxs-lookup"><span data-stu-id="3abd6-116">Method</span></span>  | <span data-ttu-id="3abd6-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="3abd6-117">Request URI</span></span>                                                                      |
|---------|----------------------------------------------------------------------------------|
| <span data-ttu-id="3abd6-118">**Obter**</span><span class="sxs-lookup"><span data-stu-id="3abd6-118">**GET**</span></span> | <span data-ttu-id="3abd6-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/usage HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="3abd6-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/usage HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="3abd6-120">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="3abd6-120">Request headers</span></span>

<span data-ttu-id="3abd6-121">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3abd6-121">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3abd6-122">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="3abd6-122">Request body</span></span>

<span data-ttu-id="3abd6-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3abd6-123">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="3abd6-124">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="3abd6-124">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/analytics/licenses/usage HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 6b588e9b-1d02-471a-bce2-79374497c24e
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="3abd6-125">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="3abd6-125">REST response</span></span>

<span data-ttu-id="3abd6-126">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [PartnerLicensesUsageInsights](analytics-resources.md#partnerlicensesusageinsights) que fornecem informações sobre as licenças utilizadas.</span><span class="sxs-lookup"><span data-stu-id="3abd6-126">If successful, the response body contains a collection of [PartnerLicensesUsageInsights](analytics-resources.md#partnerlicensesusageinsights) resources that provide information about the licenses used.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3abd6-127">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="3abd6-127">Response success and error codes</span></span>

<span data-ttu-id="3abd6-128">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="3abd6-128">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3abd6-129">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="3abd6-129">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3abd6-130">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="3abd6-130">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3abd6-131">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="3abd6-131">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1156
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
MS-RequestId: 6b588e9b-1d02-471a-bce2-79374497c24e
MS-CV: wk0/vjugzEe0Z9cv.0
MS-ServerId: 101112012
Date: Wed, 15 Mar 2017 01:18:26 GMT

{
    "totalCount": 5,
    "items": [{
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "Microsoft Dynamics CRM",
            "processedDateTime": "2017-03-10T00:00:00+00:00",
            "serviceName": "crm",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }, {
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "SharePoint",
            "processedDateTime": "2017-03-10T00:00:00+00:00",
            "serviceName": "crm",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }, {
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "Exchange",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }, {
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "SharePoint",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }, {
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "Skype For Business",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
