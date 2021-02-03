---
title: Obtenha um resumo de utilização para um parceiro
description: Pode utilizar o recurso PartnerUsageSummary para obter um resumo de utilização do parceiro de todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: ba1885f46043a75274595239fe61ce3ef0998acf
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769037"
---
# <a name="get-a-usage-summary-for-a-partner"></a><span data-ttu-id="f65de-103">Obtenha um resumo de utilização para um parceiro</span><span class="sxs-lookup"><span data-stu-id="f65de-103">Get a usage summary for a partner</span></span>

<span data-ttu-id="f65de-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="f65de-104">**Applies to:**</span></span>

- <span data-ttu-id="f65de-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="f65de-105">Partner Center</span></span>
- <span data-ttu-id="f65de-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="f65de-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="f65de-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="f65de-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="f65de-108">Pode utilizar o recurso **PartnerUsageSummary** para obter um resumo de utilização do parceiro de todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação atual.</span><span class="sxs-lookup"><span data-stu-id="f65de-108">You can use the **PartnerUsageSummary** resource to get a partner usage summary of all customers that purchased a specific Azure service or resource during the current billing period.</span></span>

<span data-ttu-id="f65de-109">*O total devolvido por esta API não devolverá o consumo aos clientes que tenham um plano Azure.*</span><span class="sxs-lookup"><span data-stu-id="f65de-109">*The total returned by this API will not return consumption for customers that have an Azure plan.*</span></span> <span data-ttu-id="f65de-110">Planejado para a depreciação no futuro.</span><span class="sxs-lookup"><span data-stu-id="f65de-110">Planned for deprecation in the future.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f65de-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f65de-111">Prerequisites</span></span>

- <span data-ttu-id="f65de-112">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f65de-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f65de-113">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="f65de-113">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="f65de-114">C\#</span><span class="sxs-lookup"><span data-stu-id="f65de-114">C\#</span></span>

<span data-ttu-id="f65de-115">Para obter um resumo de utilização para todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação em curso:</span><span class="sxs-lookup"><span data-stu-id="f65de-115">To get a usage summary for all customers that purchased a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="f65de-116">Utilize o seu **IAggregatePartner**.</span><span class="sxs-lookup"><span data-stu-id="f65de-116">Use your **IAggregatePartner**.</span></span>

2. <span data-ttu-id="f65de-117">Ligue para a propriedade **UsageSummary,** seguida dos métodos **Get()** ou **GetAsync():**</span><span class="sxs-lookup"><span data-stu-id="f65de-117">Call the **UsageSummary** property, followed by the **Get()** or **GetAsync()** methods:</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;

    var usageSummary = partnerOperations.UsageSummary.Get();
    ```

<span data-ttu-id="f65de-118">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f65de-118">For an example, see the following:</span></span>

- <span data-ttu-id="f65de-119">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="f65de-119">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="f65de-120">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="f65de-120">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="f65de-121">Classe: **GetPartnerUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="f65de-121">Class: **GetPartnerUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="f65de-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f65de-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f65de-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f65de-123">Request syntax</span></span>

| <span data-ttu-id="f65de-124">Método</span><span class="sxs-lookup"><span data-stu-id="f65de-124">Method</span></span>  | <span data-ttu-id="f65de-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f65de-125">Request URI</span></span>                                                         |
|---------|---------------------------------------------------------------------|
| <span data-ttu-id="f65de-126">**Obter**</span><span class="sxs-lookup"><span data-stu-id="f65de-126">**GET**</span></span> | <span data-ttu-id="f65de-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f65de-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f65de-128">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="f65de-128">Request headers</span></span>

<span data-ttu-id="f65de-129">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f65de-129">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f65de-130">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f65de-130">Request body</span></span>

<span data-ttu-id="f65de-131">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f65de-131">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f65de-132">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f65de-132">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="f65de-133">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f65de-133">REST response</span></span>

<span data-ttu-id="f65de-134">Se for bem sucedido, este método devolve um recurso **PartnerUsageSummary** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="f65de-134">If successful, this method returns a **PartnerUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f65de-135">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f65de-135">Response success and error codes</span></span>

<span data-ttu-id="f65de-136">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f65de-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f65de-137">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f65de-137">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="f65de-138">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f65de-138">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f65de-139">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f65de-139">Response example</span></span>

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
