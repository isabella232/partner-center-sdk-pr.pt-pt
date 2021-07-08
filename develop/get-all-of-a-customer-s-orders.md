---
title: Obter todas as encomendas de um cliente
description: Recebe uma coleção de todas as encomendas para um cliente especificado.
ms.date: 06/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: e8f23e90cbb5afb45e519e2c58fd0d3b9ea2de6a
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760305"
---
# <a name="get-all-of-a-customers-orders"></a><span data-ttu-id="818b8-103">Obter todas as encomendas de um cliente</span><span class="sxs-lookup"><span data-stu-id="818b8-103">Get all of a customer's orders</span></span>

<span data-ttu-id="818b8-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="818b8-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="818b8-105">Recebe uma coleção de todas as encomendas para um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="818b8-105">Gets a collection of all the orders for a specified customer.</span></span> <span data-ttu-id="818b8-106">Há um atraso de até 15 minutos entre o momento em que uma encomenda é submetida e quando aparecerá numa recolha de encomendas de um cliente.</span><span class="sxs-lookup"><span data-stu-id="818b8-106">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a collection of a customer's orders.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="818b8-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="818b8-107">Prerequisites</span></span>

- <span data-ttu-id="818b8-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="818b8-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="818b8-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="818b8-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="818b8-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="818b8-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="818b8-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="818b8-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="818b8-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="818b8-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="818b8-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="818b8-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="818b8-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="818b8-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="818b8-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="818b8-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="818b8-116">C\#</span><span class="sxs-lookup"><span data-stu-id="818b8-116">C\#</span></span>

<span data-ttu-id="818b8-117">Para obter uma coleção de todas as encomendas de um cliente:</span><span class="sxs-lookup"><span data-stu-id="818b8-117">To obtain a collection of all of a customer's orders:</span></span>

1. <span data-ttu-id="818b8-118">Utilize a sua coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="818b8-118">Use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span>

2. <span data-ttu-id="818b8-119">Ligue para a propriedade [**Encomendas,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) seguida dos métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="818b8-119">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var orders = partnerOperations.Customers.ById(selectedCustomerId).Orders.Get();
```

<span data-ttu-id="818b8-120">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="818b8-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="818b8-121">**Project**: PartnerSDK.FeatureSamples **Class**: GetOrders.cs</span><span class="sxs-lookup"><span data-stu-id="818b8-121">**Project**: PartnerSDK.FeatureSamples **Class**: GetOrders.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="818b8-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="818b8-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="818b8-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="818b8-123">Request syntax</span></span>

| <span data-ttu-id="818b8-124">Método</span><span class="sxs-lookup"><span data-stu-id="818b8-124">Method</span></span>  | <span data-ttu-id="818b8-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="818b8-125">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="818b8-126">**Obter**</span><span class="sxs-lookup"><span data-stu-id="818b8-126">**GET**</span></span> | <span data-ttu-id="818b8-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/encomendas HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="818b8-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders HTTP/1.1</span></span>  |

#### <a name="uri-parameter"></a><span data-ttu-id="818b8-128">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="818b8-128">URI parameter</span></span>

<span data-ttu-id="818b8-129">Utilize o seguinte parâmetro de consulta para obter todas as encomendas.</span><span class="sxs-lookup"><span data-stu-id="818b8-129">Use the following query parameter to get all orders.</span></span>

| <span data-ttu-id="818b8-130">Nome</span><span class="sxs-lookup"><span data-stu-id="818b8-130">Name</span></span>                   | <span data-ttu-id="818b8-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="818b8-131">Type</span></span>     | <span data-ttu-id="818b8-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="818b8-132">Required</span></span> | <span data-ttu-id="818b8-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="818b8-133">Description</span></span>                                               |
|------------------------|----------|----------|-----------------------------------------------------------|
| <span data-ttu-id="818b8-134">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="818b8-134">customer-tenant-id</span></span>     | <span data-ttu-id="818b8-135">string</span><span class="sxs-lookup"><span data-stu-id="818b8-135">string</span></span>   | <span data-ttu-id="818b8-136">Yes</span><span class="sxs-lookup"><span data-stu-id="818b8-136">Yes</span></span>      | <span data-ttu-id="818b8-137">Uma cadeia formatada GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="818b8-137">A GUID formatted string corresponding to the customer.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="818b8-138">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="818b8-138">Request headers</span></span>

<span data-ttu-id="818b8-139">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="818b8-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="818b8-140">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="818b8-140">Request body</span></span>

<span data-ttu-id="818b8-141">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="818b8-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="818b8-142">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="818b8-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="818b8-143">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="818b8-143">REST response</span></span>

<span data-ttu-id="818b8-144">Se for bem sucedido, este método devolve uma recolha de recursos da [Ordem](order-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="818b8-144">If successful, this method returns a collection of [Order](order-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="818b8-145">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="818b8-145">Response success and error codes</span></span>

<span data-ttu-id="818b8-146">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="818b8-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="818b8-147">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="818b8-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="818b8-148">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="818b8-148">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="818b8-149">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="818b8-149">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 22463
Content-Type: application/json; charset=utf-8
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
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
            "id": "eeba9d00-7b46-443a-917e-22887a8fc993",
            "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
            "billingCycle": "monthly",
            "currencyCode": "USD",
            "lineItems": [
                {
                    "lineItemNumber": 0,
                    "offerId": "E59159FC-6F67-4599-B3CB-17FF4020F643",
                    "subscriptionId": "DB8C695B-1C3C-4C55-B697-771503DD46BF",
                    "friendlyName": "Azure Active Directory Premium P2",
                    "quantity": 1,
                    "links": {
                        "subscription": {
                            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/subscriptions/DB8C695B-1C3C-4C55-B697-771503DD46BF",
                            "method": "GET",
                            "headers": []
                        },
                        "sku": {
                            "uri": "/products/84A661C4-E949-4BD2-A560-ED7766FCAF2B/skus/E59159FC-6F67-4599-B3CB-17FF4020F643",
                            "method": "GET",
                            "headers": []
                        },
                        "provisioningStatus": {
                            "uri": "/subscriptions/DB8C695B-1C3C-4C55-B697-771503DD46BF/provisioningstatus",
                            "method": "GET",
                            "headers": []
                        }
                    }
            ],
            "creationDate": "2018-03-06T17:37:05.253-08:00",
            "status": "completed",
            "links": {
                "self": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/eeba9d00-7b46-443a-917e-22887a8fc993",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "etag": "eyJpZCI6ImVlYmE5ZDAwLTdiNDYtNDQzYS05MTdlLTIyODg3YThmYzk5MyIsInZlcnNpb24iOjF9",
                "objectType": "Order"
            }
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
         "objectType": "Collection"
    }
}
```
