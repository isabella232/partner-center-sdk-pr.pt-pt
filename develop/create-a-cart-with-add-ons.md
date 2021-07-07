---
title: Criar um carrinho com suplementos
description: Saiba como utilizar as APIs do Partner Center para adicionar uma encomenda de clientes com suplementos através de um carrinho. O artigo partilha pré-requisitos e passos para criar um carrinho com suplementos.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 513a9607b9194c36253630c91de9622325317c3a
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973762"
---
# <a name="create-a-cart-with-add-ons-to-a-customer-order"></a><span data-ttu-id="e6d99-104">Criar um carrinho com suplementos a uma encomenda de clientes</span><span class="sxs-lookup"><span data-stu-id="e6d99-104">Create a cart with add-ons to a customer order</span></span>

<span data-ttu-id="e6d99-105">Pode comprar suplementos através de um carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-105">You can purchase add-ons through a cart.</span></span> <span data-ttu-id="e6d99-106">Para obter mais informações sobre o que está atualmente disponível para vender, consulte [as ofertas do Partner no programa Fornecedor de Soluções em Nuvem.](/partner-center/csp-offers)</span><span class="sxs-lookup"><span data-stu-id="e6d99-106">For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6d99-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e6d99-107">Prerequisites</span></span>

- <span data-ttu-id="e6d99-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e6d99-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e6d99-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="e6d99-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e6d99-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e6d99-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e6d99-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e6d99-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e6d99-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="e6d99-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e6d99-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="e6d99-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e6d99-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="e6d99-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e6d99-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e6d99-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="e6d99-116">C\#</span><span class="sxs-lookup"><span data-stu-id="e6d99-116">C\#</span></span>

<span data-ttu-id="e6d99-117">Um carrinho permite a compra de uma oferta base e os seus suplementos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="e6d99-117">A cart enables the purchase of a base offer and its corresponding add-ons.</span></span> <span data-ttu-id="e6d99-118">Siga estes passos para criar um carrinho:</span><span class="sxs-lookup"><span data-stu-id="e6d99-118">Follow these steps to create a cart:</span></span>

1. <span data-ttu-id="e6d99-119">Instantiizar um objeto [**do Carrinho.**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart)</span><span class="sxs-lookup"><span data-stu-id="e6d99-119">Instantiate a [**Cart**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart) object.</span></span>

2. <span data-ttu-id="e6d99-120">Crie uma lista de objetos [**CartLineItem**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) que representam a(s) oferta base, e atribua a lista à propriedade [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) do carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-120">Create a list of [**CartLineItem**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) objects that represent the base offer(s), and assign the list to the cart's [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) property.</span></span>

3. <span data-ttu-id="e6d99-121">Sob o item da linha de cada oferta base, povoar a lista de **AddOnItems com outros objetos** **CartLineItem** que cada um representa um addon que será comprado contra essa oferta base.</span><span class="sxs-lookup"><span data-stu-id="e6d99-121">Under each base offer's cart line item, populate the list of **AddOnItems** with other **CartLineItem** objects that each represent an add-on that will be purchased against that base offer.</span></span>

4. <span data-ttu-id="e6d99-122">Obtenha uma interface para as operações de carrinhos utilizando o [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) para ligar para o método [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface da propriedade **Cart.**</span><span class="sxs-lookup"><span data-stu-id="e6d99-122">Obtain an interface to cart operations by using [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) to call the [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.</span></span>

5. <span data-ttu-id="e6d99-123">Por fim, ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) ou [**Criar Async**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) para criar o carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-123">Finally, call the [**Create**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) method to create the cart.</span></span>

### <a name="c-example"></a><span data-ttu-id="e6d99-124">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="e6d99-124">C\# example</span></span>

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

<span data-ttu-id="e6d99-125">Siga estes passos para criar um carrinho que permita a compra de addons(s) contra subscrições de base existentes):</span><span class="sxs-lookup"><span data-stu-id="e6d99-125">Follow these steps to create a cart that will enable the purchase of add-on(s) against existing base subscription(s):</span></span>

1. <span data-ttu-id="e6d99-126">Crie um **Carrinho** com um novo **CartLineItem** contendo o ID de subscrição na propriedade **ProvisioningContext** com a chave "ParentSubscriptionId".</span><span class="sxs-lookup"><span data-stu-id="e6d99-126">Create a **Cart** with a new **CartLineItem** containing the subscription ID in the **ProvisioningContext** property with key "ParentSubscriptionId".</span></span>

2. <span data-ttu-id="e6d99-127">Chame o método **Criar** ou **Criar Async.**</span><span class="sxs-lookup"><span data-stu-id="e6d99-127">Call the **Create** or **CreateAsync** method.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="e6d99-128">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="e6d99-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e6d99-129">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6d99-129">Request syntax</span></span>

| <span data-ttu-id="e6d99-130">Método</span><span class="sxs-lookup"><span data-stu-id="e6d99-130">Method</span></span>   | <span data-ttu-id="e6d99-131">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="e6d99-131">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e6d99-132">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="e6d99-132">**POST**</span></span> | <span data-ttu-id="e6d99-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e6d99-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span></span>                        |

#### <a name="uri-parameter"></a><span data-ttu-id="e6d99-134">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="e6d99-134">URI parameter</span></span>

<span data-ttu-id="e6d99-135">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e6d99-135">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="e6d99-136">Nome</span><span class="sxs-lookup"><span data-stu-id="e6d99-136">Name</span></span>            | <span data-ttu-id="e6d99-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="e6d99-137">Type</span></span>     | <span data-ttu-id="e6d99-138">Necessário</span><span class="sxs-lookup"><span data-stu-id="e6d99-138">Required</span></span> | <span data-ttu-id="e6d99-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6d99-139">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="e6d99-140">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="e6d99-140">**customer-id**</span></span> | <span data-ttu-id="e6d99-141">string</span><span class="sxs-lookup"><span data-stu-id="e6d99-141">string</span></span>   | <span data-ttu-id="e6d99-142">Yes</span><span class="sxs-lookup"><span data-stu-id="e6d99-142">Yes</span></span>      | <span data-ttu-id="e6d99-143">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="e6d99-143">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="e6d99-144">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="e6d99-144">Request headers</span></span>

<span data-ttu-id="e6d99-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e6d99-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e6d99-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="e6d99-146">Request body</span></span>

<span data-ttu-id="e6d99-147">Esta tabela descreve as propriedades do [Carrinho](cart-resources.md) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="e6d99-147">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="e6d99-148">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e6d99-148">Property</span></span>              | <span data-ttu-id="e6d99-149">Tipo</span><span class="sxs-lookup"><span data-stu-id="e6d99-149">Type</span></span>             | <span data-ttu-id="e6d99-150">Necessário</span><span class="sxs-lookup"><span data-stu-id="e6d99-150">Required</span></span>        | <span data-ttu-id="e6d99-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6d99-151">Description</span></span> |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e6d99-152">ID</span><span class="sxs-lookup"><span data-stu-id="e6d99-152">id</span></span>                    | <span data-ttu-id="e6d99-153">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="e6d99-153">string</span></span>           | <span data-ttu-id="e6d99-154">No</span><span class="sxs-lookup"><span data-stu-id="e6d99-154">No</span></span>              | <span data-ttu-id="e6d99-155">Um identificador de carrinhos que é fornecido após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-155">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="e6d99-156">criaçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="e6d99-156">creationTimeStamp</span></span>     | <span data-ttu-id="e6d99-157">DateTime</span><span class="sxs-lookup"><span data-stu-id="e6d99-157">DateTime</span></span>         | <span data-ttu-id="e6d99-158">No</span><span class="sxs-lookup"><span data-stu-id="e6d99-158">No</span></span>              | <span data-ttu-id="e6d99-159">A data em que o carrinho foi criado, em formato de data- hora.</span><span class="sxs-lookup"><span data-stu-id="e6d99-159">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="e6d99-160">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-160">Applied upon successful creation of the cart.</span></span>         |
| <span data-ttu-id="e6d99-161">últimampadatimestamp de Tempos</span><span class="sxs-lookup"><span data-stu-id="e6d99-161">lastModifiedTimeStamp</span></span> | <span data-ttu-id="e6d99-162">DateTime</span><span class="sxs-lookup"><span data-stu-id="e6d99-162">DateTime</span></span>         | <span data-ttu-id="e6d99-163">No</span><span class="sxs-lookup"><span data-stu-id="e6d99-163">No</span></span>              | <span data-ttu-id="e6d99-164">A data em que o carrinho foi atualizado pela última vez, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="e6d99-164">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="e6d99-165">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-165">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="e6d99-166">expiraçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="e6d99-166">expirationTimeStamp</span></span>   | <span data-ttu-id="e6d99-167">DateTime</span><span class="sxs-lookup"><span data-stu-id="e6d99-167">DateTime</span></span>         | <span data-ttu-id="e6d99-168">No</span><span class="sxs-lookup"><span data-stu-id="e6d99-168">No</span></span>              | <span data-ttu-id="e6d99-169">A data em que o carrinho expirará, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="e6d99-169">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="e6d99-170">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-170">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="e6d99-171">últimoModifiedUser</span><span class="sxs-lookup"><span data-stu-id="e6d99-171">lastModifiedUser</span></span>      | <span data-ttu-id="e6d99-172">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="e6d99-172">string</span></span>           | <span data-ttu-id="e6d99-173">No</span><span class="sxs-lookup"><span data-stu-id="e6d99-173">No</span></span>              | <span data-ttu-id="e6d99-174">O utilizador que atualizou pela última vez o carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-174">The user who last updated the cart.</span></span> <span data-ttu-id="e6d99-175">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-175">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="e6d99-176">lineitems</span><span class="sxs-lookup"><span data-stu-id="e6d99-176">lineItems</span></span>             | <span data-ttu-id="e6d99-177">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="e6d99-177">Array of objects</span></span> | <span data-ttu-id="e6d99-178">Yes</span><span class="sxs-lookup"><span data-stu-id="e6d99-178">Yes</span></span>             | <span data-ttu-id="e6d99-179">Uma matriz de recursos [CartLineItem.](cart-resources.md#cartlineitem)</span><span class="sxs-lookup"><span data-stu-id="e6d99-179">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                             |

<span data-ttu-id="e6d99-180">Esta tabela descreve as propriedades [do CartLineItem](cart-resources.md#cartlineitem) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="e6d99-180">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

| <span data-ttu-id="e6d99-181">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e6d99-181">Property</span></span>             | <span data-ttu-id="e6d99-182">Tipo</span><span class="sxs-lookup"><span data-stu-id="e6d99-182">Type</span></span>                             | <span data-ttu-id="e6d99-183">Description</span><span class="sxs-lookup"><span data-stu-id="e6d99-183">Description</span></span>                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e6d99-184">ID</span><span class="sxs-lookup"><span data-stu-id="e6d99-184">id</span></span>                   | <span data-ttu-id="e6d99-185">string</span><span class="sxs-lookup"><span data-stu-id="e6d99-185">string</span></span>                           | <span data-ttu-id="e6d99-186">Um identificador único para um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-186">A unique identifier for a cart line item.</span></span> <span data-ttu-id="e6d99-187">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="e6d99-187">Applied upon successful creation of cart.</span></span>                                                                   |
| <span data-ttu-id="e6d99-188">catalogId</span><span class="sxs-lookup"><span data-stu-id="e6d99-188">catalogId</span></span>            | <span data-ttu-id="e6d99-189">string</span><span class="sxs-lookup"><span data-stu-id="e6d99-189">string</span></span>                           | <span data-ttu-id="e6d99-190">O identificador de artigos de catálogo.</span><span class="sxs-lookup"><span data-stu-id="e6d99-190">The catalog item identifier.</span></span>                                                                                                                          |
| <span data-ttu-id="e6d99-191">nome amigável</span><span class="sxs-lookup"><span data-stu-id="e6d99-191">friendlyName</span></span>         | <span data-ttu-id="e6d99-192">string</span><span class="sxs-lookup"><span data-stu-id="e6d99-192">string</span></span>                           | <span data-ttu-id="e6d99-193">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e6d99-193">Optional.</span></span> <span data-ttu-id="e6d99-194">O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="e6d99-194">The friendly name for the item defined by the partner to help disambiguate.</span></span>                                                                 |
| <span data-ttu-id="e6d99-195">quantidade</span><span class="sxs-lookup"><span data-stu-id="e6d99-195">quantity</span></span>             | <span data-ttu-id="e6d99-196">int</span><span class="sxs-lookup"><span data-stu-id="e6d99-196">int</span></span>                              | <span data-ttu-id="e6d99-197">O número de licenças ou instâncias.</span><span class="sxs-lookup"><span data-stu-id="e6d99-197">The number of licenses or instances.</span></span>                                                                                                                  |
| <span data-ttu-id="e6d99-198">currencyCode</span><span class="sxs-lookup"><span data-stu-id="e6d99-198">currencyCode</span></span>         | <span data-ttu-id="e6d99-199">string</span><span class="sxs-lookup"><span data-stu-id="e6d99-199">string</span></span>                           | <span data-ttu-id="e6d99-200">O código da moeda.</span><span class="sxs-lookup"><span data-stu-id="e6d99-200">The currency code.</span></span>                                                                                                                                    |
| <span data-ttu-id="e6d99-201">billingCycle</span><span class="sxs-lookup"><span data-stu-id="e6d99-201">billingCycle</span></span>         | <span data-ttu-id="e6d99-202">Objeto</span><span class="sxs-lookup"><span data-stu-id="e6d99-202">Object</span></span>                           | <span data-ttu-id="e6d99-203">O tipo de ciclo de faturação definido para o período atual.</span><span class="sxs-lookup"><span data-stu-id="e6d99-203">The type of billing cycle set for the current period.</span></span>                                                                                                 |
| <span data-ttu-id="e6d99-204">participantes</span><span class="sxs-lookup"><span data-stu-id="e6d99-204">participants</span></span>         | <span data-ttu-id="e6d99-205">Lista de pares de cordas de objeto</span><span class="sxs-lookup"><span data-stu-id="e6d99-205">List of Object String pairs</span></span>      | <span data-ttu-id="e6d99-206">Uma coleção de PartnerId on Record (MPN ID) na compra.</span><span class="sxs-lookup"><span data-stu-id="e6d99-206">A collection of PartnerId on Record (MPN ID) on the purchase.</span></span>                                                                                          |
| <span data-ttu-id="e6d99-207">provisionamentoContexto</span><span class="sxs-lookup"><span data-stu-id="e6d99-207">provisioningContext</span></span>  | <span data-ttu-id="e6d99-208">Cadeia de<do dicionário,> de cordas</span><span class="sxs-lookup"><span data-stu-id="e6d99-208">Dictionary<string, string></span></span>       | <span data-ttu-id="e6d99-209">Um contexto utilizado para o provisionamento da oferta.</span><span class="sxs-lookup"><span data-stu-id="e6d99-209">A context used for provisioning of offer.</span></span>                                                                                                             |
| <span data-ttu-id="e6d99-210">orderGroup</span><span class="sxs-lookup"><span data-stu-id="e6d99-210">orderGroup</span></span>           | <span data-ttu-id="e6d99-211">string</span><span class="sxs-lookup"><span data-stu-id="e6d99-211">string</span></span>                           | <span data-ttu-id="e6d99-212">Um grupo para indicar quais os itens que podem ser colocados juntos.</span><span class="sxs-lookup"><span data-stu-id="e6d99-212">A group to indicate which items can be placed together.</span></span>                                                                                               |
| <span data-ttu-id="e6d99-213">addonItems</span><span class="sxs-lookup"><span data-stu-id="e6d99-213">addonItems</span></span>           | <span data-ttu-id="e6d99-214">Lista de **objetos CartLineItem**</span><span class="sxs-lookup"><span data-stu-id="e6d99-214">List of **CartLineItem** objects</span></span> | <span data-ttu-id="e6d99-215">Uma coleção de itens de linha de carrinhos para addons que serão adquiridos para a subscrição base que resulta da compra do item da linha do carrinho dos pais.</span><span class="sxs-lookup"><span data-stu-id="e6d99-215">A collection of cart line items for add-ons that will be purchased towards the base subscription that results from the parent cart line item's purchase.</span></span> |
| <span data-ttu-id="e6d99-216">erro</span><span class="sxs-lookup"><span data-stu-id="e6d99-216">error</span></span>                | <span data-ttu-id="e6d99-217">Objeto</span><span class="sxs-lookup"><span data-stu-id="e6d99-217">Object</span></span>                           | <span data-ttu-id="e6d99-218">Aplicado após o carrinho é criado se houver um erro.</span><span class="sxs-lookup"><span data-stu-id="e6d99-218">Applied after cart is created if there is an error.</span></span>                                                                                                    |

### <a name="request-example-new-base-subscription"></a><span data-ttu-id="e6d99-219">Exemplo de pedido (nova subscrição base)</span><span class="sxs-lookup"><span data-stu-id="e6d99-219">Request example (new base subscription)</span></span>

<span data-ttu-id="e6d99-220">O exemplo REST que se segue mostra como criar um carrinho com itens adicionais para uma nova subscrição base.</span><span class="sxs-lookup"><span data-stu-id="e6d99-220">The following REST example shows how to create a cart with add-on items for a new base subscription.</span></span>

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

#### <a name="request-example-existing-base-subscription"></a><span data-ttu-id="e6d99-221">Exemplo de pedido (subscrição base existente)</span><span class="sxs-lookup"><span data-stu-id="e6d99-221">Request example (existing base subscription)</span></span>

<span data-ttu-id="e6d99-222">O exemplo REST a seguir mostra como anexar suplementos a uma subscrição base existente.</span><span class="sxs-lookup"><span data-stu-id="e6d99-222">The following REST example shows how to append add-ons to an existing base subscription.</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e6d99-223">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="e6d99-223">REST response</span></span>

<span data-ttu-id="e6d99-224">Se for bem sucedido, este método devolve o recurso [cart](cart-resources.md) povoado no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="e6d99-224">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

#### <a name="response-success-and-error-codes"></a><span data-ttu-id="e6d99-225">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="e6d99-225">Response success and error codes</span></span>

<span data-ttu-id="e6d99-226">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="e6d99-226">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e6d99-227">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="e6d99-227">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e6d99-228">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="e6d99-228">For the full list, see [Error Codes](error-codes.md).</span></span>

#### <a name="response-example-new-base-subscription"></a><span data-ttu-id="e6d99-229">Exemplo de resposta (nova subscrição base)</span><span class="sxs-lookup"><span data-stu-id="e6d99-229">Response example (new base subscription)</span></span>

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

#### <a name="response-example-existing-base-subscription"></a><span data-ttu-id="e6d99-230">Exemplo de resposta (subscrição base existente)</span><span class="sxs-lookup"><span data-stu-id="e6d99-230">Response example (existing base subscription)</span></span>

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
