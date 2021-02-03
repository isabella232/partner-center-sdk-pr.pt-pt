---
title: Obter funções de utilizador para um cliente
description: Obtenha uma lista de todas as funções/permissões anexadas a uma conta de utilizador. As variações incluem obter uma lista de todas as permissões em todas as contas de utilizador para um cliente, e obter uma lista de utilizadores que têm uma determinada função.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8dad5c035c08905c3d39052de07ebb912452a16b
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768906"
---
# <a name="get-user-roles-for-a-customer"></a><span data-ttu-id="df4ed-104">Obter funções de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="df4ed-104">Get user roles for a customer</span></span>

<span data-ttu-id="df4ed-105">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="df4ed-105">**Applies To**</span></span>

- <span data-ttu-id="df4ed-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="df4ed-106">Partner Center</span></span>

<span data-ttu-id="df4ed-107">Obtenha uma lista de todas as funções/permissões anexadas a uma conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="df4ed-107">Get a list of all the roles/permissions attached to a user account.</span></span> <span data-ttu-id="df4ed-108">As variações incluem obter uma lista de todas as permissões em todas as contas de utilizador para um cliente, e obter uma lista de utilizadores que têm uma determinada função.</span><span class="sxs-lookup"><span data-stu-id="df4ed-108">Variations include getting a list of all permissions across all user accounts for a customer, and getting a list of users that have a given role.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="df4ed-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="df4ed-109">Prerequisites</span></span>

- <span data-ttu-id="df4ed-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="df4ed-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="df4ed-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="df4ed-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="df4ed-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="df4ed-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="df4ed-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="df4ed-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="df4ed-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="df4ed-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="df4ed-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="df4ed-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="df4ed-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="df4ed-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="df4ed-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="df4ed-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="df4ed-118">C\#</span><span class="sxs-lookup"><span data-stu-id="df4ed-118">C\#</span></span>

<span data-ttu-id="df4ed-119">Para recuperar todas as funções de diretório para um cliente especificado, recupere primeiro o ID do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="df4ed-119">To retrieve all the directory roles for a specified customer, first retrieve the specified customer ID.</span></span> <span data-ttu-id="df4ed-120">Em seguida, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="df4ed-120">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="df4ed-121">Em seguida, ligue para a propriedade **DirectoryRoles,** seguida do método **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="df4ed-121">Then call the **DirectoryRoles** property, followed by the **Get()** or **GetAsync()** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var directoryRoles = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.Get();
```

<span data-ttu-id="df4ed-122">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="df4ed-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="df4ed-123">**Projeto**: Partner Center SDK Samples **Class**: GetCustomerDirectoryRoles.cs</span><span class="sxs-lookup"><span data-stu-id="df4ed-123">**Project**: Partner Center SDK Samples **Class**: GetCustomerDirectoryRoles.cs</span></span>

<span data-ttu-id="df4ed-124">Para recuperar uma lista de utilizadores de clientes que têm uma determinada função, primeiro recupere o ID do cliente especificado e o ID de papel de diretório.</span><span class="sxs-lookup"><span data-stu-id="df4ed-124">To retrieve a list of customer users that have a given role, first retrieve the specified customer ID and the directory role ID.</span></span> <span data-ttu-id="df4ed-125">Em seguida, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="df4ed-125">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="df4ed-126">Em seguida, ligue para a propriedade **Do Diretório,** em seguida, o método **ById()** e, em seguida, a propriedade **UserMembers,** o seguido pelo método **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="df4ed-126">Then call the **DirectoryRoles** property, then **ById()** method, then the **UserMembers** property, the followed by the **Get()** or **GetAsync()** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;
// string selectedDirectoryRoleId;

var userMembers = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedDirectoryRoleId).UserMembers.Get();
```

<span data-ttu-id="df4ed-127">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="df4ed-127">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="df4ed-128">**Projeto**: PartnerSDK.FeatureSamples **Class**: GetCustomerDirectoryRoleUserMembers.cs</span><span class="sxs-lookup"><span data-stu-id="df4ed-128">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerDirectoryRoleUserMembers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="df4ed-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="df4ed-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="df4ed-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="df4ed-130">Request syntax</span></span>

| <span data-ttu-id="df4ed-131">Método</span><span class="sxs-lookup"><span data-stu-id="df4ed-131">Method</span></span>  | <span data-ttu-id="df4ed-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="df4ed-132">Request URI</span></span>                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="df4ed-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="df4ed-133">**GET**</span></span> | <span data-ttu-id="df4ed-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id}/diretórios HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="df4ed-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id}/directoryroles HTTP/1.1</span></span> |
| <span data-ttu-id="df4ed-135">**Obter**</span><span class="sxs-lookup"><span data-stu-id="df4ed-135">**GET**</span></span> | <span data-ttu-id="df4ed-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/diretórios HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="df4ed-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles HTTP/1.1</span></span>                 |
| <span data-ttu-id="df4ed-137">**Obter**</span><span class="sxs-lookup"><span data-stu-id="df4ed-137">**GET**</span></span> | <span data-ttu-id="df4ed-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directyroles/{role-ID}/usermembers</span><span class="sxs-lookup"><span data-stu-id="df4ed-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers</span></span>    |

### <a name="uri-parameter"></a><span data-ttu-id="df4ed-139">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="df4ed-139">URI parameter</span></span>

<span data-ttu-id="df4ed-140">Utilize o seguinte parâmetro de consulta para identificar o cliente correto.</span><span class="sxs-lookup"><span data-stu-id="df4ed-140">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="df4ed-141">Nome</span><span class="sxs-lookup"><span data-stu-id="df4ed-141">Name</span></span>                   | <span data-ttu-id="df4ed-142">Tipo</span><span class="sxs-lookup"><span data-stu-id="df4ed-142">Type</span></span>     | <span data-ttu-id="df4ed-143">Necessário</span><span class="sxs-lookup"><span data-stu-id="df4ed-143">Required</span></span> | <span data-ttu-id="df4ed-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="df4ed-144">Description</span></span>                                                                                                                                                                                                 |
|------------------------|----------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="df4ed-145">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="df4ed-145">**customer-tenant-id**</span></span> | <span data-ttu-id="df4ed-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="df4ed-146">**guid**</span></span> | <span data-ttu-id="df4ed-147">Y</span><span class="sxs-lookup"><span data-stu-id="df4ed-147">Y</span></span>        | <span data-ttu-id="df4ed-148">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="df4ed-148">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span>                                                      |
| <span data-ttu-id="df4ed-149">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="df4ed-149">**user-id**</span></span>            | <span data-ttu-id="df4ed-150">**guid**</span><span class="sxs-lookup"><span data-stu-id="df4ed-150">**guid**</span></span> | <span data-ttu-id="df4ed-151">N</span><span class="sxs-lookup"><span data-stu-id="df4ed-151">N</span></span>        | <span data-ttu-id="df4ed-152">O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="df4ed-152">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                                                                            |
| <span data-ttu-id="df4ed-153">**id role**</span><span class="sxs-lookup"><span data-stu-id="df4ed-153">**role-id**</span></span>            | <span data-ttu-id="df4ed-154">**guid**</span><span class="sxs-lookup"><span data-stu-id="df4ed-154">**guid**</span></span> | <span data-ttu-id="df4ed-155">N</span><span class="sxs-lookup"><span data-stu-id="df4ed-155">N</span></span>        | <span data-ttu-id="df4ed-156">O valor é um **id de função** formatado GUID que pertence a um tipo de papel.</span><span class="sxs-lookup"><span data-stu-id="df4ed-156">The value is a GUID formatted **role-id** that belongs to a type of role.</span></span> <span data-ttu-id="df4ed-157">Você pode obter estes IDs consultando todas as funções de diretório para um cliente, em todas as contas do utilizador.</span><span class="sxs-lookup"><span data-stu-id="df4ed-157">You can get these IDs by querying all the directory roles for a customer, across all user accounts.</span></span> <span data-ttu-id="df4ed-158">(O segundo cenário, acima).</span><span class="sxs-lookup"><span data-stu-id="df4ed-158">(The second scenario, above).</span></span> |

### <a name="request-headers"></a><span data-ttu-id="df4ed-159">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="df4ed-159">Request headers</span></span>

<span data-ttu-id="df4ed-160">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="df4ed-160">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="df4ed-161">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="df4ed-161">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="df4ed-162">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="df4ed-162">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id>/directoryroles HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
```

## <a name="rest-response"></a><span data-ttu-id="df4ed-163">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="df4ed-163">REST response</span></span>

<span data-ttu-id="df4ed-164">Se for bem sucedido, este método devolve uma lista das funções associadas à conta de utilizador dada.</span><span class="sxs-lookup"><span data-stu-id="df4ed-164">If successful, this method returns a list of the roles associated with the given user account.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="df4ed-165">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="df4ed-165">Response success and error codes</span></span>

<span data-ttu-id="df4ed-166">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="df4ed-166">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="df4ed-167">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="df4ed-167">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="df4ed-168">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="df4ed-168">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="df4ed-169">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="df4ed-169">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST

{
      "totalCount": 2,
      "items": [
        {
          "name": "Helpdesk Administrator",
          "id": "729827e3-9c14-49f7-bb1b-9608f156bbb8",
          "attributes": { "objectType": "DirectoryRole" }
        },
        {
          "name": "User Account Administrator",
          "id": "fe930be7-5e62-47db-91af-98c3a49a38b1",
          "attributes": { "objectType": "DirectoryRole" }
        }
      ],
      "attributes": { "objectType": "Collection" }
}
```
