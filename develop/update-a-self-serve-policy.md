---
title: Atualizar uma política de autosserviço
description: Como atualizar uma política de autosserviço.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4d53ab8e5b8ef5b7be83360a3f43ec7791b2e3b4
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2020
ms.locfileid: "97770248"
---
# <a name="update-a-selfservepolicy"></a>Atualizar uma AutoServePolicy

**Aplica-se a:**

- Partner Center

Este tópico explica como atualizar uma política de autosserviço.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com credenciais de Aplicação+Utilizador.

## <a name="c"></a>C\#

Para eliminar uma política de autosserviço:

1. Ligue para o método [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) com o identificador de entidade para recuperar uma interface para operações nas políticas.

2. Ligue para o método [**Put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) ou [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) para atualizar a política de autosserviço.

``` csharp
// IAggregatePartner partnerOperations;
SelfServePolicy policy;

// All the operations executed on this partner operation instance will share the same correlation identifier but will differ in request identifier
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// updates the self-serve policies
partnerOperations.SelfServePolicies.ById(policy.id).Put(policy);
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                       |
|----------|-------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

- É necessário um identificador de pedido e um identificador de correlação.
- Consulte [os cabeçalhos REST do Partner Center](headers.md) para obter mais informações.

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades necessárias no corpo de pedido.

| Nome                              | Tipo   | Descrição                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [AutoServePolicy](self-serve-policy-resources.md#selfservepolicy)| objeto | A informação política de autosserviço. |

#### <a name="selfservepolicy"></a>AutoServePolicy

Esta tabela descreve os campos mínimos exigidos do recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) necessário para criar uma nova política de autosserviço.

| Propriedade              | Tipo             | Descrição                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| ID                    | string           | Um identificador de política de autosserviço que é fornecido após a criação bem sucedida da política de autosserviço.     |
| SelfServeEntity       | SelfServeEntity  | A entidade self-serve a quem está a ser concedido acesso.                                                     |
| Grantor               | Grantor          | O concededor que está a conceder acesso.                                                                    |
| Permissões           | Matriz de Permissão| Um conjunto de recursos [de permissão.](self-serve-policy-resources.md#permission)                                                      |
| Etag                  | string           | O Etag.                                                                                               |


### <a name="request-example"></a>Exemplo de pedido

```http
PUT https://api.partnercenter.microsoft.com/v1/SelfServePolicy HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive

{
    "id": "634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415",
    "selfServeEntity": {
        "selfServeEntityType": "customer",
        "tenantID": "0431a72c-7d8a-4393-b25e-ef63f5efb415"
    },
    "grantor": {
        "grantorType": "billToPartner",
        "tenantID": "634f6379-ad54-449b-9821-564f737158ab"
    },
    "permissions": [{
        "resource": "AzureReservedInstances",
        "action": "Purchase"
    }],
    "attributes": {
        "etag": "\"933523d1-3f63-4fc3-8789-5e21c02cdaed\"",
        "objectType": "SelfServePolicy"
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, esta API devolve um recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) para a política de autosserviço atualizada.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

Este método devolve os seguintes códigos de erro:

| Código de Estado HTTP     | Código de erro   | Descrição                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| 404                  | 600039       | A política de autosserviço não foi encontrada                                            |
| 404                  | 600040       | O identificador de política de autosserviço está incorreto                                  |


### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 Ok
Content-Length: 834
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

{
    "id": "634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415",
    "selfServeEntity": {
        "selfServeEntityType": "customer",
        "tenantID": "0431a72c-7d8a-4393-b25e-ef63f5efb415"
    },
    "grantor": {
        "grantorType": "billToPartner",
        "tenantID": "634f6379-ad54-449b-9821-564f737158ab"
    },
    "permissions": [{
        "resource": "AzureReservedInstances",
        "action": "Purchase"
    }],
    "attributes": {
        "etag": "\"1ec98034-a249-46f4-b9dd-9cd464fb5e47\"",
        "objectType": "SelfServePolicy"
    }
}
```
