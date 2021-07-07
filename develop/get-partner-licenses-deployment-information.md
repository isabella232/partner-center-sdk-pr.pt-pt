---
title: Obter informações de implementação de licenças do parceiro
description: Como obter licenças de parceiros de informação agregada para incluir todos os clientes.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2464242fc6dc4e7464511eac5d4197630e22fac0
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445989"
---
# <a name="get-partner-licenses-deployment-information"></a>Obter informações de implementação de licenças do parceiro

Como obter licenças de parceiros de informação agregada para incluir todos os clientes.

> [!NOTE]
> Este cenário é substituído pela [Obter informações de implementação de licenças](get-licenses-deployment-information.md).

## <a name="prerequisites"></a>Pré-requisitos

Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com credenciais app+utilizador.

## <a name="c"></a>C\#

Para obter dados agregados na implementação de licenças, primeiro obtenha uma interface para operações de recolha de análise de nível de parceiro a partir da propriedade [**IAggregatePartner.Analytics.**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) Em seguida, recupere uma interface para o nível de parceiro licenças de recolha de análise a partir da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) Por fim, ligue para o método [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) para obter os dados agregados sobre a implementação de licenças. Se o método for bem sucedido, obterá uma coleção de [**objetos PartnerLicensesDeploymentInsights.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesdeploymentinsights)

``` csharp
// IAggregatePartner partnerOperations;

var partnerLicensesDeploymentAnalytics = partnerOperations.Analytics.Licenses.Deployment.Get();
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                           |
|---------|---------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/deployment HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/analytics/licenses/deployment HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 25b6edd5-1f53-456b-b48c-c64f60ec2dda
MS-CorrelationId: 6492b9d6-5629-429b-934c-040b1946e760
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma coleção de [recursos PartnerLicensesDeploymentInsights](analytics-resources.md#partnerlicensesdeploymentinsights) que fornecem informações sobre as licenças implementadas.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 487
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 6492b9d6-5629-429b-934c-040b1946e760
MS-RequestId: 25b6edd5-1f53-456b-b48c-c64f60ec2dda
MS-CV: f0trvmq8mEScHcFS.0
MS-ServerId: 102030524
Date: Tue, 14 Mar 2017 17:55:01 GMT

{
    "totalCount": 2,
    "items": [{
            "proratedDeploymentPercent": 0.0,
            "licensesSold": 343,
            "processedDateTime": "2017-03-10T00:00:00+00:00",
            "serviceName": "crm",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesDeploymentInsights"
            }
        }, {
            "proratedDeploymentPercent": 1.0,
            "licensesSold": 4464,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesDeploymentInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
