---
title: Eliminar uma conta de utilizador para um cliente
description: Como eliminar uma conta de utilizador existente para um cliente.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 77fc1a1c7264779ca549be8d52798e90c91138bb
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769380"
---
# <a name="delete-a-user-account-for-a-customer"></a><span data-ttu-id="e80c6-103">Eliminar uma conta de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="e80c6-103">Delete a user account for a customer</span></span>

<span data-ttu-id="e80c6-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="e80c6-104">**Applies to:**</span></span>

- <span data-ttu-id="e80c6-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="e80c6-105">Partner Center</span></span>

<span data-ttu-id="e80c6-106">Este artigo explica como eliminar uma conta de utilizador existente para um cliente.</span><span class="sxs-lookup"><span data-stu-id="e80c6-106">This article explains how to delete an existing user account for a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e80c6-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e80c6-107">Prerequisites</span></span>

- <span data-ttu-id="e80c6-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e80c6-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e80c6-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="e80c6-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e80c6-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e80c6-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e80c6-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e80c6-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e80c6-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="e80c6-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e80c6-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="e80c6-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e80c6-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="e80c6-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e80c6-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e80c6-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="e80c6-116">Uma identificação de utilizador.</span><span class="sxs-lookup"><span data-stu-id="e80c6-116">A user ID.</span></span> <span data-ttu-id="e80c6-117">Se não tiver o ID do utilizador, consulte [obter uma lista de todas as contas do utilizador para um cliente.](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="e80c6-117">If you do not have the user ID, see [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md).</span></span>

## <a name="deleting-a-user-account"></a><span data-ttu-id="e80c6-118">Apagar uma conta de utilizador</span><span class="sxs-lookup"><span data-stu-id="e80c6-118">Deleting a user account</span></span>

<span data-ttu-id="e80c6-119">Quando elimina uma conta de utilizador, o estado do utilizador está definido para **inativar** durante trinta dias.</span><span class="sxs-lookup"><span data-stu-id="e80c6-119">When you delete a user account, the user state is set to **inactive** for thirty days.</span></span> <span data-ttu-id="e80c6-120">Após trinta dias, a conta de utilizador e os seus dados associados são purgados e tornados irrecuperáveis.</span><span class="sxs-lookup"><span data-stu-id="e80c6-120">After thirty days, the user account and its associated data are purged and made unrecoverable.</span></span>

<span data-ttu-id="e80c6-121">Pode [restaurar uma conta de utilizador eliminada para um cliente](restore-a-user-for-a-customer.md) se a conta inativa estiver dentro da janela de trinta dias.</span><span class="sxs-lookup"><span data-stu-id="e80c6-121">You can [restore a deleted user account for a customer](restore-a-user-for-a-customer.md) if the inactive account is within the thirty day window.</span></span> <span data-ttu-id="e80c6-122">No entanto, quando restaura uma conta que foi eliminada e marcada como inativa, a conta deixou de ser devolvida como membro da coleção de utilizadores (por exemplo, quando [obtém uma lista de todas as contas de utilizador de um cliente).](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="e80c6-122">However, when you restore an account that was deleted and marked as inactive, the account is no longer returned as a member of the user collection (for example, when you [get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span>

## <a name="c"></a><span data-ttu-id="e80c6-123">C\#</span><span class="sxs-lookup"><span data-stu-id="e80c6-123">C\#</span></span>

<span data-ttu-id="e80c6-124">Para eliminar uma conta de utilizador do cliente existente:</span><span class="sxs-lookup"><span data-stu-id="e80c6-124">To delete an existing customer user account:</span></span>

1. <span data-ttu-id="e80c6-125">Utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e80c6-125">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="e80c6-126">Ligue para o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para identificar o utilizador.</span><span class="sxs-lookup"><span data-stu-id="e80c6-126">Call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the user.</span></span>

3. <span data-ttu-id="e80c6-127">Ligue para o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) para eliminar o utilizador e definir o estado do utilizador para inativo.</span><span class="sxs-lookup"><span data-stu-id="e80c6-127">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) method to delete the user and set the user state to inactive.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string customerUserIdToDelete;

partnerOperations.Customers.ById(selectedCustomerId).Users.ById(customerUserIdToDelete).Delete();
```

<span data-ttu-id="e80c6-128">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e80c6-128">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e80c6-129">**Projeto**: Partner Center SDK Samples **Class**: DeleteCustomerUser.cs</span><span class="sxs-lookup"><span data-stu-id="e80c6-129">**Project**: Partner Center SDK Samples **Class**: DeleteCustomerUser.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e80c6-130">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="e80c6-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e80c6-131">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="e80c6-131">Request syntax</span></span>

| <span data-ttu-id="e80c6-132">Método</span><span class="sxs-lookup"><span data-stu-id="e80c6-132">Method</span></span>     | <span data-ttu-id="e80c6-133">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="e80c6-133">Request URI</span></span>                                                                                            |
|------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e80c6-134">DELETE</span><span class="sxs-lookup"><span data-stu-id="e80c6-134">DELETE</span></span>     | <span data-ttu-id="e80c6-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e80c6-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="e80c6-136">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="e80c6-136">URI parameters</span></span>

<span data-ttu-id="e80c6-137">Utilize os seguintes parâmetros de consulta para identificar o cliente e o utilizador.</span><span class="sxs-lookup"><span data-stu-id="e80c6-137">Use the following query parameters to identify the customer and user.</span></span>

| <span data-ttu-id="e80c6-138">Nome</span><span class="sxs-lookup"><span data-stu-id="e80c6-138">Name</span></span>                   | <span data-ttu-id="e80c6-139">Tipo</span><span class="sxs-lookup"><span data-stu-id="e80c6-139">Type</span></span>     | <span data-ttu-id="e80c6-140">Necessário</span><span class="sxs-lookup"><span data-stu-id="e80c6-140">Required</span></span> | <span data-ttu-id="e80c6-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="e80c6-141">Description</span></span>                                                                                                               |
|------------------------|----------|----------|---------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e80c6-142">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="e80c6-142">customer-tenant-id</span></span>     | <span data-ttu-id="e80c6-143">GUID</span><span class="sxs-lookup"><span data-stu-id="e80c6-143">GUID</span></span>     | <span data-ttu-id="e80c6-144">Y</span><span class="sxs-lookup"><span data-stu-id="e80c6-144">Y</span></span>        | <span data-ttu-id="e80c6-145">O valor é um **design de cliente-inquilino** formatado pelo GUID que permite ao revendedor filtrar os resultados de um determinado cliente.</span><span class="sxs-lookup"><span data-stu-id="e80c6-145">The value is a GUID-formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer.</span></span> |
| <span data-ttu-id="e80c6-146">user-id</span><span class="sxs-lookup"><span data-stu-id="e80c6-146">user-id</span></span>                | <span data-ttu-id="e80c6-147">GUID</span><span class="sxs-lookup"><span data-stu-id="e80c6-147">GUID</span></span>     | <span data-ttu-id="e80c6-148">Y</span><span class="sxs-lookup"><span data-stu-id="e80c6-148">Y</span></span>        | <span data-ttu-id="e80c6-149">O valor é um **id** de utilizador com formato GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="e80c6-149">The value is a GUID-formatted **user-id** that belongs to a single user account.</span></span>                                          |

### <a name="request-headers"></a><span data-ttu-id="e80c6-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="e80c6-150">Request headers</span></span>

<span data-ttu-id="e80c6-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e80c6-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e80c6-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="e80c6-152">Request body</span></span>

<span data-ttu-id="e80c6-153">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e80c6-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e80c6-154">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e80c6-154">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e80c6-155">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="e80c6-155">REST response</span></span>

<span data-ttu-id="e80c6-156">Se for bem sucedido, este método devolve um código de estado **204 No Content.**</span><span class="sxs-lookup"><span data-stu-id="e80c6-156">If successful, this method returns a **204 No Content** status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e80c6-157">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="e80c6-157">Response success and error codes</span></span>

<span data-ttu-id="e80c6-158">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="e80c6-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e80c6-159">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="e80c6-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e80c6-160">Para obter a lista completa, consulte [os Códigos de Erro DO Centro de Parceiros REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="e80c6-160">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e80c6-161">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e80c6-161">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CV: 90KUJA7HKEaG8wHu.0
MS-ServerId: 101112616
Date: Tue, 24 Jan 2017 23:27:18 GMT
```
