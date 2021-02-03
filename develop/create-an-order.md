---
title: Criar uma encomenda de clientes
description: Saiba como usar as APIs do Partner Center para criar uma encomenda para um cliente. O artigo inclui pré-requisitos, passos e exemplos.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ce176909a1f9c350f1c16615171de57a7beb888d
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770124"
---
# <a name="create-an-order-for-a-customer-using-partner-center-apis"></a><span data-ttu-id="258ac-104">Criar uma encomenda para um cliente que utilize APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="258ac-104">Create an order for a customer using Partner Center APIs</span></span>

<span data-ttu-id="258ac-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="258ac-105">**Applies to:**</span></span>

- <span data-ttu-id="258ac-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="258ac-106">Partner Center</span></span>
- <span data-ttu-id="258ac-107">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="258ac-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="258ac-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="258ac-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="258ac-109">A criação de uma **encomenda de produtos de instância VM reservados da Azure** aplica-se *apenas* a:</span><span class="sxs-lookup"><span data-stu-id="258ac-109">Creating an **order for Azure reserved VM instance products** applies *only* to:</span></span>

- <span data-ttu-id="258ac-110">Partner Center</span><span class="sxs-lookup"><span data-stu-id="258ac-110">Partner Center</span></span>

<span data-ttu-id="258ac-111">Para obter informações sobre o que está atualmente disponível para vender, consulte [as ofertas do Partner no programa Cloud Solution Provider](/partner-center/csp-offers).</span><span class="sxs-lookup"><span data-stu-id="258ac-111">For information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="258ac-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="258ac-112">Prerequisites</span></span>

- <span data-ttu-id="258ac-113">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="258ac-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="258ac-114">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="258ac-114">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="258ac-115">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="258ac-115">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="258ac-116">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="258ac-116">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="258ac-117">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="258ac-117">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="258ac-118">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="258ac-118">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="258ac-119">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="258ac-119">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="258ac-120">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="258ac-120">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="258ac-121">Um identificador de oferta.</span><span class="sxs-lookup"><span data-stu-id="258ac-121">An offer identifier.</span></span>

## <a name="c"></a><span data-ttu-id="258ac-122">C\#</span><span class="sxs-lookup"><span data-stu-id="258ac-122">C\#</span></span>

<span data-ttu-id="258ac-123">Para criar uma encomenda para um cliente:</span><span class="sxs-lookup"><span data-stu-id="258ac-123">To create an order for a customer:</span></span>

1. <span data-ttu-id="258ac-124">Instantiar um objeto [**de Encomenda**](order-resources.md) e definir a propriedade **ReferenceCustomerID** para o ID do cliente para gravar o cliente.</span><span class="sxs-lookup"><span data-stu-id="258ac-124">Instantiate an [**Order**](order-resources.md) object and set the **ReferenceCustomerID** property to the customer ID to record the customer.</span></span>

2. <span data-ttu-id="258ac-125">Crie uma lista de objetos [**OrderLineItem**](order-resources.md#orderlineitem) e atribua a lista à propriedade **LineItems** da encomenda.</span><span class="sxs-lookup"><span data-stu-id="258ac-125">Create a list of [**OrderLineItem**](order-resources.md#orderlineitem) objects, and assign the list to the order's **LineItems** property.</span></span> <span data-ttu-id="258ac-126">Cada item da linha de encomenda contém a informação de compra para uma oferta.</span><span class="sxs-lookup"><span data-stu-id="258ac-126">Each order line item contains the purchase information for one offer.</span></span> <span data-ttu-id="258ac-127">Deve ter pelo menos um item de linha de encomenda.</span><span class="sxs-lookup"><span data-stu-id="258ac-127">You must have at least one order line item.</span></span>

3. <span data-ttu-id="258ac-128">Obtenha uma interface para encomendar operações.</span><span class="sxs-lookup"><span data-stu-id="258ac-128">Obtain an interface to order operations.</span></span> <span data-ttu-id="258ac-129">Primeiro, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="258ac-129">First, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="258ac-130">Em seguida, recupere a interface da propriedade [**Encomendas.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders)</span><span class="sxs-lookup"><span data-stu-id="258ac-130">Next, retrieve the interface from the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property.</span></span>

4. <span data-ttu-id="258ac-131">Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) ou [**Criar Aync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) e passe no objeto [**Encomenda.**](order-resources.md)</span><span class="sxs-lookup"><span data-stu-id="258ac-131">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) method and pass in the [**Order**](order-resources.md) object.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string offerId;

var order = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            OfferId = offerId,
            FriendlyName = "new offer purchase",
            Quantity = 1,
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", "5198C069-3DAA-403A-8660-5BE11BFD12EE" },
                { "scope", "shared" },
                { "duration", "3Years" }
            }
        }
    }
};

var createdOrder = partnerOperations.Customers.ById(customerId).Orders.Create(order);
```

<span data-ttu-id="258ac-132">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="258ac-132">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="258ac-133">**Projeto**: Partner Center SDK Samples **Class**: CreateOrder.cs</span><span class="sxs-lookup"><span data-stu-id="258ac-133">**Project**: Partner Center SDK Samples **Class**: CreateOrder.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="258ac-134">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="258ac-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="258ac-135">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="258ac-135">Request syntax</span></span>

| <span data-ttu-id="258ac-136">Método</span><span class="sxs-lookup"><span data-stu-id="258ac-136">Method</span></span>   | <span data-ttu-id="258ac-137">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="258ac-137">Request URI</span></span>                                                                            |
|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="258ac-138">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="258ac-138">**POST**</span></span> | <span data-ttu-id="258ac-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/encomendas HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="258ac-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="258ac-140">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="258ac-140">URI parameters</span></span>

<span data-ttu-id="258ac-141">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="258ac-141">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="258ac-142">Nome</span><span class="sxs-lookup"><span data-stu-id="258ac-142">Name</span></span>        | <span data-ttu-id="258ac-143">Tipo</span><span class="sxs-lookup"><span data-stu-id="258ac-143">Type</span></span>   | <span data-ttu-id="258ac-144">Necessário</span><span class="sxs-lookup"><span data-stu-id="258ac-144">Required</span></span> | <span data-ttu-id="258ac-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="258ac-145">Description</span></span>                                                |
|-------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="258ac-146">id cliente</span><span class="sxs-lookup"><span data-stu-id="258ac-146">customer-id</span></span> | <span data-ttu-id="258ac-147">string</span><span class="sxs-lookup"><span data-stu-id="258ac-147">string</span></span> | <span data-ttu-id="258ac-148">Sim</span><span class="sxs-lookup"><span data-stu-id="258ac-148">Yes</span></span>      | <span data-ttu-id="258ac-149">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="258ac-149">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="258ac-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="258ac-150">Request headers</span></span>

<span data-ttu-id="258ac-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="258ac-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="258ac-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="258ac-152">Request body</span></span>

#### <a name="order"></a><span data-ttu-id="258ac-153">Encomenda</span><span class="sxs-lookup"><span data-stu-id="258ac-153">Order</span></span>

<span data-ttu-id="258ac-154">Esta tabela descreve as propriedades da [Ordem](order-resources.md) no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="258ac-154">This table describes the [Order](order-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="258ac-155">Propriedade</span><span class="sxs-lookup"><span data-stu-id="258ac-155">Property</span></span>             | <span data-ttu-id="258ac-156">Tipo</span><span class="sxs-lookup"><span data-stu-id="258ac-156">Type</span></span>                        | <span data-ttu-id="258ac-157">Necessário</span><span class="sxs-lookup"><span data-stu-id="258ac-157">Required</span></span>                        | <span data-ttu-id="258ac-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="258ac-158">Description</span></span>                                                                   |
|----------------------|-----------------------------|---------------------------------|-------------------------------------------------------------------------------|
| <span data-ttu-id="258ac-159">ID</span><span class="sxs-lookup"><span data-stu-id="258ac-159">id</span></span>                   | <span data-ttu-id="258ac-160">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-160">string</span></span>                      | <span data-ttu-id="258ac-161">No</span><span class="sxs-lookup"><span data-stu-id="258ac-161">No</span></span>                              | <span data-ttu-id="258ac-162">Um identificador de ordem que é fornecido após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="258ac-162">An order identifier that is supplied upon successful creation of the order.</span></span>   |
| <span data-ttu-id="258ac-163">referênciaStomerId</span><span class="sxs-lookup"><span data-stu-id="258ac-163">referenceCustomerId</span></span>  | <span data-ttu-id="258ac-164">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-164">string</span></span>                      | <span data-ttu-id="258ac-165">No</span><span class="sxs-lookup"><span data-stu-id="258ac-165">No</span></span>                              | <span data-ttu-id="258ac-166">O identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="258ac-166">The customer identifier.</span></span> |
| <span data-ttu-id="258ac-167">billingCycle</span><span class="sxs-lookup"><span data-stu-id="258ac-167">billingCycle</span></span>         | <span data-ttu-id="258ac-168">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-168">string</span></span>                      | <span data-ttu-id="258ac-169">No</span><span class="sxs-lookup"><span data-stu-id="258ac-169">No</span></span>                              | <span data-ttu-id="258ac-170">Indica a frequência com que o parceiro é faturado para esta encomenda.</span><span class="sxs-lookup"><span data-stu-id="258ac-170">Indicates the frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="258ac-171">Os valores suportados são os nomes dos membros encontrados no [BillingCycleType](product-resources.md#billingcycletype).</span><span class="sxs-lookup"><span data-stu-id="258ac-171">Supported values are the member names found in [BillingCycleType](product-resources.md#billingcycletype).</span></span> <span data-ttu-id="258ac-172">O padrão é "Mensal" ou "OneTime" na criação da ordem.</span><span class="sxs-lookup"><span data-stu-id="258ac-172">The default is "Monthly" or "OneTime" at order creation.</span></span> <span data-ttu-id="258ac-173">Este campo é aplicado após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="258ac-173">This field is applied upon successful creation of the order.</span></span> |
| <span data-ttu-id="258ac-174">lineitems</span><span class="sxs-lookup"><span data-stu-id="258ac-174">lineItems</span></span>            | <span data-ttu-id="258ac-175">matriz de recursos [OrderLineItem](order-resources.md#orderlineitem)</span><span class="sxs-lookup"><span data-stu-id="258ac-175">array of [OrderLineItem](order-resources.md#orderlineitem) resources</span></span> | <span data-ttu-id="258ac-176">Sim</span><span class="sxs-lookup"><span data-stu-id="258ac-176">Yes</span></span>      | <span data-ttu-id="258ac-177">Uma lista itemada das ofertas que o cliente está a comprar, incluindo a quantidade.</span><span class="sxs-lookup"><span data-stu-id="258ac-177">An itemized list of the offers the customer is purchasing including the quantity.</span></span>        |
| <span data-ttu-id="258ac-178">currencyCode</span><span class="sxs-lookup"><span data-stu-id="258ac-178">currencyCode</span></span>         | <span data-ttu-id="258ac-179">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-179">string</span></span>                      | <span data-ttu-id="258ac-180">No</span><span class="sxs-lookup"><span data-stu-id="258ac-180">No</span></span>                              | <span data-ttu-id="258ac-181">Só para ler.</span><span class="sxs-lookup"><span data-stu-id="258ac-181">Read-only.</span></span> <span data-ttu-id="258ac-182">A moeda utilizada na eção da encomenda.</span><span class="sxs-lookup"><span data-stu-id="258ac-182">The currency used when placing the order.</span></span> <span data-ttu-id="258ac-183">Aplicado após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="258ac-183">Applied upon successful creation of the order.</span></span>           |
| <span data-ttu-id="258ac-184">criaçãoDate</span><span class="sxs-lookup"><span data-stu-id="258ac-184">creationDate</span></span>         | <span data-ttu-id="258ac-185">datetime</span><span class="sxs-lookup"><span data-stu-id="258ac-185">datetime</span></span>                    | <span data-ttu-id="258ac-186">Não</span><span class="sxs-lookup"><span data-stu-id="258ac-186">No</span></span>                              | <span data-ttu-id="258ac-187">Só para ler.</span><span class="sxs-lookup"><span data-stu-id="258ac-187">Read-only.</span></span> <span data-ttu-id="258ac-188">A data em que a encomenda foi criada, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="258ac-188">The date the order was created, in date-time format.</span></span> <span data-ttu-id="258ac-189">Aplicado após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="258ac-189">Applied upon successful creation of the order.</span></span>                                   |
| <span data-ttu-id="258ac-190">status</span><span class="sxs-lookup"><span data-stu-id="258ac-190">status</span></span>               | <span data-ttu-id="258ac-191">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-191">string</span></span>                      | <span data-ttu-id="258ac-192">No</span><span class="sxs-lookup"><span data-stu-id="258ac-192">No</span></span>                              | <span data-ttu-id="258ac-193">Só para ler.</span><span class="sxs-lookup"><span data-stu-id="258ac-193">Read-only.</span></span> <span data-ttu-id="258ac-194">O estado da ordem.</span><span class="sxs-lookup"><span data-stu-id="258ac-194">The status of the order.</span></span>  <span data-ttu-id="258ac-195">Os valores suportados são os nomes dos membros encontrados no [OrderStatus](order-resources.md#orderstatus).</span><span class="sxs-lookup"><span data-stu-id="258ac-195">Supported values are the member names found in [OrderStatus](order-resources.md#orderstatus).</span></span>        |
| <span data-ttu-id="258ac-196">ligações</span><span class="sxs-lookup"><span data-stu-id="258ac-196">links</span></span>                | [<span data-ttu-id="258ac-197">Pedidos</span><span class="sxs-lookup"><span data-stu-id="258ac-197">OrderLinks</span></span>](utility-resources.md#resourcelinks)              | <span data-ttu-id="258ac-198">Não</span><span class="sxs-lookup"><span data-stu-id="258ac-198">No</span></span>                              | <span data-ttu-id="258ac-199">Os links de recursos correspondentes à Ordem.</span><span class="sxs-lookup"><span data-stu-id="258ac-199">The resource links corresponding to the Order.</span></span> |
| <span data-ttu-id="258ac-200">atributos</span><span class="sxs-lookup"><span data-stu-id="258ac-200">attributes</span></span>           | [<span data-ttu-id="258ac-201">RecursosTributos</span><span class="sxs-lookup"><span data-stu-id="258ac-201">ResourceAttributes</span></span>](utility-resources.md#resourceattributes) | <span data-ttu-id="258ac-202">Não</span><span class="sxs-lookup"><span data-stu-id="258ac-202">No</span></span>                              | <span data-ttu-id="258ac-203">Os metadados atribuem correspondentes à Ordem.</span><span class="sxs-lookup"><span data-stu-id="258ac-203">The metadata attributes corresponding to the Order.</span></span> |

#### <a name="orderlineitem"></a><span data-ttu-id="258ac-204">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="258ac-204">OrderLineItem</span></span>

<span data-ttu-id="258ac-205">Esta tabela descreve as propriedades [orderLineItem](order-resources.md#orderlineitem) no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="258ac-205">This table describes the [OrderLineItem](order-resources.md#orderlineitem) properties in the request body.</span></span>

>[!NOTE]
><span data-ttu-id="258ac-206">O parceiroIdOnRecord só deve ser fornecido quando um fornecedor indireto faz uma encomenda em nome de um revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="258ac-206">The partnerIdOnRecord should only be provided when an indirect provider places an order on behalf of an indirect reseller.</span></span> <span data-ttu-id="258ac-207">É utilizado para armazenar o ID da Rede de Parceiros microsoft apenas do revendedor indireto (nunca o ID do fornecedor indireto).</span><span class="sxs-lookup"><span data-stu-id="258ac-207">It's used to store the Microsoft Partner Network ID of the indirect reseller only (never the ID of the indirect provider).</span></span>

| <span data-ttu-id="258ac-208">Nome</span><span class="sxs-lookup"><span data-stu-id="258ac-208">Name</span></span>                 | <span data-ttu-id="258ac-209">Tipo</span><span class="sxs-lookup"><span data-stu-id="258ac-209">Type</span></span>   | <span data-ttu-id="258ac-210">Necessário</span><span class="sxs-lookup"><span data-stu-id="258ac-210">Required</span></span> | <span data-ttu-id="258ac-211">Descrição</span><span class="sxs-lookup"><span data-stu-id="258ac-211">Description</span></span>                                                                                                                                                                                                                                |
|----------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="258ac-212">lineItemNumber</span><span class="sxs-lookup"><span data-stu-id="258ac-212">lineItemNumber</span></span>       | <span data-ttu-id="258ac-213">int</span><span class="sxs-lookup"><span data-stu-id="258ac-213">int</span></span>    | <span data-ttu-id="258ac-214">Sim</span><span class="sxs-lookup"><span data-stu-id="258ac-214">Yes</span></span>      | <span data-ttu-id="258ac-215">Cada item de linha da coleção obtém um número de linha único, contando de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="258ac-215">Each line item in the collection gets a unique line number, counting up from 0 to count-1.</span></span>                                                                                                                                                 |
| <span data-ttu-id="258ac-216">offerId</span><span class="sxs-lookup"><span data-stu-id="258ac-216">offerId</span></span>              | <span data-ttu-id="258ac-217">string</span><span class="sxs-lookup"><span data-stu-id="258ac-217">string</span></span> | <span data-ttu-id="258ac-218">Sim</span><span class="sxs-lookup"><span data-stu-id="258ac-218">Yes</span></span>      | <span data-ttu-id="258ac-219">O identificador da oferta.</span><span class="sxs-lookup"><span data-stu-id="258ac-219">The offer identifier.</span></span>                                                                                                                                                                                                                      |
| <span data-ttu-id="258ac-220">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="258ac-220">subscriptionId</span></span>       | <span data-ttu-id="258ac-221">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-221">string</span></span> | <span data-ttu-id="258ac-222">No</span><span class="sxs-lookup"><span data-stu-id="258ac-222">No</span></span>       | <span data-ttu-id="258ac-223">O identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="258ac-223">The subscription identifier.</span></span>                                                                                                                                                                                                               |
| <span data-ttu-id="258ac-224">parentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="258ac-224">parentSubscriptionId</span></span> | <span data-ttu-id="258ac-225">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-225">string</span></span> | <span data-ttu-id="258ac-226">No</span><span class="sxs-lookup"><span data-stu-id="258ac-226">No</span></span>       | <span data-ttu-id="258ac-227">Opcional.</span><span class="sxs-lookup"><span data-stu-id="258ac-227">Optional.</span></span> <span data-ttu-id="258ac-228">A identificação da subscrição dos pais numa oferta de complemento.</span><span class="sxs-lookup"><span data-stu-id="258ac-228">The ID of the parent subscription in an add-on offer.</span></span> <span data-ttu-id="258ac-229">Aplica-se apenas ao PATCH.</span><span class="sxs-lookup"><span data-stu-id="258ac-229">Applies to PATCH only.</span></span>                                                                                                                                                     |
| <span data-ttu-id="258ac-230">nome amigável</span><span class="sxs-lookup"><span data-stu-id="258ac-230">friendlyName</span></span>         | <span data-ttu-id="258ac-231">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-231">string</span></span> | <span data-ttu-id="258ac-232">No</span><span class="sxs-lookup"><span data-stu-id="258ac-232">No</span></span>       | <span data-ttu-id="258ac-233">Opcional.</span><span class="sxs-lookup"><span data-stu-id="258ac-233">Optional.</span></span> <span data-ttu-id="258ac-234">O nome amigável para a subscrição definida pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="258ac-234">The friendly name for the subscription defined by the partner to help disambiguate.</span></span>                                                                                                                                              |
| <span data-ttu-id="258ac-235">quantidade</span><span class="sxs-lookup"><span data-stu-id="258ac-235">quantity</span></span>             | <span data-ttu-id="258ac-236">int</span><span class="sxs-lookup"><span data-stu-id="258ac-236">int</span></span>    | <span data-ttu-id="258ac-237">Sim</span><span class="sxs-lookup"><span data-stu-id="258ac-237">Yes</span></span>      | <span data-ttu-id="258ac-238">O número de licenças para uma assinatura baseada em licença.</span><span class="sxs-lookup"><span data-stu-id="258ac-238">The number of licenses for a license-based subscription.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="258ac-239">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="258ac-239">partnerIdOnRecord</span></span>    | <span data-ttu-id="258ac-240">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-240">string</span></span> | <span data-ttu-id="258ac-241">No</span><span class="sxs-lookup"><span data-stu-id="258ac-241">No</span></span>       | <span data-ttu-id="258ac-242">Quando um fornecedor indireto estoende uma encomenda em nome de um revendedor indireto, povoe este campo apenas com o ID MPN do **revendedor indireto** (nunca o ID do fornecedor indireto).</span><span class="sxs-lookup"><span data-stu-id="258ac-242">When an indirect provider places an order on behalf of an indirect reseller, populate this field with the MPN ID of the **indirect reseller only** (never the ID of the indirect provider).</span></span> <span data-ttu-id="258ac-243">Isto garante uma contabilização adequada dos incentivos.</span><span class="sxs-lookup"><span data-stu-id="258ac-243">This ensures proper accounting for incentives.</span></span> |
| <span data-ttu-id="258ac-244">provisionamentoContexto</span><span class="sxs-lookup"><span data-stu-id="258ac-244">provisioningContext</span></span>  | <span data-ttu-id="258ac-245">Cadeia de<do dicionário,> de cordas</span><span class="sxs-lookup"><span data-stu-id="258ac-245">Dictionary<string, string></span></span>                | <span data-ttu-id="258ac-246">Não</span><span class="sxs-lookup"><span data-stu-id="258ac-246">No</span></span>       |  <span data-ttu-id="258ac-247">Informação necessária para o provisionamento de alguns itens no catálogo.</span><span class="sxs-lookup"><span data-stu-id="258ac-247">Information required for provisioning for some items in the catalog.</span></span> <span data-ttu-id="258ac-248">A propriedade de ProvisioningVariables num SKU indica quais propriedades são necessárias para itens específicos no catálogo.</span><span class="sxs-lookup"><span data-stu-id="258ac-248">The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.</span></span>                  |
| <span data-ttu-id="258ac-249">ligações</span><span class="sxs-lookup"><span data-stu-id="258ac-249">links</span></span>                | [<span data-ttu-id="258ac-250">OrderLineItemLinks</span><span class="sxs-lookup"><span data-stu-id="258ac-250">OrderLineItemLinks</span></span>](order-resources.md#orderlineitemlinks) | <span data-ttu-id="258ac-251">Não</span><span class="sxs-lookup"><span data-stu-id="258ac-251">No</span></span>       |  <span data-ttu-id="258ac-252">Só para ler.</span><span class="sxs-lookup"><span data-stu-id="258ac-252">Read-only.</span></span> <span data-ttu-id="258ac-253">As ligações de recursos correspondentes ao item da linha Encomenda.</span><span class="sxs-lookup"><span data-stu-id="258ac-253">The resource links corresponding to the Order line item.</span></span>  |
| <span data-ttu-id="258ac-254">atributos</span><span class="sxs-lookup"><span data-stu-id="258ac-254">attributes</span></span>           | [<span data-ttu-id="258ac-255">RecursosTributos</span><span class="sxs-lookup"><span data-stu-id="258ac-255">ResourceAttributes</span></span>](utility-resources.md#resourceattributes) | <span data-ttu-id="258ac-256">Não</span><span class="sxs-lookup"><span data-stu-id="258ac-256">No</span></span>       | <span data-ttu-id="258ac-257">Os metadados atribuem correspondentes ao OrderLineItem.</span><span class="sxs-lookup"><span data-stu-id="258ac-257">The metadata attributes corresponding to the OrderLineItem.</span></span> |
| <span data-ttu-id="258ac-258">renovaTo</span><span class="sxs-lookup"><span data-stu-id="258ac-258">renewsTo</span></span>             | <span data-ttu-id="258ac-259">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="258ac-259">Array of objects</span></span>                          | <span data-ttu-id="258ac-260">Não</span><span class="sxs-lookup"><span data-stu-id="258ac-260">No</span></span>    |<span data-ttu-id="258ac-261">Uma variedade de [recursos Renovados.](order-resources.md#renewsto)</span><span class="sxs-lookup"><span data-stu-id="258ac-261">An array of [RenewsTo](order-resources.md#renewsto) resources.</span></span>                                                                            |

##### <a name="renewsto"></a><span data-ttu-id="258ac-262">RenovarTo</span><span class="sxs-lookup"><span data-stu-id="258ac-262">RenewsTo</span></span>

<span data-ttu-id="258ac-263">Esta tabela descreve as propriedades [Renovações](order-resources.md#renewsto) No corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="258ac-263">This table describes the [RenewsTo](order-resources.md#renewsto) properties in the request body.</span></span>

| <span data-ttu-id="258ac-264">Propriedade</span><span class="sxs-lookup"><span data-stu-id="258ac-264">Property</span></span>              | <span data-ttu-id="258ac-265">Tipo</span><span class="sxs-lookup"><span data-stu-id="258ac-265">Type</span></span>             | <span data-ttu-id="258ac-266">Necessário</span><span class="sxs-lookup"><span data-stu-id="258ac-266">Required</span></span>        | <span data-ttu-id="258ac-267">Descrição</span><span class="sxs-lookup"><span data-stu-id="258ac-267">Description</span></span> |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="258ac-268">termoDuração</span><span class="sxs-lookup"><span data-stu-id="258ac-268">termDuration</span></span>          | <span data-ttu-id="258ac-269">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="258ac-269">string</span></span>           | <span data-ttu-id="258ac-270">No</span><span class="sxs-lookup"><span data-stu-id="258ac-270">No</span></span>              | <span data-ttu-id="258ac-271">Uma representação ISO 8601 da duração do período de renovação.</span><span class="sxs-lookup"><span data-stu-id="258ac-271">An ISO 8601 representation of the renewal term's duration.</span></span> <span data-ttu-id="258ac-272">Os valores suportados atuais são **P1M** (1 mês) e **P1Y** (1 ano).</span><span class="sxs-lookup"><span data-stu-id="258ac-272">The current supported values are **P1M** (1 month) and **P1Y** (1 year).</span></span> |

### <a name="request-example"></a><span data-ttu-id="258ac-273">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="258ac-273">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Length: 691
Content-Type: application/json

{
  "BillingCycle": "one_time",
  "CurrencyCode": "USD",
  "LineItems": [
    {
      "LineItemNumber": 0,
      "ProvisioningContext": {
        "subscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
        "scope": "shared",
        "duration": "1Year"
      },
      "OfferId": "DZH318Z0BQ4B:0047:DZH318Z0DSM8",
      "FriendlyName": "A_sample_Azure_RI",
      "Quantity": 1
    }
  ]
}
```

## <a name="rest-response"></a><span data-ttu-id="258ac-274">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="258ac-274">REST response</span></span>

<span data-ttu-id="258ac-275">Se for bem sucedido, o método devolve um recurso [da Ordem](order-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="258ac-275">If successful, the method returns an [Order](order-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="258ac-276">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="258ac-276">Response success and error codes</span></span>

<span data-ttu-id="258ac-277">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="258ac-277">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="258ac-278">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="258ac-278">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="258ac-279">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="258ac-279">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="258ac-280">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="258ac-280">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 788
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b593cbb7-b358-4b31-81fc-e60b9c277a7f
MS-RequestId: 025f4c19-217f-49d6-a056-391902c62fb3
Date: Thu, 15 Mar 2018 22:30:02 GMT

{
  "id": "Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1",
  "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
  "billingCycle": "one_time",
  "currencyCode": "USD",
  "lineItems": [
    {
        "lineItemNumber": 0,
        "offerId": "84A03D81-6B37-4D66-8D4A-FAEA24541538",
        "friendlyName": "A_sample_Azure_RI",
        "quantity": 1,
        "links": {
            "sku": {
                "uri": "/products/DZH318Z0BQ4B/skus/0047?country=US",
                "method": "GET",
                "headers": []
            }
        }
    } ],
    "creationDate": "2018-03-15T22:30:02.085152Z",
    "status": "pending",
    "links": {
        "provisioningStatus": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Order"
    }
}
```
