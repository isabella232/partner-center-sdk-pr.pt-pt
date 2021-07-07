---
title: Criar contas de utilizador para um cliente
description: Crie uma nova conta de utilizador para o seu cliente.
ms.date: 05/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: d086d7ba72c9d9e42dc88684ddeafc9a597bfd7c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973388"
---
# <a name="create-user-accounts-for-a-customer"></a><span data-ttu-id="80a65-103">Criar contas de utilizador para um cliente</span><span class="sxs-lookup"><span data-stu-id="80a65-103">Create user accounts for a customer</span></span>

<span data-ttu-id="80a65-104">Crie uma nova conta de utilizador para o seu cliente.</span><span class="sxs-lookup"><span data-stu-id="80a65-104">Create a new user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="80a65-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="80a65-105">Prerequisites</span></span>

- <span data-ttu-id="80a65-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="80a65-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="80a65-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="80a65-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="80a65-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="80a65-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="80a65-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="80a65-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="80a65-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="80a65-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="80a65-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="80a65-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="80a65-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="80a65-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="80a65-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="80a65-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="80a65-114">C\#</span><span class="sxs-lookup"><span data-stu-id="80a65-114">C\#</span></span>

<span data-ttu-id="80a65-115">Para obter uma nova conta de utilizador para um cliente:</span><span class="sxs-lookup"><span data-stu-id="80a65-115">To obtain a new user account for a customer:</span></span>

1. <span data-ttu-id="80a65-116">Crie um novo objeto **CustomerUser** com as informações relevantes do utilizador.</span><span class="sxs-lookup"><span data-stu-id="80a65-116">Create a new **CustomerUser** object with the relevant user information.</span></span>

2. <span data-ttu-id="80a65-117">Utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="80a65-117">Use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span>

3. <span data-ttu-id="80a65-118">Ligue para a propriedade **dos Utilizadores,** seguido do método **Criar.**</span><span class="sxs-lookup"><span data-stu-id="80a65-118">Call the **Users** property, followed by the **Create** method.</span></span>

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

<span data-ttu-id="80a65-119">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="80a65-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="80a65-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserCreate.cs</span><span class="sxs-lookup"><span data-stu-id="80a65-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserCreate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="80a65-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="80a65-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="80a65-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="80a65-122">Request syntax</span></span>

| <span data-ttu-id="80a65-123">Método</span><span class="sxs-lookup"><span data-stu-id="80a65-123">Method</span></span>   | <span data-ttu-id="80a65-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="80a65-124">Request URI</span></span>                                                                                  |
|----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="80a65-125">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="80a65-125">**POST**</span></span> | <span data-ttu-id="80a65-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/utilizadores HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="80a65-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="80a65-127">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="80a65-127">URI parameters</span></span>

<span data-ttu-id="80a65-128">Utilize os seguintes parâmetros de consulta para identificar o cliente correto.</span><span class="sxs-lookup"><span data-stu-id="80a65-128">Use the following query parameters to identify the correct customer.</span></span>

| <span data-ttu-id="80a65-129">Nome</span><span class="sxs-lookup"><span data-stu-id="80a65-129">Name</span></span> | <span data-ttu-id="80a65-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="80a65-130">Type</span></span> | <span data-ttu-id="80a65-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="80a65-131">Required</span></span> | <span data-ttu-id="80a65-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="80a65-132">Description</span></span> |
|----- |----- | -------- |------------ |
| <span data-ttu-id="80a65-133">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="80a65-133">**customer-tenant-id**</span></span> | <span data-ttu-id="80a65-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="80a65-134">**guid**</span></span> | <span data-ttu-id="80a65-135">Y</span><span class="sxs-lookup"><span data-stu-id="80a65-135">Y</span></span> | <span data-ttu-id="80a65-136">O valor é um **design de cliente-inquilino-inquilino-inquilino formatado** guid. Permite ao revendedor filtrar os resultados de um determinado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="80a65-136">The value is a GUID formatted **customer-tenant-id**. It allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="80a65-137">**id utilizador**</span><span class="sxs-lookup"><span data-stu-id="80a65-137">**user-id**</span></span> | <span data-ttu-id="80a65-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="80a65-138">**guid**</span></span> | <span data-ttu-id="80a65-139">N</span><span class="sxs-lookup"><span data-stu-id="80a65-139">N</span></span> | <span data-ttu-id="80a65-140">O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="80a65-140">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="80a65-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="80a65-141">Request headers</span></span>

<span data-ttu-id="80a65-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="80a65-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="80a65-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="80a65-143">Request body</span></span>

<span data-ttu-id="80a65-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="80a65-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="80a65-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="80a65-145">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="80a65-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="80a65-146">REST response</span></span>

<span data-ttu-id="80a65-147">Se for bem sucedido, este método devolve uma conta de utilizador, incluindo o GUID.</span><span class="sxs-lookup"><span data-stu-id="80a65-147">If successful, this method returns a user account, including the GUID.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="80a65-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="80a65-148">Response success and error codes</span></span>

<span data-ttu-id="80a65-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="80a65-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="80a65-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="80a65-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="80a65-151">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="80a65-151">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="80a65-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="80a65-152">Response example</span></span>

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