---
title: Obter todos os pedidos de serviço para um cliente
description: Recebe todos os pedidos de atendimento de um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ffcbbb9cf14b1b2a5b3becab541d3042c3cad508
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760679"
---
# <a name="get-all-service-requests-for-a-customer"></a>Obter todos os pedidos de serviço para um cliente

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Recebe todos os pedidos de atendimento de um cliente.

No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md) Em seguida, selecione **a gestão** de serviço na barra lateral esquerda. Os pedidos de atendimento do cliente são apresentados nos **bilhetes de Apoio.**

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Para apresentar uma lista de todos os pedidos de serviço de um cliente, utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) Em seguida, ligue para a propriedade [**ServiceRequests,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicerequests) seguida dos métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.getasync)

``` csharp
// IAggregatePartner partnerOperations;
// string customerId as string;

ResourceCollection<ServiceRequest> serviceRequests = partnerOperations.Customers.ById(customerId).ServiceRequests.Get();
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/servicerequests HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para obter todos os pedidos de serviço para o cliente.

| Nome                   | Tipo     | Necessário | Descrição                            |
|------------------------|----------|----------|----------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | Um GUID correspondente ao cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/servicerequests HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 53d5d48c-9693-46b6-8071-2eed07797d6c
MS-CorrelationId: 998e31a1-3f17-4471-a9ee-7678dd72e033
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma recolha de recursos **de Pedido** de Serviço no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 742
Content-Type: application/json
MS-CorrelationId: 998e31a1-3f17-4471-a9ee-7678dd72e033
MS-RequestId: 53d5d48c-9693-46b6-8071-2eed07797d6c
Date: Tue, 24 Nov 2015 07:19:21 GMT

{
    "totalCount": 1,
    "items": [{
        "title": "Test",
        "severity": 0,
        "id": "615112491169010",
        "status": 1,
        "primaryContact": {
            "lastName": "LastName",
            "firstName": "FirstName"
        },
        "createdDate": "2015-11-24T01:07:00.863",
        "lastModifiedDate": "2015-11-24T01:17:10.61",
        "lastClosedDate": "0001-01-01T00:00:00",
        "attributes": {
            "objectType": "ServiceRequest"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
