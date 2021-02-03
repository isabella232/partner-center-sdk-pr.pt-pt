---
title: Obter uma lista de contas de utilizador para um cliente
description: Como obter uma lista de todas as contas de utilizador que pertencem a um dos seus clientes.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 6f2b1bcf9926e02232b6e2cc68b71e992b015324
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769332"
---
# <a name="get-a-list-of-all-user-accounts-for-a-customer"></a><span data-ttu-id="5028c-103">Obter uma lista de contas de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="5028c-103">Get a list of all user accounts for a customer</span></span>

<span data-ttu-id="5028c-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="5028c-104">**Applies to:**</span></span>

- <span data-ttu-id="5028c-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="5028c-105">Partner Center</span></span>

<span data-ttu-id="5028c-106">Este artigo descreve como obter uma lista de todas as contas de utilizador que pertencem a um dos seus clientes.</span><span class="sxs-lookup"><span data-stu-id="5028c-106">This article describes how to get a list of all user accounts that belong to one of your customers.</span></span>

<span data-ttu-id="5028c-107">Para procurar uma única conta de utilizador por ID, consulte [obter uma conta de utilizador por ID](get-a-user-account-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="5028c-107">To look up a single user account by ID, see [Get a user account by ID](get-a-user-account-by-id.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5028c-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5028c-108">Prerequisites</span></span>

- <span data-ttu-id="5028c-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5028c-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5028c-110">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="5028c-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="5028c-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5028c-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5028c-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5028c-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5028c-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="5028c-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5028c-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="5028c-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5028c-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="5028c-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5028c-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5028c-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="5028c-117">C\#</span><span class="sxs-lookup"><span data-stu-id="5028c-117">C\#</span></span>

<span data-ttu-id="5028c-118">Para recuperar a recolha de todas as contas do utilizador para um cliente especificado:</span><span class="sxs-lookup"><span data-stu-id="5028c-118">To retrieve the collection of all user accounts for a specified customer:</span></span>

1. <span data-ttu-id="5028c-119">Ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente especificado para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5028c-119">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer ID to identify the customer.</span></span>

2. <span data-ttu-id="5028c-120">Ligue para o método [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) para recuperar a coleção.</span><span class="sxs-lookup"><span data-stu-id="5028c-120">Call the [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) method to retrieve the collection.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

// Get customer users collection.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.Get();
```

<span data-ttu-id="5028c-121">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5028c-121">For an example, see the following:</span></span>

- <span data-ttu-id="5028c-122">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="5028c-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="5028c-123">Projeto: **Partner Center SDK Samples**</span><span class="sxs-lookup"><span data-stu-id="5028c-123">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="5028c-124">Classe: **GetCustomerUserCollection.cs**</span><span class="sxs-lookup"><span data-stu-id="5028c-124">Class: **GetCustomerUserCollection.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="5028c-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5028c-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5028c-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5028c-126">Request syntax</span></span>

| <span data-ttu-id="5028c-127">Método</span><span class="sxs-lookup"><span data-stu-id="5028c-127">Method</span></span>  | <span data-ttu-id="5028c-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5028c-128">Request URI</span></span>                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="5028c-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="5028c-129">**GET**</span></span> | <span data-ttu-id="5028c-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/utilizadores HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5028c-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="5028c-131">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="5028c-131">URI parameter</span></span>

<span data-ttu-id="5028c-132">Utilize o seguinte parâmetro URI para identificar o cliente correto.</span><span class="sxs-lookup"><span data-stu-id="5028c-132">Use the following URI parameter to identify the correct customer.</span></span>

| <span data-ttu-id="5028c-133">Nome</span><span class="sxs-lookup"><span data-stu-id="5028c-133">Name</span></span>                   | <span data-ttu-id="5028c-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="5028c-134">Type</span></span>     | <span data-ttu-id="5028c-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="5028c-135">Required</span></span> | <span data-ttu-id="5028c-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="5028c-136">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5028c-137">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="5028c-137">**customer-tenant-id**</span></span> | <span data-ttu-id="5028c-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="5028c-138">**guid**</span></span> | <span data-ttu-id="5028c-139">Y</span><span class="sxs-lookup"><span data-stu-id="5028c-139">Y</span></span>        | <span data-ttu-id="5028c-140">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="5028c-140">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5028c-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="5028c-141">Request headers</span></span>

<span data-ttu-id="5028c-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5028c-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5028c-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5028c-143">Request body</span></span>

<span data-ttu-id="5028c-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5028c-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5028c-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5028c-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 5d845377-5b7d-4cd4-98f6-19e5ae3faa81
MS-CorrelationId: 5a3d64d4-4490-4932-bf5e-0dc9a58f27ca
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="5028c-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5028c-146">REST response</span></span>

<span data-ttu-id="5028c-147">Se for bem sucedido, este método devolve uma coleção de contas de utilizador para um cliente.</span><span class="sxs-lookup"><span data-stu-id="5028c-147">If successful, this method returns a collection of user accounts for a customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5028c-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5028c-148">Response success and error codes</span></span>

<span data-ttu-id="5028c-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5028c-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5028c-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5028c-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5028c-151">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="5028c-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5028c-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5028c-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1030
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5a3d64d4-4490-4932-bf5e-0dc9a58f27ca
MS-RequestId: 5d845377-5b7d-4cd4-98f6-19e5ae3faa81
MS-CV: 6zmKqrSFB0+t7m3y.0
MS-ServerId: 101112616
Date: Wed, 21 Dec 2016 21:13:24 GMT

 {
    "totalCount": 2,
    "items": [{
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
        }, {
            "id": "6e668259-1f09-479d-bcb8-d9b03e826b8d",
            "userPrincipalName": "admin@dtdemocspcustomer005.onmicrosoft.com",
            "firstName": "Daniel",
            "lastName": "Tsai",
            "displayName": "DT Demo CSP Customer 005",
            "userDomainType": "none",
            "state": "active",
            "links": {
                "self": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/6e668259-1f09-479d-bcb8-d9b03e826b8d",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "CustomerUser"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
