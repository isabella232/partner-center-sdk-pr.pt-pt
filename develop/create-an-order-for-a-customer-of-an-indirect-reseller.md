---
title: Criar pedido de cliente para revendedor indireto
description: Saiba como utilizar as APIs do Partner Center para criar uma encomenda para um cliente de um revendedor indireto. O artigo inclui pré-requisitos, passos e exemplos.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6253ba2289ea1f58e7d8eaa960d7d0daaa887f0d
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973553"
---
# <a name="create-an-order-for-a-customer-of-an-indirect-reseller"></a><span data-ttu-id="f7420-104">Criar uma encomenda para um cliente de um revendedor indireto</span><span class="sxs-lookup"><span data-stu-id="f7420-104">Create an order for a customer of an indirect reseller</span></span>

<span data-ttu-id="f7420-105">Como criar uma encomenda para um cliente de um revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="f7420-105">How to create an order for a customer of an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7420-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f7420-106">Prerequisites</span></span>

- <span data-ttu-id="f7420-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f7420-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f7420-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="f7420-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="f7420-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f7420-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f7420-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f7420-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f7420-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="f7420-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f7420-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="f7420-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f7420-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="f7420-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f7420-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f7420-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f7420-115">O identificador de oferta do item para comprar.</span><span class="sxs-lookup"><span data-stu-id="f7420-115">The offer identifier of the item to purchase.</span></span>

- <span data-ttu-id="f7420-116">O identificador do inquilino do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="f7420-116">The tenant identifier of the indirect reseller.</span></span>

## <a name="c"></a><span data-ttu-id="f7420-117">C\#</span><span class="sxs-lookup"><span data-stu-id="f7420-117">C\#</span></span>

<span data-ttu-id="f7420-118">Para criar uma encomenda para um cliente de um revendedor indireto:</span><span class="sxs-lookup"><span data-stu-id="f7420-118">To create an order for a customer of an indirect reseller:</span></span>

1. <span data-ttu-id="f7420-119">Obtenha uma coleção dos revendedores indiretos que têm uma relação com o parceiro inscrito.</span><span class="sxs-lookup"><span data-stu-id="f7420-119">Get a collection of the indirect resellers that have a relationship with the signed-in partner.</span></span>

2. <span data-ttu-id="f7420-120">Obtenha uma variável local para o item na coleção que corresponda ao ID do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="f7420-120">Get a local variable to the item in the collection that matches the indirect reseller ID.</span></span> <span data-ttu-id="f7420-121">Este passo ajuda-o a aceder à propriedade [**mpnId**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationship.mpnid) do revendedor quando cria a encomenda.</span><span class="sxs-lookup"><span data-stu-id="f7420-121">This step helps you access the reseller's [**MpnId**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationship.mpnid) property when you create the order.</span></span>

3. <span data-ttu-id="f7420-122">Instantiar um objeto [**de Encomenda**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) e definir a propriedade [**ReferenceCustomerID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.referencecustomerid) ao identificador do cliente de forma a registar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f7420-122">Instantiate an [**Order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object and set the [**ReferenceCustomerID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.referencecustomerid) property to the customer identifier in order to record the customer.</span></span>

4. <span data-ttu-id="f7420-123">Crie uma lista de objetos [**OrderLineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) e atribua a lista à propriedade [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.lineitems) da encomenda.</span><span class="sxs-lookup"><span data-stu-id="f7420-123">Create a list of [**OrderLineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) objects, and assign the list to the order's [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.lineitems) property.</span></span> <span data-ttu-id="f7420-124">Cada item da linha de encomenda contém a informação de compra para uma oferta.</span><span class="sxs-lookup"><span data-stu-id="f7420-124">Each order line item contains the purchase information for one offer.</span></span> <span data-ttu-id="f7420-125">Certifique-se de que preenche a propriedade [**PartnerIdOnRecord**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem.partneridonrecord) em cada item de linha com o ID MPN do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="f7420-125">Be sure to populate the [**PartnerIdOnRecord**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem.partneridonrecord) property in each line item with the MPN ID of the indirect reseller.</span></span> <span data-ttu-id="f7420-126">Deve ter pelo menos um item de linha de encomenda.</span><span class="sxs-lookup"><span data-stu-id="f7420-126">You must have at least one order line item.</span></span>

5. <span data-ttu-id="f7420-127">Obtenha uma interface para encomendar operações ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface a partir da propriedade [**Encomendas.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders)</span><span class="sxs-lookup"><span data-stu-id="f7420-127">Obtain an interface to order operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and then retrieve the interface from the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property.</span></span>

6. <span data-ttu-id="f7420-128">Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) ou [**Criar Aync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) para criar a ordem.</span><span class="sxs-lookup"><span data-stu-id="f7420-128">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) method to create the order.</span></span>

### <a name="c-example"></a><span data-ttu-id="f7420-129">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="f7420-129">C\# example</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string offerId;
// string indirectResellerId;

// Get the indirect resellers with a relationship to the signed-in partner.
var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);

// Find the matching reseller in the collection.
var selectedIndirectReseller = (indirectResellers != null && indirectResellers.Items.Any()) ?
    indirectResellers.Items.FirstOrDefault(reseller => reseller.Id.Equals(indirectResellerId, StringComparison.OrdinalIgnoreCase)) :
    null;

// Prepare the order and populate the PartnerIdOnRecord with the reseller&#39;s Microsoft Partner Network Id.
var order = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            OfferId = offerId,
            FriendlyName = "New offer purchase.",
            Quantity = 5,
            PartnerIdOnRecord = selectedIndirectReseller != null ? selectedIndirectReseller.MpnId : null
        }
    }
};

// Place the order.
var createdOrder = partnerOperations.Customers.ById(customerId).Orders.Create(order);
```

<span data-ttu-id="f7420-130">**Amostra**: [Aplicativo de teste de consola](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: PlaceOrderForCustomer.cs</span><span class="sxs-lookup"><span data-stu-id="f7420-130">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: PlaceOrderForCustomer.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="f7420-131">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f7420-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f7420-132">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7420-132">Request syntax</span></span>

| <span data-ttu-id="f7420-133">Método</span><span class="sxs-lookup"><span data-stu-id="f7420-133">Method</span></span>   | <span data-ttu-id="f7420-134">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f7420-134">Request URI</span></span>                                                                            |
|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="f7420-135">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="f7420-135">**POST**</span></span> | <span data-ttu-id="f7420-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/encomendas HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f7420-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="f7420-137">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="f7420-137">URI parameters</span></span>

<span data-ttu-id="f7420-138">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f7420-138">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="f7420-139">Nome</span><span class="sxs-lookup"><span data-stu-id="f7420-139">Name</span></span>        | <span data-ttu-id="f7420-140">Tipo</span><span class="sxs-lookup"><span data-stu-id="f7420-140">Type</span></span>   | <span data-ttu-id="f7420-141">Necessário</span><span class="sxs-lookup"><span data-stu-id="f7420-141">Required</span></span> | <span data-ttu-id="f7420-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7420-142">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="f7420-143">id cliente</span><span class="sxs-lookup"><span data-stu-id="f7420-143">customer-id</span></span> | <span data-ttu-id="f7420-144">string</span><span class="sxs-lookup"><span data-stu-id="f7420-144">string</span></span> | <span data-ttu-id="f7420-145">Yes</span><span class="sxs-lookup"><span data-stu-id="f7420-145">Yes</span></span>      | <span data-ttu-id="f7420-146">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="f7420-146">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f7420-147">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="f7420-147">Request headers</span></span>

<span data-ttu-id="f7420-148">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f7420-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f7420-149">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f7420-149">Request body</span></span>

#### <a name="order"></a><span data-ttu-id="f7420-150">Encomenda</span><span class="sxs-lookup"><span data-stu-id="f7420-150">Order</span></span>

<span data-ttu-id="f7420-151">Esta tabela descreve as propriedades da **Ordem** no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="f7420-151">This table describes the **Order** properties in the request body.</span></span>

| <span data-ttu-id="f7420-152">Nome</span><span class="sxs-lookup"><span data-stu-id="f7420-152">Name</span></span> | <span data-ttu-id="f7420-153">Tipo</span><span class="sxs-lookup"><span data-stu-id="f7420-153">Type</span></span> | <span data-ttu-id="f7420-154">Necessário</span><span class="sxs-lookup"><span data-stu-id="f7420-154">Required</span></span> | <span data-ttu-id="f7420-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7420-155">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="f7420-156">ID</span><span class="sxs-lookup"><span data-stu-id="f7420-156">id</span></span> | <span data-ttu-id="f7420-157">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="f7420-157">string</span></span> | <span data-ttu-id="f7420-158">No</span><span class="sxs-lookup"><span data-stu-id="f7420-158">No</span></span> | <span data-ttu-id="f7420-159">Um identificador de ordem que é fornecido após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="f7420-159">An order identifier that is supplied upon successful creation of the order.</span></span> |
| <span data-ttu-id="f7420-160">referênciaStomerId</span><span class="sxs-lookup"><span data-stu-id="f7420-160">referenceCustomerId</span></span> | <span data-ttu-id="f7420-161">string</span><span class="sxs-lookup"><span data-stu-id="f7420-161">string</span></span> | <span data-ttu-id="f7420-162">Yes</span><span class="sxs-lookup"><span data-stu-id="f7420-162">Yes</span></span> | <span data-ttu-id="f7420-163">O identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="f7420-163">The customer identifier.</span></span> |
| <span data-ttu-id="f7420-164">billingCycle</span><span class="sxs-lookup"><span data-stu-id="f7420-164">billingCycle</span></span> | <span data-ttu-id="f7420-165">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="f7420-165">string</span></span> | <span data-ttu-id="f7420-166">No</span><span class="sxs-lookup"><span data-stu-id="f7420-166">No</span></span> | <span data-ttu-id="f7420-167">A frequência com que o parceiro é cobrado por esta ordem.</span><span class="sxs-lookup"><span data-stu-id="f7420-167">The frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="f7420-168">O padrão é &quot; mensal e é aplicado após a &quot; criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="f7420-168">The default is &quot;Monthly&quot; and is applied upon successful creation of the order.</span></span> <span data-ttu-id="f7420-169">Os valores suportados são os nomes dos membros encontrados no [**BillingCycleType**](/dotnet/api/microsoft.store.partnercenter.models.offers.billingcycletype).</span><span class="sxs-lookup"><span data-stu-id="f7420-169">Supported values are the member names found in [**BillingCycleType**](/dotnet/api/microsoft.store.partnercenter.models.offers.billingcycletype).</span></span> <span data-ttu-id="f7420-170">Nota: a funcionalidade anual de faturação ainda não está disponível em geral.</span><span class="sxs-lookup"><span data-stu-id="f7420-170">Note: the annual billing feature isn't yet generally available.</span></span> <span data-ttu-id="f7420-171">O apoio à faturação anual está para breve.</span><span class="sxs-lookup"><span data-stu-id="f7420-171">Support for annual billing is coming soon.</span></span> |
| <span data-ttu-id="f7420-172">lineitems</span><span class="sxs-lookup"><span data-stu-id="f7420-172">lineItems</span></span> | <span data-ttu-id="f7420-173">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="f7420-173">array of objects</span></span> | <span data-ttu-id="f7420-174">Yes</span><span class="sxs-lookup"><span data-stu-id="f7420-174">Yes</span></span> | <span data-ttu-id="f7420-175">Uma série de recursos [**orderLineItem.**](#orderlineitem)</span><span class="sxs-lookup"><span data-stu-id="f7420-175">An array of [**OrderLineItem**](#orderlineitem) resources.</span></span> |
| <span data-ttu-id="f7420-176">criaçãoDate</span><span class="sxs-lookup"><span data-stu-id="f7420-176">creationDate</span></span> | <span data-ttu-id="f7420-177">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="f7420-177">string</span></span> | <span data-ttu-id="f7420-178">No</span><span class="sxs-lookup"><span data-stu-id="f7420-178">No</span></span> | <span data-ttu-id="f7420-179">A data em que a encomenda foi criada, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="f7420-179">The date the order was created, in date-time format.</span></span> <span data-ttu-id="f7420-180">Aplicado após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="f7420-180">Applied upon successful creation of the order.</span></span> |
| <span data-ttu-id="f7420-181">atributos</span><span class="sxs-lookup"><span data-stu-id="f7420-181">attributes</span></span> | <span data-ttu-id="f7420-182">objeto</span><span class="sxs-lookup"><span data-stu-id="f7420-182">object</span></span> | <span data-ttu-id="f7420-183">No</span><span class="sxs-lookup"><span data-stu-id="f7420-183">No</span></span> | <span data-ttu-id="f7420-184">Contém "ObjectType": "Order".</span><span class="sxs-lookup"><span data-stu-id="f7420-184">Contains "ObjectType": "Order".</span></span> |

#### <a name="orderlineitem"></a><span data-ttu-id="f7420-185">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="f7420-185">OrderLineItem</span></span>

<span data-ttu-id="f7420-186">Esta tabela descreve as propriedades **orderLineItem** no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="f7420-186">This table describes the **OrderLineItem** properties in the request body.</span></span>

| <span data-ttu-id="f7420-187">Nome</span><span class="sxs-lookup"><span data-stu-id="f7420-187">Name</span></span> | <span data-ttu-id="f7420-188">Tipo</span><span class="sxs-lookup"><span data-stu-id="f7420-188">Type</span></span> | <span data-ttu-id="f7420-189">Necessário</span><span class="sxs-lookup"><span data-stu-id="f7420-189">Required</span></span> | <span data-ttu-id="f7420-190">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7420-190">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="f7420-191">lineItemNumber</span><span class="sxs-lookup"><span data-stu-id="f7420-191">lineItemNumber</span></span> | <span data-ttu-id="f7420-192">int</span><span class="sxs-lookup"><span data-stu-id="f7420-192">int</span></span> | <span data-ttu-id="f7420-193">Yes</span><span class="sxs-lookup"><span data-stu-id="f7420-193">Yes</span></span> | <span data-ttu-id="f7420-194">Cada item de linha da coleção obtém um número de linha único, contando de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="f7420-194">Each line item in the collection gets a unique line number, counting up from 0 to count-1.</span></span> |
| <span data-ttu-id="f7420-195">offerId</span><span class="sxs-lookup"><span data-stu-id="f7420-195">offerId</span></span> | <span data-ttu-id="f7420-196">string</span><span class="sxs-lookup"><span data-stu-id="f7420-196">string</span></span> | <span data-ttu-id="f7420-197">Yes</span><span class="sxs-lookup"><span data-stu-id="f7420-197">Yes</span></span> | <span data-ttu-id="f7420-198">O identificador da oferta.</span><span class="sxs-lookup"><span data-stu-id="f7420-198">The offer identifier.</span></span> |
| <span data-ttu-id="f7420-199">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="f7420-199">subscriptionId</span></span> | <span data-ttu-id="f7420-200">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="f7420-200">string</span></span> | <span data-ttu-id="f7420-201">No</span><span class="sxs-lookup"><span data-stu-id="f7420-201">No</span></span> | <span data-ttu-id="f7420-202">O identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="f7420-202">The subscription identifier.</span></span> |
| <span data-ttu-id="f7420-203">parentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="f7420-203">parentSubscriptionId</span></span> | <span data-ttu-id="f7420-204">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="f7420-204">string</span></span> | <span data-ttu-id="f7420-205">No</span><span class="sxs-lookup"><span data-stu-id="f7420-205">No</span></span> | <span data-ttu-id="f7420-206">Opcional.</span><span class="sxs-lookup"><span data-stu-id="f7420-206">Optional.</span></span> <span data-ttu-id="f7420-207">A identificação da subscrição dos pais numa oferta de complemento.</span><span class="sxs-lookup"><span data-stu-id="f7420-207">The ID of the parent subscription in an add-on offer.</span></span> <span data-ttu-id="f7420-208">Aplica-se apenas ao PATCH.</span><span class="sxs-lookup"><span data-stu-id="f7420-208">Applies to PATCH only.</span></span> |
| <span data-ttu-id="f7420-209">nome amigável</span><span class="sxs-lookup"><span data-stu-id="f7420-209">friendlyName</span></span> | <span data-ttu-id="f7420-210">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="f7420-210">string</span></span> | <span data-ttu-id="f7420-211">No</span><span class="sxs-lookup"><span data-stu-id="f7420-211">No</span></span> | <span data-ttu-id="f7420-212">Opcional.</span><span class="sxs-lookup"><span data-stu-id="f7420-212">Optional.</span></span> <span data-ttu-id="f7420-213">O nome amigável para a subscrição definida pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="f7420-213">The friendly name for the subscription defined by the partner to help disambiguate.</span></span> |
| <span data-ttu-id="f7420-214">quantidade</span><span class="sxs-lookup"><span data-stu-id="f7420-214">quantity</span></span> | <span data-ttu-id="f7420-215">int</span><span class="sxs-lookup"><span data-stu-id="f7420-215">int</span></span> | <span data-ttu-id="f7420-216">Yes</span><span class="sxs-lookup"><span data-stu-id="f7420-216">Yes</span></span> | <span data-ttu-id="f7420-217">O número de licenças para uma assinatura baseada em licença.</span><span class="sxs-lookup"><span data-stu-id="f7420-217">The number of licenses for a license-based subscription.</span></span> |
| <span data-ttu-id="f7420-218">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="f7420-218">partnerIdOnRecord</span></span> | <span data-ttu-id="f7420-219">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="f7420-219">string</span></span> | <span data-ttu-id="f7420-220">No</span><span class="sxs-lookup"><span data-stu-id="f7420-220">No</span></span> | <span data-ttu-id="f7420-221">Quando um fornecedor indireto estoende uma encomenda em nome de um revendedor indireto, povoe este campo apenas com o ID MPN do **revendedor indireto** (nunca o ID do fornecedor indireto).</span><span class="sxs-lookup"><span data-stu-id="f7420-221">When an indirect provider places an order on behalf of an indirect reseller, populate this field with the MPN ID of the **indirect reseller only** (never the ID of the indirect provider).</span></span> <span data-ttu-id="f7420-222">Isto garante uma contabilização adequada dos incentivos.</span><span class="sxs-lookup"><span data-stu-id="f7420-222">This ensures proper accounting for incentives.</span></span> <span data-ttu-id="f7420-223">**A não prestação do ID MPN do revendedor não faz com que a ordem falhe. No entanto, o revendedor não é registado e, consequentemente, os cálculos de incentivos podem não incluir a venda.**</span><span class="sxs-lookup"><span data-stu-id="f7420-223">**Failure to provide the reseller MPN ID does not cause the order to fail. However, the reseller isn't recorded and as a consequence incentive calculations may not include the sale.**</span></span> |
| <span data-ttu-id="f7420-224">atributos</span><span class="sxs-lookup"><span data-stu-id="f7420-224">attributes</span></span> | <span data-ttu-id="f7420-225">objeto</span><span class="sxs-lookup"><span data-stu-id="f7420-225">object</span></span> | <span data-ttu-id="f7420-226">No</span><span class="sxs-lookup"><span data-stu-id="f7420-226">No</span></span> | <span data-ttu-id="f7420-227">Contém "ObjectType":"OrderLineItem".</span><span class="sxs-lookup"><span data-stu-id="f7420-227">Contains "ObjectType":"OrderLineItem".</span></span> |

### <a name="request-example"></a><span data-ttu-id="f7420-228">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f7420-228">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/orders HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 02109f46-3ff2-4be4-9f37-b2eb6d58d542
MS-CorrelationId: 85195ae6-3de5-4978-abd4-7be2fbfe4c84
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 410
Expect: 100-continue

{
    "Id": null,
    "ReferenceCustomerId": "c501c3c4-d776-40ef-9ecf-9cefb59442c1",
    "BillingCycle": "unknown",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "SubscriptionId": null,
            "ParentSubscriptionId": null,
            "FriendlyName": "New offer purchase.",
            "Quantity": 5,
            "PartnerIdOnRecord": "4847383",
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

## <a name="rest-response"></a><span data-ttu-id="f7420-229">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f7420-229">REST response</span></span>

<span data-ttu-id="f7420-230">Se for bem sucedido, o organismo de resposta contém o recurso [de Encomenda](order-resources.md) povoada.</span><span class="sxs-lookup"><span data-stu-id="f7420-230">If successful, the response body contains the populated [Order](order-resources.md) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f7420-231">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f7420-231">Response success and error codes</span></span>

<span data-ttu-id="f7420-232">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f7420-232">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f7420-233">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f7420-233">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f7420-234">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f7420-234">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f7420-235">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f7420-235">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 831
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 85195ae6-3de5-4978-abd4-7be2fbfe4c84
MS-RequestId: 02109f46-3ff2-4be4-9f37-b2eb6d58d542
MS-CV: Nd3Oum/L5EywtKQK.0
MS-ServerId: 020021921
Date: Mon, 10 Apr 2017 23:02:24 GMT

{
    "id": "3eddcac6-63b2-4c40-b0b6-f47e18301492",
    "referenceCustomerId": "c501c3c4-d776-40ef-9ecf-9cefb59442c1",
    "billingCycle": "monthly",
    "lineItems": [{
            "lineItemNumber": 0,
            "offerId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "subscriptionId": "42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
            "friendlyName": "New offer purchase.",
            "quantity": 5,
            "partnerIdOnRecord": "4847383",
            "links": {
                "subscription": {
                    "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/subscriptions/42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2017-04-10T16:02:25.983-07:00",
    "links": {
        "self": {
            "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/orders/3eddcac6-63b2-4c40-b0b6-f47e18301492",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "eyJpZCI6IjNlZGRjYWM2LTYzYjItNGM0MC1iMGI2LWY0N2UxODMwMTQ5MiIsInZlcnNpb24iOjF9",
        "objectType": "Order"
    }
}
```
