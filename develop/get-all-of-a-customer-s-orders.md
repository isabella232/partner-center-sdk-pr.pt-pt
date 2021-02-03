---
title: Obter todas as encomendas de um cliente
description: Recebe uma coleção de todas as encomendas para um cliente especificado.
ms.date: 06/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 4d71cd138421704d94a55a9fe21e074d92638815
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769727"
---
# <a name="get-all-of-a-customers-orders"></a><span data-ttu-id="b688f-103">Obter todas as encomendas de um cliente</span><span class="sxs-lookup"><span data-stu-id="b688f-103">Get all of a customer's orders</span></span>

<span data-ttu-id="b688f-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="b688f-104">**Applies to:**</span></span>

- <span data-ttu-id="b688f-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="b688f-105">Partner Center</span></span>
- <span data-ttu-id="b688f-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="b688f-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="b688f-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="b688f-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="b688f-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b688f-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b688f-109">Recebe uma coleção de todas as encomendas para um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="b688f-109">Gets a collection of all the orders for a specified customer.</span></span> <span data-ttu-id="b688f-110">Há um atraso de até 15 minutos entre o momento em que uma encomenda é submetida e quando aparecerá numa recolha de encomendas de um cliente.</span><span class="sxs-lookup"><span data-stu-id="b688f-110">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a collection of a customer's orders.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b688f-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b688f-111">Prerequisites</span></span>

- <span data-ttu-id="b688f-112">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b688f-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b688f-113">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="b688f-113">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="b688f-114">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b688f-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="b688f-115">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b688f-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="b688f-116">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="b688f-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="b688f-117">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="b688f-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="b688f-118">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="b688f-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="b688f-119">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b688f-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="b688f-120">C\#</span><span class="sxs-lookup"><span data-stu-id="b688f-120">C\#</span></span>

<span data-ttu-id="b688f-121">Para obter uma coleção de todas as encomendas de um cliente:</span><span class="sxs-lookup"><span data-stu-id="b688f-121">To obtain a collection of all of a customer's orders:</span></span>

1. <span data-ttu-id="b688f-122">Utilize a sua coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="b688f-122">Use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span>

2. <span data-ttu-id="b688f-123">Ligue para a propriedade [**Encomendas,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) seguida dos métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="b688f-123">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var orders = partnerOperations.Customers.ById(selectedCustomerId).Orders.Get();
```

<span data-ttu-id="b688f-124">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b688f-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b688f-125">**Projeto**: PartnerSDK.FeatureSamples **Class**: GetOrders.cs</span><span class="sxs-lookup"><span data-stu-id="b688f-125">**Project**: PartnerSDK.FeatureSamples **Class**: GetOrders.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b688f-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b688f-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b688f-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b688f-127">Request syntax</span></span>

| <span data-ttu-id="b688f-128">Método</span><span class="sxs-lookup"><span data-stu-id="b688f-128">Method</span></span>  | <span data-ttu-id="b688f-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b688f-129">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="b688f-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b688f-130">**GET**</span></span> | <span data-ttu-id="b688f-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/encomendas HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b688f-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders HTTP/1.1</span></span>  |

#### <a name="uri-parameter"></a><span data-ttu-id="b688f-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="b688f-132">URI parameter</span></span>

<span data-ttu-id="b688f-133">Utilize o seguinte parâmetro de consulta para obter todas as encomendas.</span><span class="sxs-lookup"><span data-stu-id="b688f-133">Use the following query parameter to get all orders.</span></span>

| <span data-ttu-id="b688f-134">Nome</span><span class="sxs-lookup"><span data-stu-id="b688f-134">Name</span></span>                   | <span data-ttu-id="b688f-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="b688f-135">Type</span></span>     | <span data-ttu-id="b688f-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="b688f-136">Required</span></span> | <span data-ttu-id="b688f-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="b688f-137">Description</span></span>                                               |
|------------------------|----------|----------|-----------------------------------------------------------|
| <span data-ttu-id="b688f-138">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="b688f-138">customer-tenant-id</span></span>     | <span data-ttu-id="b688f-139">string</span><span class="sxs-lookup"><span data-stu-id="b688f-139">string</span></span>   | <span data-ttu-id="b688f-140">Sim</span><span class="sxs-lookup"><span data-stu-id="b688f-140">Yes</span></span>      | <span data-ttu-id="b688f-141">Uma cadeia formatada GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b688f-141">A GUID formatted string corresponding to the customer.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="b688f-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b688f-142">Request headers</span></span>

<span data-ttu-id="b688f-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b688f-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b688f-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b688f-144">Request body</span></span>

<span data-ttu-id="b688f-145">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b688f-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b688f-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b688f-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="b688f-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b688f-147">REST response</span></span>

<span data-ttu-id="b688f-148">Se for bem sucedido, este método devolve uma recolha de recursos da [Ordem](order-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="b688f-148">If successful, this method returns a collection of [Order](order-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b688f-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b688f-149">Response success and error codes</span></span>

<span data-ttu-id="b688f-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b688f-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b688f-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b688f-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b688f-152">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b688f-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b688f-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b688f-153">Response example</span></span>

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
