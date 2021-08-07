---
title: Obtenha uma política de autosserviço por ID
description: Obtém a política de autosserviço especificada utilizando o seu ID.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 7ad763dd6d586a58b73d0a3abb2b2fc399a0f35e7b842f5d1dd2e4c5006c3b30
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989751"
---
# <a name="get-a-self-serve-policy-by-id"></a>Obtenha uma política de autosserviço por ID

Obtém a política de autosserviço especificada utilizando o seu ID.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com credenciais app+utilizador.
- Uma identificação de política de autosserviço.

## <a name="examples"></a>Exemplos


## <a name="span-idrest_requestspan-idrest_requestspan-idrest_requestrest-request"></a><span id="REST_Request"/><span id="rest_request"/><span id="REST_REQUEST"/>Pedido de DESCANSO

**Solicitar sintaxe**

| Método  | URI do pedido                                                                   |
|---------|-------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1 |

**Parâmetro URI**

Utilize os seguintes parâmetros de trajetória para obter o produto especificado.

| Nome                       | Tipo         | Necessário | Descrição                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| **SelfServePolicy-id**     | **string**   | Yes      | Uma corda que identifica a política de autosserviço.                 |

**Cabeçalhos do pedido**

- Para obter mais informações, consulte [Headers](headers.md).

**Corpo do pedido**

Nenhum.

**Exemplo de pedido**

```http
GET https://api.partnercenter.microsoft.com/v1/SelfServePolicy/634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer  <token>
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o corpo de resposta contém um recurso [SelfServePolicy.](self-serve-policy-resources.md#selfservepolicy)

**Códigos de sucesso e erro de resposta**

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

Este método devolve os seguintes códigos de erro:

| Código de Estado HTTP     | Código de erro   | Description                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| 404                  | 600039       | A política de autosserviço não encontrada.                                                     |

**Exemplo de resposta**

```http
HTTP/1.1 200 OK
Content-Length: 1918
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
Date: Tue, 23 Jan 2018 23:13:01 GMT

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