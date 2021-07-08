---
title: Obter uma lista de encomendas por cliente e tipo de ciclo de faturação
description: Obtém uma recolha de recursos de encomenda para o cliente especificado e tipo de ciclo de faturação.
ms.date: 06/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: c52a556887dba065c4ccd1a82d6223624d0ad1f2
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874232"
---
# <a name="get-a-list-of-orders-by-customer-and-billing-cycle-type"></a><span data-ttu-id="6e2da-103">Obter uma lista de encomendas por cliente e tipo de ciclo de faturação</span><span class="sxs-lookup"><span data-stu-id="6e2da-103">Get a list of orders by customer and billing cycle type</span></span>

<span data-ttu-id="6e2da-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6e2da-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6e2da-105">Obtém uma coleção de recursos da Encomenda que correspondem a um determinado cliente e tipo de ciclo de faturação.</span><span class="sxs-lookup"><span data-stu-id="6e2da-105">Gets a collection of Order resources that correspond to a given customer and billing cycle type.</span></span> <span data-ttu-id="6e2da-106">Há um atraso de até 15 minutos entre o momento em que uma encomenda é submetida e quando aparecerá numa recolha de encomendas de um cliente.</span><span class="sxs-lookup"><span data-stu-id="6e2da-106">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a collection of a customer's orders.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6e2da-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6e2da-107">Prerequisites</span></span>

- <span data-ttu-id="6e2da-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6e2da-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6e2da-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="6e2da-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6e2da-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6e2da-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6e2da-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="6e2da-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6e2da-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="6e2da-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6e2da-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="6e2da-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6e2da-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="6e2da-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6e2da-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6e2da-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="6e2da-116">C\#</span><span class="sxs-lookup"><span data-stu-id="6e2da-116">C\#</span></span>

<span data-ttu-id="6e2da-117">Para obter uma coleção de encomendas de um cliente:</span><span class="sxs-lookup"><span data-stu-id="6e2da-117">To get a collection of a customer's orders:</span></span>

1. <span data-ttu-id="6e2da-118">Utilize a sua coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente selecionado.</span><span class="sxs-lookup"><span data-stu-id="6e2da-118">Use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the selected customer ID.</span></span>

2. <span data-ttu-id="6e2da-119">Ligue para a propriedade [**Encomendas**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) e o método **ByBillingCycleType()** com o seu  [**BillingCycleType**](product-resources.md#billingcycletype)especificado .</span><span class="sxs-lookup"><span data-stu-id="6e2da-119">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property and the **ByBillingCycleType()** method with your specified  [**BillingCycleType**](product-resources.md#billingcycletype).</span></span>
3. <span data-ttu-id="6e2da-120">Ligue para o método [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="6e2da-120">Call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// BillingCycleType selectedBillingCycleType;

var orders = partnerOperations.Customers.ById(selectedCustomerId).Orders.ByBillingCycleType(selectedBillingCycleType).Get();
```

## <a name="rest-request"></a><span data-ttu-id="6e2da-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6e2da-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6e2da-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e2da-122">Request syntax</span></span>

| <span data-ttu-id="6e2da-123">Método</span><span class="sxs-lookup"><span data-stu-id="6e2da-123">Method</span></span>  | <span data-ttu-id="6e2da-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6e2da-124">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6e2da-125">**Obter**</span><span class="sxs-lookup"><span data-stu-id="6e2da-125">**GET**</span></span> | <span data-ttu-id="6e2da-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders?billingType={billing-cycle-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6e2da-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders?billingType={billing-cycle-type} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="6e2da-127">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="6e2da-127">URI parameters</span></span>

<span data-ttu-id="6e2da-128">Esta tabela lista os parâmetros de consulta necessários para obter uma recolha de encomendas por ID do cliente e tipo de ciclo de faturação.</span><span class="sxs-lookup"><span data-stu-id="6e2da-128">This table lists the required query parameters to get a collection of orders by customer ID and billing cycle type.</span></span>

| <span data-ttu-id="6e2da-129">Nome</span><span class="sxs-lookup"><span data-stu-id="6e2da-129">Name</span></span>                   | <span data-ttu-id="6e2da-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="6e2da-130">Type</span></span>     | <span data-ttu-id="6e2da-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="6e2da-131">Required</span></span> | <span data-ttu-id="6e2da-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e2da-132">Description</span></span>                                               |
|------------------------|----------|----------|-----------------------------------------------------------|
| <span data-ttu-id="6e2da-133">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="6e2da-133">customer-tenant-id</span></span>     | <span data-ttu-id="6e2da-134">string</span><span class="sxs-lookup"><span data-stu-id="6e2da-134">string</span></span>   | <span data-ttu-id="6e2da-135">Yes</span><span class="sxs-lookup"><span data-stu-id="6e2da-135">Yes</span></span>      | <span data-ttu-id="6e2da-136">Uma cadeia formatada GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="6e2da-136">A GUID formatted string corresponding to the customer.</span></span>    |
| <span data-ttu-id="6e2da-137">tipo de ciclo de faturação</span><span class="sxs-lookup"><span data-stu-id="6e2da-137">billing-cycle-type</span></span>     | <span data-ttu-id="6e2da-138">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6e2da-138">string</span></span>   | <span data-ttu-id="6e2da-139">No</span><span class="sxs-lookup"><span data-stu-id="6e2da-139">No</span></span>       | <span data-ttu-id="6e2da-140">Uma cadeia correspondente ao tipo de ciclo de faturação.</span><span class="sxs-lookup"><span data-stu-id="6e2da-140">A string corresponding to the billing cycle type.</span></span>         |

### <a name="request-headers"></a><span data-ttu-id="6e2da-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6e2da-141">Request headers</span></span>

<span data-ttu-id="6e2da-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6e2da-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6e2da-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6e2da-143">Request body</span></span>

<span data-ttu-id="6e2da-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6e2da-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6e2da-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6e2da-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders?billingType=onetime HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="6e2da-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6e2da-146">REST response</span></span>

<span data-ttu-id="6e2da-147">Se for bem sucedido, este método devolve uma recolha de recursos da [Ordem](order-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="6e2da-147">If successful, this method returns a collection of [Order](order-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6e2da-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6e2da-148">Response success and error codes</span></span>

<span data-ttu-id="6e2da-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6e2da-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6e2da-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6e2da-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6e2da-151">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6e2da-151">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6e2da-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6e2da-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 22463
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 97fa8b4f-6576-4cd9-dd19-ac7c97a023a7
MS-RequestId: 3c6a034c-82ee-4095-d50f-9b530a415f1f
MS-CV: nb4/b3Yl2keY0eYR.0
MS-ServerId: 202010607
Date: Thu, 15 Mar 2018 20:44:40 GMT

{
    "totalCount": 2,
    "items": [
        {
            "id": "9qg-ErcO-4MPbPqq_3MIQaS7bn8W6HfG1",
            "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
            "billingCycle": "one_time",
            "currencyCode": "USD",
            "lineItems": [
                {
                    "lineItemNumber": 0,
                    "offerId": "DZH318Z0BQ4B:000Z:DZH318Z0DSPL",
                    "friendlyName": "Reserved_VM_Instance_Standard_D1_AP_East_1_Year",
                    "quantity": 1,
                    "links": {
                        "sku": {
                            "uri": "/products/DZH318Z0BQ4B/skus/000Z?country=US",
                            "method": "GET",
                            "headers": []
                        }
                    }
                }
            ],
            "creationDate": "2018-03-15T02:17:15.6455674Z",
            "status": "pending",
            "links": {
                "provisioningStatus": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/9qg-ErcO-4MPbPqq_3MIQaS7bn8W6HfG1/provisioningstatus",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/9qg-ErcO-4MPbPqq_3MIQaS7bn8W6HfG1",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Order"
            }
        },
        {
            "id": "s-BZlr_TeGksPNT61SsWRL-sqMaKbyVa1",
            "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
            "billingCycle": "one_time",
            "currencyCode": "USD",
            "lineItems": [
                {
                    "lineItemNumber": 0,
                    "offerId": "DZH318Z0BQ4Z:002P:DZH318Z0CL2D",
                    "friendlyName": "Reserved_VM_Instance_Standard_NC12_AU_East_3_Years",
                    "quantity": 1,
                    "links": {
                        "sku": {
                            "uri": "/products/DZH318Z0BQ4Z/skus/002P?country=US",
                            "method": "GET",
                            "headers": []
                        }
                    }
                }
            ],
            "creationDate": "2018-03-15T01:42:36.8440279Z",
            "status": "pending",
            "links": {
                "provisioningStatus": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/s-BZlr_TeGksPNT61SsWRL-sqMaKbyVa1/provisioningstatus",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/s-BZlr_TeGksPNT61SsWRL-sqMaKbyVa1",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": { "objectType": "Order" }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType":
        "Collection"
    }
}
```
