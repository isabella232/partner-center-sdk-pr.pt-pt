---
title: Obter informações de utilização de licenças
description: Como obter informações de utilização de licenças ao nível da carga de trabalho para Office and Dynamics.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a144fd078a36289e4a2c70880817b1f0ca627e8a
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769428"
---
# <a name="get-licenses-usage-information"></a>Obter informações de utilização de licenças

**Aplica-se a**

- Partner Center

Como obter informações de utilização de licenças ao nível da carga de trabalho para Office and Dynamics.

## <a name="prerequisites"></a>Pré-requisitos

Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com credenciais app+utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                |
|---------|--------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/usage/license/ HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="uri-parameters"></a>Parâmetros URI

| Parâmetro         | Tipo     | Descrição | Obrigatório |
|-------------------|----------|-------------|----------|
| top               | string   | O número de filas de dados a devolver no pedido. O valor máximo e o valor predefinido se não especificado for 10000. Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados. | Não |
| saltar              | int      | O número de filas para saltar na consulta. Utilize este parâmetro para páginar através de grandes conjuntos de dados. Por exemplo, top=10000 e skip=0 recupera as primeiras 10000 linhas de dados, top=10000 e skip=10000 recupera as próximas 10000 linhas de dados, e assim por diante. | Não |
| filter            | string   | O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta. Cada declaração contém um campo e valor que estão associados aos **`eq`** **`ne`** ou operadores, e as declarações podem ser combinadas usando **`and`** ou **`or`** . Aqui estão alguns parâmetros *de filtragem* de exemplo:<br/><br/>*filter=workloadCode eq 'SFB'*<br/><br/>*filter=workloadCode eq 'SFB'* ou *(canal eq 'Revendedor'*)<br/><br/>Pode especificar os seguintes campos:<br/><br/>**código de carga de trabalho**<br/>**carga de trabalhoName**<br/>**serviceCode**<br/>**nome de serviço**<br/>**canal**<br/>**customerTenantId**<br/>**nome do cliente**<br/>**productId**<br/>**produtoName** | Não |
| groupby           | string   | Uma declaração que aplica agregação de dados apenas aos campos especificados. Pode especificar os seguintes campos:<br/><br/>**código de carga de trabalho**<br/>**carga de trabalhoName**<br/>**serviceCode**<br/>**nome de serviço**<br/>**channelcustomerTenantId**<br/>**nome do cliente**<br/>**productId**<br/>**produtoName**<br/><br/>As linhas de dados devolvidas conterão os campos especificados no parâmetro *groupby,* bem como os seguintes:<br/><br/>**licençasActivar**<br/>**licençasQualizado** | Não |
| processadoDadade tempo | DateTime | Pode-se especificar a data a partir da qual os dados de utilização foram tratados. Incumprimentos até à data mais recente quando os dados foram tratados | Não |

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/usage/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém os seguintes campos que contêm dados sobre a utilização das licenças.

| Campo             | Tipo     | Descrição                                   |
|-------------------|----------|-----------------------------------------------|
| código de carga de trabalho      | string   | Código de carga de trabalho                                 |
| carga de trabalhoName      | string   | Nome da carga de trabalho                                 |
| serviceCode       | string   | Código de serviço                                  |
| nome de serviço       | string   | Nome do serviço                                  |
| canal           | string   | Nome do canal, revendedor                        |
| customerTenantId  | string   | Identificador único para o cliente            |
| nome do cliente      | string   | Nome do cliente                                 |
| productId         | string   | Identificador único para o produto             |
| produtoName       | string   | Nome do produto                                  |
| licençasActivar    | long     | Número de licenças ativas por carga de trabalho        |
| licençasQualizado | long     | Número de licenças qualificadas para a carga de trabalho |
| processadoDadade tempo | DateTime | Data em que os dados foram processados pela última vez         |

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 487
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CV: f0trvmq8mEScHcFS.0
MS-ServerId: 4
Date: Wed, 24 Oct 2018 22:37:18 GMT

{
"Value": [
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "workloadCode": "SPO",
      "workloadName": "SharePoint",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "6FD2C87F-B296-42F0-B197-1E91E994B900",
      "productName": "OFFICE 365 ENTERPRISE E3",
      "licenseActive": 0,
      "licensesQualified": 1
    },
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "workloadCode": "EXO",
      "workloadName": "Exchange",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "45A2423B-E884-448D-A831-D9E139C52D2F",
      "productName": "EXCHANGE ONLINE PROTECTION",
      "licenseActive": 0,
      "licensesQualified": 1
    }
}
```
