---
title: Finalizar a compra de um carrinho
description: Saiba como verificar um pedido de um cliente num carrinho usando APIs do Partner Center. Pode fazê-lo para completar uma encomenda de clientes.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9ee06797602b22a1f8257c94880a2d81e2280f2e
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974051"
---
# <a name="checkout-an-order-for-a-customer-in-a-cart"></a><span data-ttu-id="f93c3-104">Check-out um pedido para um cliente em um carrinho</span><span class="sxs-lookup"><span data-stu-id="f93c3-104">Checkout an order for a customer in a cart</span></span>

<span data-ttu-id="f93c3-105">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="f93c3-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="f93c3-106">Como fazer o check-out de um pedido para um cliente em um carrinho.</span><span class="sxs-lookup"><span data-stu-id="f93c3-106">How to checkout an order for a customer in a cart.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f93c3-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f93c3-107">Prerequisites</span></span>

- <span data-ttu-id="f93c3-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f93c3-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f93c3-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="f93c3-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="f93c3-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f93c3-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f93c3-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f93c3-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f93c3-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="f93c3-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f93c3-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="f93c3-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f93c3-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="f93c3-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f93c3-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f93c3-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f93c3-116">Uma identificação do carrinho para um carrinho existente.</span><span class="sxs-lookup"><span data-stu-id="f93c3-116">A Cart ID for an existing cart.</span></span>

## <a name="c"></a><span data-ttu-id="f93c3-117">C\#</span><span class="sxs-lookup"><span data-stu-id="f93c3-117">C\#</span></span>

<span data-ttu-id="f93c3-118">Para fazer o check-out de um pedido de cliente, obtenha uma referência ao carrinho usando o carrinho e o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="f93c3-118">To checkout an order for a customer, get a reference to the cart using the cart and customer identifier.</span></span> <span data-ttu-id="f93c3-119">Por fim, ligue para as funções **Criar** ou **Criar** Para completar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="f93c3-119">Finally, call the **Create** or **CreateAsync** functions to complete the order.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Checkout();
```

## <a name="java"></a><span data-ttu-id="f93c3-120">Java</span><span class="sxs-lookup"><span data-stu-id="f93c3-120">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](<../includes/java-sdk-support.md>)]

<span data-ttu-id="f93c3-121">Para fazer o check-out de um pedido de cliente, obtenha uma referência ao carrinho usando o carrinho e o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="f93c3-121">To checkout an order for a customer, get a reference to the cart using the cart and customer identifier.</span></span> <span data-ttu-id="f93c3-122">Finalmente, chame a função **de criar** para completar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="f93c3-122">Finally, call the **create** function to complete the order.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String cartId;

Cart cart = partnerOperations.getCustomers().byId(customerId).getCart().byId(cartId).checkout();
```

## <a name="powershell"></a><span data-ttu-id="f93c3-123">PowerShell</span><span class="sxs-lookup"><span data-stu-id="f93c3-123">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](<../includes/powershell-module-support.md>)]

<span data-ttu-id="f93c3-124">Para fazer o check-out de um pedido para um cliente, execute o [**Submit-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Submit-PartnerCustomerCart.md) para completar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="f93c3-124">To checkout an order for a customer, execute the [**Submit-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Submit-PartnerCustomerCart.md) to complete the order.</span></span>

```powershell
# $customerId
# $cartId

Submit-PartnerCustomerCart -CartId $cartId -CustomerId $customerId
```

## <a name="rest-request"></a><span data-ttu-id="f93c3-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f93c3-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f93c3-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f93c3-126">Request syntax</span></span>

| <span data-ttu-id="f93c3-127">Método</span><span class="sxs-lookup"><span data-stu-id="f93c3-127">Method</span></span>   | <span data-ttu-id="f93c3-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f93c3-128">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f93c3-129">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="f93c3-129">**POST**</span></span> | <span data-ttu-id="f93c3-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts/{cart-id}/checkout HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f93c3-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts/{cart-id}/checkout HTTP/1.1</span></span>     |

### <a name="uri-parameters"></a><span data-ttu-id="f93c3-131">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="f93c3-131">URI parameters</span></span>

<span data-ttu-id="f93c3-132">Utilize os seguintes parâmetros de percurso para identificar o cliente e especificar o carrinho a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="f93c3-132">Use the following path parameters to identify the customer and specify the cart to be checked out.</span></span>

| <span data-ttu-id="f93c3-133">Nome</span><span class="sxs-lookup"><span data-stu-id="f93c3-133">Name</span></span>            | <span data-ttu-id="f93c3-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="f93c3-134">Type</span></span>     | <span data-ttu-id="f93c3-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="f93c3-135">Required</span></span> | <span data-ttu-id="f93c3-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="f93c3-136">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="f93c3-137">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="f93c3-137">**customer-id**</span></span> | <span data-ttu-id="f93c3-138">string</span><span class="sxs-lookup"><span data-stu-id="f93c3-138">string</span></span>   | <span data-ttu-id="f93c3-139">Yes</span><span class="sxs-lookup"><span data-stu-id="f93c3-139">Yes</span></span>      | <span data-ttu-id="f93c3-140">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="f93c3-140">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="f93c3-141">**cart-id**</span><span class="sxs-lookup"><span data-stu-id="f93c3-141">**cart-id**</span></span>     | <span data-ttu-id="f93c3-142">string</span><span class="sxs-lookup"><span data-stu-id="f93c3-142">string</span></span>   | <span data-ttu-id="f93c3-143">Yes</span><span class="sxs-lookup"><span data-stu-id="f93c3-143">Yes</span></span>      | <span data-ttu-id="f93c3-144">Um carro-id formatado GUID que identifica o carrinho.</span><span class="sxs-lookup"><span data-stu-id="f93c3-144">A GUID formatted cart-id that identifies the cart.</span></span>                     |

### <a name="request-headers"></a><span data-ttu-id="f93c3-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="f93c3-145">Request headers</span></span>

<span data-ttu-id="f93c3-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f93c3-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f93c3-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f93c3-147">Request body</span></span>

<span data-ttu-id="f93c3-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f93c3-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f93c3-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f93c3-149">Request example</span></span>

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/b4c8fdea-cbe4-4d17-9576-13fcacbf9605/checkout HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 0
Expect: 100-continue

No-Content-Body
```

## <a name="rest-response"></a><span data-ttu-id="f93c3-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f93c3-150">REST response</span></span>

<span data-ttu-id="f93c3-151">Se for bem sucedido, o corpo de resposta contém o recurso [CartCheckoutResult](cart-resources.md#cartcheckoutresult) povoado.</span><span class="sxs-lookup"><span data-stu-id="f93c3-151">If successful, the response body contains the populated [CartCheckoutResult](cart-resources.md#cartcheckoutresult) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f93c3-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f93c3-152">Response success and error codes</span></span>

<span data-ttu-id="f93c3-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f93c3-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f93c3-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f93c3-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f93c3-155">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f93c3-155">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f93c3-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f93c3-156">Response example</span></span>

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
?{
  "orders": [
    {
      "id": "3c6f2530-1e31-4088-8230-dd1c31a18bce",
      "alternateId": "3c6f2530-1e31-4088-8230-dd1c31a18bce",
      "referenceCustomerId": "28045616-f6b9-462f-9701-0d89b5e65c44",
      "billingCycle": "monthly",
      "currencyCode": "USD",
      "lineItems": [
        {
          "lineItemNumber": 0,
          "offerId": "MS-AZR-0145P",
          "subscriptionId": "EF2E1307-86E6-40E3-A794-872403FBD31C",
          "termDuration": "P1Y",
          "transactionType": "New",
          "friendlyName": "Microsoft Azure",
          "quantity": 1,
          "links": {...}
        }
      ],
      "creationDate": "2019-01-16T00:48:44.76+00:00",
      "status": "completed",
      "transactionType": "UserPurchase",
      "links": {...},
      ...
    },
    {
      "id": "311qiN8iFwkv-XARWMvXRYAwYKMACVqv1",
      "alternateId": "0a3624c6e47d",
      "referenceCustomerId": "28045616-f6b9-462f-9701-0d89b5e65c44",
      "billingCycle": "one_time",
      "currencyCode": "USD",
      "currencySymbol": "$",
      "lineItems": [
        {
          "lineItemNumber": 0,
          "offerId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
          "termDuration": "P1Y",
          "transactionType": "New",
          "friendlyName": "Reserved VM Instance, Standard_NV12, US East 2, 1 Year",
          "quantity": 1,
          "links": {...}
        },
        {
          "lineItemNumber": 1,
          "offerId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
          "termDuration": "P3Y",
          "transactionType": "New",
          "friendlyName": "Reserved VM Instance, Standard_NV12, US East 2, 3 Years",
          "quantity": 1,
          "links": {...}
        },
        {
          "lineItemNumber": 2,
          "offerId": "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
          "transactionType": "New",
          "friendlyName": "BizTalk Server 2016 Branch",
          "quantity": 1,
          "links": {...}
        }
      ],
      "creationDate": "2019-01-16T00:48:51.6578126Z",
      "status": "pending",
      "transactionType": "UserPurchase",
      "links": {...},
      ...
    },
    {
      "id": "HVu_cO8Ea7fNRQP4ia1QTpZap-kg_7P71",
      "alternateId": "55a4e6854d54",
      "referenceCustomerId": "28045616-f6b9-462f-9701-0d89b5e65c44",
      "billingCycle": "monthly",
      "currencyCode": "USD",
      "currencySymbol": "$",
      "lineItems": [
        {
          "lineItemNumber": 0,
          "offerId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
          "termDuration": "P1M",
          "transactionType": "New",
          "friendlyName": "Barracuda WaaS - Medium Plan",
          "quantity": 1,
          "links": {...}
        }
      ],
      "creationDate": "2019-01-16T00:48:44.4514129Z",
      "status": "pending",
      "transactionType": "UserPurchase",
      "links": {...},
      ...
    }
  ],
  ...
}
```
