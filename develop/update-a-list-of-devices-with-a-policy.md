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
# <a name="update-a-list-of-devices-with-a-policy"></a>Atualizar uma lista de dispositivos com uma política

**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany

Como atualizar uma lista de dispositivos com uma política de configuração para o cliente especificado.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- O identificador de apólices.

- Os identificadores do dispositivo para atualizar.

## <a name="c"></a>C\#

Para atualizar uma lista de dispositivos com a política de configuração especificada, em primeiro lugar, instantânea a [List/dotnet/api/system.collections.generic.list-1) do tipo [KeyValuePair/dotnet/api/system.collections.generic.keyvaluepair-2)[**(PolicyCategory,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.policycategory)string) e adicionar a política a aplicar, como mostrado no seguinte código exemplo. Vai precisar do identificador de política da apólice.

Em seguida, crie uma lista de objetos do [**Dispositivo**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) a atualizar com a política, especificando o identificador do dispositivo e a lista que contém a política a aplicar, para cada dispositivo. Em seguida, instantânea um objeto [**DevicePolicyUpdateRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicepolicyupdaterequest) e definir a propriedade [**dispositivos**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) para a lista de objetos do dispositivo.

Para processar o pedido de atualização da política do dispositivo, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador do cliente para recuperar uma interface para operações no cliente especificado. Em seguida, recupere a propriedade [**DevicePolicy**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicepolicy) para obter uma interface para as operações de recolha de dispositivos do cliente. Por fim, ligue para o método [**'Actualização'**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.icustomerdevicecollection.update) com o objeto DevicePolicyUpdateRequest para atualizar os dispositivos com a política.

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

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: UpdateDevicesPolicy.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método    | URI do pedido                                                                                         |
|-----------|-----------------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/DevicePolicyUpdates HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de trajetória ao criar o pedido.

| Nome        | Tipo   | Necessário | Descrição                                           |
|-------------|--------|----------|-------------------------------------------------------|
| id cliente | string | Yes      | Uma cadeia formatada pelo GUID que identifica o cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

O corpo de pedido deve conter um recurso [DevicePolicyUpdateRequest.](device-deployment-resources.md#devicepolicyupdaterequest)

### <a name="request-example"></a>Exemplo de pedido

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

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedida, a resposta contém um **cabeçalho de localização** que tem um URI que pode ser usado para recuperar o estado deste processo de lote. Guarde este URI para utilização com outras APIs de REST relacionadas.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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
