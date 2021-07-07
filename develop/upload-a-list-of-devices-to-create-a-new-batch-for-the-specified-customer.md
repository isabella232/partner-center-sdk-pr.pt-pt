---
title: Carregar uma lista de dispositivos para criar um novo lote para o cliente especificado
description: Como carregar uma lista de informações sobre dispositivos para criar um novo lote para o cliente especificado. Isto cria um lote de dispositivo para inscrição em implementação de toque zero, e associa os dispositivos e o lote do dispositivo com o cliente especificado.
ms.date: 08/08/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 285af12034562262c99b2aa3b139e948b0fdd462
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529737"
---
# <a name="upload-a-list-of-devices-to-create-a-new-batch-for-the-specified-customer"></a><span data-ttu-id="66db1-104">Carregar uma lista de dispositivos para criar um novo lote para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="66db1-104">Upload a list of devices to create a new batch for the specified customer</span></span>

<span data-ttu-id="66db1-105">**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="66db1-105">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="66db1-106">Como carregar uma lista de informações sobre dispositivos para criar um novo lote para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="66db1-106">How to upload a list of information about devices to create a new batch for the specified customer.</span></span> <span data-ttu-id="66db1-107">Isto cria um lote de dispositivo para inscrição em implementação de toque zero, e associa os dispositivos e o lote do dispositivo com o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="66db1-107">This creates a device batch for enrollment in zero-touch deployment, and associates the devices and the device batch with the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="66db1-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="66db1-108">Prerequisites</span></span>

- <span data-ttu-id="66db1-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="66db1-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="66db1-110">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="66db1-110">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="66db1-111">Siga o [modelo de aplicação seguro](enable-secure-app-model.md) ao utilizar a autenticação App+User com APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="66db1-111">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="66db1-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="66db1-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="66db1-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="66db1-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="66db1-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="66db1-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="66db1-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="66db1-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="66db1-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="66db1-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="66db1-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="66db1-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="66db1-118">A lista de recursos do dispositivo que fornecem a informação sobre os dispositivos individuais.</span><span class="sxs-lookup"><span data-stu-id="66db1-118">The list of device resources that provide the information about the individual devices.</span></span>

## <a name="c"></a><span data-ttu-id="66db1-119">C\#</span><span class="sxs-lookup"><span data-stu-id="66db1-119">C\#</span></span>

<span data-ttu-id="66db1-120">Para carregar uma lista de dispositivos para criar um novo lote de dispositivos:</span><span class="sxs-lookup"><span data-stu-id="66db1-120">To upload a list of devices to create a new device batch:</span></span>

1. <span data-ttu-id="66db1-121">Instantiizar um novo dispositivo [List/dotnet/api/system.collections.generic.list-1) do tipo [**Dispositivo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) e povoar a lista com os dispositivos.</span><span class="sxs-lookup"><span data-stu-id="66db1-121">Instantiate a new [List/dotnet/api/system.collections.generic.list-1) of type [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) and populate the list with the devices.</span></span> <span data-ttu-id="66db1-122">São necessárias, no mínimo, as seguintes combinações de propriedades povoadas para a identificação de cada dispositivo:</span><span class="sxs-lookup"><span data-stu-id="66db1-122">The following combinations of populated properties are required at a minimum for identifying each device:</span></span>

   - <span data-ttu-id="66db1-123">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span><span class="sxs-lookup"><span data-stu-id="66db1-123">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span></span>
   - <span data-ttu-id="66db1-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**Número de série**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="66db1-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>
   - <span data-ttu-id="66db1-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  Chave de [**Produto**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)  +  [**Número de série**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="66db1-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>
   - <span data-ttu-id="66db1-126">[**HardwareHash apenas.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)</span><span class="sxs-lookup"><span data-stu-id="66db1-126">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) only.</span></span>
   - <span data-ttu-id="66db1-127">[**Apenas ProductKey.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)</span><span class="sxs-lookup"><span data-stu-id="66db1-127">[**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) only.</span></span>
   - <span data-ttu-id="66db1-128">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber)  +  [**Nome de OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername)  +  [**Nome modelo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span><span class="sxs-lookup"><span data-stu-id="66db1-128">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber) + [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername) + [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span></span>

2. <span data-ttu-id="66db1-129">Instantiate a [**DeviceBatchCreationRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest) e definir a propriedade [**BatchId**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.batchid) para um nome único à sua escolha, e a propriedade [**devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) para a lista de dispositivos a carregar.</span><span class="sxs-lookup"><span data-stu-id="66db1-129">Instantiate a [**DeviceBatchCreationRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest) object and set the [**BatchId**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.batchid) property to a unique name of your choosing, and the [**Devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) property to the list of devices to upload.</span></span>

3. <span data-ttu-id="66db1-130">Processe o pedido de criação de lote de dispositivo ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="66db1-130">Process the device batch creation request by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer.</span></span>

4. <span data-ttu-id="66db1-131">Ligue para o [**método DeviceBatches.Criar**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) ou [**Criar Oanc**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) com o pedido de criação de lote de dispositivo para criar o lote.</span><span class="sxs-lookup"><span data-stu-id="66db1-131">Call the [**DeviceBatches.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) method with the device batch creation request to create the batch.</span></span>

```csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;

List<Device> devicesToBeUploaded = new List<Device>
{
    new Device
    {
        HardwareHash = "DummyHash123",
        ProductKey = "00329-00000-0003-AA606",
        SerialNumber = "1R9-ZNP67"
    }
};

DeviceBatchCreationRequest
    newDeviceBatch = new DeviceBatchCreationRequest
{
    BatchId = "SDKTestDeviceBatch",
    Devices = devicesToBeUploaded
};

var trackingLocation =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.Create(newDeviceBatch);
```

<span data-ttu-id="66db1-132">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="66db1-132">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="66db1-133">**Project**: Partner Center SDK Samples **Class**: CreateDeviceBatch.cs</span><span class="sxs-lookup"><span data-stu-id="66db1-133">**Project**: Partner Center SDK Samples **Class**: CreateDeviceBatch.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="66db1-134">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="66db1-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="66db1-135">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="66db1-135">Request syntax</span></span>

| <span data-ttu-id="66db1-136">Método</span><span class="sxs-lookup"><span data-stu-id="66db1-136">Method</span></span>   | <span data-ttu-id="66db1-137">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="66db1-137">Request URI</span></span>                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="66db1-138">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="66db1-138">**POST**</span></span> | <span data-ttu-id="66db1-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/deviceBatches HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="66db1-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="66db1-140">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="66db1-140">URI parameter</span></span>

<span data-ttu-id="66db1-141">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="66db1-141">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="66db1-142">Nome</span><span class="sxs-lookup"><span data-stu-id="66db1-142">Name</span></span>        | <span data-ttu-id="66db1-143">Tipo</span><span class="sxs-lookup"><span data-stu-id="66db1-143">Type</span></span>   | <span data-ttu-id="66db1-144">Necessário</span><span class="sxs-lookup"><span data-stu-id="66db1-144">Required</span></span> | <span data-ttu-id="66db1-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="66db1-145">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="66db1-146">id cliente</span><span class="sxs-lookup"><span data-stu-id="66db1-146">customer-id</span></span> | <span data-ttu-id="66db1-147">string</span><span class="sxs-lookup"><span data-stu-id="66db1-147">string</span></span> | <span data-ttu-id="66db1-148">Yes</span><span class="sxs-lookup"><span data-stu-id="66db1-148">Yes</span></span>      | <span data-ttu-id="66db1-149">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="66db1-149">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="66db1-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="66db1-150">Request headers</span></span>

<span data-ttu-id="66db1-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="66db1-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="66db1-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="66db1-152">Request body</span></span>

<span data-ttu-id="66db1-153">O corpo de pedido deve conter um recurso [DeviceBatchCreationRequest.](device-deployment-resources.md#devicebatchcreationrequest)</span><span class="sxs-lookup"><span data-stu-id="66db1-153">The request body must contain a [DeviceBatchCreationRequest](device-deployment-resources.md#devicebatchcreationrequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="66db1-154">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="66db1-154">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/deviceBatches HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c245d5f2-1de3-4ae0-9e42-95e38e3cb8ff
MS-CorrelationId: e3f26e6a-044f-4371-ad52-0d91ce4200be
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 340
Expect: 100-continue
Connection: Keep-Alive
{
    "BatchId": "SDKTestDeviceBatch",
    "Devices": [{
            "Id": null,
            "SerialNumber": "1R9-ZNP67",
            "ProductKey": "00329-00000-0003-AA606",
            "HardwareHash": "DummyHash123",
            "Policies": null,
            "CreatedBy": null,
            "UploadedDate": "0001-01-01T00:00:00",
            "AllowedOperations": null,
            "Attributes": {
                "ObjectType": "Device"
            }
        }
    ],
    "Attributes": {
        "ObjectType": "DeviceBatchCreationRequest"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="66db1-155">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="66db1-155">REST response</span></span>

<span data-ttu-id="66db1-156">Se for bem sucedida, a resposta contém um **cabeçalho de localização** que tem um URI que pode ser usado para recuperar o estado de upload do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="66db1-156">If successful, the response contains a **Location** header that has a URI that can be used to retrieve device upload status.</span></span> <span data-ttu-id="66db1-157">Guarde este URI para utilização com outras APIs de REST relacionadas.</span><span class="sxs-lookup"><span data-stu-id="66db1-157">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="66db1-158">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="66db1-158">Response success and error codes</span></span>

<span data-ttu-id="66db1-159">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="66db1-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="66db1-160">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="66db1-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="66db1-161">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="66db1-161">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="66db1-162">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="66db1-162">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/batchJobStatus/beba2053-5401-46ff-9223-7e841ed78fbf
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 28 Sep 2017 20:35:35 GMT
```
