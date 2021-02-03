---
title: Restaurar um utilizador eliminado para um cliente
description: Como restaurar um Utilizador eliminado pelo ID do cliente e iD do utilizador.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9fd86a268c804a2fdd5efd67a8982afc043c95a6
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769799"
---
# <a name="restore-a-deleted-user-for-a-customer"></a><span data-ttu-id="5f8ef-103">Restaurar um utilizador eliminado para um cliente</span><span class="sxs-lookup"><span data-stu-id="5f8ef-103">Restore a deleted user for a customer</span></span>

<span data-ttu-id="5f8ef-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="5f8ef-104">**Applies To**</span></span>

- <span data-ttu-id="5f8ef-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="5f8ef-105">Partner Center</span></span>

<span data-ttu-id="5f8ef-106">Como restaurar um **Utilizador** eliminado pelo ID do cliente e iD do utilizador.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-106">How to restore a deleted **User** by customer ID and user ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f8ef-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5f8ef-107">Prerequisites</span></span>

- <span data-ttu-id="5f8ef-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5f8ef-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5f8ef-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="5f8ef-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5f8ef-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5f8ef-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5f8ef-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5f8ef-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="5f8ef-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5f8ef-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="5f8ef-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5f8ef-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5f8ef-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="5f8ef-116">A identificação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-116">The user ID.</span></span> <span data-ttu-id="5f8ef-117">Se não tiver o ID do utilizador, consulte [utilizadores eliminados para um cliente](view-a-deleted-user.md).</span><span class="sxs-lookup"><span data-stu-id="5f8ef-117">If you do not have the user ID, see [View deleted users for a customer](view-a-deleted-user.md).</span></span>

## <a name="when-can-you-restore-a-deleted-user-account"></a><span data-ttu-id="5f8ef-118">Quando pode restaurar uma conta de utilizador eliminada?</span><span class="sxs-lookup"><span data-stu-id="5f8ef-118">When can you restore a deleted user account?</span></span>

<span data-ttu-id="5f8ef-119">O estado do utilizador está definido para "inativo" quando apaga uma conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-119">The user state is set to "inactive" when you delete a user account.</span></span> <span data-ttu-id="5f8ef-120">Permanece assim durante trinta dias, após o que a conta de utilizador e os seus dados associados são purgados e tornados irrecuperáveis.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-120">It remains that way for thirty days, after which the user account and its associated data are purged and made unrecoverable.</span></span> <span data-ttu-id="5f8ef-121">Só é possível restaurar uma conta de utilizador eliminada durante esta janela de trinta dias.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-121">You can only restore a deleted user account during this thirty-day window.</span></span> <span data-ttu-id="5f8ef-122">Uma vez eliminada e marcada como "inativa", a conta de utilizador deixou de ser devolvida como membro da coleção de utilizadores (por exemplo, utilizando [a lista de todas as contas de utilizador para um cliente).](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="5f8ef-122">Once deleted and marked "inactive" the user account is no longer returned as a member of the user collection (for example, using [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span>

## <a name="c"></a><span data-ttu-id="5f8ef-123">C\#</span><span class="sxs-lookup"><span data-stu-id="5f8ef-123">C\#</span></span>

<span data-ttu-id="5f8ef-124">Para restaurar um utilizador, crie uma nova instância da classe [**CustomerUser**](/dotnet/api/microsoft.store.partnercenter.models.users.customeruser) e desaculte o valor da propriedade [**User.State**](/dotnet/api/microsoft.store.partnercenter.models.users.user.state) para [**UserState.Ative**](/dotnet/api/microsoft.store.partnercenter.models.users.userstate).</span><span class="sxs-lookup"><span data-stu-id="5f8ef-124">To restore a user, create a new instance of the [**CustomerUser**](/dotnet/api/microsoft.store.partnercenter.models.users.customeruser) class, and set the value of the [**User.State**](/dotnet/api/microsoft.store.partnercenter.models.users.user.state) property to [**UserState.Active**](/dotnet/api/microsoft.store.partnercenter.models.users.userstate).</span></span>

<span data-ttu-id="5f8ef-125">Restaura um utilizador eliminado definindo o estado do utilizador para ativo.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-125">You restore a deleted user by setting the user's state to active.</span></span> <span data-ttu-id="5f8ef-126">Não é preciso repovoar os restantes campos no recurso do utilizador.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-126">You do not have to repopulate the remaining fields in the user resource.</span></span> <span data-ttu-id="5f8ef-127">Estes valores serão automaticamente restaurados a partir do recurso de utilizador eliminado e inativo.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-127">Those values will automatically be restored from the deleted, inactive user resource.</span></span> <span data-ttu-id="5f8ef-128">Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente e o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para identificar o utilizador.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-128">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the user.</span></span>

<span data-ttu-id="5f8ef-129">Por fim, ligue para o método [**Patch**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.patch) e passe a instância **CustomerUser** para enviar o pedido para restaurar o utilizador.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-129">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.patch) method and pass the **CustomerUser** instance to send the request to restore the user.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedCustomerUserId;

var updatedCustomerUser = new CustomerUser()
{
    State = UserState.Active
};

// Restore customer user information.
var restoredCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Patch(updatedCustomerUser);
```

<span data-ttu-id="5f8ef-130">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="5f8ef-130">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="5f8ef-131">**Projeto**: Partner Center SDK Samples **Class**: CustomerUserRestore.cs</span><span class="sxs-lookup"><span data-stu-id="5f8ef-131">**Project**: Partner Center SDK Samples **Class**: CustomerUserRestore.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="5f8ef-132">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5f8ef-132">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5f8ef-133">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f8ef-133">Request syntax</span></span>

| <span data-ttu-id="5f8ef-134">Método</span><span class="sxs-lookup"><span data-stu-id="5f8ef-134">Method</span></span>    | <span data-ttu-id="5f8ef-135">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5f8ef-135">Request URI</span></span>                                                                                            |
|-----------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5f8ef-136">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="5f8ef-136">**PATCH**</span></span> | <span data-ttu-id="5f8ef-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5f8ef-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="5f8ef-138">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="5f8ef-138">URI parameter</span></span>

<span data-ttu-id="5f8ef-139">Utilize os seguintes parâmetros de consulta para especificar o id do cliente e o id do utilizador.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-139">Use the following query parameters to specify the customer id and user id.</span></span>

| <span data-ttu-id="5f8ef-140">Nome</span><span class="sxs-lookup"><span data-stu-id="5f8ef-140">Name</span></span>                   | <span data-ttu-id="5f8ef-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="5f8ef-141">Type</span></span>     | <span data-ttu-id="5f8ef-142">Necessário</span><span class="sxs-lookup"><span data-stu-id="5f8ef-142">Required</span></span> | <span data-ttu-id="5f8ef-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f8ef-143">Description</span></span>                                                                                                              |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5f8ef-144">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="5f8ef-144">**customer-tenant-id**</span></span> | <span data-ttu-id="5f8ef-145">**guid**</span><span class="sxs-lookup"><span data-stu-id="5f8ef-145">**guid**</span></span> | <span data-ttu-id="5f8ef-146">Y</span><span class="sxs-lookup"><span data-stu-id="5f8ef-146">Y</span></span>        | <span data-ttu-id="5f8ef-147">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados a um determinado cliente.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-147">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results to a given customer.</span></span> |
| <span data-ttu-id="5f8ef-148">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="5f8ef-148">**user-id**</span></span>            | <span data-ttu-id="5f8ef-149">**guid**</span><span class="sxs-lookup"><span data-stu-id="5f8ef-149">**guid**</span></span> | <span data-ttu-id="5f8ef-150">Y</span><span class="sxs-lookup"><span data-stu-id="5f8ef-150">Y</span></span>        | <span data-ttu-id="5f8ef-151">O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-151">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                         |

### <a name="request-headers"></a><span data-ttu-id="5f8ef-152">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="5f8ef-152">Request headers</span></span>

<span data-ttu-id="5f8ef-153">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5f8ef-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5f8ef-154">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5f8ef-154">Request body</span></span>

<span data-ttu-id="5f8ef-155">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-155">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="5f8ef-156">Nome</span><span class="sxs-lookup"><span data-stu-id="5f8ef-156">Name</span></span>       | <span data-ttu-id="5f8ef-157">Tipo</span><span class="sxs-lookup"><span data-stu-id="5f8ef-157">Type</span></span>   | <span data-ttu-id="5f8ef-158">Necessário</span><span class="sxs-lookup"><span data-stu-id="5f8ef-158">Required</span></span> | <span data-ttu-id="5f8ef-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f8ef-159">Description</span></span>                                                            |
|------------|--------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="5f8ef-160">Estado</span><span class="sxs-lookup"><span data-stu-id="5f8ef-160">State</span></span>      | <span data-ttu-id="5f8ef-161">string</span><span class="sxs-lookup"><span data-stu-id="5f8ef-161">string</span></span> | <span data-ttu-id="5f8ef-162">Y</span><span class="sxs-lookup"><span data-stu-id="5f8ef-162">Y</span></span>        | <span data-ttu-id="5f8ef-163">O estado de utilizador.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-163">The user state.</span></span> <span data-ttu-id="5f8ef-164">Para restaurar um utilizador eliminado, esta cadeia deve conter "ativo".</span><span class="sxs-lookup"><span data-stu-id="5f8ef-164">To restore a deleted user, this string must contain "active".</span></span> |
| <span data-ttu-id="5f8ef-165">Atributos</span><span class="sxs-lookup"><span data-stu-id="5f8ef-165">Attributes</span></span> | <span data-ttu-id="5f8ef-166">objeto</span><span class="sxs-lookup"><span data-stu-id="5f8ef-166">object</span></span> | <span data-ttu-id="5f8ef-167">N</span><span class="sxs-lookup"><span data-stu-id="5f8ef-167">N</span></span>        | <span data-ttu-id="5f8ef-168">Contém "ObjectType": "CustomerUser".</span><span class="sxs-lookup"><span data-stu-id="5f8ef-168">Contains "ObjectType": "CustomerUser".</span></span>                                 |

### <a name="request-example"></a><span data-ttu-id="5f8ef-169">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5f8ef-169">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 6e668bc0-5bd7-44d6-b6fa-529d41ce9659
MS-CorrelationId: 32be760f-8282-4e01-a37b-829c8a700e8a
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 269
Expect: 100-continue

{
    "State": "active",
    "Attributes": {
        "ObjectType": "CustomerUser"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="5f8ef-170">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5f8ef-170">REST response</span></span>

<span data-ttu-id="5f8ef-171">Se for bem sucedida, a resposta devolve a informação restaurada do utilizador no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-171">If successful, the response returns the restored user information in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5f8ef-172">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5f8ef-172">Response success and error codes</span></span>

<span data-ttu-id="5f8ef-173">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-173">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5f8ef-174">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5f8ef-174">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5f8ef-175">Para obter a lista completa, consulte [os Códigos de Erro DO Centro de Parceiros REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="5f8ef-175">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5f8ef-176">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5f8ef-176">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 465
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 32be760f-8282-4e01-a37b-829c8a700e8a
MS-RequestId: 6e668bc0-5bd7-44d6-b6fa-529d41ce9659
MS-CV: ZTeBriO7mEaiM13+.0
MS-ServerId: 101112616
Date: Fri, 20 Jan 2017 22:24:55 GMT

{
    "usageLocation": "US",
    "id": "a45f1416-3300-4f65-9e8d-f123b397a4ea",
    "userPrincipalName": "e83763f7f2204ac384cfcd49f79f2749@dtdemocspcustomer005.onmicrosoft.com",
    "firstName": "Ferdinand",
    "lastName": "Filibuster",
    "displayName": "Ferdinand",
    "userDomainType": "none",
    "state": "active",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "CustomerUser"
    }
}
```
