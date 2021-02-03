---
title: Remover um utilizador cliente de uma função
description: Como remover um utilizador de uma função de diretório dentro de uma conta de cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6253e86f3733bbf2b9c593c5ca3f3e2fccce7c2c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769649"
---
# <a name="remove-a-customer-user-from-a-role"></a><span data-ttu-id="642a4-103">Remover um utilizador cliente de uma função</span><span class="sxs-lookup"><span data-stu-id="642a4-103">Remove a customer user from a role</span></span>

<span data-ttu-id="642a4-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="642a4-104">**Applies To**</span></span>

- <span data-ttu-id="642a4-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="642a4-105">Partner Center</span></span>

<span data-ttu-id="642a4-106">Como remover um utilizador de uma função de diretório dentro de uma conta de cliente.</span><span class="sxs-lookup"><span data-stu-id="642a4-106">How to remove a user from a directory role within a customer account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="642a4-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="642a4-107">Prerequisites</span></span>

- <span data-ttu-id="642a4-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="642a4-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="642a4-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="642a4-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="642a4-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="642a4-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="642a4-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="642a4-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="642a4-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="642a4-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="642a4-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="642a4-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="642a4-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="642a4-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="642a4-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="642a4-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="642a4-116">C\#</span><span class="sxs-lookup"><span data-stu-id="642a4-116">C\#</span></span>

<span data-ttu-id="642a4-117">Para remover um utilizador de uma função de diretório, selecione o cliente com o utilizador para modificar com uma chamada para o método [**IAggregatePartner.Customers.ById,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) a partir daí, especificar a função utilizando o método [**DirectórioRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) com o ID de papel de diretório.</span><span class="sxs-lookup"><span data-stu-id="642a4-117">To remove a user from a directory role, select the customer with the user to modify with a call to the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method, From there, specify the role using the [**DirectoryRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) method with the directory role ID.</span></span> <span data-ttu-id="642a4-118">Em seguida, aceda ao método [**UserMembers.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.byid) para identificar o utilizador a remover, e o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermember.delete) para remover o utilizador da função.</span><span class="sxs-lookup"><span data-stu-id="642a4-118">Then, access the [**UserMembers.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.byid) method to identify the user to remove, and the [**Delete**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermember.delete) method to remove the user from the role.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedRoleId;
// string selectedUserMemberId;

partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedRoleId).UserMembers.ById(selectedUserMemberId).Delete();
```

<span data-ttu-id="642a4-119">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="642a4-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="642a4-120">**Projeto**: Partner Center SDK Samples **Class**: RemoveCustomerUserMemberFromDirectoryRole.cs</span><span class="sxs-lookup"><span data-stu-id="642a4-120">**Project**: Partner Center SDK Samples **Class**: RemoveCustomerUserMemberFromDirectoryRole.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="642a4-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="642a4-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="642a4-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="642a4-122">Request syntax</span></span>

| <span data-ttu-id="642a4-123">Método</span><span class="sxs-lookup"><span data-stu-id="642a4-123">Method</span></span>     | <span data-ttu-id="642a4-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="642a4-124">Request URI</span></span>                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="642a4-125">**EXCLUIR**</span><span class="sxs-lookup"><span data-stu-id="642a4-125">**DELETE**</span></span> | <span data-ttu-id="642a4-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directyroles/{role-ID}/usermembers/{user-ID} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="642a4-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers/{user-ID} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="642a4-127">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="642a4-127">URI parameter</span></span>

<span data-ttu-id="642a4-128">Utilize os seguintes parâmetros URI para identificar o cliente, função e utilizador corretos.</span><span class="sxs-lookup"><span data-stu-id="642a4-128">Use the following URI parameters to identify the correct customer, role and user.</span></span>

| <span data-ttu-id="642a4-129">Nome</span><span class="sxs-lookup"><span data-stu-id="642a4-129">Name</span></span>                   | <span data-ttu-id="642a4-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="642a4-130">Type</span></span>     | <span data-ttu-id="642a4-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="642a4-131">Required</span></span> | <span data-ttu-id="642a4-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="642a4-132">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="642a4-133">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="642a4-133">**customer-tenant-id**</span></span> | <span data-ttu-id="642a4-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="642a4-134">**guid**</span></span> | <span data-ttu-id="642a4-135">Y</span><span class="sxs-lookup"><span data-stu-id="642a4-135">Y</span></span>        | <span data-ttu-id="642a4-136">O valor é um **design de cliente-inquilino-inquilino** formatado guid que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="642a4-136">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |
| <span data-ttu-id="642a4-137">**id role**</span><span class="sxs-lookup"><span data-stu-id="642a4-137">**role-id**</span></span>            | <span data-ttu-id="642a4-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="642a4-138">**guid**</span></span> | <span data-ttu-id="642a4-139">Y</span><span class="sxs-lookup"><span data-stu-id="642a4-139">Y</span></span>        | <span data-ttu-id="642a4-140">O valor é um **id de função** formatado GUID que identifica o papel.</span><span class="sxs-lookup"><span data-stu-id="642a4-140">The value is a GUID formatted **role-id** that identifies the role.</span></span>                |
| <span data-ttu-id="642a4-141">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="642a4-141">**user-id**</span></span>            | <span data-ttu-id="642a4-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="642a4-142">**guid**</span></span> | <span data-ttu-id="642a4-143">Y</span><span class="sxs-lookup"><span data-stu-id="642a4-143">Y</span></span>        | <span data-ttu-id="642a4-144">O valor é um **id de utilizador** formatado GUID que identifica uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="642a4-144">The value is a GUID formatted **user-id** that identifies a single user account.</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="642a4-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="642a4-145">Request headers</span></span>

<span data-ttu-id="642a4-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="642a4-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="642a4-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="642a4-147">Request body</span></span>

<span data-ttu-id="642a4-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="642a4-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="642a4-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="642a4-149">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04%20/directoryroles/729827e3-9c14-49f7-bb1b-9608f156bbb8/usermembers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04%20 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0a00ec08-6273-46bb-ab6f-14a13959b381
MS-CorrelationId: 87d18a45-81fc-40cf-921a-b91cb82d67fe
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 0
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="642a4-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="642a4-150">REST response</span></span>

<span data-ttu-id="642a4-151">Se o utilizador for removido da função com sucesso, o corpo de resposta está vazio.</span><span class="sxs-lookup"><span data-stu-id="642a4-151">If the user is removed from the role successfully, the response body is empty.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="642a4-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="642a4-152">Response success and error codes</span></span>

<span data-ttu-id="642a4-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="642a4-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="642a4-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="642a4-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="642a4-155">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="642a4-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="642a4-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="642a4-156">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
MS-RequestId: e784d7aa-8c8d-45ee-8f97-9e09823d7338
MS-CV: es01VX8do0u2aTXw.0
MS-ServerId: 101112616
Date: Tue, 20 Dec 2016 23:16:35 GMT
```
