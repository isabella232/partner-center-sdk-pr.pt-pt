---
title: Obter ligação de ativação por item de linha da encomenda
description: Obtém um link de ativação de subscrição por item da linha de encomenda.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 61cb6659961cfeb22d3b0fe7ad5dd8533d5f72dda76fe96e64b4c64f39ece397
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994154"
---
# <a name="get-activation-link-by-order-line-item"></a>Obter ligação de ativação por item de linha da encomenda

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Obtém um link de ativação de subscrição de mercado comercial pelo número de item da linha de encomenda.

No painel de instrumentos Do Centro de Parceiros, pode fazer esta operação selecionando uma **Subscrição Específica** sob **Subscrição** na página principal ou selecionando o link **do site do Publisher** ao lado da subscrição para ativar na página **de Subscrições.**

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Encomenda completada com produto que precisa de ativação.

## <a name="c"></a>C\#

Para obter o link de ativação de um item de linha, utilize a sua coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente selecionado. Em seguida, ligue para a propriedade [**Encomendas**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) e o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) com o seu  [**OrderId**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.id)especificado . Em seguida, ligue para o método [**LineItems**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) com **ById()** com o identificador de número de item de linha.  Por fim, ligue para o método **ActivationLinks().**

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string orderId;
// string lineItemNumber

// get the activation link for the specific line item
var partnerOperations.Customers.ById(customerId).Orders.ById(orderId).OrderLineItems.ById(lineItemNumber).ActivationLinks();
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                                               |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customerId}/orders/{orderId}/lineitems/{lineItemNumber}/activationlinks HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/8c5b65fd-c725-4f50-8d9c-97ec9169fdd0/orders/03fb46b3-bf8c-49aa-b908-ca2e93bcc04a/lineitems/0/activationlinks HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma coleção de recursos do [Cliente](customer-resources.md#customer) no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 809
Content-Type: application/json
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
Date: Fri, 20 Nov 2015 01:08:23 GMT
{
  "totalCount": 1,
  "items": [
    {
      "lineItemNumber": 0,
      "link": {
        "uri": "<link populated here>",
        "method": "GET",
        "headers": [

        ]
      }
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/8c5b65fd-c725-4f50-8d9c-97ec9169fdd0/orders/03fb46b3-bf8c-49aa-b908-ca2e93bcc04a/lineitems/0/activationlinks",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "Collection"
  }
}
```
