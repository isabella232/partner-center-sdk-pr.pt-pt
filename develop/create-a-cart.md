---
title: Criar um carrinho
description: Saiba como usar as APIs do Partner Center para adicionar um pedido para um cliente num carrinho. O tópico inclui informações sobre a criação de um carrinho e quaisquer pré-requisitos.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: a1c559b415a7d42af4e904e09795f92aed7f125f
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770129"
---
# <a name="create-a-cart-with-a-customer-order"></a><span data-ttu-id="8e54a-104">Criar um carrinho com uma encomenda de cliente</span><span class="sxs-lookup"><span data-stu-id="8e54a-104">Create a cart with a customer order</span></span>

<span data-ttu-id="8e54a-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="8e54a-105">**Applies to:**</span></span>

- <span data-ttu-id="8e54a-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="8e54a-106">Partner Center</span></span>
- <span data-ttu-id="8e54a-107">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="8e54a-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="8e54a-108">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="8e54a-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="8e54a-109">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8e54a-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8e54a-110">Pode adicionar um pedido para um cliente num carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-110">You can add an order for a customer in a cart.</span></span> <span data-ttu-id="8e54a-111">Para obter mais informações sobre o que está atualmente disponível para vender, consulte [as ofertas do Partner no programa Cloud Solution Provider](/partner-center/csp-offers).</span><span class="sxs-lookup"><span data-stu-id="8e54a-111">For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8e54a-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8e54a-112">Prerequisites</span></span>

- <span data-ttu-id="8e54a-113">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8e54a-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8e54a-114">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="8e54a-114">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="8e54a-115">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8e54a-115">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8e54a-116">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="8e54a-116">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8e54a-117">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="8e54a-117">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8e54a-118">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="8e54a-118">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8e54a-119">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="8e54a-119">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8e54a-120">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8e54a-120">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="8e54a-121">C\#</span><span class="sxs-lookup"><span data-stu-id="8e54a-121">C\#</span></span>

<span data-ttu-id="8e54a-122">Para criar uma encomenda para um cliente:</span><span class="sxs-lookup"><span data-stu-id="8e54a-122">To create an order for a customer:</span></span>

1. <span data-ttu-id="8e54a-123">Instantiizar um objeto do Carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-123">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="8e54a-124">Crie uma lista de objetos **CartLineItem** e atribua a lista à propriedade lineItems do carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-124">Create a list of **CartLineItem** objects, and assign the list to the cart's LineItems property.</span></span> <span data-ttu-id="8e54a-125">Cada item da linha do carrinho contém a informação de compra de um produto.</span><span class="sxs-lookup"><span data-stu-id="8e54a-125">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="8e54a-126">Deve ter pelo menos um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-126">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="8e54a-127">Obtenha uma interface para as operações de carrinhos ligando para o método **IAggregatePartner.Customers.ById** com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface da propriedade **Cart.**</span><span class="sxs-lookup"><span data-stu-id="8e54a-127">Obtain an interface to cart operations by calling the **IAggregatePartner.Customers.ById** method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.</span></span>

4. <span data-ttu-id="8e54a-128">Ligue para o método **Criar** ou **Criar** Para criar o carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-128">Call the **Create** or **CreateAsync** method to create the cart.</span></span>

### <a name="c-example"></a><span data-ttu-id="8e54a-129">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="8e54a-129">C\# example</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

var cart = new Cart()
{
    LineItems = new List<CartLineItem>()
    {
        new CartLineItem()
        {
      /* Microsoft Azure Subscription */
            Id = 0,
            CatalogItemId = "MS-AZR-0145P",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1Y"
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 1,
            CatalogItemId = "DZH318Z0BQ36:004G:DZH318Z08C0S",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P1Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 2,
            CatalogItemId = "DZH318Z0BQ36:004J:DZH318Z08B8X",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P3Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Perpetual Software */
            Id = 3,
            CatalogItemId = "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime
        },
        new CartLineItem()
        {
      /* SaaS */
            Id = 4,
            CatalogItemId = "DZH318Z0BXWC:0002:DZH318Z0BMRV",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1M"
        },
        new CartLineItem()
        {
      /* SaaS Free Trial */
            Id = 5,
            CatalogItemId = "DZH318Z0C0WF:0001:DZH318Z0BP69",
            Quantity = 10,
            BillingCycle = BillingCycleType.None,
            TermDuration = "P1M",
            RenewsTo = new RenewsTo
            {
                TermDuration = "P1Y"
            }
        }
    }
};

cart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

## <a name="java"></a><span data-ttu-id="8e54a-130">Java</span><span class="sxs-lookup"><span data-stu-id="8e54a-130">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="8e54a-131">Para criar uma encomenda para um cliente:</span><span class="sxs-lookup"><span data-stu-id="8e54a-131">To create an order for a customer:</span></span>

1. <span data-ttu-id="8e54a-132">Instantiizar um objeto do Carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-132">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="8e54a-133">Crie uma lista de objetos **CartLineItem** e atribua a lista aos itens de linha do carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-133">Create a list of **CartLineItem** objects, and assign the list to the cart's line items.</span></span> <span data-ttu-id="8e54a-134">Cada item da linha do carrinho contém a informação de compra de um produto.</span><span class="sxs-lookup"><span data-stu-id="8e54a-134">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="8e54a-135">Deve ter pelo menos um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-135">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="8e54a-136">Obtenha uma interface para as operações de carrinhos ligando para o **IAggregatePartner.getCustomers ().função byId** com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface da função **getCart.**</span><span class="sxs-lookup"><span data-stu-id="8e54a-136">Obtain an interface to cart operations by calling the **IAggregatePartner.getCustomers().byId** function with the customer ID to identify the customer, and then retrieving the interface from the **getCart** function.</span></span>

4. <span data-ttu-id="8e54a-137">Ligue para a função **criar** o carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-137">Call the **create** function to create the cart.</span></span>

## <a name="java-example"></a><span data-ttu-id="8e54a-138">Exemplo de Java</span><span class="sxs-lookup"><span data-stu-id="8e54a-138">Java example</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String subscriptionId;
// String catalogItemId;

CartLineItem lineItem = new CartLineItem();

lineItem.setBillingCycle(BillingCycleType.OneTime);
lineItem.setCatalogItemId(catalogItemId);
lineItem.setFriendlyName("Sample RI Purchase");
lineItem.setQuantity(1);

Map<String, String> provisioningContext = new HashMap<String,String>();

provisioningContext.put("duration", "3Years");
provisioningContext.put("scope", "shared");
provisioningContext.put("subscriptionId", subscriptionId);

lineItem.setProvisioningContext(provisioningContext);

List<CartLineItem> lineItemList = new ArrayList<CartLineItem>();
lineItemList.add(lineItem);

Cart cart = new Cart();
cart.setLineItems(lineItemList);

Cart cartCreated = partnerOperations.getCustomers().byId(customerId).getCarts().create(cart);
```

## <a name="powershell"></a><span data-ttu-id="8e54a-139">PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e54a-139">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="8e54a-140">Para criar uma encomenda para um cliente:</span><span class="sxs-lookup"><span data-stu-id="8e54a-140">To create an order for a customer:</span></span>

1. <span data-ttu-id="8e54a-141">Instantiizar um objeto do Carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-141">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="8e54a-142">Crie uma lista de objetos **CartLineItem** e atribua a lista aos itens de linha do carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-142">Create a list of **CartLineItem** objects, and assign the list to the cart's line items.</span></span> <span data-ttu-id="8e54a-143">Cada item da linha do carrinho contém a informação de compra de um produto.</span><span class="sxs-lookup"><span data-stu-id="8e54a-143">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="8e54a-144">Deve ter pelo menos um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-144">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="8e54a-145">Execute o comando [**New PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) para criar o carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-145">Execute the [**New-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) command to create the cart.</span></span>

```powershell
# $customerId
# $subscriptionId
# $catalogItemId

$lineItem = New-Object -TypeName Microsoft.Store.PartnerCenter.PowerShell.Models.Carts.PSCartLineItem

$lineItem.BillingCycle = 'OneTime'
$lineItem.CatalogItemId = $catalogItemId
$lineItem.FriendlyName = 'Sample RI Purchase'
$lineItem.ProvisioningContext.Add('duration', '1Year')
$lineItem.ProvisioningContext.Add('scope', 'shared')
$lineItem.ProvisioningContext.Add('subscriptionId', $subsciptionId)
$lineItem.Quantity = 10

New-PartnerCustomerCart -CustomerId $customerId -LineItems $lineItem
```

## <a name="rest-request"></a><span data-ttu-id="8e54a-146">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="8e54a-146">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8e54a-147">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e54a-147">Request syntax</span></span>

| <span data-ttu-id="8e54a-148">Método</span><span class="sxs-lookup"><span data-stu-id="8e54a-148">Method</span></span>   | <span data-ttu-id="8e54a-149">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="8e54a-149">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8e54a-150">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="8e54a-150">**POST**</span></span> | <span data-ttu-id="8e54a-151">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8e54a-151">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span></span>                        |

### <a name="uri-parameter"></a><span data-ttu-id="8e54a-152">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="8e54a-152">URI parameter</span></span>

<span data-ttu-id="8e54a-153">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="8e54a-153">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="8e54a-154">Nome</span><span class="sxs-lookup"><span data-stu-id="8e54a-154">Name</span></span>            | <span data-ttu-id="8e54a-155">Tipo</span><span class="sxs-lookup"><span data-stu-id="8e54a-155">Type</span></span>     | <span data-ttu-id="8e54a-156">Necessário</span><span class="sxs-lookup"><span data-stu-id="8e54a-156">Required</span></span> | <span data-ttu-id="8e54a-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e54a-157">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="8e54a-158">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="8e54a-158">**customer-id**</span></span> | <span data-ttu-id="8e54a-159">string</span><span class="sxs-lookup"><span data-stu-id="8e54a-159">string</span></span>   | <span data-ttu-id="8e54a-160">Sim</span><span class="sxs-lookup"><span data-stu-id="8e54a-160">Yes</span></span>      | <span data-ttu-id="8e54a-161">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="8e54a-161">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="8e54a-162">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="8e54a-162">Request headers</span></span>

<span data-ttu-id="8e54a-163">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8e54a-163">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8e54a-164">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="8e54a-164">Request body</span></span>

<span data-ttu-id="8e54a-165">Esta tabela descreve as propriedades do [Carrinho](cart-resources.md) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="8e54a-165">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="8e54a-166">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8e54a-166">Property</span></span>              | <span data-ttu-id="8e54a-167">Tipo</span><span class="sxs-lookup"><span data-stu-id="8e54a-167">Type</span></span>             | <span data-ttu-id="8e54a-168">Necessário</span><span class="sxs-lookup"><span data-stu-id="8e54a-168">Required</span></span>        | <span data-ttu-id="8e54a-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e54a-169">Description</span></span> |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8e54a-170">ID</span><span class="sxs-lookup"><span data-stu-id="8e54a-170">id</span></span>                    | <span data-ttu-id="8e54a-171">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="8e54a-171">string</span></span>           | <span data-ttu-id="8e54a-172">No</span><span class="sxs-lookup"><span data-stu-id="8e54a-172">No</span></span>              | <span data-ttu-id="8e54a-173">Um identificador de carrinhos que é fornecido após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-173">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="8e54a-174">criaçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="8e54a-174">creationTimeStamp</span></span>     | <span data-ttu-id="8e54a-175">DateTime</span><span class="sxs-lookup"><span data-stu-id="8e54a-175">DateTime</span></span>         | <span data-ttu-id="8e54a-176">Não</span><span class="sxs-lookup"><span data-stu-id="8e54a-176">No</span></span>              | <span data-ttu-id="8e54a-177">A data em que o carrinho foi criado, em formato de data- hora.</span><span class="sxs-lookup"><span data-stu-id="8e54a-177">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="8e54a-178">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-178">Applied upon successful creation of the cart.</span></span>         |
| <span data-ttu-id="8e54a-179">últimampadatimestamp de Tempos</span><span class="sxs-lookup"><span data-stu-id="8e54a-179">lastModifiedTimeStamp</span></span> | <span data-ttu-id="8e54a-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="8e54a-180">DateTime</span></span>         | <span data-ttu-id="8e54a-181">Não</span><span class="sxs-lookup"><span data-stu-id="8e54a-181">No</span></span>              | <span data-ttu-id="8e54a-182">A data em que o carrinho foi atualizado pela última vez, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="8e54a-182">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="8e54a-183">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-183">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="8e54a-184">expiraçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="8e54a-184">expirationTimeStamp</span></span>   | <span data-ttu-id="8e54a-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="8e54a-185">DateTime</span></span>         | <span data-ttu-id="8e54a-186">Não</span><span class="sxs-lookup"><span data-stu-id="8e54a-186">No</span></span>              | <span data-ttu-id="8e54a-187">A data em que o carrinho expirará, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="8e54a-187">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="8e54a-188">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-188">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="8e54a-189">últimoModifiedUser</span><span class="sxs-lookup"><span data-stu-id="8e54a-189">lastModifiedUser</span></span>      | <span data-ttu-id="8e54a-190">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="8e54a-190">string</span></span>           | <span data-ttu-id="8e54a-191">No</span><span class="sxs-lookup"><span data-stu-id="8e54a-191">No</span></span>              | <span data-ttu-id="8e54a-192">O utilizador que atualizou pela última vez o carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-192">The user who last updated the cart.</span></span> <span data-ttu-id="8e54a-193">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-193">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="8e54a-194">lineitems</span><span class="sxs-lookup"><span data-stu-id="8e54a-194">lineItems</span></span>             | <span data-ttu-id="8e54a-195">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="8e54a-195">Array of objects</span></span> | <span data-ttu-id="8e54a-196">Sim</span><span class="sxs-lookup"><span data-stu-id="8e54a-196">Yes</span></span>             | <span data-ttu-id="8e54a-197">Uma matriz de recursos [CartLineItem.](cart-resources.md#cartlineitem)</span><span class="sxs-lookup"><span data-stu-id="8e54a-197">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                     |

<span data-ttu-id="8e54a-198">Esta tabela descreve as propriedades [do CartLineItem](cart-resources.md#cartlineitem) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="8e54a-198">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

|      <span data-ttu-id="8e54a-199">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8e54a-199">Property</span></span>       |            <span data-ttu-id="8e54a-200">Tipo</span><span class="sxs-lookup"><span data-stu-id="8e54a-200">Type</span></span>             | <span data-ttu-id="8e54a-201">Necessário</span><span class="sxs-lookup"><span data-stu-id="8e54a-201">Required</span></span> |                                                                                         <span data-ttu-id="8e54a-202">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e54a-202">Description</span></span>                                                                                         |
|---------------------|-----------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         <span data-ttu-id="8e54a-203">ID</span><span class="sxs-lookup"><span data-stu-id="8e54a-203">id</span></span>          |           <span data-ttu-id="8e54a-204">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="8e54a-204">string</span></span>            |    <span data-ttu-id="8e54a-205">No</span><span class="sxs-lookup"><span data-stu-id="8e54a-205">No</span></span>    |                                                     <span data-ttu-id="8e54a-206">Um identificador único para um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-206">A Unique identifier for a cart line item.</span></span> <span data-ttu-id="8e54a-207">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="8e54a-207">Applied upon successful creation of cart.</span></span>                                                     |
|      <span data-ttu-id="8e54a-208">catalogId</span><span class="sxs-lookup"><span data-stu-id="8e54a-208">catalogId</span></span>      |           <span data-ttu-id="8e54a-209">string</span><span class="sxs-lookup"><span data-stu-id="8e54a-209">string</span></span>            |   <span data-ttu-id="8e54a-210">Sim</span><span class="sxs-lookup"><span data-stu-id="8e54a-210">Yes</span></span>    |                                                                                <span data-ttu-id="8e54a-211">O identificador de artigos de catálogo.</span><span class="sxs-lookup"><span data-stu-id="8e54a-211">The catalog item identifier.</span></span>                                                                                 |
|    <span data-ttu-id="8e54a-212">nome amigável</span><span class="sxs-lookup"><span data-stu-id="8e54a-212">friendlyName</span></span>     |           <span data-ttu-id="8e54a-213">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="8e54a-213">string</span></span>            |    <span data-ttu-id="8e54a-214">No</span><span class="sxs-lookup"><span data-stu-id="8e54a-214">No</span></span>    |                                                    <span data-ttu-id="8e54a-215">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8e54a-215">Optional.</span></span> <span data-ttu-id="8e54a-216">O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="8e54a-216">The friendly name for the item defined by the partner to help disambiguate.</span></span>                                                    |
|      <span data-ttu-id="8e54a-217">quantidade</span><span class="sxs-lookup"><span data-stu-id="8e54a-217">quantity</span></span>       |             <span data-ttu-id="8e54a-218">int</span><span class="sxs-lookup"><span data-stu-id="8e54a-218">int</span></span>             |   <span data-ttu-id="8e54a-219">Sim</span><span class="sxs-lookup"><span data-stu-id="8e54a-219">Yes</span></span>    |                                                                            <span data-ttu-id="8e54a-220">O número de licenças ou instâncias.</span><span class="sxs-lookup"><span data-stu-id="8e54a-220">The number of licenses or instances.</span></span>                                                                             |
|    <span data-ttu-id="8e54a-221">currencyCode</span><span class="sxs-lookup"><span data-stu-id="8e54a-221">currencyCode</span></span>     |           <span data-ttu-id="8e54a-222">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="8e54a-222">string</span></span>            |    <span data-ttu-id="8e54a-223">No</span><span class="sxs-lookup"><span data-stu-id="8e54a-223">No</span></span>    |                                                                                     <span data-ttu-id="8e54a-224">O código da moeda.</span><span class="sxs-lookup"><span data-stu-id="8e54a-224">The currency code.</span></span>                                                                                      |
|    <span data-ttu-id="8e54a-225">billingCycle</span><span class="sxs-lookup"><span data-stu-id="8e54a-225">billingCycle</span></span>     |           <span data-ttu-id="8e54a-226">Objeto</span><span class="sxs-lookup"><span data-stu-id="8e54a-226">Object</span></span>            |   <span data-ttu-id="8e54a-227">Sim</span><span class="sxs-lookup"><span data-stu-id="8e54a-227">Yes</span></span>    |                                                                    <span data-ttu-id="8e54a-228">O tipo de ciclo de faturação definido para o período atual.</span><span class="sxs-lookup"><span data-stu-id="8e54a-228">The type of billing cycle set for the current period.</span></span>                                                                    |
|    <span data-ttu-id="8e54a-229">participantes</span><span class="sxs-lookup"><span data-stu-id="8e54a-229">participants</span></span>     | <span data-ttu-id="8e54a-230">Lista de pares de cordas de objeto</span><span class="sxs-lookup"><span data-stu-id="8e54a-230">List of Object String pairs</span></span> |    <span data-ttu-id="8e54a-231">Não</span><span class="sxs-lookup"><span data-stu-id="8e54a-231">No</span></span>    |                                                                <span data-ttu-id="8e54a-232">Uma coleção de PartnerId on Record (MPNID) na compra.</span><span class="sxs-lookup"><span data-stu-id="8e54a-232">A collection of PartnerId on Record (MPNID) on the purchase.</span></span>                                                                 |
| <span data-ttu-id="8e54a-233">provisionamentoContexto</span><span class="sxs-lookup"><span data-stu-id="8e54a-233">provisioningContext</span></span> | <span data-ttu-id="8e54a-234">Cadeia de<do dicionário,> de cordas</span><span class="sxs-lookup"><span data-stu-id="8e54a-234">Dictionary<string, string></span></span>  |    <span data-ttu-id="8e54a-235">Não</span><span class="sxs-lookup"><span data-stu-id="8e54a-235">No</span></span>    | <span data-ttu-id="8e54a-236">Informação necessária para o provisionamento de alguns itens no catálogo.</span><span class="sxs-lookup"><span data-stu-id="8e54a-236">Information required for provisioning for some items in the catalog.</span></span> <span data-ttu-id="8e54a-237">A propriedade de ProvisioningVariables num SKU indica quais propriedades são necessárias para itens específicos no catálogo.</span><span class="sxs-lookup"><span data-stu-id="8e54a-237">The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.</span></span> |
|     <span data-ttu-id="8e54a-238">orderGroup</span><span class="sxs-lookup"><span data-stu-id="8e54a-238">orderGroup</span></span>      |           <span data-ttu-id="8e54a-239">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="8e54a-239">string</span></span>            |    <span data-ttu-id="8e54a-240">No</span><span class="sxs-lookup"><span data-stu-id="8e54a-240">No</span></span>    |                                                                   <span data-ttu-id="8e54a-241">Um grupo para indicar quais os itens que podem ser colocados juntos.</span><span class="sxs-lookup"><span data-stu-id="8e54a-241">A group to indicate which items can be placed together.</span></span>                                                                   |
|        <span data-ttu-id="8e54a-242">erro</span><span class="sxs-lookup"><span data-stu-id="8e54a-242">error</span></span>        |           <span data-ttu-id="8e54a-243">Objeto</span><span class="sxs-lookup"><span data-stu-id="8e54a-243">Object</span></span>            |    <span data-ttu-id="8e54a-244">Não</span><span class="sxs-lookup"><span data-stu-id="8e54a-244">No</span></span>    |                                                                     <span data-ttu-id="8e54a-245">Aplicado após o carrinho é criado em caso de erro.</span><span class="sxs-lookup"><span data-stu-id="8e54a-245">Applied after cart is created in case of an error.</span></span>                                                                      |
|     <span data-ttu-id="8e54a-246">renovaTo</span><span class="sxs-lookup"><span data-stu-id="8e54a-246">renewsTo</span></span>        | <span data-ttu-id="8e54a-247">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="8e54a-247">Array of objects</span></span>            |    <span data-ttu-id="8e54a-248">Não</span><span class="sxs-lookup"><span data-stu-id="8e54a-248">No</span></span>    |                                                    <span data-ttu-id="8e54a-249">Uma variedade de [recursos Renovados.](cart-resources.md#renewsto)</span><span class="sxs-lookup"><span data-stu-id="8e54a-249">An array of [RenewsTo](cart-resources.md#renewsto) resources.</span></span>                                                                            |

<span data-ttu-id="8e54a-250">Esta tabela descreve as propriedades [Renovações](cart-resources.md#renewsto) No corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="8e54a-250">This table describes the [RenewsTo](cart-resources.md#renewsto) properties in the request body.</span></span>

| <span data-ttu-id="8e54a-251">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8e54a-251">Property</span></span>              | <span data-ttu-id="8e54a-252">Tipo</span><span class="sxs-lookup"><span data-stu-id="8e54a-252">Type</span></span>             | <span data-ttu-id="8e54a-253">Necessário</span><span class="sxs-lookup"><span data-stu-id="8e54a-253">Required</span></span>        | <span data-ttu-id="8e54a-254">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e54a-254">Description</span></span> |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8e54a-255">termoDuração</span><span class="sxs-lookup"><span data-stu-id="8e54a-255">termDuration</span></span>          | <span data-ttu-id="8e54a-256">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="8e54a-256">string</span></span>           | <span data-ttu-id="8e54a-257">No</span><span class="sxs-lookup"><span data-stu-id="8e54a-257">No</span></span>              | <span data-ttu-id="8e54a-258">Uma representação ISO 8601 da duração do período de renovação.</span><span class="sxs-lookup"><span data-stu-id="8e54a-258">An ISO 8601 representation of the renewal term's duration.</span></span> <span data-ttu-id="8e54a-259">Os valores suportados atuais são **P1M** (1 mês) e **P1Y** (1 ano).</span><span class="sxs-lookup"><span data-stu-id="8e54a-259">The current supported values are **P1M** (1 month) and **P1Y** (1 year).</span></span> |

### <a name="request-example"></a><span data-ttu-id="8e54a-260">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="8e54a-260">Request example</span></span>

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 496
Expect: 100-continue

{
  "lineItems": [
    {
    /* Microsoft Azure Subscription */
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1Y"
    },
    {
    /* Azure Reserved Instance */
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      }
    },
    {
    /* Azure Reserved Instance */
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "single"
      }
    },
    {
    /* Perpetual Software */
      "id": 3,
      "catalogItemId": "DG7GMGF0DWTL:0001:DG7GMGF0DSFM",
      "quantity": 1,
      "billingCycle": "one_time"
    },
    {
    /* SaaS */
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1M"
    },
  {
    /* SaaS Free Trial */
       "id": 5,
       "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
       "quantity": 10,
       "billingCycle": "none",
       "termDuration": "P1M",
       "renewsTo": {
         "termDuration": "P1Y"
       }
    }
  ]
}
```

## <a name="rest-response"></a><span data-ttu-id="8e54a-261">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="8e54a-261">REST response</span></span>

<span data-ttu-id="8e54a-262">Se for bem sucedido, este método devolve o recurso [cart](cart-resources.md) povoado no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="8e54a-262">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8e54a-263">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="8e54a-263">Response success and error codes</span></span>

<span data-ttu-id="8e54a-264">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="8e54a-264">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8e54a-265">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8e54a-265">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8e54a-266">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="8e54a-266">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8e54a-267">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="8e54a-267">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 764
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
X-Locale: en-US,en-US
MS-CV: sF/wRa2ih0CzbABc.0
MS-ServerId: 000001
Date: Thu, 15 Mar 2018 17:15:01 GMT
{
  "id": "3655b1a0-b1c9-4268-9824-577fdbc4d0be",
  "creationTimestamp": "2019-01-16T00:45:41.6062996Z",
  "lastModifiedTimestamp": "2019-01-16T00:45:41.6062996Z",
  "expirationTimestamp": "2019-01-16T01:00:54.4188497Z",
  "lastModifiedUser": "1824b7fc-2fac-4478-b177-66823c40ab75",
  "status": "Active",
  "lineItems": [
    {
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1Y",
      "orderGroup": "OMS-0"
    },
    {
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 3,
      "catalogItemId": "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "orderGroup": "0"
    },
    {
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1M",
      "orderGroup": "1"
    },
  {
      "id": 5,
      "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
      "quantity": 10,
      "currencyCode": "USD",
      "billingCycle": "none",
      "termDuration": "P1M",
      "renewsTo": {
  "termDuration": "P1Y"
      },
    "orderGroup": "2"
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/28045616-f6b9-462f-9701-0d89b5e65c44/carts/3655b1a0-b1c9-4268-9824-577fdbc4d0be",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Cart"
  }
}
```
