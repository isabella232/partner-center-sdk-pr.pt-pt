---
title: Atualizar um carrinho
description: Como atualizar um pedido para um cliente em um carrinho.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8954d4dad39f9b1a1b9a2f213e0231f01856fcd2
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446688"
---
# <a name="update-a-cart"></a><span data-ttu-id="a5a74-103">Atualizar um carrinho</span><span class="sxs-lookup"><span data-stu-id="a5a74-103">Update a cart</span></span>

<span data-ttu-id="a5a74-104">Como atualizar um pedido para um cliente em um carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-104">How to update an order for a customer in a cart.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5a74-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a5a74-105">Prerequisites</span></span>

- <span data-ttu-id="a5a74-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a5a74-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a5a74-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="a5a74-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="a5a74-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a5a74-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a5a74-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="a5a74-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a5a74-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="a5a74-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a5a74-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="a5a74-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a5a74-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="a5a74-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a5a74-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a5a74-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="a5a74-114">Uma identificação do carrinho para um carrinho existente.</span><span class="sxs-lookup"><span data-stu-id="a5a74-114">A Cart ID for an existing cart.</span></span>

## <a name="c"></a><span data-ttu-id="a5a74-115">C\#</span><span class="sxs-lookup"><span data-stu-id="a5a74-115">C\#</span></span>

<span data-ttu-id="a5a74-116">Para atualizar uma encomenda para um cliente, obtenha o carrinho utilizando o método **Get()** passando os IDs do cliente e do carrinho utilizando a função **ById().**</span><span class="sxs-lookup"><span data-stu-id="a5a74-116">To update an order for a customer, get the cart using the **Get()** method by passing the customer and cart IDs using the **ById()** function.</span></span> <span data-ttu-id="a5a74-117">Faça as alterações necessárias no carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-117">Make the necessary changes to the cart.</span></span> <span data-ttu-id="a5a74-118">Agora ligue para o método **Put** utilizando iDs de cliente e carrinho usando o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="a5a74-118">Now call the **Put** method by using customer and cart IDs using the **ById()** method.</span></span>

<span data-ttu-id="a5a74-119">Por fim, ligue para o método **Put()** ou **PutAsync** para criar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="a5a74-119">Finally, call the **Put()** or **PutAsync()** method to create the order.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Get();

cart.LineItems.ToArray()[0].Quantity++;

var updatedCart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Put(cart);
```

## <a name="rest-request"></a><span data-ttu-id="a5a74-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="a5a74-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a5a74-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5a74-121">Request syntax</span></span>

| <span data-ttu-id="a5a74-122">Método</span><span class="sxs-lookup"><span data-stu-id="a5a74-122">Method</span></span>  | <span data-ttu-id="a5a74-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="a5a74-123">Request URI</span></span>                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a5a74-124">**PUT**</span><span class="sxs-lookup"><span data-stu-id="a5a74-124">**PUT**</span></span> | <span data-ttu-id="a5a74-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts/{cart-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a5a74-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts/{cart-id} HTTP/1.1</span></span>              |

### <a name="uri-parameters"></a><span data-ttu-id="a5a74-126">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="a5a74-126">URI parameters</span></span>

<span data-ttu-id="a5a74-127">Utilize os seguintes parâmetros de trajetória para identificar o cliente e especifique o carrinho a atualizar.</span><span class="sxs-lookup"><span data-stu-id="a5a74-127">Use the following path parameters to identify the customer, and specify the cart to be updated.</span></span>

| <span data-ttu-id="a5a74-128">Nome</span><span class="sxs-lookup"><span data-stu-id="a5a74-128">Name</span></span>            | <span data-ttu-id="a5a74-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="a5a74-129">Type</span></span>     | <span data-ttu-id="a5a74-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="a5a74-130">Required</span></span> | <span data-ttu-id="a5a74-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5a74-131">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="a5a74-132">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="a5a74-132">**customer-id**</span></span> | <span data-ttu-id="a5a74-133">string</span><span class="sxs-lookup"><span data-stu-id="a5a74-133">string</span></span>   | <span data-ttu-id="a5a74-134">Yes</span><span class="sxs-lookup"><span data-stu-id="a5a74-134">Yes</span></span>      | <span data-ttu-id="a5a74-135">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="a5a74-135">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="a5a74-136">**cart-id**</span><span class="sxs-lookup"><span data-stu-id="a5a74-136">**cart-id**</span></span>     | <span data-ttu-id="a5a74-137">string</span><span class="sxs-lookup"><span data-stu-id="a5a74-137">string</span></span>   | <span data-ttu-id="a5a74-138">Yes</span><span class="sxs-lookup"><span data-stu-id="a5a74-138">Yes</span></span>      | <span data-ttu-id="a5a74-139">Um carro-id formatado GUID que identifica o carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-139">A GUID formatted cart-id that identifies the cart.</span></span>                     |

### <a name="request-headers"></a><span data-ttu-id="a5a74-140">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="a5a74-140">Request headers</span></span>

<span data-ttu-id="a5a74-141">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a5a74-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a5a74-142">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="a5a74-142">Request body</span></span>

<span data-ttu-id="a5a74-143">Esta tabela descreve as propriedades do [Carrinho](cart-resources.md) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="a5a74-143">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="a5a74-144">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a5a74-144">Property</span></span>              | <span data-ttu-id="a5a74-145">Tipo</span><span class="sxs-lookup"><span data-stu-id="a5a74-145">Type</span></span>             | <span data-ttu-id="a5a74-146">Necessário</span><span class="sxs-lookup"><span data-stu-id="a5a74-146">Required</span></span>        | <span data-ttu-id="a5a74-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5a74-147">Description</span></span>                                                                                               |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a5a74-148">ID</span><span class="sxs-lookup"><span data-stu-id="a5a74-148">id</span></span>                    | <span data-ttu-id="a5a74-149">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="a5a74-149">string</span></span>           | <span data-ttu-id="a5a74-150">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-150">No</span></span>              | <span data-ttu-id="a5a74-151">Um identificador de carrinhos que é fornecido após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-151">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="a5a74-152">criaçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="a5a74-152">creationTimeStamp</span></span>     | <span data-ttu-id="a5a74-153">DateTime</span><span class="sxs-lookup"><span data-stu-id="a5a74-153">DateTime</span></span>         | <span data-ttu-id="a5a74-154">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-154">No</span></span>              | <span data-ttu-id="a5a74-155">A data em que o carrinho foi criado, em formato de data- hora.</span><span class="sxs-lookup"><span data-stu-id="a5a74-155">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="a5a74-156">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-156">Applied upon successful creation of the cart.</span></span>        |
| <span data-ttu-id="a5a74-157">últimampadatimestamp de Tempos</span><span class="sxs-lookup"><span data-stu-id="a5a74-157">lastModifiedTimeStamp</span></span> | <span data-ttu-id="a5a74-158">DateTime</span><span class="sxs-lookup"><span data-stu-id="a5a74-158">DateTime</span></span>         | <span data-ttu-id="a5a74-159">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-159">No</span></span>              | <span data-ttu-id="a5a74-160">A data em que o carrinho foi atualizado pela última vez, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="a5a74-160">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="a5a74-161">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-161">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="a5a74-162">expiraçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="a5a74-162">expirationTimeStamp</span></span>   | <span data-ttu-id="a5a74-163">DateTime</span><span class="sxs-lookup"><span data-stu-id="a5a74-163">DateTime</span></span>         | <span data-ttu-id="a5a74-164">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-164">No</span></span>              | <span data-ttu-id="a5a74-165">A data em que o carrinho expirará, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="a5a74-165">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="a5a74-166">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-166">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="a5a74-167">últimoModifiedUser</span><span class="sxs-lookup"><span data-stu-id="a5a74-167">lastModifiedUser</span></span>      | <span data-ttu-id="a5a74-168">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="a5a74-168">string</span></span>           | <span data-ttu-id="a5a74-169">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-169">No</span></span>              | <span data-ttu-id="a5a74-170">O utilizador que atualizou pela última vez o carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-170">The user who last updated the cart.</span></span> <span data-ttu-id="a5a74-171">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-171">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="a5a74-172">lineitems</span><span class="sxs-lookup"><span data-stu-id="a5a74-172">lineItems</span></span>             | <span data-ttu-id="a5a74-173">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="a5a74-173">Array of objects</span></span> | <span data-ttu-id="a5a74-174">Yes</span><span class="sxs-lookup"><span data-stu-id="a5a74-174">Yes</span></span>             | <span data-ttu-id="a5a74-175">Uma matriz de recursos [CartLineItem.](cart-resources.md#cartlineitem)</span><span class="sxs-lookup"><span data-stu-id="a5a74-175">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                               |

<span data-ttu-id="a5a74-176">Esta tabela descreve as propriedades [do CartLineItem](cart-resources.md#cartlineitem) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="a5a74-176">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

| <span data-ttu-id="a5a74-177">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a5a74-177">Property</span></span>             | <span data-ttu-id="a5a74-178">Tipo</span><span class="sxs-lookup"><span data-stu-id="a5a74-178">Type</span></span>                        | <span data-ttu-id="a5a74-179">Necessário</span><span class="sxs-lookup"><span data-stu-id="a5a74-179">Required</span></span>     | <span data-ttu-id="a5a74-180">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5a74-180">Description</span></span>                                                                                        |
|----------------------|-----------------------------|--------------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a5a74-181">ID</span><span class="sxs-lookup"><span data-stu-id="a5a74-181">id</span></span>                   | <span data-ttu-id="a5a74-182">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="a5a74-182">string</span></span>                      | <span data-ttu-id="a5a74-183">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-183">No</span></span>           | <span data-ttu-id="a5a74-184">Um identificador único para um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-184">A Unique identifier for a cart line item.</span></span> <span data-ttu-id="a5a74-185">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="a5a74-185">Applied upon successful creation of cart.</span></span>                |
| <span data-ttu-id="a5a74-186">catalogId</span><span class="sxs-lookup"><span data-stu-id="a5a74-186">catalogId</span></span>            | <span data-ttu-id="a5a74-187">string</span><span class="sxs-lookup"><span data-stu-id="a5a74-187">string</span></span>                      | <span data-ttu-id="a5a74-188">Yes</span><span class="sxs-lookup"><span data-stu-id="a5a74-188">Yes</span></span>          | <span data-ttu-id="a5a74-189">O identificador de artigos de catálogo.</span><span class="sxs-lookup"><span data-stu-id="a5a74-189">The catalog item identifier.</span></span>                                                                       |
| <span data-ttu-id="a5a74-190">nome amigável</span><span class="sxs-lookup"><span data-stu-id="a5a74-190">friendlyName</span></span>         | <span data-ttu-id="a5a74-191">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="a5a74-191">string</span></span>                      | <span data-ttu-id="a5a74-192">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-192">No</span></span>           | <span data-ttu-id="a5a74-193">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a5a74-193">Optional.</span></span> <span data-ttu-id="a5a74-194">O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="a5a74-194">The friendly name for the item defined by the partner to help disambiguate.</span></span>              |
| <span data-ttu-id="a5a74-195">quantidade</span><span class="sxs-lookup"><span data-stu-id="a5a74-195">quantity</span></span>             | <span data-ttu-id="a5a74-196">int</span><span class="sxs-lookup"><span data-stu-id="a5a74-196">int</span></span>                         | <span data-ttu-id="a5a74-197">Yes</span><span class="sxs-lookup"><span data-stu-id="a5a74-197">Yes</span></span>          | <span data-ttu-id="a5a74-198">O número de licenças ou instâncias.</span><span class="sxs-lookup"><span data-stu-id="a5a74-198">The number of licenses or instances.</span></span>     |
| <span data-ttu-id="a5a74-199">currencyCode</span><span class="sxs-lookup"><span data-stu-id="a5a74-199">currencyCode</span></span>         | <span data-ttu-id="a5a74-200">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="a5a74-200">string</span></span>                      | <span data-ttu-id="a5a74-201">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-201">No</span></span>           | <span data-ttu-id="a5a74-202">O código da moeda.</span><span class="sxs-lookup"><span data-stu-id="a5a74-202">The currency code.</span></span>                                                                                 |
| <span data-ttu-id="a5a74-203">billingCycle</span><span class="sxs-lookup"><span data-stu-id="a5a74-203">billingCycle</span></span>         | <span data-ttu-id="a5a74-204">Objeto</span><span class="sxs-lookup"><span data-stu-id="a5a74-204">Object</span></span>                      | <span data-ttu-id="a5a74-205">Yes</span><span class="sxs-lookup"><span data-stu-id="a5a74-205">Yes</span></span>          | <span data-ttu-id="a5a74-206">O tipo de ciclo de faturação definido para o período atual.</span><span class="sxs-lookup"><span data-stu-id="a5a74-206">The type of billing cycle set for the current period.</span></span>                                              |
| <span data-ttu-id="a5a74-207">participantes</span><span class="sxs-lookup"><span data-stu-id="a5a74-207">participants</span></span>         | <span data-ttu-id="a5a74-208">Lista de pares de cordas de objeto</span><span class="sxs-lookup"><span data-stu-id="a5a74-208">List of Object String pairs</span></span> | <span data-ttu-id="a5a74-209">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-209">No</span></span>           | <span data-ttu-id="a5a74-210">Uma coleção de participantes na compra.</span><span class="sxs-lookup"><span data-stu-id="a5a74-210">A collection of participants on the purchase.</span></span>                                                      |
| <span data-ttu-id="a5a74-211">provisionamentoContexto</span><span class="sxs-lookup"><span data-stu-id="a5a74-211">provisioningContext</span></span>  | <span data-ttu-id="a5a74-212">Cadeia de<do dicionário,> de cordas</span><span class="sxs-lookup"><span data-stu-id="a5a74-212">Dictionary<string, string></span></span>  | <span data-ttu-id="a5a74-213">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-213">No</span></span>           | <span data-ttu-id="a5a74-214">Um contexto utilizado para o provisionamento da oferta.</span><span class="sxs-lookup"><span data-stu-id="a5a74-214">A context used for provisioning of offer.</span></span>                                                          |
| <span data-ttu-id="a5a74-215">orderGroup</span><span class="sxs-lookup"><span data-stu-id="a5a74-215">orderGroup</span></span>           | <span data-ttu-id="a5a74-216">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="a5a74-216">string</span></span>                      | <span data-ttu-id="a5a74-217">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-217">No</span></span>           | <span data-ttu-id="a5a74-218">Um grupo para indicar quais os itens que podem ser colocados juntos.</span><span class="sxs-lookup"><span data-stu-id="a5a74-218">A group to indicate which items can be placed together.</span></span>                                            |
| <span data-ttu-id="a5a74-219">erro</span><span class="sxs-lookup"><span data-stu-id="a5a74-219">error</span></span>                | <span data-ttu-id="a5a74-220">Objeto</span><span class="sxs-lookup"><span data-stu-id="a5a74-220">Object</span></span>                      | <span data-ttu-id="a5a74-221">No</span><span class="sxs-lookup"><span data-stu-id="a5a74-221">No</span></span>           | <span data-ttu-id="a5a74-222">Aplicado após o carrinho é criado em caso de erro.</span><span class="sxs-lookup"><span data-stu-id="a5a74-222">Applied after cart is created in case of an error.</span></span>                                                 |

### <a name="request-example"></a><span data-ttu-id="a5a74-223">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a5a74-223">Request example</span></span>

```http
PUT /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/65faf57b-0205-47ee-92b3-08dcf233ea73/ HTTP/1.1
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
    {
        "Id":"b4c8fdea-cbe4-4d17-9576-13fcacbf9605",
        "CreationTimestamp":"2018-03-15T17:15:02.3840528Z",
        "LastModifiedTimestamp":"2018-03-15T17:15:02.3840528Z",
        "ExpirationTimestamp":"0001-01-01T00:00:00",
        "LastModifiedUser":"2713ccd7-ea3b-470a-9cfb-451d5d0482cc",
        "LineItems":[
            {
                "Id":0,
                "CatalogItemId":"DG7GMGF0DWTL:0001:DG7GMGF0DSJB",
                "FriendlyName":"A_sample_Azure_RI",
                "Quantity":2,
                "BillingCycle":"one_time",
                "ProvisioningContext": {
                    "SubscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
                    "Scope": "shared",
                    "Duration": "1Year"
                }
            }
        ],
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="a5a74-224">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="a5a74-224">REST response</span></span>

<span data-ttu-id="a5a74-225">Se for bem sucedido, este método devolve o recurso [cart](cart-resources.md) povoado no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="a5a74-225">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a5a74-226">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="a5a74-226">Response success and error codes</span></span>

<span data-ttu-id="a5a74-227">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="a5a74-227">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a5a74-228">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="a5a74-228">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a5a74-229">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="a5a74-229">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a5a74-230">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a5a74-230">Response example</span></span>

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
    "id": "b4c8fdea-cbe4-4d17-9576-13fcacbf9605",
    "creationTimestamp": "2018-03-15T17:15:02.3840528Z",
    "lastModifiedTimestamp": "2018-03-15T17:15:02.3840528Z",
    "lastModifiedUser": "2713ccd7-ea3b-470a-9cfb-451d5d0482cc",
    "lineItems": [
        {
            "id": 0,
            "catalogItemId": "DG7GMGF0DWTL:0001:DG7GMGF0DSJB",
            "friendlyName": "A_sample_Azure_RI",
            "quantity": 2,
            "currencyCode": "USD",
            "billingCycle": "one_time",
            "ProvisioningContext": {
                "subscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
                "scope": "shared",
                "duration": "1Year"
            }
            "orderGroup": "0"
        }
    ],
    "links": {
        "self": {
            "uri": "/v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/b4c8fdea-cbe4-4d17-9576-13fcacbf9605/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Cart"
    }
}
```
