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
# <a name="upload-a-list-of-devices-to-create-a-new-batch-for-the-specified-customer"></a>Carregar uma lista de dispositivos para criar um novo lote para o cliente especificado

**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany

Como carregar uma lista de informações sobre dispositivos para criar um novo lote para o cliente especificado. Isto cria um lote de dispositivo para inscrição em implementação de toque zero, e associa os dispositivos e o lote do dispositivo com o cliente especificado.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com credenciais app+utilizador. Siga o [modelo de aplicação seguro](enable-secure-app-model.md) ao utilizar a autenticação App+User com APIs do Partner Center.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- A lista de recursos do dispositivo que fornecem a informação sobre os dispositivos individuais.

## <a name="c"></a>C\#

Para carregar uma lista de dispositivos para criar um novo lote de dispositivos:

1. Instantiizar um novo dispositivo [List/dotnet/api/system.collections.generic.list-1) do tipo [**Dispositivo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) e povoar a lista com os dispositivos. São necessárias, no mínimo, as seguintes combinações de propriedades povoadas para a identificação de cada dispositivo:

   - [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).
   - [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**Número de série**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).
   - [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  Chave de [**Produto**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)  +  [**Número de série**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).
   - [**HardwareHash apenas.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)
   - [**Apenas ProductKey.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)
   - [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber)  +  [**Nome de OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername)  +  [**Nome modelo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).

2. Instantiate a [**DeviceBatchCreationRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest) e definir a propriedade [**BatchId**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.batchid) para um nome único à sua escolha, e a propriedade [**devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) para a lista de dispositivos a carregar.

3. Processe o pedido de criação de lote de dispositivo ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador do cliente para recuperar uma interface para operações no cliente especificado.

4. Ligue para o [**método DeviceBatches.Criar**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) ou [**Criar Oanc**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) com o pedido de criação de lote de dispositivo para criar o lote.

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

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: CreateDeviceBatch.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/deviceBatches HTTP/1.1 |

#### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de trajetória ao criar o pedido.

| Nome        | Tipo   | Necessário | Descrição                                           |
|-------------|--------|----------|-------------------------------------------------------|
| id cliente | string | Yes      | Uma cadeia formatada pelo GUID que identifica o cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

O corpo de pedido deve conter um recurso [DeviceBatchCreationRequest.](device-deployment-resources.md#devicebatchcreationrequest)

### <a name="request-example"></a>Exemplo de pedido

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

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedida, a resposta contém um **cabeçalho de localização** que tem um URI que pode ser usado para recuperar o estado de upload do dispositivo. Guarde este URI para utilização com outras APIs de REST relacionadas.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

#### <a name="response-example"></a>Exemplo de resposta

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
