---
title: Obtenha resumo de utilização para a subscrição do cliente
description: Pode utilizar o recurso SubscriptionUsageSummary para obter um resumo de utilização por subscrição de um serviço ou recurso Azure específico durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df7757807256fee8326969011f4d038c981c07362ee354ef929e592a7931a728
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115992777"
---
# <a name="get-usage-summary-for-customers-subscription"></a>Obtenha resumo de utilização para a subscrição do cliente

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Pode utilizar o recurso **SubscriptionUsageSummary** para obter um resumo de utilização de subscrição para um cliente. Este recurso representa o resumo de utilização da subscrição de um serviço ou recurso Azure específico durante o período de faturação atual.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um identificador de assinatura

## <a name="c"></a>C\#

Para obter um resumo de utilização de subscrição para a subscrição de um cliente:

1. Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**

2. Em seguida, ligue para a propriedade Subscrições e para a propriedade **UsageSummary.** Termine chamando os métodos Get() ou GetAsync().

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var subscriptionUsageSummary = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageSummary.Get();
    ```

Por exemplo, consulte o seguinte:

- Amostra: [App de teste de consola](console-test-app.md)
- Project: **PartnerSDK.FeatureSamples**
- Classe: **GetSubscriptionUsageSummary.cs**

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/usagesummary HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização classificadas do cliente.

| Nome                   | Tipo     | Necessário | Descrição                               |
|------------------------|----------|----------|-------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | Um GUID correspondente ao cliente.     |
| **id de subscrição**    | **guid** | Y        | Um GUID correspondente ao identificador de uma subscrição. Para um plano Azure, este é o identificador do recurso de [subscrição](subscription-resources.md#subscription)correspondente do Partner Center, que representa o plano Azure. *Para os recursos de subscrição do plano Azure, forneça o **id de plano** como **id de subscrição** nesta rota.* |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um **recurso SubscriptionUsageSummary** no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais. Para obter uma lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Exemplo de resposta para subscrições Microsoft Azure (MS-AZR-0145P)

Neste exemplo, o cliente comprou uma oferta **de 145P Azure PayG.**

*Para clientes com assinaturas Microsoft Azure (MS-AZR-0145P), não haverá alteração da resposta da API.*

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "resourceId": "ABCDEFGH-F347-41B6-B02C-187B1B778A43",
    "id": "ABCDEFGH-F347-41B6-B02C-187B1B778A43",
    "resourceName": "Microsoft Azure",
    "name": "Microsoft Azure",
    "billingStartDate": "2019-08-28T00:00:00-07:00",
    "billingEndDate": "2019-09-27T00:00:00-07:00",
    "totalCost": 22.861172,
    "currencyLocale": "fr-FR",
    "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SubscriptionUsageSummary"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a>Exemplo de resposta do REST para o plano Azure

Neste exemplo, o cliente comprou um plano Azure.

*Para clientes com planos Azure, existem as seguintes alterações de resposta da API:*

- **currencyLocale** é substituída por **moedaSCo**
- **usdTotalCost** é um novo campo

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac1
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "resourceId": "11111111-dca5-6f31-d3a6-dbbfad9be0fc",
    "resourceName": "Azure plan",
    "billingStartDate": "2019-09-01T00:00:00+00:00",
    "billingEndDate": "2019-10-01T00:00:00+00:00",
    "totalCost": 28.82860766744404945074,
    "currencyCode": "GBP",
    "usdTotalCost": 35.23000000000000362337,
    "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SubscriptionUsageSummary"
    }
}
```
