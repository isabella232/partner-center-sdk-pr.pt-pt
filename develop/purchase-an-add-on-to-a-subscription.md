---
title: Comprar um suplemento para uma subscrição
description: Como comprar um suplemento a uma subscrição existente.
ms.date: 11/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d8b700a2ad41a37ca0ad745f3e7767449974b18a
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547687"
---
# <a name="purchase-an-add-on-to-a-subscription"></a><span data-ttu-id="4a5a3-103">Comprar um suplemento para uma subscrição</span><span class="sxs-lookup"><span data-stu-id="4a5a3-103">Purchase an add-on to a subscription</span></span>

<span data-ttu-id="4a5a3-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4a5a3-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4a5a3-105">Como comprar um suplemento a uma subscrição existente.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-105">How to purchase an add-on to an existing subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4a5a3-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4a5a3-106">Prerequisites</span></span>

- <span data-ttu-id="4a5a3-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4a5a3-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4a5a3-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="4a5a3-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4a5a3-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4a5a3-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4a5a3-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4a5a3-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="4a5a3-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4a5a3-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="4a5a3-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4a5a3-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4a5a3-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="4a5a3-115">Um ID de assinatura.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-115">A subscription ID.</span></span> <span data-ttu-id="4a5a3-116">Esta é a subscrição existente para a compra de uma oferta de complemento.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-116">This is the existing subscription for which to purchase an add-on offer.</span></span>

- <span data-ttu-id="4a5a3-117">Um ID de oferta que identifica a oferta de compra.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-117">An offer ID that identifies the add-on offer to purchase.</span></span>

## <a name="purchasing-an-add-on-through-code"></a><span data-ttu-id="4a5a3-118">Compra de um código add-on através</span><span class="sxs-lookup"><span data-stu-id="4a5a3-118">Purchasing an add-on through code</span></span>

<span data-ttu-id="4a5a3-119">Ao adquirir um complemento a uma subscrição, está a atualizar a ordem de subscrição original com a encomenda para o add-on.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-119">When you purchase an add-on to a subscription, you are updating the original subscription order with the order for the add-on.</span></span> <span data-ttu-id="4a5a3-120">No seguinte, customerId é o ID do cliente, subscriçãoId é o ID de subscrição, e addOnOfferId é o ID de oferta para o add-on.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-120">In the following, customerId is the customer ID, subscriptionId is the subscription ID, and addOnOfferId is the offer ID for the add-on.</span></span>

<span data-ttu-id="4a5a3-121">Eis os passos:</span><span class="sxs-lookup"><span data-stu-id="4a5a3-121">Here are the steps:</span></span>

1.  <span data-ttu-id="4a5a3-122">Obtenha uma interface para as operações para a subscrição.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-122">Get an interface to the operations for the subscription.</span></span>

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2.  <span data-ttu-id="4a5a3-123">Utilize essa interface para instantaneaizar um objeto de subscrição.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-123">Use that interface to instantiate a subscription object.</span></span> <span data-ttu-id="4a5a3-124">Isto dá-lhe os detalhes da subscrição dos pais, incluindo o ID da encomenda.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-124">This gets you the parent subscription details, including the order ID.</span></span>

    ``` csharp
    var parentSubscription = subscriptionOperations.Get();
    ```

3.  <span data-ttu-id="4a5a3-125">Instantaneamente um novo objeto [**da Ordem.**](/dotnet/api/microsoft.store.partnercenter.models.orders.order)</span><span class="sxs-lookup"><span data-stu-id="4a5a3-125">Instantiate a new [**Order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object.</span></span> <span data-ttu-id="4a5a3-126">Esta instância de encomenda é utilizada para atualizar a encomenda original utilizada para a compra da subscrição.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-126">This order instance is used to update the original order used to purchase the subscription.</span></span> <span data-ttu-id="4a5a3-127">Adicione um item de linha única à ordem que representa o addon.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-127">Add a single-line item to the order that represents the add-on.</span></span>
    ``` csharp
    var orderToUpdate = new Order()
    {
        ReferenceCustomerId = customerId,
        LineItems = new List<OrderLineItem>()
        {
            new OrderLineItem()
            {
                LineItemNumber = 0,
                OfferId = addOnOfferId,
                FriendlyName = "Some friendly name",
                Quantity = 2,
                ParentSubscriptionId = subscriptionId
            }
        }
    };
    ```

4.  <span data-ttu-id="4a5a3-128">Atualize a encomenda original para a subscrição com a nova encomenda para o add-on.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-128">Update the original order for the subscription with the new order for the add-on.</span></span>
    ``` csharp
    Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
    ```

## <a name="c"></a><span data-ttu-id="4a5a3-129">C\#</span><span class="sxs-lookup"><span data-stu-id="4a5a3-129">C\#</span></span>

<span data-ttu-id="4a5a3-130">Para adquirir um addon, comece por obter uma interface para as operações de subscrição, ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente, e o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para identificar a subscrição que tem a oferta adicional.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-130">To purchase an add-on, begin by obtaining an interface to the subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the subscription that has the add-on offer.</span></span> <span data-ttu-id="4a5a3-131">Utilize essa [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) para recuperar os detalhes da subscrição chamando [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get).</span><span class="sxs-lookup"><span data-stu-id="4a5a3-131">Use that [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) to retrieve the subscription details by calling [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get).</span></span> <span data-ttu-id="4a5a3-132">Os detalhes da subscrição contêm o ID de encomenda da ordem de subscrição, que é a ordem a ser atualizada com o addon.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-132">The subscription details contain the order ID of the subscription order, which is the order to be updated with the add-on.</span></span>

<span data-ttu-id="4a5a3-133">Em seguida, instantânea um novo objeto [**de Encomenda**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) e povoa-o com uma única instância [**LineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) que contém a informação para identificar o addon, como mostrado no seguinte corte de código.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-133">Next, instantiate a new [**Order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object and populate it with a single [**LineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) instance that contains the information to identify the add-on, as shown in the following code snippet.</span></span> <span data-ttu-id="4a5a3-134">Utilizará este novo objeto para atualizar a ordem de subscrição com o addon.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-134">You'll use this new object to update the subscription order with the add-on.</span></span> <span data-ttu-id="4a5a3-135">Por fim, ligue para o método [**Patch**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.patch) para atualizar a ordem de subscrição, depois de primeiro identificar o cliente com [**iAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) e a encomenda com [**Encomendas.ById**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid).</span><span class="sxs-lookup"><span data-stu-id="4a5a3-135">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.patch) method to update the subscription order, after first identifying the customer with [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) and the order with [**Orders.ById**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;
// string addOnOfferId;

// Get an interface to the operations for the subscription.
var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);

// Get the parent subscription details.
var parentSubscription = subscriptionOperations.Get();

// In order to buy an add-on subscription for this offer, we need to patch/update the order through which the base offer was purchased
// by creating an order object with a single line item which represents the add-on offer purchase.
var orderToUpdate = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            LineItemNumber = 0,
            OfferId = addOnOfferId,
            FriendlyName = "Some friendly name",
            Quantity = 2,
            ParentSubscriptionId = subscriptionId
        }
    }
};

// Update the order to apply the add on purchase.
Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
```

<span data-ttu-id="4a5a3-136">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="4a5a3-136">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="4a5a3-137">**Project**: Partner Center SDK Samples **Class**: AddSubscriptionAddOn.cs</span><span class="sxs-lookup"><span data-stu-id="4a5a3-137">**Project**: Partner Center SDK Samples **Class**: AddSubscriptionAddOn.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="4a5a3-138">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="4a5a3-138">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4a5a3-139">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a5a3-139">Request syntax</span></span>

| <span data-ttu-id="4a5a3-140">Método</span><span class="sxs-lookup"><span data-stu-id="4a5a3-140">Method</span></span>    | <span data-ttu-id="4a5a3-141">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="4a5a3-141">Request URI</span></span>                                                                                              |
|-----------|----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4a5a3-142">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="4a5a3-142">**PATCH**</span></span> | <span data-ttu-id="4a5a3-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/orders/{order-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4a5a3-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="4a5a3-144">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="4a5a3-144">URI parameters</span></span>

<span data-ttu-id="4a5a3-145">Utilize os seguintes parâmetros para identificar o cliente e encomendar.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-145">Use the following parameters to identify the customer and order.</span></span>

| <span data-ttu-id="4a5a3-146">Nome</span><span class="sxs-lookup"><span data-stu-id="4a5a3-146">Name</span></span>                   | <span data-ttu-id="4a5a3-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="4a5a3-147">Type</span></span>     | <span data-ttu-id="4a5a3-148">Necessário</span><span class="sxs-lookup"><span data-stu-id="4a5a3-148">Required</span></span> | <span data-ttu-id="4a5a3-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a5a3-149">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="4a5a3-150">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="4a5a3-150">**customer-tenant-id**</span></span> | <span data-ttu-id="4a5a3-151">**guid**</span><span class="sxs-lookup"><span data-stu-id="4a5a3-151">**guid**</span></span> | <span data-ttu-id="4a5a3-152">Y</span><span class="sxs-lookup"><span data-stu-id="4a5a3-152">Y</span></span>        | <span data-ttu-id="4a5a3-153">O valor é um **design de cliente-inquilino-inquilino** formatado guid que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-153">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |
| <span data-ttu-id="4a5a3-154">**ordem id**</span><span class="sxs-lookup"><span data-stu-id="4a5a3-154">**order-id**</span></span>           | <span data-ttu-id="4a5a3-155">**guid**</span><span class="sxs-lookup"><span data-stu-id="4a5a3-155">**guid**</span></span> | <span data-ttu-id="4a5a3-156">Y</span><span class="sxs-lookup"><span data-stu-id="4a5a3-156">Y</span></span>        | <span data-ttu-id="4a5a3-157">O identificador da ordem.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-157">The order identifier.</span></span>                                                              |

### <a name="request-headers"></a><span data-ttu-id="4a5a3-158">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="4a5a3-158">Request headers</span></span>

<span data-ttu-id="4a5a3-159">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4a5a3-159">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4a5a3-160">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="4a5a3-160">Request body</span></span>

<span data-ttu-id="4a5a3-161">As tabelas seguintes descrevem as propriedades no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-161">The following tables describe the properties in the request body.</span></span>

## <a name="order"></a><span data-ttu-id="4a5a3-162">Encomenda</span><span class="sxs-lookup"><span data-stu-id="4a5a3-162">Order</span></span>

| <span data-ttu-id="4a5a3-163">Nome</span><span class="sxs-lookup"><span data-stu-id="4a5a3-163">Name</span></span>                | <span data-ttu-id="4a5a3-164">Tipo</span><span class="sxs-lookup"><span data-stu-id="4a5a3-164">Type</span></span>             | <span data-ttu-id="4a5a3-165">Necessário</span><span class="sxs-lookup"><span data-stu-id="4a5a3-165">Required</span></span> | <span data-ttu-id="4a5a3-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a5a3-166">Description</span></span>                                          |
|---------------------|------------------|----------|------------------------------------------------------|
| <span data-ttu-id="4a5a3-167">Id</span><span class="sxs-lookup"><span data-stu-id="4a5a3-167">Id</span></span>                  | <span data-ttu-id="4a5a3-168">string</span><span class="sxs-lookup"><span data-stu-id="4a5a3-168">string</span></span>           | <span data-ttu-id="4a5a3-169">N</span><span class="sxs-lookup"><span data-stu-id="4a5a3-169">N</span></span>        | <span data-ttu-id="4a5a3-170">A identificação da ordem.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-170">The order ID.</span></span>                                        |
| <span data-ttu-id="4a5a3-171">ReferênciaStotomerIda</span><span class="sxs-lookup"><span data-stu-id="4a5a3-171">ReferenceCustomerId</span></span> | <span data-ttu-id="4a5a3-172">string</span><span class="sxs-lookup"><span data-stu-id="4a5a3-172">string</span></span>           | <span data-ttu-id="4a5a3-173">Y</span><span class="sxs-lookup"><span data-stu-id="4a5a3-173">Y</span></span>        | <span data-ttu-id="4a5a3-174">A identificação do cliente.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-174">The customer ID.</span></span>                                     |
| <span data-ttu-id="4a5a3-175">LineItems</span><span class="sxs-lookup"><span data-stu-id="4a5a3-175">LineItems</span></span>           | <span data-ttu-id="4a5a3-176">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="4a5a3-176">array of objects</span></span> | <span data-ttu-id="4a5a3-177">Y</span><span class="sxs-lookup"><span data-stu-id="4a5a3-177">Y</span></span>        | <span data-ttu-id="4a5a3-178">Uma variedade de objetos [OrderLineItem.](#orderlineitem)</span><span class="sxs-lookup"><span data-stu-id="4a5a3-178">An array of [OrderLineItem](#orderlineitem) objects.</span></span> |
| <span data-ttu-id="4a5a3-179">Encontro de Criação</span><span class="sxs-lookup"><span data-stu-id="4a5a3-179">CreationDate</span></span>        | <span data-ttu-id="4a5a3-180">string</span><span class="sxs-lookup"><span data-stu-id="4a5a3-180">string</span></span>           | <span data-ttu-id="4a5a3-181">N</span><span class="sxs-lookup"><span data-stu-id="4a5a3-181">N</span></span>        | <span data-ttu-id="4a5a3-182">A data em que a encomenda foi criada, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-182">The date the order was created, in date-time format.</span></span> |
| <span data-ttu-id="4a5a3-183">Atributos</span><span class="sxs-lookup"><span data-stu-id="4a5a3-183">Attributes</span></span>          | <span data-ttu-id="4a5a3-184">objeto</span><span class="sxs-lookup"><span data-stu-id="4a5a3-184">object</span></span>           | <span data-ttu-id="4a5a3-185">N</span><span class="sxs-lookup"><span data-stu-id="4a5a3-185">N</span></span>        | <span data-ttu-id="4a5a3-186">Contém "ObjectType": "Order".</span><span class="sxs-lookup"><span data-stu-id="4a5a3-186">Contains "ObjectType": "Order".</span></span>                      |

## <a name="orderlineitem"></a><span data-ttu-id="4a5a3-187">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="4a5a3-187">OrderLineItem</span></span>

| <span data-ttu-id="4a5a3-188">Nome</span><span class="sxs-lookup"><span data-stu-id="4a5a3-188">Name</span></span>                 | <span data-ttu-id="4a5a3-189">Tipo</span><span class="sxs-lookup"><span data-stu-id="4a5a3-189">Type</span></span>   | <span data-ttu-id="4a5a3-190">Necessário</span><span class="sxs-lookup"><span data-stu-id="4a5a3-190">Required</span></span> | <span data-ttu-id="4a5a3-191">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a5a3-191">Description</span></span>                                                  |
|----------------------|--------|----------|--------------------------------------------------------------|
| <span data-ttu-id="4a5a3-192">LineItemNumber</span><span class="sxs-lookup"><span data-stu-id="4a5a3-192">LineItemNumber</span></span>       | <span data-ttu-id="4a5a3-193">número</span><span class="sxs-lookup"><span data-stu-id="4a5a3-193">number</span></span> | <span data-ttu-id="4a5a3-194">Y</span><span class="sxs-lookup"><span data-stu-id="4a5a3-194">Y</span></span>        | <span data-ttu-id="4a5a3-195">O número do item da linha, a começar por 0.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-195">The line item number, starting with 0.</span></span>                       |
| <span data-ttu-id="4a5a3-196">OfferId</span><span class="sxs-lookup"><span data-stu-id="4a5a3-196">OfferId</span></span>              | <span data-ttu-id="4a5a3-197">string</span><span class="sxs-lookup"><span data-stu-id="4a5a3-197">string</span></span> | <span data-ttu-id="4a5a3-198">Y</span><span class="sxs-lookup"><span data-stu-id="4a5a3-198">Y</span></span>        | <span data-ttu-id="4a5a3-199">A identificação da oferta do add-on.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-199">The offer ID of the add-on.</span></span>                                  |
| <span data-ttu-id="4a5a3-200">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="4a5a3-200">SubscriptionId</span></span>       | <span data-ttu-id="4a5a3-201">string</span><span class="sxs-lookup"><span data-stu-id="4a5a3-201">string</span></span> | <span data-ttu-id="4a5a3-202">N</span><span class="sxs-lookup"><span data-stu-id="4a5a3-202">N</span></span>        | <span data-ttu-id="4a5a3-203">O ID da subscrição adicionada adquirida.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-203">The ID of the add-on subscription purchased.</span></span>                 |
| <span data-ttu-id="4a5a3-204">ParentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="4a5a3-204">ParentSubscriptionId</span></span> | <span data-ttu-id="4a5a3-205">string</span><span class="sxs-lookup"><span data-stu-id="4a5a3-205">string</span></span> | <span data-ttu-id="4a5a3-206">Y</span><span class="sxs-lookup"><span data-stu-id="4a5a3-206">Y</span></span>        | <span data-ttu-id="4a5a3-207">O ID da subscrição dos pais que tem a oferta de complemento.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-207">The ID of the parent subscription that has the add-on offer.</span></span> |
| <span data-ttu-id="4a5a3-208">FriendlyName</span><span class="sxs-lookup"><span data-stu-id="4a5a3-208">FriendlyName</span></span>         | <span data-ttu-id="4a5a3-209">string</span><span class="sxs-lookup"><span data-stu-id="4a5a3-209">string</span></span> | <span data-ttu-id="4a5a3-210">N</span><span class="sxs-lookup"><span data-stu-id="4a5a3-210">N</span></span>        | <span data-ttu-id="4a5a3-211">O nome amigável para este item de linha.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-211">The friendly name for this line item.</span></span>                        |
| <span data-ttu-id="4a5a3-212">Quantidade</span><span class="sxs-lookup"><span data-stu-id="4a5a3-212">Quantity</span></span>             | <span data-ttu-id="4a5a3-213">número</span><span class="sxs-lookup"><span data-stu-id="4a5a3-213">number</span></span> | <span data-ttu-id="4a5a3-214">Y</span><span class="sxs-lookup"><span data-stu-id="4a5a3-214">Y</span></span>        | <span data-ttu-id="4a5a3-215">O número de licenças.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-215">The number of licenses.</span></span>                                      |
| <span data-ttu-id="4a5a3-216">PartnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="4a5a3-216">PartnerIdOnRecord</span></span>    | <span data-ttu-id="4a5a3-217">string</span><span class="sxs-lookup"><span data-stu-id="4a5a3-217">string</span></span> | <span data-ttu-id="4a5a3-218">N</span><span class="sxs-lookup"><span data-stu-id="4a5a3-218">N</span></span>        | <span data-ttu-id="4a5a3-219">A identificação da MPN do sócio do registo.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-219">The MPN ID of the partner of record.</span></span>                         |
| <span data-ttu-id="4a5a3-220">Atributos</span><span class="sxs-lookup"><span data-stu-id="4a5a3-220">Attributes</span></span>           | <span data-ttu-id="4a5a3-221">objeto</span><span class="sxs-lookup"><span data-stu-id="4a5a3-221">object</span></span> | <span data-ttu-id="4a5a3-222">N</span><span class="sxs-lookup"><span data-stu-id="4a5a3-222">N</span></span>        | <span data-ttu-id="4a5a3-223">Contém "ObjectType": "OrderLineItem".</span><span class="sxs-lookup"><span data-stu-id="4a5a3-223">Contains "ObjectType": "OrderLineItem".</span></span>                      |

### <a name="request-example"></a><span data-ttu-id="4a5a3-224">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="4a5a3-224">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/orders/CF3B0E37-BE0B-4CDD-B584-D1A97D98A922 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 17a2658e-d2cc-439b-a2f0-2aefd9344fbc
MS-CorrelationId: 60efdd24-17ef-4080-9b02-4fc315f916ff
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 414
Expect: 100-continue

{
    "Id": null,
    "ReferenceCustomerId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "SubscriptionId": null,
            "ParentSubscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
            "FriendlyName": "Some friendly name",
            "Quantity": 2,
            "PartnerIdOnRecord": null,
            "Attributes": {
                "ObjectType": "OrderLineItem"
            }
        }
    ],
    "CreationDate": null,
    "Attributes": {
        "ObjectType": "Order"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="4a5a3-225">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="4a5a3-225">REST response</span></span>

<span data-ttu-id="4a5a3-226">Se for bem sucedido, este método devolve a ordem de subscrição atualizada no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-226">If successful, this method returns the updated subscription order in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4a5a3-227">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="4a5a3-227">Response success and error codes</span></span>

<span data-ttu-id="4a5a3-228">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-228">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4a5a3-229">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4a5a3-229">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4a5a3-230">Para obter a lista completa, consulte [os Códigos de Erro do Centro de Parceiros](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4a5a3-230">For the full list, see [Partner Center Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4a5a3-231">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="4a5a3-231">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1135
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 60efdd24-17ef-4080-9b02-4fc315f916ff
MS-RequestId: 17a2658e-d2cc-439b-a2f0-2aefd9344fbc
MS-CV: WtFy3zI8V0u2lnT9.0
MS-ServerId: 020021921
Date: Wed, 25 Jan 2017 23:01:08 GMT

{
    "id": "cf3b0e37-be0b-4cdd-b584-d1a97d98a922",
    "referenceCustomerId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "billingCycle": "none",
    "lineItems": [{
            "lineItemNumber": 0,
            "offerId": "195416C1-3447-423A-B37B-EE59A99A19C4",
            "subscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
            "friendlyName": "new offer purchase",
            "quantity": 5,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
                    "method": "GET",
                    "headers": []
                }
            }
        }, {
            "lineItemNumber": 1,
            "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "subscriptionId": "968BA1CF-C146-4ADF-A300-308DCF718EEE",
            "friendlyName": "Some friendly name",
            "quantity": 2,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/968BA1CF-C146-4ADF-A300-308DCF718EEE",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2017-01-25T14:53:12.093-08:00",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/orders/cf3b0e37-be0b-4cdd-b584-d1a97d98a922",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "eyJpZCI6ImNmM2IwZTM3LWJlMGItNGNkZC1iNTg0LWQxYTk3ZDk4YTkyMiIsInZlcnNpb24iOjJ9",
        "objectType": "Order"
    }
}
```
