---
title: Obter uma lista de suplementos para uma subscrição
description: Como obter uma coleção de addons que um cliente escolheu adicionar à sua subscrição.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 4e62ad22cf30c34dedfeb628003c695e33b78758
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769337"
---
# <a name="get-a-list-of-add-ons-for-a-subscription"></a><span data-ttu-id="5d780-103">Obter uma lista de suplementos para uma subscrição</span><span class="sxs-lookup"><span data-stu-id="5d780-103">Get a list of add-ons for a subscription</span></span>

<span data-ttu-id="5d780-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="5d780-104">**Applies to:**</span></span>

- <span data-ttu-id="5d780-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="5d780-105">Partner Center</span></span>
- <span data-ttu-id="5d780-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="5d780-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="5d780-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="5d780-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="5d780-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5d780-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5d780-109">Este artigo descreve como obter uma coleção de addons que um cliente escolheu adicionar ao seu recurso **[de Subscrição.](subscription-resources.md)**</span><span class="sxs-lookup"><span data-stu-id="5d780-109">This article describes how to get a collection of add-ons that a customer has chosen to add to their **[Subscription](subscription-resources.md)** resource.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5d780-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5d780-110">Prerequisites</span></span>

- <span data-ttu-id="5d780-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5d780-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5d780-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="5d780-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="5d780-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5d780-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5d780-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5d780-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5d780-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="5d780-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5d780-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="5d780-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5d780-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="5d780-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5d780-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5d780-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="5d780-119">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="5d780-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="5d780-120">C\#</span><span class="sxs-lookup"><span data-stu-id="5d780-120">C\#</span></span>

<span data-ttu-id="5d780-121">Para obter a lista de complementos para a subscrição de um cliente:</span><span class="sxs-lookup"><span data-stu-id="5d780-121">To get the list of add-ons for a customer's subscription:</span></span>

1. <span data-ttu-id="5d780-122">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="5d780-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="5d780-123">Ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método [**ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="5d780-123">Call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span>

3. <span data-ttu-id="5d780-124">Ligue para a propriedade [**Addons,**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.addons) seguida por [**Get()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.get) ou [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.getasync).</span><span class="sxs-lookup"><span data-stu-id="5d780-124">Call the [**Addons**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.addons) property, followed by [**Get()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.getasync).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// var selectedSubscription Subscription;

var subscriptionDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).AddOns.Get();

```

<span data-ttu-id="5d780-125">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5d780-125">For an example, see the following:</span></span>

- <span data-ttu-id="5d780-126">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="5d780-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="5d780-127">Projeto: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="5d780-127">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="5d780-128">Classe: **SubscriptionAddons.cs**</span><span class="sxs-lookup"><span data-stu-id="5d780-128">Class: **SubscriptionAddons.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="5d780-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5d780-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5d780-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d780-130">Request syntax</span></span>

| <span data-ttu-id="5d780-131">Método</span><span class="sxs-lookup"><span data-stu-id="5d780-131">Method</span></span>  | <span data-ttu-id="5d780-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5d780-132">Request URI</span></span>                                                                                                                       |
|---------|-----------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5d780-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="5d780-133">**GET**</span></span> | <span data-ttu-id="5d780-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscrições/{id-for-subscription}/addons HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5d780-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/addons HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="5d780-135">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="5d780-135">URI parameter</span></span>

<span data-ttu-id="5d780-136">Esta tabela lista os parâmetros de consulta necessários para obter a lista de addons para a subscrição.</span><span class="sxs-lookup"><span data-stu-id="5d780-136">This table lists the required query parameters to get the list of add-ons for the subscription.</span></span>

| <span data-ttu-id="5d780-137">Nome</span><span class="sxs-lookup"><span data-stu-id="5d780-137">Name</span></span>                    | <span data-ttu-id="5d780-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="5d780-138">Type</span></span>     | <span data-ttu-id="5d780-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="5d780-139">Required</span></span> | <span data-ttu-id="5d780-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d780-140">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="5d780-141">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="5d780-141">**customer-tenant-id**</span></span>  | <span data-ttu-id="5d780-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="5d780-142">**guid**</span></span> | <span data-ttu-id="5d780-143">Y</span><span class="sxs-lookup"><span data-stu-id="5d780-143">Y</span></span>        | <span data-ttu-id="5d780-144">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="5d780-144">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="5d780-145">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="5d780-145">**id-for-subscription**</span></span> | <span data-ttu-id="5d780-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="5d780-146">**guid**</span></span> | <span data-ttu-id="5d780-147">Y</span><span class="sxs-lookup"><span data-stu-id="5d780-147">Y</span></span>        | <span data-ttu-id="5d780-148">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="5d780-148">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5d780-149">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="5d780-149">Request headers</span></span>

<span data-ttu-id="5d780-150">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5d780-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5d780-151">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5d780-151">Request body</span></span>

<span data-ttu-id="5d780-152">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5d780-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5d780-153">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5d780-153">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription>/addons HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 429902e2-ea2f-4704-b8a0-27fc53c539ba
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
```

## <a name="rest-response"></a><span data-ttu-id="5d780-154">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5d780-154">REST response</span></span>

<span data-ttu-id="5d780-155">Se for bem sucedido, este método devolve uma recolha de recursos no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="5d780-155">If successful, this method returns a collection of resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5d780-156">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5d780-156">Response success and error codes</span></span>

<span data-ttu-id="5d780-157">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5d780-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5d780-158">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5d780-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5d780-159">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="5d780-159">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5d780-160">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5d780-160">Response example</span></span>

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
