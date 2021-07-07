---
title: Atualizar as contas de utilizador para um cliente
description: Atualizar detalhes numa conta de utilizador existente para o seu cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6ebfdbb5df1d56416835af771fd6b70190776012
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445277"
---
# <a name="update-user-accounts-for-a-customer"></a><span data-ttu-id="6b776-103">Atualizar as contas de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="6b776-103">Update user accounts for a customer</span></span>

<span data-ttu-id="6b776-104">Atualizar detalhes numa conta de utilizador existente para o seu cliente.</span><span class="sxs-lookup"><span data-stu-id="6b776-104">Update details in an existing user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b776-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6b776-105">Prerequisites</span></span>

- <span data-ttu-id="6b776-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6b776-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6b776-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="6b776-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="6b776-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6b776-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6b776-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="6b776-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6b776-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="6b776-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6b776-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="6b776-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6b776-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="6b776-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6b776-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6b776-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="6b776-114">C\#</span><span class="sxs-lookup"><span data-stu-id="6b776-114">C\#</span></span>

<span data-ttu-id="6b776-115">Para atualizar os detalhes de um utilizador específico do cliente, recupere primeiro o ID do cliente especificado e o utilizador para atualizar.</span><span class="sxs-lookup"><span data-stu-id="6b776-115">To update the details for a specified customer user, first retrieve the specified customer ID and user to update.</span></span> <span data-ttu-id="6b776-116">Em seguida, crie uma versão atualizada do utilizador num novo objeto **CustomerUser.**</span><span class="sxs-lookup"><span data-stu-id="6b776-116">Then, create an updated version of the user in a new **CustomerUser** object.</span></span> <span data-ttu-id="6b776-117">Em seguida, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="6b776-117">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="6b776-118">Em seguida, ligue para a propriedade **do Utilizadores,** o método **ById(),** seguido do método **Patch().**</span><span class="sxs-lookup"><span data-stu-id="6b776-118">Then call the **Users** property, the **ById()** method, followed by the **Patch()** method.</span></span>

``` csharp
// string selectedCustomerId;
// customerUser specifiedUser;
// IAggregatePartner partnerOperations;

// Updated information
var userToUpdate = new CustomerUser()
{
    PasswordProfile = new PasswordProfile() { ForceChangePassword = true, Password = "testPw@!122B" },
    DisplayName = "DisplayNameChange",
    FirstName = "FirstNameChange",
    LastName = "LastNameChange",
    UsageLocation = "US",
    UserPrincipalName = Guid.NewGuid().ToString("N") + "@" + selectedCustomer.CompanyProfile.Domain.ToString()
};

// Update customer user information
User updatedCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(specifiedUser.Id).Patch(userToUpdate);

```

<span data-ttu-id="6b776-119">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="6b776-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="6b776-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs</span><span class="sxs-lookup"><span data-stu-id="6b776-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="6b776-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6b776-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6b776-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b776-122">Request syntax</span></span>

| <span data-ttu-id="6b776-123">Método</span><span class="sxs-lookup"><span data-stu-id="6b776-123">Method</span></span>    | <span data-ttu-id="6b776-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6b776-124">Request URI</span></span>                                                                                  |
|-----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="6b776-125">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="6b776-125">**PATCH**</span></span> | <span data-ttu-id="6b776-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/utilizadores HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6b776-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="6b776-127">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="6b776-127">URI parameter</span></span>

<span data-ttu-id="6b776-128">Utilize o seguinte parâmetro de consulta para identificar o cliente correto.</span><span class="sxs-lookup"><span data-stu-id="6b776-128">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="6b776-129">Nome</span><span class="sxs-lookup"><span data-stu-id="6b776-129">Name</span></span>                   | <span data-ttu-id="6b776-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="6b776-130">Type</span></span>     | <span data-ttu-id="6b776-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="6b776-131">Required</span></span> | <span data-ttu-id="6b776-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b776-132">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6b776-133">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="6b776-133">**customer-tenant-id**</span></span> | <span data-ttu-id="6b776-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="6b776-134">**guid**</span></span> | <span data-ttu-id="6b776-135">Y</span><span class="sxs-lookup"><span data-stu-id="6b776-135">Y</span></span>        | <span data-ttu-id="6b776-136">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="6b776-136">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="6b776-137">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="6b776-137">**user-id**</span></span>            | <span data-ttu-id="6b776-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="6b776-138">**guid**</span></span> | <span data-ttu-id="6b776-139">Y</span><span class="sxs-lookup"><span data-stu-id="6b776-139">Y</span></span>        | <span data-ttu-id="6b776-140">O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="6b776-140">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="6b776-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6b776-141">Request headers</span></span>

<span data-ttu-id="6b776-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6b776-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6b776-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6b776-143">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="6b776-144">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6b776-144">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
{
      "usageLocation": "new country/region code",

      "attributes": {
        "objectType": "CustomerUser"
      }
}
```

## <a name="rest-response"></a><span data-ttu-id="6b776-145">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6b776-145">REST response</span></span>

<span data-ttu-id="6b776-146">Se for bem sucedido, este método devolve uma conta de utilizador com as informações atualizadas.</span><span class="sxs-lookup"><span data-stu-id="6b776-146">If successful, this method returns a user account with the updated information.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6b776-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6b776-147">Response success and error codes</span></span>

<span data-ttu-id="6b776-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6b776-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6b776-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6b776-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6b776-150">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6b776-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6b776-151">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6b776-151">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST
{
  "usageLocation": "new country/region code",
  "id": "4b10bf41-ab11-40e3-8c53-cd67849b50de",
  "userPrincipalName": "emailidchange@abcdefgh1234.ccsctp.net",
  "firstName": "FirstNameChange",
  "lastName": "LastNameChange",
  "displayName": "DisplayNameChange",
  "userDomainType": "none",
  "state": "active",
  "links": {
    "self": {
      "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/users/4b10bf41-ab11-40e3-8c53-cd67849b50de",
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
