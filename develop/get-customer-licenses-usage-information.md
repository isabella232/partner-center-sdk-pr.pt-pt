---
title: Obter informações de utilização de licenças do cliente
description: Como obter insights de utilização de licenças para um cliente específico.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 1ee19e458ec65faa21034dd230b5388f7de981b2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769709"
---
# <a name="get-customer-licenses-usage-information"></a><span data-ttu-id="e4f22-103">Obter informações de utilização de licenças do cliente</span><span class="sxs-lookup"><span data-stu-id="e4f22-103">Get customer licenses usage information</span></span>

<span data-ttu-id="e4f22-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="e4f22-104">**Applies To**</span></span>

- <span data-ttu-id="e4f22-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="e4f22-105">Partner Center</span></span>

<span data-ttu-id="e4f22-106">Como obter insights de implementação de licenças para um cliente específico.</span><span class="sxs-lookup"><span data-stu-id="e4f22-106">How to get licenses deployment insights for a specific customer.</span></span>

> [!NOTE]
> <span data-ttu-id="e4f22-107">Este cenário é substituído pela [Obter informações de utilização de licenças](get-licenses-usage-information.md).</span><span class="sxs-lookup"><span data-stu-id="e4f22-107">This scenario is superceded by [Get licenses usage information](get-licenses-usage-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e4f22-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e4f22-108">Prerequisites</span></span>

<span data-ttu-id="e4f22-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e4f22-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e4f22-110">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="e4f22-110">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="e4f22-111">C\#</span><span class="sxs-lookup"><span data-stu-id="e4f22-111">C\#</span></span>

<span data-ttu-id="e4f22-112">Para obter dados agregados sobre a implementação de um cliente especificado, ligue primeiro para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e4f22-112">To retrieve aggregated data on deployment for a specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="e4f22-113">Em seguida, obtenha uma interface para operações de recolha de análise ao nível do cliente a partir da propriedade [**Analytics.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics)</span><span class="sxs-lookup"><span data-stu-id="e4f22-113">Then get an interface to customer level analytics collection operations from the [**Analytics**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics) property.</span></span> <span data-ttu-id="e4f22-114">Em seguida, recupere uma interface para a recolha de análise de licenças de nível de cliente da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses)</span><span class="sxs-lookup"><span data-stu-id="e4f22-114">Next, retrieve an interface to the customer level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses) property.</span></span> <span data-ttu-id="e4f22-115">Por fim, ligue para o método [**Usage.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) para obter os dados agregados sobre o uso das licenças.</span><span class="sxs-lookup"><span data-stu-id="e4f22-115">Finally, call the [**Usage.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses usage.</span></span> <span data-ttu-id="e4f22-116">Se o método for bem sucedido, obterá uma coleção de [**objetos CustomerLicensesUsageInsights.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesusageinsights)</span><span class="sxs-lookup"><span data-stu-id="e4f22-116">If the method succeeds you'll get a collection of [**CustomerLicensesUsageInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesusageinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

var customerLicensesDeploymentAnalytics = partnerOperations.Customers.ById(customerIdToRetrieve).Analytics.Licenses.Usage.Get();
```

## <a name="rest-request"></a><span data-ttu-id="e4f22-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="e4f22-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e4f22-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4f22-118">Request syntax</span></span>

| <span data-ttu-id="e4f22-119">Método</span><span class="sxs-lookup"><span data-stu-id="e4f22-119">Method</span></span>  | <span data-ttu-id="e4f22-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="e4f22-120">Request URI</span></span>                                                                                              |
|---------|----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e4f22-121">**Obter**</span><span class="sxs-lookup"><span data-stu-id="e4f22-121">**GET**</span></span> | <span data-ttu-id="e4f22-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/analytics/licenses/usage HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e4f22-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/analytics/licenses/usage HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e4f22-123">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="e4f22-123">URI parameter</span></span>

<span data-ttu-id="e4f22-124">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e4f22-124">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="e4f22-125">Nome</span><span class="sxs-lookup"><span data-stu-id="e4f22-125">Name</span></span>        | <span data-ttu-id="e4f22-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="e4f22-126">Type</span></span> | <span data-ttu-id="e4f22-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="e4f22-127">Required</span></span> | <span data-ttu-id="e4f22-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4f22-128">Description</span></span>                                                |
|-------------|------|----------|------------------------------------------------------------|
| <span data-ttu-id="e4f22-129">id cliente</span><span class="sxs-lookup"><span data-stu-id="e4f22-129">customer-id</span></span> | <span data-ttu-id="e4f22-130">guid</span><span class="sxs-lookup"><span data-stu-id="e4f22-130">guid</span></span> | <span data-ttu-id="e4f22-131">Sim</span><span class="sxs-lookup"><span data-stu-id="e4f22-131">Yes</span></span>      | <span data-ttu-id="e4f22-132">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="e4f22-132">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e4f22-133">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="e4f22-133">Request headers</span></span>

<span data-ttu-id="e4f22-134">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e4f22-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e4f22-135">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="e4f22-135">Request body</span></span>

<span data-ttu-id="e4f22-136">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e4f22-136">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e4f22-137">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e4f22-137">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e4f22-138">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="e4f22-138">REST response</span></span>

<span data-ttu-id="e4f22-139">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [CustomerLicensesUsageInsights](analytics-resources.md#customerlicensesusageinsights) que fornecem informações sobre o uso das licenças.</span><span class="sxs-lookup"><span data-stu-id="e4f22-139">If successful, the response body contains a collection of [CustomerLicensesUsageInsights](analytics-resources.md#customerlicensesusageinsights) resources that provide information about licenses usage.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e4f22-140">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="e4f22-140">Response success and error codes</span></span>

<span data-ttu-id="e4f22-141">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="e4f22-141">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e4f22-142">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="e4f22-142">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e4f22-143">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="e4f22-143">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e4f22-144">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e4f22-144">Response example</span></span>

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
