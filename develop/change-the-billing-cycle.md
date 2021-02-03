---
title: Alterar o ciclo de faturação
description: Saiba como atualizar uma subscrição de um cliente à faturação mensal ou anual usando APIs do Partner Center. Também pode fazê-lo a partir do painel partner Center.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 8a2879db061ced799e29d84e71be5b1259b07689
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770088"
---
# <a name="change-a-customer-subscription-billing-cycle"></a><span data-ttu-id="4f6eb-104">Alterar um ciclo de faturação de subscrição de clientes</span><span class="sxs-lookup"><span data-stu-id="4f6eb-104">Change a customer subscription billing cycle</span></span>

<span data-ttu-id="4f6eb-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="4f6eb-105">**Applies to:**</span></span>

- <span data-ttu-id="4f6eb-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="4f6eb-106">Partner Center</span></span>
- <span data-ttu-id="4f6eb-107">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="4f6eb-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="4f6eb-108">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="4f6eb-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="4f6eb-109">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4f6eb-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4f6eb-110">Atualiza uma [Encomenda](order-resources.md) de faturação mensal a anual ou de faturação anual a mensal.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-110">Updates an [Order](order-resources.md) from monthly to annual billing or from annual to monthly billing.</span></span>

<span data-ttu-id="4f6eb-111">No painel de instrumentos partner Center, esta operação pode ser realizada navegando para a página de detalhes de subscrição de um cliente.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-111">In the Partner Center dashboard, this operation can be performed by navigating to a customer's subscription details page.</span></span> <span data-ttu-id="4f6eb-112">Uma vez lá, verá uma opção que define o ciclo de faturação atual para a subscrição com a capacidade de alterá-la e submetê-la.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-112">Once there, you will see an option defining the current billing cycle for the subscription with the ability to change and submit it.</span></span>

<span data-ttu-id="4f6eb-113">**Fora do âmbito** deste artigo:</span><span class="sxs-lookup"><span data-stu-id="4f6eb-113">**Out of scope** for this article:</span></span>

- <span data-ttu-id="4f6eb-114">Alteração do ciclo de faturação para ensaios</span><span class="sxs-lookup"><span data-stu-id="4f6eb-114">Changing the billing cycle for trials</span></span>
- <span data-ttu-id="4f6eb-115">Alteração dos ciclos de faturação para quaisquer ofertas não anuais (mensalmente, 6 anos) & assinaturas Azure</span><span class="sxs-lookup"><span data-stu-id="4f6eb-115">Changing the billing cycles for any non-annual term offers (monthly, 6-year) & Azure subscriptions</span></span>
- <span data-ttu-id="4f6eb-116">Alteração dos ciclos de faturação para subscrições inativas</span><span class="sxs-lookup"><span data-stu-id="4f6eb-116">Changing the billing cycles for inactive subscriptions</span></span>
- <span data-ttu-id="4f6eb-117">Alteração dos ciclos de faturação para subscrições baseadas em licenças de serviços online da Microsoft</span><span class="sxs-lookup"><span data-stu-id="4f6eb-117">Changing billing cycles for Microsoft online services license-based subscriptions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4f6eb-118">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4f6eb-118">Prerequisites</span></span>

- <span data-ttu-id="4f6eb-119">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4f6eb-119">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4f6eb-120">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-120">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="4f6eb-121">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4f6eb-121">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4f6eb-122">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-122">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4f6eb-123">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-123">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4f6eb-124">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="4f6eb-124">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4f6eb-125">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="4f6eb-125">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4f6eb-126">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4f6eb-126">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="4f6eb-127">Uma identificação de encomenda.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-127">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="4f6eb-128">C\#</span><span class="sxs-lookup"><span data-stu-id="4f6eb-128">C\#</span></span>

<span data-ttu-id="4f6eb-129">Para alterar a frequência do ciclo de faturação, atualize a propriedade [**Order.BillingCycle.**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.billingcycle#Microsoft_Store_PartnerCenter_Models_Orders_Order_BillingCycle)</span><span class="sxs-lookup"><span data-stu-id="4f6eb-129">To change the frequency of the billing cycle, update the [**Order.BillingCycle**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.billingcycle#Microsoft_Store_PartnerCenter_Models_Orders_Order_BillingCycle) property.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string offerId;
// string orderId;

var order = new Order()
{
    ReferenceCustomerId = customerId,
    BillingCycle = BillingCycleType.Annual,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            LineItemNumber = 0,
            OfferId = offerId,
            SubscriptionId = "69829602-C219-40FD-A3D5-4150FCA41A19",
            Quantity = 1
        }
    }
};

var createdOrder = partnerOperations.Customers.ById(customerId).Orders.ById(orderId).Patch(order);
```

## <a name="rest-request"></a><span data-ttu-id="4f6eb-130">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="4f6eb-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4f6eb-131">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f6eb-131">Request syntax</span></span>

| <span data-ttu-id="4f6eb-132">Método</span><span class="sxs-lookup"><span data-stu-id="4f6eb-132">Method</span></span>    | <span data-ttu-id="4f6eb-133">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="4f6eb-133">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4f6eb-134">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="4f6eb-134">**PATCH**</span></span> | <span data-ttu-id="4f6eb-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/orders/{order-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4f6eb-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="4f6eb-136">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="4f6eb-136">URI parameter</span></span>

<span data-ttu-id="4f6eb-137">Esta tabela lista o parâmetro de consulta necessário para alterar a quantidade da subscrição.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-137">This table lists the required query parameter to change the quantity of the subscription.</span></span>

| <span data-ttu-id="4f6eb-138">Nome</span><span class="sxs-lookup"><span data-stu-id="4f6eb-138">Name</span></span>                   | <span data-ttu-id="4f6eb-139">Tipo</span><span class="sxs-lookup"><span data-stu-id="4f6eb-139">Type</span></span> | <span data-ttu-id="4f6eb-140">Necessário</span><span class="sxs-lookup"><span data-stu-id="4f6eb-140">Required</span></span> | <span data-ttu-id="4f6eb-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f6eb-141">Description</span></span>                                                          |
|------------------------|------|----------|----------------------------------------------------------------------|
| <span data-ttu-id="4f6eb-142">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="4f6eb-142">**customer-tenant-id**</span></span> | <span data-ttu-id="4f6eb-143">GUID</span><span class="sxs-lookup"><span data-stu-id="4f6eb-143">GUID</span></span> |    <span data-ttu-id="4f6eb-144">Y</span><span class="sxs-lookup"><span data-stu-id="4f6eb-144">Y</span></span>     | <span data-ttu-id="4f6eb-145">Um design **de cliente-inquilino-cliente-inativação** que identifica o cliente</span><span class="sxs-lookup"><span data-stu-id="4f6eb-145">A GUID formatted **customer-tenant-id** that identifies the customer</span></span> |
| <span data-ttu-id="4f6eb-146">**ordem id**</span><span class="sxs-lookup"><span data-stu-id="4f6eb-146">**order-id**</span></span>           | <span data-ttu-id="4f6eb-147">GUID</span><span class="sxs-lookup"><span data-stu-id="4f6eb-147">GUID</span></span> |    <span data-ttu-id="4f6eb-148">Y</span><span class="sxs-lookup"><span data-stu-id="4f6eb-148">Y</span></span>     | <span data-ttu-id="4f6eb-149">O identificador de ordem</span><span class="sxs-lookup"><span data-stu-id="4f6eb-149">The order identifier</span></span>                                                 |

### <a name="request-headers"></a><span data-ttu-id="4f6eb-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="4f6eb-150">Request headers</span></span>

<span data-ttu-id="4f6eb-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4f6eb-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4f6eb-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="4f6eb-152">Request body</span></span>

<span data-ttu-id="4f6eb-153">As tabelas seguintes descrevem as propriedades no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-153">The following tables describe the properties in the request body.</span></span>

### <a name="order"></a><span data-ttu-id="4f6eb-154">Encomenda</span><span class="sxs-lookup"><span data-stu-id="4f6eb-154">Order</span></span>

| <span data-ttu-id="4f6eb-155">Propriedade</span><span class="sxs-lookup"><span data-stu-id="4f6eb-155">Property</span></span>           | <span data-ttu-id="4f6eb-156">Tipo</span><span class="sxs-lookup"><span data-stu-id="4f6eb-156">Type</span></span>             | <span data-ttu-id="4f6eb-157">Necessário</span><span class="sxs-lookup"><span data-stu-id="4f6eb-157">Required</span></span> | <span data-ttu-id="4f6eb-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f6eb-158">Description</span></span>                                                                |
|--------------------|------------------|----------|----------------------------------------------------------------------------|
| <span data-ttu-id="4f6eb-159">Id</span><span class="sxs-lookup"><span data-stu-id="4f6eb-159">Id</span></span>                 | <span data-ttu-id="4f6eb-160">string</span><span class="sxs-lookup"><span data-stu-id="4f6eb-160">string</span></span>           |    <span data-ttu-id="4f6eb-161">N</span><span class="sxs-lookup"><span data-stu-id="4f6eb-161">N</span></span>     | <span data-ttu-id="4f6eb-162">Um identificador de ordem que é fornecido após a criação bem sucedida da ordem</span><span class="sxs-lookup"><span data-stu-id="4f6eb-162">An order identifier that is supplied upon successful creation of the order</span></span> |
|<span data-ttu-id="4f6eb-163">ReferênciaStotomerIda</span><span class="sxs-lookup"><span data-stu-id="4f6eb-163">ReferenceCustomerId</span></span> | <span data-ttu-id="4f6eb-164">string</span><span class="sxs-lookup"><span data-stu-id="4f6eb-164">string</span></span>           |    <span data-ttu-id="4f6eb-165">Y</span><span class="sxs-lookup"><span data-stu-id="4f6eb-165">Y</span></span>     | <span data-ttu-id="4f6eb-166">O identificador de clientes</span><span class="sxs-lookup"><span data-stu-id="4f6eb-166">The customer identifier</span></span>                                                    |
| <span data-ttu-id="4f6eb-167">BillingCycle</span><span class="sxs-lookup"><span data-stu-id="4f6eb-167">BillingCycle</span></span>       | <span data-ttu-id="4f6eb-168">string</span><span class="sxs-lookup"><span data-stu-id="4f6eb-168">string</span></span>           |    <span data-ttu-id="4f6eb-169">Y</span><span class="sxs-lookup"><span data-stu-id="4f6eb-169">Y</span></span>     | <span data-ttu-id="4f6eb-170">Indica a frequência com que o parceiro é faturado para esta encomenda.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-170">Indicates the frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="4f6eb-171">Os valores suportados são os nomes dos membros encontrados no [BillingCycleType](product-resources.md#billingcycletype).</span><span class="sxs-lookup"><span data-stu-id="4f6eb-171">Supported values are the member names found in [BillingCycleType](product-resources.md#billingcycletype).</span></span> |
| <span data-ttu-id="4f6eb-172">LineItems</span><span class="sxs-lookup"><span data-stu-id="4f6eb-172">LineItems</span></span>          | <span data-ttu-id="4f6eb-173">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="4f6eb-173">array of objects</span></span> |    <span data-ttu-id="4f6eb-174">Y</span><span class="sxs-lookup"><span data-stu-id="4f6eb-174">Y</span></span>     | <span data-ttu-id="4f6eb-175">Uma variedade de recursos [OrderLineItem](#orderlineitem)</span><span class="sxs-lookup"><span data-stu-id="4f6eb-175">An array of [OrderLineItem](#orderlineitem) resources</span></span>                      |
| <span data-ttu-id="4f6eb-176">Encontro de Criação</span><span class="sxs-lookup"><span data-stu-id="4f6eb-176">CreationDate</span></span>       | <span data-ttu-id="4f6eb-177">datetime</span><span class="sxs-lookup"><span data-stu-id="4f6eb-177">datetime</span></span>         |    <span data-ttu-id="4f6eb-178">N</span><span class="sxs-lookup"><span data-stu-id="4f6eb-178">N</span></span>     | <span data-ttu-id="4f6eb-179">A data em que a encomenda foi criada, em formato de data-hora</span><span class="sxs-lookup"><span data-stu-id="4f6eb-179">The date the order was created, in date-time format</span></span>                        |
| <span data-ttu-id="4f6eb-180">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f6eb-180">Attributes</span></span>         | <span data-ttu-id="4f6eb-181">Objeto</span><span class="sxs-lookup"><span data-stu-id="4f6eb-181">Object</span></span>           |    <span data-ttu-id="4f6eb-182">N</span><span class="sxs-lookup"><span data-stu-id="4f6eb-182">N</span></span>     | <span data-ttu-id="4f6eb-183">Contém "ObjectType": "OrderLineItem"</span><span class="sxs-lookup"><span data-stu-id="4f6eb-183">Contains "ObjectType": "OrderLineItem"</span></span>                                     |

### <a name="orderlineitem"></a><span data-ttu-id="4f6eb-184">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="4f6eb-184">OrderLineItem</span></span>

| <span data-ttu-id="4f6eb-185">Propriedade</span><span class="sxs-lookup"><span data-stu-id="4f6eb-185">Property</span></span>             | <span data-ttu-id="4f6eb-186">Tipo</span><span class="sxs-lookup"><span data-stu-id="4f6eb-186">Type</span></span>   | <span data-ttu-id="4f6eb-187">Necessário</span><span class="sxs-lookup"><span data-stu-id="4f6eb-187">Required</span></span> | <span data-ttu-id="4f6eb-188">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f6eb-188">Description</span></span>                                                                        |
|----------------------|--------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="4f6eb-189">LineItemNumber</span><span class="sxs-lookup"><span data-stu-id="4f6eb-189">LineItemNumber</span></span>       | <span data-ttu-id="4f6eb-190">número</span><span class="sxs-lookup"><span data-stu-id="4f6eb-190">number</span></span> |    <span data-ttu-id="4f6eb-191">Y</span><span class="sxs-lookup"><span data-stu-id="4f6eb-191">Y</span></span>     | <span data-ttu-id="4f6eb-192">O número do item da linha, começando com 0</span><span class="sxs-lookup"><span data-stu-id="4f6eb-192">The line item number, starting with 0</span></span>                                              |
| <span data-ttu-id="4f6eb-193">OfferId</span><span class="sxs-lookup"><span data-stu-id="4f6eb-193">OfferId</span></span>              | <span data-ttu-id="4f6eb-194">string</span><span class="sxs-lookup"><span data-stu-id="4f6eb-194">string</span></span> |    <span data-ttu-id="4f6eb-195">Y</span><span class="sxs-lookup"><span data-stu-id="4f6eb-195">Y</span></span>     | <span data-ttu-id="4f6eb-196">O ID da oferta</span><span class="sxs-lookup"><span data-stu-id="4f6eb-196">The ID of the offer</span></span>                                                                |
| <span data-ttu-id="4f6eb-197">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="4f6eb-197">SubscriptionId</span></span>       | <span data-ttu-id="4f6eb-198">string</span><span class="sxs-lookup"><span data-stu-id="4f6eb-198">string</span></span> |    <span data-ttu-id="4f6eb-199">Y</span><span class="sxs-lookup"><span data-stu-id="4f6eb-199">Y</span></span>     | <span data-ttu-id="4f6eb-200">O ID da subscrição</span><span class="sxs-lookup"><span data-stu-id="4f6eb-200">The ID of the subscription</span></span>                                                         |
| <span data-ttu-id="4f6eb-201">FriendlyName</span><span class="sxs-lookup"><span data-stu-id="4f6eb-201">FriendlyName</span></span>         | <span data-ttu-id="4f6eb-202">string</span><span class="sxs-lookup"><span data-stu-id="4f6eb-202">string</span></span> |    <span data-ttu-id="4f6eb-203">N</span><span class="sxs-lookup"><span data-stu-id="4f6eb-203">N</span></span>     | <span data-ttu-id="4f6eb-204">O nome amigável para a subscrição definida pelo parceiro para ajudar a desambiguar</span><span class="sxs-lookup"><span data-stu-id="4f6eb-204">The friendly name for the subscription defined by the partner to help disambiguate</span></span> |
| <span data-ttu-id="4f6eb-205">Quantidade</span><span class="sxs-lookup"><span data-stu-id="4f6eb-205">Quantity</span></span>             | <span data-ttu-id="4f6eb-206">número</span><span class="sxs-lookup"><span data-stu-id="4f6eb-206">number</span></span> |    <span data-ttu-id="4f6eb-207">Y</span><span class="sxs-lookup"><span data-stu-id="4f6eb-207">Y</span></span>     | <span data-ttu-id="4f6eb-208">O número de licenças ou instâncias</span><span class="sxs-lookup"><span data-stu-id="4f6eb-208">The number of licenses or instances</span></span>                                                |
| <span data-ttu-id="4f6eb-209">PartnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="4f6eb-209">PartnerIdOnRecord</span></span>    | <span data-ttu-id="4f6eb-210">string</span><span class="sxs-lookup"><span data-stu-id="4f6eb-210">string</span></span> |    <span data-ttu-id="4f6eb-211">N</span><span class="sxs-lookup"><span data-stu-id="4f6eb-211">N</span></span>     | <span data-ttu-id="4f6eb-212">A MPN ID do sócio do registo</span><span class="sxs-lookup"><span data-stu-id="4f6eb-212">The MPN ID of the partner of record</span></span>                                                |
| <span data-ttu-id="4f6eb-213">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f6eb-213">Attributes</span></span>           | <span data-ttu-id="4f6eb-214">Objeto</span><span class="sxs-lookup"><span data-stu-id="4f6eb-214">Object</span></span> |    <span data-ttu-id="4f6eb-215">N</span><span class="sxs-lookup"><span data-stu-id="4f6eb-215">N</span></span>     | <span data-ttu-id="4f6eb-216">Contém "ObjectType": "OrderLineItem"</span><span class="sxs-lookup"><span data-stu-id="4f6eb-216">Contains "ObjectType": "OrderLineItem"</span></span>                                             |

### <a name="request-example"></a><span data-ttu-id="4f6eb-217">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="4f6eb-217">Request example</span></span>

<span data-ttu-id="4f6eb-218">Atualização da faturação anual</span><span class="sxs-lookup"><span data-stu-id="4f6eb-218">Update to annual billing</span></span>

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
    "BillingCycle" : "Annual",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "SubscriptionId": "69829602-C219-40FD-A3D5-4150FCA41A19",
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

## <a name="rest-response"></a><span data-ttu-id="4f6eb-219">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="4f6eb-219">REST response</span></span>

<span data-ttu-id="4f6eb-220">Se for bem sucedido, este método devolve a ordem de subscrição atualizada no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-220">If successful, this method returns the updated subscription order in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4f6eb-221">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="4f6eb-221">Response success and error codes</span></span>

<span data-ttu-id="4f6eb-222">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-222">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4f6eb-223">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4f6eb-223">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4f6eb-224">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4f6eb-224">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4f6eb-225">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="4f6eb-225">Response example</span></span>

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
    "billingCycle": "Annual",
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
        },
        {
            "lineItemNumber": 1,
            "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "subscriptionId": "69829602-C219-40FD-A3D5-4150FCA41A19",
            "friendlyName": "Some friendly name",
            "quantity": 2,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/69829602-C219-40FD-A3D5-4150FCA41A19",
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