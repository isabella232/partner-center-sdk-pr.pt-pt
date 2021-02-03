---
title: Definir funções de utilizador para um cliente
description: Dentro de uma conta de cliente, há um conjunto de funções de diretório. Pode atribuir contas de utilizador a essas funções.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f42120e40e54ff8bd6242634d97268091abf8e1c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769590"
---
# <a name="set-user-roles-for-a-customer"></a><span data-ttu-id="1fd4d-104">Definir funções de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="1fd4d-104">Set user roles for a customer</span></span>

<span data-ttu-id="1fd4d-105">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-105">**Applies To**</span></span>

- <span data-ttu-id="1fd4d-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="1fd4d-106">Partner Center</span></span>

<span data-ttu-id="1fd4d-107">Dentro de uma conta de cliente, há um conjunto de funções de diretório.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-107">Within a customer account, there's a set of directory roles.</span></span> <span data-ttu-id="1fd4d-108">Pode atribuir contas de utilizador a essas funções.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-108">You can assign user accounts to those roles.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1fd4d-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1fd4d-109">Prerequisites</span></span>

- <span data-ttu-id="1fd4d-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1fd4d-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1fd4d-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="1fd4d-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1fd4d-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="1fd4d-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="1fd4d-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="1fd4d-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="1fd4d-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="1fd4d-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1fd4d-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="1fd4d-118">C\#</span><span class="sxs-lookup"><span data-stu-id="1fd4d-118">C\#</span></span>

<span data-ttu-id="1fd4d-119">Para atribuir uma função de diretório a um utilizador do cliente, crie um novo [**UserMember**](/dotnet/api/microsoft.store.partnercenter.models.roles.usermember) com os detalhes relevantes do utilizador.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-119">To assign a directory role to a customer user, create a new [**UserMember**](/dotnet/api/microsoft.store.partnercenter.models.roles.usermember) with the relevant user details.</span></span> <span data-ttu-id="1fd4d-120">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente especificado para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-120">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer ID to identify the customer.</span></span> <span data-ttu-id="1fd4d-121">A partir daí, utilize o método [**Diretório.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) com o ID de papel de diretório para especificar a função.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-121">From there, use the [**DirectoryRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) method with the directory role ID to specify the role.</span></span> <span data-ttu-id="1fd4d-122">Em seguida, aceda à coleção **UserMembers** e use o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.create) para adicionar o novo membro do utilizador à recolha de membros do utilizador atribuídos a essa função.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-122">Then, access the **UserMembers** collection, and use the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.create) method to add the new user member to the collection of user members assigned to that role.</span></span>

``` csharp
// UserMember createdUser;
// IAggregatePartner partnerOperations;
// Customer selectedCustomer;
// IDirectoryRole selectedRole;

// Create the new user member.
UserMember userMemberToAdd = new UserMember()
{
    UserPrincipalName = createdUser.UserPrincipalName,
    DisplayName = createdUser.DisplayName,
    Id = createdUser.Id
};

// Add the new user member to the role.
var userMemberAdded = partnerOperations.Customers.ById(selectedCustomer.Id).DirectoryRoles.ById(selectedRole.Id).UserMembers.Create(userMemberToAdd);
```

<span data-ttu-id="1fd4d-123">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="1fd4d-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="1fd4d-124">**Projeto**: Partner Center SDK Samples **Class**: AddUserMemberToDirectoryRole.cs</span><span class="sxs-lookup"><span data-stu-id="1fd4d-124">**Project**: Partner Center SDK Samples **Class**: AddUserMemberToDirectoryRole.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="1fd4d-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="1fd4d-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1fd4d-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="1fd4d-126">Request syntax</span></span>

| <span data-ttu-id="1fd4d-127">Método</span><span class="sxs-lookup"><span data-stu-id="1fd4d-127">Method</span></span>   | <span data-ttu-id="1fd4d-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="1fd4d-128">Request URI</span></span>                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1fd4d-129">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-129">**POST**</span></span> | <span data-ttu-id="1fd4d-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directyroles/{role-ID}/usermembers HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1fd4d-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="1fd4d-131">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="1fd4d-131">URI parameter</span></span>

<span data-ttu-id="1fd4d-132">Utilize os seguintes parâmetros URI para identificar o cliente e a função corretos.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-132">Use the following URI parameters to identify the correct customer and role.</span></span> <span data-ttu-id="1fd4d-133">Para identificar o utilizador a quem atribuir a função, forneça a informação de identificação no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-133">To identify the user to whom to assign the role, supply the identifying information in the request body.</span></span>

| <span data-ttu-id="1fd4d-134">Nome</span><span class="sxs-lookup"><span data-stu-id="1fd4d-134">Name</span></span>                   | <span data-ttu-id="1fd4d-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="1fd4d-135">Type</span></span>     | <span data-ttu-id="1fd4d-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="1fd4d-136">Required</span></span> | <span data-ttu-id="1fd4d-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="1fd4d-137">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1fd4d-138">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-138">**customer-tenant-id**</span></span> | <span data-ttu-id="1fd4d-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-139">**guid**</span></span> | <span data-ttu-id="1fd4d-140">Y</span><span class="sxs-lookup"><span data-stu-id="1fd4d-140">Y</span></span>        | <span data-ttu-id="1fd4d-141">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-141">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="1fd4d-142">**id role**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-142">**role-id**</span></span>            | <span data-ttu-id="1fd4d-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-143">**guid**</span></span> | <span data-ttu-id="1fd4d-144">Y</span><span class="sxs-lookup"><span data-stu-id="1fd4d-144">Y</span></span>        | <span data-ttu-id="1fd4d-145">O valor é um **id de função** formatado GUID que identifica a função a atribuir ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-145">The value is a GUID formatted **role-id** that identifies the role to assign to the user.</span></span>                                                              |

### <a name="request-headers"></a><span data-ttu-id="1fd4d-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="1fd4d-146">Request headers</span></span>

<span data-ttu-id="1fd4d-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1fd4d-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1fd4d-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="1fd4d-148">Request body</span></span>

<span data-ttu-id="1fd4d-149">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-149">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="1fd4d-150">Nome</span><span class="sxs-lookup"><span data-stu-id="1fd4d-150">Name</span></span>                  | <span data-ttu-id="1fd4d-151">Tipo</span><span class="sxs-lookup"><span data-stu-id="1fd4d-151">Type</span></span>       | <span data-ttu-id="1fd4d-152">Necessário</span><span class="sxs-lookup"><span data-stu-id="1fd4d-152">Required</span></span> | <span data-ttu-id="1fd4d-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="1fd4d-153">Description</span></span>                            |
|-----------------------|------------|----------|----------------------------------------|
| <span data-ttu-id="1fd4d-154">**ID**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-154">**Id**</span></span>                | <span data-ttu-id="1fd4d-155">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-155">**string**</span></span> | <span data-ttu-id="1fd4d-156">Y</span><span class="sxs-lookup"><span data-stu-id="1fd4d-156">Y</span></span>        | <span data-ttu-id="1fd4d-157">O ID do utilizador para adicionar ao papel.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-157">The Id of the user to add to the role.</span></span> |
| <span data-ttu-id="1fd4d-158">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-158">**DisplayName**</span></span>       | <span data-ttu-id="1fd4d-159">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-159">**string**</span></span> | <span data-ttu-id="1fd4d-160">Y</span><span class="sxs-lookup"><span data-stu-id="1fd4d-160">Y</span></span>        | <span data-ttu-id="1fd4d-161">O nome de exibição amigável do utilizador.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-161">The friendly display name of the user.</span></span> |
| <span data-ttu-id="1fd4d-162">**Nome do UtilizadorPrincipal**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-162">**UserPrincipalName**</span></span> | <span data-ttu-id="1fd4d-163">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-163">**string**</span></span> | <span data-ttu-id="1fd4d-164">Y</span><span class="sxs-lookup"><span data-stu-id="1fd4d-164">Y</span></span>        | <span data-ttu-id="1fd4d-165">O nome do diretor do utilizador.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-165">The name of the user principal.</span></span>        |
| <span data-ttu-id="1fd4d-166">**Atributos**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-166">**Attributes**</span></span>        | <span data-ttu-id="1fd4d-167">**objeto**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-167">**object**</span></span> | <span data-ttu-id="1fd4d-168">Y</span><span class="sxs-lookup"><span data-stu-id="1fd4d-168">Y</span></span>        | <span data-ttu-id="1fd4d-169">Contém "ObjectType":"UserMember"</span><span class="sxs-lookup"><span data-stu-id="1fd4d-169">Contains "ObjectType":"UserMember"</span></span>     |

### <a name="request-example"></a><span data-ttu-id="1fd4d-170">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="1fd4d-170">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/directoryroles/f023fd81-a637-4b56-95fd-791ac0226033/usermembers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a56cb2e5-a156-4f68-9155-57ffe2b93d18
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 180
Expect: 100-continue

{
    "Id": "a9ef48bb-8758-4590-a312-d4a47bfaded4",
    "DisplayName": "Daniel Tsai",
    "UserPrincipalName": "Daniel@dtdemocspcustomer005.onmicrosoft.com",
    "Attributes": {
        "ObjectType": "UserMember"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="1fd4d-171">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="1fd4d-171">REST response</span></span>

<span data-ttu-id="1fd4d-172">Este método devolve a conta do utilizador com a identificação de função anexada quando o utilizador é atribuído com sucesso a função.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-172">This method returns the user account with the role id attached when the user is successfully assigned the role.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1fd4d-173">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="1fd4d-173">Response success and error codes</span></span>

<span data-ttu-id="1fd4d-174">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-174">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1fd4d-175">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-175">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1fd4d-176">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="1fd4d-176">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1fd4d-177">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="1fd4d-177">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 231
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
MS-RequestId: a56cb2e5-a156-4f68-9155-57ffe2b93d18
MS-CV: aia94+gnrEeQqkGr.0
MS-ServerId: 101112202
Date: Tue, 20 Dec 2016 23:36:55 GMT

{
    "displayName": "Daniel Tsai",
    "userPrincipalName": "Daniel@dtdemocspcustomer005.onmicrosoft.com",
    "roleId": "f023fd81-a637-4b56-95fd-791ac0226033",
    "id": "a9ef48bb-8758-4590-a312-d4a47bfaded4",
    "attributes": {
        "objectType": "UserMember"
    }
}
```
