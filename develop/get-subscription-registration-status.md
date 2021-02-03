---
title: Obter o estado de registo da subscrição
description: Obtenha o estado de uma subscrição que tenha sido registada para uso com Azure Reserved VM Instances.
ms.date: 03/19/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e06cf8a450d6c281f7f83a68c899d1e5b29e9855
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769848"
---
# <a name="get-subscription-registration-status"></a>Obter o estado de registo da subscrição

**Aplica-se a**

- Partner Center

Como obter o estado de registo de subscrição de uma subscrição de cliente que foi habilitada para a compra de Azure Reserved VM Instances.

Para adquirir uma Instância VM Reservada Azure utilizando a API do Centro Parceiro, deve ter pelo menos uma subscrição CSP Azure existente. O Registo de um método [de subscrição](register-a-subscription.md) permite-lhe registar a subscrição CSP Azure existente, permitindo-lhe a aquisição de Azure Reserved VM Instances. Este método permite-lhe recuperar o estado desse registo.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de assinatura.

## <a name="c"></a>C\#

Para obter o estado de registo de uma subscrição, comece por utilizar o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente. Em seguida, obtenha uma interface para as operações de subscrição ligando para o método [**Subscrição.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) com o ID de subscrição para identificar a subscrição. Em seguida, utilize a propriedade RegistrationStatus para obter uma interface para as operações de estado de registo da subscrição atual, e ligue para o método **Get** or **GetAsync** para recuperar o objeto **SubscriptionRegistrationStatus.**

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve a subscription's registration status details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).RegistrationStatus.Get();
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método    | URI do pedido                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| **Obter**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/registrationstatus HTTP/1.1 |

### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros de percurso para identificar o cliente e a subscrição.

| Nome                    | Tipo       | Necessário | Descrição                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| id cliente             | string     | Sim      | Uma cadeia formatada GUID que identifica o cliente.         |
| id de subscrição         | string     | Sim      | Uma cadeia formatada GUID que identifica a subscrição.     |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém um recurso [SubscriptionRegistrationStatus.](subscription-resources.md#subscriptionregistrationstatus)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: InswEQre402koceL.0
MS-ServerId: 030020344

{
    "subscriptionId":"<subscription-id>",
    "status":"NotRegistered",
    "attributes":{
        "objectType":"SubscriptionRegistrationStatus"
    }
}
```
