---
title: Obter informações de implementação de licenças
description: Como obter informações de implementação para licenças Office e Dinâmica.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c47ab4f839c102c7a7bcab0169bf13955ab49beb97c48800e882598714347e67
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115990720"
---
# <a name="get-licenses-deployment-information"></a>Obter informações de implementação de licenças

Como obter informações de implementação para licenças Office e Dinâmica.

## <a name="prerequisites"></a>Pré-requisitos

Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com credenciais app+utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                     |
|---------|-------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/deployment/license/ HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="uri-parameters"></a>Parâmetros URI

| Parâmetro         | Tipo     | Descrição | Obrigatório |
|-------------------|----------|-------------|----------|
| top               | string   | O número de filas de dados a devolver no pedido. O valor máximo e o valor predefinido se não especificado for 10000. Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados. | No |
| saltar              | int      | O número de filas para saltar na consulta. Utilize este parâmetro para páginar através de grandes conjuntos de dados. Por exemplo, top=10000 e skip=0 recupera as primeiras 10000 linhas de dados, top=10000 e skip=10000 recupera as próximas 10000 linhas de dados, e assim por diante. | No |
| filter            | string   | O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta. Cada declaração contém um campo e valor que estão associados aos `eq` `ne` ou operadores, e as declarações podem ser combinadas usando `and` ou `or` . Aqui estão alguns parâmetros *de filtragem* de exemplo:<br/><br/> *filter=serviceCode eq 'O365'*<br/> *filter=serviceCode eq 'O365'* ou *(canal eq 'Revendedor'*)<br/><br/> Pode especificar os seguintes campos:<br/><br/>**serviceCode**<br/>**nome de serviço**<br/>**canal**<br/>**customerTenantId**<br/>**nome do cliente**<br/>**productId**<br/>**produtoName**  | No |
| groupby           | string   | Uma declaração que aplica agregação de dados apenas aos campos especificados. Pode especificar os seguintes campos:<br/><br/>**serviceCode**<br/>**nome de serviço**<br/>**canal**<br/>**customerTenantId**<br/>**nome do cliente**<br/>**productId**<br/>**produtoName**<br/><br/> As linhas de dados devolvidas conterão os campos especificados no parâmetro *groupby* e os seguintes:<br/><br/>**licençasDeployed**<br/>**licençasSold**  | No |
| processadoDadade tempo | DateTime | Pode-se especificar a data a partir da qual os dados de utilização foram tratados. Incumprimentos até à data mais recente quando os dados foram tratados | No |

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/deployment/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém os seguintes campos contendo dados sobre as licenças implementadas.

| Campo             | Tipo     | Description                           |
|-------------------|----------|---------------------------------------|
| serviceCode       | string   | Código de serviço                          |
| nome de serviço       | string   | Nome do serviço                          |
| canal           | string   | Nome do canal, revendedor                |
| customerTenantId  | string   | Identificador único para o cliente    |
| nome do cliente      | string   | Nome do cliente                         |
| productId         | string   | Identificador único para o produto     |
| produtoName       | string   | Nome do produto                          |
| licençasDeployed  | long     | Número de licenças implantadas           |
| licençasSold      | long     | Número de licenças vendidas               |
| processadoDadade tempo | DateTime | Data em que os dados foram processados pela última vez |

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
      "serviceCode": "crm",
      "serviceName": "Microsoft Dynamics",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "54B84594-9C77-4499-8D65-5E0D5F410E78",
      "productName": "DYNAMICS AX TASK",
      "licensesDeployed": 0,
      "licensesSold": 9
    },
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "D3B4FE1F-9992-4930-8ACB-CA6EC609365E",
      "productName": "DOMESTIC AND INTERNATIONAL CALLING PLAN",
      "licensesDeployed": 0,
      "licensesSold": 5
    }
],
  "@nextLink": null,
  "TotalCount": 2
}
```
