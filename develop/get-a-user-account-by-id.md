---
title: Obter uma conta de utilizador por ID
description: Obtenha uma conta de utilizador específica para um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: a2f42001365324a65376318cb1f2d57dc123df0c
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769271"
---
# <a name="get-a-user-account-by-id"></a><span data-ttu-id="d73f4-103">Obter uma conta de utilizador por ID</span><span class="sxs-lookup"><span data-stu-id="d73f4-103">Get a user account by ID</span></span>

<span data-ttu-id="d73f4-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="d73f4-104">**Applies To**</span></span>

- <span data-ttu-id="d73f4-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="d73f4-105">Partner Center</span></span>

<span data-ttu-id="d73f4-106">Obtenha uma conta de utilizador específica para um cliente.</span><span class="sxs-lookup"><span data-stu-id="d73f4-106">Get a specific user account for a customer.</span></span>

- <span data-ttu-id="d73f4-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d73f4-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d73f4-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="d73f4-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="d73f4-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d73f4-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d73f4-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d73f4-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d73f4-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d73f4-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d73f4-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d73f4-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d73f4-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d73f4-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d73f4-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d73f4-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="d73f4-115">C\#</span><span class="sxs-lookup"><span data-stu-id="d73f4-115">C\#</span></span>

<span data-ttu-id="d73f4-116">Para recuperar uma conta de utilizador para um cliente, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="d73f4-116">To retrieve a user account for a customer, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="d73f4-117">Em seguida, ligue para o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para recuperar o utilizador específico.</span><span class="sxs-lookup"><span data-stu-id="d73f4-117">Next, call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to retrieve the specific user.</span></span> <span data-ttu-id="d73f4-118">Por fim, ligue para o método [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) para recuperar a conta do utilizador.</span><span class="sxs-lookup"><span data-stu-id="d73f4-118">Finally, call the [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) method to retrieve the user account.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedCustomerUserId;

// Get customer user detail.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Get();
```

<span data-ttu-id="d73f4-119">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d73f4-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d73f4-120">**Projeto**: Partner Center SDK Samples **Class**: GetCustomerUserDetails.cs</span><span class="sxs-lookup"><span data-stu-id="d73f4-120">**Project**: Partner Center SDK Samples **Class**: GetCustomerUserDetails.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="d73f4-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d73f4-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d73f4-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d73f4-122">Request syntax</span></span>

| <span data-ttu-id="d73f4-123">Método</span><span class="sxs-lookup"><span data-stu-id="d73f4-123">Method</span></span>  | <span data-ttu-id="d73f4-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d73f4-124">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d73f4-125">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d73f4-125">**GET**</span></span> | <span data-ttu-id="d73f4-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d73f4-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="d73f4-127">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="d73f4-127">URI parameter</span></span>

<span data-ttu-id="d73f4-128">Utilize os seguintes parâmetros URI para identificar o cliente e o utilizador corretos.</span><span class="sxs-lookup"><span data-stu-id="d73f4-128">Use the following URI parameters to identify the correct customer and user.</span></span>

| <span data-ttu-id="d73f4-129">Nome</span><span class="sxs-lookup"><span data-stu-id="d73f4-129">Name</span></span>                   | <span data-ttu-id="d73f4-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="d73f4-130">Type</span></span>     | <span data-ttu-id="d73f4-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="d73f4-131">Required</span></span> | <span data-ttu-id="d73f4-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="d73f4-132">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d73f4-133">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="d73f4-133">**customer-tenant-id**</span></span> | <span data-ttu-id="d73f4-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="d73f4-134">**guid**</span></span> | <span data-ttu-id="d73f4-135">Y</span><span class="sxs-lookup"><span data-stu-id="d73f4-135">Y</span></span>        | <span data-ttu-id="d73f4-136">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="d73f4-136">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="d73f4-137">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="d73f4-137">**user-id**</span></span>            | <span data-ttu-id="d73f4-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="d73f4-138">**guid**</span></span> | <span data-ttu-id="d73f4-139">Y</span><span class="sxs-lookup"><span data-stu-id="d73f4-139">Y</span></span>        | <span data-ttu-id="d73f4-140">O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="d73f4-140">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="d73f4-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d73f4-141">Request headers</span></span>

<span data-ttu-id="d73f4-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d73f4-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d73f4-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d73f4-143">Request body</span></span>

<span data-ttu-id="d73f4-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d73f4-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d73f4-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d73f4-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a9ef48bb-8758-4590-a312-d4a47bfaded4 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c1f673cb-655c-45a7-8a6b-257a0a006f4b
MS-CorrelationId: 24a631eb-a110-49dc-8325-99d4b196774c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="d73f4-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d73f4-146">REST response</span></span>

<span data-ttu-id="d73f4-147">Se for bem sucedido, este método devolve a conta de utilizador para o cliente.</span><span class="sxs-lookup"><span data-stu-id="d73f4-147">If successful, this method returns the user account for the customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d73f4-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d73f4-148">Response success and error codes</span></span>

<span data-ttu-id="d73f4-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d73f4-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d73f4-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d73f4-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d73f4-151">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d73f4-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d73f4-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d73f4-152">Response example</span></span>

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
