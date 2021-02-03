---
title: Suspender uma subscrição
description: Suspende um recurso de Subscrição que corresponda ao ID do cliente e subscrição devido a fraude ou não pagamento. No painel partner Center, esta operação pode ser realizada selecionando primeiro um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f351c87efe2bdc810a66c64a9d01b7d376f8a6e3
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769596"
---
# <a name="suspend-a-subscription"></a><span data-ttu-id="01cd7-103">Suspender uma subscrição</span><span class="sxs-lookup"><span data-stu-id="01cd7-103">Suspend a subscription</span></span>

<span data-ttu-id="01cd7-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="01cd7-104">**Applies To**</span></span>

- <span data-ttu-id="01cd7-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="01cd7-105">Partner Center</span></span>
- <span data-ttu-id="01cd7-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="01cd7-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="01cd7-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="01cd7-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="01cd7-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="01cd7-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="01cd7-109">Suspende um recurso [de Subscrição](subscription-resources.md) que corresponda ao ID do cliente e subscrição devido a fraude ou não pagamento.</span><span class="sxs-lookup"><span data-stu-id="01cd7-109">Suspends a [Subscription](subscription-resources.md) resource that matches the customer and subscription ID due to fraud or non-payment.</span></span>

<span data-ttu-id="01cd7-110">No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="01cd7-110">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="01cd7-111">Em seguida, selecione a subscrição em questão que deseja renomear.</span><span class="sxs-lookup"><span data-stu-id="01cd7-111">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="01cd7-112">Para terminar, escolha o botão **Suspenso** e, em seguida, selecione **Enviar por isso.**</span><span class="sxs-lookup"><span data-stu-id="01cd7-112">To finish, choose the **Suspended** button, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="01cd7-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="01cd7-113">Prerequisites</span></span>

- <span data-ttu-id="01cd7-114">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="01cd7-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="01cd7-115">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="01cd7-115">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="01cd7-116">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="01cd7-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="01cd7-117">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="01cd7-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="01cd7-118">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="01cd7-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="01cd7-119">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="01cd7-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="01cd7-120">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="01cd7-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="01cd7-121">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="01cd7-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="01cd7-122">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="01cd7-122">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="01cd7-123">C\#</span><span class="sxs-lookup"><span data-stu-id="01cd7-123">C\#</span></span>

<span data-ttu-id="01cd7-124">Para suspender a subscrição de um cliente, primeiro [obtenha a subscrição,](get-a-subscription-by-id.md)em seguida, altere a propriedade [**status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) da subscrição.</span><span class="sxs-lookup"><span data-stu-id="01cd7-124">To suspend a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then change the subscription's [**Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property.</span></span> <span data-ttu-id="01cd7-125">Para obter informações sobre códigos **de estado,** consulte [Subscrição Estatística/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span><span class="sxs-lookup"><span data-stu-id="01cd7-125">For information on **Status** codes, consult [SubscriptionStatus enumeration/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span> <span data-ttu-id="01cd7-126">Assim que a alteração for feita, utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="01cd7-126">Once the change is made, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="01cd7-127">Em seguida, ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método [**ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="01cd7-127">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="01cd7-128">Em seguida, termine chamando o método **Patch().**</span><span class="sxs-lookup"><span data-stu-id="01cd7-128">Then, finish by calling the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(
   new Subscription()
   {
      Status = SubscriptionStatus.Suspended
   });
```

<span data-ttu-id="01cd7-129">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="01cd7-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="01cd7-130">**Projeto**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="01cd7-130">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="01cd7-131">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="01cd7-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="01cd7-132">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="01cd7-132">Request syntax</span></span>

| <span data-ttu-id="01cd7-133">Método</span><span class="sxs-lookup"><span data-stu-id="01cd7-133">Method</span></span>    | <span data-ttu-id="01cd7-134">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="01cd7-134">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="01cd7-135">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="01cd7-135">**PATCH**</span></span> | <span data-ttu-id="01cd7-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="01cd7-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="01cd7-137">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="01cd7-137">URI parameter</span></span>

<span data-ttu-id="01cd7-138">Esta tabela lista o parâmetro de consulta necessário para suspender a subscrição.</span><span class="sxs-lookup"><span data-stu-id="01cd7-138">This table lists the required query parameter to suspend the subscription.</span></span>

| <span data-ttu-id="01cd7-139">Nome</span><span class="sxs-lookup"><span data-stu-id="01cd7-139">Name</span></span>                    | <span data-ttu-id="01cd7-140">Tipo</span><span class="sxs-lookup"><span data-stu-id="01cd7-140">Type</span></span>     | <span data-ttu-id="01cd7-141">Necessário</span><span class="sxs-lookup"><span data-stu-id="01cd7-141">Required</span></span> | <span data-ttu-id="01cd7-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="01cd7-142">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="01cd7-143">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="01cd7-143">**customer-tenant-id**</span></span>  | <span data-ttu-id="01cd7-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="01cd7-144">**guid**</span></span> | <span data-ttu-id="01cd7-145">Y</span><span class="sxs-lookup"><span data-stu-id="01cd7-145">Y</span></span>        | <span data-ttu-id="01cd7-146">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="01cd7-146">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="01cd7-147">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="01cd7-147">**id-for-subscription**</span></span> | <span data-ttu-id="01cd7-148">**guid**</span><span class="sxs-lookup"><span data-stu-id="01cd7-148">**guid**</span></span> | <span data-ttu-id="01cd7-149">Y</span><span class="sxs-lookup"><span data-stu-id="01cd7-149">Y</span></span>        | <span data-ttu-id="01cd7-150">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="01cd7-150">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="01cd7-151">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="01cd7-151">Request headers</span></span>

<span data-ttu-id="01cd7-152">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="01cd7-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="01cd7-153">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="01cd7-153">Request body</span></span>

<span data-ttu-id="01cd7-154">É necessário um recurso **de subscrição** completo no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="01cd7-154">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="01cd7-155">Certifique-se de que a propriedade **Status** foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="01cd7-155">Ensure that the **Status** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="01cd7-156">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="01cd7-156">Request example</span></span>

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
    "Id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
    "FriendlyName": "nickname",
    "Quantity": 2,
    "UnitType": "none",
    "ParentSubscriptionId": null,
    "CreationDate": "2015-11-25T06:41:12Z",
    "EffectiveStartDate": "2015-11-24T08:00:00Z",
    "CommitmentEndDate": "2016-12-12T08:00:00Z",
    "Status": "suspended",
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

## <a name="rest-response"></a><span data-ttu-id="01cd7-157">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="01cd7-157">REST response</span></span>

<span data-ttu-id="01cd7-158">Se for bem sucedido, este método devolve as propriedades atualizadas dos recursos [de subscrição](subscription-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="01cd7-158">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="01cd7-159">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="01cd7-159">Response success and error codes</span></span>

<span data-ttu-id="01cd7-160">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="01cd7-160">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="01cd7-161">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="01cd7-161">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="01cd7-162">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="01cd7-162">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="01cd7-163">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="01cd7-163">Response example</span></span>

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
    "Status": "suspended",
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
