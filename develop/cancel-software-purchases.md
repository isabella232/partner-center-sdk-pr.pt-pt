---
title: Cancelar compras de software
description: Opção de autosserviço para cancelar subscrições de software e compras de software perpétuo usando APIs do Partner Center.
ms.date: 12/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 25fd10a171fa6ca01f3442d49145443f2382cc18
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769326"
---
# <a name="cancel-software-purchases"></a><span data-ttu-id="9377a-103">Cancelar compras de software</span><span class="sxs-lookup"><span data-stu-id="9377a-103">Cancel software purchases</span></span>

<span data-ttu-id="9377a-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="9377a-104">**Applies to:**</span></span>

- <span data-ttu-id="9377a-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="9377a-105">Partner Center</span></span>

<span data-ttu-id="9377a-106">Pode utilizar as APIs do Partner Center para cancelar subscrições de software e compras perpétuas de software (desde que essas compras fossem efetuas dentro da janela de cancelamento a partir da data de compra).</span><span class="sxs-lookup"><span data-stu-id="9377a-106">You can use the Partner Center APIs to cancel software subscriptions and perpetual software purchases (as long as those purchases were made within the cancellation window from the purchase date).</span></span> <span data-ttu-id="9377a-107">Você não precisa criar um bilhete de apoio para escamar tais cancelamentos, e pode usar os seguintes métodos de autosserviço em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9377a-107">You don't need to create a support ticket to make such cancellations, and can use the following self-service methods instead.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9377a-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9377a-108">Prerequisites</span></span>

- <span data-ttu-id="9377a-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9377a-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9377a-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="9377a-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="9377a-111">C\#</span><span class="sxs-lookup"><span data-stu-id="9377a-111">C\#</span></span>

<span data-ttu-id="9377a-112">Para cancelar uma ordem de software,</span><span class="sxs-lookup"><span data-stu-id="9377a-112">To cancel a software order,</span></span>

1. <span data-ttu-id="9377a-113">Passe as credenciais de conta para o método [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) para obter uma interface [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) para obter operações de parceiros.</span><span class="sxs-lookup"><span data-stu-id="9377a-113">Pass your account credentials to the [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to get partner operations.</span></span>

2. <span data-ttu-id="9377a-114">Selecione uma [determinada Ordem](order-resources.md#order) que pretende cancelar.</span><span class="sxs-lookup"><span data-stu-id="9377a-114">Select a particular [Order](order-resources.md#order) you wish to cancel.</span></span> <span data-ttu-id="9377a-115">Ligue para o método [**Clientes.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes, seguido de **Orders.ById()** com identificador de encomendas.</span><span class="sxs-lookup"><span data-stu-id="9377a-115">Call the [**Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier, followed by **Orders.ById()** with order identifier.</span></span>

3. <span data-ttu-id="9377a-116">Ligue para o método **Get** or **GetAsync** para recuperar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="9377a-116">Call the **Get** or **GetAsync** method to retrieve the order.</span></span>

4. <span data-ttu-id="9377a-117">Desa estação a [**propriedade Order.Status**](order-resources.md#order) para `cancelled` .</span><span class="sxs-lookup"><span data-stu-id="9377a-117">Set the [**Order.Status**](order-resources.md#order) property to `cancelled`.</span></span>

5. <span data-ttu-id="9377a-118">(Opcional) Se pretende especificar determinados itens de linha para cancelamento, deite o [**Order.LineItems**](order-resources.md#order) para listar os itens de linha que pretende cancelar.</span><span class="sxs-lookup"><span data-stu-id="9377a-118">(Optional) If you want to specify certain line items for cancellation, set the [**Order.LineItems**](order-resources.md#order) to list of line items that you want to cancel.</span></span>

6. <span data-ttu-id="9377a-119">Utilize o método **Patch()** para atualizar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="9377a-119">Use the **Patch()** method to update the order.</span></span>

``` csharp
// IPartnerCredentials accountCredentials;
// Customer tenant Id to be deleted.
// string customerTenantId;

IPartner accountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(accountCredentials);

// Cancel order
var order = accountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Get();
order.Status = "cancelled";
order.LineItems = new List<OrderLineItem> {
    order.LineItems.First()
};
order = accountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Patch(order);

```

## <a name="rest-request"></a><span data-ttu-id="9377a-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="9377a-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9377a-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="9377a-121">Request syntax</span></span>

| <span data-ttu-id="9377a-122">Método</span><span class="sxs-lookup"><span data-stu-id="9377a-122">Method</span></span>     | <span data-ttu-id="9377a-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="9377a-123">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="9377a-124">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="9377a-124">**PATCH**</span></span> | <span data-ttu-id="9377a-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/orders/{order-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9377a-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="9377a-126">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="9377a-126">URI parameters</span></span>

<span data-ttu-id="9377a-127">Utilize os seguintes parâmetros de consulta para eliminar um cliente.</span><span class="sxs-lookup"><span data-stu-id="9377a-127">Use the following query parameters to delete a customer.</span></span>

| <span data-ttu-id="9377a-128">Nome</span><span class="sxs-lookup"><span data-stu-id="9377a-128">Name</span></span>                   | <span data-ttu-id="9377a-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="9377a-129">Type</span></span>     | <span data-ttu-id="9377a-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="9377a-130">Required</span></span> | <span data-ttu-id="9377a-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="9377a-131">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9377a-132">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="9377a-132">**customer-tenant-id**</span></span> | <span data-ttu-id="9377a-133">**guid**</span><span class="sxs-lookup"><span data-stu-id="9377a-133">**guid**</span></span> | <span data-ttu-id="9377a-134">Y</span><span class="sxs-lookup"><span data-stu-id="9377a-134">Y</span></span>        | <span data-ttu-id="9377a-135">O valor é um identificador de inquilino de cliente formatado GUID que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="9377a-135">The value is a GUID formatted customer tenant identifier that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="9377a-136">**ordem id**</span><span class="sxs-lookup"><span data-stu-id="9377a-136">**order-id**</span></span> | <span data-ttu-id="9377a-137">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="9377a-137">**string**</span></span> | <span data-ttu-id="9377a-138">Y</span><span class="sxs-lookup"><span data-stu-id="9377a-138">Y</span></span>        | <span data-ttu-id="9377a-139">O valor é uma cadeia que denota o identificador da ordem que pretende cancelar.</span><span class="sxs-lookup"><span data-stu-id="9377a-139">The value is a string that denotes the identifier of the order that you want to cancel.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9377a-140">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="9377a-140">Request headers</span></span>

<span data-ttu-id="9377a-141">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9377a-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9377a-142">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="9377a-142">Request body</span></span>

```http
{
    “id”: “2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
    status": "cancelled",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DWMS"
        }
    ]
}
```

### <a name="request-example"></a><span data-ttu-id="9377a-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="9377a-143">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/orders/<order-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd

{
    "id": "2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
    "status": "cancelled",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DWMS"
        }
    ]
}
```

## <a name="rest-response"></a><span data-ttu-id="9377a-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="9377a-144">REST response</span></span>

<span data-ttu-id="9377a-145">Se for bem sucedido, este método devolve a encomenda com itens de linha cancelados.</span><span class="sxs-lookup"><span data-stu-id="9377a-145">If successful, this method returns the order with canceled line items.</span></span>

<span data-ttu-id="9377a-146">O estado da encomenda será marcado como **cancelado** se todos os itens de linha na encomenda forem cancelados, ou **concluídos** se não todos os itens de linha na encomenda forem cancelados.</span><span class="sxs-lookup"><span data-stu-id="9377a-146">The order status will be marked as either **cancelled** if all the line items in the order are cancelled, or **completed** if not all line items in the order are canceled.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9377a-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="9377a-147">Response success and error codes</span></span>

<span data-ttu-id="9377a-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="9377a-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9377a-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="9377a-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9377a-150">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="9377a-150">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9377a-151">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="9377a-151">Response example</span></span>

<span data-ttu-id="9377a-152">Na resposta de exemplo a seguir, pode ver que a quantidade de item de linha com o identificador de oferta **`DG7GMGF0FKZV:0003:DG7GMGF0DWMS`** tornou-se zero (0).</span><span class="sxs-lookup"><span data-stu-id="9377a-152">In the following example response, you can see that the quantity of line item with the offer identifier **`DG7GMGF0FKZV:0003:DG7GMGF0DWMS`** has become zero (0).</span></span> <span data-ttu-id="9377a-153">Esta alteração significa que o item da linha que foi marcado para cancelamento foi cancelado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="9377a-153">This change means that the line item that was marked for cancellation has been canceled successfully.</span></span> <span data-ttu-id="9377a-154">A ordem de exemplo contém outros itens de linha que não foram cancelados, o que significa que o estado da encomenda global será marcado como **concluído**, não **cancelado**.</span><span class="sxs-lookup"><span data-stu-id="9377a-154">The example order contains other line items that weren't canceled, which means that the status of the overall order will be marked as **completed**, not **cancelled**.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 866
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "id": "2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
    "alternateId": "c403d91b21d2",
    "referenceCustomerId": "45411344-b09d-47e7-9653-542006bf9766",
    "billingCycle": "one_time",
    "currencyCode": "USD",
    "currencySymbol": "$",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DWMS",
            "termDuration": "P3Y",
            "transactionType": "New",
            "friendlyName": "SQL Server Enterprise - 2 Core License Pack - 3 year",
            "quantity": 0,
            "links": {
                "product": {
                    "uri": "/products/DG7GMGF0FKZV?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DG7GMGF0FKZV/skus/0003?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DG7GMGF0FKZV/skus/0003/availabilities/DG7GMGF0DWMS?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        {
            "lineItemNumber": 1,
            "offerId": "DG7GMGF0DVT7:000C:DG7GMGF0FVZM",
            "termDuration": "P3Y",
            "transactionType": "New",
            "friendlyName": "Windows Server CAL - 1 Device CAL - 3 year",
            "quantity": 1,
            "links": {
                "product": {
                    "uri": "/products/DG7GMGF0DVT7?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DG7GMGF0DVT7/skus/000C?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DG7GMGF0DVT7/skus/000C/availabilities/DG7GMGF0FVZM?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2019-12-12T17:33:56.1306495Z",
    "status": "completed",
    "transactionType": "UserPurchase",
    "links": {
        "self": {
            "uri": "/customers/45411344-b09d-47e7-9653-542006bf9766/orders/2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
            "method": "GET",
            "headers": []
        },
        "provisioningStatus": {
            "uri": "/customers/45411344-b09d-47e7-9653-542006bf9766/orders/2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "patchOperation": {
            "uri": "/customers/45411344-b09d-47e7-9653-542006bf9766/orders/2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
            "method": "PATCH",
            "headers": []
        }
    },
    "client": {
        "marketplaceCountry": "US",
        "deviceFamily": "UniversalStore-PartnerCenter",
        "name": "Partner Center API"
    },
    "attributes": {
        "objectType": "Order"
    }
}
```
