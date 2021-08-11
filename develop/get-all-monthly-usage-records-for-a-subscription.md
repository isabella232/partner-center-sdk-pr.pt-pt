---
title: Obter todos os registos de utilização mensal de uma subscrição
description: Pode utilizar a coleção de recursos AzureResourceMonthlyUsageRecord para obter uma lista de serviços dentro da subscrição de um cliente e as suas informações de utilização cotadas associadas.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 62cbca9fada5e6935aea647e76097eb73bb3f8f3a5f355f4b43a64e21831070b
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994001"
---
# <a name="get-all-monthly-usage-records-for-a-subscription"></a>Obter todos os registos de utilização mensal de uma subscrição

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Pode utilizar a coleção de recursos [**AzureResourceMonthlyUsageRecord**](/dotnet/api/microsoft.store.partnercenter.models.usage.azureresourcemonthlyusagerecord) para obter uma lista de serviços dentro da subscrição de um cliente e as suas informações de utilização cotadas associadas.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um identificador de assinatura.

*Esta API suporta apenas Microsoft Azure subscrições (MS-AZR-0145P). Se estiver a utilizar um plano Azure, consulte [obter dados de utilização para subscrição por contador.](get-a-customer-subscription-meter-usage-records.md)*

## <a name="c"></a>C\#

Para obter as informações de utilização de recursos de uma subscrição:

1. Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**

2. Ligue para a propriedade **Subscrições,** e **UsageRecords,** em seguida, a propriedade **Recursos.**
3. Ligue para os **métodos Get()** ou **GetAsync().**

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// var selectedSubscriptionID as string;

var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Resources.Get();
```

Por exemplo, consulte o seguinte:

- Amostra: [App de teste de consola](console-test-app.md)
- Project: **PartnerSDK.FeatureSample**
- Classe: **SubscriptionResourceUsageRecords.cs**

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                                                       |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-subscription}/usagerecords/resources HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização nominal.

| Nome                    | Tipo     | Necessário | Descrição                               |
|-------------------------|----------|----------|-------------------------------------------|
| **cliente-inquilino-id**  | **guid** | Y        | Um GUID correspondente ao cliente.     |
| **id de subscrição** | **guid** | Y        | Um GUID correspondente à subscrição. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/usagerecords/resources HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 65b26053-37d0-4303-9fd1-46ad8012bcb6
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma coleção de recursos **AzureResourceMonthlyUsageRecord** no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 12014
Content-Type: application/json
MS-CorrelationId: 648a26a4-a63e-459f-844b-4f29d7913353
MS-RequestId: be82a8ba-4a53-49f7-8313-b033c058687e
Date: Tue, 10 Nov 2015 19:09:59 GMT

{
    "totalCount":20,
    "items":[{
        "category":"Storage",
        "subcategory":"LOCALLY REDUNDANT",
        "quantityUsed":0.151287527825352,
        "unit":"GB",
        "id":"2a2419c0-cefe-46b2-8004-8eb002ad606c",
        "name":"Azure Resource 1",
        "totalCost":0.195779159290613,
        "currencyLocale":"en-US",
        "attributes":{
            "objectType":"AzureResourceMonthlyUsageRecord"
        }
    },
    {
        "category":"Remote App",
        "subcategory":"Remote App",
        "quantityUsed":0.932546524299563,
        "unit":"GB",
        "id":"7e4099c8-2b3d-41a6-a1bd-d5cf315989b2",
        "name":"Azure Resource 2",
        "totalCost":0.920983775016379,
        "currencyLocale":"en-US",
        "attributes":{
            "objectType":"AzureResourceMonthlyUsageRecord"
        }
    }],
    "links":{
        "self":{
            "uri":"/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription>%20/usagerecords",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"Collection"
    }
}
```
