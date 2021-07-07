---
title: Alterar a quantidade de uma subscrição
description: Saiba como utilizar as APIs do Partner Center para alterar a quantidade de licenças para uma subscrição de clientes. Também pode fazê-lo no painel partner Center.
ms.date: 06/05/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d57ece4dd19ef2852f39130916222c54a9ccc85a
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974102"
---
# <a name="change-the-quantity-of-licenses-in-a-customer-subscription"></a><span data-ttu-id="bcfc5-104">Alterar a quantidade de licenças numa subscrição de cliente</span><span class="sxs-lookup"><span data-stu-id="bcfc5-104">Change the quantity of licenses in a customer subscription</span></span>

<span data-ttu-id="bcfc5-105">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="bcfc5-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="bcfc5-106">Atualiza uma [subscrição](subscription-resources.md) para aumentar ou diminuir a quantidade de licenças.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-106">Updates a [subscription](subscription-resources.md) to increase or decrease the quantity of licenses.</span></span>

<span data-ttu-id="bcfc5-107">No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="bcfc5-107">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="bcfc5-108">Em seguida, selecione a subscrição em questão que deseja renomear.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-108">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="bcfc5-109">Para terminar, altere o valor no campo **Quantidade** e, em seguida, selecione **Enviar.**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-109">To finish, change the value in the **Quantity** field, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bcfc5-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bcfc5-110">Prerequisites</span></span>

- <span data-ttu-id="bcfc5-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bcfc5-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bcfc5-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="bcfc5-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bcfc5-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="bcfc5-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="bcfc5-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="bcfc5-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="bcfc5-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="bcfc5-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bcfc5-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="bcfc5-119">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="bcfc5-120">C\#</span><span class="sxs-lookup"><span data-stu-id="bcfc5-120">C\#</span></span>

<span data-ttu-id="bcfc5-121">Para alterar a quantidade da subscrição de um cliente, primeiro [obtenha a subscrição,](get-a-subscription-by-id.md)em seguida, altere a propriedade [**quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.quantity) da subscrição.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-121">To change the quantity of a customer's subscription, first [get the subscription](get-a-subscription-by-id.md), then change the subscription's [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.quantity) property.</span></span> <span data-ttu-id="bcfc5-122">Assim que a alteração for feita, utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-122">Once the change is made, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="bcfc5-123">Em seguida, ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método [**ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="bcfc5-123">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="bcfc5-124">Em seguida, termine chamando o método **Patch().**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-124">Then, finish by calling the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var customerId;
// var subscriptionId;

//retrieving the subscription, for the purpose of the sample
ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.Get();
Subscription selectedSubscription = customerSubscriptions.Items.FirstOrDefault(sub => sub.Status == SubscriptionStatus.Active);

//update selected subscription,
selectedSubscription.Quantity++;

var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

<span data-ttu-id="bcfc5-125">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="bcfc5-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="bcfc5-126">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="bcfc5-126">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="bcfc5-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="bcfc5-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bcfc5-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="bcfc5-128">Request syntax</span></span>

| <span data-ttu-id="bcfc5-129">Método</span><span class="sxs-lookup"><span data-stu-id="bcfc5-129">Method</span></span>    | <span data-ttu-id="bcfc5-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="bcfc5-130">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bcfc5-131">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-131">**PATCH**</span></span> | <span data-ttu-id="bcfc5-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="bcfc5-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="bcfc5-133">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="bcfc5-133">URI parameter</span></span>

<span data-ttu-id="bcfc5-134">Esta tabela lista o parâmetro de consulta necessário para alterar a quantidade da subscrição.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-134">This table lists the required query parameter to change the quantity of the subscription.</span></span>

| <span data-ttu-id="bcfc5-135">Nome</span><span class="sxs-lookup"><span data-stu-id="bcfc5-135">Name</span></span>                    | <span data-ttu-id="bcfc5-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="bcfc5-136">Type</span></span>     | <span data-ttu-id="bcfc5-137">Necessário</span><span class="sxs-lookup"><span data-stu-id="bcfc5-137">Required</span></span> | <span data-ttu-id="bcfc5-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcfc5-138">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="bcfc5-139">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-139">**customer-tenant-id**</span></span>  | <span data-ttu-id="bcfc5-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-140">**guid**</span></span> | <span data-ttu-id="bcfc5-141">Y</span><span class="sxs-lookup"><span data-stu-id="bcfc5-141">Y</span></span>        | <span data-ttu-id="bcfc5-142">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-142">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="bcfc5-143">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-143">**id-for-subscription**</span></span> | <span data-ttu-id="bcfc5-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-144">**guid**</span></span> | <span data-ttu-id="bcfc5-145">Y</span><span class="sxs-lookup"><span data-stu-id="bcfc5-145">Y</span></span>        | <span data-ttu-id="bcfc5-146">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-146">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="bcfc5-147">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="bcfc5-147">Request headers</span></span>

<span data-ttu-id="bcfc5-148">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="bcfc5-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bcfc5-149">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="bcfc5-149">Request body</span></span>

<span data-ttu-id="bcfc5-150">É necessário um recurso **de subscrição** completo no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-150">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="bcfc5-151">Certifique-se de que a propriedade **Quantidade** foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-151">Ensure that the **Quantity** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="bcfc5-152">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="bcfc5-152">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
    "FriendlyName": "nickname",
    "Quantity": 2,
    "UnitType": "none",
    "ParentSubscriptionId": null,
    "CreationDate": "2015-11-25T06:41:12Z",
    "EffectiveStartDate": "2015-11-24T08:00:00Z",
    "CommitmentEndDate": "2016-12-12T08:00:00Z",
    "Status": "active",
    "AutoRenewEnabled": false,
    "BillingType": "none",
    "PartnerId": null,
    "ContractType": "subscription",
    "OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="bcfc5-153">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="bcfc5-153">REST response</span></span>

<span data-ttu-id="bcfc5-154">Se for bem sucedido, este método devolve um código de estado **HTTP 200** e atualiza as propriedades [dos recursos de subscrição](subscription-resources.md)  no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-154">If successful, this method returns an **HTTP status 200** status code and updated [subscription resource](subscription-resources.md)  properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bcfc5-155">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="bcfc5-155">Response success and error codes</span></span>

<span data-ttu-id="bcfc5-156">Cada resposta devolve um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-156">Each response returns an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bcfc5-157">Utilize uma ferramenta de rastreio de rede para ler o código de estado, o tipo de erro e os parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-157">Use a network trace tool to read the status code, error type, and additional parameters.</span></span> <span data-ttu-id="bcfc5-158">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="bcfc5-158">For the full list, see [Error Codes](error-codes.md).</span></span>

<span data-ttu-id="bcfc5-159">Quando a operação de correção demorar mais do que o tempo esperado, o Partner Center envia um código de estado **HTTP 202** e um cabeçalho de localização que aponta para onde recuperar a subscrição.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-159">When the patch operation takes longer than the expected time, the Partner Center sends an **HTTP status 202** status code and a location header that points to where to retrieve the subscription.</span></span> <span data-ttu-id="bcfc5-160">Pode consultar periodicamente a subscrição para monitorizar o estado e as alterações de quantidade.</span><span class="sxs-lookup"><span data-stu-id="bcfc5-160">You can query the subscription periodically to monitor the status and quantity changes.</span></span>

### <a name="response-examples"></a><span data-ttu-id="bcfc5-161">Exemplos de resposta</span><span class="sxs-lookup"><span data-stu-id="bcfc5-161">Response examples</span></span>

#### <a name="response-example-1"></a><span data-ttu-id="bcfc5-162">Exemplo de resposta 1</span><span class="sxs-lookup"><span data-stu-id="bcfc5-162">Response example 1</span></span>

<span data-ttu-id="bcfc5-163">Pedido de sucesso com um código de estado **HTTP 200:**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-163">Successful request with an **HTTP status 200** status code:</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-Contract-Version: v1
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
    "FriendlyName": "nickname",
    "Quantity": 2,
    "UnitType": "none",
    "ParentSubscriptionId": null,
    "CreationDate": "2015-11-25T06:41:12Z",
    "EffectiveStartDate": "2015-11-24T08:00:00Z",
    "CommitmentEndDate": "2016-12-12T08:00:00Z",
    "Status": "active",
    "AutoRenewEnabled": false,
    "BillingType": "none",
    "PartnerId": null,
    "ContractType": "subscription",
    "Links": {
        "Offer": {
            "Uri": "/v1/offers/0CCA44D6-68E9-4762-94EE-31ECE98783B9",
            "Method": "GET",
            "Headers": []
        },
        "Entitlement": {
            "Uri": "/entitlements?key=<key>",
            "Method": "GET",
            "Headers": []
        },
        "Self": {
            "Uri": "/subscriptions?key=<key>",
            "Method": "GET",
            "Headers": []
        }
    },
    "OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```

#### <a name="response-example-2"></a><span data-ttu-id="bcfc5-164">Exemplo de resposta 2</span><span class="sxs-lookup"><span data-stu-id="bcfc5-164">Response example 2</span></span>

<span data-ttu-id="bcfc5-165">Pedido de sucesso com um código de estado **HTTP 202:**</span><span class="sxs-lookup"><span data-stu-id="bcfc5-165">Successful request with an **HTTP status 202** status code:</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 01880c1b-1966-40f0-d470-501a66d9948b
MS-CorrelationId: 2c5827c1-d5f9-4835-cc6d-f1918b782c79
Content-Type: application/json
Content-Length: 1432
Connection: Keep-Alive
Location: /customers/<customer-tenant-id>/subscriptions/<subscriptionID>
```
