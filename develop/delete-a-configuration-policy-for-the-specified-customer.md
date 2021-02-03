---
title: Eliminar uma política de configuração para o cliente especificado
description: Como eliminar uma política de configuração para um cliente especificado e identificador de política.
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 586878367fc0873ef0fb1415799b2b7022954053
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769391"
---
# <a name="delete-a-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="595c2-103">Eliminar uma política de configuração para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="595c2-103">Delete a configuration policy for the specified customer</span></span>

<span data-ttu-id="595c2-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="595c2-104">**Applies to:**</span></span>

- <span data-ttu-id="595c2-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="595c2-105">Partner Center</span></span>
- <span data-ttu-id="595c2-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="595c2-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="595c2-107">Como eliminar uma política de configuração para um cliente especificado e identificador de política.</span><span class="sxs-lookup"><span data-stu-id="595c2-107">How to delete a configuration policy for a specified customer and policy identifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="595c2-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="595c2-108">Prerequisites</span></span>

- <span data-ttu-id="595c2-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="595c2-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="595c2-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="595c2-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="595c2-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="595c2-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="595c2-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="595c2-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="595c2-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="595c2-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="595c2-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="595c2-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="595c2-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="595c2-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="595c2-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="595c2-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="595c2-117">O identificador de apólices.</span><span class="sxs-lookup"><span data-stu-id="595c2-117">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="595c2-118">C\#</span><span class="sxs-lookup"><span data-stu-id="595c2-118">C\#</span></span>

<span data-ttu-id="595c2-119">Para eliminar uma política de configuração para um cliente especificado:</span><span class="sxs-lookup"><span data-stu-id="595c2-119">To delete a configuration policy for a specified customer:</span></span>

1. <span data-ttu-id="595c2-120">Ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="595c2-120">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="595c2-121">Ligue para o método [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) com o ID da política para recuperar uma interface para configurar operações de política para a política especificada.</span><span class="sxs-lookup"><span data-stu-id="595c2-121">Call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span>

3. <span data-ttu-id="595c2-122">Ligue para o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.delete) ou [**EliminarAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.deleteasync) para eliminar a política de configuração.</span><span class="sxs-lookup"><span data-stu-id="595c2-122">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.deleteasync) method to delete the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedPolicyId;

partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedPolicyId).Delete();
```

<span data-ttu-id="595c2-123">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="595c2-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="595c2-124">**Projeto**: Partner Center SDK Samples **Class**: DeleteConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="595c2-124">**Project**: Partner Center SDK Samples **Class**: DeleteConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="595c2-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="595c2-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="595c2-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="595c2-126">Request syntax</span></span>

| <span data-ttu-id="595c2-127">Método</span><span class="sxs-lookup"><span data-stu-id="595c2-127">Method</span></span>     | <span data-ttu-id="595c2-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="595c2-128">Request URI</span></span>                                                                                          |
|------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="595c2-129">**EXCLUIR**</span><span class="sxs-lookup"><span data-stu-id="595c2-129">**DELETE**</span></span> | <span data-ttu-id="595c2-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/policies/{policy-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="595c2-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="595c2-131">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="595c2-131">URI parameters</span></span>

<span data-ttu-id="595c2-132">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="595c2-132">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="595c2-133">Nome</span><span class="sxs-lookup"><span data-stu-id="595c2-133">Name</span></span>        | <span data-ttu-id="595c2-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="595c2-134">Type</span></span>   | <span data-ttu-id="595c2-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="595c2-135">Required</span></span> | <span data-ttu-id="595c2-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="595c2-136">Description</span></span>                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| <span data-ttu-id="595c2-137">id cliente</span><span class="sxs-lookup"><span data-stu-id="595c2-137">customer-id</span></span> | <span data-ttu-id="595c2-138">string</span><span class="sxs-lookup"><span data-stu-id="595c2-138">string</span></span> | <span data-ttu-id="595c2-139">Sim</span><span class="sxs-lookup"><span data-stu-id="595c2-139">Yes</span></span>      | <span data-ttu-id="595c2-140">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="595c2-140">A GUID-formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="595c2-141">id de política</span><span class="sxs-lookup"><span data-stu-id="595c2-141">policy-id</span></span>   | <span data-ttu-id="595c2-142">string</span><span class="sxs-lookup"><span data-stu-id="595c2-142">string</span></span> | <span data-ttu-id="595c2-143">Sim</span><span class="sxs-lookup"><span data-stu-id="595c2-143">Yes</span></span>      | <span data-ttu-id="595c2-144">Uma cadeia formatada por GUID que identifica a política de eliminar.</span><span class="sxs-lookup"><span data-stu-id="595c2-144">A GUID-formatted string that identifies the policy to delete.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="595c2-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="595c2-145">Request headers</span></span>

<span data-ttu-id="595c2-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="595c2-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="595c2-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="595c2-147">Request body</span></span>

<span data-ttu-id="595c2-148">Nenhum</span><span class="sxs-lookup"><span data-stu-id="595c2-148">None</span></span>

### <a name="request-example"></a><span data-ttu-id="595c2-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="595c2-149">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies/56edf752-ee77-4fd8-b7f5-df1f74a3a9ac HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 0
Content-Type: application/json
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="595c2-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="595c2-150">REST response</span></span>

<span data-ttu-id="595c2-151">Se for bem sucedida, a resposta devolve um código de estado 204 No Content.</span><span class="sxs-lookup"><span data-stu-id="595c2-151">If successful, the response returns a 204 No Content status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="595c2-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="595c2-152">Response success and error codes</span></span>

<span data-ttu-id="595c2-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="595c2-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="595c2-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="595c2-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="595c2-155">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="595c2-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="595c2-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="595c2-156">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: cee5caf4-c322-4baa-b1d7-e94afb9891a4
MS-RequestId: 76b6f317-1da1-4b61-a6fd-9952439a2c46
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:10:41 GMT
```
