---
title: Obter informações de implementação de licenças do parceiro
description: Como obter licenças de parceiros de informação agregada para incluir todos os clientes.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2464242fc6dc4e7464511eac5d4197630e22fac0
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445989"
---
# <a name="get-partner-licenses-deployment-information"></a><span data-ttu-id="27e4a-103">Obter informações de implementação de licenças do parceiro</span><span class="sxs-lookup"><span data-stu-id="27e4a-103">Get partner licenses deployment information</span></span>

<span data-ttu-id="27e4a-104">Como obter licenças de parceiros de informação agregada para incluir todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="27e4a-104">How to get partner licenses deployment information aggregated to include all customers.</span></span>

> [!NOTE]
> <span data-ttu-id="27e4a-105">Este cenário é substituído pela [Obter informações de implementação de licenças](get-licenses-deployment-information.md).</span><span class="sxs-lookup"><span data-stu-id="27e4a-105">This scenario is superceded by [Get licenses deployment information](get-licenses-deployment-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27e4a-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="27e4a-106">Prerequisites</span></span>

<span data-ttu-id="27e4a-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="27e4a-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="27e4a-108">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="27e4a-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="27e4a-109">C\#</span><span class="sxs-lookup"><span data-stu-id="27e4a-109">C\#</span></span>

<span data-ttu-id="27e4a-110">Para obter dados agregados na implementação de licenças, primeiro obtenha uma interface para operações de recolha de análise de nível de parceiro a partir da propriedade [**IAggregatePartner.Analytics.**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics)</span><span class="sxs-lookup"><span data-stu-id="27e4a-110">To retrieve aggregated data on licenses deployment, first get an interface to partner level analytics collection operations from the [**IAggregatePartner.Analytics**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) property.</span></span> <span data-ttu-id="27e4a-111">Em seguida, recupere uma interface para o nível de parceiro licenças de recolha de análise a partir da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses)</span><span class="sxs-lookup"><span data-stu-id="27e4a-111">Then retrieve an interface to the partner level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) property.</span></span> <span data-ttu-id="27e4a-112">Por fim, ligue para o método [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) para obter os dados agregados sobre a implementação de licenças.</span><span class="sxs-lookup"><span data-stu-id="27e4a-112">Finally, call the [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses deployment.</span></span> <span data-ttu-id="27e4a-113">Se o método for bem sucedido, obterá uma coleção de [**objetos PartnerLicensesDeploymentInsights.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesdeploymentinsights)</span><span class="sxs-lookup"><span data-stu-id="27e4a-113">If the method succeeds, you'll get a collection of [**PartnerLicensesDeploymentInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesdeploymentinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var partnerLicensesDeploymentAnalytics = partnerOperations.Analytics.Licenses.Deployment.Get();
```

## <a name="rest-request"></a><span data-ttu-id="27e4a-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="27e4a-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="27e4a-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="27e4a-115">Request syntax</span></span>

| <span data-ttu-id="27e4a-116">Método</span><span class="sxs-lookup"><span data-stu-id="27e4a-116">Method</span></span>  | <span data-ttu-id="27e4a-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="27e4a-117">Request URI</span></span>                                                                           |
|---------|---------------------------------------------------------------------------------------|
| <span data-ttu-id="27e4a-118">**Obter**</span><span class="sxs-lookup"><span data-stu-id="27e4a-118">**GET**</span></span> | <span data-ttu-id="27e4a-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/deployment HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="27e4a-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/deployment HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="27e4a-120">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="27e4a-120">Request headers</span></span>

<span data-ttu-id="27e4a-121">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="27e4a-121">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="27e4a-122">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="27e4a-122">Request body</span></span>

<span data-ttu-id="27e4a-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="27e4a-123">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="27e4a-124">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="27e4a-124">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/analytics/licenses/deployment HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 25b6edd5-1f53-456b-b48c-c64f60ec2dda
MS-CorrelationId: 6492b9d6-5629-429b-934c-040b1946e760
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="27e4a-125">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="27e4a-125">REST response</span></span>

<span data-ttu-id="27e4a-126">Se for bem sucedido, o organismo de resposta contém uma coleção de [recursos PartnerLicensesDeploymentInsights](analytics-resources.md#partnerlicensesdeploymentinsights) que fornecem informações sobre as licenças implementadas.</span><span class="sxs-lookup"><span data-stu-id="27e4a-126">If successful, the response body contains a collection of [PartnerLicensesDeploymentInsights](analytics-resources.md#partnerlicensesdeploymentinsights) resources that provide information about the licenses deployed.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="27e4a-127">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="27e4a-127">Response success and error codes</span></span>

<span data-ttu-id="27e4a-128">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="27e4a-128">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="27e4a-129">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="27e4a-129">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="27e4a-130">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="27e4a-130">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="27e4a-131">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="27e4a-131">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 487
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 6492b9d6-5629-429b-934c-040b1946e760
MS-RequestId: 25b6edd5-1f53-456b-b48c-c64f60ec2dda
MS-CV: f0trvmq8mEScHcFS.0
MS-ServerId: 102030524
Date: Tue, 14 Mar 2017 17:55:01 GMT

{
    "totalCount": 2,
    "items": [{
            "proratedDeploymentPercent": 0.0,
            "licensesSold": 343,
            "processedDateTime": "2017-03-10T00:00:00+00:00",
            "serviceName": "crm",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesDeploymentInsights"
            }
        }, {
            "proratedDeploymentPercent": 1.0,
            "licensesSold": 4464,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesDeploymentInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
