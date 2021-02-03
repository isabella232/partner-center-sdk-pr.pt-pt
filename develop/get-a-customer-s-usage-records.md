---
title: Obtenha registos de utilização para todos os clientes
description: Pode utilizar a coleção de recursos CustomerMonthlyUsageRecord para obter registos de utilização para todos os clientes que adquiriram um serviço ou recurso Azure específico.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: da829a6de3690a9b1117ce9dfa58fbe381cafd81
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769158"
---
# <a name="get-usage-records-for-all-customers"></a><span data-ttu-id="1894b-103">Obtenha registos de utilização para todos os clientes</span><span class="sxs-lookup"><span data-stu-id="1894b-103">Get usage records for all customers</span></span>

<span data-ttu-id="1894b-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="1894b-104">**Applies to:**</span></span>

- <span data-ttu-id="1894b-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="1894b-105">Partner Center</span></span>
- <span data-ttu-id="1894b-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="1894b-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="1894b-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1894b-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1894b-108">Os parceiros podem utilizar a coleção de recursos **CustomerMonthlyUsageRecord** para obter registos de utilização para todos os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="1894b-108">Partners can use the **CustomerMonthlyUsageRecord** resource collection to get usage records for all their customers.</span></span> <span data-ttu-id="1894b-109">Este recurso representa registos de utilização para todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="1894b-109">This resource represents usage records for all customers.</span></span> <span data-ttu-id="1894b-110">Isto inclui os clientes com uma subscrição do Microsoft Azure (MS-AZR-0145P) ou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="1894b-110">That includes those customers with a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1894b-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1894b-111">Prerequisites</span></span>

- <span data-ttu-id="1894b-112">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1894b-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1894b-113">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="1894b-113">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="1894b-114">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1894b-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="1894b-115">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="1894b-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="1894b-116">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="1894b-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="1894b-117">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="1894b-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="1894b-118">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="1894b-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="1894b-119">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1894b-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="1894b-120">C\#</span><span class="sxs-lookup"><span data-stu-id="1894b-120">C\#</span></span>

<span data-ttu-id="1894b-121">Para obter todos os registos de utilização de todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação em curso:</span><span class="sxs-lookup"><span data-stu-id="1894b-121">To get all the usage records for all customers who purchased a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="1894b-122">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="1894b-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="1894b-123">Ligue para a propriedade **UsageRecords** e, em seguida, ligue para o método **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="1894b-123">Call **UsageRecords** property, then call the **Get()** or **GetAsync()** method.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    var usageRecords = partnerOperations.Customers.UsageRecords.Get();
    ```

<span data-ttu-id="1894b-124">Por exemplo, consulte a seguinte amostra:</span><span class="sxs-lookup"><span data-stu-id="1894b-124">For an example, see the following sample:</span></span>

- <span data-ttu-id="1894b-125">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="1894b-125">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="1894b-126">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="1894b-126">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="1894b-127">Classe: **GetCustomerUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="1894b-127">Class: **GetCustomerUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="1894b-128">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="1894b-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1894b-129">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="1894b-129">Request syntax</span></span>

| <span data-ttu-id="1894b-130">Método</span><span class="sxs-lookup"><span data-stu-id="1894b-130">Method</span></span>  | <span data-ttu-id="1894b-131">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="1894b-131">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="1894b-132">**Obter**</span><span class="sxs-lookup"><span data-stu-id="1894b-132">**GET**</span></span> | <span data-ttu-id="1894b-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/registos de uso HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1894b-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/usagerecords HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1894b-134">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="1894b-134">Request headers</span></span>

<span data-ttu-id="1894b-135">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1894b-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1894b-136">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="1894b-136">Request body</span></span>

<span data-ttu-id="1894b-137">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1894b-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="1894b-138">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="1894b-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/usagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="1894b-139">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="1894b-139">REST response</span></span>

<span data-ttu-id="1894b-140">Se for bem sucedido, este método devolve um recurso **CustomerMonthlyUsageRecord** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="1894b-140">If successful, this method returns a **CustomerMonthlyUsageRecord** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1894b-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="1894b-141">Response success and error codes</span></span>

<span data-ttu-id="1894b-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="1894b-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1894b-143">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="1894b-143">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="1894b-144">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="1894b-144">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1894b-145">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="1894b-145">Response example</span></span>

<span data-ttu-id="1894b-146">Você pode usar a propriedade **isUpgraded** para identificar clientes que têm um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="1894b-146">You can use the **isUpgraded** property to identify customers who have an Azure plan.</span></span> <span data-ttu-id="1894b-147">Se o valor para **o isUpgraded** for **verdadeiro,** significa que os clientes têm planos Azure.</span><span class="sxs-lookup"><span data-stu-id="1894b-147">If the value for **isUpgraded** is **true**, it means the customers have Azure plans.</span></span>

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
