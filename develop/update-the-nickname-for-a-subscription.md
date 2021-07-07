---
title: Atualizar a alcunha para uma subscrição
description: Atualiza o nome ou apelido amigável para a Subscrição de um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 195a85fcf29b3e4c9fe0e578d4d8cb80ca068c40
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530009"
---
# <a name="update-the-nickname-for-a-subscription"></a><span data-ttu-id="96b55-103">Atualizar a alcunha para uma subscrição</span><span class="sxs-lookup"><span data-stu-id="96b55-103">Update the nickname for a subscription</span></span>

<span data-ttu-id="96b55-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="96b55-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="96b55-105">Atualiza o nome ou apelido amigável para a [Subscrição](subscription-resources.md)de um cliente .</span><span class="sxs-lookup"><span data-stu-id="96b55-105">Updates the friendly name or nickname for a customer's [Subscription](subscription-resources.md).</span></span> <span data-ttu-id="96b55-106">Este nome aparece no Partner Center para ajudar a diferenciar as subscrições na conta do cliente.</span><span class="sxs-lookup"><span data-stu-id="96b55-106">This name appears in Partner Center to help differentiate the subscriptions in the customer's account.</span></span>

<span data-ttu-id="96b55-107">No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="96b55-107">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="96b55-108">Em seguida, selecione a subscrição em questão que deseja renomear.</span><span class="sxs-lookup"><span data-stu-id="96b55-108">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="96b55-109">Para terminar, mude o nome no campo do **apelido de Assinatura** e, em seguida, selecione **Enviar.**</span><span class="sxs-lookup"><span data-stu-id="96b55-109">To finish, change the name in the **Subscription nickname** field, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96b55-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="96b55-110">Prerequisites</span></span>

- <span data-ttu-id="96b55-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="96b55-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="96b55-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="96b55-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="96b55-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="96b55-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="96b55-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="96b55-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="96b55-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="96b55-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="96b55-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="96b55-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="96b55-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="96b55-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="96b55-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="96b55-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="96b55-119">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="96b55-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="96b55-120">C\#</span><span class="sxs-lookup"><span data-stu-id="96b55-120">C\#</span></span>

<span data-ttu-id="96b55-121">Para atualizar o apelido da subscrição de um cliente, primeiro [obtenha a subscrição,](get-a-subscription-by-id.md)em seguida, altere a propriedade [**FriendlyName**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.friendlyname) da subscrição.</span><span class="sxs-lookup"><span data-stu-id="96b55-121">To update the nickname of a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then change the subscription's [**FriendlyName**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.friendlyname) property.</span></span> <span data-ttu-id="96b55-122">Assim que a alteração for feita, utilize a sua coleção [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="96b55-122">Once the change is made, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="96b55-123">Em seguida, ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método [**ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="96b55-123">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="96b55-124">Em seguida, termine chamando o método [**Patch().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch)</span><span class="sxs-lookup"><span data-stu-id="96b55-124">Then, finish by calling the [**Patch()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var SelectedcustomerId as string;

ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.Get();
Subscription selectedSubscription = customerSubscriptions.Items.FirstOrDefault(sub => sub.Status == SubscriptionStatus.Active);

// Apply changes to subscription;

var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

<span data-ttu-id="96b55-125">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="96b55-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="96b55-126">**Project**: PartnerSDK.FeatureSamples **Class**: UpdateSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="96b55-126">**Project**: PartnerSDK.FeatureSamples **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="96b55-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="96b55-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="96b55-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="96b55-128">Request syntax</span></span>

| <span data-ttu-id="96b55-129">Método</span><span class="sxs-lookup"><span data-stu-id="96b55-129">Method</span></span>    | <span data-ttu-id="96b55-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="96b55-130">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="96b55-131">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="96b55-131">**PATCH**</span></span> | <span data-ttu-id="96b55-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="96b55-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="96b55-133">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="96b55-133">URI parameter</span></span>

<span data-ttu-id="96b55-134">Esta tabela lista o parâmetro de consulta necessário para atualizar o apelido de subscrição.</span><span class="sxs-lookup"><span data-stu-id="96b55-134">This table lists the required query parameter to update the subscription nickname.</span></span>

| <span data-ttu-id="96b55-135">Nome</span><span class="sxs-lookup"><span data-stu-id="96b55-135">Name</span></span>                    | <span data-ttu-id="96b55-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="96b55-136">Type</span></span>     | <span data-ttu-id="96b55-137">Necessário</span><span class="sxs-lookup"><span data-stu-id="96b55-137">Required</span></span> | <span data-ttu-id="96b55-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="96b55-138">Description</span></span>                          |
|-------------------------|----------|----------|--------------------------------------|
| <span data-ttu-id="96b55-139">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="96b55-139">**customer-tenant-id**</span></span>  | <span data-ttu-id="96b55-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="96b55-140">**guid**</span></span> | <span data-ttu-id="96b55-141">Y</span><span class="sxs-lookup"><span data-stu-id="96b55-141">Y</span></span>        | <span data-ttu-id="96b55-142">O **cliente-inquilino-id** (um GUID).</span><span class="sxs-lookup"><span data-stu-id="96b55-142">The **customer-tenant-id** (a GUID).</span></span> |
| <span data-ttu-id="96b55-143">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="96b55-143">**id-for-subscription**</span></span> | <span data-ttu-id="96b55-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="96b55-144">**guid**</span></span> | <span data-ttu-id="96b55-145">Y</span><span class="sxs-lookup"><span data-stu-id="96b55-145">Y</span></span>        | <span data-ttu-id="96b55-146">O ID de assinatura (um GUID).</span><span class="sxs-lookup"><span data-stu-id="96b55-146">The subscription ID (a GUID).</span></span>        |

### <a name="request-headers"></a><span data-ttu-id="96b55-147">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="96b55-147">Request headers</span></span>

<span data-ttu-id="96b55-148">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="96b55-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="96b55-149">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="96b55-149">Request body</span></span>

<span data-ttu-id="96b55-150">É necessário um recurso **de subscrição** completo no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="96b55-150">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="96b55-151">Certifique-se de que a propriedade **FriendlyName** foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="96b55-151">Ensure the **FriendlyName** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="96b55-152">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="96b55-152">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": "<subscriptionID>",
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
    OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="96b55-153">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="96b55-153">REST response</span></span>

<span data-ttu-id="96b55-154">Se for bem sucedido, este método devolve as propriedades atualizadas dos recursos [de subscrição](subscription-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="96b55-154">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="96b55-155">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="96b55-155">Response success and error codes</span></span>

<span data-ttu-id="96b55-156">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="96b55-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="96b55-157">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="96b55-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="96b55-158">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="96b55-158">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="96b55-159">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="96b55-159">Response example</span></span>

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
    "Id": "<subscriptionID>",
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
