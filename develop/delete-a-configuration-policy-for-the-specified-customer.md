---
title: Eliminar uma política de configuração para o cliente especificado
description: Como eliminar uma política de configuração para um cliente especificado e identificador de política.
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2d6a7d392bd6af6850eb7716528e6745943bb7bb
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973031"
---
# <a name="delete-a-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="4092b-103">Eliminar uma política de configuração para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="4092b-103">Delete a configuration policy for the specified customer</span></span>

<span data-ttu-id="4092b-104">**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="4092b-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="4092b-105">Como eliminar uma política de configuração para um cliente especificado e identificador de política.</span><span class="sxs-lookup"><span data-stu-id="4092b-105">How to delete a configuration policy for a specified customer and policy identifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4092b-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4092b-106">Prerequisites</span></span>

- <span data-ttu-id="4092b-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4092b-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4092b-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="4092b-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="4092b-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4092b-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4092b-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="4092b-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4092b-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="4092b-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4092b-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="4092b-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4092b-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="4092b-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4092b-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4092b-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="4092b-115">O identificador de apólices.</span><span class="sxs-lookup"><span data-stu-id="4092b-115">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="4092b-116">C\#</span><span class="sxs-lookup"><span data-stu-id="4092b-116">C\#</span></span>

<span data-ttu-id="4092b-117">Para eliminar uma política de configuração para um cliente especificado:</span><span class="sxs-lookup"><span data-stu-id="4092b-117">To delete a configuration policy for a specified customer:</span></span>

1. <span data-ttu-id="4092b-118">Ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="4092b-118">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="4092b-119">Ligue para o método [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) com o ID da política para recuperar uma interface para configurar operações de política para a política especificada.</span><span class="sxs-lookup"><span data-stu-id="4092b-119">Call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span>

3. <span data-ttu-id="4092b-120">Ligue para o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.delete) ou [**EliminarAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.deleteasync) para eliminar a política de configuração.</span><span class="sxs-lookup"><span data-stu-id="4092b-120">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.deleteasync) method to delete the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedPolicyId;

partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedPolicyId).Delete();
```

<span data-ttu-id="4092b-121">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="4092b-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="4092b-122">**Project**: Partner Center SDK Samples **Class**: DeleteConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="4092b-122">**Project**: Partner Center SDK Samples **Class**: DeleteConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="4092b-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="4092b-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4092b-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="4092b-124">Request syntax</span></span>

| <span data-ttu-id="4092b-125">Método</span><span class="sxs-lookup"><span data-stu-id="4092b-125">Method</span></span>     | <span data-ttu-id="4092b-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="4092b-126">Request URI</span></span>                                                                                          |
|------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4092b-127">**EXCLUIR**</span><span class="sxs-lookup"><span data-stu-id="4092b-127">**DELETE**</span></span> | <span data-ttu-id="4092b-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/policies/{policy-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4092b-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="4092b-129">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="4092b-129">URI parameters</span></span>

<span data-ttu-id="4092b-130">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="4092b-130">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="4092b-131">Nome</span><span class="sxs-lookup"><span data-stu-id="4092b-131">Name</span></span>        | <span data-ttu-id="4092b-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="4092b-132">Type</span></span>   | <span data-ttu-id="4092b-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="4092b-133">Required</span></span> | <span data-ttu-id="4092b-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="4092b-134">Description</span></span>                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| <span data-ttu-id="4092b-135">id cliente</span><span class="sxs-lookup"><span data-stu-id="4092b-135">customer-id</span></span> | <span data-ttu-id="4092b-136">string</span><span class="sxs-lookup"><span data-stu-id="4092b-136">string</span></span> | <span data-ttu-id="4092b-137">Yes</span><span class="sxs-lookup"><span data-stu-id="4092b-137">Yes</span></span>      | <span data-ttu-id="4092b-138">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="4092b-138">A GUID-formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="4092b-139">id de política</span><span class="sxs-lookup"><span data-stu-id="4092b-139">policy-id</span></span>   | <span data-ttu-id="4092b-140">string</span><span class="sxs-lookup"><span data-stu-id="4092b-140">string</span></span> | <span data-ttu-id="4092b-141">Yes</span><span class="sxs-lookup"><span data-stu-id="4092b-141">Yes</span></span>      | <span data-ttu-id="4092b-142">Uma cadeia formatada por GUID que identifica a política de eliminar.</span><span class="sxs-lookup"><span data-stu-id="4092b-142">A GUID-formatted string that identifies the policy to delete.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4092b-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="4092b-143">Request headers</span></span>

<span data-ttu-id="4092b-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4092b-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4092b-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="4092b-145">Request body</span></span>

<span data-ttu-id="4092b-146">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="4092b-146">None</span></span>

### <a name="request-example"></a><span data-ttu-id="4092b-147">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="4092b-147">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="4092b-148">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="4092b-148">REST response</span></span>

<span data-ttu-id="4092b-149">Se for bem sucedida, a resposta devolve um código de estado 204 No Content.</span><span class="sxs-lookup"><span data-stu-id="4092b-149">If successful, the response returns a 204 No Content status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4092b-150">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="4092b-150">Response success and error codes</span></span>

<span data-ttu-id="4092b-151">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="4092b-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4092b-152">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4092b-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4092b-153">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4092b-153">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4092b-154">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="4092b-154">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: cee5caf4-c322-4baa-b1d7-e94afb9891a4
MS-RequestId: 76b6f317-1da1-4b61-a6fd-9952439a2c46
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:10:41 GMT
```
