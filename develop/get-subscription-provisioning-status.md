---
title: Obter o estado de aprovisionamento da subscrição
description: Como obter o estado de provisão de subscrição para uma subscrição de cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 38544aa380ba0a6a8804ae45f7d8ae7cb431d3ba
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769842"
---
# <a name="get-subscription-provisioning-status"></a><span data-ttu-id="7667b-103">Obter o estado de aprovisionamento da subscrição</span><span class="sxs-lookup"><span data-stu-id="7667b-103">Get subscription provisioning status</span></span>

<span data-ttu-id="7667b-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="7667b-104">**Applies To**</span></span>

- <span data-ttu-id="7667b-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="7667b-105">Partner Center</span></span>
- <span data-ttu-id="7667b-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="7667b-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="7667b-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="7667b-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="7667b-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7667b-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7667b-109">Como obter o estado de provisão de subscrição para uma subscrição de cliente.</span><span class="sxs-lookup"><span data-stu-id="7667b-109">How to get the subscription provisioning status for a customer subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7667b-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7667b-110">Prerequisites</span></span>

- <span data-ttu-id="7667b-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7667b-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7667b-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="7667b-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="7667b-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7667b-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7667b-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="7667b-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7667b-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="7667b-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7667b-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="7667b-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7667b-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="7667b-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7667b-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7667b-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7667b-119">Um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="7667b-119">A subscription identifier.</span></span>

- <span data-ttu-id="7667b-120">As permissões de administração delegadas na subscrição são necessárias para realizar esta operação.</span><span class="sxs-lookup"><span data-stu-id="7667b-120">Delegated admin permissions on the subscription are required to perform this operation.</span></span>

## <a name="c"></a><span data-ttu-id="7667b-121">C\#</span><span class="sxs-lookup"><span data-stu-id="7667b-121">C\#</span></span>

<span data-ttu-id="7667b-122">Para obter o estado de provisionamento de uma subscrição, comece por utilizar o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="7667b-122">To get the provisioning status of a subscription, begin by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="7667b-123">Em seguida, obtenha uma interface para as operações de subscrição ligando para o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID de subscrição.</span><span class="sxs-lookup"><span data-stu-id="7667b-123">Then, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="7667b-124">Em seguida, utilize a propriedade [**ProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.provisioningstatus) para obter uma interface para as operações de estado de provisionamento da subscrição atual e, em seguida, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.getasync) para recuperar o objeto [**SubscriptionProvisioningStatus.**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionprovisioningstatus)</span><span class="sxs-lookup"><span data-stu-id="7667b-124">Next, use the [**ProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.provisioningstatus) property to obtain an interface to the current subscription's provisioning status operations, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.getasync) method to retrieve the [**SubscriptionProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionprovisioningstatus) object.</span></span>

``` csharp
// IAggregatePartner partnerOperations.
// string customerId;
// string subscriptionId;

// Retrieve a subscription's provisioning status.
var provisioningStatus = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionID).ProvisioningStatus.Get();
```

## <a name="rest-request"></a><span data-ttu-id="7667b-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="7667b-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7667b-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="7667b-126">Request syntax</span></span>

| <span data-ttu-id="7667b-127">Método</span><span class="sxs-lookup"><span data-stu-id="7667b-127">Method</span></span>  | <span data-ttu-id="7667b-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="7667b-128">Request URI</span></span>                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7667b-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="7667b-129">**GET**</span></span> | <span data-ttu-id="7667b-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/provisioningstatus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7667b-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/provisioningstatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="7667b-131">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="7667b-131">URI parameters</span></span>

<span data-ttu-id="7667b-132">Utilize os seguintes parâmetros de percurso para identificar o cliente e a subscrição.</span><span class="sxs-lookup"><span data-stu-id="7667b-132">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="7667b-133">Nome</span><span class="sxs-lookup"><span data-stu-id="7667b-133">Name</span></span>            | <span data-ttu-id="7667b-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="7667b-134">Type</span></span>   | <span data-ttu-id="7667b-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="7667b-135">Required</span></span> | <span data-ttu-id="7667b-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="7667b-136">Description</span></span>                                               |
|-----------------|--------|----------|-----------------------------------------------------------|
| <span data-ttu-id="7667b-137">id cliente</span><span class="sxs-lookup"><span data-stu-id="7667b-137">customer-id</span></span>     | <span data-ttu-id="7667b-138">string</span><span class="sxs-lookup"><span data-stu-id="7667b-138">string</span></span> | <span data-ttu-id="7667b-139">Sim</span><span class="sxs-lookup"><span data-stu-id="7667b-139">Yes</span></span>      | <span data-ttu-id="7667b-140">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="7667b-140">A GUID formatted string that identifies the customer.</span></span>     |
| <span data-ttu-id="7667b-141">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="7667b-141">subscription-id</span></span> | <span data-ttu-id="7667b-142">string</span><span class="sxs-lookup"><span data-stu-id="7667b-142">string</span></span> | <span data-ttu-id="7667b-143">Sim</span><span class="sxs-lookup"><span data-stu-id="7667b-143">Yes</span></span>      | <span data-ttu-id="7667b-144">Uma cadeia formatada GUID que identifica a subscrição.</span><span class="sxs-lookup"><span data-stu-id="7667b-144">A GUID formatted string that identifies the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="7667b-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="7667b-145">Request headers</span></span>

<span data-ttu-id="7667b-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7667b-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7667b-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="7667b-147">Request body</span></span>

<span data-ttu-id="7667b-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7667b-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7667b-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="7667b-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/34828C05-C16C-4D6F-9CFC-4D2650EF19A1/provisioningstatus HTTP/1.1
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="7667b-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="7667b-150">REST response</span></span>

<span data-ttu-id="7667b-151">Se for bem sucedido, o organismo de resposta contém um recurso [SubscriptionProvisioningStatus.](subscription-resources.md#subscriptionprovisioningstatus)</span><span class="sxs-lookup"><span data-stu-id="7667b-151">If successful, the response body contains a [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7667b-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="7667b-152">Response success and error codes</span></span>

<span data-ttu-id="7667b-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="7667b-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7667b-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="7667b-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7667b-155">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="7667b-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7667b-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="7667b-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CV: InswEQre402koceL.0
MS-ServerId: 030020344
Date: Thu, 20 Apr 2017 19:23:39 GMT

{
    "skuId": "6FD2C87F-B296-42F0-B197-1E91E994B900",
    "status": "success",
    "quantity": 5,
    "endDate": "2018-05-10T00:00:00Z",
    "attributes": {
        "objectType": "SubscriptionProvisioningStatus"
    }
}
```

## <a name="remarks"></a><span data-ttu-id="7667b-157">Observações</span><span class="sxs-lookup"><span data-stu-id="7667b-157">Remarks</span></span>

- <span data-ttu-id="7667b-158">Durante uma atribuição de alteração de licença, o campo de estado no [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) está definido para "pendente".</span><span class="sxs-lookup"><span data-stu-id="7667b-158">During a license change assignment, the status field in [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) is set to "pending".</span></span>

- <span data-ttu-id="7667b-159">O campo de estado é atualizado a cada quinze minutos.</span><span class="sxs-lookup"><span data-stu-id="7667b-159">The status field is updated every fifteen minutes.</span></span>
