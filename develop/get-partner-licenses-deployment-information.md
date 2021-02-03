---
title: Obter informações de implementação de licenças do parceiro
description: Como obter licenças de parceiros de informação agregada para incluir todos os clientes.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 229f63d4df4f59cd0fde2bd0fc5e3f10cf6b25c0
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769836"
---
# <a name="get-partner-licenses-deployment-information"></a><span data-ttu-id="70ffa-103">Obter informações de implementação de licenças do parceiro</span><span class="sxs-lookup"><span data-stu-id="70ffa-103">Get partner licenses deployment information</span></span>

<span data-ttu-id="70ffa-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="70ffa-104">**Applies To**</span></span>

- <span data-ttu-id="70ffa-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="70ffa-105">Partner Center</span></span>

<span data-ttu-id="70ffa-106">Como obter licenças de parceiros de informação agregada para incluir todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="70ffa-106">How to get partner licenses deployment information aggregated to include all customers.</span></span>

> [!NOTE]
> <span data-ttu-id="70ffa-107">Este cenário é substituído pela [Obter informações de implementação de licenças](get-licenses-deployment-information.md).</span><span class="sxs-lookup"><span data-stu-id="70ffa-107">This scenario is superceded by [Get licenses deployment information](get-licenses-deployment-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70ffa-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="70ffa-108">Prerequisites</span></span>

<span data-ttu-id="70ffa-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="70ffa-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="70ffa-110">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="70ffa-110">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="70ffa-111">C\#</span><span class="sxs-lookup"><span data-stu-id="70ffa-111">C\#</span></span>

<span data-ttu-id="70ffa-112">Para obter dados agregados na implementação de licenças, primeiro obtenha uma interface para operações de recolha de análise de nível de parceiro a partir da propriedade [**IAggregatePartner.Analytics.**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics)</span><span class="sxs-lookup"><span data-stu-id="70ffa-112">To retrieve aggregated data on licenses deployment, first get an interface to partner level analytics collection operations from the [**IAggregatePartner.Analytics**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) property.</span></span> <span data-ttu-id="70ffa-113">Em seguida, recupere uma interface para o nível de parceiro licenças de recolha de análise a partir da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses)</span><span class="sxs-lookup"><span data-stu-id="70ffa-113">Then retrieve an interface to the partner level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) property.</span></span> <span data-ttu-id="70ffa-114">Por fim, ligue para o método [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) para obter os dados agregados sobre a implementação de licenças.</span><span class="sxs-lookup"><span data-stu-id="70ffa-114">Finally, call the [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses deployment.</span></span> <span data-ttu-id="70ffa-115">Se o método for bem sucedido, obterá uma coleção de [**objetos PartnerLicensesDeploymentInsights.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesdeploymentinsights)</span><span class="sxs-lookup"><span data-stu-id="70ffa-115">If the method succeeds you'll get a collection of [**PartnerLicensesDeploymentInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesdeploymentinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var partnerLicensesDeploymentAnalytics = partnerOperations.Analytics.Licenses.Deployment.Get();
```

## <a name="rest-request"></a><span data-ttu-id="70ffa-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="70ffa-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="70ffa-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="70ffa-117">Request syntax</span></span>

| <span data-ttu-id="70ffa-118">Método</span><span class="sxs-lookup"><span data-stu-id="70ffa-118">Method</span></span>  | <span data-ttu-id="70ffa-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="70ffa-119">Request URI</span></span>                                                                           |
|---------|---------------------------------------------------------------------------------------|
| <span data-ttu-id="70ffa-120">**Obter**</span><span class="sxs-lookup"><span data-stu-id="70ffa-120">**GET**</span></span> | <span data-ttu-id="70ffa-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/deployment HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="70ffa-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/deployment HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="70ffa-122">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="70ffa-122">Request headers</span></span>

<span data-ttu-id="70ffa-123">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="70ffa-123">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="70ffa-124">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="70ffa-124">Request body</span></span>

<span data-ttu-id="70ffa-125">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="70ffa-125">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="70ffa-126">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="70ffa-126">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/analytics/licenses/deployment HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 25b6edd5-1f53-456b-b48c-c64f60ec2dda
MS-CorrelationId: 6492b9d6-5629-429b-934c-040b1946e760
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="70ffa-127">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="70ffa-127">REST response</span></span>

<span data-ttu-id="70ffa-128">Se for bem sucedido, o organismo de resposta contém uma coleção de [recursos PartnerLicensesDeploymentInsights](analytics-resources.md#partnerlicensesdeploymentinsights) que fornecem informações sobre as licenças implementadas.</span><span class="sxs-lookup"><span data-stu-id="70ffa-128">If successful, the response body contains a collection of [PartnerLicensesDeploymentInsights](analytics-resources.md#partnerlicensesdeploymentinsights) resources that provide information about the licenses deployed.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="70ffa-129">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="70ffa-129">Response success and error codes</span></span>

<span data-ttu-id="70ffa-130">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="70ffa-130">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="70ffa-131">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="70ffa-131">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="70ffa-132">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="70ffa-132">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="70ffa-133">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="70ffa-133">Response example</span></span>

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
