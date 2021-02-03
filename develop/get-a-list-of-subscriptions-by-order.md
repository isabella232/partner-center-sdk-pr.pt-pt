---
title: Obter uma lista de subscrições por encomenda
description: Obtém uma coleção de recursos de Subscrição que correspondem a uma determinada encomenda.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 56b9c80021cace03976d410b2a6cd4c0eee18398
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769553"
---
# <a name="get-a-list-of-subscriptions-by-order"></a><span data-ttu-id="cbf73-103">Obter uma lista de subscrições por encomenda</span><span class="sxs-lookup"><span data-stu-id="cbf73-103">Get a list of subscriptions by order</span></span>

<span data-ttu-id="cbf73-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="cbf73-104">**Applies To**</span></span>

- <span data-ttu-id="cbf73-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="cbf73-105">Partner Center</span></span>
- <span data-ttu-id="cbf73-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="cbf73-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="cbf73-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="cbf73-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="cbf73-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cbf73-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cbf73-109">Obtém uma coleção de recursos de [Subscrição](subscription-resources.md) que correspondem a uma determinada encomenda.</span><span class="sxs-lookup"><span data-stu-id="cbf73-109">Gets a collection of [Subscription](subscription-resources.md) resources that correspond to a given order.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cbf73-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="cbf73-110">Prerequisites</span></span>

- <span data-ttu-id="cbf73-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cbf73-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cbf73-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="cbf73-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="cbf73-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cbf73-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="cbf73-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="cbf73-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="cbf73-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="cbf73-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="cbf73-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="cbf73-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="cbf73-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="cbf73-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="cbf73-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cbf73-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="cbf73-119">Uma identificação de encomenda.</span><span class="sxs-lookup"><span data-stu-id="cbf73-119">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="cbf73-120">C\#</span><span class="sxs-lookup"><span data-stu-id="cbf73-120">C\#</span></span>

<span data-ttu-id="cbf73-121">Para obter uma lista de subscrições por encomenda, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="cbf73-121">To get a list of subscriptions by order, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="cbf73-122">Em seguida, ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método **ByOrder().**</span><span class="sxs-lookup"><span data-stu-id="cbf73-122">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the **ByOrder()** method.</span></span> <span data-ttu-id="cbf73-123">Termine chamando [**Get()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) ou [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync).</span><span class="sxs-lookup"><span data-stu-id="cbf73-123">Finish by calling [**Get()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// string orderID;

ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ByOrder(orderID).Get();
```

<span data-ttu-id="cbf73-124">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cbf73-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cbf73-125">**Projeto**: PartnerSDK.FeatureSample **Class**: SubscriptionsByOrder.cs</span><span class="sxs-lookup"><span data-stu-id="cbf73-125">**Project**: PartnerSDK.FeatureSample **Class**: SubscriptionsByOrder.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="cbf73-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="cbf73-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cbf73-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbf73-127">Request syntax</span></span>

| <span data-ttu-id="cbf73-128">Método</span><span class="sxs-lookup"><span data-stu-id="cbf73-128">Method</span></span>  | <span data-ttu-id="cbf73-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="cbf73-129">Request URI</span></span>                                                                                                                   |
|---------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cbf73-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="cbf73-130">**GET**</span></span> | <span data-ttu-id="cbf73-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscrições?order \_ id={id-for-order} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="cbf73-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions?order\_id={id-for-order} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="cbf73-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="cbf73-132">URI parameter</span></span>

<span data-ttu-id="cbf73-133">Esta tabela lista o parâmetro de consulta necessário para obter todas as subscrições.</span><span class="sxs-lookup"><span data-stu-id="cbf73-133">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="cbf73-134">Nome</span><span class="sxs-lookup"><span data-stu-id="cbf73-134">Name</span></span>                   | <span data-ttu-id="cbf73-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="cbf73-135">Type</span></span>     | <span data-ttu-id="cbf73-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="cbf73-136">Required</span></span> | <span data-ttu-id="cbf73-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbf73-137">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="cbf73-138">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="cbf73-138">**customer-tenant-id**</span></span> | <span data-ttu-id="cbf73-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="cbf73-139">**guid**</span></span> | <span data-ttu-id="cbf73-140">Y</span><span class="sxs-lookup"><span data-stu-id="cbf73-140">Y</span></span>        | <span data-ttu-id="cbf73-141">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="cbf73-141">A GUID corresponding to the customer.</span></span> |
| <span data-ttu-id="cbf73-142">**id-for-order**</span><span class="sxs-lookup"><span data-stu-id="cbf73-142">**id-for-order**</span></span>       | <span data-ttu-id="cbf73-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="cbf73-143">**guid**</span></span> | <span data-ttu-id="cbf73-144">Y</span><span class="sxs-lookup"><span data-stu-id="cbf73-144">Y</span></span>        | <span data-ttu-id="cbf73-145">Um GUID correspondente à ordem.</span><span class="sxs-lookup"><span data-stu-id="cbf73-145">A GUID corresponding to the order.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="cbf73-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="cbf73-146">Request headers</span></span>

<span data-ttu-id="cbf73-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cbf73-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cbf73-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="cbf73-148">Request body</span></span>

<span data-ttu-id="cbf73-149">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cbf73-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="cbf73-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="cbf73-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions?order_id={id-for-order} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="cbf73-151">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="cbf73-151">REST response</span></span>

<span data-ttu-id="cbf73-152">Se for bem sucedido, este método devolve uma recolha de recursos de [Subscrição](subscription-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="cbf73-152">If successful, this method returns a collection of [Subscription](subscription-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cbf73-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="cbf73-153">Response success and error codes</span></span>

<span data-ttu-id="cbf73-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="cbf73-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cbf73-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="cbf73-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cbf73-156">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="cbf73-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cbf73-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="cbf73-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
Date: Wed, 25 Nov 2015 05:50:45 GMT

{
    "totalCount": 37,
    "items": [{
        "id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
        "entitlementId": "a356ac8c-e310-44f4-bf85-C7f29044af99",
        "friendlyName": "Myofferpurchase",
        "quantity": 1,
        "unitType": "none",
        "creationDate": "2015-11-25T06: 41: 12Z",
        "effectiveStartDate": "2015-11-24T08: 00: 00Z",
        "commitmentEndDate": "2016-12-12T08: 00: 00Z",
        "status": "active",
        "autoRenewEnabled": false,
        "billingType": "none",
        "contractType": "subscription",
        "links": {
            "offer": {
                "uri": "/v1/offers/0CCA44D6-68E9-4762-94EE-31ECE98783B9",
                "method": "GET",
                "headers": []
            },
            "self": {
                "uri": "/subscriptions?key=<key>",
                "method": "GET",
                "headers": []
            }
        },
        "orderId": "{id-for-order}",
        "attributes": {
            "etag": "<etag>",
            "objectType": "Subscription"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
