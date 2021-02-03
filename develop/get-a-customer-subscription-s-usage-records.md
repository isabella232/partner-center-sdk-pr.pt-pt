---
title: Obter todos os registos de utilização da subscrição de um cliente
description: Pode utilizar a coleção de recursos SubscriptionMonthlyUsageRecord para obter registos de utilização de subscrição para um cliente de um serviço ou recurso Azure específico durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 765ea16ff58b462d83ae3b8764b8b34c3ef804dc
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769145"
---
# <a name="get-subscription-usage-records-for-a-customer"></a><span data-ttu-id="2136a-103">Obtenha registos de utilização de assinaturas para um cliente</span><span class="sxs-lookup"><span data-stu-id="2136a-103">Get subscription usage records for a customer</span></span>

<span data-ttu-id="2136a-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="2136a-104">**Applies to:**</span></span>

- <span data-ttu-id="2136a-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="2136a-105">Partner Center</span></span>
- <span data-ttu-id="2136a-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="2136a-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="2136a-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2136a-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2136a-108">Pode utilizar a coleção de recursos **SubscriptionMonthlyUsageRecord** para obter registos de utilização de subscrição para um cliente de um serviço ou recurso Azure específico durante o período de faturação atual.</span><span class="sxs-lookup"><span data-stu-id="2136a-108">You can use the **SubscriptionMonthlyUsageRecord** resource collection to get subscription usage records for a customer of a specific Azure service or resource during the current billing period.</span></span> <span data-ttu-id="2136a-109">Este recurso representa todas as subscrições para o cliente.</span><span class="sxs-lookup"><span data-stu-id="2136a-109">This resource represents all subscriptions for the customer.</span></span> <span data-ttu-id="2136a-110">Para um cliente com um plano Azure, este recurso devolve uma lista desses planos (não subscrições individuais do Azure).</span><span class="sxs-lookup"><span data-stu-id="2136a-110">For a customer with an Azure plan, this resource returns a list of those plans (not individual Azure subscriptions).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2136a-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2136a-111">Prerequisites</span></span>

- <span data-ttu-id="2136a-112">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2136a-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2136a-113">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="2136a-113">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="2136a-114">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2136a-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="2136a-115">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="2136a-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="2136a-116">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="2136a-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="2136a-117">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="2136a-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="2136a-118">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="2136a-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="2136a-119">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2136a-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="2136a-120">C\#</span><span class="sxs-lookup"><span data-stu-id="2136a-120">C\#</span></span>

<span data-ttu-id="2136a-121">Para obter registos de utilização de subscrição para um cliente de um serviço ou recurso Azure específico durante o período de faturação atual.:</span><span class="sxs-lookup"><span data-stu-id="2136a-121">To get subscription usage records for a customer of a specific Azure service or resource during the current billing period.:</span></span>

1. <span data-ttu-id="2136a-122">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="2136a-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="2136a-123">Em seguida, ligue para a propriedade **Subscrições,** bem como a propriedade **UsageRecords.**</span><span class="sxs-lookup"><span data-stu-id="2136a-123">Then call the **Subscriptions** property, as well as **UsageRecords** property.</span></span> <span data-ttu-id="2136a-124">Termine chamando os métodos Get() ou GetAsync().</span><span class="sxs-lookup"><span data-stu-id="2136a-124">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.UsageRecords.Get();
    ```

<span data-ttu-id="2136a-125">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2136a-125">For an example, see the following:</span></span>

- <span data-ttu-id="2136a-126">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="2136a-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="2136a-127">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="2136a-127">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="2136a-128">Classe: **GetSubscriptionUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="2136a-128">Class: **GetSubscriptionUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="2136a-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2136a-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2136a-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2136a-130">Request syntax</span></span>

| <span data-ttu-id="2136a-131">Método</span><span class="sxs-lookup"><span data-stu-id="2136a-131">Method</span></span>  | <span data-ttu-id="2136a-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2136a-132">Request URI</span></span>                                                                                                      |
|---------|------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2136a-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="2136a-133">**GET**</span></span> | <span data-ttu-id="2136a-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/registos de uso HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2136a-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="2136a-135">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="2136a-135">URI parameter</span></span>

<span data-ttu-id="2136a-136">Esta tabela lista o parâmetro de consulta necessário para obter as informações de utilização classificadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="2136a-136">This table lists the required query parameter to get the customer's rated usage information.</span></span>

| <span data-ttu-id="2136a-137">Nome</span><span class="sxs-lookup"><span data-stu-id="2136a-137">Name</span></span>                   | <span data-ttu-id="2136a-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="2136a-138">Type</span></span>     | <span data-ttu-id="2136a-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="2136a-139">Required</span></span> | <span data-ttu-id="2136a-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="2136a-140">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="2136a-141">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="2136a-141">**customer-tenant-id**</span></span> | <span data-ttu-id="2136a-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="2136a-142">**guid**</span></span> | <span data-ttu-id="2136a-143">Y</span><span class="sxs-lookup"><span data-stu-id="2136a-143">Y</span></span>        | <span data-ttu-id="2136a-144">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="2136a-144">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2136a-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2136a-145">Request headers</span></span>

<span data-ttu-id="2136a-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2136a-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2136a-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="2136a-147">Request body</span></span>

<span data-ttu-id="2136a-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2136a-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="2136a-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="2136a-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="2136a-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2136a-150">REST response</span></span>

<span data-ttu-id="2136a-151">Se for bem sucedido, este método devolve um recurso **SubscriptionMonthlyUsageRecord** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="2136a-151">If successful, this method returns a **SubscriptionMonthlyUsageRecord** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2136a-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2136a-152">Response success and error codes</span></span>

<span data-ttu-id="2136a-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2136a-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2136a-154">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2136a-154">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="2136a-155">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2136a-155">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="2136a-156">Exemplo de resposta para subscrições microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="2136a-156">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="2136a-157">Neste exemplo, o cliente comprou uma oferta **de 145P Azure PayG.**</span><span class="sxs-lookup"><span data-stu-id="2136a-157">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="2136a-158">*Para clientes com subscrições Microsoft Azure (MS-AZR-0145P), não haverá alteração na resposta da API.*</span><span class="sxs-lookup"><span data-stu-id="2136a-158">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 1,
    "items": [
        {
            "status": "active",
            "offerId": "MS-AZR-0145P",
            "resourceId": "11111111-F347-41B6-B02C-187B1B778A43",
            "id": "11111111-F347-41B6-B02C-187B1B778A43",
            "resourceName": "Microsoft Azure",
            "name": "Microsoft Azure",
            "totalCost": 22.861172,
            "currencyLocale": "fr-FR",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/usagerecords/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="2136a-159">Exemplo de resposta do REST para o plano Azure</span><span class="sxs-lookup"><span data-stu-id="2136a-159">REST response example for Azure plan</span></span>

<span data-ttu-id="2136a-160">Neste exemplo, o cliente comprou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="2136a-160">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="2136a-161">*Para clientes com planos Azure, existem as seguintes alterações na resposta da API:*</span><span class="sxs-lookup"><span data-stu-id="2136a-161">*For customers with Azure plans, there are the following changes in the API response:*</span></span>

- <span data-ttu-id="2136a-162">**currencyLocale** é substituída por **moedaSCo**</span><span class="sxs-lookup"><span data-stu-id="2136a-162">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="2136a-163">**usdTotalCost** é um novo campo</span><span class="sxs-lookup"><span data-stu-id="2136a-163">**usdTotalCost** is a new field</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 2,
    "items": [
        {
            "status": "active",
            "partnerOnRecord": "some-id",
            "offerId": "DZH318Z0BPS6:0001:DZH318Z0BML6",
            "resourceId": "11111111-7d58-6654-69fa-0797198155d3",
            "id": "11111111-7d58-6654-69fa-0797198155d3",
            "resourceName": "Azure plan",
            "name": "Azure plan",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        },
        {
            "status": "active",
            "partnerOnRecord": "some-id",
            "offerId": "DZH318Z0BPS6:0001:DZH318Z0BML6",
            "resourceId": "11111111-25aa-ebb8-2bb4-fb406307babd",
            "id": "11111111-25aa-ebb8-2bb4-fb406307babd",
            "resourceName": "Azure plan",
            "name": "Azure plan",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/usagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
