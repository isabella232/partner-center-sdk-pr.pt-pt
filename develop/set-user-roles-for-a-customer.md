---
title: Definir funções de utilizador para um cliente
description: Dentro de uma conta de cliente, há um conjunto de funções de diretório. Pode atribuir contas de utilizador a essas funções.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a035d711ffa91200fa7b479ed5ec53929aa4feaf
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446705"
---
# <a name="set-user-roles-for-a-customer"></a><span data-ttu-id="94976-104">Definir funções de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="94976-104">Set user roles for a customer</span></span>

<span data-ttu-id="94976-105">Dentro de uma conta de cliente, há um conjunto de funções de diretório.</span><span class="sxs-lookup"><span data-stu-id="94976-105">Within a customer account, there's a set of directory roles.</span></span> <span data-ttu-id="94976-106">Pode atribuir contas de utilizador a essas funções.</span><span class="sxs-lookup"><span data-stu-id="94976-106">You can assign user accounts to those roles.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94976-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="94976-107">Prerequisites</span></span>

- <span data-ttu-id="94976-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="94976-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="94976-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="94976-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="94976-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="94976-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="94976-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="94976-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="94976-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="94976-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="94976-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="94976-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="94976-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="94976-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="94976-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="94976-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="94976-116">C\#</span><span class="sxs-lookup"><span data-stu-id="94976-116">C\#</span></span>

<span data-ttu-id="94976-117">Para atribuir uma função de diretório a um utilizador do cliente, crie um novo [**UserMember**](/dotnet/api/microsoft.store.partnercenter.models.roles.usermember) com os detalhes relevantes do utilizador.</span><span class="sxs-lookup"><span data-stu-id="94976-117">To assign a directory role to a customer user, create a new [**UserMember**](/dotnet/api/microsoft.store.partnercenter.models.roles.usermember) with the relevant user details.</span></span> <span data-ttu-id="94976-118">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente especificado para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="94976-118">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer ID to identify the customer.</span></span> <span data-ttu-id="94976-119">A partir daí, utilize o método [**Diretório.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) com o ID de papel de diretório para especificar a função.</span><span class="sxs-lookup"><span data-stu-id="94976-119">From there, use the [**DirectoryRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) method with the directory role ID to specify the role.</span></span> <span data-ttu-id="94976-120">Em seguida, aceda à coleção **UserMembers** e use o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.create) para adicionar o novo membro do utilizador à recolha de membros do utilizador atribuídos a essa função.</span><span class="sxs-lookup"><span data-stu-id="94976-120">Then, access the **UserMembers** collection, and use the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.create) method to add the new user member to the collection of user members assigned to that role.</span></span>

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

<span data-ttu-id="94976-121">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="94976-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="94976-122">**Project**: Partner Center SDK Samples **Class**: AddUserMemberToDirectoryRole.cs</span><span class="sxs-lookup"><span data-stu-id="94976-122">**Project**: Partner Center SDK Samples **Class**: AddUserMemberToDirectoryRole.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="94976-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="94976-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="94976-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="94976-124">Request syntax</span></span>

| <span data-ttu-id="94976-125">Método</span><span class="sxs-lookup"><span data-stu-id="94976-125">Method</span></span>   | <span data-ttu-id="94976-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="94976-126">Request URI</span></span>                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="94976-127">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="94976-127">**POST**</span></span> | <span data-ttu-id="94976-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directyroles/{role-ID}/usermembers HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="94976-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="94976-129">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="94976-129">URI parameter</span></span>

<span data-ttu-id="94976-130">Utilize os seguintes parâmetros URI para identificar o cliente e a função corretos.</span><span class="sxs-lookup"><span data-stu-id="94976-130">Use the following URI parameters to identify the correct customer and role.</span></span> <span data-ttu-id="94976-131">Para identificar o utilizador a quem atribuir a função, forneça a informação de identificação no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="94976-131">To identify the user to whom to assign the role, supply the identifying information in the request body.</span></span>

| <span data-ttu-id="94976-132">Nome</span><span class="sxs-lookup"><span data-stu-id="94976-132">Name</span></span>                   | <span data-ttu-id="94976-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="94976-133">Type</span></span>     | <span data-ttu-id="94976-134">Necessário</span><span class="sxs-lookup"><span data-stu-id="94976-134">Required</span></span> | <span data-ttu-id="94976-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="94976-135">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="94976-136">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="94976-136">**customer-tenant-id**</span></span> | <span data-ttu-id="94976-137">**guid**</span><span class="sxs-lookup"><span data-stu-id="94976-137">**guid**</span></span> | <span data-ttu-id="94976-138">Y</span><span class="sxs-lookup"><span data-stu-id="94976-138">Y</span></span>        | <span data-ttu-id="94976-139">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="94976-139">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="94976-140">**id role**</span><span class="sxs-lookup"><span data-stu-id="94976-140">**role-id**</span></span>            | <span data-ttu-id="94976-141">**guid**</span><span class="sxs-lookup"><span data-stu-id="94976-141">**guid**</span></span> | <span data-ttu-id="94976-142">Y</span><span class="sxs-lookup"><span data-stu-id="94976-142">Y</span></span>        | <span data-ttu-id="94976-143">O valor é um **id de função** formatado GUID que identifica a função a atribuir ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="94976-143">The value is a GUID formatted **role-id** that identifies the role to assign to the user.</span></span>                                                              |

### <a name="request-headers"></a><span data-ttu-id="94976-144">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="94976-144">Request headers</span></span>

<span data-ttu-id="94976-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="94976-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="94976-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="94976-146">Request body</span></span>

<span data-ttu-id="94976-147">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="94976-147">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="94976-148">Nome</span><span class="sxs-lookup"><span data-stu-id="94976-148">Name</span></span>                  | <span data-ttu-id="94976-149">Tipo</span><span class="sxs-lookup"><span data-stu-id="94976-149">Type</span></span>       | <span data-ttu-id="94976-150">Necessário</span><span class="sxs-lookup"><span data-stu-id="94976-150">Required</span></span> | <span data-ttu-id="94976-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="94976-151">Description</span></span>                            |
|-----------------------|------------|----------|----------------------------------------|
| <span data-ttu-id="94976-152">**ID**</span><span class="sxs-lookup"><span data-stu-id="94976-152">**Id**</span></span>                | <span data-ttu-id="94976-153">**string**</span><span class="sxs-lookup"><span data-stu-id="94976-153">**string**</span></span> | <span data-ttu-id="94976-154">Y</span><span class="sxs-lookup"><span data-stu-id="94976-154">Y</span></span>        | <span data-ttu-id="94976-155">O ID do utilizador para adicionar ao papel.</span><span class="sxs-lookup"><span data-stu-id="94976-155">The ID of the user to add to the role.</span></span> |
| <span data-ttu-id="94976-156">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="94976-156">**DisplayName**</span></span>       | <span data-ttu-id="94976-157">**string**</span><span class="sxs-lookup"><span data-stu-id="94976-157">**string**</span></span> | <span data-ttu-id="94976-158">Y</span><span class="sxs-lookup"><span data-stu-id="94976-158">Y</span></span>        | <span data-ttu-id="94976-159">O nome de exibição amigável do utilizador.</span><span class="sxs-lookup"><span data-stu-id="94976-159">The friendly display name of the user.</span></span> |
| <span data-ttu-id="94976-160">**Nome do UtilizadorPrincipal**</span><span class="sxs-lookup"><span data-stu-id="94976-160">**UserPrincipalName**</span></span> | <span data-ttu-id="94976-161">**string**</span><span class="sxs-lookup"><span data-stu-id="94976-161">**string**</span></span> | <span data-ttu-id="94976-162">Y</span><span class="sxs-lookup"><span data-stu-id="94976-162">Y</span></span>        | <span data-ttu-id="94976-163">O nome do diretor do utilizador.</span><span class="sxs-lookup"><span data-stu-id="94976-163">The name of the user principal.</span></span>        |
| <span data-ttu-id="94976-164">**Atributos**</span><span class="sxs-lookup"><span data-stu-id="94976-164">**Attributes**</span></span>        | <span data-ttu-id="94976-165">**objeto**</span><span class="sxs-lookup"><span data-stu-id="94976-165">**object**</span></span> | <span data-ttu-id="94976-166">Y</span><span class="sxs-lookup"><span data-stu-id="94976-166">Y</span></span>        | <span data-ttu-id="94976-167">Contém "ObjectType":"UserMember"</span><span class="sxs-lookup"><span data-stu-id="94976-167">Contains "ObjectType":"UserMember"</span></span>     |

### <a name="request-example"></a><span data-ttu-id="94976-168">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="94976-168">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="94976-169">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="94976-169">REST response</span></span>

<span data-ttu-id="94976-170">Este método devolve a conta do utilizador com o ID de função anexado quando o utilizador é atribuído com sucesso a função.</span><span class="sxs-lookup"><span data-stu-id="94976-170">This method returns the user account with the role ID attached when the user is successfully assigned the role.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="94976-171">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="94976-171">Response success and error codes</span></span>

<span data-ttu-id="94976-172">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="94976-172">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="94976-173">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="94976-173">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="94976-174">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="94976-174">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="94976-175">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="94976-175">Response example</span></span>

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
