---
title: Criar um carrinho com suplementos
description: Saiba como utilizar as APIs do Partner Center para adicionar uma encomenda de clientes com suplementos através de um carrinho. O artigo partilha pré-requisitos e passos para criar um carrinho com suplementos.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 81c41405a2f56eb4d1d3447d14b93e05d550cc70
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770130"
---
# <a name="create-a-cart-with-add-ons-to-a-customer-order"></a><span data-ttu-id="aeb72-104">Criar um carrinho com suplementos a uma encomenda de clientes</span><span class="sxs-lookup"><span data-stu-id="aeb72-104">Create a cart with add-ons to a customer order</span></span>

<span data-ttu-id="aeb72-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="aeb72-105">**Applies to:**</span></span>

- <span data-ttu-id="aeb72-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="aeb72-106">Partner Center</span></span>

<span data-ttu-id="aeb72-107">Pode comprar suplementos através de um carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-107">You can purchase add-ons through a cart.</span></span> <span data-ttu-id="aeb72-108">Para obter mais informações sobre o que está atualmente disponível para vender, consulte [as ofertas do Partner no programa Cloud Solution Provider](/partner-center/csp-offers).</span><span class="sxs-lookup"><span data-stu-id="aeb72-108">For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aeb72-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="aeb72-109">Prerequisites</span></span>

- <span data-ttu-id="aeb72-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="aeb72-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="aeb72-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="aeb72-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="aeb72-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="aeb72-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="aeb72-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="aeb72-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="aeb72-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="aeb72-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="aeb72-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="aeb72-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="aeb72-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="aeb72-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="aeb72-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="aeb72-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="aeb72-118">C\#</span><span class="sxs-lookup"><span data-stu-id="aeb72-118">C\#</span></span>

<span data-ttu-id="aeb72-119">Um carrinho permite a compra de uma oferta base e os seus suplementos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="aeb72-119">A cart enables the purchase of a base offer and its corresponding add-ons.</span></span> <span data-ttu-id="aeb72-120">Siga estes passos para criar um carrinho:</span><span class="sxs-lookup"><span data-stu-id="aeb72-120">Follow these steps to create a cart:</span></span>

1. <span data-ttu-id="aeb72-121">Instantiizar um objeto [**do Carrinho.**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart)</span><span class="sxs-lookup"><span data-stu-id="aeb72-121">Instantiate a [**Cart**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart) object.</span></span>

2. <span data-ttu-id="aeb72-122">Crie uma lista de objetos [**CartLineItem**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) que representam a(s) oferta base, e atribua a lista à propriedade [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) do carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-122">Create a list of [**CartLineItem**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) objects which represent the base offer(s), and assign the list to the cart's [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) property.</span></span>

3. <span data-ttu-id="aeb72-123">Sob o item da linha de cada oferta base, povoar a lista de **AddOnItems com outros objetos** **CartLineItem** que cada um representa um addon que será comprado contra essa oferta base.</span><span class="sxs-lookup"><span data-stu-id="aeb72-123">Under each base offer's cart line item, populate the list of **AddOnItems** with other **CartLineItem** objects that each represent an add-on that will be purchased against that base offer.</span></span>

4. <span data-ttu-id="aeb72-124">Obtenha uma interface para as operações de carrinhos utilizando o [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) para ligar para o método [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface da propriedade **Cart.**</span><span class="sxs-lookup"><span data-stu-id="aeb72-124">Obtain an interface to cart operations by using [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) to call the [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.</span></span>

5. <span data-ttu-id="aeb72-125">Por fim, ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) ou [**Criar Async**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) para criar o carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-125">Finally, call the [**Create**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) method to create the cart.</span></span>

### <a name="c-example"></a><span data-ttu-id="aeb72-126">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="aeb72-126">C\# example</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "A_base_offer_ID",
                FriendlyName = "Myofferpurchase",
                Quantity = 3,
                BillingCycle = BillingCycleType.Monthly,
                AddonItems = new List<CartLineItem>
                {
                    new CartLineItem
                    {
                        Id = 1,
                        CatalogItemId = "An_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 2,
                    },
                    new CartLineItem
                    {
                        Id = 2,
                        CatalogItemId = "Another_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 3
                    }
                }
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

<span data-ttu-id="aeb72-127">Siga estas medidas para criar um carrinho que permita a compra de complementos(s) contra subscrições de base existentes):</span><span class="sxs-lookup"><span data-stu-id="aeb72-127">Follow these steps to create a cart which will enable the purchase of add-on(s) against existing base subscription(s):</span></span>

1. <span data-ttu-id="aeb72-128">Crie um **Carrinho** com um novo **CartLineItem** contendo o ID de subscrição na propriedade **ProvisioningContext** com a chave "ParentSubscriptionId".</span><span class="sxs-lookup"><span data-stu-id="aeb72-128">Create a **Cart** with a new **CartLineItem** containing the subscription ID in the **ProvisioningContext** property with key "ParentSubscriptionId".</span></span>

2. <span data-ttu-id="aeb72-129">Chame o método **Criar** ou **Criar Async.**</span><span class="sxs-lookup"><span data-stu-id="aeb72-129">Call the **Create** or **CreateAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "An_addon_item_ID",
                ProvisioningContext = new Dictionary<string, string>
                {
                    {
                        "ParentSubscriptionId", "An_existing_subscription_Id"
                    }
                },
                Quantity = 1,
                BillingCycle = BillingCycleType.Annual,
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(selectedCustomerId).Carts.Create(cart);
```

## <a name="rest-request"></a><span data-ttu-id="aeb72-130">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="aeb72-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="aeb72-131">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="aeb72-131">Request syntax</span></span>

| <span data-ttu-id="aeb72-132">Método</span><span class="sxs-lookup"><span data-stu-id="aeb72-132">Method</span></span>   | <span data-ttu-id="aeb72-133">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="aeb72-133">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="aeb72-134">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="aeb72-134">**POST**</span></span> | <span data-ttu-id="aeb72-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="aeb72-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span></span>                        |

#### <a name="uri-parameter"></a><span data-ttu-id="aeb72-136">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="aeb72-136">URI parameter</span></span>

<span data-ttu-id="aeb72-137">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="aeb72-137">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="aeb72-138">Nome</span><span class="sxs-lookup"><span data-stu-id="aeb72-138">Name</span></span>            | <span data-ttu-id="aeb72-139">Tipo</span><span class="sxs-lookup"><span data-stu-id="aeb72-139">Type</span></span>     | <span data-ttu-id="aeb72-140">Necessário</span><span class="sxs-lookup"><span data-stu-id="aeb72-140">Required</span></span> | <span data-ttu-id="aeb72-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="aeb72-141">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="aeb72-142">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="aeb72-142">**customer-id**</span></span> | <span data-ttu-id="aeb72-143">string</span><span class="sxs-lookup"><span data-stu-id="aeb72-143">string</span></span>   | <span data-ttu-id="aeb72-144">Sim</span><span class="sxs-lookup"><span data-stu-id="aeb72-144">Yes</span></span>      | <span data-ttu-id="aeb72-145">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="aeb72-145">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="aeb72-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="aeb72-146">Request headers</span></span>

<span data-ttu-id="aeb72-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="aeb72-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="aeb72-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="aeb72-148">Request body</span></span>

<span data-ttu-id="aeb72-149">Esta tabela descreve as propriedades do [Carrinho](cart-resources.md) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="aeb72-149">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="aeb72-150">Propriedade</span><span class="sxs-lookup"><span data-stu-id="aeb72-150">Property</span></span>              | <span data-ttu-id="aeb72-151">Tipo</span><span class="sxs-lookup"><span data-stu-id="aeb72-151">Type</span></span>             | <span data-ttu-id="aeb72-152">Necessário</span><span class="sxs-lookup"><span data-stu-id="aeb72-152">Required</span></span>        | <span data-ttu-id="aeb72-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="aeb72-153">Description</span></span> |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="aeb72-154">ID</span><span class="sxs-lookup"><span data-stu-id="aeb72-154">id</span></span>                    | <span data-ttu-id="aeb72-155">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="aeb72-155">string</span></span>           | <span data-ttu-id="aeb72-156">No</span><span class="sxs-lookup"><span data-stu-id="aeb72-156">No</span></span>              | <span data-ttu-id="aeb72-157">Um identificador de carrinhos que é fornecido após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-157">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="aeb72-158">criaçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="aeb72-158">creationTimeStamp</span></span>     | <span data-ttu-id="aeb72-159">DateTime</span><span class="sxs-lookup"><span data-stu-id="aeb72-159">DateTime</span></span>         | <span data-ttu-id="aeb72-160">Não</span><span class="sxs-lookup"><span data-stu-id="aeb72-160">No</span></span>              | <span data-ttu-id="aeb72-161">A data em que o carrinho foi criado, em formato de data- hora.</span><span class="sxs-lookup"><span data-stu-id="aeb72-161">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="aeb72-162">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-162">Applied upon successful creation of the cart.</span></span>         |
| <span data-ttu-id="aeb72-163">últimampadatimestamp de Tempos</span><span class="sxs-lookup"><span data-stu-id="aeb72-163">lastModifiedTimeStamp</span></span> | <span data-ttu-id="aeb72-164">DateTime</span><span class="sxs-lookup"><span data-stu-id="aeb72-164">DateTime</span></span>         | <span data-ttu-id="aeb72-165">Não</span><span class="sxs-lookup"><span data-stu-id="aeb72-165">No</span></span>              | <span data-ttu-id="aeb72-166">A data em que o carrinho foi atualizado pela última vez, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="aeb72-166">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="aeb72-167">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-167">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="aeb72-168">expiraçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="aeb72-168">expirationTimeStamp</span></span>   | <span data-ttu-id="aeb72-169">DateTime</span><span class="sxs-lookup"><span data-stu-id="aeb72-169">DateTime</span></span>         | <span data-ttu-id="aeb72-170">Não</span><span class="sxs-lookup"><span data-stu-id="aeb72-170">No</span></span>              | <span data-ttu-id="aeb72-171">A data em que o carrinho expirará, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="aeb72-171">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="aeb72-172">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-172">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="aeb72-173">últimoModifiedUser</span><span class="sxs-lookup"><span data-stu-id="aeb72-173">lastModifiedUser</span></span>      | <span data-ttu-id="aeb72-174">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="aeb72-174">string</span></span>           | <span data-ttu-id="aeb72-175">No</span><span class="sxs-lookup"><span data-stu-id="aeb72-175">No</span></span>              | <span data-ttu-id="aeb72-176">O utilizador que atualizou pela última vez o carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-176">The user who last updated the cart.</span></span> <span data-ttu-id="aeb72-177">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-177">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="aeb72-178">lineitems</span><span class="sxs-lookup"><span data-stu-id="aeb72-178">lineItems</span></span>             | <span data-ttu-id="aeb72-179">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="aeb72-179">Array of objects</span></span> | <span data-ttu-id="aeb72-180">Sim</span><span class="sxs-lookup"><span data-stu-id="aeb72-180">Yes</span></span>             | <span data-ttu-id="aeb72-181">Uma matriz de recursos [CartLineItem.](cart-resources.md#cartlineitem)</span><span class="sxs-lookup"><span data-stu-id="aeb72-181">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                             |

<span data-ttu-id="aeb72-182">Esta tabela descreve as propriedades [do CartLineItem](cart-resources.md#cartlineitem) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="aeb72-182">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

| <span data-ttu-id="aeb72-183">Propriedade</span><span class="sxs-lookup"><span data-stu-id="aeb72-183">Property</span></span>             | <span data-ttu-id="aeb72-184">Tipo</span><span class="sxs-lookup"><span data-stu-id="aeb72-184">Type</span></span>                             | <span data-ttu-id="aeb72-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="aeb72-185">Description</span></span>                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="aeb72-186">ID</span><span class="sxs-lookup"><span data-stu-id="aeb72-186">id</span></span>                   | <span data-ttu-id="aeb72-187">string</span><span class="sxs-lookup"><span data-stu-id="aeb72-187">string</span></span>                           | <span data-ttu-id="aeb72-188">Um identificador único para um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-188">A unique identifier for a cart line item.</span></span> <span data-ttu-id="aeb72-189">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="aeb72-189">Applied upon successful creation of cart.</span></span>                                                                   |
| <span data-ttu-id="aeb72-190">catalogId</span><span class="sxs-lookup"><span data-stu-id="aeb72-190">catalogId</span></span>            | <span data-ttu-id="aeb72-191">string</span><span class="sxs-lookup"><span data-stu-id="aeb72-191">string</span></span>                           | <span data-ttu-id="aeb72-192">O identificador de artigos de catálogo.</span><span class="sxs-lookup"><span data-stu-id="aeb72-192">The catalog item identifier.</span></span>                                                                                                                          |
| <span data-ttu-id="aeb72-193">nome amigável</span><span class="sxs-lookup"><span data-stu-id="aeb72-193">friendlyName</span></span>         | <span data-ttu-id="aeb72-194">string</span><span class="sxs-lookup"><span data-stu-id="aeb72-194">string</span></span>                           | <span data-ttu-id="aeb72-195">Opcional.</span><span class="sxs-lookup"><span data-stu-id="aeb72-195">Optional.</span></span> <span data-ttu-id="aeb72-196">O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="aeb72-196">The friendly name for the item defined by the partner to help disambiguate.</span></span>                                                                 |
| <span data-ttu-id="aeb72-197">quantidade</span><span class="sxs-lookup"><span data-stu-id="aeb72-197">quantity</span></span>             | <span data-ttu-id="aeb72-198">int</span><span class="sxs-lookup"><span data-stu-id="aeb72-198">int</span></span>                              | <span data-ttu-id="aeb72-199">O número de licenças ou instâncias.</span><span class="sxs-lookup"><span data-stu-id="aeb72-199">The number of licenses or instances.</span></span>                                                                                                                  |
| <span data-ttu-id="aeb72-200">currencyCode</span><span class="sxs-lookup"><span data-stu-id="aeb72-200">currencyCode</span></span>         | <span data-ttu-id="aeb72-201">string</span><span class="sxs-lookup"><span data-stu-id="aeb72-201">string</span></span>                           | <span data-ttu-id="aeb72-202">O código da moeda.</span><span class="sxs-lookup"><span data-stu-id="aeb72-202">The currency code.</span></span>                                                                                                                                    |
| <span data-ttu-id="aeb72-203">billingCycle</span><span class="sxs-lookup"><span data-stu-id="aeb72-203">billingCycle</span></span>         | <span data-ttu-id="aeb72-204">Objeto</span><span class="sxs-lookup"><span data-stu-id="aeb72-204">Object</span></span>                           | <span data-ttu-id="aeb72-205">O tipo de ciclo de faturação definido para o período atual.</span><span class="sxs-lookup"><span data-stu-id="aeb72-205">The type of billing cycle set for the current period.</span></span>                                                                                                 |
| <span data-ttu-id="aeb72-206">participantes</span><span class="sxs-lookup"><span data-stu-id="aeb72-206">participants</span></span>         | <span data-ttu-id="aeb72-207">Lista de pares de cordas de objeto</span><span class="sxs-lookup"><span data-stu-id="aeb72-207">List of Object String pairs</span></span>      | <span data-ttu-id="aeb72-208">Uma coleção de PartnerId on Record (MPNID) na compra.</span><span class="sxs-lookup"><span data-stu-id="aeb72-208">A collection of PartnerId on Record (MPNID) on the purchase.</span></span>                                                                                          |
| <span data-ttu-id="aeb72-209">provisionamentoContexto</span><span class="sxs-lookup"><span data-stu-id="aeb72-209">provisioningContext</span></span>  | <span data-ttu-id="aeb72-210">Cadeia de<do dicionário,> de cordas</span><span class="sxs-lookup"><span data-stu-id="aeb72-210">Dictionary<string, string></span></span>       | <span data-ttu-id="aeb72-211">Um contexto utilizado para o provisionamento da oferta.</span><span class="sxs-lookup"><span data-stu-id="aeb72-211">A context used for provisioning of offer.</span></span>                                                                                                             |
| <span data-ttu-id="aeb72-212">orderGroup</span><span class="sxs-lookup"><span data-stu-id="aeb72-212">orderGroup</span></span>           | <span data-ttu-id="aeb72-213">string</span><span class="sxs-lookup"><span data-stu-id="aeb72-213">string</span></span>                           | <span data-ttu-id="aeb72-214">Um grupo para indicar quais os itens que podem ser colocados juntos.</span><span class="sxs-lookup"><span data-stu-id="aeb72-214">A group to indicate which items can be placed together.</span></span>                                                                                               |
| <span data-ttu-id="aeb72-215">addonItems</span><span class="sxs-lookup"><span data-stu-id="aeb72-215">addonItems</span></span>           | <span data-ttu-id="aeb72-216">Lista de **objetos CartLineItem**</span><span class="sxs-lookup"><span data-stu-id="aeb72-216">List of **CartLineItem** objects</span></span> | <span data-ttu-id="aeb72-217">Uma coleção de itens de linha de carrinhos para addons que serão adquiridos para a subscrição base que resulta da compra do item da linha do carrinho dos pais.</span><span class="sxs-lookup"><span data-stu-id="aeb72-217">A collection of cart line items for add-ons that will be purchased towards the base subscription that results from the parent cart line item's purchase.</span></span> |
| <span data-ttu-id="aeb72-218">erro</span><span class="sxs-lookup"><span data-stu-id="aeb72-218">error</span></span>                | <span data-ttu-id="aeb72-219">Objeto</span><span class="sxs-lookup"><span data-stu-id="aeb72-219">Object</span></span>                           | <span data-ttu-id="aeb72-220">Aplicado após o carrinho é criado em caso de erro.</span><span class="sxs-lookup"><span data-stu-id="aeb72-220">Applied after cart is created in case of an error.</span></span>                                                                                                    |

### <a name="request-example-new-base-subscription"></a><span data-ttu-id="aeb72-221">Exemplo de pedido (nova subscrição base)</span><span class="sxs-lookup"><span data-stu-id="aeb72-221">Request example (new base subscription)</span></span>

<span data-ttu-id="aeb72-222">O exemplo REST que se segue mostra como criar um carrinho com itens adicionais para uma nova subscrição base.</span><span class="sxs-lookup"><span data-stu-id="aeb72-222">The following REST example shows how to create a cart with add-on items for a new base subscription.</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "FriendlyName":"Myofferpurchase",
            "Quantity":3,
            "BillingCycle":"monthly",
            "AddonItems": [
                {
                    "Id":1,
                    "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "Quantity":2,
                    "BillingCycle":"monthly"
                },
                {
                    "Id":2,
                    "CatalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "Quantity":3,
                    "BillingCycle":"monthly"
                }
            ]
        }
    ]
}
```

#### <a name="request-example-existing-base-subscription"></a><span data-ttu-id="aeb72-223">Exemplo de pedido (subscrição base existente)</span><span class="sxs-lookup"><span data-stu-id="aeb72-223">Request example (existing base subscription)</span></span>

<span data-ttu-id="aeb72-224">O exemplo REST a seguir mostra como anexar suplementos a uma subscrição base existente.</span><span class="sxs-lookup"><span data-stu-id="aeb72-224">The following REST example show how to append add-ons to an existing base subscription.</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "Quantity":1,
            "BillingCycle":"annual",
            "ProvisioningContext":{"ParentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"}
        }
    ]
}
```

## <a name="rest-response"></a><span data-ttu-id="aeb72-225">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="aeb72-225">REST response</span></span>

<span data-ttu-id="aeb72-226">Se for bem sucedido, este método devolve o recurso [cart](cart-resources.md) povoado no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="aeb72-226">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

#### <a name="response-success-and-error-codes"></a><span data-ttu-id="aeb72-227">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="aeb72-227">Response success and error codes</span></span>

<span data-ttu-id="aeb72-228">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="aeb72-228">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="aeb72-229">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="aeb72-229">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="aeb72-230">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="aeb72-230">For the full list, see [Error Codes](error-codes.md).</span></span>

#### <a name="response-example-new-base-subscription"></a><span data-ttu-id="aeb72-231">Exemplo de resposta (nova subscrição base)</span><span class="sxs-lookup"><span data-stu-id="aeb72-231">Response example (new base subscription)</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 958
Content-Type: application/json
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:29:05 GMT

{
    "id":"dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
    "creationTimestamp":"2018-11-01T22:29:03.6900182Z",
    "lastModifiedTimestamp":"2018-11-01T22:29:03.6900182Z",
    "expirationTimestamp":"2018-11-01T22:44:05.0025799Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "friendlyName":"Myofferpurchase",
            "quantity":3,
            "currencyCode":"USD",
            "billingCycle":"monthly",
            "orderGroup":"OMS-0",
            "addonItems": [
                {
                    "id":1,
                    "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "quantity":2,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                },
                {
                    "id":2,
                    "catalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "quantity":3,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                }
            ]
        }
],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```

#### <a name="response-example-existing-base-subscription"></a><span data-ttu-id="aeb72-232">Exemplo de resposta (subscrição base existente)</span><span class="sxs-lookup"><span data-stu-id="aeb72-232">Response example (existing base subscription)</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 707
Content-Type: application/json
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:46:18 GMT

{
    "id":"4d927e27-93d1-448b-abe5-819b66ecca22",
    "creationTimestamp":"2018-11-01T22:46:16.2996364Z",
    "lastModifiedTimestamp":"2018-11-01T22:46:16.2996364Z",
    "expirationTimestamp":"2018-11-01T23:01:18.7543264Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "quantity":1,
            "currencyCode":"USD",
            "billingCycle":"annual",
            "provisioningContext": {
                "parentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"
            },
            "orderGroup":"OMS-0"
        }
    ],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/4d927e27-93d1-448b-abe5-819b66ecca22",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```
