---
title: Obter o estado de registo da subscrição
description: Obtenha o estado de uma subscrição que tenha sido registada para uso com Azure Reserved VM Instances.
ms.date: 03/19/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e06cf8a450d6c281f7f83a68c899d1e5b29e9855
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769848"
---
# <a name="get-subscription-registration-status"></a><span data-ttu-id="d0085-103">Obter o estado de registo da subscrição</span><span class="sxs-lookup"><span data-stu-id="d0085-103">Get subscription registration status</span></span>

<span data-ttu-id="d0085-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="d0085-104">**Applies To**</span></span>

- <span data-ttu-id="d0085-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="d0085-105">Partner Center</span></span>

<span data-ttu-id="d0085-106">Como obter o estado de registo de subscrição de uma subscrição de cliente que foi habilitada para a compra de Azure Reserved VM Instances.</span><span class="sxs-lookup"><span data-stu-id="d0085-106">How to get the subscription registration status for a customer subscription that has been enabled for purchasing Azure Reserved VM Instances.</span></span>

<span data-ttu-id="d0085-107">Para adquirir uma Instância VM Reservada Azure utilizando a API do Centro Parceiro, deve ter pelo menos uma subscrição CSP Azure existente.</span><span class="sxs-lookup"><span data-stu-id="d0085-107">To purchase an Azure Reserved VM Instance using the Partner Center API, you must have at least one existing CSP Azure subscription.</span></span> <span data-ttu-id="d0085-108">O Registo de um método [de subscrição](register-a-subscription.md) permite-lhe registar a subscrição CSP Azure existente, permitindo-lhe a aquisição de Azure Reserved VM Instances.</span><span class="sxs-lookup"><span data-stu-id="d0085-108">The [Register a subscription](register-a-subscription.md) method allows you to register your existing CSP Azure subscription, enabling it for purchasing Azure Reserved VM Instances.</span></span> <span data-ttu-id="d0085-109">Este método permite-lhe recuperar o estado desse registo.</span><span class="sxs-lookup"><span data-stu-id="d0085-109">This method allows you to retrieve the status of that registration.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d0085-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d0085-110">Prerequisites</span></span>

- <span data-ttu-id="d0085-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d0085-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d0085-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="d0085-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="d0085-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d0085-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d0085-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d0085-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d0085-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d0085-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d0085-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d0085-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d0085-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d0085-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d0085-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d0085-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d0085-119">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="d0085-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="d0085-120">C\#</span><span class="sxs-lookup"><span data-stu-id="d0085-120">C\#</span></span>

<span data-ttu-id="d0085-121">Para obter o estado de registo de uma subscrição, comece por utilizar o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="d0085-121">To get the registration status of a subscription, begin by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="d0085-122">Em seguida, obtenha uma interface para as operações de subscrição ligando para o método [**Subscrição.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) com o ID de subscrição para identificar a subscrição.</span><span class="sxs-lookup"><span data-stu-id="d0085-122">Then, get an interface to subscription operations by calling the [**Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method with the subscription ID to identify the subscription.</span></span> <span data-ttu-id="d0085-123">Em seguida, utilize a propriedade RegistrationStatus para obter uma interface para as operações de estado de registo da subscrição atual, e ligue para o método **Get** or **GetAsync** para recuperar o objeto **SubscriptionRegistrationStatus.**</span><span class="sxs-lookup"><span data-stu-id="d0085-123">Next, use the RegistrationStatus property to obtain an interface to the current subscription's registration status operations, and call the **Get** or **GetAsync** method to retrieve the **SubscriptionRegistrationStatus** object.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve a subscription's registration status details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).RegistrationStatus.Get();
```

## <a name="rest-request"></a><span data-ttu-id="d0085-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d0085-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d0085-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0085-125">Request syntax</span></span>

| <span data-ttu-id="d0085-126">Método</span><span class="sxs-lookup"><span data-stu-id="d0085-126">Method</span></span>    | <span data-ttu-id="d0085-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d0085-127">Request URI</span></span>                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d0085-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d0085-128">**GET**</span></span>  | <span data-ttu-id="d0085-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/registrationstatus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d0085-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrationstatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="d0085-130">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="d0085-130">URI parameters</span></span>

<span data-ttu-id="d0085-131">Utilize os seguintes parâmetros de percurso para identificar o cliente e a subscrição.</span><span class="sxs-lookup"><span data-stu-id="d0085-131">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="d0085-132">Nome</span><span class="sxs-lookup"><span data-stu-id="d0085-132">Name</span></span>                    | <span data-ttu-id="d0085-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="d0085-133">Type</span></span>       | <span data-ttu-id="d0085-134">Necessário</span><span class="sxs-lookup"><span data-stu-id="d0085-134">Required</span></span> | <span data-ttu-id="d0085-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0085-135">Description</span></span>                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| <span data-ttu-id="d0085-136">id cliente</span><span class="sxs-lookup"><span data-stu-id="d0085-136">customer-id</span></span>             | <span data-ttu-id="d0085-137">string</span><span class="sxs-lookup"><span data-stu-id="d0085-137">string</span></span>     | <span data-ttu-id="d0085-138">Sim</span><span class="sxs-lookup"><span data-stu-id="d0085-138">Yes</span></span>      | <span data-ttu-id="d0085-139">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="d0085-139">A GUID formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="d0085-140">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="d0085-140">subscription-id</span></span>         | <span data-ttu-id="d0085-141">string</span><span class="sxs-lookup"><span data-stu-id="d0085-141">string</span></span>     | <span data-ttu-id="d0085-142">Sim</span><span class="sxs-lookup"><span data-stu-id="d0085-142">Yes</span></span>      | <span data-ttu-id="d0085-143">Uma cadeia formatada GUID que identifica a subscrição.</span><span class="sxs-lookup"><span data-stu-id="d0085-143">A GUID formatted string that identifies the subscription.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="d0085-144">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d0085-144">Request headers</span></span>

<span data-ttu-id="d0085-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d0085-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d0085-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d0085-146">Request body</span></span>

<span data-ttu-id="d0085-147">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d0085-147">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d0085-148">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d0085-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="d0085-149">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d0085-149">REST response</span></span>

<span data-ttu-id="d0085-150">Se for bem sucedido, o organismo de resposta contém um recurso [SubscriptionRegistrationStatus.](subscription-resources.md#subscriptionregistrationstatus)</span><span class="sxs-lookup"><span data-stu-id="d0085-150">If successful, the response body contains a [SubscriptionRegistrationStatus](subscription-resources.md#subscriptionregistrationstatus) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d0085-151">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d0085-151">Response success and error codes</span></span>

<span data-ttu-id="d0085-152">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d0085-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d0085-153">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d0085-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d0085-154">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d0085-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d0085-155">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d0085-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: InswEQre402koceL.0
MS-ServerId: 030020344

{
    "subscriptionId":"<subscription-id>",
    "status":"NotRegistered",
    "attributes":{
        "objectType":"SubscriptionRegistrationStatus"
    }
}
```
