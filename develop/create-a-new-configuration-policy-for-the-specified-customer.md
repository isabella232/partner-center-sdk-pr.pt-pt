---
title: Criar uma nova política de configuração do cliente
description: Saiba como utilizar as APIs do Partner Center para criar uma nova política de configuração para um cliente especificado. O artigo inclui pré-requisitos, passos e exemplos.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 21a0bfde7f931371ff09d6c27de0281a4ed3b3cb
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770167"
---
# <a name="create-a-new-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="27e29-104">Criar uma nova política de configuração para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="27e29-104">Create a new configuration policy for the specified customer</span></span>

<span data-ttu-id="27e29-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="27e29-105">**Applies to:**</span></span>

- <span data-ttu-id="27e29-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="27e29-106">Partner Center</span></span>
- <span data-ttu-id="27e29-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="27e29-107">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="27e29-108">Como criar uma nova política de configuração para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="27e29-108">How to create a new configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27e29-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="27e29-109">Prerequisites</span></span>

- <span data-ttu-id="27e29-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="27e29-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="27e29-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="27e29-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="27e29-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="27e29-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="27e29-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="27e29-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="27e29-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="27e29-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="27e29-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="27e29-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="27e29-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="27e29-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="27e29-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="27e29-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="27e29-118">C\#</span><span class="sxs-lookup"><span data-stu-id="27e29-118">C\#</span></span>

<span data-ttu-id="27e29-119">Para criar uma nova política de configuração para o cliente especificado:</span><span class="sxs-lookup"><span data-stu-id="27e29-119">To create a new configuration policy for the specified customer:</span></span>

1. <span data-ttu-id="27e29-120">Instantaneamente um novo objeto [**ConfigurationPolicy,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) tal como mostrado no seguinte corte de código.</span><span class="sxs-lookup"><span data-stu-id="27e29-120">Instantiate a new [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) object as shown in the following code snippet.</span></span> <span data-ttu-id="27e29-121">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="27e29-121">Then call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="27e29-122">Recupere a propriedade [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) para obter uma interface para configurar operações de recolha de políticas.</span><span class="sxs-lookup"><span data-stu-id="27e29-122">Retrieve the [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) property to get an interface to configuration policy collection operations.</span></span>

3. <span data-ttu-id="27e29-123">Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) ou [**Criar**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) Para criar a política de configuração.</span><span class="sxs-lookup"><span data-stu-id="27e29-123">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) method to create the configuration policy.</span></span>

### <a name="c-example"></a><span data-ttu-id="27e29-124">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="27e29-124">C\# example</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var configurationPolicyToCreate = new ConfigurationPolicy
{
    Name = "Test Config Policy",
    Description = "This configuration policy is created by the SDK samples",
    PolicySettings = new List<PolicySettingsType>() {
        PolicySettingsType.OobeUserNotLocalAdmin,
        PolicySettingsType.SkipEula }
};

var createdConfigurationPolicy =
    partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.Create(configurationPolicyToCreate);
```

<span data-ttu-id="27e29-125">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="27e29-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="27e29-126">**Projeto**: Partner Center SDK Samples **Class**: CreateConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="27e29-126">**Project**: Partner Center SDK Samples **Class**: CreateConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="27e29-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="27e29-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="27e29-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="27e29-128">Request syntax</span></span>

| <span data-ttu-id="27e29-129">Método</span><span class="sxs-lookup"><span data-stu-id="27e29-129">Method</span></span>   | <span data-ttu-id="27e29-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="27e29-130">Request URI</span></span>                                                                              |
|----------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="27e29-131">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="27e29-131">**POST**</span></span> | <span data-ttu-id="27e29-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/policies HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="27e29-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="27e29-133">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="27e29-133">URI parameter</span></span>

<span data-ttu-id="27e29-134">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="27e29-134">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="27e29-135">Nome</span><span class="sxs-lookup"><span data-stu-id="27e29-135">Name</span></span>        | <span data-ttu-id="27e29-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="27e29-136">Type</span></span>   | <span data-ttu-id="27e29-137">Necessário</span><span class="sxs-lookup"><span data-stu-id="27e29-137">Required</span></span> | <span data-ttu-id="27e29-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="27e29-138">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="27e29-139">id cliente</span><span class="sxs-lookup"><span data-stu-id="27e29-139">customer-id</span></span> | <span data-ttu-id="27e29-140">string</span><span class="sxs-lookup"><span data-stu-id="27e29-140">string</span></span> | <span data-ttu-id="27e29-141">Sim</span><span class="sxs-lookup"><span data-stu-id="27e29-141">Yes</span></span>      | <span data-ttu-id="27e29-142">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="27e29-142">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="27e29-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="27e29-143">Request headers</span></span>

<span data-ttu-id="27e29-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="27e29-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="27e29-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="27e29-145">Request body</span></span>

<span data-ttu-id="27e29-146">O organismo de pedido deve conter um objeto com as informações da política de configuração descritas no quadro seguinte:</span><span class="sxs-lookup"><span data-stu-id="27e29-146">The request body must contain an object with the configuration policy information as described in the following table:</span></span>

| <span data-ttu-id="27e29-147">Nome</span><span class="sxs-lookup"><span data-stu-id="27e29-147">Name</span></span>           | <span data-ttu-id="27e29-148">Tipo</span><span class="sxs-lookup"><span data-stu-id="27e29-148">Type</span></span>             | <span data-ttu-id="27e29-149">Necessário</span><span class="sxs-lookup"><span data-stu-id="27e29-149">Required</span></span> | <span data-ttu-id="27e29-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="27e29-150">Description</span></span>                      |
|----------------|------------------|----------|----------------------------------|
| <span data-ttu-id="27e29-151">name</span><span class="sxs-lookup"><span data-stu-id="27e29-151">name</span></span>           | <span data-ttu-id="27e29-152">string</span><span class="sxs-lookup"><span data-stu-id="27e29-152">string</span></span>           | <span data-ttu-id="27e29-153">Sim</span><span class="sxs-lookup"><span data-stu-id="27e29-153">Yes</span></span>      | <span data-ttu-id="27e29-154">O nome amigável da apólice.</span><span class="sxs-lookup"><span data-stu-id="27e29-154">The friendly name of the policy.</span></span> |
| <span data-ttu-id="27e29-155">categoria</span><span class="sxs-lookup"><span data-stu-id="27e29-155">category</span></span>       | <span data-ttu-id="27e29-156">string</span><span class="sxs-lookup"><span data-stu-id="27e29-156">string</span></span>           | <span data-ttu-id="27e29-157">Sim</span><span class="sxs-lookup"><span data-stu-id="27e29-157">Yes</span></span>      | <span data-ttu-id="27e29-158">A categoria política.</span><span class="sxs-lookup"><span data-stu-id="27e29-158">The policy category.</span></span>             |
| <span data-ttu-id="27e29-159">descrição</span><span class="sxs-lookup"><span data-stu-id="27e29-159">description</span></span>    | <span data-ttu-id="27e29-160">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="27e29-160">string</span></span>           | <span data-ttu-id="27e29-161">No</span><span class="sxs-lookup"><span data-stu-id="27e29-161">No</span></span>       | <span data-ttu-id="27e29-162">A descrição da apólice.</span><span class="sxs-lookup"><span data-stu-id="27e29-162">The policy description.</span></span>          |
| <span data-ttu-id="27e29-163">policySettings</span><span class="sxs-lookup"><span data-stu-id="27e29-163">policySettings</span></span> | <span data-ttu-id="27e29-164">matriz de cadeias (de carateres)</span><span class="sxs-lookup"><span data-stu-id="27e29-164">array of strings</span></span> | <span data-ttu-id="27e29-165">Sim</span><span class="sxs-lookup"><span data-stu-id="27e29-165">Yes</span></span>      | <span data-ttu-id="27e29-166">As definições de política.</span><span class="sxs-lookup"><span data-stu-id="27e29-166">The policy settings.</span></span>             |

### <a name="request-example"></a><span data-ttu-id="27e29-167">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="27e29-167">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com//v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 212
Content-Type: application/json
Host: api.partnercenter.microsoft.com

{
    "name": "Windows 10 Enterprise E5",
    "category": "o_o_b_e",
    "description": "test policy creation from API",
    "policySettings": ["oobe_user_not_local_admin", "skip_express_settings"]
}
```

## <a name="rest-response"></a><span data-ttu-id="27e29-168">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="27e29-168">REST response</span></span>

<span data-ttu-id="27e29-169">Se for bem sucedido, o organismo de resposta contém o recurso [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) para a nova política.</span><span class="sxs-lookup"><span data-stu-id="27e29-169">If successful, the response body contains the [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource for the new policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="27e29-170">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="27e29-170">Response success and error codes</span></span>

<span data-ttu-id="27e29-171">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="27e29-171">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="27e29-172">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="27e29-172">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="27e29-173">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="27e29-173">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="27e29-174">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="27e29-174">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 404
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4beda413-74fc-4839-b74f-f580c353ab45
MS-RequestId: 0dfadf74-aa66-49ed-9a67-b3b78d9297cc
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:07:36 GMT

{
    "id": "40cdb858-edcc-44d7-9083-d6a36d43bd3f",
    "name": "Windows 10 Enterprise E5",
    "category": "o_o_b_e",
    "description": "test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["oobe_user_not_local_admin", "skip_express_settings"],
    "createdDate": "2017-07-25T18:07:36",
    "lastModifiedDate": "2017-07-25T18:07:36",
    "attributes": {
        "objectType": "ConfigurationPolicy"
    }
}
```
