---
title: Obter ligação de ativação por item de linha da encomenda
description: Obtém um link de ativação de subscrição por item da linha de encomenda.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: aa02a5a5b4a281b96e32ee6d239cc440cf8af4ec
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760781"
---
# <a name="get-activation-link-by-order-line-item"></a><span data-ttu-id="756ae-103">Obter ligação de ativação por item de linha da encomenda</span><span class="sxs-lookup"><span data-stu-id="756ae-103">Get activation link by order line item</span></span>

<span data-ttu-id="756ae-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="756ae-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="756ae-105">Obtém um link de ativação de subscrição de mercado comercial pelo número de item da linha de encomenda.</span><span class="sxs-lookup"><span data-stu-id="756ae-105">Gets a commercial marketplace subscription activation link by the order line item number.</span></span>

<span data-ttu-id="756ae-106">No painel de instrumentos Do Centro de Parceiros, pode fazer esta operação selecionando uma **Subscrição Específica** sob **Subscrição** na página principal ou selecionando o link **do site do Publisher** ao lado da subscrição para ativar na página **de Subscrições.**</span><span class="sxs-lookup"><span data-stu-id="756ae-106">In the Partner Center dashboard, you can do this operation by selecting either a **Specific Subscription** under **Subscription** on the main page, or selecting the **Go to Publisher's site** link next to the subscription to activate on the **Subscriptions** page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="756ae-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="756ae-107">Prerequisites</span></span>

- <span data-ttu-id="756ae-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="756ae-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="756ae-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="756ae-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="756ae-110">Encomenda completada com produto que precisa de ativação.</span><span class="sxs-lookup"><span data-stu-id="756ae-110">Completed order with product that needs activation.</span></span>

## <a name="c"></a><span data-ttu-id="756ae-111">C\#</span><span class="sxs-lookup"><span data-stu-id="756ae-111">C\#</span></span>

<span data-ttu-id="756ae-112">Para obter o link de ativação de um item de linha, utilize a sua coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente selecionado.</span><span class="sxs-lookup"><span data-stu-id="756ae-112">To get a line item's activation link, use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the selected customer ID.</span></span> <span data-ttu-id="756ae-113">Em seguida, ligue para a propriedade [**Encomendas**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) e o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) com o seu  [**OrderId**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.id)especificado .</span><span class="sxs-lookup"><span data-stu-id="756ae-113">Then call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property and the [**ById()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) method with your specified  [**OrderId**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.id).</span></span> <span data-ttu-id="756ae-114">Em seguida, ligue para o método [**LineItems**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) com **ById()** com o identificador de número de item de linha.</span><span class="sxs-lookup"><span data-stu-id="756ae-114">Then, call the [**LineItems**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) with **ById()** method with the line item number identifier.</span></span>  <span data-ttu-id="756ae-115">Por fim, ligue para o método **ActivationLinks().**</span><span class="sxs-lookup"><span data-stu-id="756ae-115">Finally, call the **ActivationLinks()** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string orderId;
// string lineItemNumber

// get the activation link for the specific line item
var partnerOperations.Customers.ById(customerId).Orders.ById(orderId).OrderLineItems.ById(lineItemNumber).ActivationLinks();
```

## <a name="rest-request"></a><span data-ttu-id="756ae-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="756ae-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="756ae-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="756ae-117">Request syntax</span></span>

| <span data-ttu-id="756ae-118">Método</span><span class="sxs-lookup"><span data-stu-id="756ae-118">Method</span></span>  | <span data-ttu-id="756ae-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="756ae-119">Request URI</span></span>                                                                                                                               |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="756ae-120">**Obter**</span><span class="sxs-lookup"><span data-stu-id="756ae-120">**GET**</span></span> | <span data-ttu-id="756ae-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customerId}/orders/{orderId}/lineitems/{lineItemNumber}/activationlinks HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="756ae-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/orders/{orderId}/lineitems/{lineItemNumber}/activationlinks HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="756ae-122">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="756ae-122">Request headers</span></span>

<span data-ttu-id="756ae-123">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="756ae-123">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="756ae-124">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="756ae-124">Request body</span></span>

<span data-ttu-id="756ae-125">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="756ae-125">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="756ae-126">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="756ae-126">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/8c5b65fd-c725-4f50-8d9c-97ec9169fdd0/orders/03fb46b3-bf8c-49aa-b908-ca2e93bcc04a/lineitems/0/activationlinks HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="756ae-127">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="756ae-127">REST response</span></span>

<span data-ttu-id="756ae-128">Se for bem sucedido, este método devolve uma coleção de recursos do [Cliente](customer-resources.md#customer) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="756ae-128">If successful, this method returns a collection of [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="756ae-129">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="756ae-129">Response success and error codes</span></span>

<span data-ttu-id="756ae-130">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="756ae-130">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="756ae-131">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="756ae-131">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="756ae-132">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="756ae-132">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="756ae-133">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="756ae-133">Response example</span></span>

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
