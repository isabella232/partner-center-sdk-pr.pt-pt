---
title: Obter dados de utilização da subscrição por medidor
description: Pode utilizar a recolha de recursos MeterUsageRecord para obter registos de utilização de medidores de um cliente para serviços ou recursos específicos da Azure durante o período de faturação em curso.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df981eae8d2caee2dcb7f36696725ec011ead75b
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769146"
---
# <a name="get-usage-data-for-subscription-by-meter"></a>Obter dados de utilização da subscrição por medidor

**Aplica-se a:**

- Partner Center
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Pode utilizar a recolha de recursos **MeterUsageRecord** para obter registos de utilização de medidores de um cliente para serviços ou recursos específicos da Azure durante o período de faturação em curso. Esta recolha de recursos representa um total agregado para cada metro para o ciclo de faturação atual, em todo o seu plano Azure.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de assinatura

*Esta nova rota é equivalente a `subscriptions/{subscription-id}/usagerecords/resources` , que continuará a funcionar apenas para as subscrições do Microsoft Azure (MS-AZR-0145P).* Esta nova rota irá suportar tanto as subscrições do Microsoft Azure (MS-AZR-0145P) como os planos Azure. Para obter esta informação para o seu plano Azure, você precisa mudar para esta nova rota. Além das propriedades mencionadas nas secções seguintes, a resposta é a mesma da rota antiga.

## <a name="c"></a>C\#

Para obter registos de utilização de medidores de um cliente para um serviço ou recurso Azure específico durante o período de faturação em curso:

1. Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**

2. Ligue para a propriedade Subscrições, e **UsageRecords,** em seguida, a propriedade **Meters.** Termine chamando os métodos Get() ou GetAsync().

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Meters.Get();
    ```

Por exemplo, consulte a seguinte amostra:

- Amostra: [App de teste de consola](console-test-app.md)
- Projeto: **PartnerSDK.FeatureSamples**
- Classe: **GetSubscriptionUsageRecordsByMeter.cs**

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                                             |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/meterusagerecords HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização classificadas do cliente.

| Nome                   | Tipo     | Necessário | Descrição                               |
|------------------------|----------|----------|-------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | Um GUID correspondente ao cliente.     |
| **id de subscrição**    | **guid** | Y        | Um GUID correspondente ao identificador de um recurso de [subscrição](subscription-resources.md#subscription)partner Center, que representa uma subscrição do Microsoft Azure (MS-AZR-0145P) ou um plano Azure. *Para os recursos de subscrição do plano Azure, forneça o **id de plano** como **id de subscrição** nesta rota.* |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um recurso **PagedResourceCollection \<MeterUsageRecord>** no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais. Para obter uma lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Exemplo de resposta para subscrições microsoft Azure (MS-AZR-0145P)

Neste exemplo, o cliente comprou **145P Azure PayG**.

*Para clientes com uma subscrição Microsoft Azure (MS-AZR-0145P), não haverá alteração na resposta da API.*

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 1,
    "items": [
        {
            "status": "active",
            "offerId": "MS-AZR-0145P",
            "resourceId": "11111111-F347-41B6-B02C-187B1B778A43",
            "id": "11111111-F347-41B6-B02C-187B1B778A43",
            "resourceName": "Microsoft Azure",
            "name": "Microsoft Azure",
            "totalCost": 22.861172,
            "currencyLocale": "fr-FR",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/{customer-tenant-id}/subscriptions/usagerecords/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a>Exemplo de resposta do REST para o plano Azure

Neste exemplo, o cliente comprou um plano Azure.

*Para clientes com planos Azure, existem as seguintes alterações na resposta da API:*

- **currencyLocale** é substituída por **moedaSCo**
- **usdTotalCost** é um novo campo

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Fri, 26 Feb 2016 20:31:45 GMT

{
    "totalCount": 4,
    "items": [
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNVX-005J-Data Transfer In (GB)",
            "meterName": "Data Transfer In",
            "category": "Bandwidth",
            "subcategory": "Bandwidth",
            "quantityUsed": 0.01129,
            "unit": "1 GB",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNVX-005J-Data Transfer Out (GB)",
            "meterName": "Data Transfer Out",
            "category": "Bandwidth",
            "subcategory": "Bandwidth",
            "quantityUsed": 0.000224,
            "unit": "1 GB",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNZ5-006G-10K Batch Write Operations",
            "meterName": "Batch Write Operations",
            "category": "Storage",
            "subcategory": "Tables",
            "quantityUsed": 0.2462,
            "unit": "10K",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNZ5-006G-Data Stored (GB/Month)",
            "meterName": "LRS Data Stored",
            "category": "Storage",
            "subcategory": "Tables",
            "quantityUsed": 0.002632,
            "unit": "1 GB/Month",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/meterusagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
