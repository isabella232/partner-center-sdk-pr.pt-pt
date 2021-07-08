---
title: Obter uma lista de suplementos para uma subscrição
description: Como obter uma coleção de addons que um cliente escolheu adicionar à sua subscrição.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: c627f595333a295048b02ec4326dcdc279d07b51
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874640"
---
# <a name="get-a-list-of-add-ons-for-a-subscription"></a><span data-ttu-id="5c3ae-103">Obter uma lista de suplementos para uma subscrição</span><span class="sxs-lookup"><span data-stu-id="5c3ae-103">Get a list of add-ons for a subscription</span></span>

<span data-ttu-id="5c3ae-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5c3ae-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5c3ae-105">Este artigo descreve como obter uma coleção de addons que um cliente escolheu adicionar ao seu recurso **[de Subscrição.](subscription-resources.md)**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-105">This article describes how to get a collection of add-ons that a customer has chosen to add to their **[Subscription](subscription-resources.md)** resource.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5c3ae-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5c3ae-106">Prerequisites</span></span>

- <span data-ttu-id="5c3ae-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5c3ae-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5c3ae-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="5c3ae-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5c3ae-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5c3ae-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5c3ae-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5c3ae-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5c3ae-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5c3ae-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5c3ae-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="5c3ae-115">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-115">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="5c3ae-116">C\#</span><span class="sxs-lookup"><span data-stu-id="5c3ae-116">C\#</span></span>

<span data-ttu-id="5c3ae-117">Para obter a lista de complementos para a subscrição de um cliente:</span><span class="sxs-lookup"><span data-stu-id="5c3ae-117">To get the list of add-ons for a customer's subscription:</span></span>

1. <span data-ttu-id="5c3ae-118">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-118">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="5c3ae-119">Ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método [**ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="5c3ae-119">Call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span>

3. <span data-ttu-id="5c3ae-120">Ligue para a propriedade [**Addons,**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.addons) seguida por [**Get()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.get) ou [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.getasync).</span><span class="sxs-lookup"><span data-stu-id="5c3ae-120">Call the [**Addons**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.addons) property, followed by [**Get()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.getasync).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// var selectedSubscription Subscription;

var subscriptionDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).AddOns.Get();

```

<span data-ttu-id="5c3ae-121">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5c3ae-121">For an example, see the following:</span></span>

- <span data-ttu-id="5c3ae-122">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="5c3ae-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="5c3ae-123">Project: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-123">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="5c3ae-124">Classe: **AssinaturaAddons.cs**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-124">Class: **SubscriptionAddons.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="5c3ae-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5c3ae-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5c3ae-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c3ae-126">Request syntax</span></span>

| <span data-ttu-id="5c3ae-127">Método</span><span class="sxs-lookup"><span data-stu-id="5c3ae-127">Method</span></span>  | <span data-ttu-id="5c3ae-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5c3ae-128">Request URI</span></span>                                                                                                                       |
|---------|-----------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5c3ae-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-129">**GET**</span></span> | <span data-ttu-id="5c3ae-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscrições/{id-for-subscription}/addons HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5c3ae-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/addons HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="5c3ae-131">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="5c3ae-131">URI parameter</span></span>

<span data-ttu-id="5c3ae-132">Esta tabela lista os parâmetros de consulta necessários para obter a lista de addons para a subscrição.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-132">This table lists the required query parameters to get the list of add-ons for the subscription.</span></span>

| <span data-ttu-id="5c3ae-133">Nome</span><span class="sxs-lookup"><span data-stu-id="5c3ae-133">Name</span></span>                    | <span data-ttu-id="5c3ae-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="5c3ae-134">Type</span></span>     | <span data-ttu-id="5c3ae-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="5c3ae-135">Required</span></span> | <span data-ttu-id="5c3ae-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c3ae-136">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="5c3ae-137">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-137">**customer-tenant-id**</span></span>  | <span data-ttu-id="5c3ae-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-138">**guid**</span></span> | <span data-ttu-id="5c3ae-139">Y</span><span class="sxs-lookup"><span data-stu-id="5c3ae-139">Y</span></span>        | <span data-ttu-id="5c3ae-140">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-140">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="5c3ae-141">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-141">**id-for-subscription**</span></span> | <span data-ttu-id="5c3ae-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="5c3ae-142">**guid**</span></span> | <span data-ttu-id="5c3ae-143">Y</span><span class="sxs-lookup"><span data-stu-id="5c3ae-143">Y</span></span>        | <span data-ttu-id="5c3ae-144">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-144">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5c3ae-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="5c3ae-145">Request headers</span></span>

<span data-ttu-id="5c3ae-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5c3ae-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5c3ae-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5c3ae-147">Request body</span></span>

<span data-ttu-id="5c3ae-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5c3ae-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5c3ae-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription>/addons HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 429902e2-ea2f-4704-b8a0-27fc53c539ba
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
```

## <a name="rest-response"></a><span data-ttu-id="5c3ae-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5c3ae-150">REST response</span></span>

<span data-ttu-id="5c3ae-151">Se for bem sucedido, este método devolve uma recolha de recursos no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-151">If successful, this method returns a collection of resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5c3ae-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5c3ae-152">Response success and error codes</span></span>

<span data-ttu-id="5c3ae-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5c3ae-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5c3ae-155">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="5c3ae-155">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5c3ae-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5c3ae-156">Response example</span></span>

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
        "entitlementId": "42226ed6-070a-4e0f-b80c-4cdfB3e97aa7",
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
