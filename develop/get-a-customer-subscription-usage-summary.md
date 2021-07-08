---
title: Obtenha resumo de utilização para a subscrição do cliente
description: Pode utilizar o recurso SubscriptionUsageSummary para obter um resumo de utilização por subscrição de um serviço ou recurso Azure específico durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 362e72e1b54a62a114564d4dc48a082bcdeea012
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874674"
---
# <a name="get-usage-summary-for-customers-subscription"></a><span data-ttu-id="c69c2-103">Obtenha resumo de utilização para a subscrição do cliente</span><span class="sxs-lookup"><span data-stu-id="c69c2-103">Get usage summary for customer's subscription</span></span>

<span data-ttu-id="c69c2-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c69c2-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c69c2-105">Pode utilizar o recurso **SubscriptionUsageSummary** para obter um resumo de utilização de subscrição para um cliente.</span><span class="sxs-lookup"><span data-stu-id="c69c2-105">You can use the **SubscriptionUsageSummary** resource to get a subscription usage summary for a customer.</span></span> <span data-ttu-id="c69c2-106">Este recurso representa o resumo de utilização da subscrição de um serviço ou recurso Azure específico durante o período de faturação atual.</span><span class="sxs-lookup"><span data-stu-id="c69c2-106">This resource represents the subscription usage summary of a specific Azure service or resource during the current billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c69c2-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c69c2-107">Prerequisites</span></span>

- <span data-ttu-id="c69c2-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c69c2-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c69c2-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="c69c2-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="c69c2-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c69c2-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c69c2-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="c69c2-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c69c2-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="c69c2-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c69c2-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="c69c2-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c69c2-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="c69c2-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c69c2-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c69c2-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="c69c2-116">Um identificador de assinatura</span><span class="sxs-lookup"><span data-stu-id="c69c2-116">A subscription identifier</span></span>

## <a name="c"></a><span data-ttu-id="c69c2-117">C\#</span><span class="sxs-lookup"><span data-stu-id="c69c2-117">C\#</span></span>

<span data-ttu-id="c69c2-118">Para obter um resumo de utilização de subscrição para a subscrição de um cliente:</span><span class="sxs-lookup"><span data-stu-id="c69c2-118">To get a subscription usage summary for a customer's subscription:</span></span>

1. <span data-ttu-id="c69c2-119">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="c69c2-119">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="c69c2-120">Em seguida, ligue para a propriedade Subscrições e para a propriedade **UsageSummary.**</span><span class="sxs-lookup"><span data-stu-id="c69c2-120">Then call the Subscriptions property and the **UsageSummary** property.</span></span> <span data-ttu-id="c69c2-121">Termine chamando os métodos Get() ou GetAsync().</span><span class="sxs-lookup"><span data-stu-id="c69c2-121">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var subscriptionUsageSummary = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageSummary.Get();
    ```

<span data-ttu-id="c69c2-122">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c69c2-122">For an example, see the following:</span></span>

- <span data-ttu-id="c69c2-123">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="c69c2-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="c69c2-124">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="c69c2-124">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="c69c2-125">Classe: **GetSubscriptionUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="c69c2-125">Class: **GetSubscriptionUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="c69c2-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c69c2-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c69c2-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c69c2-127">Request syntax</span></span>

| <span data-ttu-id="c69c2-128">Método</span><span class="sxs-lookup"><span data-stu-id="c69c2-128">Method</span></span>  | <span data-ttu-id="c69c2-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c69c2-129">Request URI</span></span>                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c69c2-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="c69c2-130">**GET**</span></span> | <span data-ttu-id="c69c2-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/usagesummary HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c69c2-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="c69c2-132">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="c69c2-132">URI parameters</span></span>

<span data-ttu-id="c69c2-133">Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização classificadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="c69c2-133">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="c69c2-134">Nome</span><span class="sxs-lookup"><span data-stu-id="c69c2-134">Name</span></span>                   | <span data-ttu-id="c69c2-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="c69c2-135">Type</span></span>     | <span data-ttu-id="c69c2-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="c69c2-136">Required</span></span> | <span data-ttu-id="c69c2-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="c69c2-137">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="c69c2-138">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="c69c2-138">**customer-tenant-id**</span></span> | <span data-ttu-id="c69c2-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="c69c2-139">**guid**</span></span> | <span data-ttu-id="c69c2-140">Y</span><span class="sxs-lookup"><span data-stu-id="c69c2-140">Y</span></span>        | <span data-ttu-id="c69c2-141">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="c69c2-141">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="c69c2-142">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="c69c2-142">**subscription-id**</span></span>    | <span data-ttu-id="c69c2-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="c69c2-143">**guid**</span></span> | <span data-ttu-id="c69c2-144">Y</span><span class="sxs-lookup"><span data-stu-id="c69c2-144">Y</span></span>        | <span data-ttu-id="c69c2-145">Um GUID correspondente ao identificador de uma subscrição.</span><span class="sxs-lookup"><span data-stu-id="c69c2-145">A GUID corresponding to the identifier of a subscription.</span></span> <span data-ttu-id="c69c2-146">Para um plano Azure, este é o identificador do recurso de [subscrição](subscription-resources.md#subscription)correspondente do Partner Center, que representa o plano Azure.</span><span class="sxs-lookup"><span data-stu-id="c69c2-146">For an Azure plan, this is the identifier of the corresponding Partner Center [subscription resource](subscription-resources.md#subscription), which represents the Azure plan.</span></span> <span data-ttu-id="c69c2-147">*Para os recursos de subscrição do plano Azure, forneça o **id de plano** como **id de subscrição** nesta rota.*</span><span class="sxs-lookup"><span data-stu-id="c69c2-147">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c69c2-148">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c69c2-148">Request headers</span></span>

<span data-ttu-id="c69c2-149">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c69c2-149">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c69c2-150">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="c69c2-150">Request body</span></span>

<span data-ttu-id="c69c2-151">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c69c2-151">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c69c2-152">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c69c2-152">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="c69c2-153">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c69c2-153">REST response</span></span>

<span data-ttu-id="c69c2-154">Se for bem sucedido, este método devolve um **recurso SubscriptionUsageSummary** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="c69c2-154">If successful, this method returns a **SubscriptionUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c69c2-155">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c69c2-155">Response success and error codes</span></span>

<span data-ttu-id="c69c2-156">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c69c2-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c69c2-157">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c69c2-157">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="c69c2-158">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c69c2-158">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="c69c2-159">Exemplo de resposta para subscrições Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="c69c2-159">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="c69c2-160">Neste exemplo, o cliente comprou uma oferta **de 145P Azure PayG.**</span><span class="sxs-lookup"><span data-stu-id="c69c2-160">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="c69c2-161">*Para clientes com assinaturas Microsoft Azure (MS-AZR-0145P), não haverá alteração da resposta da API.*</span><span class="sxs-lookup"><span data-stu-id="c69c2-161">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "resourceId": "ABCDEFGH-F347-41B6-B02C-187B1B778A43",
    "id": "ABCDEFGH-F347-41B6-B02C-187B1B778A43",
    "resourceName": "Microsoft Azure",
    "name": "Microsoft Azure",
    "billingStartDate": "2019-08-28T00:00:00-07:00",
    "billingEndDate": "2019-09-27T00:00:00-07:00",
    "totalCost": 22.861172,
    "currencyLocale": "fr-FR",
    "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SubscriptionUsageSummary"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="c69c2-162">Exemplo de resposta do REST para o plano Azure</span><span class="sxs-lookup"><span data-stu-id="c69c2-162">REST response example for Azure plan</span></span>

<span data-ttu-id="c69c2-163">Neste exemplo, o cliente comprou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="c69c2-163">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="c69c2-164">*Para clientes com planos Azure, existem as seguintes alterações de resposta da API:*</span><span class="sxs-lookup"><span data-stu-id="c69c2-164">*For customers with Azure plans, there are the following API response changes:*</span></span>

- <span data-ttu-id="c69c2-165">**currencyLocale** é substituída por **moedaSCo**</span><span class="sxs-lookup"><span data-stu-id="c69c2-165">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="c69c2-166">**usdTotalCost** é um novo campo</span><span class="sxs-lookup"><span data-stu-id="c69c2-166">**usdTotalCost** is a new field</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac1
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "resourceId": "11111111-dca5-6f31-d3a6-dbbfad9be0fc",
    "resourceName": "Azure plan",
    "billingStartDate": "2019-09-01T00:00:00+00:00",
    "billingEndDate": "2019-10-01T00:00:00+00:00",
    "totalCost": 28.82860766744404945074,
    "currencyCode": "GBP",
    "usdTotalCost": 35.23000000000000362337,
    "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SubscriptionUsageSummary"
    }
}
```
