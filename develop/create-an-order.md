---
title: Criar uma encomenda de clientes
description: Saiba como usar as APIs do Partner Center para criar uma encomenda para um cliente. O artigo inclui pré-requisitos, passos e exemplos.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c3a86a99f43bdeec5e4c560ab59e1924b76c0636
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973554"
---
# <a name="create-an-order-for-a-customer-using-partner-center-apis"></a><span data-ttu-id="6c48a-104">Criar uma encomenda para um cliente que utilize APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="6c48a-104">Create an order for a customer using Partner Center APIs</span></span>

<span data-ttu-id="6c48a-105">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6c48a-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6c48a-106">A criação de uma **encomenda de produtos de instância VM reservados da Azure** aplica-se *apenas* a:</span><span class="sxs-lookup"><span data-stu-id="6c48a-106">Creating an **order for Azure reserved VM instance products** applies *only* to:</span></span>

- <span data-ttu-id="6c48a-107">Partner Center</span><span class="sxs-lookup"><span data-stu-id="6c48a-107">Partner Center</span></span>

<span data-ttu-id="6c48a-108">Para obter informações sobre o que está atualmente disponível para vender, consulte [as ofertas do Partner no programa Fornecedor de Soluções em Nuvem.](/partner-center/csp-offers)</span><span class="sxs-lookup"><span data-stu-id="6c48a-108">For information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6c48a-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6c48a-109">Prerequisites</span></span>

- <span data-ttu-id="6c48a-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6c48a-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6c48a-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="6c48a-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6c48a-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6c48a-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6c48a-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="6c48a-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6c48a-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="6c48a-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6c48a-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="6c48a-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6c48a-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="6c48a-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6c48a-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6c48a-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="6c48a-118">Um identificador de oferta.</span><span class="sxs-lookup"><span data-stu-id="6c48a-118">An offer identifier.</span></span>

## <a name="c"></a><span data-ttu-id="6c48a-119">C\#</span><span class="sxs-lookup"><span data-stu-id="6c48a-119">C\#</span></span>

<span data-ttu-id="6c48a-120">Para criar uma encomenda para um cliente:</span><span class="sxs-lookup"><span data-stu-id="6c48a-120">To create an order for a customer:</span></span>

1. <span data-ttu-id="6c48a-121">Instantiar um objeto [**de Encomenda**](order-resources.md) e definir a propriedade **ReferenceCustomerID** para o ID do cliente para gravar o cliente.</span><span class="sxs-lookup"><span data-stu-id="6c48a-121">Instantiate an [**Order**](order-resources.md) object and set the **ReferenceCustomerID** property to the customer ID to record the customer.</span></span>

2. <span data-ttu-id="6c48a-122">Crie uma lista de objetos [**OrderLineItem**](order-resources.md#orderlineitem) e atribua a lista à propriedade **LineItems** da encomenda.</span><span class="sxs-lookup"><span data-stu-id="6c48a-122">Create a list of [**OrderLineItem**](order-resources.md#orderlineitem) objects, and assign the list to the order's **LineItems** property.</span></span> <span data-ttu-id="6c48a-123">Cada item da linha de encomenda contém a informação de compra para uma oferta.</span><span class="sxs-lookup"><span data-stu-id="6c48a-123">Each order line item contains the purchase information for one offer.</span></span> <span data-ttu-id="6c48a-124">Deve ter pelo menos um item de linha de encomenda.</span><span class="sxs-lookup"><span data-stu-id="6c48a-124">You must have at least one order line item.</span></span>

3. <span data-ttu-id="6c48a-125">Obtenha uma interface para encomendar operações.</span><span class="sxs-lookup"><span data-stu-id="6c48a-125">Obtain an interface to order operations.</span></span> <span data-ttu-id="6c48a-126">Primeiro, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="6c48a-126">First, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="6c48a-127">Em seguida, recupere a interface da propriedade [**Encomendas.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders)</span><span class="sxs-lookup"><span data-stu-id="6c48a-127">Next, retrieve the interface from the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property.</span></span>

4. <span data-ttu-id="6c48a-128">Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) ou [**Criar Aync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) e passe no objeto [**Encomenda.**](order-resources.md)</span><span class="sxs-lookup"><span data-stu-id="6c48a-128">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) method and pass in the [**Order**](order-resources.md) object.</span></span>

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

<span data-ttu-id="6c48a-129">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="6c48a-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="6c48a-130">**Project**: Partner Center SDK Samples **Class**: CreateOrder.cs</span><span class="sxs-lookup"><span data-stu-id="6c48a-130">**Project**: Partner Center SDK Samples **Class**: CreateOrder.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="6c48a-131">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6c48a-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6c48a-132">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c48a-132">Request syntax</span></span>

| <span data-ttu-id="6c48a-133">Método</span><span class="sxs-lookup"><span data-stu-id="6c48a-133">Method</span></span>   | <span data-ttu-id="6c48a-134">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6c48a-134">Request URI</span></span>                                                                            |
|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="6c48a-135">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="6c48a-135">**POST**</span></span> | <span data-ttu-id="6c48a-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/encomendas HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6c48a-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="6c48a-137">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="6c48a-137">URI parameters</span></span>

<span data-ttu-id="6c48a-138">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="6c48a-138">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="6c48a-139">Nome</span><span class="sxs-lookup"><span data-stu-id="6c48a-139">Name</span></span>        | <span data-ttu-id="6c48a-140">Tipo</span><span class="sxs-lookup"><span data-stu-id="6c48a-140">Type</span></span>   | <span data-ttu-id="6c48a-141">Necessário</span><span class="sxs-lookup"><span data-stu-id="6c48a-141">Required</span></span> | <span data-ttu-id="6c48a-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c48a-142">Description</span></span>                                                |
|-------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="6c48a-143">id cliente</span><span class="sxs-lookup"><span data-stu-id="6c48a-143">customer-id</span></span> | <span data-ttu-id="6c48a-144">string</span><span class="sxs-lookup"><span data-stu-id="6c48a-144">string</span></span> | <span data-ttu-id="6c48a-145">Yes</span><span class="sxs-lookup"><span data-stu-id="6c48a-145">Yes</span></span>      | <span data-ttu-id="6c48a-146">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="6c48a-146">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6c48a-147">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6c48a-147">Request headers</span></span>

<span data-ttu-id="6c48a-148">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6c48a-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6c48a-149">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6c48a-149">Request body</span></span>

#### <a name="order"></a><span data-ttu-id="6c48a-150">Encomenda</span><span class="sxs-lookup"><span data-stu-id="6c48a-150">Order</span></span>

<span data-ttu-id="6c48a-151">Esta tabela descreve as propriedades da [Ordem](order-resources.md) no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="6c48a-151">This table describes the [Order](order-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="6c48a-152">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6c48a-152">Property</span></span>             | <span data-ttu-id="6c48a-153">Tipo</span><span class="sxs-lookup"><span data-stu-id="6c48a-153">Type</span></span>                        | <span data-ttu-id="6c48a-154">Necessário</span><span class="sxs-lookup"><span data-stu-id="6c48a-154">Required</span></span>                        | <span data-ttu-id="6c48a-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c48a-155">Description</span></span>                                                                   |
|----------------------|-----------------------------|---------------------------------|-------------------------------------------------------------------------------|
| <span data-ttu-id="6c48a-156">ID</span><span class="sxs-lookup"><span data-stu-id="6c48a-156">id</span></span>                   | <span data-ttu-id="6c48a-157">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-157">string</span></span>                      | <span data-ttu-id="6c48a-158">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-158">No</span></span>                              | <span data-ttu-id="6c48a-159">Um identificador de ordem que é fornecido após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-159">An order identifier that is supplied upon successful creation of the order.</span></span>   |
| <span data-ttu-id="6c48a-160">referênciaStomerId</span><span class="sxs-lookup"><span data-stu-id="6c48a-160">referenceCustomerId</span></span>  | <span data-ttu-id="6c48a-161">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-161">string</span></span>                      | <span data-ttu-id="6c48a-162">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-162">No</span></span>                              | <span data-ttu-id="6c48a-163">O identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="6c48a-163">The customer identifier.</span></span> |
| <span data-ttu-id="6c48a-164">billingCycle</span><span class="sxs-lookup"><span data-stu-id="6c48a-164">billingCycle</span></span>         | <span data-ttu-id="6c48a-165">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-165">string</span></span>                      | <span data-ttu-id="6c48a-166">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-166">No</span></span>                              | <span data-ttu-id="6c48a-167">Indica a frequência com que o parceiro é faturado para esta encomenda.</span><span class="sxs-lookup"><span data-stu-id="6c48a-167">Indicates the frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="6c48a-168">Os valores suportados são os nomes dos membros encontrados no [BillingCycleType](product-resources.md#billingcycletype).</span><span class="sxs-lookup"><span data-stu-id="6c48a-168">Supported values are the member names found in [BillingCycleType](product-resources.md#billingcycletype).</span></span> <span data-ttu-id="6c48a-169">O padrão é "Mensal" ou "OneTime" na criação da ordem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-169">The default is "Monthly" or "OneTime" at order creation.</span></span> <span data-ttu-id="6c48a-170">Este campo é aplicado após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-170">This field is applied upon successful creation of the order.</span></span> |
| <span data-ttu-id="6c48a-171">lineitems</span><span class="sxs-lookup"><span data-stu-id="6c48a-171">lineItems</span></span>            | <span data-ttu-id="6c48a-172">matriz de recursos [OrderLineItem](order-resources.md#orderlineitem)</span><span class="sxs-lookup"><span data-stu-id="6c48a-172">array of [OrderLineItem](order-resources.md#orderlineitem) resources</span></span> | <span data-ttu-id="6c48a-173">Yes</span><span class="sxs-lookup"><span data-stu-id="6c48a-173">Yes</span></span>      | <span data-ttu-id="6c48a-174">Uma lista itemada das ofertas que o cliente está a comprar, incluindo a quantidade.</span><span class="sxs-lookup"><span data-stu-id="6c48a-174">An itemized list of the offers the customer is purchasing including the quantity.</span></span>        |
| <span data-ttu-id="6c48a-175">currencyCode</span><span class="sxs-lookup"><span data-stu-id="6c48a-175">currencyCode</span></span>         | <span data-ttu-id="6c48a-176">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-176">string</span></span>                      | <span data-ttu-id="6c48a-177">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-177">No</span></span>                              | <span data-ttu-id="6c48a-178">Só para ler.</span><span class="sxs-lookup"><span data-stu-id="6c48a-178">Read-only.</span></span> <span data-ttu-id="6c48a-179">A moeda utilizada na eção da encomenda.</span><span class="sxs-lookup"><span data-stu-id="6c48a-179">The currency used when placing the order.</span></span> <span data-ttu-id="6c48a-180">Aplicado após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-180">Applied upon successful creation of the order.</span></span>           |
| <span data-ttu-id="6c48a-181">criaçãoDate</span><span class="sxs-lookup"><span data-stu-id="6c48a-181">creationDate</span></span>         | <span data-ttu-id="6c48a-182">datetime</span><span class="sxs-lookup"><span data-stu-id="6c48a-182">datetime</span></span>                    | <span data-ttu-id="6c48a-183">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-183">No</span></span>                              | <span data-ttu-id="6c48a-184">Só para ler.</span><span class="sxs-lookup"><span data-stu-id="6c48a-184">Read-only.</span></span> <span data-ttu-id="6c48a-185">A data em que a encomenda foi criada, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="6c48a-185">The date the order was created, in date-time format.</span></span> <span data-ttu-id="6c48a-186">Aplicado após a criação bem sucedida da ordem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-186">Applied upon successful creation of the order.</span></span>                                   |
| <span data-ttu-id="6c48a-187">status</span><span class="sxs-lookup"><span data-stu-id="6c48a-187">status</span></span>               | <span data-ttu-id="6c48a-188">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-188">string</span></span>                      | <span data-ttu-id="6c48a-189">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-189">No</span></span>                              | <span data-ttu-id="6c48a-190">Só para ler.</span><span class="sxs-lookup"><span data-stu-id="6c48a-190">Read-only.</span></span> <span data-ttu-id="6c48a-191">O estado da ordem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-191">The status of the order.</span></span>  <span data-ttu-id="6c48a-192">Os valores suportados são os nomes dos membros encontrados no [OrderStatus](order-resources.md#orderstatus).</span><span class="sxs-lookup"><span data-stu-id="6c48a-192">Supported values are the member names found in [OrderStatus](order-resources.md#orderstatus).</span></span>        |
| <span data-ttu-id="6c48a-193">ligações</span><span class="sxs-lookup"><span data-stu-id="6c48a-193">links</span></span>                | [<span data-ttu-id="6c48a-194">Pedidos</span><span class="sxs-lookup"><span data-stu-id="6c48a-194">OrderLinks</span></span>](utility-resources.md#resourcelinks)              | <span data-ttu-id="6c48a-195">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-195">No</span></span>                              | <span data-ttu-id="6c48a-196">Os links de recursos correspondentes à Ordem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-196">The resource links corresponding to the Order.</span></span> |
| <span data-ttu-id="6c48a-197">atributos</span><span class="sxs-lookup"><span data-stu-id="6c48a-197">attributes</span></span>           | [<span data-ttu-id="6c48a-198">RecursosTributos</span><span class="sxs-lookup"><span data-stu-id="6c48a-198">ResourceAttributes</span></span>](utility-resources.md#resourceattributes) | <span data-ttu-id="6c48a-199">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-199">No</span></span>                              | <span data-ttu-id="6c48a-200">Os metadados atribuem correspondentes à Ordem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-200">The metadata attributes corresponding to the Order.</span></span> |

#### <a name="orderlineitem"></a><span data-ttu-id="6c48a-201">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="6c48a-201">OrderLineItem</span></span>

<span data-ttu-id="6c48a-202">Esta tabela descreve as propriedades [orderLineItem](order-resources.md#orderlineitem) no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="6c48a-202">This table describes the [OrderLineItem](order-resources.md#orderlineitem) properties in the request body.</span></span>

>[!NOTE]
><span data-ttu-id="6c48a-203">O parceiroIdOnRecord só deve ser fornecido quando um fornecedor indireto faz uma encomenda em nome de um revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="6c48a-203">The partnerIdOnRecord should only be provided when an indirect provider places an order on behalf of an indirect reseller.</span></span> <span data-ttu-id="6c48a-204">É utilizado para armazenar o ID da Rede de Parceiros microsoft apenas do revendedor indireto (nunca o ID do fornecedor indireto).</span><span class="sxs-lookup"><span data-stu-id="6c48a-204">It's used to store the Microsoft Partner Network ID of the indirect reseller only (never the ID of the indirect provider).</span></span>

| <span data-ttu-id="6c48a-205">Nome</span><span class="sxs-lookup"><span data-stu-id="6c48a-205">Name</span></span>                 | <span data-ttu-id="6c48a-206">Tipo</span><span class="sxs-lookup"><span data-stu-id="6c48a-206">Type</span></span>   | <span data-ttu-id="6c48a-207">Necessário</span><span class="sxs-lookup"><span data-stu-id="6c48a-207">Required</span></span> | <span data-ttu-id="6c48a-208">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c48a-208">Description</span></span>                                                                                                                                                                                                                                |
|----------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6c48a-209">lineItemNumber</span><span class="sxs-lookup"><span data-stu-id="6c48a-209">lineItemNumber</span></span>       | <span data-ttu-id="6c48a-210">int</span><span class="sxs-lookup"><span data-stu-id="6c48a-210">int</span></span>    | <span data-ttu-id="6c48a-211">Yes</span><span class="sxs-lookup"><span data-stu-id="6c48a-211">Yes</span></span>      | <span data-ttu-id="6c48a-212">Cada item de linha da coleção obtém um número de linha único, contando de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="6c48a-212">Each line item in the collection gets a unique line number, counting up from 0 to count-1.</span></span>                                                                                                                                                 |
| <span data-ttu-id="6c48a-213">offerId</span><span class="sxs-lookup"><span data-stu-id="6c48a-213">offerId</span></span>              | <span data-ttu-id="6c48a-214">string</span><span class="sxs-lookup"><span data-stu-id="6c48a-214">string</span></span> | <span data-ttu-id="6c48a-215">Yes</span><span class="sxs-lookup"><span data-stu-id="6c48a-215">Yes</span></span>      | <span data-ttu-id="6c48a-216">O identificador da oferta.</span><span class="sxs-lookup"><span data-stu-id="6c48a-216">The offer identifier.</span></span>                                                                                                                                                                                                                      |
| <span data-ttu-id="6c48a-217">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="6c48a-217">subscriptionId</span></span>       | <span data-ttu-id="6c48a-218">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-218">string</span></span> | <span data-ttu-id="6c48a-219">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-219">No</span></span>       | <span data-ttu-id="6c48a-220">O identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="6c48a-220">The subscription identifier.</span></span>                                                                                                                                                                                                               |
| <span data-ttu-id="6c48a-221">parentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="6c48a-221">parentSubscriptionId</span></span> | <span data-ttu-id="6c48a-222">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-222">string</span></span> | <span data-ttu-id="6c48a-223">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-223">No</span></span>       | <span data-ttu-id="6c48a-224">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6c48a-224">Optional.</span></span> <span data-ttu-id="6c48a-225">A identificação da subscrição dos pais numa oferta de complemento.</span><span class="sxs-lookup"><span data-stu-id="6c48a-225">The ID of the parent subscription in an add-on offer.</span></span> <span data-ttu-id="6c48a-226">Aplica-se apenas ao PATCH.</span><span class="sxs-lookup"><span data-stu-id="6c48a-226">Applies to PATCH only.</span></span>                                                                                                                                                     |
| <span data-ttu-id="6c48a-227">nome amigável</span><span class="sxs-lookup"><span data-stu-id="6c48a-227">friendlyName</span></span>         | <span data-ttu-id="6c48a-228">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-228">string</span></span> | <span data-ttu-id="6c48a-229">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-229">No</span></span>       | <span data-ttu-id="6c48a-230">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6c48a-230">Optional.</span></span> <span data-ttu-id="6c48a-231">O nome amigável para a subscrição definida pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="6c48a-231">The friendly name for the subscription defined by the partner to help disambiguate.</span></span>                                                                                                                                              |
| <span data-ttu-id="6c48a-232">quantidade</span><span class="sxs-lookup"><span data-stu-id="6c48a-232">quantity</span></span>             | <span data-ttu-id="6c48a-233">int</span><span class="sxs-lookup"><span data-stu-id="6c48a-233">int</span></span>    | <span data-ttu-id="6c48a-234">Yes</span><span class="sxs-lookup"><span data-stu-id="6c48a-234">Yes</span></span>      | <span data-ttu-id="6c48a-235">O número de licenças para uma assinatura baseada em licença.</span><span class="sxs-lookup"><span data-stu-id="6c48a-235">The number of licenses for a license-based subscription.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="6c48a-236">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="6c48a-236">partnerIdOnRecord</span></span>    | <span data-ttu-id="6c48a-237">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-237">string</span></span> | <span data-ttu-id="6c48a-238">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-238">No</span></span>       | <span data-ttu-id="6c48a-239">Quando um fornecedor indireto estoende uma encomenda em nome de um revendedor indireto, povoe este campo apenas com o ID MPN do **revendedor indireto** (nunca o ID do fornecedor indireto).</span><span class="sxs-lookup"><span data-stu-id="6c48a-239">When an indirect provider places an order on behalf of an indirect reseller, populate this field with the MPN ID of the **indirect reseller only** (never the ID of the indirect provider).</span></span> <span data-ttu-id="6c48a-240">Isto garante uma contabilização adequada dos incentivos.</span><span class="sxs-lookup"><span data-stu-id="6c48a-240">This ensures proper accounting for incentives.</span></span> |
| <span data-ttu-id="6c48a-241">provisionamentoContexto</span><span class="sxs-lookup"><span data-stu-id="6c48a-241">provisioningContext</span></span>  | <span data-ttu-id="6c48a-242">Cadeia de<do dicionário,> de cordas</span><span class="sxs-lookup"><span data-stu-id="6c48a-242">Dictionary<string, string></span></span>                | <span data-ttu-id="6c48a-243">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-243">No</span></span>       |  <span data-ttu-id="6c48a-244">Informação necessária para o provisionamento de alguns itens no catálogo.</span><span class="sxs-lookup"><span data-stu-id="6c48a-244">Information required for provisioning for some items in the catalog.</span></span> <span data-ttu-id="6c48a-245">A propriedade de ProvisioningVariables num SKU indica quais propriedades são necessárias para itens específicos no catálogo.</span><span class="sxs-lookup"><span data-stu-id="6c48a-245">The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.</span></span>                  |
| <span data-ttu-id="6c48a-246">ligações</span><span class="sxs-lookup"><span data-stu-id="6c48a-246">links</span></span>                | [<span data-ttu-id="6c48a-247">OrderLineItemLinks</span><span class="sxs-lookup"><span data-stu-id="6c48a-247">OrderLineItemLinks</span></span>](order-resources.md#orderlineitemlinks) | <span data-ttu-id="6c48a-248">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-248">No</span></span>       |  <span data-ttu-id="6c48a-249">Só para ler.</span><span class="sxs-lookup"><span data-stu-id="6c48a-249">Read-only.</span></span> <span data-ttu-id="6c48a-250">As ligações de recursos correspondentes ao item da linha Encomenda.</span><span class="sxs-lookup"><span data-stu-id="6c48a-250">The resource links corresponding to the Order line item.</span></span>  |
| <span data-ttu-id="6c48a-251">atributos</span><span class="sxs-lookup"><span data-stu-id="6c48a-251">attributes</span></span>           | [<span data-ttu-id="6c48a-252">RecursosTributos</span><span class="sxs-lookup"><span data-stu-id="6c48a-252">ResourceAttributes</span></span>](utility-resources.md#resourceattributes) | <span data-ttu-id="6c48a-253">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-253">No</span></span>       | <span data-ttu-id="6c48a-254">Os metadados atribuem correspondentes ao OrderLineItem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-254">The metadata attributes corresponding to the OrderLineItem.</span></span> |
| <span data-ttu-id="6c48a-255">renovaTo</span><span class="sxs-lookup"><span data-stu-id="6c48a-255">renewsTo</span></span>             | <span data-ttu-id="6c48a-256">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="6c48a-256">Array of objects</span></span>                          | <span data-ttu-id="6c48a-257">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-257">No</span></span>    |<span data-ttu-id="6c48a-258">Uma variedade de [recursos Renovados.](order-resources.md#renewsto)</span><span class="sxs-lookup"><span data-stu-id="6c48a-258">An array of [RenewsTo](order-resources.md#renewsto) resources.</span></span>                                                                            |

##### <a name="renewsto"></a><span data-ttu-id="6c48a-259">RenovarTo</span><span class="sxs-lookup"><span data-stu-id="6c48a-259">RenewsTo</span></span>

<span data-ttu-id="6c48a-260">Esta tabela descreve as propriedades [Renovações](order-resources.md#renewsto) No corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="6c48a-260">This table describes the [RenewsTo](order-resources.md#renewsto) properties in the request body.</span></span>

| <span data-ttu-id="6c48a-261">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6c48a-261">Property</span></span>              | <span data-ttu-id="6c48a-262">Tipo</span><span class="sxs-lookup"><span data-stu-id="6c48a-262">Type</span></span>             | <span data-ttu-id="6c48a-263">Necessário</span><span class="sxs-lookup"><span data-stu-id="6c48a-263">Required</span></span>        | <span data-ttu-id="6c48a-264">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c48a-264">Description</span></span> |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6c48a-265">termoDuração</span><span class="sxs-lookup"><span data-stu-id="6c48a-265">termDuration</span></span>          | <span data-ttu-id="6c48a-266">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6c48a-266">string</span></span>           | <span data-ttu-id="6c48a-267">No</span><span class="sxs-lookup"><span data-stu-id="6c48a-267">No</span></span>              | <span data-ttu-id="6c48a-268">Uma representação ISO 8601 da duração do período de renovação.</span><span class="sxs-lookup"><span data-stu-id="6c48a-268">An ISO 8601 representation of the renewal term's duration.</span></span> <span data-ttu-id="6c48a-269">Os valores suportados atuais são **P1M** (1 mês) e **P1Y** (1 ano).</span><span class="sxs-lookup"><span data-stu-id="6c48a-269">The current supported values are **P1M** (1 month) and **P1Y** (1 year).</span></span> |

### <a name="request-example"></a><span data-ttu-id="6c48a-270">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6c48a-270">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="6c48a-271">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6c48a-271">REST response</span></span>

<span data-ttu-id="6c48a-272">Se for bem sucedido, o método devolve um recurso [da Ordem](order-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="6c48a-272">If successful, the method returns an [Order](order-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6c48a-273">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6c48a-273">Response success and error codes</span></span>

<span data-ttu-id="6c48a-274">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6c48a-274">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6c48a-275">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6c48a-275">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6c48a-276">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6c48a-276">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6c48a-277">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6c48a-277">Response example</span></span>

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
