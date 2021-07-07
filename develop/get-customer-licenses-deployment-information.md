---
title: Obter informações de implementação de licenças do cliente
description: Como obter insights de implementação de licenças para um cliente específico.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 91fe9da185aa59025d4dc8263257b207edb4a5be
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446467"
---
# <a name="get-customer-licenses-deployment-information"></a><span data-ttu-id="e8898-103">Obter informações de implementação de licenças do cliente</span><span class="sxs-lookup"><span data-stu-id="e8898-103">Get customer licenses deployment information</span></span>

<span data-ttu-id="e8898-104">Como obter insights de implementação de licenças para um cliente específico.</span><span class="sxs-lookup"><span data-stu-id="e8898-104">How to get licenses deployment insights for a specific customer.</span></span>

> [!NOTE]
> <span data-ttu-id="e8898-105">Este cenário é substituído pela [Obter informações de implementação de licenças](get-licenses-deployment-information.md).</span><span class="sxs-lookup"><span data-stu-id="e8898-105">This scenario is superceded by [Get licenses deployment information](get-licenses-deployment-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e8898-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e8898-106">Prerequisites</span></span>

<span data-ttu-id="e8898-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e8898-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e8898-108">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="e8898-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="e8898-109">C\#</span><span class="sxs-lookup"><span data-stu-id="e8898-109">C\#</span></span>

<span data-ttu-id="e8898-110">Para obter dados agregados sobre a implementação de um cliente especificado, ligue primeiro para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e8898-110">To retrieve aggregated data on deployment for a specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="e8898-111">Em seguida, obtenha uma interface para operações de recolha de análise ao nível do cliente a partir da propriedade [**Analytics.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics)</span><span class="sxs-lookup"><span data-stu-id="e8898-111">Then get an interface to customer level analytics collection operations from the [**Analytics**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics) property.</span></span> <span data-ttu-id="e8898-112">Em seguida, recupere uma interface para a recolha de análise de licenças de nível de cliente da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses)</span><span class="sxs-lookup"><span data-stu-id="e8898-112">Next, retrieve an interface to the customer level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses) property.</span></span> <span data-ttu-id="e8898-113">Por fim, ligue para o método [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) para obter os dados agregados sobre a implementação de licenças.</span><span class="sxs-lookup"><span data-stu-id="e8898-113">Finally, call the [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses deployment.</span></span> <span data-ttu-id="e8898-114">Se o método for bem sucedido, obterá uma coleção de [**objetos CustomerLicensesDeploymentInsights.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesdeploymentinsights)</span><span class="sxs-lookup"><span data-stu-id="e8898-114">If the method succeeds, you'll get a collection of [**CustomerLicensesDeploymentInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesdeploymentinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

var customerLicensesDeploymentAnalytics = partnerOperations.Customers.ById(customerIdToRetrieve).Analytics.Licenses.Deployment.Get();
```

## <a name="rest-request"></a><span data-ttu-id="e8898-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="e8898-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e8898-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8898-116">Request syntax</span></span>

| <span data-ttu-id="e8898-117">Método</span><span class="sxs-lookup"><span data-stu-id="e8898-117">Method</span></span>  | <span data-ttu-id="e8898-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="e8898-118">Request URI</span></span>                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e8898-119">**Obter**</span><span class="sxs-lookup"><span data-stu-id="e8898-119">**GET**</span></span> | <span data-ttu-id="e8898-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/analytics/licenses/deployment HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e8898-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/analytics/licenses/deployment HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e8898-121">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="e8898-121">URI parameter</span></span>

<span data-ttu-id="e8898-122">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e8898-122">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="e8898-123">Nome</span><span class="sxs-lookup"><span data-stu-id="e8898-123">Name</span></span>        | <span data-ttu-id="e8898-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="e8898-124">Type</span></span> | <span data-ttu-id="e8898-125">Necessário</span><span class="sxs-lookup"><span data-stu-id="e8898-125">Required</span></span> | <span data-ttu-id="e8898-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8898-126">Description</span></span>                                                |
|-------------|------|----------|------------------------------------------------------------|
| <span data-ttu-id="e8898-127">id cliente</span><span class="sxs-lookup"><span data-stu-id="e8898-127">customer-id</span></span> | <span data-ttu-id="e8898-128">guid</span><span class="sxs-lookup"><span data-stu-id="e8898-128">guid</span></span> | <span data-ttu-id="e8898-129">Yes</span><span class="sxs-lookup"><span data-stu-id="e8898-129">Yes</span></span>      | <span data-ttu-id="e8898-130">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="e8898-130">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e8898-131">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="e8898-131">Request headers</span></span>

<span data-ttu-id="e8898-132">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e8898-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e8898-133">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="e8898-133">Request body</span></span>

<span data-ttu-id="e8898-134">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e8898-134">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e8898-135">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e8898-135">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/analytics/licenses/deployment HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b01b8759-4dbe-4605-adb7-e5839a796c33
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="e8898-136">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="e8898-136">REST response</span></span>

<span data-ttu-id="e8898-137">Se for bem sucedido, o organismo de resposta contém uma coleção de [recursos CustomerLicensesDeploymentInsights](analytics-resources.md#customerlicensesdeploymentinsights) que fornecem informações sobre as licenças implementadas.</span><span class="sxs-lookup"><span data-stu-id="e8898-137">If successful, the response body contains a collection of [CustomerLicensesDeploymentInsights](analytics-resources.md#customerlicensesdeploymentinsights) resources that provide information about the licenses deployed.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e8898-138">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="e8898-138">Response success and error codes</span></span>

<span data-ttu-id="e8898-139">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="e8898-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e8898-140">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="e8898-140">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e8898-141">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="e8898-141">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e8898-142">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e8898-142">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1012
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
MS-RequestId: b01b8759-4dbe-4605-adb7-e5839a796c33
MS-CV: deEp2Wy6DUitMCYA.0
MS-ServerId: 102030524
Date: Wed, 15 Mar 2017 01:19:18 GMT

{
    "totalCount": 3,
    "items": [{
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "OFFICE 365 BUSINESS ESSENTIALS",
            "licensesDeployed": 0,
            "deploymentPercent": 0.0,
            "licensesSold": 1,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesDeploymentInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE (PLAN 1)",
            "licensesDeployed": 0,
            "deploymentPercent": 0.0,
            "licensesSold": 5,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesDeploymentInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE ARCHIVING FOR EXCHANGE ONLINE",
            "licensesDeployed": 0,
            "deploymentPercent": 0.0,
            "licensesSold": 2,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesDeploymentInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
