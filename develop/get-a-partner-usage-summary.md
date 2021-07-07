---
title: Obtenha um resumo de utilização para um parceiro
description: Pode utilizar o recurso PartnerUsageSummary para obter um resumo de utilização do parceiro de todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: f003980f1b521ad0ac26dbfd0d4821b9096fdd27
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873909"
---
# <a name="get-a-usage-summary-for-a-partner"></a><span data-ttu-id="c7ccc-103">Obtenha um resumo de utilização para um parceiro</span><span class="sxs-lookup"><span data-stu-id="c7ccc-103">Get a usage summary for a partner</span></span>

<span data-ttu-id="c7ccc-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c7ccc-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c7ccc-105">Pode utilizar o recurso **PartnerUsageSummary** para obter um resumo de utilização do parceiro de todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação atual.</span><span class="sxs-lookup"><span data-stu-id="c7ccc-105">You can use the **PartnerUsageSummary** resource to get a partner usage summary of all customers that purchased a specific Azure service or resource during the current billing period.</span></span>

<span data-ttu-id="c7ccc-106">*O total devolvido por esta API não devolverá o consumo aos clientes que tenham um plano Azure.*</span><span class="sxs-lookup"><span data-stu-id="c7ccc-106">*The total returned by this API will not return consumption for customers that have an Azure plan.*</span></span> <span data-ttu-id="c7ccc-107">Planejado para a depreciação no futuro.</span><span class="sxs-lookup"><span data-stu-id="c7ccc-107">Planned for deprecation in the future.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7ccc-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c7ccc-108">Prerequisites</span></span>

- <span data-ttu-id="c7ccc-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c7ccc-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c7ccc-110">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="c7ccc-110">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="c7ccc-111">C\#</span><span class="sxs-lookup"><span data-stu-id="c7ccc-111">C\#</span></span>

<span data-ttu-id="c7ccc-112">Para obter um resumo de utilização para todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação em curso:</span><span class="sxs-lookup"><span data-stu-id="c7ccc-112">To get a usage summary for all customers that purchased a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="c7ccc-113">Utilize o seu **IAggregatePartner**.</span><span class="sxs-lookup"><span data-stu-id="c7ccc-113">Use your **IAggregatePartner**.</span></span>

2. <span data-ttu-id="c7ccc-114">Ligue para a propriedade **UsageSummary,** seguida dos métodos **Get()** ou **GetAsync():**</span><span class="sxs-lookup"><span data-stu-id="c7ccc-114">Call the **UsageSummary** property, followed by the **Get()** or **GetAsync()** methods:</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;

    var usageSummary = partnerOperations.UsageSummary.Get();
    ```

<span data-ttu-id="c7ccc-115">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c7ccc-115">For an example, see the following:</span></span>

- <span data-ttu-id="c7ccc-116">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="c7ccc-116">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="c7ccc-117">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="c7ccc-117">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="c7ccc-118">Classe: **GetPartnerUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="c7ccc-118">Class: **GetPartnerUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="c7ccc-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c7ccc-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c7ccc-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7ccc-120">Request syntax</span></span>

| <span data-ttu-id="c7ccc-121">Método</span><span class="sxs-lookup"><span data-stu-id="c7ccc-121">Method</span></span>  | <span data-ttu-id="c7ccc-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c7ccc-122">Request URI</span></span>                                                         |
|---------|---------------------------------------------------------------------|
| <span data-ttu-id="c7ccc-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="c7ccc-123">**GET**</span></span> | <span data-ttu-id="c7ccc-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c7ccc-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c7ccc-125">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c7ccc-125">Request headers</span></span>

<span data-ttu-id="c7ccc-126">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c7ccc-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c7ccc-127">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="c7ccc-127">Request body</span></span>

<span data-ttu-id="c7ccc-128">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c7ccc-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c7ccc-129">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c7ccc-129">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="c7ccc-130">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c7ccc-130">REST response</span></span>

<span data-ttu-id="c7ccc-131">Se for bem sucedido, este método devolve um recurso **PartnerUsageSummary** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="c7ccc-131">If successful, this method returns a **PartnerUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c7ccc-132">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c7ccc-132">Response success and error codes</span></span>

<span data-ttu-id="c7ccc-133">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c7ccc-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c7ccc-134">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c7ccc-134">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="c7ccc-135">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c7ccc-135">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c7ccc-136">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="c7ccc-136">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "customersOverBudget": 1,
    "customersTrendingOver": 0,
    "customersWithUsageBasedSubscription": 11,
    "resourceId": "11111111-4574-4539-bc42-0e539b9684c0",
    "id": "11111111-4574-4539-bc42-0e539b9684c0",
    "resourceName": "PLAMUATT2NETNEW",
    "name": "PLAMUATT2NETNEW",
    "billingStartDate": "2019-08-28T00:00:00-07:00",
    "billingEndDate": "2019-09-27T00:00:00-07:00",
    "totalCost": 22.861172,
    "currencyLocale": "fr-FR",
    "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
    "links": {
        "self": {
            "uri": "/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "PartnerUsageSummary"
    }
}
```
