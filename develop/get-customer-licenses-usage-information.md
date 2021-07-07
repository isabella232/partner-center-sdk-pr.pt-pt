---
title: Obter informações de utilização de licenças do cliente
description: Como obter insights de utilização de licenças para um cliente específico.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: cfec12d37ce4f5f50baad57bfd45770388f8a2dc
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446433"
---
# <a name="get-customer-licenses-usage-information"></a><span data-ttu-id="38b92-103">Obter informações de utilização de licenças do cliente</span><span class="sxs-lookup"><span data-stu-id="38b92-103">Get customer licenses usage information</span></span>

<span data-ttu-id="38b92-104">Como obter insights de implementação de licenças para um cliente específico.</span><span class="sxs-lookup"><span data-stu-id="38b92-104">How to get licenses deployment insights for a specific customer.</span></span>

> [!NOTE]
> <span data-ttu-id="38b92-105">Este cenário é substituído pela [Obter informações de utilização de licenças](get-licenses-usage-information.md).</span><span class="sxs-lookup"><span data-stu-id="38b92-105">This scenario is superceded by [Get licenses usage information](get-licenses-usage-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="38b92-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="38b92-106">Prerequisites</span></span>

<span data-ttu-id="38b92-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="38b92-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="38b92-108">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="38b92-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="38b92-109">C\#</span><span class="sxs-lookup"><span data-stu-id="38b92-109">C\#</span></span>

<span data-ttu-id="38b92-110">Para obter dados agregados sobre a implementação de um cliente especificado, ligue primeiro para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="38b92-110">To retrieve aggregated data on deployment for a specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="38b92-111">Em seguida, obtenha uma interface para operações de recolha de análise ao nível do cliente a partir da propriedade [**Analytics.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics)</span><span class="sxs-lookup"><span data-stu-id="38b92-111">Then get an interface to customer level analytics collection operations from the [**Analytics**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics) property.</span></span> <span data-ttu-id="38b92-112">Em seguida, recupere uma interface para a recolha de análise de licenças de nível de cliente da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses)</span><span class="sxs-lookup"><span data-stu-id="38b92-112">Next, retrieve an interface to the customer level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses) property.</span></span> <span data-ttu-id="38b92-113">Por fim, ligue para o método [**Usage.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) para obter os dados agregados sobre o uso das licenças.</span><span class="sxs-lookup"><span data-stu-id="38b92-113">Finally, call the [**Usage.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses usage.</span></span> <span data-ttu-id="38b92-114">Se o método for bem sucedido, obterá uma coleção de [**objetos CustomerLicensesUsageInsights.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesusageinsights)</span><span class="sxs-lookup"><span data-stu-id="38b92-114">If the method succeeds, you'll get a collection of [**CustomerLicensesUsageInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesusageinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

var customerLicensesDeploymentAnalytics = partnerOperations.Customers.ById(customerIdToRetrieve).Analytics.Licenses.Usage.Get();
```

## <a name="rest-request"></a><span data-ttu-id="38b92-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="38b92-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="38b92-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="38b92-116">Request syntax</span></span>

| <span data-ttu-id="38b92-117">Método</span><span class="sxs-lookup"><span data-stu-id="38b92-117">Method</span></span>  | <span data-ttu-id="38b92-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="38b92-118">Request URI</span></span>                                                                                              |
|---------|----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="38b92-119">**Obter**</span><span class="sxs-lookup"><span data-stu-id="38b92-119">**GET**</span></span> | <span data-ttu-id="38b92-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/analytics/licenses/usage HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="38b92-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/analytics/licenses/usage HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="38b92-121">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="38b92-121">URI parameter</span></span>

<span data-ttu-id="38b92-122">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="38b92-122">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="38b92-123">Nome</span><span class="sxs-lookup"><span data-stu-id="38b92-123">Name</span></span>        | <span data-ttu-id="38b92-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="38b92-124">Type</span></span> | <span data-ttu-id="38b92-125">Necessário</span><span class="sxs-lookup"><span data-stu-id="38b92-125">Required</span></span> | <span data-ttu-id="38b92-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="38b92-126">Description</span></span>                                                |
|-------------|------|----------|------------------------------------------------------------|
| <span data-ttu-id="38b92-127">id cliente</span><span class="sxs-lookup"><span data-stu-id="38b92-127">customer-id</span></span> | <span data-ttu-id="38b92-128">guid</span><span class="sxs-lookup"><span data-stu-id="38b92-128">guid</span></span> | <span data-ttu-id="38b92-129">Yes</span><span class="sxs-lookup"><span data-stu-id="38b92-129">Yes</span></span>      | <span data-ttu-id="38b92-130">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="38b92-130">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="38b92-131">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="38b92-131">Request headers</span></span>

<span data-ttu-id="38b92-132">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="38b92-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="38b92-133">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="38b92-133">Request body</span></span>

<span data-ttu-id="38b92-134">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="38b92-134">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="38b92-135">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="38b92-135">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/analytics/licenses/usage HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f657d2a8-9ed6-41b4-abfc-3cf4abebd62f
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="38b92-136">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="38b92-136">REST response</span></span>

<span data-ttu-id="38b92-137">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [CustomerLicensesUsageInsights](analytics-resources.md#customerlicensesusageinsights) que fornecem informações sobre o uso das licenças.</span><span class="sxs-lookup"><span data-stu-id="38b92-137">If successful, the response body contains a collection of [CustomerLicensesUsageInsights](analytics-resources.md#customerlicensesusageinsights) resources that provide information about licenses usage.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="38b92-138">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="38b92-138">Response success and error codes</span></span>

<span data-ttu-id="38b92-139">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="38b92-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="38b92-140">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="38b92-140">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="38b92-141">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="38b92-141">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="38b92-142">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="38b92-142">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1726
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
MS-RequestId: f657d2a8-9ed6-41b4-abfc-3cf4abebd62f
MS-CV: 0mufM0K1kEOoR7oI.0
MS-ServerId: 030020525
Date: Wed, 15 Mar 2017 01:19:58 GMT

{
    "totalCount": 5,
    "items": [{
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "OFFICE 365 BUSINESS ESSENTIALS",
            "licensesActive": 0,
            "licensesQualified": 1,
            "usagePercent": 0.0,
            "workloadName": "Exchange",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "OFFICE 365 BUSINESS ESSENTIALS",
            "licensesActive": 0,
            "licensesQualified": 1,
            "usagePercent": 0.0,
            "workloadName": "SharePoint",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "OFFICE 365 BUSINESS ESSENTIALS",
            "licensesActive": 0,
            "licensesQualified": 1,
            "usagePercent": 0.0,
            "workloadName": "Skype For Business",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE (PLAN 1)",
            "licensesActive": 0,
            "licensesQualified": 5,
            "usagePercent": 0.0,
            "workloadName": "Exchange",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE ARCHIVING FOR EXCHANGE ONLINE",
            "licensesActive": 0,
            "licensesQualified": 2,
            "usagePercent": 0.0,
            "workloadName": "Exchange",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
