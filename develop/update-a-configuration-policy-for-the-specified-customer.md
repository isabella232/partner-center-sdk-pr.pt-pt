---
title: Atualizar uma política de configuração para o cliente especificado
description: Como atualizar a política de configuração especificada para o cliente especificado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 5e008f41a44f2b7cf3ddfd705505175c69bbad38
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530243"
---
# <a name="update-a-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="76090-103">Atualizar uma política de configuração para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="76090-103">Update a configuration policy for the specified customer</span></span>

<span data-ttu-id="76090-104">**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="76090-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="76090-105">Como atualizar a política de configuração especificada para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="76090-105">How to update the specified configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="76090-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="76090-106">Prerequisites</span></span>

- <span data-ttu-id="76090-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="76090-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="76090-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="76090-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="76090-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="76090-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="76090-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="76090-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="76090-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="76090-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="76090-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="76090-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="76090-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="76090-113">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="76090-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="76090-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="76090-115">O identificador de apólices.</span><span class="sxs-lookup"><span data-stu-id="76090-115">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="76090-116">C\#</span><span class="sxs-lookup"><span data-stu-id="76090-116">C\#</span></span>

<span data-ttu-id="76090-117">Para atualizar uma política de configuração existente para o cliente especificado, instantânea um novo objeto [**ConfigurationPolicy,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) tal como mostrado no seguinte corte de código.</span><span class="sxs-lookup"><span data-stu-id="76090-117">To update an existing configuration policy for the specified customer, instantiate a new [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) object as shown in the following code snippet.</span></span> <span data-ttu-id="76090-118">Os valores deste novo objeto substituem os valores correspondentes no objeto existente.</span><span class="sxs-lookup"><span data-stu-id="76090-118">The values in this new object replace the corresponding values in the existing object.</span></span> <span data-ttu-id="76090-119">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="76090-119">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="76090-120">Em seguida, ligue para o método [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) com o ID da política para recuperar uma interface para configurar operações de política para a política especificada.</span><span class="sxs-lookup"><span data-stu-id="76090-120">Next, call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span> <span data-ttu-id="76090-121">Por fim, ligue para o método [**Patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) ou [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) para atualizar a política de configuração.</span><span class="sxs-lookup"><span data-stu-id="76090-121">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) or [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) method to update the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;

ConfigurationPolicy configPolicyToBeUpdated = new ConfigurationPolicy()
{
    Name= "Test Config Policy",
    Id = selectedConfigurationPolicyId,
    PolicySettings = new List<PolicySettingsType>() {
        PolicySettingsType.OobeUserNotLocalAdmin,
        PolicySettingsType.RemoveOemPreinstalls }
};

ConfigurationPolicy updatedConfigurationPolicy =
    partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedConfigurationPolicyId).Patch(configPolicyToBeUpdated);
```

<span data-ttu-id="76090-122">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="76090-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="76090-123">**Project**: Partner Center SDK Samples **Class**: UpdateConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="76090-123">**Project**: Partner Center SDK Samples **Class**: UpdateConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="76090-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="76090-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="76090-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="76090-125">Request syntax</span></span>

| <span data-ttu-id="76090-126">Método</span><span class="sxs-lookup"><span data-stu-id="76090-126">Method</span></span>  | <span data-ttu-id="76090-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="76090-127">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="76090-128">**PUT**</span><span class="sxs-lookup"><span data-stu-id="76090-128">**PUT**</span></span> | <span data-ttu-id="76090-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/policies/{policy-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="76090-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="76090-130">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="76090-130">URI parameter</span></span>

<span data-ttu-id="76090-131">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="76090-131">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="76090-132">Nome</span><span class="sxs-lookup"><span data-stu-id="76090-132">Name</span></span>        | <span data-ttu-id="76090-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="76090-133">Type</span></span>   | <span data-ttu-id="76090-134">Necessário</span><span class="sxs-lookup"><span data-stu-id="76090-134">Required</span></span> | <span data-ttu-id="76090-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="76090-135">Description</span></span>                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| <span data-ttu-id="76090-136">id cliente</span><span class="sxs-lookup"><span data-stu-id="76090-136">customer-id</span></span> | <span data-ttu-id="76090-137">string</span><span class="sxs-lookup"><span data-stu-id="76090-137">string</span></span> | <span data-ttu-id="76090-138">Yes</span><span class="sxs-lookup"><span data-stu-id="76090-138">Yes</span></span>      | <span data-ttu-id="76090-139">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="76090-139">A GUID-formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="76090-140">id de política</span><span class="sxs-lookup"><span data-stu-id="76090-140">policy-id</span></span>   | <span data-ttu-id="76090-141">string</span><span class="sxs-lookup"><span data-stu-id="76090-141">string</span></span> | <span data-ttu-id="76090-142">Yes</span><span class="sxs-lookup"><span data-stu-id="76090-142">Yes</span></span>      | <span data-ttu-id="76090-143">Uma cadeia formatada por GUID que identifica a política de atualização.</span><span class="sxs-lookup"><span data-stu-id="76090-143">A GUID-formatted string that identifies the policy to update.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="76090-144">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="76090-144">Request headers</span></span>

<span data-ttu-id="76090-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="76090-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="76090-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="76090-146">Request body</span></span>

<span data-ttu-id="76090-147">O organismo de pedido deve conter um objeto que forneça a informação da apólice.</span><span class="sxs-lookup"><span data-stu-id="76090-147">The request body must contain an object that provides the policy information.</span></span>

| <span data-ttu-id="76090-148">Nome</span><span class="sxs-lookup"><span data-stu-id="76090-148">Name</span></span>            | <span data-ttu-id="76090-149">Tipo</span><span class="sxs-lookup"><span data-stu-id="76090-149">Type</span></span>             | <span data-ttu-id="76090-150">Necessário</span><span class="sxs-lookup"><span data-stu-id="76090-150">Required</span></span> | <span data-ttu-id="76090-151">Updatable</span><span class="sxs-lookup"><span data-stu-id="76090-151">Updatable</span></span> | <span data-ttu-id="76090-152">Description</span><span class="sxs-lookup"><span data-stu-id="76090-152">Description</span></span>                                                                                                                                              |
|-----------------|------------------|----------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="76090-153">ID</span><span class="sxs-lookup"><span data-stu-id="76090-153">id</span></span>              | <span data-ttu-id="76090-154">string</span><span class="sxs-lookup"><span data-stu-id="76090-154">string</span></span>           | <span data-ttu-id="76090-155">Yes</span><span class="sxs-lookup"><span data-stu-id="76090-155">Yes</span></span>      | <span data-ttu-id="76090-156">No</span><span class="sxs-lookup"><span data-stu-id="76090-156">No</span></span>        | <span data-ttu-id="76090-157">A cadeia formatada pelo GUID que identifica a política.</span><span class="sxs-lookup"><span data-stu-id="76090-157">The GUID-formatted string that identifies the policy.</span></span>                                                                                                    |
| <span data-ttu-id="76090-158">name</span><span class="sxs-lookup"><span data-stu-id="76090-158">name</span></span>            | <span data-ttu-id="76090-159">string</span><span class="sxs-lookup"><span data-stu-id="76090-159">string</span></span>           | <span data-ttu-id="76090-160">Yes</span><span class="sxs-lookup"><span data-stu-id="76090-160">Yes</span></span>      | <span data-ttu-id="76090-161">Yes</span><span class="sxs-lookup"><span data-stu-id="76090-161">Yes</span></span>       | <span data-ttu-id="76090-162">O nome amigável da apólice.</span><span class="sxs-lookup"><span data-stu-id="76090-162">The friendly name of the policy.</span></span>                                                                                                                         |
| <span data-ttu-id="76090-163">categoria</span><span class="sxs-lookup"><span data-stu-id="76090-163">category</span></span>        | <span data-ttu-id="76090-164">string</span><span class="sxs-lookup"><span data-stu-id="76090-164">string</span></span>           | <span data-ttu-id="76090-165">Yes</span><span class="sxs-lookup"><span data-stu-id="76090-165">Yes</span></span>      | <span data-ttu-id="76090-166">No</span><span class="sxs-lookup"><span data-stu-id="76090-166">No</span></span>        | <span data-ttu-id="76090-167">A categoria política.</span><span class="sxs-lookup"><span data-stu-id="76090-167">The policy category.</span></span>                                                                                                                                     |
| <span data-ttu-id="76090-168">descrição</span><span class="sxs-lookup"><span data-stu-id="76090-168">description</span></span>     | <span data-ttu-id="76090-169">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="76090-169">string</span></span>           | <span data-ttu-id="76090-170">No</span><span class="sxs-lookup"><span data-stu-id="76090-170">No</span></span>       | <span data-ttu-id="76090-171">Yes</span><span class="sxs-lookup"><span data-stu-id="76090-171">Yes</span></span>       | <span data-ttu-id="76090-172">A descrição da apólice.</span><span class="sxs-lookup"><span data-stu-id="76090-172">The policy description.</span></span>                                                                                                                                  |
| <span data-ttu-id="76090-173">dispositivosAssed</span><span class="sxs-lookup"><span data-stu-id="76090-173">devicesAssigned</span></span> | <span data-ttu-id="76090-174">número</span><span class="sxs-lookup"><span data-stu-id="76090-174">number</span></span>           | <span data-ttu-id="76090-175">No</span><span class="sxs-lookup"><span data-stu-id="76090-175">No</span></span>       | <span data-ttu-id="76090-176">No</span><span class="sxs-lookup"><span data-stu-id="76090-176">No</span></span>        | <span data-ttu-id="76090-177">O número de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="76090-177">The number of devices.</span></span>                                                                                                                                   |
| <span data-ttu-id="76090-178">policySettings</span><span class="sxs-lookup"><span data-stu-id="76090-178">policySettings</span></span>  | <span data-ttu-id="76090-179">matriz de cadeias (de carateres)</span><span class="sxs-lookup"><span data-stu-id="76090-179">array of strings</span></span> | <span data-ttu-id="76090-180">Yes</span><span class="sxs-lookup"><span data-stu-id="76090-180">Yes</span></span>      | <span data-ttu-id="76090-181">Yes</span><span class="sxs-lookup"><span data-stu-id="76090-181">Yes</span></span>       | <span data-ttu-id="76090-182">As definições de política: "nenhum", "remover \_ oem \_ pré-instalações", "utilizador oobe \_ não administrador \_ \_ \_ local", "saltar \_ as \_ definições expressas", "saltar \_ o registo de \_ oem", "saltar \_ eula".</span><span class="sxs-lookup"><span data-stu-id="76090-182">The policy settings: "none","remove\_oem\_preinstalls","oobe\_user\_not\_local\_admin","skip\_express\_settings","skip \_oem\_registration,"skip\_eula".</span></span> |

### <a name="request-example"></a><span data-ttu-id="76090-183">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="76090-183">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies/56edf752-ee77-4fd8-b7f5-df1f74a3a9ac HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 256
Content-Type: application/json
Host: api.partnercenter.microsoft.com

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Windows test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"]
}
```

## <a name="rest-response"></a><span data-ttu-id="76090-184">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="76090-184">REST response</span></span>

<span data-ttu-id="76090-185">Se for bem sucedido, o organismo de resposta contém o recurso [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) para a nova política.</span><span class="sxs-lookup"><span data-stu-id="76090-185">If successful, the response body contains the [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource for the new policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="76090-186">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="76090-186">Response success and error codes</span></span>

<span data-ttu-id="76090-187">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="76090-187">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="76090-188">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="76090-188">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="76090-189">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="76090-189">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="76090-190">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="76090-190">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 421
Content-Type: application/json; charset=utf-8
MS-CorrelationId: f9fd5973-6ad8-4585-aadc-f2b0443fe27b
MS-RequestId: cb1fa1f3-1381-45d9-99c5-511e5d3efa7c
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:10:29 GMT

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Windows test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"],
    "createdDate": "2017-01-01T00:00:00",
    "lastModifiedDate": "2017-07-25T18:10:15",
    "attributes": {
        "objectType": "ConfigurationPolicy"
    }
}
```
