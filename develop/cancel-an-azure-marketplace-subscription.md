---
title: Cancelar uma subscrição de marketplace comercial
description: Saiba como usar as APIs do Partner Center para cancelar um recurso de subscrição de mercado comercial que corresponda a um ID de cliente e subscrição.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 95fa265a3c103d1ec55066f12a3ede7fdb2d0170
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974289"
---
# <a name="cancel-a-commercial-marketplace-subscription-using-partner-center-apis"></a><span data-ttu-id="49b04-103">Cancelar uma subscrição de marketplace comercial usando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="49b04-103">Cancel a commercial marketplace subscription using Partner Center APIs</span></span>

<span data-ttu-id="49b04-104">Este artigo descreve como pode usar a API do Partner Center para cancelar um recurso de [subscrição](subscription-resources.md) de marketplace comercial que corresponda ao ID do cliente e da subscrição.</span><span class="sxs-lookup"><span data-stu-id="49b04-104">This article describes how you can use Partner Center API to cancel a commercial marketplace [subscription](subscription-resources.md) resource that matches the customer and subscription ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49b04-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="49b04-105">Prerequisites</span></span>

- <span data-ttu-id="49b04-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="49b04-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="49b04-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="49b04-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="49b04-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="49b04-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="49b04-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="49b04-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="49b04-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="49b04-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="49b04-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="49b04-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="49b04-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="49b04-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="49b04-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="49b04-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="49b04-114">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="49b04-114">A subscription ID.</span></span>

## <a name="partner-center-dashboard-method"></a><span data-ttu-id="49b04-115">Método do painel do Centro Parceiro</span><span class="sxs-lookup"><span data-stu-id="49b04-115">Partner Center dashboard method</span></span>

<span data-ttu-id="49b04-116">Para cancelar uma subscrição de mercado comercial no painel partner center:</span><span class="sxs-lookup"><span data-stu-id="49b04-116">To cancel a commercial marketplace subscription in the Partner Center dashboard:</span></span>

1. <span data-ttu-id="49b04-117">[Selecione um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="49b04-117">[Select a customer](get-a-customer-by-name.md).</span></span>

2. <span data-ttu-id="49b04-118">Selecione a subscrição que deseja cancelar.</span><span class="sxs-lookup"><span data-stu-id="49b04-118">Select the subscription that you wish to cancel.</span></span>

3. <span data-ttu-id="49b04-119">Escolha a opção **de subscrição cancelar** e, em seguida, selecione **Enviar por email o que se possa fazer.**</span><span class="sxs-lookup"><span data-stu-id="49b04-119">Choose the **Cancel subscription** option, then select **Submit**.</span></span>

## <a name="c"></a><span data-ttu-id="49b04-120">C\#</span><span class="sxs-lookup"><span data-stu-id="49b04-120">C\#</span></span>

<span data-ttu-id="49b04-121">Para cancelar a subscrição de um cliente:</span><span class="sxs-lookup"><span data-stu-id="49b04-121">To cancel a customer's subscription:</span></span>

1. <span data-ttu-id="49b04-122">[Obtenha a subscrição por ID](get-a-subscription-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="49b04-122">[Get the subscription by ID](get-a-subscription-by-id.md).</span></span>

2. <span data-ttu-id="49b04-123">Alterar a propriedade [**status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) da subscrição.</span><span class="sxs-lookup"><span data-stu-id="49b04-123">Change the subscription's [**Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property.</span></span> <span data-ttu-id="49b04-124">Para obter informações sobre códigos **de estado,** consulte [a enumeração SubscriptionStatus](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span><span class="sxs-lookup"><span data-stu-id="49b04-124">For information on **Status** codes, see [SubscriptionStatus enumeration](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span>

3. <span data-ttu-id="49b04-125">Depois de escorção da alteração, utilize a sua **`IAggregatePartner.Customers`** coleção e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="49b04-125">After the change is made, use your **`IAggregatePartner.Customers`** collection and call the **ById()** method.</span></span>

4. <span data-ttu-id="49b04-126">Ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método [**ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="49b04-126">Call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span>

5. <span data-ttu-id="49b04-127">Ligue para o método **Patch().**</span><span class="sxs-lookup"><span data-stu-id="49b04-127">Call the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

selectedSubscription.Status = SubscriptionStatus.Deleted;
var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

### <a name="sample-console-test-app"></a><span data-ttu-id="49b04-128">Aplicação de teste de consola de amostra</span><span class="sxs-lookup"><span data-stu-id="49b04-128">Sample console test app</span></span>

<span data-ttu-id="49b04-129">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="49b04-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="49b04-130">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="49b04-130">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="49b04-131">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="49b04-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="49b04-132">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="49b04-132">Request syntax</span></span>

| <span data-ttu-id="49b04-133">Método</span><span class="sxs-lookup"><span data-stu-id="49b04-133">Method</span></span>    | <span data-ttu-id="49b04-134">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="49b04-134">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="49b04-135">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="49b04-135">**PATCH**</span></span> | <span data-ttu-id="49b04-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="49b04-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="49b04-137">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="49b04-137">URI parameter</span></span>

<span data-ttu-id="49b04-138">Esta tabela lista o parâmetro de consulta necessário para suspender a subscrição.</span><span class="sxs-lookup"><span data-stu-id="49b04-138">This table lists the required query parameter to suspend the subscription.</span></span>

| <span data-ttu-id="49b04-139">Nome</span><span class="sxs-lookup"><span data-stu-id="49b04-139">Name</span></span>                    | <span data-ttu-id="49b04-140">Tipo</span><span class="sxs-lookup"><span data-stu-id="49b04-140">Type</span></span>     | <span data-ttu-id="49b04-141">Necessário</span><span class="sxs-lookup"><span data-stu-id="49b04-141">Required</span></span> | <span data-ttu-id="49b04-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="49b04-142">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="49b04-143">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="49b04-143">**customer-tenant-id**</span></span>  | <span data-ttu-id="49b04-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="49b04-144">**guid**</span></span> | <span data-ttu-id="49b04-145">Y</span><span class="sxs-lookup"><span data-stu-id="49b04-145">Y</span></span>        | <span data-ttu-id="49b04-146">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="49b04-146">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="49b04-147">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="49b04-147">**id-for-subscription**</span></span> | <span data-ttu-id="49b04-148">**guid**</span><span class="sxs-lookup"><span data-stu-id="49b04-148">**guid**</span></span> | <span data-ttu-id="49b04-149">Y</span><span class="sxs-lookup"><span data-stu-id="49b04-149">Y</span></span>        | <span data-ttu-id="49b04-150">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="49b04-150">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="49b04-151">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="49b04-151">Request headers</span></span>

<span data-ttu-id="49b04-152">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="49b04-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="49b04-153">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="49b04-153">Request body</span></span>

<span data-ttu-id="49b04-154">É necessário um recurso **de subscrição** completo no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="49b04-154">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="49b04-155">Certifique-se de que a propriedade **Status** foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="49b04-155">Ensure that the **Status** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="49b04-156">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="49b04-156">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
If-Match: <etag>
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "deleted",
    "autoRenewEnabled": false,
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [{
        "type": "Full",
        "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
    }],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "publisherName": "publisher Name",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {"objectType": "Subscription"},
}
```

## <a name="rest-response"></a><span data-ttu-id="49b04-157">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="49b04-157">REST response</span></span>

<span data-ttu-id="49b04-158">Se for bem sucedido, este método devolve as propriedades de recursos [de subscrição](subscription-resources.md) eliminadas no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="49b04-158">If successful, this method returns deleted [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="49b04-159">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="49b04-159">Response success and error codes</span></span>

<span data-ttu-id="49b04-160">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="49b04-160">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="49b04-161">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="49b04-161">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="49b04-162">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="49b04-162">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="49b04-163">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="49b04-163">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1322
Content-Type: application/json; charset=utf-8
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
X-Locale: en-US

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "deleted",
    "autoRenewEnabled": false,
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [
        {
            "type": "Full",
            "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
        }
    ],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "links": {
        "product": {
            "uri": "/products/DZH318Z0BXWC?country=US",
            "method": "GET",
            "headers": []
        },
        "sku": {
            "uri": "/products/DZH318Z0BXWC/skus/0001?country=US",
            "method": "GET",
            "headers": []
        },
        "availability": {
            "uri": "/products/DZH318Z0BXWC/skus/0001/availabilities/DZH318Z0BMJX?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/5921f00a-32c0-4457-aaa1-e8018c650895/subscriptions/6e7aa601-629e-461b-8933-0898c3cc3c7c",
            "method": "GET",
            "headers": []
        }
    },
    "publisherName": "publishe rName",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {
        "etag": "",
        "objectType": "Subscription"
    }
}
```
