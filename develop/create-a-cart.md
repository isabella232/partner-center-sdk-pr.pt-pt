---
title: Criar um carrinho
description: Saiba como usar as APIs do Partner Center para adicionar um pedido para um cliente num carrinho. O tópico inclui informações sobre a criação de um carrinho e quaisquer pré-requisitos.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: dba54d4f6b97f3d0a51e2f87b32edca686466b89
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973779"
---
# <a name="create-a-cart-with-a-customer-order"></a><span data-ttu-id="383fa-104">Criar um carrinho com uma encomenda de cliente</span><span class="sxs-lookup"><span data-stu-id="383fa-104">Create a cart with a customer order</span></span>

<span data-ttu-id="383fa-105">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="383fa-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="383fa-106">Pode adicionar um pedido para um cliente num carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-106">You can add an order for a customer in a cart.</span></span> <span data-ttu-id="383fa-107">Para obter mais informações sobre o que está atualmente disponível para vender, consulte [as ofertas do Partner no programa Fornecedor de Soluções em Nuvem.](/partner-center/csp-offers)</span><span class="sxs-lookup"><span data-stu-id="383fa-107">For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="383fa-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="383fa-108">Prerequisites</span></span>

- <span data-ttu-id="383fa-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="383fa-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="383fa-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="383fa-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="383fa-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="383fa-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="383fa-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="383fa-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="383fa-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="383fa-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="383fa-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="383fa-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="383fa-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="383fa-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="383fa-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="383fa-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="383fa-117">C\#</span><span class="sxs-lookup"><span data-stu-id="383fa-117">C\#</span></span>

<span data-ttu-id="383fa-118">Para criar uma encomenda para um cliente:</span><span class="sxs-lookup"><span data-stu-id="383fa-118">To create an order for a customer:</span></span>

1. <span data-ttu-id="383fa-119">Instantiizar um objeto do Carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-119">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="383fa-120">Crie uma lista de objetos **CartLineItem** e atribua a lista à propriedade lineItems do carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-120">Create a list of **CartLineItem** objects, and assign the list to the cart's LineItems property.</span></span> <span data-ttu-id="383fa-121">Cada item da linha do carrinho contém a informação de compra de um produto.</span><span class="sxs-lookup"><span data-stu-id="383fa-121">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="383fa-122">Deve ter pelo menos um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-122">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="383fa-123">Obtenha uma interface para as operações de carrinhos ligando para o método **IAggregatePartner.Customers.ById** com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface da propriedade **Cart.**</span><span class="sxs-lookup"><span data-stu-id="383fa-123">Obtain an interface to cart operations by calling the **IAggregatePartner.Customers.ById** method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.</span></span>

4. <span data-ttu-id="383fa-124">Ligue para o método **Criar** ou **Criar** Para criar o carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-124">Call the **Create** or **CreateAsync** method to create the cart.</span></span>

### <a name="c-example"></a><span data-ttu-id="383fa-125">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="383fa-125">C\# example</span></span>

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

## <a name="java"></a><span data-ttu-id="383fa-126">Java</span><span class="sxs-lookup"><span data-stu-id="383fa-126">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="383fa-127">Para criar uma encomenda para um cliente:</span><span class="sxs-lookup"><span data-stu-id="383fa-127">To create an order for a customer:</span></span>

1. <span data-ttu-id="383fa-128">Instantiizar um objeto do Carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-128">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="383fa-129">Crie uma lista de objetos **CartLineItem** e atribua a lista aos itens de linha do carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-129">Create a list of **CartLineItem** objects, and assign the list to the cart's line items.</span></span> <span data-ttu-id="383fa-130">Cada item da linha do carrinho contém a informação de compra de um produto.</span><span class="sxs-lookup"><span data-stu-id="383fa-130">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="383fa-131">Deve ter pelo menos um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-131">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="383fa-132">Obtenha uma interface para as operações de carrinhos ligando para o **IAggregatePartner.getCustomers ().função byId** com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface da função **getCart.**</span><span class="sxs-lookup"><span data-stu-id="383fa-132">Obtain an interface to cart operations by calling the **IAggregatePartner.getCustomers().byId** function with the customer ID to identify the customer, and then retrieving the interface from the **getCart** function.</span></span>

4. <span data-ttu-id="383fa-133">Ligue para a função **criar** o carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-133">Call the **create** function to create the cart.</span></span>

## <a name="java-example"></a><span data-ttu-id="383fa-134">Exemplo de Java</span><span class="sxs-lookup"><span data-stu-id="383fa-134">Java example</span></span>

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

## <a name="powershell"></a><span data-ttu-id="383fa-135">PowerShell</span><span class="sxs-lookup"><span data-stu-id="383fa-135">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="383fa-136">Para criar uma encomenda para um cliente:</span><span class="sxs-lookup"><span data-stu-id="383fa-136">To create an order for a customer:</span></span>

1. <span data-ttu-id="383fa-137">Instantiizar um objeto do Carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-137">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="383fa-138">Crie uma lista de objetos **CartLineItem** e atribua a lista aos itens de linha do carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-138">Create a list of **CartLineItem** objects, and assign the list to the cart's line items.</span></span> <span data-ttu-id="383fa-139">Cada item da linha do carrinho contém a informação de compra de um produto.</span><span class="sxs-lookup"><span data-stu-id="383fa-139">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="383fa-140">Deve ter pelo menos um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-140">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="383fa-141">Execute o comando [**New PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) para criar o carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-141">Execute the [**New-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) command to create the cart.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="383fa-142">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="383fa-142">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="383fa-143">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="383fa-143">Request syntax</span></span>

| <span data-ttu-id="383fa-144">Método</span><span class="sxs-lookup"><span data-stu-id="383fa-144">Method</span></span>   | <span data-ttu-id="383fa-145">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="383fa-145">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="383fa-146">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="383fa-146">**POST**</span></span> | <span data-ttu-id="383fa-147">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="383fa-147">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span></span>                        |

### <a name="uri-parameter"></a><span data-ttu-id="383fa-148">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="383fa-148">URI parameter</span></span>

<span data-ttu-id="383fa-149">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="383fa-149">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="383fa-150">Nome</span><span class="sxs-lookup"><span data-stu-id="383fa-150">Name</span></span>            | <span data-ttu-id="383fa-151">Tipo</span><span class="sxs-lookup"><span data-stu-id="383fa-151">Type</span></span>     | <span data-ttu-id="383fa-152">Necessário</span><span class="sxs-lookup"><span data-stu-id="383fa-152">Required</span></span> | <span data-ttu-id="383fa-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="383fa-153">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="383fa-154">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="383fa-154">**customer-id**</span></span> | <span data-ttu-id="383fa-155">string</span><span class="sxs-lookup"><span data-stu-id="383fa-155">string</span></span>   | <span data-ttu-id="383fa-156">Yes</span><span class="sxs-lookup"><span data-stu-id="383fa-156">Yes</span></span>      | <span data-ttu-id="383fa-157">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="383fa-157">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="383fa-158">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="383fa-158">Request headers</span></span>

<span data-ttu-id="383fa-159">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="383fa-159">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="383fa-160">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="383fa-160">Request body</span></span>

<span data-ttu-id="383fa-161">Esta tabela descreve as propriedades do [Carrinho](cart-resources.md) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="383fa-161">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="383fa-162">Propriedade</span><span class="sxs-lookup"><span data-stu-id="383fa-162">Property</span></span>              | <span data-ttu-id="383fa-163">Tipo</span><span class="sxs-lookup"><span data-stu-id="383fa-163">Type</span></span>             | <span data-ttu-id="383fa-164">Necessário</span><span class="sxs-lookup"><span data-stu-id="383fa-164">Required</span></span>        | <span data-ttu-id="383fa-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="383fa-165">Description</span></span> |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="383fa-166">ID</span><span class="sxs-lookup"><span data-stu-id="383fa-166">id</span></span>                    | <span data-ttu-id="383fa-167">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="383fa-167">string</span></span>           | <span data-ttu-id="383fa-168">No</span><span class="sxs-lookup"><span data-stu-id="383fa-168">No</span></span>              | <span data-ttu-id="383fa-169">Um identificador de carrinhos que é fornecido após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-169">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="383fa-170">criaçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="383fa-170">creationTimeStamp</span></span>     | <span data-ttu-id="383fa-171">DateTime</span><span class="sxs-lookup"><span data-stu-id="383fa-171">DateTime</span></span>         | <span data-ttu-id="383fa-172">No</span><span class="sxs-lookup"><span data-stu-id="383fa-172">No</span></span>              | <span data-ttu-id="383fa-173">A data em que o carrinho foi criado, em formato de data- hora.</span><span class="sxs-lookup"><span data-stu-id="383fa-173">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="383fa-174">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-174">Applied upon successful creation of the cart.</span></span>         |
| <span data-ttu-id="383fa-175">últimampadatimestamp de Tempos</span><span class="sxs-lookup"><span data-stu-id="383fa-175">lastModifiedTimeStamp</span></span> | <span data-ttu-id="383fa-176">DateTime</span><span class="sxs-lookup"><span data-stu-id="383fa-176">DateTime</span></span>         | <span data-ttu-id="383fa-177">No</span><span class="sxs-lookup"><span data-stu-id="383fa-177">No</span></span>              | <span data-ttu-id="383fa-178">A data em que o carrinho foi atualizado pela última vez, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="383fa-178">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="383fa-179">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-179">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="383fa-180">expiraçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="383fa-180">expirationTimeStamp</span></span>   | <span data-ttu-id="383fa-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="383fa-181">DateTime</span></span>         | <span data-ttu-id="383fa-182">No</span><span class="sxs-lookup"><span data-stu-id="383fa-182">No</span></span>              | <span data-ttu-id="383fa-183">A data em que o carrinho expirará, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="383fa-183">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="383fa-184">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-184">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="383fa-185">últimoModifiedUser</span><span class="sxs-lookup"><span data-stu-id="383fa-185">lastModifiedUser</span></span>      | <span data-ttu-id="383fa-186">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="383fa-186">string</span></span>           | <span data-ttu-id="383fa-187">No</span><span class="sxs-lookup"><span data-stu-id="383fa-187">No</span></span>              | <span data-ttu-id="383fa-188">O utilizador que atualizou pela última vez o carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-188">The user who last updated the cart.</span></span> <span data-ttu-id="383fa-189">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-189">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="383fa-190">lineitems</span><span class="sxs-lookup"><span data-stu-id="383fa-190">lineItems</span></span>             | <span data-ttu-id="383fa-191">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="383fa-191">Array of objects</span></span> | <span data-ttu-id="383fa-192">Yes</span><span class="sxs-lookup"><span data-stu-id="383fa-192">Yes</span></span>             | <span data-ttu-id="383fa-193">Uma matriz de recursos [CartLineItem.](cart-resources.md#cartlineitem)</span><span class="sxs-lookup"><span data-stu-id="383fa-193">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                     |

<span data-ttu-id="383fa-194">Esta tabela descreve as propriedades [do CartLineItem](cart-resources.md#cartlineitem) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="383fa-194">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

|      <span data-ttu-id="383fa-195">Propriedade</span><span class="sxs-lookup"><span data-stu-id="383fa-195">Property</span></span>       |            <span data-ttu-id="383fa-196">Tipo</span><span class="sxs-lookup"><span data-stu-id="383fa-196">Type</span></span>             | <span data-ttu-id="383fa-197">Necessário</span><span class="sxs-lookup"><span data-stu-id="383fa-197">Required</span></span> |                                                                                         <span data-ttu-id="383fa-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="383fa-198">Description</span></span>                                                                                         |
|---------------------|-----------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         <span data-ttu-id="383fa-199">ID</span><span class="sxs-lookup"><span data-stu-id="383fa-199">id</span></span>          |           <span data-ttu-id="383fa-200">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="383fa-200">string</span></span>            |    <span data-ttu-id="383fa-201">No</span><span class="sxs-lookup"><span data-stu-id="383fa-201">No</span></span>    |                                                     <span data-ttu-id="383fa-202">Um identificador único para um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-202">A unique identifier for a cart line item.</span></span> <span data-ttu-id="383fa-203">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="383fa-203">Applied upon successful creation of cart.</span></span>                                                     |
|      <span data-ttu-id="383fa-204">catalogId</span><span class="sxs-lookup"><span data-stu-id="383fa-204">catalogId</span></span>      |           <span data-ttu-id="383fa-205">string</span><span class="sxs-lookup"><span data-stu-id="383fa-205">string</span></span>            |   <span data-ttu-id="383fa-206">Yes</span><span class="sxs-lookup"><span data-stu-id="383fa-206">Yes</span></span>    |                                                                                <span data-ttu-id="383fa-207">O identificador de artigos de catálogo.</span><span class="sxs-lookup"><span data-stu-id="383fa-207">The catalog item identifier.</span></span>                                                                                 |
|    <span data-ttu-id="383fa-208">nome amigável</span><span class="sxs-lookup"><span data-stu-id="383fa-208">friendlyName</span></span>     |           <span data-ttu-id="383fa-209">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="383fa-209">string</span></span>            |    <span data-ttu-id="383fa-210">No</span><span class="sxs-lookup"><span data-stu-id="383fa-210">No</span></span>    |                                                    <span data-ttu-id="383fa-211">Opcional.</span><span class="sxs-lookup"><span data-stu-id="383fa-211">Optional.</span></span> <span data-ttu-id="383fa-212">O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="383fa-212">The friendly name for the item defined by the partner to help disambiguate.</span></span>                                                    |
|      <span data-ttu-id="383fa-213">quantidade</span><span class="sxs-lookup"><span data-stu-id="383fa-213">quantity</span></span>       |             <span data-ttu-id="383fa-214">int</span><span class="sxs-lookup"><span data-stu-id="383fa-214">int</span></span>             |   <span data-ttu-id="383fa-215">Yes</span><span class="sxs-lookup"><span data-stu-id="383fa-215">Yes</span></span>    |                                                                            <span data-ttu-id="383fa-216">O número de licenças ou instâncias.</span><span class="sxs-lookup"><span data-stu-id="383fa-216">The number of licenses or instances.</span></span>                                                                             |
|    <span data-ttu-id="383fa-217">currencyCode</span><span class="sxs-lookup"><span data-stu-id="383fa-217">currencyCode</span></span>     |           <span data-ttu-id="383fa-218">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="383fa-218">string</span></span>            |    <span data-ttu-id="383fa-219">No</span><span class="sxs-lookup"><span data-stu-id="383fa-219">No</span></span>    |                                                                                     <span data-ttu-id="383fa-220">O código da moeda.</span><span class="sxs-lookup"><span data-stu-id="383fa-220">The currency code.</span></span>                                                                                      |
|    <span data-ttu-id="383fa-221">billingCycle</span><span class="sxs-lookup"><span data-stu-id="383fa-221">billingCycle</span></span>     |           <span data-ttu-id="383fa-222">Objeto</span><span class="sxs-lookup"><span data-stu-id="383fa-222">Object</span></span>            |   <span data-ttu-id="383fa-223">Yes</span><span class="sxs-lookup"><span data-stu-id="383fa-223">Yes</span></span>    |                                                                    <span data-ttu-id="383fa-224">O tipo de ciclo de faturação definido para o período atual.</span><span class="sxs-lookup"><span data-stu-id="383fa-224">The type of billing cycle set for the current period.</span></span>                                                                    |
|    <span data-ttu-id="383fa-225">participantes</span><span class="sxs-lookup"><span data-stu-id="383fa-225">participants</span></span>     | <span data-ttu-id="383fa-226">Lista de pares de cordas de objeto</span><span class="sxs-lookup"><span data-stu-id="383fa-226">List of Object String pairs</span></span> |    <span data-ttu-id="383fa-227">No</span><span class="sxs-lookup"><span data-stu-id="383fa-227">No</span></span>    |                                                                <span data-ttu-id="383fa-228">Uma coleção de PartnerId on Record (MPNID) na compra.</span><span class="sxs-lookup"><span data-stu-id="383fa-228">A collection of PartnerId on Record (MPNID) on the purchase.</span></span>                                                                 |
| <span data-ttu-id="383fa-229">provisionamentoContexto</span><span class="sxs-lookup"><span data-stu-id="383fa-229">provisioningContext</span></span> | <span data-ttu-id="383fa-230">Cadeia de<do dicionário,> de cordas</span><span class="sxs-lookup"><span data-stu-id="383fa-230">Dictionary<string, string></span></span>  |    <span data-ttu-id="383fa-231">No</span><span class="sxs-lookup"><span data-stu-id="383fa-231">No</span></span>    | <span data-ttu-id="383fa-232">Informação necessária para o provisionamento de alguns itens no catálogo.</span><span class="sxs-lookup"><span data-stu-id="383fa-232">Information required for provisioning for some items in the catalog.</span></span> <span data-ttu-id="383fa-233">A propriedade de ProvisioningVariables num SKU indica quais propriedades são necessárias para itens específicos no catálogo.</span><span class="sxs-lookup"><span data-stu-id="383fa-233">The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.</span></span> |
|     <span data-ttu-id="383fa-234">orderGroup</span><span class="sxs-lookup"><span data-stu-id="383fa-234">orderGroup</span></span>      |           <span data-ttu-id="383fa-235">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="383fa-235">string</span></span>            |    <span data-ttu-id="383fa-236">No</span><span class="sxs-lookup"><span data-stu-id="383fa-236">No</span></span>    |                                                                   <span data-ttu-id="383fa-237">Um grupo para indicar quais os itens que podem ser colocados juntos.</span><span class="sxs-lookup"><span data-stu-id="383fa-237">A group to indicate which items can be placed together.</span></span>                                                                   |
|        <span data-ttu-id="383fa-238">erro</span><span class="sxs-lookup"><span data-stu-id="383fa-238">error</span></span>        |           <span data-ttu-id="383fa-239">Objeto</span><span class="sxs-lookup"><span data-stu-id="383fa-239">Object</span></span>            |    <span data-ttu-id="383fa-240">No</span><span class="sxs-lookup"><span data-stu-id="383fa-240">No</span></span>    |                                                                     <span data-ttu-id="383fa-241">Aplicado após o carrinho é criado se houver um erro.</span><span class="sxs-lookup"><span data-stu-id="383fa-241">Applied after cart is created if there is an error.</span></span>                                                                      |
|     <span data-ttu-id="383fa-242">renovaTo</span><span class="sxs-lookup"><span data-stu-id="383fa-242">renewsTo</span></span>        | <span data-ttu-id="383fa-243">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="383fa-243">Array of objects</span></span>            |    <span data-ttu-id="383fa-244">No</span><span class="sxs-lookup"><span data-stu-id="383fa-244">No</span></span>    |                                                    <span data-ttu-id="383fa-245">Uma variedade de [recursos Renovados.](cart-resources.md#renewsto)</span><span class="sxs-lookup"><span data-stu-id="383fa-245">An array of [RenewsTo](cart-resources.md#renewsto) resources.</span></span>                                                                            |

<span data-ttu-id="383fa-246">Esta tabela descreve as propriedades [Renovações](cart-resources.md#renewsto) No corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="383fa-246">This table describes the [RenewsTo](cart-resources.md#renewsto) properties in the request body.</span></span>

| <span data-ttu-id="383fa-247">Propriedade</span><span class="sxs-lookup"><span data-stu-id="383fa-247">Property</span></span>              | <span data-ttu-id="383fa-248">Tipo</span><span class="sxs-lookup"><span data-stu-id="383fa-248">Type</span></span>             | <span data-ttu-id="383fa-249">Necessário</span><span class="sxs-lookup"><span data-stu-id="383fa-249">Required</span></span>        | <span data-ttu-id="383fa-250">Descrição</span><span class="sxs-lookup"><span data-stu-id="383fa-250">Description</span></span> |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="383fa-251">termoDuração</span><span class="sxs-lookup"><span data-stu-id="383fa-251">termDuration</span></span>          | <span data-ttu-id="383fa-252">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="383fa-252">string</span></span>           | <span data-ttu-id="383fa-253">No</span><span class="sxs-lookup"><span data-stu-id="383fa-253">No</span></span>              | <span data-ttu-id="383fa-254">Uma representação ISO 8601 da duração do período de renovação.</span><span class="sxs-lookup"><span data-stu-id="383fa-254">An ISO 8601 representation of the renewal term's duration.</span></span> <span data-ttu-id="383fa-255">Os valores suportados atuais são **P1M** (1 mês) e **P1Y** (1 ano).</span><span class="sxs-lookup"><span data-stu-id="383fa-255">The current supported values are **P1M** (1 month) and **P1Y** (1 year).</span></span> |

### <a name="request-example"></a><span data-ttu-id="383fa-256">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="383fa-256">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="383fa-257">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="383fa-257">REST response</span></span>

<span data-ttu-id="383fa-258">Se for bem sucedido, este método devolve o recurso [cart](cart-resources.md) povoado no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="383fa-258">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="383fa-259">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="383fa-259">Response success and error codes</span></span>

<span data-ttu-id="383fa-260">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="383fa-260">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="383fa-261">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="383fa-261">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="383fa-262">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="383fa-262">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="383fa-263">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="383fa-263">Response example</span></span>

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
