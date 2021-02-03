---
title: Atualizar um carrinho
description: Como atualizar um pedido para um cliente em um carrinho.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7c0806ccc87281b9b34005f22cd8d6ad57fb5de5
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768941"
---
# <a name="update-a-cart"></a><span data-ttu-id="bfc51-103">Atualizar um carrinho</span><span class="sxs-lookup"><span data-stu-id="bfc51-103">Update a cart</span></span>

<span data-ttu-id="bfc51-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="bfc51-104">**Applies To**</span></span>

- <span data-ttu-id="bfc51-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="bfc51-105">Partner Center</span></span>

<span data-ttu-id="bfc51-106">Como atualizar um pedido para um cliente em um carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-106">How to update an order for a customer in a cart.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bfc51-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bfc51-107">Prerequisites</span></span>

- <span data-ttu-id="bfc51-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bfc51-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bfc51-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="bfc51-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="bfc51-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bfc51-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="bfc51-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="bfc51-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="bfc51-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="bfc51-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="bfc51-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="bfc51-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="bfc51-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="bfc51-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="bfc51-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bfc51-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="bfc51-116">Uma identificação do carrinho para um carrinho existente.</span><span class="sxs-lookup"><span data-stu-id="bfc51-116">A Cart ID for an existing cart.</span></span>

## <a name="c"></a><span data-ttu-id="bfc51-117">C\#</span><span class="sxs-lookup"><span data-stu-id="bfc51-117">C\#</span></span>

<span data-ttu-id="bfc51-118">Para atualizar uma encomenda para um cliente, obtenha o carrinho utilizando o método **Get()** passando o ID do cliente e do carrinho utilizando a função **ById().**</span><span class="sxs-lookup"><span data-stu-id="bfc51-118">To update an order for a customer, get the cart using the **Get()** method by passing the customer and cart ID's using the **ById()** function.</span></span> <span data-ttu-id="bfc51-119">Faça as alterações necessárias no carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-119">Make the necessary changes to the cart.</span></span> <span data-ttu-id="bfc51-120">Agora ligue para o método **Put** utilizando o iD do cliente e do carrinho utilizando o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="bfc51-120">Now call the **Put** method by using customer and cart ID's using the **ById()** method.</span></span>

<span data-ttu-id="bfc51-121">Por fim, ligue para o método **Put()** ou **PutAsync** para criar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="bfc51-121">Finally, call the **Put()** or **PutAsync()** method to create the order.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Get();

cart.LineItems.ToArray()[0].Quantity++;

var updatedCart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Put(cart);
```

## <a name="rest-request"></a><span data-ttu-id="bfc51-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="bfc51-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bfc51-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfc51-123">Request syntax</span></span>

| <span data-ttu-id="bfc51-124">Método</span><span class="sxs-lookup"><span data-stu-id="bfc51-124">Method</span></span>  | <span data-ttu-id="bfc51-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="bfc51-125">Request URI</span></span>                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bfc51-126">**PUT**</span><span class="sxs-lookup"><span data-stu-id="bfc51-126">**PUT**</span></span> | <span data-ttu-id="bfc51-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts/{cart-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="bfc51-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts/{cart-id} HTTP/1.1</span></span>              |

### <a name="uri-parameters"></a><span data-ttu-id="bfc51-128">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="bfc51-128">URI parameters</span></span>

<span data-ttu-id="bfc51-129">Utilize os seguintes parâmetros de trajetória para identificar o cliente e especifique o carrinho a atualizar.</span><span class="sxs-lookup"><span data-stu-id="bfc51-129">Use the following path parameters to identify the customer, and specify the cart to be updated.</span></span>

| <span data-ttu-id="bfc51-130">Nome</span><span class="sxs-lookup"><span data-stu-id="bfc51-130">Name</span></span>            | <span data-ttu-id="bfc51-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="bfc51-131">Type</span></span>     | <span data-ttu-id="bfc51-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="bfc51-132">Required</span></span> | <span data-ttu-id="bfc51-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfc51-133">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="bfc51-134">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="bfc51-134">**customer-id**</span></span> | <span data-ttu-id="bfc51-135">string</span><span class="sxs-lookup"><span data-stu-id="bfc51-135">string</span></span>   | <span data-ttu-id="bfc51-136">Sim</span><span class="sxs-lookup"><span data-stu-id="bfc51-136">Yes</span></span>      | <span data-ttu-id="bfc51-137">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="bfc51-137">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="bfc51-138">**cart-id**</span><span class="sxs-lookup"><span data-stu-id="bfc51-138">**cart-id**</span></span>     | <span data-ttu-id="bfc51-139">string</span><span class="sxs-lookup"><span data-stu-id="bfc51-139">string</span></span>   | <span data-ttu-id="bfc51-140">Sim</span><span class="sxs-lookup"><span data-stu-id="bfc51-140">Yes</span></span>      | <span data-ttu-id="bfc51-141">Um carro-id formatado GUID que identifica o carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-141">A GUID formatted cart-id that identifies the cart.</span></span>                     |

### <a name="request-headers"></a><span data-ttu-id="bfc51-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="bfc51-142">Request headers</span></span>

<span data-ttu-id="bfc51-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="bfc51-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bfc51-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="bfc51-144">Request body</span></span>

<span data-ttu-id="bfc51-145">Esta tabela descreve as propriedades do [Carrinho](cart-resources.md) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="bfc51-145">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="bfc51-146">Propriedade</span><span class="sxs-lookup"><span data-stu-id="bfc51-146">Property</span></span>              | <span data-ttu-id="bfc51-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="bfc51-147">Type</span></span>             | <span data-ttu-id="bfc51-148">Necessário</span><span class="sxs-lookup"><span data-stu-id="bfc51-148">Required</span></span>        | <span data-ttu-id="bfc51-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfc51-149">Description</span></span>                                                                                               |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bfc51-150">ID</span><span class="sxs-lookup"><span data-stu-id="bfc51-150">id</span></span>                    | <span data-ttu-id="bfc51-151">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="bfc51-151">string</span></span>           | <span data-ttu-id="bfc51-152">No</span><span class="sxs-lookup"><span data-stu-id="bfc51-152">No</span></span>              | <span data-ttu-id="bfc51-153">Um identificador de carrinhos que é fornecido após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-153">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="bfc51-154">criaçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="bfc51-154">creationTimeStamp</span></span>     | <span data-ttu-id="bfc51-155">DateTime</span><span class="sxs-lookup"><span data-stu-id="bfc51-155">DateTime</span></span>         | <span data-ttu-id="bfc51-156">Não</span><span class="sxs-lookup"><span data-stu-id="bfc51-156">No</span></span>              | <span data-ttu-id="bfc51-157">A data em que o carrinho foi criado, em formato de data- hora.</span><span class="sxs-lookup"><span data-stu-id="bfc51-157">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="bfc51-158">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-158">Applied upon successful creation of the cart.</span></span>        |
| <span data-ttu-id="bfc51-159">últimampadatimestamp de Tempos</span><span class="sxs-lookup"><span data-stu-id="bfc51-159">lastModifiedTimeStamp</span></span> | <span data-ttu-id="bfc51-160">DateTime</span><span class="sxs-lookup"><span data-stu-id="bfc51-160">DateTime</span></span>         | <span data-ttu-id="bfc51-161">Não</span><span class="sxs-lookup"><span data-stu-id="bfc51-161">No</span></span>              | <span data-ttu-id="bfc51-162">A data em que o carrinho foi atualizado pela última vez, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="bfc51-162">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="bfc51-163">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-163">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="bfc51-164">expiraçãoTimeStamp</span><span class="sxs-lookup"><span data-stu-id="bfc51-164">expirationTimeStamp</span></span>   | <span data-ttu-id="bfc51-165">DateTime</span><span class="sxs-lookup"><span data-stu-id="bfc51-165">DateTime</span></span>         | <span data-ttu-id="bfc51-166">Não</span><span class="sxs-lookup"><span data-stu-id="bfc51-166">No</span></span>              | <span data-ttu-id="bfc51-167">A data em que o carrinho expirará, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="bfc51-167">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="bfc51-168">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-168">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="bfc51-169">últimoModifiedUser</span><span class="sxs-lookup"><span data-stu-id="bfc51-169">lastModifiedUser</span></span>      | <span data-ttu-id="bfc51-170">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="bfc51-170">string</span></span>           | <span data-ttu-id="bfc51-171">No</span><span class="sxs-lookup"><span data-stu-id="bfc51-171">No</span></span>              | <span data-ttu-id="bfc51-172">O utilizador que atualizou pela última vez o carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-172">The user who last updated the cart.</span></span> <span data-ttu-id="bfc51-173">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-173">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="bfc51-174">lineitems</span><span class="sxs-lookup"><span data-stu-id="bfc51-174">lineItems</span></span>             | <span data-ttu-id="bfc51-175">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="bfc51-175">Array of objects</span></span> | <span data-ttu-id="bfc51-176">Sim</span><span class="sxs-lookup"><span data-stu-id="bfc51-176">Yes</span></span>             | <span data-ttu-id="bfc51-177">Uma matriz de recursos [CartLineItem.](cart-resources.md#cartlineitem)</span><span class="sxs-lookup"><span data-stu-id="bfc51-177">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                               |

<span data-ttu-id="bfc51-178">Esta tabela descreve as propriedades [do CartLineItem](cart-resources.md#cartlineitem) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="bfc51-178">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

| <span data-ttu-id="bfc51-179">Propriedade</span><span class="sxs-lookup"><span data-stu-id="bfc51-179">Property</span></span>             | <span data-ttu-id="bfc51-180">Tipo</span><span class="sxs-lookup"><span data-stu-id="bfc51-180">Type</span></span>                        | <span data-ttu-id="bfc51-181">Necessário</span><span class="sxs-lookup"><span data-stu-id="bfc51-181">Required</span></span>     | <span data-ttu-id="bfc51-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfc51-182">Description</span></span>                                                                                        |
|----------------------|-----------------------------|--------------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bfc51-183">ID</span><span class="sxs-lookup"><span data-stu-id="bfc51-183">id</span></span>                   | <span data-ttu-id="bfc51-184">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="bfc51-184">string</span></span>                      | <span data-ttu-id="bfc51-185">No</span><span class="sxs-lookup"><span data-stu-id="bfc51-185">No</span></span>           | <span data-ttu-id="bfc51-186">Um identificador único para um item de linha de carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-186">A Unique identifier for a cart line item.</span></span> <span data-ttu-id="bfc51-187">Aplicado após a criação bem sucedida do carrinho.</span><span class="sxs-lookup"><span data-stu-id="bfc51-187">Applied upon successful creation of cart.</span></span>                |
| <span data-ttu-id="bfc51-188">catalogId</span><span class="sxs-lookup"><span data-stu-id="bfc51-188">catalogId</span></span>            | <span data-ttu-id="bfc51-189">string</span><span class="sxs-lookup"><span data-stu-id="bfc51-189">string</span></span>                      | <span data-ttu-id="bfc51-190">Sim</span><span class="sxs-lookup"><span data-stu-id="bfc51-190">Yes</span></span>          | <span data-ttu-id="bfc51-191">O identificador de artigos de catálogo.</span><span class="sxs-lookup"><span data-stu-id="bfc51-191">The catalog item identifier.</span></span>                                                                       |
| <span data-ttu-id="bfc51-192">nome amigável</span><span class="sxs-lookup"><span data-stu-id="bfc51-192">friendlyName</span></span>         | <span data-ttu-id="bfc51-193">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="bfc51-193">string</span></span>                      | <span data-ttu-id="bfc51-194">No</span><span class="sxs-lookup"><span data-stu-id="bfc51-194">No</span></span>           | <span data-ttu-id="bfc51-195">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bfc51-195">Optional.</span></span> <span data-ttu-id="bfc51-196">O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="bfc51-196">The friendly name for the item defined by the partner to help disambiguate.</span></span>              |
| <span data-ttu-id="bfc51-197">quantidade</span><span class="sxs-lookup"><span data-stu-id="bfc51-197">quantity</span></span>             | <span data-ttu-id="bfc51-198">int</span><span class="sxs-lookup"><span data-stu-id="bfc51-198">int</span></span>                         | <span data-ttu-id="bfc51-199">Sim</span><span class="sxs-lookup"><span data-stu-id="bfc51-199">Yes</span></span>          | <span data-ttu-id="bfc51-200">O número de licenças ou instâncias.</span><span class="sxs-lookup"><span data-stu-id="bfc51-200">The number of licenses or instances.</span></span>     |
| <span data-ttu-id="bfc51-201">currencyCode</span><span class="sxs-lookup"><span data-stu-id="bfc51-201">currencyCode</span></span>         | <span data-ttu-id="bfc51-202">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="bfc51-202">string</span></span>                      | <span data-ttu-id="bfc51-203">No</span><span class="sxs-lookup"><span data-stu-id="bfc51-203">No</span></span>           | <span data-ttu-id="bfc51-204">O código da moeda.</span><span class="sxs-lookup"><span data-stu-id="bfc51-204">The currency code.</span></span>                                                                                 |
| <span data-ttu-id="bfc51-205">billingCycle</span><span class="sxs-lookup"><span data-stu-id="bfc51-205">billingCycle</span></span>         | <span data-ttu-id="bfc51-206">Objeto</span><span class="sxs-lookup"><span data-stu-id="bfc51-206">Object</span></span>                      | <span data-ttu-id="bfc51-207">Sim</span><span class="sxs-lookup"><span data-stu-id="bfc51-207">Yes</span></span>          | <span data-ttu-id="bfc51-208">O tipo de ciclo de faturação definido para o período atual.</span><span class="sxs-lookup"><span data-stu-id="bfc51-208">The type of billing cycle set for the current period.</span></span>                                              |
| <span data-ttu-id="bfc51-209">participantes</span><span class="sxs-lookup"><span data-stu-id="bfc51-209">participants</span></span>         | <span data-ttu-id="bfc51-210">Lista de pares de cordas de objeto</span><span class="sxs-lookup"><span data-stu-id="bfc51-210">List of Object String pairs</span></span> | <span data-ttu-id="bfc51-211">Não</span><span class="sxs-lookup"><span data-stu-id="bfc51-211">No</span></span>           | <span data-ttu-id="bfc51-212">Uma coleção de participantes na compra.</span><span class="sxs-lookup"><span data-stu-id="bfc51-212">A collection of participants on the purchase.</span></span>                                                      |
| <span data-ttu-id="bfc51-213">provisionamentoContexto</span><span class="sxs-lookup"><span data-stu-id="bfc51-213">provisioningContext</span></span>  | <span data-ttu-id="bfc51-214">Cadeia de<do dicionário,> de cordas</span><span class="sxs-lookup"><span data-stu-id="bfc51-214">Dictionary<string, string></span></span>  | <span data-ttu-id="bfc51-215">Não</span><span class="sxs-lookup"><span data-stu-id="bfc51-215">No</span></span>           | <span data-ttu-id="bfc51-216">Um contexto utilizado para o provisionamento da oferta.</span><span class="sxs-lookup"><span data-stu-id="bfc51-216">A context used for provisioning of offer.</span></span>                                                          |
| <span data-ttu-id="bfc51-217">orderGroup</span><span class="sxs-lookup"><span data-stu-id="bfc51-217">orderGroup</span></span>           | <span data-ttu-id="bfc51-218">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="bfc51-218">string</span></span>                      | <span data-ttu-id="bfc51-219">No</span><span class="sxs-lookup"><span data-stu-id="bfc51-219">No</span></span>           | <span data-ttu-id="bfc51-220">Um grupo para indicar quais os itens que podem ser colocados juntos.</span><span class="sxs-lookup"><span data-stu-id="bfc51-220">A group to indicate which items can be placed together.</span></span>                                            |
| <span data-ttu-id="bfc51-221">erro</span><span class="sxs-lookup"><span data-stu-id="bfc51-221">error</span></span>                | <span data-ttu-id="bfc51-222">Objeto</span><span class="sxs-lookup"><span data-stu-id="bfc51-222">Object</span></span>                      | <span data-ttu-id="bfc51-223">Não</span><span class="sxs-lookup"><span data-stu-id="bfc51-223">No</span></span>           | <span data-ttu-id="bfc51-224">Aplicado após o carrinho é criado em caso de erro.</span><span class="sxs-lookup"><span data-stu-id="bfc51-224">Applied after cart is created in case of an error.</span></span>                                                 |

### <a name="request-example"></a><span data-ttu-id="bfc51-225">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="bfc51-225">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="bfc51-226">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="bfc51-226">REST response</span></span>

<span data-ttu-id="bfc51-227">Se for bem sucedido, este método devolve o recurso [cart](cart-resources.md) povoado no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="bfc51-227">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bfc51-228">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="bfc51-228">Response success and error codes</span></span>

<span data-ttu-id="bfc51-229">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="bfc51-229">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bfc51-230">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="bfc51-230">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bfc51-231">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="bfc51-231">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="bfc51-232">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="bfc51-232">Response example</span></span>

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
