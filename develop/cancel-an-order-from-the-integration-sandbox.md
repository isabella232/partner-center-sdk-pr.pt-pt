---
title: Cancelar uma encomenda da caixa de areia de integração
description: Saiba como usar as APIs do Partner Center para cancelar diferentes tipos de pedidos de subscrição a partir de contas de caixas de areia de integração.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 363bf209e27d5223259c8c533710a3b35bbef1e6
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770082"
---
# <a name="cancel-an-order-from-the-integration-sandbox-using-partner-center-apis"></a><span data-ttu-id="bc1fd-103">Cancelar uma encomenda da caixa de areia de integração usando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="bc1fd-103">Cancel an order from the integration sandbox using Partner Center APIs</span></span>

<span data-ttu-id="bc1fd-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="bc1fd-104">**Applies to:**</span></span>

- <span data-ttu-id="bc1fd-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="bc1fd-105">Partner Center</span></span>
- <span data-ttu-id="bc1fd-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="bc1fd-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="bc1fd-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="bc1fd-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="bc1fd-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="bc1fd-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="bc1fd-109">Este artigo descreve como usar as APIs do Partner Center para cancelar diferentes tipos de ordens de subscrição a partir de contas de caixas de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-109">This article describes how to use Partner Center APIs to cancel different types of subscription orders from integration sandbox accounts.</span></span> <span data-ttu-id="bc1fd-110">Tais encomendas podem incluir instâncias reservadas, software e marketplace comercial Software como uma ordem de subscrição de Serviço (SaaS).</span><span class="sxs-lookup"><span data-stu-id="bc1fd-110">Such orders can include reserved instances, software, and commercial marketplace Software as a Service (SaaS) subscription orders.</span></span>

>[!NOTE]
><span data-ttu-id="bc1fd-111">Tenha em atenção que os cancelamentos de instâncias reservadas ou encomendas de subscrição saaS de marketplace comercial só são possíveis a partir de contas de sandbox de integração.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-111">Please be aware that the cancellations of reserved instance, or commercial marketplace SaaS subscription orders are only possible from integration sandbox accounts.</span></span>  

<span data-ttu-id="bc1fd-112">Para cancelar as ordens de produção de software através da API, utilize [as compras de cancelamento de software](cancel-software-purchases.md).</span><span class="sxs-lookup"><span data-stu-id="bc1fd-112">To cancel production orders of software through API, use [cancel-software-purchases](cancel-software-purchases.md).</span></span>
<span data-ttu-id="bc1fd-113">Também pode cancelar as ordens de produção de software através do dashboard usando [cancelar uma compra](/partner-center/csp-software-subscriptions).</span><span class="sxs-lookup"><span data-stu-id="bc1fd-113">You can also cancel production orders of software through dashboard using [cancel a purchase](/partner-center/csp-software-subscriptions).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bc1fd-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bc1fd-114">Prerequisites</span></span>

- <span data-ttu-id="bc1fd-115">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bc1fd-115">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bc1fd-116">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-116">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="bc1fd-117">Uma conta parceira de sandbox de integração com um cliente com uma instância reservada ativa / software / encomendas de subscrição saaS de terceiros.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-117">An integration sandbox partner account with a customer having active reserved instance / software / third-party SaaS subscription orders.</span></span>

## <a name="c"></a><span data-ttu-id="bc1fd-118">C\#</span><span class="sxs-lookup"><span data-stu-id="bc1fd-118">C\#</span></span>

<span data-ttu-id="bc1fd-119">Para cancelar uma encomenda da caixa de areia de integração, passe as credenciais da sua conta para o [**`CreatePartnerOperations`**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) método para obter uma interface para obter [**`IPartner`**](/dotnet/api/microsoft.store.partnercenter.ipartner) operações de parceiro.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-119">To cancel an order from the integration sandbox, pass your account credentials to the [**`CreatePartnerOperations`**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**`IPartner`**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to get partner operations.</span></span>

<span data-ttu-id="bc1fd-120">Para selecionar uma [determinada Encomenda](order-resources.md#order), utilize as operações do parceiro e ligue com [**`Customers.ById()`**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) o identificador do cliente para especificar o cliente, seguido pelo **`Orders.ById()`** identificador de encomendas para especificar a encomenda e, **`Get`** finalmente, ou método para **`GetAsync`** recuperá-la.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-120">To select a particular [Order](order-resources.md#order), use the partner operations and call [**`Customers.ById()`**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to specify the customer, followed by **`Orders.ById()`** with order identifier to specify the order and finally **`Get`** or **`GetAsync`** method to retrieve it.</span></span>

<span data-ttu-id="bc1fd-121">Desave o [**`Order.Status`**](order-resources.md#order) imóvel `cancelled` e utilize o método para atualizar a **`Patch()`** encomenda.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-121">Set the [**`Order.Status`**](order-resources.md#order) property to `cancelled` and use the **`Patch()`** method to update the order.</span></span>

``` csharp
// IPartnerCredentials tipAccountCredentials;
// Customer tenant Id to be deleted.
// string customerTenantId;

IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

// Cancel order
var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Get();
order.Status = "cancelled";
order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Patch(order);

```

## <a name="rest-request"></a><span data-ttu-id="bc1fd-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="bc1fd-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bc1fd-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc1fd-123">Request syntax</span></span>

| <span data-ttu-id="bc1fd-124">Método</span><span class="sxs-lookup"><span data-stu-id="bc1fd-124">Method</span></span>     | <span data-ttu-id="bc1fd-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="bc1fd-125">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="bc1fd-126">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="bc1fd-126">**PATCH**</span></span> | <span data-ttu-id="bc1fd-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/orders/{order-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="bc1fd-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="bc1fd-128">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="bc1fd-128">URI parameter</span></span>

<span data-ttu-id="bc1fd-129">Utilize o seguinte parâmetro de consulta para eliminar um cliente.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-129">Use the following query parameter to delete a customer.</span></span>

| <span data-ttu-id="bc1fd-130">Nome</span><span class="sxs-lookup"><span data-stu-id="bc1fd-130">Name</span></span>                   | <span data-ttu-id="bc1fd-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="bc1fd-131">Type</span></span>     | <span data-ttu-id="bc1fd-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="bc1fd-132">Required</span></span> | <span data-ttu-id="bc1fd-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc1fd-133">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bc1fd-134">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="bc1fd-134">**customer-tenant-id**</span></span> | <span data-ttu-id="bc1fd-135">**guid**</span><span class="sxs-lookup"><span data-stu-id="bc1fd-135">**guid**</span></span> | <span data-ttu-id="bc1fd-136">Y</span><span class="sxs-lookup"><span data-stu-id="bc1fd-136">Y</span></span>        | <span data-ttu-id="bc1fd-137">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-137">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="bc1fd-138">**ordem id**</span><span class="sxs-lookup"><span data-stu-id="bc1fd-138">**order-id**</span></span> | <span data-ttu-id="bc1fd-139">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="bc1fd-139">**string**</span></span> | <span data-ttu-id="bc1fd-140">Y</span><span class="sxs-lookup"><span data-stu-id="bc1fd-140">Y</span></span>        | <span data-ttu-id="bc1fd-141">O valor é uma cadeia que denota os IDs de encomenda que precisam de ser cancelados.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-141">The value is a string denoting the order IDs that need to be canceled.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="bc1fd-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="bc1fd-142">Request headers</span></span>

<span data-ttu-id="bc1fd-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="bc1fd-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bc1fd-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="bc1fd-144">Request body</span></span>

```http
{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "status": "cancelled",
}
```

### <a name="request-example"></a><span data-ttu-id="bc1fd-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="bc1fd-145">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/orders/<order-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd

{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "status": "cancelled",
}
```

## <a name="rest-response"></a><span data-ttu-id="bc1fd-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="bc1fd-146">REST response</span></span>

<span data-ttu-id="bc1fd-147">Se for bem sucedido, este método devolve a encomenda cancelada.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-147">If successful, this method returns the canceled order.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bc1fd-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="bc1fd-148">Response success and error codes</span></span>

<span data-ttu-id="bc1fd-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bc1fd-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="bc1fd-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bc1fd-151">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="bc1fd-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="bc1fd-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="bc1fd-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 866
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "alternateId": "11fc4bdfd47a",
    "referenceCustomerId": "bd59b416-37f9-4d8f-8df3-5750111fc615",
    "billingCycle": "one_time",
    "currencyCode": "USD",
    "currencySymbol": "$",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0DWT0:0001:DG7GMGF0DSQR",
            "termDuration": "",
            "transactionType": "New",
            "friendlyName": "Microsoft Identity Manager 2016 - 1 User CAL",
            "quantity": 1,
            "links": {
                "product": {
                    "uri": "/products/DG7GMGF0DWT0?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DG7GMGF0DWT0/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DG7GMGF0DWT0/skus/0001/availabilities/DG7GMGF0DSQR?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2019-02-21T17:56:21.1335741Z",
    "status": "cancelled",
    "transactionType": "UserPurchase",
    "attributes": {
        "objectType": "Order"
    }
}
```
