---
title: Obter a política de configuração de um cliente
description: Como recuperar a política de configuração especificada para o cliente especificado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f9a8cb435c63d8d02c3b4633abc8723353116f37
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547500"
---
# <a name="retrieve-a-customers-configuration-policy"></a><span data-ttu-id="82ac5-103">Obter a política de configuração de um cliente</span><span class="sxs-lookup"><span data-stu-id="82ac5-103">Retrieve a customer's configuration policy</span></span>

<span data-ttu-id="82ac5-104">**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="82ac5-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="82ac5-105">Como recuperar a política de configuração especificada para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="82ac5-105">How to retrieve the specified configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="82ac5-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="82ac5-106">Prerequisites</span></span>

- <span data-ttu-id="82ac5-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="82ac5-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="82ac5-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="82ac5-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="82ac5-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="82ac5-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="82ac5-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="82ac5-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="82ac5-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="82ac5-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="82ac5-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="82ac5-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="82ac5-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="82ac5-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="82ac5-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="82ac5-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="82ac5-115">O identificador de apólices.</span><span class="sxs-lookup"><span data-stu-id="82ac5-115">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="82ac5-116">C\#</span><span class="sxs-lookup"><span data-stu-id="82ac5-116">C\#</span></span>

<span data-ttu-id="82ac5-117">Para recuperar uma política de configuração para o cliente especificado, ligue primeiro para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="82ac5-117">To retrieve a configuration policy for the specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="82ac5-118">Em seguida, ligue para o método [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) com o ID da política para recuperar uma interface para configurar operações de política para a política especificada.</span><span class="sxs-lookup"><span data-stu-id="82ac5-118">Next, call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span> <span data-ttu-id="82ac5-119">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.getasync) para recuperar a política de configuração.</span><span class="sxs-lookup"><span data-stu-id="82ac5-119">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.getasync) method to retrieve the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;

ConfigurationPolicy retrievedConfigurationPolicy =
    partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedConfigurationPolicyId).Get();
```

<span data-ttu-id="82ac5-120">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="82ac5-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="82ac5-121">**Project**: Partner Center SDK Samples **Class**: GetConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="82ac5-121">**Project**: Partner Center SDK Samples **Class**: GetConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="82ac5-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="82ac5-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="82ac5-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="82ac5-123">Request syntax</span></span>

| <span data-ttu-id="82ac5-124">Método</span><span class="sxs-lookup"><span data-stu-id="82ac5-124">Method</span></span>  | <span data-ttu-id="82ac5-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="82ac5-125">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="82ac5-126">**Obter**</span><span class="sxs-lookup"><span data-stu-id="82ac5-126">**GET**</span></span> | <span data-ttu-id="82ac5-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/policies/{policy-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="82ac5-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="82ac5-128">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="82ac5-128">URI parameter</span></span>

<span data-ttu-id="82ac5-129">Utilize os seguintes parâmetros de percurso e consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="82ac5-129">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="82ac5-130">Nome</span><span class="sxs-lookup"><span data-stu-id="82ac5-130">Name</span></span>        | <span data-ttu-id="82ac5-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="82ac5-131">Type</span></span>   | <span data-ttu-id="82ac5-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="82ac5-132">Required</span></span> | <span data-ttu-id="82ac5-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="82ac5-133">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="82ac5-134">id cliente</span><span class="sxs-lookup"><span data-stu-id="82ac5-134">customer-id</span></span> | <span data-ttu-id="82ac5-135">string</span><span class="sxs-lookup"><span data-stu-id="82ac5-135">string</span></span> | <span data-ttu-id="82ac5-136">Yes</span><span class="sxs-lookup"><span data-stu-id="82ac5-136">Yes</span></span>      | <span data-ttu-id="82ac5-137">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="82ac5-137">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="82ac5-138">id de política</span><span class="sxs-lookup"><span data-stu-id="82ac5-138">policy-id</span></span>   | <span data-ttu-id="82ac5-139">string</span><span class="sxs-lookup"><span data-stu-id="82ac5-139">string</span></span> | <span data-ttu-id="82ac5-140">Yes</span><span class="sxs-lookup"><span data-stu-id="82ac5-140">Yes</span></span>      | <span data-ttu-id="82ac5-141">Uma cadeia formatada por GUID que identifica a política.</span><span class="sxs-lookup"><span data-stu-id="82ac5-141">A GUID-formatted string that identifies the policy.</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="82ac5-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="82ac5-142">Request headers</span></span>

<span data-ttu-id="82ac5-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="82ac5-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="82ac5-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="82ac5-144">Request body</span></span>

<span data-ttu-id="82ac5-145">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="82ac5-145">None</span></span>

### <a name="request-example"></a><span data-ttu-id="82ac5-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="82ac5-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies/56edf752-ee77-4fd8-b7f5-df1f74a3a9ac HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 0
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="82ac5-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="82ac5-147">REST response</span></span>

<span data-ttu-id="82ac5-148">Se for bem sucedida, a resposta contém o recurso [ConfiguraçãoPolicy](device-deployment-resources.md#configurationpolicy) solicitado.</span><span class="sxs-lookup"><span data-stu-id="82ac5-148">If successful, the response contains the requested [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="82ac5-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="82ac5-149">Response success and error codes</span></span>

<span data-ttu-id="82ac5-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="82ac5-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="82ac5-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="82ac5-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="82ac5-152">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="82ac5-152">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="82ac5-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="82ac5-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 443
MS-CorrelationId: abe150cf-c677-435c-b5d5-b34899a6d1ec
MS-RequestId: ab3abfe7-dce7-46c0-ab20-4fd49bc3e2f7
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:08:27 GMT

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API 1",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"],
    "createdDate": "2017-07-25T11:03:03.8457116-07:00",
    "lastModifiedDate": "2017-07-25T11:04:00.8149974-07:00",
    "attributes": {
        "objectType": "ConfigurationPolicy"
    }
}
```
