---
title: Obter todas as informações de análise de utilização do Azure
description: Como obter toda a informação de análise de uso do Azure.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: c281dcdeb93771a69a388ad64e1127b24156c809
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769440"
---
# <a name="get-all-azure-usage-analytics-information"></a>Obter todas as informações de análise de utilização do Azure

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Como obter todas as informações de análise de uso da Azure para os seus clientes.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais do Utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido |
|---------|-------------|
| **Obter** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/usage/azure HTTP/1.1 |

### <a name="uri-parameters"></a>Parâmetros URI

|Parâmetro        |Tipo                        |Descrição               |
|:----------------|:---------------------------|:-------------------------|
|top              | string                     | O número de filas de dados a devolver no pedido. O valor máximo e o valor predefinido se não especificado for 10000. Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.                        |
|saltar             | int                        | O número de filas para saltar na consulta. Utilize este parâmetro para páginar através de grandes conjuntos de dados. Por exemplo, `top=10000 and skip=0` recupera as primeiras 10000 linhas de `top=10000 and skip=10000` dados, recupera as próximas 10000 linhas de dados, e assim por diante.                       |
|filter           | string                     | O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta. Cada declaração contém um campo e valor que estão associados aos `eq` `ne` ou operadores, e as declarações podem ser combinadas usando `and` ou `or` . Pode especificar as seguintes cordas:<br/><br/>                                                       `customerTenantId`<br/> `customerName`<br/> `subscriptionId`<br/> `subscriptionName`<br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/>**Exemplo:**<br/> `.../usage/azure?filter=meterCategory eq 'Data Management'`<br/><br/> **Exemplo:**<br/>`.../usage/azure?filter=meterCategory eq 'Data Management' or (usageDate le cast('2018-01-01', Edm.DateTimeOffset) and usageDate le cast('2018-04-01', Edm.DateTimeOffset))`                        |
|agregaçãoLevel | string                    | Especifica o intervalo de tempo para a recuperação de dados agregados. Pode ser uma das seguintes cordas: `day` `week` , ou `month` . Se não for especificado, o padrão é `day` .<br/><br/>                                              O `aggregationLevel` parâmetro não é suportado sem um `groupby` . O `aggregationLevel` parâmetro aplica-se a todos os campos de data presentes no `groupby` .                                                      |
|orderby          |string                     | Uma declaração que encomenda os valores de dados de resultados para cada instalação. A sintaxe é `...&orderby=field [order],field [order],...`. O `field` parâmetro pode ser uma das seguintes cordas:<br/><br/>                    `customerTenantId`<br/>`customerName`<br/>`subscriptionId`<br/>`subscriptionName`<br/>`usageDate`<br/>`resourceLocation`<br/>`meterCategory`<br/>`meterSubcategory`<br/>`meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/> O parâmetro *de encomenda* é opcional e pode ser `asc` ou `desc` especificar a ordem ascendente ou descendente para cada campo, respectivamente. A predefinição é `asc`.<br/><br/>**Exemplo:**<br/> `...&orderby=meterCategory,meterUnit`                                                                                           |
|groupby          |string                    | Uma declaração que aplica agregação de dados apenas aos campos especificados. Pode especificar os seguintes campos:<br/><br/>                                                                                                                     `customerTenantId`<br/>`customerName`<br/> `subscriptionId` <br/> `subscriptionName` <br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit` <br/> `reservationOrderId` <br/> `reservationId` <br/> `consumptionMeterId` <br/> `serviceType` <br/><br/>As linhas de dados devolvidas conterão os campos especificados no `groupby`  parâmetro, bem como a *Quantidade*.<br/><br/>O `groupby` parâmetro pode ser usado com o `aggregationLevel` parâmetro.<br/><br/>**Exemplo:**<br/>`...&groupby=meterCategory,meterUnit` |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/usage/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o corpo de resposta contém uma coleção de recursos de [uso Azure.](partner-center-analytics-resources.md#csp-program-azure-usage-analytics)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
{
  "customerTenantId": "39A1DFAC-4969-4F31-AF94-D76588189CFE",
  "customerName": "A",
  "subscriptionId": "EC649980-D623-49F5-B7C1-80CC772B83A8",
  "subscriptionName": "AZURE PURCHSE SAMPLE APP",
  "usageDate": "2018-05-27T00:00:00",
  "resourceLocation": "useast",
  "meterCategory": "Data Management",
  "meterSubcategory": "None",
  "meterUnit": "10,000s",
  "reservationOrderId": "",
  "reservationId": "",
  "consumptionMeterId": "",
  "serviceType": "",
  "quantity": 20
}
```

## <a name="see-also"></a>Ver também

- [Análise do Centro de Parceiros – Recursos](partner-center-analytics-resources.md)
