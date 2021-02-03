---
title: Atualizar uma política de configuração para o cliente especificado
description: Como atualizar a política de configuração especificada para o cliente especificado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 42c57a92020723415b4621e9f9d7c5c3278bfb77
ms.sourcegitcommit: 970031473b2e8cd3d08c6c097949c057a51df3ef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505344"
---
# <a name="update-a-configuration-policy-for-the-specified-customer"></a>Atualizar uma política de configuração para o cliente especificado

**Aplica-se a**

- Partner Center
- Centro de Parceiros para Microsoft Cloud Germany

Como atualizar a política de configuração especificada para o cliente especificado.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- O identificador de apólices.

## <a name="c"></a>C\#

Para atualizar uma política de configuração existente para o cliente especificado, instantânea um novo objeto [**ConfigurationPolicy,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) tal como mostrado no seguinte corte de código. Os valores deste novo objeto substituem os valores correspondentes no objeto existente. Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado. Em seguida, ligue para o método [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) com o ID da política para recuperar uma interface para configurar operações de política para a política especificada. Por fim, ligue para o método [**Patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) ou [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) para atualizar a política de configuração.

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

**Amostra**: [App de teste de consola](console-test-app.md). **Projeto**: Partner Center SDK Samples **Class**: UpdateConfigurationPolicy.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/policies/{policy-id} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de trajetória ao criar o pedido.

| Nome        | Tipo   | Necessário | Descrição                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| id cliente | string | Sim      | Uma cadeia formatada pelo GUID que identifica o cliente.         |
| id de política   | string | Sim      | Uma cadeia formatada por GUID que identifica a política de atualização. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

O organismo de pedido deve conter um objeto que forneça a informação da apólice.

| Nome            | Tipo             | Necessário | Updatable | Descrição                                                                                                                                              |
|-----------------|------------------|----------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID              | string           | Sim      | Não        | A cadeia formatada pelo GUID que identifica a política.                                                                                                    |
| name            | string           | Sim      | Sim       | O nome amigável da apólice.                                                                                                                         |
| categoria        | string           | Sim      | Não        | A categoria política.                                                                                                                                     |
| descrição     | cadeia (de carateres)           | No       | Sim       | A descrição da apólice.                                                                                                                                  |
| dispositivosAssed | número           | Não       | Não        | O número de dispositivos.                                                                                                                                   |
| policySettings  | matriz de cadeias (de carateres) | Sim      | Sim       | As definições de política: "nenhum", "remover \_ oem \_ pré-instalações", "utilizador oobe \_ não administrador \_ \_ \_ local", "saltar \_ as \_ definições expressas", "saltar \_ o registo de \_ oem", "saltar \_ eula". |

### <a name="request-example"></a>Exemplo de pedido

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

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém o recurso [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) para a nova política.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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
