---
title: Repor a palavra-passe de utilizador para um cliente
description: A reposição de uma palavra-passe é muito semelhante à atualização de outros detalhes numa conta de utilizador existente para o seu cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: e0df93c2db55ec0fe49fc0e3089b7e11928f32bb
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768875"
---
# <a name="reset-user-password-for-a-customer"></a><span data-ttu-id="95440-103">Repor a palavra-passe de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="95440-103">Reset user password for a customer</span></span>

<span data-ttu-id="95440-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="95440-104">**Applies To**</span></span>

- <span data-ttu-id="95440-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="95440-105">Partner Center</span></span>

<span data-ttu-id="95440-106">A reposição de uma palavra-passe é muito semelhante à atualização de outros detalhes numa conta de utilizador existente para o seu cliente.</span><span class="sxs-lookup"><span data-stu-id="95440-106">Resetting a password is very similar to updating other details in an existing user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95440-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="95440-107">Prerequisites</span></span>

- <span data-ttu-id="95440-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="95440-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="95440-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="95440-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="95440-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="95440-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="95440-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="95440-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="95440-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="95440-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="95440-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="95440-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="95440-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="95440-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="95440-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="95440-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="95440-116">C\#</span><span class="sxs-lookup"><span data-stu-id="95440-116">C\#</span></span>

<span data-ttu-id="95440-117">Para redefinir uma palavra-passe para um utilizador de cliente especificado, recupere primeiro o ID do cliente especificado e o utilizador-alvo.</span><span class="sxs-lookup"><span data-stu-id="95440-117">To reset a password for a specified customer user, first retrieve the specified customer ID and the targeted user.</span></span> <span data-ttu-id="95440-118">Em seguida, crie um novo objeto **CustomerUser** que contenha a informação para o cliente existente, mas com um novo objeto **PasswordProfile.**</span><span class="sxs-lookup"><span data-stu-id="95440-118">Then, create a new **CustomerUser** object that contains the information for the existing customer, but with a new **PasswordProfile** object.</span></span> <span data-ttu-id="95440-119">Em seguida, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="95440-119">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="95440-120">Em seguida, ligue para a propriedade **do Utilizadores,** o método **ById()** e, em seguida, o método **Patch.**</span><span class="sxs-lookup"><span data-stu-id="95440-120">Then call the **Users** property, the **ById()** method, and then the **Patch** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// CustomerUser specifiedUser;

var selectedCustomer = partnerOperations.Customers.ById(selectedCustomerId).Get();
var userToUpdate = new CustomerUser()
   {
      PasswordProfile = new PasswordProfile() { ForceChangePassword = true, Password = "newPassword" },
      DisplayName = "Roger Federer",
      FirstName = "Roger",
      LastName = "Federer",
      UsageLocation = "US",
      UserPrincipalName = Guid.NewGuid().ToString("N") + "@" + selectedCustomer.CompanyProfile.Domain.ToString()
   };

// update customer user information
User updatedCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(specifiedUser.Id).Patch(userToUpdate);

```

<span data-ttu-id="95440-121">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="95440-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="95440-122">**Projeto**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs</span><span class="sxs-lookup"><span data-stu-id="95440-122">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="95440-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="95440-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="95440-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="95440-124">Request syntax</span></span>

| <span data-ttu-id="95440-125">Método</span><span class="sxs-lookup"><span data-stu-id="95440-125">Method</span></span>    | <span data-ttu-id="95440-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="95440-126">Request URI</span></span>                                                                                  |
|-----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="95440-127">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="95440-127">**PATCH**</span></span> | <span data-ttu-id="95440-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/utilizadores HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="95440-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="95440-129">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="95440-129">URI parameter</span></span>

<span data-ttu-id="95440-130">Utilize o seguinte parâmetro de consulta para identificar o cliente correto.</span><span class="sxs-lookup"><span data-stu-id="95440-130">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="95440-131">Nome</span><span class="sxs-lookup"><span data-stu-id="95440-131">Name</span></span>                   | <span data-ttu-id="95440-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="95440-132">Type</span></span>     | <span data-ttu-id="95440-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="95440-133">Required</span></span> | <span data-ttu-id="95440-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="95440-134">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="95440-135">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="95440-135">**customer-tenant-id**</span></span> | <span data-ttu-id="95440-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="95440-136">**guid**</span></span> | <span data-ttu-id="95440-137">Y</span><span class="sxs-lookup"><span data-stu-id="95440-137">Y</span></span>        | <span data-ttu-id="95440-138">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="95440-138">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="95440-139">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="95440-139">**user-id**</span></span>            | <span data-ttu-id="95440-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="95440-140">**guid**</span></span> | <span data-ttu-id="95440-141">Y</span><span class="sxs-lookup"><span data-stu-id="95440-141">Y</span></span>        | <span data-ttu-id="95440-142">O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="95440-142">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="95440-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="95440-143">Request headers</span></span>

<span data-ttu-id="95440-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="95440-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="95440-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="95440-145">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="95440-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="95440-146">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
{
     "passwordProfile":{
        password: "Renew456*",
        forceChangePassword: true
      },

      "attributes": {
        "objectType": "CustomerUser"
      }
}
```

## <a name="rest-response"></a><span data-ttu-id="95440-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="95440-147">REST response</span></span>

<span data-ttu-id="95440-148">Se for bem sucedido, este método devolve as informações do utilizador, juntamente com as informações atualizadas da palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="95440-148">If successful, this method returns the user information, along with the updated password information.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="95440-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="95440-149">Response success and error codes</span></span>

<span data-ttu-id="95440-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="95440-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="95440-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="95440-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="95440-152">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="95440-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="95440-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="95440-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST
{
  "usageLocation": "AX",
  "id": "95794928-9abe-4548-8b43-50ffc20b9404",
  "userPrincipalName": "aaaa4@abcdefgh1234.ccsctp.net",
  "firstName": "aaaa4",
  "lastName": "aaaa4",
  "displayName": "aaaa4",
  "passwordProfile": {
    "forceChangePassword": false,
    "password": "Renew456*"
  },
  "lastDirectorySyncTime": null,
  "userDomainType": "none",
  "state": "active",
  "softDeletionTime": null,
  "links": {
    "self": {
      "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/users/95794928-9abe-4548-8b43-50ffc20b9404",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "CustomerUser"
  }
}
```
