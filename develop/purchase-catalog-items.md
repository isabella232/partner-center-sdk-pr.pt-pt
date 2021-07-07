---
title: Comprar itens do catálogo
description: Como adquirir itens de catálogo utilizando a API do Partner Center.
ms.date: 07/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d3e0deedff194b1c836d9266c2201a2b3a52cc1b
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445362"
---
# <a name="purchase-catalog-items"></a><span data-ttu-id="1b9ff-103">Comprar itens do catálogo</span><span class="sxs-lookup"><span data-stu-id="1b9ff-103">Purchase catalog items</span></span>

<span data-ttu-id="1b9ff-104">O seguinte cenário demonstra o processo genérico de compra de artigos do catálogo através da API do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-104">The following scenario demonstrates the generic process for purchasing items from the catalog by using the Partner Center API.</span></span>

## <a name="discovery"></a><span data-ttu-id="1b9ff-105">Deteção</span><span class="sxs-lookup"><span data-stu-id="1b9ff-105">Discovery</span></span>

<span data-ttu-id="1b9ff-106">Selecione produtos e Unidades de Armazenamento (SKUs) e verifique a sua disponibilidade utilizando os seguintes modelos API do Partner Center:</span><span class="sxs-lookup"><span data-stu-id="1b9ff-106">Select products and Stock Keeping Units (SKUs) and check their availability using the following Partner Center API models:</span></span>

- <span data-ttu-id="1b9ff-107">[Produto](product-resources.md#product) - Uma construção de agrupamento para bens ou serviços puriáveis.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-107">[Product](product-resources.md#product) - A grouping construct for purchasable goods or services.</span></span> <span data-ttu-id="1b9ff-108">Um produto por si só não é um item purivel.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-108">A product by itself isn't a purchasable item.</span></span>
- <span data-ttu-id="1b9ff-109">[SKU](product-resources.md#sku) - Um SKU purável sob um produto.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-109">[SKU](product-resources.md#sku) - A purchasable SKU under a product.</span></span> <span data-ttu-id="1b9ff-110">Estes representam as diferentes formas do produto.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-110">These represent the different shapes of the product.</span></span>
- <span data-ttu-id="1b9ff-111">[Disponibilidade](product-resources.md#availability) - Uma configuração na qual um SKU está disponível para compra (como país, moeda e segmento da indústria).</span><span class="sxs-lookup"><span data-stu-id="1b9ff-111">[Availability](product-resources.md#availability) - A configuration in which a SKU is available for purchase (such as country, currency, and industry segment).</span></span>

<span data-ttu-id="1b9ff-112">Para adquirir um artigo no catálogo, complete os seguintes passos:</span><span class="sxs-lookup"><span data-stu-id="1b9ff-112">To purchase an item from the catalog, complete the following steps:</span></span>

1. <span data-ttu-id="1b9ff-113">Identifique e recupere o Produto e SKU que pretende comprar.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-113">Identify and retrieve the Product and SKU that you want to purchase.</span></span>

   - [<span data-ttu-id="1b9ff-114">Obtenha uma lista de produtos</span><span class="sxs-lookup"><span data-stu-id="1b9ff-114">Get a list of products</span></span>](get-a-list-of-products.md)
   - [<span data-ttu-id="1b9ff-115">Obtenha um produto usando o ID do produto</span><span class="sxs-lookup"><span data-stu-id="1b9ff-115">Get a product using the product ID</span></span>](get-a-product-by-id.md)
   - [<span data-ttu-id="1b9ff-116">Obtenha uma lista de SKUs para um produto</span><span class="sxs-lookup"><span data-stu-id="1b9ff-116">Get a list of SKUs for a product</span></span>](get-a-list-of-skus-for-a-product.md)
   - [<span data-ttu-id="1b9ff-117">Obtenha um SKU usando o SKU ID</span><span class="sxs-lookup"><span data-stu-id="1b9ff-117">Get a SKU using the SKU ID</span></span>](get-a-sku-by-id.md)

2. <span data-ttu-id="1b9ff-118">Verifique o inventário de um SKU.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-118">Check the inventory for a SKU.</span></span> <span data-ttu-id="1b9ff-119">Este passo é apenas necessário para SKUs que são marcados com um valor **InventárioCheck** na [propriedade de compraPrerequisites.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="1b9ff-119">This step is only needed for SKUs that are tagged with an **InventoryCheck** value in the [purchasePrerequisites](product-resources.md#sku) property.</span></span>

   - [<span data-ttu-id="1b9ff-120">Verificar Inventário</span><span class="sxs-lookup"><span data-stu-id="1b9ff-120">Check Inventory</span></span>](check-inventory.md)

3. <span data-ttu-id="1b9ff-121">Recupere a [disponibilidade](product-resources.md#availability) para o [SKU.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="1b9ff-121">Retrieve the [availability](product-resources.md#availability) for the [SKU](product-resources.md#sku).</span></span> <span data-ttu-id="1b9ff-122">Necessitará do **CatalogItemId** da disponibilidade ao fazer a encomenda.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-122">You will need the **CatalogItemId** of the availability when placing the order.</span></span> <span data-ttu-id="1b9ff-123">Para obter este valor, utilize uma das seguintes APIs:</span><span class="sxs-lookup"><span data-stu-id="1b9ff-123">To get this value, use one of the following APIs:</span></span>

   - [<span data-ttu-id="1b9ff-124">Obtenha uma lista de disponibilidades para um SKU</span><span class="sxs-lookup"><span data-stu-id="1b9ff-124">Get a list of availabilities for a SKU</span></span>](get-a-list-of-availabilities-for-a-sku.md)
   - [<span data-ttu-id="1b9ff-125">Obtenha uma disponibilidade usando o ID de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="1b9ff-125">Get an availability using the availability ID</span></span>](get-an-availability-by-id.md)

## <a name="order-submission"></a><span data-ttu-id="1b9ff-126">Submissão de encomendas</span><span class="sxs-lookup"><span data-stu-id="1b9ff-126">Order submission</span></span>

<span data-ttu-id="1b9ff-127">Para submeter a sua encomenda de artigo de catálogo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1b9ff-127">To submit your catalog item order, do the following:</span></span>

1. <span data-ttu-id="1b9ff-128">Crie um [Carrinho](cart-resources.md) para guardar a coleção de itens de catálogo que pretende comprar.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-128">Create a [Cart](cart-resources.md) to hold the collection of catalog items that you intend to buy.</span></span> <span data-ttu-id="1b9ff-129">Quando cria um carrinho, os [itens](cart-resources.md#cartlineitem) da linha do carrinho são automaticamente agrupados com base no que pode ser comprado juntos na mesma [Ordem](order-resources.md).</span><span class="sxs-lookup"><span data-stu-id="1b9ff-129">When you create a cart, the [cart line items](cart-resources.md#cartlineitem) are automatically grouped based on what can be purchased together in the same [Order](order-resources.md).</span></span>

   - [<span data-ttu-id="1b9ff-130">Criar um carrinho de compras</span><span class="sxs-lookup"><span data-stu-id="1b9ff-130">Create a shopping cart</span></span>](create-a-cart.md)
   - [<span data-ttu-id="1b9ff-131">Atualize um carrinho de compras</span><span class="sxs-lookup"><span data-stu-id="1b9ff-131">Update a shopping cart</span></span>](update-a-cart.md)

2. <span data-ttu-id="1b9ff-132">Olha para o carrinho.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-132">Check out the cart.</span></span> <span data-ttu-id="1b9ff-133">A verificação de um carrinho resulta na criação de uma [Ordem.](order-resources.md)</span><span class="sxs-lookup"><span data-stu-id="1b9ff-133">Checking out a cart results in the creation of an [Order](order-resources.md).</span></span>

   - [<span data-ttu-id="1b9ff-134">Check-out do carrinho</span><span class="sxs-lookup"><span data-stu-id="1b9ff-134">Checkout the cart</span></span>](checkout-a-cart.md)

## <a name="get-order-details"></a><span data-ttu-id="1b9ff-135">Obter detalhes da encomenda</span><span class="sxs-lookup"><span data-stu-id="1b9ff-135">Get order details</span></span>

<span data-ttu-id="1b9ff-136">Pode recuperar os detalhes de uma encomenda individual utilizando o ID da encomenda ou obter uma lista de encomendas para um cliente.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-136">You can retrieve the details of an individual order using the order ID, or get a list of orders for a customer.</span></span> <span data-ttu-id="1b9ff-137">Há um atraso de até 15 minutos entre o momento em que uma encomenda é submetida e quando aparecerá numa lista de encomendas de um cliente.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-137">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a list of a customer's orders.</span></span>

- <span data-ttu-id="1b9ff-138">Consulte [obter uma encomenda por ID](get-an-order-by-id.md) para obter os detalhes de uma encomenda individual usando os IDs de encomenda.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-138">See [Get an order by ID](get-an-order-by-id.md) to get the details of an individual order using the order IDs.</span></span>

- <span data-ttu-id="1b9ff-139">Consulte [todas as ordens de um cliente](get-all-of-a-customer-s-orders.md) para obter uma lista de encomendas para um cliente que utilize a identificação do cliente.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-139">See [Get all of a customer's orders](get-all-of-a-customer-s-orders.md) to get a list of orders for a customer using the customer ID.</span></span>

- <span data-ttu-id="1b9ff-140">Consulte obter uma lista de encomendas por cliente e tipo de ciclo de [faturação](get-a-list-of-orders-by-customer-and-billing-cycle-type.md) para obter uma lista de encomendas para um cliente por tipo de ciclo de [faturação,](product-resources.md#billingcycletype) permitindo-lhe listar as encomendas de artigos de catálogo (taxas pontuais) e encomendas anuais ou mensais faturadas separadamente.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-140">See [Get a list of orders by customer and billing cycle type](get-a-list-of-orders-by-customer-and-billing-cycle-type.md) to get a list of orders for a customer by [billing cycle type](product-resources.md#billingcycletype) allowing you to list catalog item orders (one-time charges) and annual or monthly billed orders separately.</span></span>

## <a name="lifecycle-management"></a><span data-ttu-id="1b9ff-141">Gestão do ciclo de vida</span><span class="sxs-lookup"><span data-stu-id="1b9ff-141">Lifecycle management</span></span>

<span data-ttu-id="1b9ff-142">Como parte da gestão do ciclo de vida dos seus itens de catálogo no Partner Center, pode obter informações sobre o seu item de catálogo [Direitos](entitlement-resources.md), e obter detalhes da reserva usando o ID da encomenda de reservas.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-142">As part of managing the lifecycle of your catalog items in Partner Center, you can retrieve information about your catalog item [Entitlements](entitlement-resources.md), and get reservation details using the reservation order ID.</span></span> <span data-ttu-id="1b9ff-143">Por exemplo, como fazê-lo, consulte [obter direitos](get-a-collection-of-entitlements.md).</span><span class="sxs-lookup"><span data-stu-id="1b9ff-143">For examples of how to do this, see [Get entitlements](get-a-collection-of-entitlements.md).</span></span>   

## <a name="invoice-and-reconciliation"></a><span data-ttu-id="1b9ff-144">Fatura e reconciliação</span><span class="sxs-lookup"><span data-stu-id="1b9ff-144">Invoice and reconciliation</span></span>

<span data-ttu-id="1b9ff-145">Os seguintes cenários mostram-lhe como visualizar programaticamente as [faturas](invoice-resources.md)do seu cliente, e obter os saldos e resumos da sua conta que incluem taxas únicas para itens de catálogo.</span><span class="sxs-lookup"><span data-stu-id="1b9ff-145">The following scenarios show you how to programmatically view your customer's [invoices](invoice-resources.md), and get your account balances and summaries that include one-time charges for catalog items.</span></span>

### <a name="balance-and-payment"></a><span data-ttu-id="1b9ff-146">Saldo e pagamento</span><span class="sxs-lookup"><span data-stu-id="1b9ff-146">Balance and payment</span></span>

<span data-ttu-id="1b9ff-147">Para obter o saldo da conta corrente no seu tipo de moeda padrão que é um saldo de encargos recorrentes e pontuais (item de catálogo), consulte [obter o saldo da sua conta corrente](get-the-reseller-s-current-account-balance.md).</span><span class="sxs-lookup"><span data-stu-id="1b9ff-147">To get current account balance in your default currency type that is a balance of both recurring and one-time (catalog item) charges, see [Get your current account balance](get-the-reseller-s-current-account-balance.md).</span></span>

### <a name="multi-currency-balance-and-payment"></a><span data-ttu-id="1b9ff-148">Balança e pagamento multi-moedas</span><span class="sxs-lookup"><span data-stu-id="1b9ff-148">Multi-currency balance and payment</span></span>

<span data-ttu-id="1b9ff-149">Para obter o saldo da sua conta corrente e uma recolha de resumos de faturas contendo um resumo da fatura com encargos recorrentes e pontuais para cada um dos tipos de moeda do seu cliente, consulte [resumos](get-invoice-summaries.md)da fatura .</span><span class="sxs-lookup"><span data-stu-id="1b9ff-149">To get your current account balance and a collection of invoice summaries containing an invoice summary with both recurring and one-time charges for each of your customer's currency types, see [Get invoice summaries](get-invoice-summaries.md).</span></span>

### <a name="invoices"></a><span data-ttu-id="1b9ff-150">Faturas</span><span class="sxs-lookup"><span data-stu-id="1b9ff-150">Invoices</span></span>

<span data-ttu-id="1b9ff-151">Para obter uma coleção de faturas que mostrem taxas recorrentes e pontuais, consulte [obter uma coleção de faturas.](get-a-collection-of-invoices.md)</span><span class="sxs-lookup"><span data-stu-id="1b9ff-151">To get a collection of invoices that show both recurring and one-time charges, see [Get a collection of invoices](get-a-collection-of-invoices.md).</span></span> 

### <a name="single-invoice"></a><span data-ttu-id="1b9ff-152">Fatura Única</span><span class="sxs-lookup"><span data-stu-id="1b9ff-152">Single Invoice</span></span>

<span data-ttu-id="1b9ff-153">Para obter uma fatura específica utilizando o ID da fatura, consulte [obter uma fatura por ID](get-invoice-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="1b9ff-153">To retrieve a specific invoice using the invoice ID, see [Get an invoice by ID](get-invoice-by-id.md).</span></span>  

### <a name="reconciliation"></a><span data-ttu-id="1b9ff-154">Reconciliação</span><span class="sxs-lookup"><span data-stu-id="1b9ff-154">Reconciliation</span></span>

<span data-ttu-id="1b9ff-155">Para obter uma recolha de detalhes de item da linha de fatura (itens de linha de reconciliação) para um ID de fatura específico, consulte [obter itens de linha de fatura](get-invoiceline-items.md).</span><span class="sxs-lookup"><span data-stu-id="1b9ff-155">To get a collection of invoice line item details (Reconciliation line items) for a specific invoice ID, see [Get invoice line items](get-invoiceline-items.md).</span></span>  

### <a name="download-an-invoice-as-a-pdf"></a><span data-ttu-id="1b9ff-156">Faça o download de uma fatura como UM PDF</span><span class="sxs-lookup"><span data-stu-id="1b9ff-156">Download an invoice as a PDF</span></span>

<span data-ttu-id="1b9ff-157">Para obter uma declaração de fatura em formulário PDF utilizando um ID de fatura, consulte [uma declaração de fatura](get-invoice-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1b9ff-157">To retrieve an invoice statement in PDF form using an invoice ID, see [Get an invoice statement](get-invoice-statement.md).</span></span>
