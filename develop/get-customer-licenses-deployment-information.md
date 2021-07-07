---
title: Obter informações de implementação de licenças do cliente
description: Como obter insights de implementação de licenças para um cliente específico.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 91fe9da185aa59025d4dc8263257b207edb4a5be
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446467"
---
# <a name="get-customer-licenses-deployment-information"></a>Obter informações de implementação de licenças do cliente

Como obter insights de implementação de licenças para um cliente específico.

> [!NOTE]
> Este cenário é substituído pela [Obter informações de implementação de licenças](get-licenses-deployment-information.md).

## <a name="prerequisites"></a>Pré-requisitos

Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com credenciais app+utilizador.

## <a name="c"></a>C\#

Para obter dados agregados sobre a implementação de um cliente especificado, ligue primeiro para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente. Em seguida, obtenha uma interface para operações de recolha de análise ao nível do cliente a partir da propriedade [**Analytics.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics) Em seguida, recupere uma interface para a recolha de análise de licenças de nível de cliente da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses) Por fim, ligue para o método [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) para obter os dados agregados sobre a implementação de licenças. Se o método for bem sucedido, obterá uma coleção de [**objetos CustomerLicensesDeploymentInsights.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesdeploymentinsights)

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

var customerLicensesDeploymentAnalytics = partnerOperations.Customers.ById(customerIdToRetrieve).Analytics.Licenses.Deployment.Get();
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/analytics/licenses/deployment HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de percurso para identificar o cliente.

| Nome        | Tipo | Necessário | Descrição                                                |
|-------------|------|----------|------------------------------------------------------------|
| id cliente | guid | Yes      | Um id de cliente formatado GUID que identifica o cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/analytics/licenses/deployment HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b01b8759-4dbe-4605-adb7-e5839a796c33
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma coleção de [recursos CustomerLicensesDeploymentInsights](analytics-resources.md#customerlicensesdeploymentinsights) que fornecem informações sobre as licenças implementadas.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 1012
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
MS-RequestId: b01b8759-4dbe-4605-adb7-e5839a796c33
MS-CV: deEp2Wy6DUitMCYA.0
MS-ServerId: 102030524
Date: Wed, 15 Mar 2017 01:19:18 GMT

{
    "totalCount": 3,
    "items": [{
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "OFFICE 365 BUSINESS ESSENTIALS",
            "licensesDeployed": 0,
            "deploymentPercent": 0.0,
            "licensesSold": 1,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesDeploymentInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE (PLAN 1)",
            "licensesDeployed": 0,
            "deploymentPercent": 0.0,
            "licensesSold": 5,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesDeploymentInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE ARCHIVING FOR EXCHANGE ONLINE",
            "licensesDeployed": 0,
            "deploymentPercent": 0.0,
            "licensesSold": 2,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesDeploymentInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
