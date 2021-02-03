---
title: Obter encomenda por ID
description: Obtém um recurso de Encomenda que corresponda ao cliente e encomende iD de encomenda.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 0a39d7142e5bf97f9fb345416964d4ed6bb935ad
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769871"
---
# <a name="get-an-order-by-id"></a><span data-ttu-id="0daab-103">Obter encomenda por ID</span><span class="sxs-lookup"><span data-stu-id="0daab-103">Get an order by ID</span></span>

<span data-ttu-id="0daab-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="0daab-104">**Applies to:**</span></span>

- <span data-ttu-id="0daab-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="0daab-105">Partner Center</span></span>
- <span data-ttu-id="0daab-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="0daab-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="0daab-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="0daab-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="0daab-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0daab-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0daab-109">Obtém um recurso [de Encomenda](order-resources.md) que corresponda ao cliente e encomende iD de encomenda.</span><span class="sxs-lookup"><span data-stu-id="0daab-109">Gets an [Order](order-resources.md) resource that matches the customer and order ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0daab-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0daab-110">Prerequisites</span></span>

- <span data-ttu-id="0daab-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0daab-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0daab-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="0daab-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="0daab-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0daab-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="0daab-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="0daab-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="0daab-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="0daab-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="0daab-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="0daab-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="0daab-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="0daab-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="0daab-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0daab-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="0daab-119">Uma identificação de encomenda.</span><span class="sxs-lookup"><span data-stu-id="0daab-119">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="0daab-120">C\#</span><span class="sxs-lookup"><span data-stu-id="0daab-120">C\#</span></span>

<span data-ttu-id="0daab-121">Para obter uma encomenda de um cliente por ID:</span><span class="sxs-lookup"><span data-stu-id="0daab-121">To get a customer's order by ID:</span></span>

1. <span data-ttu-id="0daab-122">Utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="0daab-122">Use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span>

2. <span data-ttu-id="0daab-123">Ligue para a propriedade [**Encomendas,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) seguida do método [**ByID()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) mais uma vez.</span><span class="sxs-lookup"><span data-stu-id="0daab-123">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property, followed by the [**ByID()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) method once more.</span></span>
3. <span data-ttu-id="0daab-124">Ligue [**para Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.get) ou [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.getasync).</span><span class="sxs-lookup"><span data-stu-id="0daab-124">Call [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.getasync).</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedOrderId;

var order = partnerOperations.Customers.ById(selectedCustomerId).Orders.ById(selectedOrderId).Get();
```

<span data-ttu-id="0daab-125">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="0daab-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="0daab-126">**Projeto**: PartnerSDK.FeatureSample **Class**: GetOrder.cs</span><span class="sxs-lookup"><span data-stu-id="0daab-126">**Project**: PartnerSDK.FeatureSample **Class**: GetOrder.cs</span></span>

## <a name="java"></a><span data-ttu-id="0daab-127">Java</span><span class="sxs-lookup"><span data-stu-id="0daab-127">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="0daab-128">Para obter uma encomenda de um cliente por ID:</span><span class="sxs-lookup"><span data-stu-id="0daab-128">To get a customer's order by ID:</span></span>

1. <span data-ttu-id="0daab-129">Utilize a função **IAggregatePartner.getCustomers** e ligue para a função **byId().**</span><span class="sxs-lookup"><span data-stu-id="0daab-129">Use your **IAggregatePartner.getCustomers** function and call the **byId()** function.</span></span>

2. <span data-ttu-id="0daab-130">Ligue para a função **getOrders,** seguida da função **byID()** mais uma vez.</span><span class="sxs-lookup"><span data-stu-id="0daab-130">Call the **getOrders** function, followed by the **byID()** function once more.</span></span>
3. <span data-ttu-id="0daab-131">Ligue para a função **get().**</span><span class="sxs-lookup"><span data-stu-id="0daab-131">Call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;
// String selectedOrderId;

Order order = partnerOperations.getCustomers().byId(selectedCustomerId).getOrders().byId(selectedOrderId).get();
```

## <a name="powershell"></a><span data-ttu-id="0daab-132">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0daab-132">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="0daab-133">Para obter uma encomenda de um cliente por ID, execute o comando [**Get-PartnerCustomerOrder**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerOrder.md) e especifique os parâmetros **CustomerId** e **OrderId.**</span><span class="sxs-lookup"><span data-stu-id="0daab-133">To get a customer's order by ID, execute the [**Get-PartnerCustomerOrder**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerOrder.md) command, and specify the **CustomerId** and **OrderId** parameters.</span></span>

```powershell
# $selectedCustomerId
# $selectedOrderId

Get-PartnerCustomerOrder -CustomerId $selectedCustomerId -OrderId $selectedOrderId
```

## <a name="rest-request"></a><span data-ttu-id="0daab-134">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="0daab-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0daab-135">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="0daab-135">Request syntax</span></span>

| <span data-ttu-id="0daab-136">Método</span><span class="sxs-lookup"><span data-stu-id="0daab-136">Method</span></span>  | <span data-ttu-id="0daab-137">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="0daab-137">Request URI</span></span>                                                                                                  |
|---------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0daab-138">**Obter**</span><span class="sxs-lookup"><span data-stu-id="0daab-138">**GET**</span></span> | <span data-ttu-id="0daab-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{id-for-order} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0daab-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{id-for-order} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="0daab-140">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="0daab-140">URI parameters</span></span>

<span data-ttu-id="0daab-141">Esta tabela lista os parâmetros de consulta necessários para obter uma encomenda por ID.</span><span class="sxs-lookup"><span data-stu-id="0daab-141">This table lists the required query parameters to get an order by ID.</span></span>

| <span data-ttu-id="0daab-142">Nome</span><span class="sxs-lookup"><span data-stu-id="0daab-142">Name</span></span>                   | <span data-ttu-id="0daab-143">Tipo</span><span class="sxs-lookup"><span data-stu-id="0daab-143">Type</span></span>     | <span data-ttu-id="0daab-144">Necessário</span><span class="sxs-lookup"><span data-stu-id="0daab-144">Required</span></span> | <span data-ttu-id="0daab-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="0daab-145">Description</span></span>                                            |
|------------------------|----------|----------|--------------------------------------------------------|
| <span data-ttu-id="0daab-146">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="0daab-146">customer-tenant-id</span></span>     | <span data-ttu-id="0daab-147">string</span><span class="sxs-lookup"><span data-stu-id="0daab-147">string</span></span>   | <span data-ttu-id="0daab-148">Sim</span><span class="sxs-lookup"><span data-stu-id="0daab-148">Yes</span></span>      | <span data-ttu-id="0daab-149">Uma cadeia formatada GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="0daab-149">A GUID formatted string corresponding to the customer.</span></span> |
| <span data-ttu-id="0daab-150">id-for-order</span><span class="sxs-lookup"><span data-stu-id="0daab-150">id-for-order</span></span>           | <span data-ttu-id="0daab-151">string</span><span class="sxs-lookup"><span data-stu-id="0daab-151">string</span></span>   | <span data-ttu-id="0daab-152">Sim</span><span class="sxs-lookup"><span data-stu-id="0daab-152">Yes</span></span>      | <span data-ttu-id="0daab-153">Uma corda correspondente à identificação da ordem.</span><span class="sxs-lookup"><span data-stu-id="0daab-153">A string corresponding to the order ID.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="0daab-154">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="0daab-154">Request headers</span></span>

<span data-ttu-id="0daab-155">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="0daab-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0daab-156">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="0daab-156">Request body</span></span>

<span data-ttu-id="0daab-157">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0daab-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0daab-158">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="0daab-158">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/orders/<id-for-order> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="0daab-159">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="0daab-159">REST response</span></span>

<span data-ttu-id="0daab-160">Se for bem sucedido, este método devolve um recurso [da Ordem](order-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="0daab-160">If successful, this method returns an [Order](order-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0daab-161">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="0daab-161">Response success and error codes</span></span>

<span data-ttu-id="0daab-162">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="0daab-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0daab-163">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="0daab-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0daab-164">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="0daab-164">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0daab-165">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="0daab-165">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 823
Content-Type: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Date: Thu, 15 Mar 2018 22:05:30 GMT

{
    "id": "YxH1q4KScfvfkJQjgRI8QY1DznnUWZTH1",
    "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
    "billingCycle": "one_time",
    "currencyCode": "USD",
    "currencySymbol" : "$",
    "lineItems": [
    {
        "lineItemNumber": 0,
        "offerId": "DZH318Z0BQ4Z:002L:DZH318Z0CMNP",
        "friendlyName": "Reserved_VM_Instance_Standard_NC12_AU_East_1_Year",
        "quantity": 1,
        "links": {
            "sku": {
                "uri": "/products/DZH318Z0BQ4Z/skus/002L?country=US",
                "method": "GET",
                "headers": []
            }
        }
    }
    ],
    "creationDate": "2018-03-13T22:49:54.3396949Z",
    "status": "completed",
    "links": {
        "provisioningStatus": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/YxH1q4KScfvfkJQjgRI8QY1DznnUWZTH1/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/YxH1q4KScfvfkJQjgRI8QY1DznnUWZTH1",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Order"
    }
}
```
