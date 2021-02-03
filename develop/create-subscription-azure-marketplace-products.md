---
title: Criar uma subscrição para produtos de mercado comercial
description: Os desenvolvedores podem criar e gerir uma subscrição de produtos de marketplace comercial usando APIs do Partner Center.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df2a3707e00ba36a11c404b102304c08d105244e
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768810"
---
# <a name="create-a-subscription-for-commercial-marketplace-products"></a><span data-ttu-id="17c1a-103">Criar uma subscrição para produtos de mercado comercial</span><span class="sxs-lookup"><span data-stu-id="17c1a-103">Create a subscription for commercial marketplace products</span></span>

<span data-ttu-id="17c1a-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="17c1a-104">**Applies to:**</span></span>

* <span data-ttu-id="17c1a-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="17c1a-105">Partner Center</span></span>

<span data-ttu-id="17c1a-106">Pode criar uma subscrição para produtos de marketplace comercial utilizando APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="17c1a-106">You can create a subscription for commercial marketplace products using Partner Center APIs.</span></span> <span data-ttu-id="17c1a-107">Você deve [obter uma lista de ofertas para um mercado,](#get-a-list-of-offers-for-a-market)criar e enviar uma [encomenda](#create-and-submit-an-order) para uma subscrição de mercado comercial, em seguida, recuperar um link [de ativação](#get-activation-link).</span><span class="sxs-lookup"><span data-stu-id="17c1a-107">You must [get a list of offers for a market](#get-a-list-of-offers-for-a-market), [create and submit an order](#create-and-submit-an-order) for a commercial marketplace subscription, then [retrieve an activation link](#get-activation-link).</span></span>

<span data-ttu-id="17c1a-108">Também pode [realizar gestão de ciclo de vida](#lifecycle-management) e gerir [faturas](#invoice-and-reconciliation) para estas subscrições.</span><span class="sxs-lookup"><span data-stu-id="17c1a-108">You can also [perform lifecycle management](#lifecycle-management) and [manage invoices](#invoice-and-reconciliation) for these subscriptions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="17c1a-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="17c1a-109">Prerequisites</span></span>

* <span data-ttu-id="17c1a-110">[Credenciais de autenticação do Partner Center.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="17c1a-110">[Partner Center authentication](partner-center-authentication.md) credentials.</span></span> <span data-ttu-id="17c1a-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="17c1a-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>
* <span data-ttu-id="17c1a-112">O identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="17c1a-112">The customer identifier.</span></span> <span data-ttu-id="17c1a-113">Se não tiver o identificador de um cliente, siga os passos na [Obter uma lista de clientes.](get-a-list-of-customers.md)</span><span class="sxs-lookup"><span data-stu-id="17c1a-113">If you don't have a customer's identifier, follow the steps in [Get a list of customers](get-a-list-of-customers.md).</span></span> <span data-ttu-id="17c1a-114">Em alternativa, inscreva-se no Partner Center, escolha o cliente na lista de clientes, selecione **Conta** e guarde o seu **ID Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="17c1a-114">Alternatively, sign in to Partner Center, choose the customer from the list of customers, select **Account**, then save their **Microsoft ID**.</span></span>

## <a name="get-a-list-of-offers-for-a-market"></a><span data-ttu-id="17c1a-115">Obter uma lista de ofertas para um mercado</span><span class="sxs-lookup"><span data-stu-id="17c1a-115">Get a list of offers for a market</span></span>

<span data-ttu-id="17c1a-116">Pode consultar as ofertas disponíveis para um mercado utilizando os seguintes modelos API do Partner Center:</span><span class="sxs-lookup"><span data-stu-id="17c1a-116">You can check the available offers for a market using the following Partner Center API models:</span></span>

* <span data-ttu-id="17c1a-117">**[Produto](product-resources.md#product)**: Uma construção de agrupamento para bens ou serviços puriáveis.</span><span class="sxs-lookup"><span data-stu-id="17c1a-117">**[Product](product-resources.md#product)**: A grouping construct for purchasable goods or services.</span></span> <span data-ttu-id="17c1a-118">Um produto em si não é um item purivel.</span><span class="sxs-lookup"><span data-stu-id="17c1a-118">A product itself isn't a purchasable item.</span></span>
* <span data-ttu-id="17c1a-119">**[SKU](product-resources.md#sku)**: Uma unidade de armazenamento de stock (SKU) em baixo de um produto.</span><span class="sxs-lookup"><span data-stu-id="17c1a-119">**[SKU](product-resources.md#sku)**: A purchasable Stock Keeping Unit (SKU) under a product.</span></span> <span data-ttu-id="17c1a-120">Estes representam as diferentes formas do produto.</span><span class="sxs-lookup"><span data-stu-id="17c1a-120">These represent the different shapes of the product.</span></span>
* <span data-ttu-id="17c1a-121">**[Disponibilidade](product-resources.md#availability)**: Uma configuração na qual um SKU está disponível para compra (como país, moeda ou segmento da indústria).</span><span class="sxs-lookup"><span data-stu-id="17c1a-121">**[Availability](product-resources.md#availability)**: A configuration in which a SKU is available for purchase (such as country, currency, or industry segment).</span></span>

<span data-ttu-id="17c1a-122">Antes de adquirir uma reserva Azure, complete os seguintes passos:</span><span class="sxs-lookup"><span data-stu-id="17c1a-122">Before you purchase an Azure reservation, complete the following steps:</span></span>

1. <span data-ttu-id="17c1a-123">Identifique e recupere o produto e o SKU que pretende comprar.</span><span class="sxs-lookup"><span data-stu-id="17c1a-123">Identify and retrieve the product and SKU that you want to purchase.</span></span> <span data-ttu-id="17c1a-124">Se já conhece o ID do Produto e o ID SKU, selecione-os.</span><span class="sxs-lookup"><span data-stu-id="17c1a-124">If you already know the Product ID and SKU ID, select them.</span></span>

    * [<span data-ttu-id="17c1a-125">Obtenha uma lista de produtos</span><span class="sxs-lookup"><span data-stu-id="17c1a-125">Get a list of products</span></span>](get-a-list-of-products.md)
    * [<span data-ttu-id="17c1a-126">Obtenha um produto usando o ID do produto</span><span class="sxs-lookup"><span data-stu-id="17c1a-126">Get a product using the product ID</span></span>](get-a-product-by-id.md)
    * [<span data-ttu-id="17c1a-127">Obtenha uma lista de SKUs para um produto</span><span class="sxs-lookup"><span data-stu-id="17c1a-127">Get a list of SKUs for a product</span></span>](get-a-list-of-skus-for-a-product.md)
    * [<span data-ttu-id="17c1a-128">Obtenha um SKU usando o SKU ID</span><span class="sxs-lookup"><span data-stu-id="17c1a-128">Get a SKU using the SKU ID</span></span>](get-a-sku-by-id.md)

    > [!NOTE]
    > <span data-ttu-id="17c1a-129">Pode identificar produtos de mercado comercial através da sua propriedade **ProductType** de **"Azure"** e da sua propriedade **subType** de **"SaaS".**</span><span class="sxs-lookup"><span data-stu-id="17c1a-129">You can identify commercial marketplace products by their **ProductType** property of **"Azure"** and their **SubType** property of **"SaaS"**.</span></span>

2. <span data-ttu-id="17c1a-130">Se os SKUs estiverem marcados com um pré-requisito **do InventárioCheck,** [verifique o inventário de um SKU](check-inventory.md).</span><span class="sxs-lookup"><span data-stu-id="17c1a-130">If the SKUs are tagged with an **InventoryCheck** prerequisite, [check the inventory for a SKU](check-inventory.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="17c1a-131">Neste momento, não existem produtos de mercado comercial que suportem a verificação de inventário ou estejam marcados com um pré-requisito **do InventárioCheck.**</span><span class="sxs-lookup"><span data-stu-id="17c1a-131">At this time, there are no commercial marketplace products that support inventory check or are tagged with an **InventoryCheck** prerequisite.</span></span>

3. <span data-ttu-id="17c1a-132">Recupere a disponibilidade para o SKU.</span><span class="sxs-lookup"><span data-stu-id="17c1a-132">Retrieve the availability for the SKU.</span></span> <span data-ttu-id="17c1a-133">Necessitará do **CatalogItemId** da disponibilidade ao esemcrutinar a encomenda, que poderá obter através das seguintes APIs:</span><span class="sxs-lookup"><span data-stu-id="17c1a-133">You will need the **CatalogItemId** of the availability when placing the order, which you can retrieve through the following APIs:</span></span>

    * [<span data-ttu-id="17c1a-134">Obtenha uma lista de disponibilidades para um SKU</span><span class="sxs-lookup"><span data-stu-id="17c1a-134">Get a list of availabilities for a SKU</span></span>](get-a-list-of-availabilities-for-a-sku.md)
    * [<span data-ttu-id="17c1a-135">Obtenha uma disponibilidade usando o ID de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="17c1a-135">Get an availability using the availability ID</span></span>](get-an-availability-by-id.md)

## <a name="create-and-submit-an-order"></a><span data-ttu-id="17c1a-136">Criar e submeter uma encomenda</span><span class="sxs-lookup"><span data-stu-id="17c1a-136">Create and submit an order</span></span>

<span data-ttu-id="17c1a-137">Para submeter a sua ordem de reserva Azure, siga estes passos:</span><span class="sxs-lookup"><span data-stu-id="17c1a-137">To submit your Azure reservation order, follow these steps:</span></span>

1. <span data-ttu-id="17c1a-138">[Crie um carrinho](create-a-cart.md) para guardar a coleção de itens de catálogo que pretende comprar.</span><span class="sxs-lookup"><span data-stu-id="17c1a-138">[Create a cart](create-a-cart.md) to hold the collection of catalog items that you intend to buy.</span></span> <span data-ttu-id="17c1a-139">Ao criar um [carrinho,](cart-resources.md#cart)os [itens](cart-resources.md#cartlineitem) da linha do carrinho são automaticamente agrupados com base no que pode ser comprado em conjunto na mesma [ordem](order-resources.md#order).</span><span class="sxs-lookup"><span data-stu-id="17c1a-139">When you create a [cart](cart-resources.md#cart), the [cart line items](cart-resources.md#cartlineitem) are automatically grouped based on what can be purchased together in the same [order](order-resources.md#order).</span></span> <span data-ttu-id="17c1a-140">(Também pode [atualizar um carrinho.)](update-a-cart.md)</span><span class="sxs-lookup"><span data-stu-id="17c1a-140">(You can also [update a cart](update-a-cart.md).)</span></span>
2. <span data-ttu-id="17c1a-141">[Confira o carrinho,](checkout-a-cart.md)que resulta na criação de uma [encomenda.](order-resources.md#order)</span><span class="sxs-lookup"><span data-stu-id="17c1a-141">[Check out the cart](checkout-a-cart.md), which results in the creation of an [order](order-resources.md#order).</span></span>

### <a name="get-order-details"></a><span data-ttu-id="17c1a-142">Obter detalhes da encomenda</span><span class="sxs-lookup"><span data-stu-id="17c1a-142">Get order details</span></span>

<span data-ttu-id="17c1a-143">Pode [recuperar os detalhes de uma encomenda individual utilizando o ID da encomenda](get-an-order-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="17c1a-143">You can [retrieve the details of an individual order using the order ID](get-an-order-by-id.md).</span></span> <span data-ttu-id="17c1a-144">Também pode [obter uma lista de todas as encomendas para um cliente específico.](get-all-of-a-customer-s-orders.md)</span><span class="sxs-lookup"><span data-stu-id="17c1a-144">You can also [retrieve a list of all orders for a specific customer](get-all-of-a-customer-s-orders.md).</span></span>

> [!NOTE]
> <span data-ttu-id="17c1a-145">Após a entrega de uma encomenda, há um atraso de até 15 minutos antes da encomenda aparecer na lista de pedidos do cliente.</span><span class="sxs-lookup"><span data-stu-id="17c1a-145">After an order is submitted, there is a delay of up to 15 minutes before the order appears in that customer's order list.</span></span>

## <a name="get-activation-link"></a><span data-ttu-id="17c1a-146">Obtenha ligação de ativação</span><span class="sxs-lookup"><span data-stu-id="17c1a-146">Get activation link</span></span>

<span data-ttu-id="17c1a-147">O parceiro ou cliente deve ativar subscrições de produtos Azure Marketplace.</span><span class="sxs-lookup"><span data-stu-id="17c1a-147">The partner or customer must activate subscriptions to Azure Marketplace products.</span></span> <span data-ttu-id="17c1a-148">Pode [obter um link de ativação por linha de encomenda](get-activation-link-by-order-line-item.md).</span><span class="sxs-lookup"><span data-stu-id="17c1a-148">You can [get an activation link by order line item](get-activation-link-by-order-line-item.md).</span></span> <span data-ttu-id="17c1a-149">Também pode [obter uma subscrição por ID,](get-a-subscription-by-id.md)enumerando depois a propriedade **Links** para criar uma ligação de ativação.</span><span class="sxs-lookup"><span data-stu-id="17c1a-149">You can also [get a subscription by ID](get-a-subscription-by-id.md), then enumerate its **Links** property to create an activation link.</span></span>

## <a name="lifecycle-management"></a><span data-ttu-id="17c1a-150">Gestão do ciclo de vida</span><span class="sxs-lookup"><span data-stu-id="17c1a-150">Lifecycle management</span></span>

<span data-ttu-id="17c1a-151">Pode gerir o ciclo de vida das suas subscrições a produtos de mercado comercial utilizando os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="17c1a-151">You can manage the lifecycle of your subscriptions to commercial marketplace products using the following methods:</span></span>

* [<span data-ttu-id="17c1a-152">Cancelar uma subscrição de marketplace comercial</span><span class="sxs-lookup"><span data-stu-id="17c1a-152">Cancel a commercial marketplace subscription</span></span>](cancel-an-azure-marketplace-subscription.md)
* [<span data-ttu-id="17c1a-153">Permitir ou desativar novamente a autoria para uma subscrição de mercado comercial</span><span class="sxs-lookup"><span data-stu-id="17c1a-153">Enable or disable autorenew for a commercial marketplace subscription</span></span>](update-autorenew-for-an-azure-marketplace-subscription.md)

## <a name="quantity-management"></a><span data-ttu-id="17c1a-154">Gestão de quantidades</span><span class="sxs-lookup"><span data-stu-id="17c1a-154">Quantity management</span></span>

<span data-ttu-id="17c1a-155">A quantidade de uma subscrição de mercado comercial deve estar dentro dos limites definidos pelo seu [SKU](product-resources.md#sku) associado (ver os **atributos mínimos deQuantidade** equantidade). </span><span class="sxs-lookup"><span data-stu-id="17c1a-155">The quantity of a commercial marketplace subscription must be within the limits defined by its associated [SKU](product-resources.md#sku) (see the **minimumQuantity** and **maximumQuantity** attributes).</span></span> <span data-ttu-id="17c1a-156">Para atualizar a quantidade de uma subscrição de mercado comercial, utilize o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="17c1a-156">To update the quantity of a commercial marketplace subscription, use the following method:</span></span>

* [<span data-ttu-id="17c1a-157">Alterar a quantidade de uma subscrição</span><span class="sxs-lookup"><span data-stu-id="17c1a-157">Change the quantity of a subscription</span></span>](change-the-quantity-of-a-subscription.md)

## <a name="invoice-and-reconciliation"></a><span data-ttu-id="17c1a-158">Fatura e reconciliação</span><span class="sxs-lookup"><span data-stu-id="17c1a-158">Invoice and reconciliation</span></span>

<span data-ttu-id="17c1a-159">Pode gerir [faturas de clientes](invoice-resources.md) (incluindo taxas para subscrições de produtos de mercado comercial) utilizando os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="17c1a-159">You can manage customer [invoices](invoice-resources.md) (including charges for subscriptions to commercial marketplace products) using the following methods:</span></span>

* [<span data-ttu-id="17c1a-160">Obtenha faturas de produtos da linha de consumo de mercado comercial</span><span class="sxs-lookup"><span data-stu-id="17c1a-160">Get invoice billed commercial marketplace consumption line items</span></span>](get-invoice-billed-consumption-lineitems.md)
* [<span data-ttu-id="17c1a-161">Obter ligações de estimativa da fatura</span><span class="sxs-lookup"><span data-stu-id="17c1a-161">Get invoice estimate links</span></span>](get-invoice-estimate-links.md)
* [<span data-ttu-id="17c1a-162">Obter faturas sem faturas de produtos de linha de consumo de mercado comercial</span><span class="sxs-lookup"><span data-stu-id="17c1a-162">Get invoice unbilled commercial marketplace consumption line items</span></span>](get-invoice-unbilled-consumption-lineitems.md)
* [<span data-ttu-id="17c1a-163">Obtenha itens de linha de reconciliação sem faturação</span><span class="sxs-lookup"><span data-stu-id="17c1a-163">Get invoice unbilled reconciliation line items</span></span>](get-invoice-unbilled-recon-lineitems.md)

## <a name="test-using-integration-sandbox-account"></a><span data-ttu-id="17c1a-164">Teste utilizando a conta de caixa de areia de integração</span><span class="sxs-lookup"><span data-stu-id="17c1a-164">Test using integration sandbox account</span></span>

<span data-ttu-id="17c1a-165">Na produção, depois de ter criado uma subscrição de produtos SaaS de marketplace comercial, precisa de recuperar uma ligação de ativação personalizada do Partner Center e visitar o site da editora para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="17c1a-165">In production, after you have created a subscription to commercial marketplace SaaS products, you need to retrieve a personalized activation link from Partner Center and visit the publisher's site to complete the setup process.</span></span> <span data-ttu-id="17c1a-166">A faturação da subscrição só começará depois de a configuração estar concluída.</span><span class="sxs-lookup"><span data-stu-id="17c1a-166">Subscription billing will begin only after setup is complete.</span></span>

<span data-ttu-id="17c1a-167">No ambiente da caixa de areia da CSP, não existe integração com os ISVs.</span><span class="sxs-lookup"><span data-stu-id="17c1a-167">In the CSP sandbox environment, there is no integration with ISVs.</span></span> <span data-ttu-id="17c1a-168">Se tentar recuperar uma ligação de ativação do Partner Center, será devolvido um link falso.</span><span class="sxs-lookup"><span data-stu-id="17c1a-168">If you try to retrieve an activation link from Partner Center, a dummy link will be returned.</span></span> <span data-ttu-id="17c1a-169">Não é possível utilizar este link falso para completar o processo de configuração no site da editora.</span><span class="sxs-lookup"><span data-stu-id="17c1a-169">You cannot use this dummy link to complete the setup process at the publisher's site.</span></span> <span data-ttu-id="17c1a-170">Para utilizar a conta de sandbox de integração para testar a faturação para subscrições de produtos SaaS de marketplace comercial, utilize o seguinte método para ativar a subscrição.</span><span class="sxs-lookup"><span data-stu-id="17c1a-170">To use the integration sandbox account to test billing for subscriptions to commercial marketplace SaaS products, use the following method to activate the subscription instead.</span></span> <span data-ttu-id="17c1a-171">A faturação da subscrição começará após a ativação bem sucedida:</span><span class="sxs-lookup"><span data-stu-id="17c1a-171">Subscription billing will begin after successful activation:</span></span>

* [<span data-ttu-id="17c1a-172">Ativar uma subscrição de sandbox para produtos de mercado comercial</span><span class="sxs-lookup"><span data-stu-id="17c1a-172">Activate a sandbox subscription for commercial marketplace products</span></span>](activate-sandbox-subscription-azure-marketplace-products.md)

