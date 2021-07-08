---
title: Obter todos os registos de utilização da subscrição de um cliente
description: Pode utilizar a coleção de recursos SubscriptionMonthlyUsageRecord para obter registos de utilização de subscrição para um cliente de um serviço ou recurso Azure específico durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 976abd86f34c1c27184f277ffc89fbc65f16bb37
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874691"
---
# <a name="get-subscription-usage-records-for-a-customer"></a><span data-ttu-id="a557c-103">Obtenha registos de utilização de assinaturas para um cliente</span><span class="sxs-lookup"><span data-stu-id="a557c-103">Get subscription usage records for a customer</span></span>

<span data-ttu-id="a557c-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="a557c-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="a557c-105">Pode utilizar a coleção de recursos **SubscriptionMonthlyUsageRecord** para obter registos de utilização de subscrição para um cliente de um serviço ou recurso Azure específico durante o período de faturação atual.</span><span class="sxs-lookup"><span data-stu-id="a557c-105">You can use the **SubscriptionMonthlyUsageRecord** resource collection to get subscription usage records for a customer of a specific Azure service or resource during the current billing period.</span></span> <span data-ttu-id="a557c-106">Este recurso representa todas as subscrições para o cliente.</span><span class="sxs-lookup"><span data-stu-id="a557c-106">This resource represents all subscriptions for the customer.</span></span> <span data-ttu-id="a557c-107">Para um cliente com um plano Azure, este recurso devolve uma lista desses planos (não subscrições individuais do Azure).</span><span class="sxs-lookup"><span data-stu-id="a557c-107">For a customer with an Azure plan, this resource returns a list of those plans (not individual Azure subscriptions).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a557c-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a557c-108">Prerequisites</span></span>

- <span data-ttu-id="a557c-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a557c-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a557c-110">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="a557c-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="a557c-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a557c-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a557c-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="a557c-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a557c-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="a557c-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a557c-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="a557c-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a557c-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="a557c-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a557c-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a557c-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="a557c-117">C\#</span><span class="sxs-lookup"><span data-stu-id="a557c-117">C\#</span></span>

<span data-ttu-id="a557c-118">Para obter registos de utilização de subscrição para um cliente de um serviço ou recurso Azure específico durante o período de faturação em curso, faça os seguintes passos:</span><span class="sxs-lookup"><span data-stu-id="a557c-118">To get subscription usage records for a customer of a specific Azure service or resource during the current billing period, do the following steps:</span></span>

1. <span data-ttu-id="a557c-119">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="a557c-119">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="a557c-120">Em seguida, ligue para a propriedade **Subscrições** e para a propriedade **UsageRecords.**</span><span class="sxs-lookup"><span data-stu-id="a557c-120">Then call the **Subscriptions** property and the **UsageRecords** property.</span></span> <span data-ttu-id="a557c-121">Termine chamando os métodos Get() ou GetAsync().</span><span class="sxs-lookup"><span data-stu-id="a557c-121">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.UsageRecords.Get();
    ```

<span data-ttu-id="a557c-122">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a557c-122">For an example, see the following:</span></span>

- <span data-ttu-id="a557c-123">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="a557c-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="a557c-124">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="a557c-124">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="a557c-125">Classe: **GetSubscriptionUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="a557c-125">Class: **GetSubscriptionUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="a557c-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="a557c-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a557c-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="a557c-127">Request syntax</span></span>

| <span data-ttu-id="a557c-128">Método</span><span class="sxs-lookup"><span data-stu-id="a557c-128">Method</span></span>  | <span data-ttu-id="a557c-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="a557c-129">Request URI</span></span>                                                                                                      |
|---------|------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a557c-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="a557c-130">**GET**</span></span> | <span data-ttu-id="a557c-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/registos de uso HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a557c-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="a557c-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="a557c-132">URI parameter</span></span>

<span data-ttu-id="a557c-133">Esta tabela lista o parâmetro de consulta necessário para obter as informações de utilização classificadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="a557c-133">This table lists the required query parameter to get the customer's rated usage information.</span></span>

| <span data-ttu-id="a557c-134">Nome</span><span class="sxs-lookup"><span data-stu-id="a557c-134">Name</span></span>                   | <span data-ttu-id="a557c-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="a557c-135">Type</span></span>     | <span data-ttu-id="a557c-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="a557c-136">Required</span></span> | <span data-ttu-id="a557c-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="a557c-137">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="a557c-138">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="a557c-138">**customer-tenant-id**</span></span> | <span data-ttu-id="a557c-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="a557c-139">**guid**</span></span> | <span data-ttu-id="a557c-140">Y</span><span class="sxs-lookup"><span data-stu-id="a557c-140">Y</span></span>        | <span data-ttu-id="a557c-141">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="a557c-141">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a557c-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="a557c-142">Request headers</span></span>

<span data-ttu-id="a557c-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a557c-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a557c-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="a557c-144">Request body</span></span>

<span data-ttu-id="a557c-145">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a557c-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="a557c-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a557c-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="a557c-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="a557c-147">REST response</span></span>

<span data-ttu-id="a557c-148">Se for bem sucedido, este método devolve um recurso **SubscriptionMonthlyUsageRecord** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="a557c-148">If successful, this method returns a **SubscriptionMonthlyUsageRecord** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a557c-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="a557c-149">Response success and error codes</span></span>

<span data-ttu-id="a557c-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="a557c-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a557c-151">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="a557c-151">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="a557c-152">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="a557c-152">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="a557c-153">Exemplo de resposta para subscrições Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="a557c-153">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="a557c-154">Neste exemplo, o cliente comprou uma oferta **de 145P Azure PayG.**</span><span class="sxs-lookup"><span data-stu-id="a557c-154">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="a557c-155">*Para clientes com assinaturas Microsoft Azure (MS-AZR-0145P), não haverá alteração da resposta da API.*</span><span class="sxs-lookup"><span data-stu-id="a557c-155">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

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

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="a557c-156">Exemplo de resposta do REST para o plano Azure</span><span class="sxs-lookup"><span data-stu-id="a557c-156">REST response example for Azure plan</span></span>

<span data-ttu-id="a557c-157">Neste exemplo, o cliente comprou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="a557c-157">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="a557c-158">*Para clientes com planos Azure, existem as seguintes alterações na resposta da API:*</span><span class="sxs-lookup"><span data-stu-id="a557c-158">*For customers with Azure plans, there are the following changes in the API response:*</span></span>

- <span data-ttu-id="a557c-159">**currencyLocale** é substituída por **moedaSCo**</span><span class="sxs-lookup"><span data-stu-id="a557c-159">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="a557c-160">**usdTotalCost** é um novo campo</span><span class="sxs-lookup"><span data-stu-id="a557c-160">**usdTotalCost** is a new field</span></span>

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
