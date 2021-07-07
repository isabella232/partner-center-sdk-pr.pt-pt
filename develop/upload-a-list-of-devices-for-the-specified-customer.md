---
title: Carregar uma lista de dispositivos para um lote existente para o cliente especificado
description: Como enviar uma lista de informações sobre dispositivos para um lote existente para o cliente especificado. Isto associa os dispositivos a um lote de dispositivo já criado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3fa9cff39113130c54cecfaef1f8ca28e0ac5adf
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530315"
---
# <a name="upload-a-list-of-devices-to-an-existing-batch-for-the-specified-customer"></a><span data-ttu-id="f169a-104">Carregar uma lista de dispositivos para um lote existente para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="f169a-104">Upload a list of devices to an existing batch for the specified customer</span></span>

<span data-ttu-id="f169a-105">**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="f169a-105">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="f169a-106">Como enviar uma lista de informações sobre dispositivos para um lote existente para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="f169a-106">How to upload a list of information about devices to an existing batch for the specified customer.</span></span> <span data-ttu-id="f169a-107">Isto associa os dispositivos a um lote de dispositivo já criado.</span><span class="sxs-lookup"><span data-stu-id="f169a-107">This associates the devices with a device batch already created.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f169a-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f169a-108">Prerequisites</span></span>

- <span data-ttu-id="f169a-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f169a-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f169a-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="f169a-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="f169a-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f169a-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f169a-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f169a-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f169a-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="f169a-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f169a-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="f169a-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f169a-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="f169a-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f169a-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f169a-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f169a-117">O identificador do lote do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f169a-117">The device batch identifier.</span></span>

- <span data-ttu-id="f169a-118">A lista de recursos do dispositivo que fornecem a informação sobre os dispositivos individuais.</span><span class="sxs-lookup"><span data-stu-id="f169a-118">The list of device resources that provide the information about the individual devices.</span></span>

## <a name="c"></a><span data-ttu-id="f169a-119">C\#</span><span class="sxs-lookup"><span data-stu-id="f169a-119">C\#</span></span>

<span data-ttu-id="f169a-120">Para fazer o upload de uma lista de dispositivos para um lote de dispositivo existente, em primeiro lugar, instantaneamente um novo dispositivo [List/dotnet/api/system.collections.generic.list-1) do [**tipo Dispositivo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) e povoar a lista com os dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f169a-120">To upload a list of devices to an existing device batch, first, instantiate a new [List/dotnet/api/system.collections.generic.list-1) of type [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) and populate the list with the devices.</span></span> <span data-ttu-id="f169a-121">São necessárias, no mínimo, as seguintes combinações de propriedades povoadas para a identificação de cada dispositivo:</span><span class="sxs-lookup"><span data-stu-id="f169a-121">The following combinations of populated properties are required at a minimum for identifying each device:</span></span>

- <span data-ttu-id="f169a-122">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span><span class="sxs-lookup"><span data-stu-id="f169a-122">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span></span>

- <span data-ttu-id="f169a-123">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**Número de série**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="f169a-123">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>

- <span data-ttu-id="f169a-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  Chave de [**Produto**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)  +  [**Número de série**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="f169a-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>

- <span data-ttu-id="f169a-125">[**HardwareHash apenas.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)</span><span class="sxs-lookup"><span data-stu-id="f169a-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) only.</span></span>

- <span data-ttu-id="f169a-126">[**Apenas ProductKey.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)</span><span class="sxs-lookup"><span data-stu-id="f169a-126">[**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) only.</span></span>

- <span data-ttu-id="f169a-127">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber)  +  [**Nome de OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername)  +  [**Nome modelo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span><span class="sxs-lookup"><span data-stu-id="f169a-127">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber) + [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername) + [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span></span>

<span data-ttu-id="f169a-128">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="f169a-128">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="f169a-129">Em seguida, ligue para o método [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) com o identificador de lote do dispositivo para obter uma interface para as operações do lote especificado.</span><span class="sxs-lookup"><span data-stu-id="f169a-129">Next, call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method with the device batch identifier to get an interface to operations for the specified batch.</span></span> <span data-ttu-id="f169a-130">Por fim, ligue para o método [**Dispositivos.Criar**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.create) ou Criar Como [**se é que a**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.createasync) lista de dispositivos para adicionar os dispositivos ao lote do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f169a-130">Finally, call the [**Devices.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.createasync) method with the list of devices to add the devices to the device batch.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;

List<Device> devicesToBeUploaded = new List<Device>
{
    new Device
    {
        HardwareHash = "DummyHash1234",
        ProductKey = "00329-00000-0003-AA606",
        SerialNumber = "2R9-ZNP67"
    },

    new Device
    {
        HardwareHash = "DummyHash12345",
        ProductKey = "00329-00000-0003-AA606",
        SerialNumber = "2R9-ZNP67"
    }
};

var trackingLocation =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.Create(devicesToBeUploaded);
```

<span data-ttu-id="f169a-131">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="f169a-131">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="f169a-132">**Project**: Partner Center SDK Samples **Class**: CreateDevices.cs</span><span class="sxs-lookup"><span data-stu-id="f169a-132">**Project**: Partner Center SDK Samples **Class**: CreateDevices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="f169a-133">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f169a-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f169a-134">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f169a-134">Request syntax</span></span>

| <span data-ttu-id="f169a-135">Método</span><span class="sxs-lookup"><span data-stu-id="f169a-135">Method</span></span>   | <span data-ttu-id="f169a-136">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f169a-136">Request URI</span></span>                                                                                                            |
|----------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f169a-137">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="f169a-137">**POST**</span></span> | <span data-ttu-id="f169a-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/deviceBatches/{devicebatch-id}/dispositivos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f169a-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="f169a-139">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="f169a-139">URI parameter</span></span>

<span data-ttu-id="f169a-140">Utilize os seguintes parâmetros de percurso e consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="f169a-140">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="f169a-141">Nome</span><span class="sxs-lookup"><span data-stu-id="f169a-141">Name</span></span>           | <span data-ttu-id="f169a-142">Tipo</span><span class="sxs-lookup"><span data-stu-id="f169a-142">Type</span></span>   | <span data-ttu-id="f169a-143">Necessário</span><span class="sxs-lookup"><span data-stu-id="f169a-143">Required</span></span> | <span data-ttu-id="f169a-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="f169a-144">Description</span></span>                                           |
|----------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="f169a-145">id cliente</span><span class="sxs-lookup"><span data-stu-id="f169a-145">customer-id</span></span>    | <span data-ttu-id="f169a-146">string</span><span class="sxs-lookup"><span data-stu-id="f169a-146">string</span></span> | <span data-ttu-id="f169a-147">Yes</span><span class="sxs-lookup"><span data-stu-id="f169a-147">Yes</span></span>      | <span data-ttu-id="f169a-148">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="f169a-148">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="f169a-149">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="f169a-149">devicebatch-id</span></span> | <span data-ttu-id="f169a-150">string</span><span class="sxs-lookup"><span data-stu-id="f169a-150">string</span></span> | <span data-ttu-id="f169a-151">Yes</span><span class="sxs-lookup"><span data-stu-id="f169a-151">Yes</span></span>      | <span data-ttu-id="f169a-152">Um identificador de cordas que identifica o lote do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f169a-152">A string identifier that identifies the device batch.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f169a-153">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="f169a-153">Request headers</span></span>

<span data-ttu-id="f169a-154">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f169a-154">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f169a-155">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f169a-155">Request body</span></span>

<span data-ttu-id="f169a-156">O corpo do pedido deve conter uma série de objetos [do Dispositivo.](device-deployment-resources.md#device)</span><span class="sxs-lookup"><span data-stu-id="f169a-156">The request body must contain an array of [Device](device-deployment-resources.md#device) objects.</span></span> <span data-ttu-id="f169a-157">São aceites as seguintes combinações de campos para a identificação de um dispositivo:</span><span class="sxs-lookup"><span data-stu-id="f169a-157">The following combinations of fields for identifying a device are accepted:</span></span>

- <span data-ttu-id="f169a-158">hardwareHash + produtoKey.</span><span class="sxs-lookup"><span data-stu-id="f169a-158">hardwareHash + productKey.</span></span>
- <span data-ttu-id="f169a-159">hardwareHash + serialNumber.</span><span class="sxs-lookup"><span data-stu-id="f169a-159">hardwareHash + serialNumber.</span></span>
- <span data-ttu-id="f169a-160">hardwareHash + produtoKey + serialNumber.</span><span class="sxs-lookup"><span data-stu-id="f169a-160">hardwareHash + productKey + serialNumber.</span></span>
- <span data-ttu-id="f169a-161">hardwareHash apenas.</span><span class="sxs-lookup"><span data-stu-id="f169a-161">hardwareHash only.</span></span>
- <span data-ttu-id="f169a-162">produtoKey apenas.</span><span class="sxs-lookup"><span data-stu-id="f169a-162">productKey only.</span></span>
- <span data-ttu-id="f169a-163">serialNumber + oemManufacturerName + modeloName.</span><span class="sxs-lookup"><span data-stu-id="f169a-163">serialNumber + oemManufacturerName + modelName.</span></span>

### <a name="request-example"></a><span data-ttu-id="f169a-164">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f169a-164">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/deviceBatches/Test/devices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e286d69b-7f5f-4098-8999-21d3b54e4e47
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 482
Expect: 100-continue

[{
        "Id": null,
        "SerialNumber": "2R9-ZNP67",
        "ProductKey": "00329-00000-0003-AA606",
        "HardwareHash": "DummyHash1234",
        "Policies": null,
        "CreatedBy": null,
        "UploadedDate": "0001-01-01T00:00:00",
        "AllowedOperations": null,
        "Attributes": {
            "ObjectType": "Device"
        }
    }, {
        "Id": null,
        "SerialNumber": "2R9-ZNP67",
        "ProductKey": "00329-00000-0003-AA606",
        "HardwareHash": "DummyHash12345",
        "Policies": null,
        "CreatedBy": null,
        "UploadedDate": "0001-01-01T00:00:00",
        "AllowedOperations": null,
        "Attributes": {
            "ObjectType": "Device"
        }
    }
]
```

## <a name="rest-response"></a><span data-ttu-id="f169a-165">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f169a-165">REST response</span></span>

<span data-ttu-id="f169a-166">Se for bem sucedida, a resposta contém um **cabeçalho de localização** que tem um URI que pode ser usado para recuperar o estado de upload do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f169a-166">If successful, the response contains a **Location** header that has a URI that can be used to retrieve device upload status.</span></span> <span data-ttu-id="f169a-167">Guarde este URI para utilização com outras APIs de REST relacionadas.</span><span class="sxs-lookup"><span data-stu-id="f169a-167">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f169a-168">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f169a-168">Response success and error codes</span></span>

<span data-ttu-id="f169a-169">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f169a-169">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f169a-170">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f169a-170">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f169a-171">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f169a-171">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f169a-172">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f169a-172">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/batchJobStatus/16c00110-e79a-433d-aa28-f69dd60df671
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: e286d69b-7f5f-4098-8999-21d3b54e4e47
MS-CV: OBkGN9pSN0a5xvua.0
MS-ServerId: 101112012
Date: Thu, 28 Sep 2017 20:08:46 GMT
```
