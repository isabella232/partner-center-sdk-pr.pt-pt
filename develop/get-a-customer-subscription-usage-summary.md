---
title: Obtenha resumo de utilização para a subscrição do cliente
description: Pode utilizar o recurso SubscriptionUsageSummary para obter um resumo de utilização por subscrição de um serviço ou recurso Azure específico durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 30334b6f08829eccf0693b566c11f94cb3ece976
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769139"
---
# <a name="get-usage-summary-for-customers-subscription"></a><span data-ttu-id="74543-103">Obtenha resumo de utilização para a subscrição do cliente</span><span class="sxs-lookup"><span data-stu-id="74543-103">Get usage summary for customer's subscription</span></span>

<span data-ttu-id="74543-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="74543-104">**Applies to:**</span></span>

- <span data-ttu-id="74543-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="74543-105">Partner Center</span></span>
- <span data-ttu-id="74543-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="74543-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="74543-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="74543-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="74543-108">Pode utilizar o recurso **SubscriptionUsageSummary** para obter um resumo de utilização de subscrição para um cliente.</span><span class="sxs-lookup"><span data-stu-id="74543-108">You can use the **SubscriptionUsageSummary** resource to get a subscription usage summary for a customer.</span></span> <span data-ttu-id="74543-109">Este recurso representa o resumo de utilização da subscrição de um serviço ou recurso Azure específico durante o período de faturação atual.</span><span class="sxs-lookup"><span data-stu-id="74543-109">This resource represents the subscription usage summary of a specific Azure service or resource during the current billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74543-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="74543-110">Prerequisites</span></span>

- <span data-ttu-id="74543-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="74543-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="74543-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="74543-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="74543-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="74543-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="74543-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="74543-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="74543-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="74543-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="74543-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="74543-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="74543-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="74543-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="74543-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="74543-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="74543-119">Um identificador de assinatura</span><span class="sxs-lookup"><span data-stu-id="74543-119">A subscription identifier</span></span>

## <a name="c"></a><span data-ttu-id="74543-120">C\#</span><span class="sxs-lookup"><span data-stu-id="74543-120">C\#</span></span>

<span data-ttu-id="74543-121">Para obter um resumo de utilização de subscrição para a subscrição de um cliente:</span><span class="sxs-lookup"><span data-stu-id="74543-121">To get a subscription usage summary for a customer's subscription:</span></span>

1. <span data-ttu-id="74543-122">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="74543-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="74543-123">Em seguida, ligue para a propriedade Subscrições, bem como a propriedade **UsageSummary.**</span><span class="sxs-lookup"><span data-stu-id="74543-123">Then call the Subscriptions property, as well as **UsageSummary** property.</span></span> <span data-ttu-id="74543-124">Termine chamando os métodos Get() ou GetAsync().</span><span class="sxs-lookup"><span data-stu-id="74543-124">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var subscriptionUsageSummary = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageSummary.Get();
    ```

<span data-ttu-id="74543-125">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="74543-125">For an example, see the following:</span></span>

- <span data-ttu-id="74543-126">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="74543-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="74543-127">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="74543-127">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="74543-128">Classe: **GetSubscriptionUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="74543-128">Class: **GetSubscriptionUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="74543-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="74543-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="74543-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="74543-130">Request syntax</span></span>

| <span data-ttu-id="74543-131">Método</span><span class="sxs-lookup"><span data-stu-id="74543-131">Method</span></span>  | <span data-ttu-id="74543-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="74543-132">Request URI</span></span>                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="74543-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="74543-133">**GET**</span></span> | <span data-ttu-id="74543-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/usagesummary HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="74543-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="74543-135">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="74543-135">URI parameters</span></span>

<span data-ttu-id="74543-136">Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização classificadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="74543-136">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="74543-137">Nome</span><span class="sxs-lookup"><span data-stu-id="74543-137">Name</span></span>                   | <span data-ttu-id="74543-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="74543-138">Type</span></span>     | <span data-ttu-id="74543-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="74543-139">Required</span></span> | <span data-ttu-id="74543-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="74543-140">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="74543-141">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="74543-141">**customer-tenant-id**</span></span> | <span data-ttu-id="74543-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="74543-142">**guid**</span></span> | <span data-ttu-id="74543-143">Y</span><span class="sxs-lookup"><span data-stu-id="74543-143">Y</span></span>        | <span data-ttu-id="74543-144">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="74543-144">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="74543-145">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="74543-145">**subscription-id**</span></span>    | <span data-ttu-id="74543-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="74543-146">**guid**</span></span> | <span data-ttu-id="74543-147">Y</span><span class="sxs-lookup"><span data-stu-id="74543-147">Y</span></span>        | <span data-ttu-id="74543-148">Um GUID correspondente ao identificador de uma subscrição.</span><span class="sxs-lookup"><span data-stu-id="74543-148">A GUID corresponding to the identifier of a subscription.</span></span> <span data-ttu-id="74543-149">Para um plano Azure, este é o identificador do recurso de [subscrição](subscription-resources.md#subscription)correspondente do Partner Center, que representa o plano Azure.</span><span class="sxs-lookup"><span data-stu-id="74543-149">For an Azure plan, this is the identifier of the corresponding Partner Center [subscription resource](subscription-resources.md#subscription), which represents the Azure plan.</span></span> <span data-ttu-id="74543-150">*Para os recursos de subscrição do plano Azure, forneça o **id de plano** como **id de subscrição** nesta rota.*</span><span class="sxs-lookup"><span data-stu-id="74543-150">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="74543-151">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="74543-151">Request headers</span></span>

<span data-ttu-id="74543-152">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="74543-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="74543-153">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="74543-153">Request body</span></span>

<span data-ttu-id="74543-154">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="74543-154">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="74543-155">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="74543-155">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="74543-156">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="74543-156">REST response</span></span>

<span data-ttu-id="74543-157">Se for bem sucedido, este método devolve um **recurso SubscriptionUsageSummary** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="74543-157">If successful, this method returns a **SubscriptionUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="74543-158">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="74543-158">Response success and error codes</span></span>

<span data-ttu-id="74543-159">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="74543-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="74543-160">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="74543-160">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="74543-161">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="74543-161">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="74543-162">Exemplo de resposta para subscrições microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="74543-162">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="74543-163">Neste exemplo, o cliente comprou uma oferta **de 145P Azure PayG.**</span><span class="sxs-lookup"><span data-stu-id="74543-163">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="74543-164">*Para clientes com subscrições Microsoft Azure (MS-AZR-0145P), não haverá alteração na resposta da API.*</span><span class="sxs-lookup"><span data-stu-id="74543-164">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

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

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="74543-165">Exemplo de resposta do REST para o plano Azure</span><span class="sxs-lookup"><span data-stu-id="74543-165">REST response example for Azure plan</span></span>

<span data-ttu-id="74543-166">Neste exemplo, o cliente comprou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="74543-166">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="74543-167">*Para clientes com planos Azure, existem as seguintes alterações de resposta da API:*</span><span class="sxs-lookup"><span data-stu-id="74543-167">*For customers with Azure plans, there are the following API response changes:*</span></span>

- <span data-ttu-id="74543-168">**currencyLocale** é substituída por **moedaSCo**</span><span class="sxs-lookup"><span data-stu-id="74543-168">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="74543-169">**usdTotalCost** é um novo campo</span><span class="sxs-lookup"><span data-stu-id="74543-169">**usdTotalCost** is a new field</span></span>

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
