---
title: Obtenha registos de utilização para todos os clientes
description: Pode utilizar a coleção de recursos CustomerMonthlyUsageRecord para obter registos de utilização para todos os clientes que adquiriram um serviço ou recurso Azure específico.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6b3fb0e1989336810f2afcc2a5bfc3a1d2849b7f
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874895"
---
# <a name="get-usage-records-for-all-customers"></a><span data-ttu-id="f6bc6-103">Obtenha registos de utilização para todos os clientes</span><span class="sxs-lookup"><span data-stu-id="f6bc6-103">Get usage records for all customers</span></span>

<span data-ttu-id="f6bc6-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="f6bc6-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="f6bc6-105">Os parceiros podem utilizar a coleção de recursos **CustomerMonthlyUsageRecord** para obter registos de utilização para todos os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-105">Partners can use the **CustomerMonthlyUsageRecord** resource collection to get usage records for all their customers.</span></span> <span data-ttu-id="f6bc6-106">Este recurso representa registos de utilização para todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-106">This resource represents usage records for all customers.</span></span> <span data-ttu-id="f6bc6-107">Isto inclui os clientes com uma subscrição de Microsoft Azure (MS-AZR-0145P) ou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-107">That includes those customers with a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6bc6-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f6bc6-108">Prerequisites</span></span>

- <span data-ttu-id="f6bc6-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f6bc6-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f6bc6-110">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="f6bc6-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f6bc6-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f6bc6-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f6bc6-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f6bc6-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="f6bc6-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f6bc6-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="f6bc6-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f6bc6-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f6bc6-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="f6bc6-117">C\#</span><span class="sxs-lookup"><span data-stu-id="f6bc6-117">C\#</span></span>

<span data-ttu-id="f6bc6-118">Para obter todos os registos de utilização de todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação em curso:</span><span class="sxs-lookup"><span data-stu-id="f6bc6-118">To get all the usage records for all customers who purchased a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="f6bc6-119">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="f6bc6-119">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="f6bc6-120">Ligue para a propriedade **UsageRecords** e, em seguida, ligue para o método **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="f6bc6-120">Call **UsageRecords** property, then call the **Get()** or **GetAsync()** method.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    var usageRecords = partnerOperations.Customers.UsageRecords.Get();
    ```

<span data-ttu-id="f6bc6-121">Por exemplo, consulte a seguinte amostra:</span><span class="sxs-lookup"><span data-stu-id="f6bc6-121">For an example, see the following sample:</span></span>

- <span data-ttu-id="f6bc6-122">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="f6bc6-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="f6bc6-123">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="f6bc6-123">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="f6bc6-124">Classe: **GetCustomerUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="f6bc6-124">Class: **GetCustomerUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="f6bc6-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f6bc6-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f6bc6-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6bc6-126">Request syntax</span></span>

| <span data-ttu-id="f6bc6-127">Método</span><span class="sxs-lookup"><span data-stu-id="f6bc6-127">Method</span></span>  | <span data-ttu-id="f6bc6-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f6bc6-128">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="f6bc6-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="f6bc6-129">**GET**</span></span> | <span data-ttu-id="f6bc6-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/registos de uso HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f6bc6-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/usagerecords HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f6bc6-131">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="f6bc6-131">Request headers</span></span>

<span data-ttu-id="f6bc6-132">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f6bc6-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f6bc6-133">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f6bc6-133">Request body</span></span>

<span data-ttu-id="f6bc6-134">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-134">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f6bc6-135">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f6bc6-135">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/usagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="f6bc6-136">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f6bc6-136">REST response</span></span>

<span data-ttu-id="f6bc6-137">Se for bem sucedido, este método devolve um recurso **CustomerMonthlyUsageRecord** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-137">If successful, this method returns a **CustomerMonthlyUsageRecord** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f6bc6-138">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f6bc6-138">Response success and error codes</span></span>

<span data-ttu-id="f6bc6-139">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f6bc6-140">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-140">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="f6bc6-141">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f6bc6-141">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f6bc6-142">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f6bc6-142">Response example</span></span>

<span data-ttu-id="f6bc6-143">Você pode usar a propriedade **isUpgraded** para identificar clientes que têm um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-143">You can use the **isUpgraded** property to identify customers who have an Azure plan.</span></span> <span data-ttu-id="f6bc6-144">Se o valor para **o isUpgraded** for **verdadeiro,** significa que os clientes têm planos Azure.</span><span class="sxs-lookup"><span data-stu-id="f6bc6-144">If the value for **isUpgraded** is **true**, it means the customers have Azure plans.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 25,
    "items": [
        {
            "budget": {
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "customerSpendingBudget": {
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "percentUsed": 0,
            "isUpgraded": false,
            "resourceId": "11111111-1843-4b3b-872f-206e08a08e51",
            "id": "11111111-1843-4b3b-872f-206e08a08e51",
            "resourceName": "LEGACY AZURE CUSTOMER SE",
            "name": "LEGACY AZURE CUSTOMER SE",
            "totalCost": 0,
            "currencyLocale": "fr-FR",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-08-01T23:00:16.57+00:00",
            "attributes": {
                "objectType": "CustomerMonthlyUsageRecord"
            }
        },
        {
            "budget": {
                "amount": 20,
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "percentUsed": 602.84,
            "isUpgraded": true,
            "resourceId": "11111111-6fb9-4b05-8f15-b3d72e0596e6",
            "id": "11111111-6fb9-4b05-8f15-b3d72e0596e6",
            "resourceName": "Modern Azure Customer SE",
            "name": "Modern Azure Customer SE",
            "totalCost": 120.5682999999995904716,
            "currencyCode": "SEK",
            "usdTotalCost": 12.39999999999999985235,
            "lastModifiedDate": "2019-09-17T17:08:11.1433333+00:00",
            "attributes": {
                "objectType": "CustomerMonthlyUsageRecord"
            }
        },
        {
            "budget": {
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "percentUsed": 0,
            "isUpgraded": true,
            "resourceId": "11111111-5892-4326-8541-9da1fdb233fb",
            "id": "11111111-5892-4326-8541-9da1fdb233fb",
            "resourceName": "Test_Test_MA20190829_14",
            "name": "Test_Test_MA20190829_14",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T17:08:11.1433333+00:00",
            "attributes": {
                "objectType": "CustomerMonthlyUsageRecord"
            }
        },
           {
            "budget": {
                "amount": 97,
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "percentUsed": 28.08,
            "isUpgraded": true,
            "resourceId": "11111111-641b-4c53-b7fc-0f2bfca8a581",
            "id": "11111111-641b-4c53-b7fc-0f2bfca8a581",
            "resourceName": "Modern Azure Customer UK",
            "name": "Modern Azure Customer UK",
            "totalCost": 27.23292827625710931604,
            "currencyCode": "GBP",
            "usdTotalCost": 33.280000000000001044,
            "lastModifiedDate": "2019-09-17T17:08:11.1433333+00:00",
            "attributes": {
                "objectType": "CustomerMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/usagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
