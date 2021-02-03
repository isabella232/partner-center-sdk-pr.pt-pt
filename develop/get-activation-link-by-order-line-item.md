---
title: Obter ligação de ativação por item de linha da encomenda
description: Obtém um link de ativação de subscrição por item da linha de encomenda.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: c0e84888870571cf6bd21306f527863f2aa7ee85
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769266"
---
# <a name="get-activation-link-by-order-line-item"></a><span data-ttu-id="d40f9-103">Obter ligação de ativação por item de linha da encomenda</span><span class="sxs-lookup"><span data-stu-id="d40f9-103">Get activation link by order line item</span></span>

<span data-ttu-id="d40f9-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="d40f9-104">**Applies To**</span></span>

- <span data-ttu-id="d40f9-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="d40f9-105">Partner Center</span></span>
- <span data-ttu-id="d40f9-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="d40f9-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="d40f9-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="d40f9-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="d40f9-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d40f9-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d40f9-109">Obtém um link de ativação de subscrição de mercado comercial pelo número de item da linha de encomenda.</span><span class="sxs-lookup"><span data-stu-id="d40f9-109">Gets a commercial marketplace subscription activation link by the order line item number.</span></span>

<span data-ttu-id="d40f9-110">No painel de instrumentos Partner Center, pode fazer esta operação selecionando uma **Subscrição Específica** sob **Subscrição** na página principal ou selecionando o link **do site do 'Ir para** o site' do Editor ao lado da subscrição para ativar na página de **Subscrições.**</span><span class="sxs-lookup"><span data-stu-id="d40f9-110">In the Partner Center dashboard, you can do this operation by selecting either a **Specific Subscription** under **Subscription** on the main page, or selecting the **Go to Publisher's site** link next to the subscription to activate on the **Subscriptions** page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d40f9-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d40f9-111">Prerequisites</span></span>

- <span data-ttu-id="d40f9-112">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d40f9-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d40f9-113">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="d40f9-113">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="d40f9-114">Encomenda completada com produto que precisa de ativação.</span><span class="sxs-lookup"><span data-stu-id="d40f9-114">Completed order with product that needs activation.</span></span>

## <a name="c"></a><span data-ttu-id="d40f9-115">C\#</span><span class="sxs-lookup"><span data-stu-id="d40f9-115">C\#</span></span>

<span data-ttu-id="d40f9-116">Para obter o link de ativação de um item de linha, utilize a sua coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente selecionado.</span><span class="sxs-lookup"><span data-stu-id="d40f9-116">To get a line item's activation link, use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the selected customer ID.</span></span> <span data-ttu-id="d40f9-117">Em seguida, ligue para a propriedade [**Encomendas**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) e o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) com o seu  [**OrderId**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.id)especificado .</span><span class="sxs-lookup"><span data-stu-id="d40f9-117">Then call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property and the [**ById()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) method with your specified  [**OrderId**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.id).</span></span> <span data-ttu-id="d40f9-118">Em seguida, ligue para o método [**LineItems**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) com **ById()** com o identificador de número de item de linha.</span><span class="sxs-lookup"><span data-stu-id="d40f9-118">Then, call the [**LineItems**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) with **ById()** method with the line item number identifier.</span></span>  <span data-ttu-id="d40f9-119">Por fim, ligue para o método **ActivationLinks().**</span><span class="sxs-lookup"><span data-stu-id="d40f9-119">Finally, call the **ActivationLinks()** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string orderId;
// string lineItemNumber

// get the activation link for the specific line item
var partnerOperations.Customers.ById(customerId).Orders.ById(orderId).OrderLineItems.ById(lineItemNumber).ActivationLinks();
```

## <a name="rest-request"></a><span data-ttu-id="d40f9-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d40f9-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d40f9-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d40f9-121">Request syntax</span></span>

| <span data-ttu-id="d40f9-122">Método</span><span class="sxs-lookup"><span data-stu-id="d40f9-122">Method</span></span>  | <span data-ttu-id="d40f9-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d40f9-123">Request URI</span></span>                                                                                                                               |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d40f9-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d40f9-124">**GET**</span></span> | <span data-ttu-id="d40f9-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customerId}/orders/{orderId}/lineitems/{lineItemNumber}/activationlinks HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d40f9-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/orders/{orderId}/lineitems/{lineItemNumber}/activationlinks HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d40f9-126">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d40f9-126">Request headers</span></span>

<span data-ttu-id="d40f9-127">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d40f9-127">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d40f9-128">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d40f9-128">Request body</span></span>

<span data-ttu-id="d40f9-129">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d40f9-129">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d40f9-130">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d40f9-130">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/8c5b65fd-c725-4f50-8d9c-97ec9169fdd0/orders/03fb46b3-bf8c-49aa-b908-ca2e93bcc04a/lineitems/0/activationlinks HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="d40f9-131">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d40f9-131">REST response</span></span>

<span data-ttu-id="d40f9-132">Se for bem sucedido, este método devolve uma coleção de recursos do [Cliente](customer-resources.md#customer) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="d40f9-132">If successful, this method returns a collection of [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d40f9-133">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d40f9-133">Response success and error codes</span></span>

<span data-ttu-id="d40f9-134">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d40f9-134">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d40f9-135">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d40f9-135">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d40f9-136">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d40f9-136">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d40f9-137">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d40f9-137">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 809
Content-Type: application/json
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
Date: Fri, 20 Nov 2015 01:08:23 GMT
{
  "totalCount": 1,
  "items": [
    {
      "lineItemNumber": 0,
      "link": {
        "uri": "<link populated here>",
        "method": "GET",
        "headers": [

        ]
      }
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/8c5b65fd-c725-4f50-8d9c-97ec9169fdd0/orders/03fb46b3-bf8c-49aa-b908-ca2e93bcc04a/lineitems/0/activationlinks",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "Collection"
  }
}
```
