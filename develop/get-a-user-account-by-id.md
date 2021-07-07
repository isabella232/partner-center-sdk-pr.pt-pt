---
title: Obter uma conta de utilizador por ID
description: Obtenha uma conta de utilizador específica para um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 3a7cac98a8081a8557dcadfb0724f5497be7d14c
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760271"
---
# <a name="get-a-user-account-by-id"></a><span data-ttu-id="09c95-103">Obter uma conta de utilizador por ID</span><span class="sxs-lookup"><span data-stu-id="09c95-103">Get a user account by ID</span></span>

<span data-ttu-id="09c95-104">Obtenha uma conta de utilizador específica para um cliente.</span><span class="sxs-lookup"><span data-stu-id="09c95-104">Get a specific user account for a customer.</span></span>

- <span data-ttu-id="09c95-105">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="09c95-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="09c95-106">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="09c95-106">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="09c95-107">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="09c95-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="09c95-108">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="09c95-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="09c95-109">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="09c95-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="09c95-110">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="09c95-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="09c95-111">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="09c95-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="09c95-112">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="09c95-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="09c95-113">C\#</span><span class="sxs-lookup"><span data-stu-id="09c95-113">C\#</span></span>

<span data-ttu-id="09c95-114">Para recuperar uma conta de utilizador para um cliente, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="09c95-114">To retrieve a user account for a customer, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="09c95-115">Em seguida, ligue para o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para recuperar o utilizador específico.</span><span class="sxs-lookup"><span data-stu-id="09c95-115">Next, call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to retrieve the specific user.</span></span> <span data-ttu-id="09c95-116">Por fim, ligue para o método [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) para recuperar a conta do utilizador.</span><span class="sxs-lookup"><span data-stu-id="09c95-116">Finally, call the [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) method to retrieve the user account.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedCustomerUserId;

// Get customer user detail.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Get();
```

<span data-ttu-id="09c95-117">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="09c95-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="09c95-118">**Project**: Partner Center SDK Samples **Class**: GetCustomerUserDetails.cs</span><span class="sxs-lookup"><span data-stu-id="09c95-118">**Project**: Partner Center SDK Samples **Class**: GetCustomerUserDetails.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="09c95-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="09c95-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="09c95-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="09c95-120">Request syntax</span></span>

| <span data-ttu-id="09c95-121">Método</span><span class="sxs-lookup"><span data-stu-id="09c95-121">Method</span></span>  | <span data-ttu-id="09c95-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="09c95-122">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="09c95-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="09c95-123">**GET**</span></span> | <span data-ttu-id="09c95-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="09c95-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="09c95-125">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="09c95-125">URI parameter</span></span>

<span data-ttu-id="09c95-126">Utilize os seguintes parâmetros URI para identificar o cliente e o utilizador corretos.</span><span class="sxs-lookup"><span data-stu-id="09c95-126">Use the following URI parameters to identify the correct customer and user.</span></span>

| <span data-ttu-id="09c95-127">Nome</span><span class="sxs-lookup"><span data-stu-id="09c95-127">Name</span></span>                   | <span data-ttu-id="09c95-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="09c95-128">Type</span></span>     | <span data-ttu-id="09c95-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="09c95-129">Required</span></span> | <span data-ttu-id="09c95-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="09c95-130">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="09c95-131">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="09c95-131">**customer-tenant-id**</span></span> | <span data-ttu-id="09c95-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="09c95-132">**guid**</span></span> | <span data-ttu-id="09c95-133">Y</span><span class="sxs-lookup"><span data-stu-id="09c95-133">Y</span></span>        | <span data-ttu-id="09c95-134">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="09c95-134">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="09c95-135">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="09c95-135">**user-id**</span></span>            | <span data-ttu-id="09c95-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="09c95-136">**guid**</span></span> | <span data-ttu-id="09c95-137">Y</span><span class="sxs-lookup"><span data-stu-id="09c95-137">Y</span></span>        | <span data-ttu-id="09c95-138">O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="09c95-138">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="09c95-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="09c95-139">Request headers</span></span>

<span data-ttu-id="09c95-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="09c95-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="09c95-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="09c95-141">Request body</span></span>

<span data-ttu-id="09c95-142">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="09c95-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="09c95-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="09c95-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a9ef48bb-8758-4590-a312-d4a47bfaded4 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c1f673cb-655c-45a7-8a6b-257a0a006f4b
MS-CorrelationId: 24a631eb-a110-49dc-8325-99d4b196774c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="09c95-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="09c95-144">REST response</span></span>

<span data-ttu-id="09c95-145">Se for bem sucedido, este método devolve a conta de utilizador para o cliente.</span><span class="sxs-lookup"><span data-stu-id="09c95-145">If successful, this method returns the user account for the customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="09c95-146">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="09c95-146">Response success and error codes</span></span>

<span data-ttu-id="09c95-147">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="09c95-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="09c95-148">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="09c95-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="09c95-149">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="09c95-149">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="09c95-150">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="09c95-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 432
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 24a631eb-a110-49dc-8325-99d4b196774c
MS-RequestId: c1f673cb-655c-45a7-8a6b-257a0a006f4b
MS-CV: uWM1EGU7+0aI2MvV.0
MS-ServerId: 020021921
Date: Wed, 21 Dec 2016 22:59:10 GMT

{
    "usageLocation": "US",
    "id": "a9ef48bb-8758-4590-a312-d4a47bfaded4",
    "userPrincipalName": "Daniel@dtdemocspcustomer005.onmicrosoft.com",
    "firstName": "Daniel",
    "lastName": "Tsai",
    "displayName": "Daniel Tsai",
    "userDomainType": "none",
    "state": "active",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a9ef48bb-8758-4590-a312-d4a47bfaded4",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "CustomerUser"
    }
}
```
