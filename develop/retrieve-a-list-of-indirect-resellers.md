---
title: Obter uma lista de revendedores indiretos
description: Como recuperar uma lista dos revendedores indiretos do parceiro inscrito.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 58f5c3378b5b941fdc9dafcf28f5efbc58c29c7c
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446569"
---
# <a name="retrieve-a-list-of-indirect-resellers"></a>Obter uma lista de revendedores indiretos

Como recuperar uma lista dos revendedores indiretos do parceiro inscrito.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

## <a name="c"></a>C\#

Para recuperar uma lista de revendedores indiretos com quem o parceiro inscrito tem uma relação, primeiro obter uma interface para operações de recolha de relacionamentos a partir da propriedade [**partnerOperations.Relationships.**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) Em seguida, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.get) or [**Get \_ Async,**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.getasync) passando um membro da enumeração [**PartnerRelationshipType**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype) para identificar o tipo de relacionamento. Para recuperar revendedores indiretos, tem de utilizar o IsIndirectCloudSolutionProviderOf.

``` csharp
// IAggregatePartner partnerOperations;

var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);
```

**Amostra**: [Aplicativo de teste de consola](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetIndirectResellers.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/relationships?relationship \_ type=IsIndirectCloudSolutionProviderOf HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para identificar o tipo de relacionamento.

| Nome               | Tipo    | Necessário  | Descrição                         |
|--------------------|---------|-----------|-------------------------------------|
| relationship_type  | string  | Yes       | O valor é a representação de uma das cordas encontradas no [PartnerRelationshipType](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype).<br/><br/> Se o parceiro estiver inscrito como fornecedor e pretender obter uma lista dos revendedores indiretos com quem estabeleceram uma relação, utilize o IsIndirectCloudSolutionProviderOf.<br/><br/> Se o parceiro for inscrito como revendedor e pretender obter uma lista dos fornecedores indiretos com quem estabeleceram uma relação, utilize o IsIndirectResellerOf.    |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/relationships?relationship_type=IsIndirectCloudSolutionProviderOf HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 144391a4-fb06-41ae-b684-3308ce4706bd
MS-CorrelationId: 72524ef8-81aa-4141-a049-45a4fece5d84
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [partnerRelationship](relationships-resources.md) para identificar os revendedores.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 298
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 72524ef8-81aa-4141-a049-45a4fece5d84
MS-RequestId: 144391a4-fb06-41ae-b684-3308ce4706bd
MS-CV: b21Ll1miM0yFMPQQ.0
MS-ServerId: 030020643
Date: Wed, 05 Apr 2017 21:08:44 GMT

{
    "totalCount": 2,
    "items": [{
            "id": "484e548c-f5f3-4528-93a9-c16c6373cb59",
            "name": "First Up Consultants",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "state": "Active",
            "mpnId": "4847383",
            "location": "US",
            "attributes": {
                "objectType": "PartnerRelationship"
            }
        }, {
            "id": "b01b1487-b36e-4e6d-9b5e-0b58974c4b28",
            "name": "ReleCloud",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "state": "Active",
            "mpnId": "4847433",
            "location": "BR",
            "attributes": {
                "objectType": "PartnerRelationship"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```