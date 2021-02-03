---
title: Finalizar a compra de um carrinho
description: Saiba como verificar um pedido de um cliente num carrinho usando APIs do Partner Center. Pode fazê-lo para completar uma encomenda de clientes.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 094817a34cd29bc96788fcfb6a16610a8192d784
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770081"
---
# <a name="checkout-an-order-for-a-customer-in-a-cart"></a><span data-ttu-id="16e08-104">Check-out um pedido para um cliente em um carrinho</span><span class="sxs-lookup"><span data-stu-id="16e08-104">Checkout an order for a customer in a cart</span></span>

<span data-ttu-id="16e08-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="16e08-105">**Applies to:**</span></span>

- <span data-ttu-id="16e08-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="16e08-106">Partner Center</span></span>
- <span data-ttu-id="16e08-107">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="16e08-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="16e08-108">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="16e08-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="16e08-109">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="16e08-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="16e08-110">Como fazer o check-out de um pedido para um cliente em um carrinho.</span><span class="sxs-lookup"><span data-stu-id="16e08-110">How to checkout an order for a customer in a cart.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16e08-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="16e08-111">Prerequisites</span></span>

- <span data-ttu-id="16e08-112">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="16e08-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="16e08-113">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="16e08-113">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="16e08-114">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="16e08-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="16e08-115">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="16e08-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="16e08-116">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="16e08-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="16e08-117">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="16e08-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="16e08-118">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="16e08-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="16e08-119">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="16e08-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="16e08-120">Uma identificação do carrinho para um carrinho existente.</span><span class="sxs-lookup"><span data-stu-id="16e08-120">A Cart ID for an existing cart.</span></span>

## <a name="c"></a><span data-ttu-id="16e08-121">C\#</span><span class="sxs-lookup"><span data-stu-id="16e08-121">C\#</span></span>

<span data-ttu-id="16e08-122">Para fazer o check-out de um pedido de cliente, obtenha uma referência ao carrinho usando o carrinho e o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="16e08-122">To checkout an order for a customer, get a reference to the cart using the cart and customer identifier.</span></span> <span data-ttu-id="16e08-123">Por fim, ligue para as funções **Criar** ou **Criar** Para completar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="16e08-123">Finally, call the **Create** or **CreateAsync** functions to complete the order.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Checkout();
```

## <a name="java"></a><span data-ttu-id="16e08-124">Java</span><span class="sxs-lookup"><span data-stu-id="16e08-124">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](<../includes/java-sdk-support.md>)]

<span data-ttu-id="16e08-125">Para fazer o check-out de um pedido de cliente, obtenha uma referência ao carrinho usando o carrinho e o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="16e08-125">To checkout an order for a customer, get a reference to the cart using the cart and customer identifier.</span></span> <span data-ttu-id="16e08-126">Finalmente, chame a função **de criar** para completar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="16e08-126">Finally, call the **create** function to complete the order.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String cartId;

Cart cart = partnerOperations.getCustomers().byId(customerId).getCart().byId(cartId).checkout();
```

## <a name="powershell"></a><span data-ttu-id="16e08-127">PowerShell</span><span class="sxs-lookup"><span data-stu-id="16e08-127">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](<../includes/powershell-module-support.md>)]

<span data-ttu-id="16e08-128">Para fazer o check-out de um pedido para um cliente, execute o [**Submit-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Submit-PartnerCustomerCart.md) para completar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="16e08-128">To checkout an order for a customer, execute the [**Submit-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Submit-PartnerCustomerCart.md) to complete the order.</span></span>

```powershell
# $customerId
# $cartId

Submit-PartnerCustomerCart -CartId $cartId -CustomerId $customerId
```

## <a name="rest-request"></a><span data-ttu-id="16e08-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="16e08-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="16e08-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="16e08-130">Request syntax</span></span>

| <span data-ttu-id="16e08-131">Método</span><span class="sxs-lookup"><span data-stu-id="16e08-131">Method</span></span>   | <span data-ttu-id="16e08-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="16e08-132">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="16e08-133">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="16e08-133">**POST**</span></span> | <span data-ttu-id="16e08-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts/{cart-id}/checkout HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="16e08-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts/{cart-id}/checkout HTTP/1.1</span></span>     |

### <a name="uri-parameters"></a><span data-ttu-id="16e08-135">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="16e08-135">URI parameters</span></span>

<span data-ttu-id="16e08-136">Utilize os seguintes parâmetros de percurso para identificar o cliente e especificar o carrinho a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="16e08-136">Use the following path parameters to identify the customer and specify the cart to be checked out.</span></span>

| <span data-ttu-id="16e08-137">Nome</span><span class="sxs-lookup"><span data-stu-id="16e08-137">Name</span></span>            | <span data-ttu-id="16e08-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="16e08-138">Type</span></span>     | <span data-ttu-id="16e08-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="16e08-139">Required</span></span> | <span data-ttu-id="16e08-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="16e08-140">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="16e08-141">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="16e08-141">**customer-id**</span></span> | <span data-ttu-id="16e08-142">string</span><span class="sxs-lookup"><span data-stu-id="16e08-142">string</span></span>   | <span data-ttu-id="16e08-143">Sim</span><span class="sxs-lookup"><span data-stu-id="16e08-143">Yes</span></span>      | <span data-ttu-id="16e08-144">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="16e08-144">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="16e08-145">**cart-id**</span><span class="sxs-lookup"><span data-stu-id="16e08-145">**cart-id**</span></span>     | <span data-ttu-id="16e08-146">string</span><span class="sxs-lookup"><span data-stu-id="16e08-146">string</span></span>   | <span data-ttu-id="16e08-147">Sim</span><span class="sxs-lookup"><span data-stu-id="16e08-147">Yes</span></span>      | <span data-ttu-id="16e08-148">Um carro-id formatado GUID que identifica o carrinho.</span><span class="sxs-lookup"><span data-stu-id="16e08-148">A GUID formatted cart-id that identifies the cart.</span></span>                     |

### <a name="request-headers"></a><span data-ttu-id="16e08-149">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="16e08-149">Request headers</span></span>

<span data-ttu-id="16e08-150">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="16e08-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="16e08-151">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="16e08-151">Request body</span></span>

<span data-ttu-id="16e08-152">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="16e08-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="16e08-153">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="16e08-153">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="16e08-154">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="16e08-154">REST response</span></span>

<span data-ttu-id="16e08-155">Se for bem sucedido, o corpo de resposta contém o recurso [CartCheckoutResult](cart-resources.md#cartcheckoutresult) povoado.</span><span class="sxs-lookup"><span data-stu-id="16e08-155">If successful, the response body contains the populated [CartCheckoutResult](cart-resources.md#cartcheckoutresult) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="16e08-156">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="16e08-156">Response success and error codes</span></span>

<span data-ttu-id="16e08-157">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="16e08-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="16e08-158">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="16e08-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="16e08-159">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="16e08-159">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="16e08-160">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="16e08-160">Response example</span></span>

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
