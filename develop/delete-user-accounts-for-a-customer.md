---
title: Eliminar uma conta de utilizador para um cliente
description: Como eliminar uma conta de utilizador existente para um cliente.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c45646da43b8926f911942374de5da07f318c526
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973065"
---
# <a name="delete-a-user-account-for-a-customer"></a><span data-ttu-id="87dde-103">Eliminar uma conta de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="87dde-103">Delete a user account for a customer</span></span>

<span data-ttu-id="87dde-104">Este artigo explica como eliminar uma conta de utilizador existente para um cliente.</span><span class="sxs-lookup"><span data-stu-id="87dde-104">This article explains how to delete an existing user account for a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="87dde-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="87dde-105">Prerequisites</span></span>

- <span data-ttu-id="87dde-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="87dde-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="87dde-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="87dde-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="87dde-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="87dde-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="87dde-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="87dde-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="87dde-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="87dde-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="87dde-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="87dde-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="87dde-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="87dde-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="87dde-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="87dde-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="87dde-114">Uma identificação de utilizador.</span><span class="sxs-lookup"><span data-stu-id="87dde-114">A user ID.</span></span> <span data-ttu-id="87dde-115">Se não tiver o ID do utilizador, consulte [obter uma lista de todas as contas do utilizador para um cliente.](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="87dde-115">If you do not have the user ID, see [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md).</span></span>

## <a name="deleting-a-user-account"></a><span data-ttu-id="87dde-116">Apagar uma conta de utilizador</span><span class="sxs-lookup"><span data-stu-id="87dde-116">Deleting a user account</span></span>

<span data-ttu-id="87dde-117">Quando elimina uma conta de utilizador, o estado do utilizador está definido para **inativo** durante 30 dias.</span><span class="sxs-lookup"><span data-stu-id="87dde-117">When you delete a user account, the user state is set to **inactive** for 30 days.</span></span> <span data-ttu-id="87dde-118">Após 330 dias, a conta de utilizador e os seus dados associados são purgados e tornados irrecuperáveis.</span><span class="sxs-lookup"><span data-stu-id="87dde-118">After thirty 30 days, the user account and its associated data are purged and made unrecoverable.</span></span>

<span data-ttu-id="87dde-119">Pode [restaurar uma conta de utilizador eliminada para um cliente](restore-a-user-for-a-customer.md) se a conta inativa estiver dentro da janela de 30 dias.</span><span class="sxs-lookup"><span data-stu-id="87dde-119">You can [restore a deleted user account for a customer](restore-a-user-for-a-customer.md) if the inactive account is within the 30-day window.</span></span> <span data-ttu-id="87dde-120">No entanto, quando restaura uma conta que foi eliminada e marcada como inativa, a conta deixou de ser devolvida como membro da coleção de utilizadores (por exemplo, quando [obtém uma lista de todas as contas de utilizador de um cliente).](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="87dde-120">However, when you restore an account that was deleted and marked as inactive, the account is no longer returned as a member of the user collection (for example, when you [get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span>

## <a name="c"></a><span data-ttu-id="87dde-121">C\#</span><span class="sxs-lookup"><span data-stu-id="87dde-121">C\#</span></span>

<span data-ttu-id="87dde-122">Para eliminar uma conta de utilizador do cliente existente:</span><span class="sxs-lookup"><span data-stu-id="87dde-122">To delete an existing customer user account:</span></span>

1. <span data-ttu-id="87dde-123">Utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="87dde-123">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="87dde-124">Ligue para o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para identificar o utilizador.</span><span class="sxs-lookup"><span data-stu-id="87dde-124">Call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the user.</span></span>

3. <span data-ttu-id="87dde-125">Ligue para o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) para eliminar o utilizador e definir o estado do utilizador para inativo.</span><span class="sxs-lookup"><span data-stu-id="87dde-125">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) method to delete the user and set the user state to inactive.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string customerUserIdToDelete;

partnerOperations.Customers.ById(selectedCustomerId).Users.ById(customerUserIdToDelete).Delete();
```

<span data-ttu-id="87dde-126">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="87dde-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="87dde-127">**Project**: Partner Center SDK Samples **Class**: DeleteCustomerUser.cs</span><span class="sxs-lookup"><span data-stu-id="87dde-127">**Project**: Partner Center SDK Samples **Class**: DeleteCustomerUser.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="87dde-128">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="87dde-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="87dde-129">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="87dde-129">Request syntax</span></span>

| <span data-ttu-id="87dde-130">Método</span><span class="sxs-lookup"><span data-stu-id="87dde-130">Method</span></span>     | <span data-ttu-id="87dde-131">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="87dde-131">Request URI</span></span>                                                                                            |
|------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="87dde-132">DELETE</span><span class="sxs-lookup"><span data-stu-id="87dde-132">DELETE</span></span>     | <span data-ttu-id="87dde-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="87dde-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="87dde-134">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="87dde-134">URI parameters</span></span>

<span data-ttu-id="87dde-135">Utilize os seguintes parâmetros de consulta para identificar o cliente e o utilizador.</span><span class="sxs-lookup"><span data-stu-id="87dde-135">Use the following query parameters to identify the customer and user.</span></span>

| <span data-ttu-id="87dde-136">Nome</span><span class="sxs-lookup"><span data-stu-id="87dde-136">Name</span></span>                   | <span data-ttu-id="87dde-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="87dde-137">Type</span></span>     | <span data-ttu-id="87dde-138">Necessário</span><span class="sxs-lookup"><span data-stu-id="87dde-138">Required</span></span> | <span data-ttu-id="87dde-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="87dde-139">Description</span></span>                                                                                                               |
|------------------------|----------|----------|---------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="87dde-140">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="87dde-140">customer-tenant-id</span></span>     | <span data-ttu-id="87dde-141">GUID</span><span class="sxs-lookup"><span data-stu-id="87dde-141">GUID</span></span>     | <span data-ttu-id="87dde-142">Y</span><span class="sxs-lookup"><span data-stu-id="87dde-142">Y</span></span>        | <span data-ttu-id="87dde-143">O valor é um **design de cliente-inquilino** formatado pelo GUID que permite ao revendedor filtrar os resultados de um determinado cliente.</span><span class="sxs-lookup"><span data-stu-id="87dde-143">The value is a GUID-formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer.</span></span> |
| <span data-ttu-id="87dde-144">user-id</span><span class="sxs-lookup"><span data-stu-id="87dde-144">user-id</span></span>                | <span data-ttu-id="87dde-145">GUID</span><span class="sxs-lookup"><span data-stu-id="87dde-145">GUID</span></span>     | <span data-ttu-id="87dde-146">Y</span><span class="sxs-lookup"><span data-stu-id="87dde-146">Y</span></span>        | <span data-ttu-id="87dde-147">O valor é um **id** de utilizador com formato GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="87dde-147">The value is a GUID-formatted **user-id** that belongs to a single user account.</span></span>                                          |

### <a name="request-headers"></a><span data-ttu-id="87dde-148">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="87dde-148">Request headers</span></span>

<span data-ttu-id="87dde-149">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="87dde-149">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="87dde-150">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="87dde-150">Request body</span></span>

<span data-ttu-id="87dde-151">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="87dde-151">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="87dde-152">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="87dde-152">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="87dde-153">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="87dde-153">REST response</span></span>

<span data-ttu-id="87dde-154">Se for bem sucedido, este método devolve um código de estado **204 No Content.**</span><span class="sxs-lookup"><span data-stu-id="87dde-154">If successful, this method returns a **204 No Content** status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="87dde-155">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="87dde-155">Response success and error codes</span></span>

<span data-ttu-id="87dde-156">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="87dde-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="87dde-157">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="87dde-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="87dde-158">Para obter a lista completa, consulte [os Códigos de Erro DO Centro de Parceiros REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="87dde-158">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="87dde-159">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="87dde-159">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CV: 90KUJA7HKEaG8wHu.0
MS-ServerId: 101112616
Date: Tue, 24 Jan 2017 23:27:18 GMT
```
