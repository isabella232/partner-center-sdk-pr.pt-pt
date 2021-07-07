---
title: Atualizar a renovação automática de uma subscrição de marketplace comercial
description: Atualize a nova propriedade de uma subscrição que corresponda ao ID do cliente e da subscrição.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: cc0b4c4bff5e8762ffcc2552b2e9e36bcf93686c
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446671"
---
# <a name="update-autorenew-for-a-commercial-marketplace-subscription"></a><span data-ttu-id="32795-103">Atualizar a renovação automática de uma subscrição de marketplace comercial</span><span class="sxs-lookup"><span data-stu-id="32795-103">Update autorenew for a commercial marketplace subscription</span></span>

<span data-ttu-id="32795-104">Atualizar a nova propriedade de um mercado comercial O recurso [de subscrição](subscription-resources.md) que corresponda ao ID do cliente e da subscrição.</span><span class="sxs-lookup"><span data-stu-id="32795-104">Update the autorenew property for a commercial marketplace [Subscription](subscription-resources.md) resource that matches the customer and subscription ID.</span></span>

<span data-ttu-id="32795-105">No painel partner center, esta operação é realizada [selecionando](get-a-customer-by-name.md)primeiro um cliente .</span><span class="sxs-lookup"><span data-stu-id="32795-105">In the Partner Center dashboard, this operation is performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="32795-106">Em seguida, selecione a subscrição que deseja atualizar.</span><span class="sxs-lookup"><span data-stu-id="32795-106">Then, select the subscription that you wish to update.</span></span> <span data-ttu-id="32795-107">Finalmente, alternar a opção **de renovação automática** e, em seguida, selecione **Enviar por inteiro**.</span><span class="sxs-lookup"><span data-stu-id="32795-107">Finally, toggle the **Auto-renew** option, then select **Submit**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="32795-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="32795-108">Prerequisites</span></span>

- <span data-ttu-id="32795-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="32795-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="32795-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="32795-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="32795-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="32795-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="32795-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="32795-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="32795-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="32795-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="32795-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="32795-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="32795-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="32795-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="32795-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="32795-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="32795-117">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="32795-117">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="32795-118">C\#</span><span class="sxs-lookup"><span data-stu-id="32795-118">C\#</span></span>

<span data-ttu-id="32795-119">Para atualizar a subscrição de um cliente, primeiro [obtenha a subscrição,](get-a-subscription-by-id.md)em seguida, desafie a propriedade [**autoRenewEnabled**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.autoRenewEnabled) da subscrição.</span><span class="sxs-lookup"><span data-stu-id="32795-119">To update a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then set the subscription's [**autoRenewEnabled**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.autoRenewEnabled) property.</span></span> <span data-ttu-id="32795-120">Assim que a alteração for feita, utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="32795-120">Once the change is made, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="32795-121">Em seguida, ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método [**ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="32795-121">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="32795-122">Em seguida, termine chamando o método **Patch().**</span><span class="sxs-lookup"><span data-stu-id="32795-122">Then, finish by calling the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

// turn off auto renew.
selectedSubscription.AutoRenewEnabled = false;
var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

<span data-ttu-id="32795-123">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="32795-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="32795-124">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="32795-124">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="32795-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="32795-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="32795-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="32795-126">Request syntax</span></span>

| <span data-ttu-id="32795-127">Método</span><span class="sxs-lookup"><span data-stu-id="32795-127">Method</span></span>    | <span data-ttu-id="32795-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="32795-128">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32795-129">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="32795-129">**PATCH**</span></span> | <span data-ttu-id="32795-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="32795-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="32795-131">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="32795-131">URI parameter</span></span>

<span data-ttu-id="32795-132">Esta tabela lista o parâmetro de consulta necessário para suspender a subscrição.</span><span class="sxs-lookup"><span data-stu-id="32795-132">This table lists the required query parameter to suspend the subscription.</span></span>

| <span data-ttu-id="32795-133">Nome</span><span class="sxs-lookup"><span data-stu-id="32795-133">Name</span></span>                    | <span data-ttu-id="32795-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="32795-134">Type</span></span>     | <span data-ttu-id="32795-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="32795-135">Required</span></span> | <span data-ttu-id="32795-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="32795-136">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="32795-137">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="32795-137">**customer-tenant-id**</span></span>  | <span data-ttu-id="32795-138">**GUIADOR**</span><span class="sxs-lookup"><span data-stu-id="32795-138">**GUID**</span></span> | <span data-ttu-id="32795-139">Y</span><span class="sxs-lookup"><span data-stu-id="32795-139">Y</span></span>        | <span data-ttu-id="32795-140">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="32795-140">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="32795-141">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="32795-141">**id-for-subscription**</span></span> | <span data-ttu-id="32795-142">**GUIADOR**</span><span class="sxs-lookup"><span data-stu-id="32795-142">**GUID**</span></span> | <span data-ttu-id="32795-143">Y</span><span class="sxs-lookup"><span data-stu-id="32795-143">Y</span></span>        | <span data-ttu-id="32795-144">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="32795-144">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="32795-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="32795-145">Request headers</span></span>

<span data-ttu-id="32795-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="32795-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="32795-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="32795-147">Request body</span></span>

<span data-ttu-id="32795-148">Um recurso de **subscrição** de mercado comercial completo é necessário no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="32795-148">A full commercial marketplace **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="32795-149">Certifique-se de que a propriedade **AutoRenewEnabled** foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="32795-149">Ensure that the **AutoRenewEnabled** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="32795-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="32795-150">Request example</span></span>

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
    "status": "active",
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

## <a name="rest-response"></a><span data-ttu-id="32795-151">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="32795-151">REST response</span></span>

<span data-ttu-id="32795-152">Se for bem sucedido, este método devolve as propriedades atualizadas dos recursos [de subscrição](subscription-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="32795-152">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="32795-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="32795-153">Response success and error codes</span></span>

<span data-ttu-id="32795-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="32795-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="32795-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="32795-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="32795-156">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="32795-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="32795-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="32795-157">Response example</span></span>

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
    "status": "active",
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
