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
# <a name="upload-a-list-of-devices-to-an-existing-batch-for-the-specified-customer"></a>Carregar uma lista de dispositivos para um lote existente para o cliente especificado

**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany

Como enviar uma lista de informações sobre dispositivos para um lote existente para o cliente especificado. Isto associa os dispositivos a um lote de dispositivo já criado.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- O identificador do lote do dispositivo.

- A lista de recursos do dispositivo que fornecem a informação sobre os dispositivos individuais.

## <a name="c"></a>C\#

Para fazer o upload de uma lista de dispositivos para um lote de dispositivo existente, em primeiro lugar, instantaneamente um novo dispositivo [List/dotnet/api/system.collections.generic.list-1) do [**tipo Dispositivo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) e povoar a lista com os dispositivos. São necessárias, no mínimo, as seguintes combinações de propriedades povoadas para a identificação de cada dispositivo:

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**Número de série**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  Chave de [**Produto**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)  +  [**Número de série**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).

- [**HardwareHash apenas.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)

- [**Apenas ProductKey.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)

- [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber)  +  [**Nome de OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername)  +  [**Nome modelo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).

Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes para recuperar uma interface para operações no cliente especificado. Em seguida, ligue para o método [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) com o identificador de lote do dispositivo para obter uma interface para as operações do lote especificado. Por fim, ligue para o método [**Dispositivos.Criar**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.create) ou Criar Como [**se é que a**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.createasync) lista de dispositivos para adicionar os dispositivos ao lote do dispositivo.

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

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: CreateDevices.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                            |
|----------|------------------------------------------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/deviceBatches/{devicebatch-id}/dispositivos HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de percurso e consulta ao criar o pedido.

| Nome           | Tipo   | Necessário | Descrição                                           |
|----------------|--------|----------|-------------------------------------------------------|
| id cliente    | string | Yes      | Uma cadeia formatada pelo GUID que identifica o cliente. |
| devicebatch-id | string | Yes      | Um identificador de cordas que identifica o lote do dispositivo. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

O corpo do pedido deve conter uma série de objetos [do Dispositivo.](device-deployment-resources.md#device) São aceites as seguintes combinações de campos para a identificação de um dispositivo:

- hardwareHash + produtoKey.
- hardwareHash + serialNumber.
- hardwareHash + produtoKey + serialNumber.
- hardwareHash apenas.
- produtoKey apenas.
- serialNumber + oemManufacturerName + modeloName.

### <a name="request-example"></a>Exemplo de pedido

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

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedida, a resposta contém um **cabeçalho de localização** que tem um URI que pode ser usado para recuperar o estado de upload do dispositivo. Guarde este URI para utilização com outras APIs de REST relacionadas.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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
