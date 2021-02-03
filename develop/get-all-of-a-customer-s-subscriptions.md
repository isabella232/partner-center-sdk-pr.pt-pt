---
title: Obter as subscrições de um cliente
description: Como obter uma coleção de assinaturas de um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a037e4a81fccbff0a02b0bdf6d93478ee15fd50f
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769716"
---
# <a name="get-a-customers-subscriptions"></a><span data-ttu-id="fbc2e-103">Obter as subscrições de um cliente</span><span class="sxs-lookup"><span data-stu-id="fbc2e-103">Get a customer's subscriptions</span></span>

<span data-ttu-id="fbc2e-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="fbc2e-104">**Applies To**</span></span>

- <span data-ttu-id="fbc2e-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="fbc2e-105">Partner Center</span></span>
- <span data-ttu-id="fbc2e-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="fbc2e-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="fbc2e-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="fbc2e-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="fbc2e-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fbc2e-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fbc2e-109">Como obter uma coleção de assinaturas de um cliente.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-109">How to get a collection of a customer's subscriptions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fbc2e-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fbc2e-110">Prerequisites</span></span>

- <span data-ttu-id="fbc2e-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fbc2e-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fbc2e-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="fbc2e-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fbc2e-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="fbc2e-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="fbc2e-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="fbc2e-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="fbc2e-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="fbc2e-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="fbc2e-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="fbc2e-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fbc2e-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="fbc2e-119">C\#</span><span class="sxs-lookup"><span data-stu-id="fbc2e-119">C\#</span></span>

<span data-ttu-id="fbc2e-120">Para obter uma lista de todas as subscrições de um cliente, utilize primeiro o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-120">To get a list of all of a customer's subscriptions, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to identify the customer.</span></span> <span data-ttu-id="fbc2e-121">Em seguida, utilize a propriedade [**Subscrições**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) para recuperar uma interface para operações de recolha de subscrição.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-121">Then use the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to subscription collection operations.</span></span> <span data-ttu-id="fbc2e-122">Por fim, ligue para os métodos [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) para recuperar a recolha de assinaturas do cliente.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-122">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) methods to retrieve the customer's subscriptions collection.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var customerSubscriptions = partnerOperations.Customers.ById(customerId).Subscriptions.Get();
```

<span data-ttu-id="fbc2e-123">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="fbc2e-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="fbc2e-124">**Projeto**: Partner Center SDK Samples **Class**: GetSubscriptions.cs</span><span class="sxs-lookup"><span data-stu-id="fbc2e-124">**Project**: Partner Center SDK Samples **Class**: GetSubscriptions.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="fbc2e-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="fbc2e-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fbc2e-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbc2e-126">Request syntax</span></span>

| <span data-ttu-id="fbc2e-127">Método</span><span class="sxs-lookup"><span data-stu-id="fbc2e-127">Method</span></span>  | <span data-ttu-id="fbc2e-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="fbc2e-128">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fbc2e-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="fbc2e-129">**GET**</span></span> | <span data-ttu-id="fbc2e-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fbc2e-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="fbc2e-131">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="fbc2e-131">URI parameter</span></span>

<span data-ttu-id="fbc2e-132">Esta tabela lista o parâmetro de consulta necessário para obter todas as subscrições.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-132">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="fbc2e-133">Nome</span><span class="sxs-lookup"><span data-stu-id="fbc2e-133">Name</span></span>               | <span data-ttu-id="fbc2e-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="fbc2e-134">Type</span></span>   | <span data-ttu-id="fbc2e-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="fbc2e-135">Required</span></span> | <span data-ttu-id="fbc2e-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbc2e-136">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="fbc2e-137">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="fbc2e-137">customer-tenant-id</span></span> | <span data-ttu-id="fbc2e-138">string</span><span class="sxs-lookup"><span data-stu-id="fbc2e-138">string</span></span> | <span data-ttu-id="fbc2e-139">Sim</span><span class="sxs-lookup"><span data-stu-id="fbc2e-139">Yes</span></span>      | <span data-ttu-id="fbc2e-140">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-140">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fbc2e-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="fbc2e-141">Request headers</span></span>

<span data-ttu-id="fbc2e-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="fbc2e-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fbc2e-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="fbc2e-143">Request body</span></span>

<span data-ttu-id="fbc2e-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fbc2e-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="fbc2e-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b2d13828-2ca5-41d4-94fb-9946214f4244
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="fbc2e-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="fbc2e-146">REST response</span></span>

<span data-ttu-id="fbc2e-147">Se for bem sucedido, este método devolve uma recolha de recursos de [Subscrição](subscription-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-147">If successful, this method returns a collection of [Subscription](subscription-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fbc2e-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="fbc2e-148">Response success and error codes</span></span>

<span data-ttu-id="fbc2e-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fbc2e-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="fbc2e-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fbc2e-151">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="fbc2e-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fbc2e-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="fbc2e-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
MS-RequestId: b2d13828-2ca5-41d4-94fb-9946214f4244
Date: Wed, 25 Nov 2015 05:43:06 GMT

{
    "totalCount": 37,
    "items": [{
        "id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
        "entitlementId": "a356ac8c-e310-44f4-bf85-C7f29044af99",
        "friendlyName": "nickname",
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
        "orderId": "6183db3d-6318-4e52-877e-25806e4971be",
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
