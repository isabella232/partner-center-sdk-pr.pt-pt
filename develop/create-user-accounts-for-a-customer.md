---
title: Criar contas de utilizador para um cliente
description: Crie uma nova conta de utilizador para o seu cliente.
ms.date: 05/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 9131a1c4c37d07b1994b67379ec8361fda13a371
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768809"
---
# <a name="create-user-accounts-for-a-customer"></a><span data-ttu-id="22a2e-103">Criar contas de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="22a2e-103">Create user accounts for a customer</span></span>

<span data-ttu-id="22a2e-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="22a2e-104">**Applies to:**</span></span>

- <span data-ttu-id="22a2e-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="22a2e-105">Partner Center</span></span>

<span data-ttu-id="22a2e-106">Crie uma nova conta de utilizador para o seu cliente.</span><span class="sxs-lookup"><span data-stu-id="22a2e-106">Create a new user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22a2e-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="22a2e-107">Prerequisites</span></span>

- <span data-ttu-id="22a2e-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="22a2e-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="22a2e-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="22a2e-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="22a2e-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="22a2e-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="22a2e-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="22a2e-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="22a2e-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="22a2e-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="22a2e-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="22a2e-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="22a2e-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="22a2e-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="22a2e-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="22a2e-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="22a2e-116">C\#</span><span class="sxs-lookup"><span data-stu-id="22a2e-116">C\#</span></span>

<span data-ttu-id="22a2e-117">Para obter uma nova conta de utilizador para um cliente:</span><span class="sxs-lookup"><span data-stu-id="22a2e-117">To obtain a new user account for a customer:</span></span>

1. <span data-ttu-id="22a2e-118">Crie um novo objeto **CustomerUser** com as informações relevantes do utilizador.</span><span class="sxs-lookup"><span data-stu-id="22a2e-118">Create a new **CustomerUser** object with the relevant user information.</span></span>

2. <span data-ttu-id="22a2e-119">Utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="22a2e-119">Use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span>

3. <span data-ttu-id="22a2e-120">Ligue para a propriedade **dos Utilizadores,** seguido do método **Criar.**</span><span class="sxs-lookup"><span data-stu-id="22a2e-120">Call the **Users** property, followed by the **Create** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;
// var SelectedCustomer;

var userToCreate = new CustomerUser()
{
    PasswordProfile = new PasswordProfile() { ForceChangePassword = true, Password = "Password!1" },
    DisplayName = "TestDisplayName",
    FirstName = "TestFirstName",
    LastName = "TestLastName",
    UsageLocation = "US",
    UserPrincipalName = Guid.NewGuid().ToString("N") + "@" + selectedCustomer.CompanyProfile.Domain.ToString()
};

User createdUser = partnerOperations.Customers.ById(selectedCustomerId).Users.Create(userToCreate);
```

<span data-ttu-id="22a2e-121">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="22a2e-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="22a2e-122">**Projeto**: PartnerSDK.FeatureSamples **Class**: CustomerUserCreate.cs</span><span class="sxs-lookup"><span data-stu-id="22a2e-122">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserCreate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="22a2e-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="22a2e-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="22a2e-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="22a2e-124">Request syntax</span></span>

| <span data-ttu-id="22a2e-125">Método</span><span class="sxs-lookup"><span data-stu-id="22a2e-125">Method</span></span>   | <span data-ttu-id="22a2e-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="22a2e-126">Request URI</span></span>                                                                                  |
|----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="22a2e-127">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="22a2e-127">**POST**</span></span> | <span data-ttu-id="22a2e-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/utilizadores HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="22a2e-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="22a2e-129">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="22a2e-129">URI parameters</span></span>

<span data-ttu-id="22a2e-130">Utilize os seguintes parâmetros de consulta para identificar o cliente correto.</span><span class="sxs-lookup"><span data-stu-id="22a2e-130">Use the following query parameters to identify the correct customer.</span></span>

| <span data-ttu-id="22a2e-131">Nome</span><span class="sxs-lookup"><span data-stu-id="22a2e-131">Name</span></span> | <span data-ttu-id="22a2e-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="22a2e-132">Type</span></span> | <span data-ttu-id="22a2e-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="22a2e-133">Required</span></span> | <span data-ttu-id="22a2e-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="22a2e-134">Description</span></span> |
|----- |----- | -------- |------------ |
| <span data-ttu-id="22a2e-135">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="22a2e-135">**customer-tenant-id**</span></span> | <span data-ttu-id="22a2e-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="22a2e-136">**guid**</span></span> | <span data-ttu-id="22a2e-137">Y</span><span class="sxs-lookup"><span data-stu-id="22a2e-137">Y</span></span> | <span data-ttu-id="22a2e-138">O valor é um **design de cliente-inquilino formatado** guid. Permite ao revendedor filtrar os resultados de um determinado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="22a2e-138">The value is a GUID formatted **customer-tenant-id**. It allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="22a2e-139">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="22a2e-139">**user-id**</span></span> | <span data-ttu-id="22a2e-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="22a2e-140">**guid**</span></span> | <span data-ttu-id="22a2e-141">N</span><span class="sxs-lookup"><span data-stu-id="22a2e-141">N</span></span> | <span data-ttu-id="22a2e-142">O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="22a2e-142">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="22a2e-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="22a2e-143">Request headers</span></span>

<span data-ttu-id="22a2e-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="22a2e-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="22a2e-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="22a2e-145">Request body</span></span>

<span data-ttu-id="22a2e-146">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="22a2e-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="22a2e-147">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="22a2e-147">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
{
      "usageLocation": "country/region code",
      "userPrincipalName": "userid@domain.onmicrosoft.com",
      "firstName": "First",
      "lastName": "Last",
      "displayName": "User name",
      "immutableId": "Some unique ID",
      "passwordProfile":{
                 password: "abCD123*",
                 forceChangePassword: true
      },
      "attributes": {
        "objectType": "CustomerUser"
      }
}
```

## <a name="rest-response"></a><span data-ttu-id="22a2e-148">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="22a2e-148">REST response</span></span>

<span data-ttu-id="22a2e-149">Se for bem sucedido, este método devolve uma conta de utilizador, incluindo o GUID.</span><span class="sxs-lookup"><span data-stu-id="22a2e-149">If successful, this method returns a user account, including the GUID.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="22a2e-150">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="22a2e-150">Response success and error codes</span></span>

<span data-ttu-id="22a2e-151">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="22a2e-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="22a2e-152">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="22a2e-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="22a2e-153">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="22a2e-153">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="22a2e-154">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="22a2e-154">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST

{
  "usageLocation": "country/region code",
  "id": "4b10bf41-ab11-40e3-8c53-cd67849b50de",
  "userPrincipalName": "userid@domain.onmicrosoft.com",
  "firstName": "First",
  "lastName": "Last",
  "displayName": "User name",
  "immutableId": "Some unique ID",
  "passwordProfile": {
    "forceChangePassword": true,
    "password": "abCD123*"
  },
  "lastDirectorySyncTime": null,
  "userDomainType": "none",
  "state": "active",
  "softDeletionTime": null,
  "attributes": {
    "objectType": "CustomerUser"
  }
}
```