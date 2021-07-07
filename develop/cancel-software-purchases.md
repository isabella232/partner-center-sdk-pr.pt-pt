---
title: Cancelar compras de software
description: Opção de autosserviço para cancelar subscrições de software e compras de software perpétuo usando APIs do Partner Center.
ms.date: 12/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 877702ac930919ff72c6cc45a3c0e8ecc7e1b5f4
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974238"
---
# <a name="cancel-software-purchases"></a><span data-ttu-id="013c3-103">Cancelar compras de software</span><span class="sxs-lookup"><span data-stu-id="013c3-103">Cancel software purchases</span></span>

<span data-ttu-id="013c3-104">Pode utilizar as APIs do Partner Center para cancelar subscrições de software e compras perpétuas de software (desde que essas compras fossem efetuas dentro da janela de cancelamento a partir da data de compra).</span><span class="sxs-lookup"><span data-stu-id="013c3-104">You can use the Partner Center APIs to cancel software subscriptions and perpetual software purchases (as long as those purchases were made within the cancellation window from the purchase date).</span></span> <span data-ttu-id="013c3-105">Você não precisa criar um bilhete de apoio para escamar tais cancelamentos, e pode usar os seguintes métodos de autosserviço em vez disso.</span><span class="sxs-lookup"><span data-stu-id="013c3-105">You don't need to create a support ticket to make such cancellations, and can use the following self-service methods instead.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="013c3-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="013c3-106">Prerequisites</span></span>

- <span data-ttu-id="013c3-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="013c3-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="013c3-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="013c3-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="013c3-109">C\#</span><span class="sxs-lookup"><span data-stu-id="013c3-109">C\#</span></span>

<span data-ttu-id="013c3-110">Para cancelar uma ordem de software,</span><span class="sxs-lookup"><span data-stu-id="013c3-110">To cancel a software order,</span></span>

1. <span data-ttu-id="013c3-111">Passe as credenciais de conta para o método [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) para obter uma interface [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) para obter operações de parceiros.</span><span class="sxs-lookup"><span data-stu-id="013c3-111">Pass your account credentials to the [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to get partner operations.</span></span>

2. <span data-ttu-id="013c3-112">Selecione uma [determinada Ordem](order-resources.md#order) que pretende cancelar.</span><span class="sxs-lookup"><span data-stu-id="013c3-112">Select a particular [Order](order-resources.md#order) you wish to cancel.</span></span> <span data-ttu-id="013c3-113">Ligue para o método [**Clientes.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes, seguido de **Orders.ById()** com identificador de encomendas.</span><span class="sxs-lookup"><span data-stu-id="013c3-113">Call the [**Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier, followed by **Orders.ById()** with order identifier.</span></span>

3. <span data-ttu-id="013c3-114">Ligue para o método **Get** or **GetAsync** para recuperar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="013c3-114">Call the **Get** or **GetAsync** method to retrieve the order.</span></span>

4. <span data-ttu-id="013c3-115">Desa estação a [**propriedade Order.Status**](order-resources.md#order) para `cancelled` .</span><span class="sxs-lookup"><span data-stu-id="013c3-115">Set the [**Order.Status**](order-resources.md#order) property to `cancelled`.</span></span>

5. <span data-ttu-id="013c3-116">(Opcional) Se pretende especificar determinados itens de linha para cancelamento, deite o [**Order.LineItems**](order-resources.md#order) para listar os itens de linha que pretende cancelar.</span><span class="sxs-lookup"><span data-stu-id="013c3-116">(Optional) If you want to specify certain line items for cancellation, set the [**Order.LineItems**](order-resources.md#order) to list of line items that you want to cancel.</span></span>

6. <span data-ttu-id="013c3-117">Utilize o método **Patch()** para atualizar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="013c3-117">Use the **Patch()** method to update the order.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="013c3-118">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="013c3-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="013c3-119">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="013c3-119">Request syntax</span></span>

| <span data-ttu-id="013c3-120">Método</span><span class="sxs-lookup"><span data-stu-id="013c3-120">Method</span></span>     | <span data-ttu-id="013c3-121">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="013c3-121">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="013c3-122">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="013c3-122">**PATCH**</span></span> | <span data-ttu-id="013c3-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/orders/{order-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="013c3-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="013c3-124">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="013c3-124">URI parameters</span></span>

<span data-ttu-id="013c3-125">Utilize os seguintes parâmetros de consulta para eliminar um cliente.</span><span class="sxs-lookup"><span data-stu-id="013c3-125">Use the following query parameters to delete a customer.</span></span>

| <span data-ttu-id="013c3-126">Nome</span><span class="sxs-lookup"><span data-stu-id="013c3-126">Name</span></span>                   | <span data-ttu-id="013c3-127">Tipo</span><span class="sxs-lookup"><span data-stu-id="013c3-127">Type</span></span>     | <span data-ttu-id="013c3-128">Necessário</span><span class="sxs-lookup"><span data-stu-id="013c3-128">Required</span></span> | <span data-ttu-id="013c3-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="013c3-129">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="013c3-130">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="013c3-130">**customer-tenant-id**</span></span> | <span data-ttu-id="013c3-131">**guid**</span><span class="sxs-lookup"><span data-stu-id="013c3-131">**guid**</span></span> | <span data-ttu-id="013c3-132">Y</span><span class="sxs-lookup"><span data-stu-id="013c3-132">Y</span></span>        | <span data-ttu-id="013c3-133">O valor é um identificador de inquilino de cliente formatado GUID que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="013c3-133">The value is a GUID formatted customer tenant identifier that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="013c3-134">**ordem id**</span><span class="sxs-lookup"><span data-stu-id="013c3-134">**order-id**</span></span> | <span data-ttu-id="013c3-135">**string**</span><span class="sxs-lookup"><span data-stu-id="013c3-135">**string**</span></span> | <span data-ttu-id="013c3-136">Y</span><span class="sxs-lookup"><span data-stu-id="013c3-136">Y</span></span>        | <span data-ttu-id="013c3-137">O valor é uma cadeia que denota o identificador da ordem que pretende cancelar.</span><span class="sxs-lookup"><span data-stu-id="013c3-137">The value is a string that denotes the identifier of the order that you want to cancel.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="013c3-138">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="013c3-138">Request headers</span></span>

<span data-ttu-id="013c3-139">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="013c3-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="013c3-140">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="013c3-140">Request body</span></span>

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

### <a name="request-example"></a><span data-ttu-id="013c3-141">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="013c3-141">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="013c3-142">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="013c3-142">REST response</span></span>

<span data-ttu-id="013c3-143">Se for bem sucedido, este método devolve a encomenda com itens de linha cancelados.</span><span class="sxs-lookup"><span data-stu-id="013c3-143">If successful, this method returns the order with canceled line items.</span></span>

<span data-ttu-id="013c3-144">O estado da encomenda será marcado como **cancelado** se todos os itens de linha na encomenda forem cancelados, ou **concluídos** se não todos os itens de linha na encomenda forem cancelados.</span><span class="sxs-lookup"><span data-stu-id="013c3-144">The order status will be marked as either **cancelled** if all the line items in the order are canceled, or **completed** if not all line items in the order are canceled.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="013c3-145">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="013c3-145">Response success and error codes</span></span>

<span data-ttu-id="013c3-146">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="013c3-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="013c3-147">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="013c3-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="013c3-148">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="013c3-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="013c3-149">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="013c3-149">Response example</span></span>

<span data-ttu-id="013c3-150">Na resposta de exemplo a seguir, pode ver que a quantidade de item de linha com o identificador de oferta **`DG7GMGF0FKZV:0003:DG7GMGF0DWMS`** tornou-se zero (0).</span><span class="sxs-lookup"><span data-stu-id="013c3-150">In the following example response, you can see that the quantity of line item with the offer identifier **`DG7GMGF0FKZV:0003:DG7GMGF0DWMS`** has become zero (0).</span></span> <span data-ttu-id="013c3-151">Esta alteração significa que o item da linha que foi marcado para cancelamento foi cancelado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="013c3-151">This change means that the line item that was marked for cancellation has been canceled successfully.</span></span> <span data-ttu-id="013c3-152">A ordem de exemplo contém outros itens de linha que não foram cancelados, o que significa que o estado da encomenda global será marcado como **concluído**, não **cancelado**.</span><span class="sxs-lookup"><span data-stu-id="013c3-152">The example order contains other line items that weren't canceled, which means that the status of the overall order will be marked as **completed**, not **cancelled**.</span></span>

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
