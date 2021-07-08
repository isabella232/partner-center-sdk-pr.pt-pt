---
title: Obter uma lista de subscrições por encomenda
description: Obtém uma coleção de recursos de Subscrição que correspondem a uma determinada encomenda.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 011a92500d0c7ed44f86030febd1ea83be2c6474
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873960"
---
# <a name="get-a-list-of-subscriptions-by-order"></a><span data-ttu-id="00c46-103">Obter uma lista de subscrições por encomenda</span><span class="sxs-lookup"><span data-stu-id="00c46-103">Get a list of subscriptions by order</span></span>

<span data-ttu-id="00c46-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="00c46-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="00c46-105">Obtém uma coleção de recursos de [Subscrição](subscription-resources.md) que correspondem a uma determinada encomenda.</span><span class="sxs-lookup"><span data-stu-id="00c46-105">Gets a collection of [Subscription](subscription-resources.md) resources that correspond to a given order.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00c46-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="00c46-106">Prerequisites</span></span>

- <span data-ttu-id="00c46-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="00c46-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="00c46-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="00c46-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="00c46-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="00c46-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="00c46-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="00c46-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="00c46-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="00c46-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="00c46-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="00c46-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="00c46-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="00c46-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="00c46-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="00c46-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="00c46-115">Uma identificação de encomenda.</span><span class="sxs-lookup"><span data-stu-id="00c46-115">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="00c46-116">C\#</span><span class="sxs-lookup"><span data-stu-id="00c46-116">C\#</span></span>

<span data-ttu-id="00c46-117">Para obter uma lista de subscrições por encomenda, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="00c46-117">To get a list of subscriptions by order, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="00c46-118">Em seguida, ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método **ByOrder().**</span><span class="sxs-lookup"><span data-stu-id="00c46-118">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the **ByOrder()** method.</span></span> <span data-ttu-id="00c46-119">Termine chamando [**Get()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) ou [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync).</span><span class="sxs-lookup"><span data-stu-id="00c46-119">Finish by calling [**Get()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// string orderID;

ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ByOrder(orderID).Get();
```

<span data-ttu-id="00c46-120">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="00c46-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="00c46-121">**Project**: PartnerSDK.FeatureSample **Class**: SubscriptionsByOrder.cs</span><span class="sxs-lookup"><span data-stu-id="00c46-121">**Project**: PartnerSDK.FeatureSample **Class**: SubscriptionsByOrder.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="00c46-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="00c46-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="00c46-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="00c46-123">Request syntax</span></span>

| <span data-ttu-id="00c46-124">Método</span><span class="sxs-lookup"><span data-stu-id="00c46-124">Method</span></span>  | <span data-ttu-id="00c46-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="00c46-125">Request URI</span></span>                                                                                                                   |
|---------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="00c46-126">**Obter**</span><span class="sxs-lookup"><span data-stu-id="00c46-126">**GET**</span></span> | <span data-ttu-id="00c46-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscrições?order \_ id={id-for-order} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="00c46-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions?order\_id={id-for-order} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="00c46-128">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="00c46-128">URI parameter</span></span>

<span data-ttu-id="00c46-129">Esta tabela lista o parâmetro de consulta necessário para obter todas as subscrições.</span><span class="sxs-lookup"><span data-stu-id="00c46-129">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="00c46-130">Nome</span><span class="sxs-lookup"><span data-stu-id="00c46-130">Name</span></span>                   | <span data-ttu-id="00c46-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="00c46-131">Type</span></span>     | <span data-ttu-id="00c46-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="00c46-132">Required</span></span> | <span data-ttu-id="00c46-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="00c46-133">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="00c46-134">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="00c46-134">**customer-tenant-id**</span></span> | <span data-ttu-id="00c46-135">**guid**</span><span class="sxs-lookup"><span data-stu-id="00c46-135">**guid**</span></span> | <span data-ttu-id="00c46-136">Y</span><span class="sxs-lookup"><span data-stu-id="00c46-136">Y</span></span>        | <span data-ttu-id="00c46-137">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="00c46-137">A GUID corresponding to the customer.</span></span> |
| <span data-ttu-id="00c46-138">**id-for-order**</span><span class="sxs-lookup"><span data-stu-id="00c46-138">**id-for-order**</span></span>       | <span data-ttu-id="00c46-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="00c46-139">**guid**</span></span> | <span data-ttu-id="00c46-140">Y</span><span class="sxs-lookup"><span data-stu-id="00c46-140">Y</span></span>        | <span data-ttu-id="00c46-141">Um GUID correspondente à ordem.</span><span class="sxs-lookup"><span data-stu-id="00c46-141">A GUID corresponding to the order.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="00c46-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="00c46-142">Request headers</span></span>

<span data-ttu-id="00c46-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="00c46-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="00c46-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="00c46-144">Request body</span></span>

<span data-ttu-id="00c46-145">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="00c46-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="00c46-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="00c46-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions?order_id={id-for-order} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="00c46-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="00c46-147">REST response</span></span>

<span data-ttu-id="00c46-148">Se for bem sucedido, este método devolve uma recolha de recursos de [Subscrição](subscription-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="00c46-148">If successful, this method returns a collection of [Subscription](subscription-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="00c46-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="00c46-149">Response success and error codes</span></span>

<span data-ttu-id="00c46-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="00c46-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="00c46-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="00c46-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="00c46-152">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="00c46-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="00c46-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="00c46-153">Response example</span></span>

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
