---
title: Atualizar uma lista de dispositivos com uma política
description: Como atualizar uma lista de dispositivos com uma política de configuração para o cliente especificado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 35b35873eb253b0929bfc01662b0beb9b31d0c6b
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530077"
---
# <a name="update-a-list-of-devices-with-a-policy"></a><span data-ttu-id="8d5a7-103">Atualizar uma lista de dispositivos com uma política</span><span class="sxs-lookup"><span data-stu-id="8d5a7-103">Update a list of devices with a policy</span></span>

<span data-ttu-id="8d5a7-104">**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="8d5a7-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="8d5a7-105">Como atualizar uma lista de dispositivos com uma política de configuração para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-105">How to update a list of devices with a configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d5a7-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8d5a7-106">Prerequisites</span></span>

- <span data-ttu-id="8d5a7-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8d5a7-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="8d5a7-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8d5a7-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8d5a7-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8d5a7-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="8d5a7-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8d5a7-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="8d5a7-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8d5a7-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="8d5a7-115">O identificador de apólices.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-115">The policy identifier.</span></span>

- <span data-ttu-id="8d5a7-116">Os identificadores do dispositivo para atualizar.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-116">The device identifiers of the devices to update.</span></span>

## <a name="c"></a><span data-ttu-id="8d5a7-117">C\#</span><span class="sxs-lookup"><span data-stu-id="8d5a7-117">C\#</span></span>

<span data-ttu-id="8d5a7-118">Para atualizar uma lista de dispositivos com a política de configuração especificada, em primeiro lugar, instantânea a [List/dotnet/api/system.collections.generic.list-1) do tipo [KeyValuePair/dotnet/api/system.collections.generic.keyvaluepair-2)[**(PolicyCategory,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.policycategory)string) e adicionar a política a aplicar, como mostrado no seguinte código exemplo.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-118">To update a list of devices with the specified configuration policy, first, instantiate a [List/dotnet/api/system.collections.generic.list-1) of type [KeyValuePair/dotnet/api/system.collections.generic.keyvaluepair-2)[**(PolicyCategory,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.policycategory)string) and add the policy to apply, as shown in the following code example.</span></span> <span data-ttu-id="8d5a7-119">Vai precisar do identificador de política da apólice.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-119">You will need the policy identifier of the policy.</span></span>

<span data-ttu-id="8d5a7-120">Em seguida, crie uma lista de objetos do [**Dispositivo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) a atualizar com a política, especificando o identificador do dispositivo e a lista que contém a política a aplicar, para cada dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-120">Then, create a list of [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) objects to be updated with the policy, specifying the device identifier and the list that contains the policy to apply, for each device.</span></span> <span data-ttu-id="8d5a7-121">Em seguida, instantânea um objeto [**DevicePolicyUpdateRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicepolicyupdaterequest) e definir a propriedade [**dispositivos**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) para a lista de objetos do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-121">Next, instantiate a [**DevicePolicyUpdateRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicepolicyupdaterequest) object and set the [**Devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) property to the list of device objects.</span></span>

<span data-ttu-id="8d5a7-122">Para processar o pedido de atualização da política do dispositivo, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-122">To process the device policy update request, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="8d5a7-123">Em seguida, recupere a propriedade [**DevicePolicy**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicepolicy) para obter uma interface para as operações de recolha de dispositivos do cliente.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-123">Then, retrieve the [**DevicePolicy**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicepolicy) property to get an interface to customer device collection operations.</span></span> <span data-ttu-id="8d5a7-124">Por fim, ligue para o método [**'Actualização'**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.icustomerdevicecollection.update) com o objeto DevicePolicyUpdateRequest para atualizar os dispositivos com a política.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-124">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.icustomerdevicecollection.update) method with the DevicePolicyUpdateRequest object to update the devices with the policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;
string selectedDeviceId;

// Indicate the policy to apply to the list of devices.
List<KeyValuePair<PolicyCategory, string>>
    policyToBeAdded = new List<KeyValuePair<PolicyCategory, string>>
{
    new KeyValuePair<PolicyCategory, string>
        (PolicyCategory.OOBE, selectedConfigurationPolicyId)
};

// Create a list of devices to be updated with a policy.
List<Device> devices = new List<Device>
{
    new Device
    {
        Id = selectedDeviceId,
        Policies=policyToBeAdded
    }
};

// Instantiate a DevicePolicyUpdateRequest object.
DevicePolicyUpdateRequest
    devicePolicyUpdateRequest = new DevicePolicyUpdateRequest
{
    Devices = devices
};

// Process the DevicePolicyUpdateRequest.
var trackingLocation =
    partnerOperations.Customers.ById(selectedCustomerId).DevicePolicy.Update(devicePolicyUpdateRequest);
```

<span data-ttu-id="8d5a7-125">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="8d5a7-126">**Project**: Partner Center SDK Samples **Class**: UpdateDevicesPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="8d5a7-126">**Project**: Partner Center SDK Samples **Class**: UpdateDevicesPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="8d5a7-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="8d5a7-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8d5a7-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d5a7-128">Request syntax</span></span>

| <span data-ttu-id="8d5a7-129">Método</span><span class="sxs-lookup"><span data-stu-id="8d5a7-129">Method</span></span>    | <span data-ttu-id="8d5a7-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="8d5a7-130">Request URI</span></span>                                                                                         |
|-----------|-----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8d5a7-131">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="8d5a7-131">**PATCH**</span></span> | <span data-ttu-id="8d5a7-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/DevicePolicyUpdates HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8d5a7-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/DevicePolicyUpdates HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="8d5a7-133">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="8d5a7-133">URI parameter</span></span>

<span data-ttu-id="8d5a7-134">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-134">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="8d5a7-135">Nome</span><span class="sxs-lookup"><span data-stu-id="8d5a7-135">Name</span></span>        | <span data-ttu-id="8d5a7-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="8d5a7-136">Type</span></span>   | <span data-ttu-id="8d5a7-137">Necessário</span><span class="sxs-lookup"><span data-stu-id="8d5a7-137">Required</span></span> | <span data-ttu-id="8d5a7-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d5a7-138">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="8d5a7-139">id cliente</span><span class="sxs-lookup"><span data-stu-id="8d5a7-139">customer-id</span></span> | <span data-ttu-id="8d5a7-140">string</span><span class="sxs-lookup"><span data-stu-id="8d5a7-140">string</span></span> | <span data-ttu-id="8d5a7-141">Yes</span><span class="sxs-lookup"><span data-stu-id="8d5a7-141">Yes</span></span>      | <span data-ttu-id="8d5a7-142">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-142">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8d5a7-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="8d5a7-143">Request headers</span></span>

<span data-ttu-id="8d5a7-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8d5a7-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="8d5a7-145">Request body</span></span>

<span data-ttu-id="8d5a7-146">O corpo de pedido deve conter um recurso [DevicePolicyUpdateRequest.](device-deployment-resources.md#devicepolicyupdaterequest)</span><span class="sxs-lookup"><span data-stu-id="8d5a7-146">The request body must contain a [DevicePolicyUpdateRequest](device-deployment-resources.md#devicepolicyupdaterequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="8d5a7-147">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="8d5a7-147">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/DevicePolicyUpdates HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1b658428-5afa-46d4-af86-c9c6af5634e2
MS-CorrelationId: 49b1e7b2-82e7-4403-b63b-8765269b448d
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 363
Expect: 100-continue
Connection: Keep-Alive

{
    "Devices": [{
            "Id": "9993-8627-3608-6844-6369-4361-72",
            "SerialNumber": null,
            "ProductKey": null,
            "HardwareHash": null,
            "Policies": [{
                    "Key": "o_o_b_e",
                    "Value": "15a04610-9229-4e80-94e0-0e826a09c9e2"
                }
            ],
            "CreatedBy": null,
            "UploadedDate": "0001-01-01T00:00:00",
            "AllowedOperations": null,
            "Attributes": {
                "ObjectType": "Device"
            }
        }
    ],
    "Attributes": {
        "ObjectType": "DevicePolicyUpdateRequest"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="8d5a7-148">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="8d5a7-148">REST response</span></span>

<span data-ttu-id="8d5a7-149">Se for bem sucedida, a resposta contém um **cabeçalho de localização** que tem um URI que pode ser usado para recuperar o estado deste processo de lote.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-149">If successful, the response contains a **Location** header that has a URI that can be used to retrieve the status of this batch process.</span></span> <span data-ttu-id="8d5a7-150">Guarde este URI para utilização com outras APIs de REST relacionadas.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-150">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8d5a7-151">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="8d5a7-151">Response success and error codes</span></span>

<span data-ttu-id="8d5a7-152">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8d5a7-153">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8d5a7-154">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8d5a7-155">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="8d5a7-155">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/batchJobStatus/a15f3996-620a-4404-9f1f-4c2de78de0de
MS-CorrelationId: 49b1e7b2-82e7-4403-b63b-8765269b448d
MS-RequestId: 1b658428-5afa-46d4-af86-c9c6af5634e2
MS-CV: rCXyd8Z/lUSxUd0P.0
MS-ServerId: 020021921
Date: Thu, 28 Sep 2017 21:33:05 GMT
```
