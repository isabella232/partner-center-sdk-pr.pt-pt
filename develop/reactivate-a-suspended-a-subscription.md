---
title: Reativar uma subscrição suspensa
description: Reativa uma Subscrição que foi previamente suspensa por não pagamento. No painel partner Center, esta operação pode ser realizada selecionando primeiro um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c2b6e3574119f9c645cc3f730047d2a23484ad8a
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547720"
---
# <a name="reactivate-a-suspended-subscription"></a><span data-ttu-id="70975-104">Reativar uma subscrição suspensa</span><span class="sxs-lookup"><span data-stu-id="70975-104">Reactivate a suspended subscription</span></span>

<span data-ttu-id="70975-105">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="70975-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="70975-106">Reativa uma [Subscrição](subscription-resources.md) que foi previamente suspensa por não pagamento.</span><span class="sxs-lookup"><span data-stu-id="70975-106">Reactivates a [Subscription](subscription-resources.md) that was previously suspended for nonpayment.</span></span>

<span data-ttu-id="70975-107">No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="70975-107">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="70975-108">Em seguida, selecione a subscrição em questão que deseja renomear.</span><span class="sxs-lookup"><span data-stu-id="70975-108">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="70975-109">Para terminar, escolha o botão **Ative** e, em seguida, selecione **Enviar por isso.**</span><span class="sxs-lookup"><span data-stu-id="70975-109">To finish, choose the **Active** button, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70975-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="70975-110">Prerequisites</span></span>

- <span data-ttu-id="70975-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="70975-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="70975-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="70975-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="70975-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="70975-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="70975-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="70975-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="70975-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="70975-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="70975-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="70975-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="70975-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="70975-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="70975-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="70975-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="70975-119">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="70975-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="70975-120">C\#</span><span class="sxs-lookup"><span data-stu-id="70975-120">C\#</span></span>

<span data-ttu-id="70975-121">Para reativar a subscrição de um cliente, primeiro [obtenha a subscrição,](get-a-subscription-by-id.md)em seguida, altere a propriedade [**Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) da subscrição.</span><span class="sxs-lookup"><span data-stu-id="70975-121">To reactivate a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then change the subscription's [**Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property.</span></span> <span data-ttu-id="70975-122">Para obter informações sobre códigos **de estado,** consulte [Subscrição Estatística/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span><span class="sxs-lookup"><span data-stu-id="70975-122">For information on **Status** codes, consult [SubscriptionStatus enumeration/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span> <span data-ttu-id="70975-123">Assim que a alteração for feita, utilize a sua coleção [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="70975-123">Once the change is made, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="70975-124">Em seguida, ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método [**ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="70975-124">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="70975-125">Em seguida, termine chamando o método [**Patch().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch)</span><span class="sxs-lookup"><span data-stu-id="70975-125">Then, finish by calling the [**Patch()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) method.</span></span>

``` csharp
// IPartner partnerOperations;
// var selectedCustomer as Customer;
// var selectedSubscription as Subscription;

updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(
   new Subscription()
   {
      Status = SubscriptionStatus.Active
   });

```

<span data-ttu-id="70975-126">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="70975-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="70975-127">**Project**: FuncionalidadessamplesApplicação.</span><span class="sxs-lookup"><span data-stu-id="70975-127">**Project**: FeatureSamplesApplication.</span></span> <span data-ttu-id="70975-128">**Classe**: ActualizaçõesSubscrição</span><span class="sxs-lookup"><span data-stu-id="70975-128">**Class**: UpdateSubscription</span></span>

## <a name="rest-request"></a><span data-ttu-id="70975-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="70975-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="70975-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="70975-130">Request syntax</span></span>

| <span data-ttu-id="70975-131">Método</span><span class="sxs-lookup"><span data-stu-id="70975-131">Method</span></span>    | <span data-ttu-id="70975-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="70975-132">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="70975-133">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="70975-133">**PATCH**</span></span> | <span data-ttu-id="70975-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="70975-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="70975-135">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="70975-135">URI parameter</span></span>

<span data-ttu-id="70975-136">Esta tabela lista o parâmetro de consulta necessário para reativar a subscrição.</span><span class="sxs-lookup"><span data-stu-id="70975-136">This table lists the required query parameter to reactivate the subscription.</span></span>

| <span data-ttu-id="70975-137">Nome</span><span class="sxs-lookup"><span data-stu-id="70975-137">Name</span></span>                    | <span data-ttu-id="70975-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="70975-138">Type</span></span>     | <span data-ttu-id="70975-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="70975-139">Required</span></span> | <span data-ttu-id="70975-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="70975-140">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="70975-141">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="70975-141">**customer-tenant-id**</span></span>  | <span data-ttu-id="70975-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="70975-142">**guid**</span></span> | <span data-ttu-id="70975-143">Y</span><span class="sxs-lookup"><span data-stu-id="70975-143">Y</span></span>        | <span data-ttu-id="70975-144">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="70975-144">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="70975-145">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="70975-145">**id-for-subscription**</span></span> | <span data-ttu-id="70975-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="70975-146">**guid**</span></span> | <span data-ttu-id="70975-147">Y</span><span class="sxs-lookup"><span data-stu-id="70975-147">Y</span></span>        | <span data-ttu-id="70975-148">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="70975-148">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="70975-149">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="70975-149">Request headers</span></span>

<span data-ttu-id="70975-150">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="70975-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="70975-151">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="70975-151">Request body</span></span>

<span data-ttu-id="70975-152">É necessário um recurso **de subscrição** completo no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="70975-152">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="70975-153">Certifique-se de que a propriedade **Status** foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="70975-153">Ensure that the **Status** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="70975-154">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="70975-154">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="70975-155">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="70975-155">REST response</span></span>

<span data-ttu-id="70975-156">Se for bem sucedido, este método devolve as propriedades atualizadas dos recursos [de subscrição](subscription-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="70975-156">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="70975-157">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="70975-157">Response success and error codes</span></span>

<span data-ttu-id="70975-158">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="70975-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="70975-159">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="70975-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="70975-160">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="70975-160">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="70975-161">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="70975-161">Response example</span></span>

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
