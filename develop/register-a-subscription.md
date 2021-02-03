---
title: Registar uma subscrição
description: Registe uma subscrição existente de modo a que possa encomendar reservas Azure.
ms.date: 07/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9a96bb350f22430c9fd7a1759e336cc9f3ca1939
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769650"
---
# <a name="register-a-subscription"></a>Registar uma subscrição

**Aplica-se a**

- Partner Center

Registe uma [Subscrição](subscription-resources.md) existente de modo a que possa encomendar reservas Azure.

Para adquirir uma reserva Azure deve ter pelo menos uma subscrição CSP Azure existente. Este método permite-lhe registar a subscrição CSP Azure existente, permitindo-lhe a compra de reservas Azure.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de assinatura.

## <a name="c"></a>C\#

Para registar a subscrição de um cliente, recupere uma interface para operações de subscrição ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente. Em seguida, ligue para o método [**Subscrição.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) com o ID de subscrição para identificar a subscrição que está a registar.

Por fim, ligue para o método **Registo.Registo()** para registar a subscrição e recuperar um URI que pode ser usado para obter o estado de registo de assinatura. Para mais informações, consulte [obter o estado de registo de assinatura.](get-subscription-registration-status.md)

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve the subscription registration details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).Registration.Register();
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método    | URI do pedido                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| **Publicar**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/registos HTTP/1.1 |

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
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-id>/subscriptions/<subscription-id>/registrations HTTP/1.1
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

Se for bem sucedida, a resposta contém um **cabeçalho de localização** com um URI que pode ser usado para recuperar o estado de registo de subscrição. Guarde este URI para utilização com outras APIs de REST relacionadas. Para obter um exemplo de como recuperar o estado, consulte obter o [estado de registo de assinatura](get-subscription-registration-status.md).

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
```
