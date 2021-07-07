---
title: Obter funções de utilizador para um cliente
description: Obtenha uma lista de todas as funções/permissões anexadas a uma conta de utilizador. As variações incluem obter uma lista de todas as permissões em todas as contas de utilizador para um cliente, e obter uma lista de utilizadores que têm uma determinada função.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8f58e8b7eae5bb47265bb1ac83fcdcd160f735d2
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445923"
---
# <a name="get-user-roles-for-a-customer"></a><span data-ttu-id="22056-104">Obter funções de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="22056-104">Get user roles for a customer</span></span>

<span data-ttu-id="22056-105">Obtenha uma lista de todas as funções/permissões anexadas a uma conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="22056-105">Get a list of all the roles/permissions attached to a user account.</span></span> <span data-ttu-id="22056-106">As variações incluem obter uma lista de todas as permissões em todas as contas de utilizador para um cliente, e obter uma lista de utilizadores que têm uma determinada função.</span><span class="sxs-lookup"><span data-stu-id="22056-106">Variations include getting a list of all permissions across all user accounts for a customer, and getting a list of users that have a given role.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22056-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="22056-107">Prerequisites</span></span>

- <span data-ttu-id="22056-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="22056-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="22056-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="22056-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="22056-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="22056-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="22056-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="22056-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="22056-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="22056-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="22056-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="22056-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="22056-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="22056-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="22056-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="22056-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="22056-116">C\#</span><span class="sxs-lookup"><span data-stu-id="22056-116">C\#</span></span>

<span data-ttu-id="22056-117">Para recuperar todas as funções de diretório para um cliente especificado, recupere primeiro o ID do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="22056-117">To retrieve all the directory roles for a specified customer, first retrieve the specified customer ID.</span></span> <span data-ttu-id="22056-118">Em seguida, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="22056-118">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="22056-119">Em seguida, ligue para a propriedade **DirectoryRoles,** seguida do método **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="22056-119">Then call the **DirectoryRoles** property, followed by the **Get()** or **GetAsync()** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var directoryRoles = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.Get();
```

<span data-ttu-id="22056-120">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="22056-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="22056-121">**Project**: Partner Center SDK Samples **Class**: GetCustomerDirectoryRoles.cs</span><span class="sxs-lookup"><span data-stu-id="22056-121">**Project**: Partner Center SDK Samples **Class**: GetCustomerDirectoryRoles.cs</span></span>

<span data-ttu-id="22056-122">Para recuperar uma lista de utilizadores de clientes que têm uma determinada função, primeiro recupere o ID do cliente especificado e o ID de papel de diretório.</span><span class="sxs-lookup"><span data-stu-id="22056-122">To retrieve a list of customer users that have a given role, first retrieve the specified customer ID and the directory role ID.</span></span> <span data-ttu-id="22056-123">Em seguida, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="22056-123">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="22056-124">Em seguida, ligue para a propriedade **Do Diretório,** em seguida, o método **ById()** e, em seguida, a propriedade **UserMembers,** o seguido pelo método **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="22056-124">Then call the **DirectoryRoles** property, then **ById()** method, then the **UserMembers** property, the followed by the **Get()** or **GetAsync()** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;
// string selectedDirectoryRoleId;

var userMembers = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedDirectoryRoleId).UserMembers.Get();
```

<span data-ttu-id="22056-125">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="22056-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="22056-126">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerDirectoryRoleUserMembers.cs</span><span class="sxs-lookup"><span data-stu-id="22056-126">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerDirectoryRoleUserMembers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="22056-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="22056-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="22056-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="22056-128">Request syntax</span></span>

| <span data-ttu-id="22056-129">Método</span><span class="sxs-lookup"><span data-stu-id="22056-129">Method</span></span>  | <span data-ttu-id="22056-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="22056-130">Request URI</span></span>                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="22056-131">**Obter**</span><span class="sxs-lookup"><span data-stu-id="22056-131">**GET**</span></span> | <span data-ttu-id="22056-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id}/diretórios HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="22056-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id}/directoryroles HTTP/1.1</span></span> |
| <span data-ttu-id="22056-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="22056-133">**GET**</span></span> | <span data-ttu-id="22056-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/diretórios HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="22056-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles HTTP/1.1</span></span>                 |
| <span data-ttu-id="22056-135">**Obter**</span><span class="sxs-lookup"><span data-stu-id="22056-135">**GET**</span></span> | <span data-ttu-id="22056-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directyroles/{role-ID}/usermembers</span><span class="sxs-lookup"><span data-stu-id="22056-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers</span></span>    |

### <a name="uri-parameter"></a><span data-ttu-id="22056-137">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="22056-137">URI parameter</span></span>

<span data-ttu-id="22056-138">Utilize o seguinte parâmetro de consulta para identificar o cliente correto.</span><span class="sxs-lookup"><span data-stu-id="22056-138">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="22056-139">Nome</span><span class="sxs-lookup"><span data-stu-id="22056-139">Name</span></span>                   | <span data-ttu-id="22056-140">Tipo</span><span class="sxs-lookup"><span data-stu-id="22056-140">Type</span></span>     | <span data-ttu-id="22056-141">Necessário</span><span class="sxs-lookup"><span data-stu-id="22056-141">Required</span></span> | <span data-ttu-id="22056-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="22056-142">Description</span></span>                                                                                                                                                                                                 |
|------------------------|----------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="22056-143">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="22056-143">**customer-tenant-id**</span></span> | <span data-ttu-id="22056-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="22056-144">**guid**</span></span> | <span data-ttu-id="22056-145">Y</span><span class="sxs-lookup"><span data-stu-id="22056-145">Y</span></span>        | <span data-ttu-id="22056-146">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="22056-146">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span>                                                      |
| <span data-ttu-id="22056-147">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="22056-147">**user-id**</span></span>            | <span data-ttu-id="22056-148">**guid**</span><span class="sxs-lookup"><span data-stu-id="22056-148">**guid**</span></span> | <span data-ttu-id="22056-149">N</span><span class="sxs-lookup"><span data-stu-id="22056-149">N</span></span>        | <span data-ttu-id="22056-150">O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="22056-150">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                                                                            |
| <span data-ttu-id="22056-151">**id role**</span><span class="sxs-lookup"><span data-stu-id="22056-151">**role-id**</span></span>            | <span data-ttu-id="22056-152">**guid**</span><span class="sxs-lookup"><span data-stu-id="22056-152">**guid**</span></span> | <span data-ttu-id="22056-153">N</span><span class="sxs-lookup"><span data-stu-id="22056-153">N</span></span>        | <span data-ttu-id="22056-154">O valor é um **id de função** formatado GUID que pertence a um tipo de papel.</span><span class="sxs-lookup"><span data-stu-id="22056-154">The value is a GUID formatted **role-id** that belongs to a type of role.</span></span> <span data-ttu-id="22056-155">Você pode obter estes IDs consultando todas as funções de diretório para um cliente, em todas as contas do utilizador.</span><span class="sxs-lookup"><span data-stu-id="22056-155">You can get these IDs by querying all the directory roles for a customer, across all user accounts.</span></span> <span data-ttu-id="22056-156">(O segundo cenário, acima).</span><span class="sxs-lookup"><span data-stu-id="22056-156">(The second scenario, above).</span></span> |

### <a name="request-headers"></a><span data-ttu-id="22056-157">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="22056-157">Request headers</span></span>

<span data-ttu-id="22056-158">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="22056-158">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="22056-159">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="22056-159">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="22056-160">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="22056-160">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id>/directoryroles HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
```

## <a name="rest-response"></a><span data-ttu-id="22056-161">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="22056-161">REST response</span></span>

<span data-ttu-id="22056-162">Se for bem sucedido, este método devolve uma lista das funções associadas à conta de utilizador dada.</span><span class="sxs-lookup"><span data-stu-id="22056-162">If successful, this method returns a list of the roles associated with the given user account.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="22056-163">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="22056-163">Response success and error codes</span></span>

<span data-ttu-id="22056-164">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="22056-164">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="22056-165">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="22056-165">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="22056-166">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="22056-166">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="22056-167">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="22056-167">Response example</span></span>

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
