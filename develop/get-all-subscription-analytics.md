---
title: Obter todas as informações de análise de subscrições
description: Como obter todas as informações de análise de subscrição.
ms.date: 08/02/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: e1f16c92569a02bc51c96a85ecb642fbeb76a9a7
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760254"
---
# <a name="get-all-subscription-analytics-information"></a>Obter todas as informações de análise de subscrições

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Este artigo descreve como obter todas as informações de análise de subscrição para os seus clientes.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais do Utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido |
|--------|-------------|
| **Obter** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscrições HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

O quadro que se segue enumera os parâmetros opcionais e as suas descrições:

| Parâmetro | Tipo |  Description |
|-----------|------|--------------|
| top | int | O número de filas de dados a devolver no pedido. Se o valor não for especificado, o valor máximo e o valor predefinido são `10000` . Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados. |
| saltar | int | O número de filas para saltar na consulta. Utilize este parâmetro para páginar através de grandes conjuntos de dados. Por exemplo, `top=10000` e `skip=0` recupera as primeiras 10000 linhas de dados, `top=10000` e recupera as `skip=10000` próximas 10000 linhas de dados. |
| filter | string | Uma ou mais declarações que filtram as linhas na resposta. Cada declaração de filtro contém um nome de campo do corpo de resposta e um valor que está associado ao **`eq`** , ou para certos **`ne`** campos, o **`contains`** operador. As declarações podem ser combinadas utilizando **`and`** ou **`or`** . Os valores das cordas devem ser rodeados por citações únicas no parâmetro do **filtro.** Consulte a secção seguinte para obter uma lista de campos que podem ser filtrados e os operadores que são apoiados nesses campos. |
| agregaçãoLevel | string | Especifica o intervalo de tempo para a recuperação de dados agregados. Pode ser uma das seguintes cordas: **dia,** **semana,** **ou mês.** Se o valor não for especificado, o padrão é **dataRange**. Este parâmetro só se aplica quando um campo de data é passado como parte do parâmetro **groupBy.** |
| grupoBy | string | Uma declaração que aplica agregação de dados apenas aos campos especificados. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [**Subscrição.**](partner-center-analytics-resources.md#subscription-resource)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
{
    "customerTenantId": "76906668-27FC-4F5B-A35C-75A9823E13AF",
    "customerName": "TESTORG65656565",
    "customerMarket": "US",
    "id": "4BF546B2-8998-4838-BEE2-5F1BBE65A04F",
    "status": "ACTIVE",
    "productName": "OFFICE 365 BUSINESS PREMIUM",
    "subscriptionType": "Office",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "FULL OFFICE SUITE",
    "partnerName": "Partner Name",
    "providerName": "Provider Name",
    "creationDate": "2016-02-04T19:29:38.037",
   "effectiveStartDate": "2016-02-04T00:00:00",
    "commitmentEndDate": "2019-02-10T00:00:00",
    "currentStateEndDate": "2019-02-10T00:00:00",
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": "2018-02-10T02:39:57.729",
    "licenseCount": 2,
    "churnRisk": "High",
    "billingCycleName": "MONTHLY"

}
```

## <a name="see-also"></a>Ver também

- [Análise do Centro de Parceiros – Recursos](partner-center-analytics-resources.md)
