---
title: Obtenha um resumo de utilização para um parceiro
description: Pode utilizar o recurso PartnerUsageSummary para obter um resumo de utilização do parceiro de todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: e82c2220768b211b37fad4bbc675e347a25a59217aa881f4e4db2e4d586eb354
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993627"
---
# <a name="get-a-usage-summary-for-a-partner"></a>Obtenha um resumo de utilização para um parceiro

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Pode utilizar o recurso **PartnerUsageSummary** para obter um resumo de utilização do parceiro de todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação atual.

*O total devolvido por esta API não devolverá o consumo aos clientes que tenham um plano Azure.* Planejado para a depreciação no futuro.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

## <a name="c"></a>C\#

Para obter um resumo de utilização para todos os clientes que adquiriram um serviço ou recurso Azure específico durante o período de faturação em curso:

1. Utilize o seu **IAggregatePartner**.

2. Ligue para a propriedade **UsageSummary,** seguida dos métodos **Get()** ou **GetAsync():**

    ``` csharp
    // IAggregatePartner partnerOperations;

    var usageSummary = partnerOperations.UsageSummary.Get();
    ```

Por exemplo, consulte o seguinte:

- Amostra: [App de teste de consola](console-test-app.md)
- Project: **PartnerSDK.FeatureSamples**
- Classe: **GetPartnerUsageSummary.cs**

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                         |
|---------|---------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um recurso **PartnerUsageSummary** no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais. Para obter uma lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "customersOverBudget": 1,
    "customersTrendingOver": 0,
    "customersWithUsageBasedSubscription": 11,
    "resourceId": "11111111-4574-4539-bc42-0e539b9684c0",
    "id": "11111111-4574-4539-bc42-0e539b9684c0",
    "resourceName": "PLAMUATT2NETNEW",
    "name": "PLAMUATT2NETNEW",
    "billingStartDate": "2019-08-28T00:00:00-07:00",
    "billingEndDate": "2019-09-27T00:00:00-07:00",
    "totalCost": 22.861172,
    "currencyLocale": "fr-FR",
    "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
    "links": {
        "self": {
            "uri": "/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "PartnerUsageSummary"
    }
}
```
