---
title: Ver utilizadores eliminados para um cliente
description: Obtém uma lista de recursos do CustomerUser eliminados para um cliente por identificação do cliente. Pode configurar opcionalmente o tamanho da página. Deve fornecer um filtro.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9b1a9b85e3eba7ae7ec1dab8e951134d03371604
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769535"
---
# <a name="view-deleted-users-for-a-customer"></a><span data-ttu-id="eb1fd-105">Ver utilizadores eliminados para um cliente</span><span class="sxs-lookup"><span data-stu-id="eb1fd-105">View deleted users for a customer</span></span>

<span data-ttu-id="eb1fd-106">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="eb1fd-106">**Applies To**</span></span>

- <span data-ttu-id="eb1fd-107">Partner Center</span><span class="sxs-lookup"><span data-stu-id="eb1fd-107">Partner Center</span></span>

<span data-ttu-id="eb1fd-108">Obtém uma lista de recursos do CustomerUser eliminados para um cliente por identificação do cliente.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-108">Gets a list of deleted CustomerUser resources for a customer by customer ID.</span></span> <span data-ttu-id="eb1fd-109">Pode configurar opcionalmente o tamanho da página.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-109">You can optionally set a page size.</span></span> <span data-ttu-id="eb1fd-110">Deve fornecer um filtro.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-110">You must supply a filter.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb1fd-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="eb1fd-111">Prerequisites</span></span>

- <span data-ttu-id="eb1fd-112">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eb1fd-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="eb1fd-113">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-113">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="eb1fd-114">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb1fd-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="eb1fd-115">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="eb1fd-116">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="eb1fd-117">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="eb1fd-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="eb1fd-118">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="eb1fd-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="eb1fd-119">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb1fd-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="what-happens-when-you-delete-a-user-account"></a><span data-ttu-id="eb1fd-120">O que acontece quando se apaga uma conta de utilizador?</span><span class="sxs-lookup"><span data-stu-id="eb1fd-120">What happens when you delete a user account?</span></span>

<span data-ttu-id="eb1fd-121">O estado do utilizador está definido para "inativo" quando apaga uma conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-121">The user state is set to "inactive" when you delete a user account.</span></span> <span data-ttu-id="eb1fd-122">Permanece assim durante trinta dias, após o que a conta de utilizador e os seus dados associados são purgados e tornados irrecuperáveis.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-122">It remains that way for thirty days, after which the user account and its associated data are purged and made unrecoverable.</span></span> <span data-ttu-id="eb1fd-123">Se pretender restaurar uma conta de utilizador eliminada dentro da janela de trinta dias, consulte [Restaurar um utilizador eliminado para um cliente](restore-a-user-for-a-customer.md).</span><span class="sxs-lookup"><span data-stu-id="eb1fd-123">If you want to restore a deleted user account within the thirty day window, see [Restore a deleted user for a customer](restore-a-user-for-a-customer.md).</span></span> <span data-ttu-id="eb1fd-124">Uma vez eliminada e marcada como "inativa", a conta de utilizador deixou de ser devolvida como membro da coleção de utilizadores (por exemplo, utilizando [a lista de todas as contas de utilizador para um cliente).](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="eb1fd-124">Once deleted and marked "inactive", the user account is no longer returned as a member of the user collection (for example, using [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span> <span data-ttu-id="eb1fd-125">Para obter uma lista de utilizadores eliminados que ainda não foram purgados, é necessário consultar as contas dos utilizadores que tenham sido definidas como inativas.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-125">To get a list of deleted users that have not yet been purged, you must query for user accounts that have been set to inactive.</span></span>

## <a name="c"></a><span data-ttu-id="eb1fd-126">C\#</span><span class="sxs-lookup"><span data-stu-id="eb1fd-126">C\#</span></span>

<span data-ttu-id="eb1fd-127">Para recuperar uma lista de utilizadores eliminados, construa uma consulta que filtra para os utilizadores do cliente cujo estado está definido para inativo.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-127">To retrieve a list of deleted users, construct a query that filters for customer users whose status is set to inactive.</span></span> <span data-ttu-id="eb1fd-128">Em primeiro lugar, crie o filtro instantaneamente um objeto [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) com os parâmetros mostrados no seguinte corte de código.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-128">First, create the filter by instantiating a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object with the parameters as shown in the following code snippet.</span></span> <span data-ttu-id="eb1fd-129">Em seguida, crie a consulta utilizando o método [**BuildIndexedQuery.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery)</span><span class="sxs-lookup"><span data-stu-id="eb1fd-129">Then create the query using the [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) method.</span></span> <span data-ttu-id="eb1fd-130">Se não quiser resultados em página, pode utilizar o método [**BuildSimpleQuery.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery)</span><span class="sxs-lookup"><span data-stu-id="eb1fd-130">If you do not want paged results, you can use the [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method instead.</span></span> <span data-ttu-id="eb1fd-131">Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-131">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="eb1fd-132">Finalmente, ligue para o método [**de consulta**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.query) para enviar o pedido.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-132">Finally, call the [**Query**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.query) method to send the request.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// int customerUserPageSize;

// Create a filter for users whose status is inactive (i.e. deleted).
var filter = new SimpleFieldFilter("UserState", FieldFilterOperation.Equals, "Inactive");

// Build a paged query.
var simpleQueryWithFilter = QueryFactory.Instance.BuildIndexedQuery(customerUserPageSize, 0, filter);

// Send the request.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.Query(simpleQueryWithFilter);
```

<span data-ttu-id="eb1fd-133">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="eb1fd-133">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="eb1fd-134">**Projeto**: Partner Center SDK Samples **Class**: GetCustomerInactiveUsers.cs</span><span class="sxs-lookup"><span data-stu-id="eb1fd-134">**Project**: Partner Center SDK Samples **Class**: GetCustomerInactiveUsers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="eb1fd-135">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="eb1fd-135">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="eb1fd-136">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb1fd-136">Request syntax</span></span>

| <span data-ttu-id="eb1fd-137">Método</span><span class="sxs-lookup"><span data-stu-id="eb1fd-137">Method</span></span>  | <span data-ttu-id="eb1fd-138">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="eb1fd-138">Request URI</span></span>                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb1fd-139">**Obter**</span><span class="sxs-lookup"><span data-stu-id="eb1fd-139">**GET**</span></span> | <span data-ttu-id="eb1fd-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users?size={size}&filtro={{filter} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="eb1fd-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users?size={size}&filter={filter} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="eb1fd-141">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="eb1fd-141">URI parameter</span></span>

<span data-ttu-id="eb1fd-142">Utilize os seguintes parâmetros de percurso e consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-142">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="eb1fd-143">Nome</span><span class="sxs-lookup"><span data-stu-id="eb1fd-143">Name</span></span>        | <span data-ttu-id="eb1fd-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="eb1fd-144">Type</span></span>   | <span data-ttu-id="eb1fd-145">Necessário</span><span class="sxs-lookup"><span data-stu-id="eb1fd-145">Required</span></span> | <span data-ttu-id="eb1fd-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb1fd-146">Description</span></span>                                                                                                                                                                        |
|-------------|--------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb1fd-147">id cliente</span><span class="sxs-lookup"><span data-stu-id="eb1fd-147">customer-id</span></span> | <span data-ttu-id="eb1fd-148">guid</span><span class="sxs-lookup"><span data-stu-id="eb1fd-148">guid</span></span>   | <span data-ttu-id="eb1fd-149">Sim</span><span class="sxs-lookup"><span data-stu-id="eb1fd-149">Yes</span></span>      | <span data-ttu-id="eb1fd-150">O valor é um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-150">The value is a GUID formatted customer-id that identifies the customer.</span></span>                                                                                                            |
| <span data-ttu-id="eb1fd-151">size</span><span class="sxs-lookup"><span data-stu-id="eb1fd-151">size</span></span>        | <span data-ttu-id="eb1fd-152">int</span><span class="sxs-lookup"><span data-stu-id="eb1fd-152">int</span></span>    | <span data-ttu-id="eb1fd-153">Não</span><span class="sxs-lookup"><span data-stu-id="eb1fd-153">No</span></span>       | <span data-ttu-id="eb1fd-154">O número de resultados a apresentar ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-154">The number of results to be displayed at one time.</span></span> <span data-ttu-id="eb1fd-155">Este parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-155">This parameter is optional.</span></span>                                                                                                     |
| <span data-ttu-id="eb1fd-156">filter</span><span class="sxs-lookup"><span data-stu-id="eb1fd-156">filter</span></span>      | <span data-ttu-id="eb1fd-157">filter</span><span class="sxs-lookup"><span data-stu-id="eb1fd-157">filter</span></span> | <span data-ttu-id="eb1fd-158">Sim</span><span class="sxs-lookup"><span data-stu-id="eb1fd-158">Yes</span></span>      | <span data-ttu-id="eb1fd-159">A consulta que filtra a procura do utilizador.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-159">The query that filters the user search.</span></span> <span data-ttu-id="eb1fd-160">Para recuperar os utilizadores eliminados, deve incluir e codificar a seguinte cadeia: {"Field":"UserState","Value":"Inative", "Operador":"igual"}.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-160">To retrieve deleted users, you must include and encode the following string: {"Field":"UserState","Value":"Inactive","Operator":"equals"}.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="eb1fd-161">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="eb1fd-161">Request headers</span></span>

<span data-ttu-id="eb1fd-162">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="eb1fd-162">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="eb1fd-163">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="eb1fd-163">Request body</span></span>

<span data-ttu-id="eb1fd-164">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-164">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="eb1fd-165">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="eb1fd-165">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users?size=500&filter=%7B%22Field%22%3A%22UserState%22%2C%22Value%22%3A%22Inactive%22%2C%22Operator%22%3A%22equals%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c11feb95-55d2-45b6-9d1b-74b55d2221fb
MS-CorrelationId: 2b4ab588-f48c-4874-b479-a61895e107b2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="eb1fd-166">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="eb1fd-166">REST response</span></span>

<span data-ttu-id="eb1fd-167">Se for bem sucedido, este método devolve uma coleção de recursos [CustomerUser](user-resources.md#customeruser) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-167">If successful, this method returns a collection of [CustomerUser](user-resources.md#customeruser) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="eb1fd-168">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="eb1fd-168">Response success and error codes</span></span>

<span data-ttu-id="eb1fd-169">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-169">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="eb1fd-170">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="eb1fd-170">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="eb1fd-171">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="eb1fd-171">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="eb1fd-172">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="eb1fd-172">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 802
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 690b34ca-07c8-4f8a-ab13-f22a50594a43
MS-RequestId: 1187f9ad-02b4-4d96-b668-7cf3d289467b
MS-CV: 3TLmR9gz6EaCVCjR.0
MS-ServerId: 101112616
Date: Fri, 20 Jan 2017 19:13:14 GMT

{
    "totalCount": 1,
    "items": [{
            "usageLocation": "US",
            "id": "a45f1416-3300-4f65-9e8d-f123b397a4ea",
            "userPrincipalName": "e83763f7f2204ac384cfcd49f79f2749@dtdemocspcustomer005.onmicrosoft.com",
            "firstName": "Ferdinand",
            "lastName": "Filibuster",
            "displayName": "Ferdinand",
            "userDomainType": "none",
            "state": "inactive",
            "softDeletionTime": "2017-01-20T00:33:34Z",
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
    ],
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users?size=500&filter=%7B%22Field%22%3A%22UserStatus%22%2C%22Value%22%3A%22Inactive%22%2C%22Operator%22%3A%22equals%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
