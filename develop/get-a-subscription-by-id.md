---
title: Obter uma subscrição por ID
description: Obtém um recurso de subscrição que corresponda ao ID do cliente e ao ID de subscrição.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 75f21a3f76e5502ba40b89995aa26bd0e668b3fa
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873824"
---
# <a name="get-a-subscription-by-id"></a><span data-ttu-id="d063c-103">Obter uma subscrição por ID</span><span class="sxs-lookup"><span data-stu-id="d063c-103">Get a subscription by ID</span></span>

<span data-ttu-id="d063c-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d063c-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d063c-105">Obtém um recurso [de subscrição](subscription-resources.md) que corresponda ao ID do cliente e ao ID de subscrição.</span><span class="sxs-lookup"><span data-stu-id="d063c-105">Gets a [Subscription](subscription-resources.md) resource that matches the customer ID and the subscription ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d063c-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d063c-106">Prerequisites</span></span>

- <span data-ttu-id="d063c-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d063c-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d063c-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="d063c-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="d063c-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d063c-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d063c-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d063c-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d063c-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d063c-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d063c-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d063c-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d063c-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d063c-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d063c-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d063c-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d063c-115">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="d063c-115">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="d063c-116">C\#</span><span class="sxs-lookup"><span data-stu-id="d063c-116">C\#</span></span>

<span data-ttu-id="d063c-117">Para obter uma subscrição por ID, comece por obter uma interface para as operações de subscrição, ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente, e o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para identificar a subscrição.</span><span class="sxs-lookup"><span data-stu-id="d063c-117">To get a subscription by ID, begin by obtaining an interface to the subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the subscription.</span></span> <span data-ttu-id="d063c-118">Utilize essa [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) para recuperar os detalhes da subscrição chamando [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get).</span><span class="sxs-lookup"><span data-stu-id="d063c-118">Use that [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) to retrieve the subscription details by calling [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string subscriptionID;

var subscriptionDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(subscriptionID).Get();
```

<span data-ttu-id="d063c-119">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d063c-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d063c-120">**Project**: Partner Center SDK Samples **Class**: GetSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="d063c-120">**Project**: Partner Center SDK Samples **Class**: GetSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="d063c-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d063c-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d063c-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d063c-122">Request syntax</span></span>

| <span data-ttu-id="d063c-123">Método</span><span class="sxs-lookup"><span data-stu-id="d063c-123">Method</span></span>  | <span data-ttu-id="d063c-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d063c-124">Request URI</span></span>                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d063c-125">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d063c-125">**GET**</span></span> | <span data-ttu-id="d063c-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d063c-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="d063c-127">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="d063c-127">URI parameter</span></span>

<span data-ttu-id="d063c-128">Esta tabela lista os parâmetros de consulta necessários para obter a subscrição.</span><span class="sxs-lookup"><span data-stu-id="d063c-128">This table lists the required query parameters to get the subscription.</span></span>

| <span data-ttu-id="d063c-129">Nome</span><span class="sxs-lookup"><span data-stu-id="d063c-129">Name</span></span>                    | <span data-ttu-id="d063c-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="d063c-130">Type</span></span>     | <span data-ttu-id="d063c-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="d063c-131">Required</span></span> | <span data-ttu-id="d063c-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="d063c-132">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="d063c-133">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="d063c-133">**customer-tenant-id**</span></span>  | <span data-ttu-id="d063c-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="d063c-134">**guid**</span></span> | <span data-ttu-id="d063c-135">Y</span><span class="sxs-lookup"><span data-stu-id="d063c-135">Y</span></span>        | <span data-ttu-id="d063c-136">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="d063c-136">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="d063c-137">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="d063c-137">**id-for-subscription**</span></span> | <span data-ttu-id="d063c-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="d063c-138">**guid**</span></span> | <span data-ttu-id="d063c-139">Y</span><span class="sxs-lookup"><span data-stu-id="d063c-139">Y</span></span>        | <span data-ttu-id="d063c-140">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="d063c-140">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d063c-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d063c-141">Request headers</span></span>

<span data-ttu-id="d063c-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d063c-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d063c-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d063c-143">Request body</span></span>

<span data-ttu-id="d063c-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d063c-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d063c-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d063c-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/A356AC8C-E310-44F4-BF85-C7F29044AF99 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="d063c-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d063c-146">REST response</span></span>

<span data-ttu-id="d063c-147">Se for bem sucedido, este método devolve um recurso [de Subscrição](subscription-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="d063c-147">If successful, this method returns a [Subscription](subscription-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d063c-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d063c-148">Response success and error codes</span></span>

<span data-ttu-id="d063c-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d063c-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d063c-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d063c-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d063c-151">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d063c-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-for-a-standard-subscription"></a><span data-ttu-id="d063c-152">Exemplo de resposta para uma subscrição padrão</span><span class="sxs-lookup"><span data-stu-id="d063c-152">Response example for a standard subscription</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 833
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CV: 7v11Wa//5EuGEo+A.0
MS-ServerId: 202010406
Date: Fri, 27 Jan 2017 21:51:40 GMT

{
    "id": "A356AC8C-E310-44F4-BF85-C7F29044AF99",
    "entitlementId": "42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
    "offerId": "MS-AZR-0145P",
    "offerName": "Microsoft Azure",
    "friendlyName": "Microsoft Azure",
    "quantity": 1,
    "unitType": "Usage-based",
    "creationDate": "2016-05-10T07:30:05.427Z",
    "effectiveStartDate": "2016-05-10T00:00:00Z",
    "commitmentEndDate": "9999-12-10T00:00:00Z",
    "status": "active",
    "autoRenewEnabled": false,
    "billingType": "usage",
    "contractType": "subscription",
    "links": {
        "offer": {
            "uri": "/offers/MS-AZR-0145P?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/A356AC8C-E310-44F4-BF85-C7F29044AF99",
            "method": "GET",
            "headers": []
        }
    },
    "orderId": "B23FDEDD-D6BD-415A-8B71-3624C81C9644",
    "attributes": {
        "etag": "eyJpZCI6ImEzNTZhYzhjLWUzMTAtNDRmNC1iZjg1LWM3ZjI5MDQ0YWY5OSIsInZlcnNpb24iOjJ9",
        "objectType": "Subscription"
    }
}
```

### <a name="response-example-for-an-add-on-subscription"></a><span data-ttu-id="d063c-153">Exemplo de resposta para uma subscrição de complemento</span><span class="sxs-lookup"><span data-stu-id="d063c-153">Response example for an add-on subscription</span></span>

<span data-ttu-id="d063c-154">A resposta para uma subscrição adicionada inclui o ID de subscrição dos pais no corpo e nos links.</span><span class="sxs-lookup"><span data-stu-id="d063c-154">The response for an add-on subscription includes the parent subscription ID in the body and in the links.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1132
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 6eacec93-852d-4167-9d96-c57809bea7ed
MS-RequestId: 22bfd0fb-d1e6-4a8f-aa1a-124b7c820d80
MS-CV: cmde2DtbuUWi8JLq.0
MS-ServerId: 201022015
Date: Fri, 27 Jan 2017 00:12:53 GMT

{
    "id": "968BA1CF-C146-4ADF-A300-308DCF718EEE",
    "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
    "offerName": "Exchange Online Archiving for Exchange Online",
    "friendlyName": "Some friendly name",
    "quantity": 2,
    "unitType": "Licenses",
    "parentSubscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
    "creationDate": "2017-01-25T23:01:08.693Z",
    "effectiveStartDate": "2017-01-25T00:00:00Z",
    "commitmentEndDate": "2018-02-10T00:00:00Z",
    "status": "active",
    "autoRenewEnabled": true,
    "billingType": "license",
    "contractType": "subscription",
    "links": {
        "offer": {
            "uri": "/offers/2828BE95-46BA-4F91-B2FD-0BEF192ECF60?country=US",
            "method": "GET",
            "headers": []
        },
        "parentSubscription": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/968BA1CF-C146-4ADF-A300-308DCF718EEE",
            "method": "GET",
            "headers": []
        }
    },
    "orderId": "CF3B0E37-BE0B-4CDD-B584-D1A97D98A922",
    "attributes": {
        "etag": "eyJpZCI6Ijk2OGJhMWNmLWMxNDYtNGFkZi1hMzAwLTMwOGRjZjcxOGVlZSIsInZlcnNpb24iOjF9",
        "objectType": "Subscription"
    }
}
```
