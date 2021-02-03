---
title: Registar uma subscrição
description: Registe uma subscrição existente de modo a que possa encomendar reservas Azure.
ms.date: 07/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9a96bb350f22430c9fd7a1759e336cc9f3ca1939
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769650"
---
# <a name="register-a-subscription"></a><span data-ttu-id="63dec-103">Registar uma subscrição</span><span class="sxs-lookup"><span data-stu-id="63dec-103">Register a subscription</span></span>

<span data-ttu-id="63dec-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="63dec-104">**Applies To**</span></span>

- <span data-ttu-id="63dec-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="63dec-105">Partner Center</span></span>

<span data-ttu-id="63dec-106">Registe uma [Subscrição](subscription-resources.md) existente de modo a que possa encomendar reservas Azure.</span><span class="sxs-lookup"><span data-stu-id="63dec-106">Register an existing [Subscription](subscription-resources.md) so that it is enabled for ordering Azure reservations.</span></span>

<span data-ttu-id="63dec-107">Para adquirir uma reserva Azure deve ter pelo menos uma subscrição CSP Azure existente.</span><span class="sxs-lookup"><span data-stu-id="63dec-107">To purchase an Azure reservation you must have at least one existing CSP Azure subscription.</span></span> <span data-ttu-id="63dec-108">Este método permite-lhe registar a subscrição CSP Azure existente, permitindo-lhe a compra de reservas Azure.</span><span class="sxs-lookup"><span data-stu-id="63dec-108">This method allows you to register your existing CSP Azure subscription, enabling it for purchasing Azure reservations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63dec-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="63dec-109">Prerequisites</span></span>

- <span data-ttu-id="63dec-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="63dec-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="63dec-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="63dec-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="63dec-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="63dec-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="63dec-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="63dec-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="63dec-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="63dec-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="63dec-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="63dec-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="63dec-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="63dec-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="63dec-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="63dec-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="63dec-118">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="63dec-118">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="63dec-119">C\#</span><span class="sxs-lookup"><span data-stu-id="63dec-119">C\#</span></span>

<span data-ttu-id="63dec-120">Para registar a subscrição de um cliente, recupere uma interface para operações de subscrição ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="63dec-120">To register a customer's subscription, retrieve an interface to subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="63dec-121">Em seguida, ligue para o método [**Subscrição.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) com o ID de subscrição para identificar a subscrição que está a registar.</span><span class="sxs-lookup"><span data-stu-id="63dec-121">Then, call the [**Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method with the subscription ID to identify the subscription that you are registering.</span></span>

<span data-ttu-id="63dec-122">Por fim, ligue para o método **Registo.Registo()** para registar a subscrição e recuperar um URI que pode ser usado para obter o estado de registo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="63dec-122">Finally, call the **Registration.Register()** method to register the subscription and retrieve a URI that can be used to get the subscription registration status.</span></span> <span data-ttu-id="63dec-123">Para mais informações, consulte [obter o estado de registo de assinatura.](get-subscription-registration-status.md)</span><span class="sxs-lookup"><span data-stu-id="63dec-123">For more information, see [Get subscription registration status](get-subscription-registration-status.md).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve the subscription registration details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).Registration.Register();
```

## <a name="rest-request"></a><span data-ttu-id="63dec-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="63dec-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="63dec-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="63dec-125">Request syntax</span></span>

| <span data-ttu-id="63dec-126">Método</span><span class="sxs-lookup"><span data-stu-id="63dec-126">Method</span></span>    | <span data-ttu-id="63dec-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="63dec-127">Request URI</span></span>                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="63dec-128">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="63dec-128">**POST**</span></span>  | <span data-ttu-id="63dec-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/registos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="63dec-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="63dec-130">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="63dec-130">URI parameters</span></span>

<span data-ttu-id="63dec-131">Utilize os seguintes parâmetros de percurso para identificar o cliente e a subscrição.</span><span class="sxs-lookup"><span data-stu-id="63dec-131">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="63dec-132">Nome</span><span class="sxs-lookup"><span data-stu-id="63dec-132">Name</span></span>                    | <span data-ttu-id="63dec-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="63dec-133">Type</span></span>       | <span data-ttu-id="63dec-134">Necessário</span><span class="sxs-lookup"><span data-stu-id="63dec-134">Required</span></span> | <span data-ttu-id="63dec-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="63dec-135">Description</span></span>                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| <span data-ttu-id="63dec-136">id cliente</span><span class="sxs-lookup"><span data-stu-id="63dec-136">customer-id</span></span>             | <span data-ttu-id="63dec-137">string</span><span class="sxs-lookup"><span data-stu-id="63dec-137">string</span></span>     | <span data-ttu-id="63dec-138">Sim</span><span class="sxs-lookup"><span data-stu-id="63dec-138">Yes</span></span>      | <span data-ttu-id="63dec-139">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="63dec-139">A GUID formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="63dec-140">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="63dec-140">subscription-id</span></span>         | <span data-ttu-id="63dec-141">string</span><span class="sxs-lookup"><span data-stu-id="63dec-141">string</span></span>     | <span data-ttu-id="63dec-142">Sim</span><span class="sxs-lookup"><span data-stu-id="63dec-142">Yes</span></span>      | <span data-ttu-id="63dec-143">Uma cadeia formatada GUID que identifica a subscrição.</span><span class="sxs-lookup"><span data-stu-id="63dec-143">A GUID formatted string that identifies the subscription.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="63dec-144">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="63dec-144">Request headers</span></span>

<span data-ttu-id="63dec-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="63dec-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="63dec-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="63dec-146">Request body</span></span>

<span data-ttu-id="63dec-147">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="63dec-147">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="63dec-148">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="63dec-148">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-id>/subscriptions/<subscription-id>/registrations HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="63dec-149">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="63dec-149">REST response</span></span>

<span data-ttu-id="63dec-150">Se for bem sucedida, a resposta contém um **cabeçalho de localização** com um URI que pode ser usado para recuperar o estado de registo de subscrição.</span><span class="sxs-lookup"><span data-stu-id="63dec-150">If successful, the response contains a **Location** header with a URI that can be used to retrieve the subscription registration status.</span></span> <span data-ttu-id="63dec-151">Guarde este URI para utilização com outras APIs de REST relacionadas.</span><span class="sxs-lookup"><span data-stu-id="63dec-151">Save this URI for use with other related REST APIs.</span></span> <span data-ttu-id="63dec-152">Para obter um exemplo de como recuperar o estado, consulte obter o [estado de registo de assinatura](get-subscription-registration-status.md).</span><span class="sxs-lookup"><span data-stu-id="63dec-152">For an example of how to retrieve the status, see [Get subscription registration status](get-subscription-registration-status.md).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="63dec-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="63dec-153">Response success and error codes</span></span>

<span data-ttu-id="63dec-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="63dec-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="63dec-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="63dec-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="63dec-156">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="63dec-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="63dec-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="63dec-157">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
```
