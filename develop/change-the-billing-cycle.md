---
title: Alterar o ciclo de faturação
description: Saiba como atualizar uma subscrição de um cliente à faturação mensal ou anual usando APIs do Partner Center. Também pode fazê-lo a partir do painel partner Center.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 8a2879db061ced799e29d84e71be5b1259b07689
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770088"
---
# <a name="change-a-customer-subscription-billing-cycle"></a>Alterar um ciclo de faturação de subscrição de clientes

**Aplica-se a:**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Atualiza uma [Encomenda](order-resources.md) de faturação mensal a anual ou de faturação anual a mensal.

No painel de instrumentos partner Center, esta operação pode ser realizada navegando para a página de detalhes de subscrição de um cliente. Uma vez lá, verá uma opção que define o ciclo de faturação atual para a subscrição com a capacidade de alterá-la e submetê-la.

**Fora do âmbito** deste artigo:

- Alteração do ciclo de faturação para ensaios
- Alteração dos ciclos de faturação para quaisquer ofertas não anuais (mensalmente, 6 anos) & assinaturas Azure
- Alteração dos ciclos de faturação para subscrições inativas
- Alteração dos ciclos de faturação para subscrições baseadas em licenças de serviços online da Microsoft

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Uma identificação de encomenda.

## <a name="c"></a>C\#

Para alterar a frequência do ciclo de faturação, atualize a propriedade [**Order.BillingCycle.**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.billingcycle#Microsoft_Store_PartnerCenter_Models_Orders_Order_BillingCycle)

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string offerId;
// string orderId;

var order = new Order()
{
    ReferenceCustomerId = customerId,
    BillingCycle = BillingCycleType.Annual,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            LineItemNumber = 0,
            OfferId = offerId,
            SubscriptionId = "69829602-C219-40FD-A3D5-4150FCA41A19",
            Quantity = 1
        }
    }
};

var createdOrder = partnerOperations.Customers.ById(customerId).Orders.ById(orderId).Patch(order);
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método    | URI do pedido                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/orders/{order-id} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Esta tabela lista o parâmetro de consulta necessário para alterar a quantidade da subscrição.

| Nome                   | Tipo | Necessário | Descrição                                                          |
|------------------------|------|----------|----------------------------------------------------------------------|
| **cliente-inquilino-id** | GUID |    Y     | Um design **de cliente-inquilino-cliente-inativação** que identifica o cliente |
| **ordem id**           | GUID |    Y     | O identificador de ordem                                                 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

As tabelas seguintes descrevem as propriedades no corpo de pedido.

### <a name="order"></a>Encomenda

| Propriedade           | Tipo             | Necessário | Descrição                                                                |
|--------------------|------------------|----------|----------------------------------------------------------------------------|
| Id                 | string           |    N     | Um identificador de ordem que é fornecido após a criação bem sucedida da ordem |
|ReferênciaStotomerIda | string           |    Y     | O identificador de clientes                                                    |
| BillingCycle       | string           |    Y     | Indica a frequência com que o parceiro é faturado para esta encomenda. Os valores suportados são os nomes dos membros encontrados no [BillingCycleType](product-resources.md#billingcycletype). |
| LineItems          | matriz de objetos |    Y     | Uma variedade de recursos [OrderLineItem](#orderlineitem)                      |
| Encontro de Criação       | datetime         |    N     | A data em que a encomenda foi criada, em formato de data-hora                        |
| Atributos         | Objeto           |    N     | Contém "ObjectType": "OrderLineItem"                                     |

### <a name="orderlineitem"></a>OrderLineItem

| Propriedade             | Tipo   | Necessário | Descrição                                                                        |
|----------------------|--------|----------|------------------------------------------------------------------------------------|
| LineItemNumber       | número |    Y     | O número do item da linha, começando com 0                                              |
| OfferId              | string |    Y     | O ID da oferta                                                                |
| SubscriptionId       | string |    Y     | O ID da subscrição                                                         |
| FriendlyName         | string |    N     | O nome amigável para a subscrição definida pelo parceiro para ajudar a desambiguar |
| Quantidade             | número |    Y     | O número de licenças ou instâncias                                                |
| PartnerIdOnRecord    | string |    N     | A MPN ID do sócio do registo                                                |
| Atributos           | Objeto |    N     | Contém "ObjectType": "OrderLineItem"                                             |

### <a name="request-example"></a>Exemplo de pedido

Atualização da faturação anual

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/orders/CF3B0E37-BE0B-4CDD-B584-D1A97D98A922 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 17a2658e-d2cc-439b-a2f0-2aefd9344fbc
MS-CorrelationId: 60efdd24-17ef-4080-9b02-4fc315f916ff
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 414
Expect: 100-continue

{
    "Id": null,
    "ReferenceCustomerId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "BillingCycle" : "Annual",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "SubscriptionId": "69829602-C219-40FD-A3D5-4150FCA41A19",
            "FriendlyName": "Some friendly name",
            "Quantity": 2,
            "PartnerIdOnRecord": null,
            "Attributes": {
                "ObjectType": "OrderLineItem"
            }
        }
    ],
    "CreationDate": null,
    "Attributes": {
        "ObjectType": "Order"
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve a ordem de subscrição atualizada no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 1135
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 60efdd24-17ef-4080-9b02-4fc315f916ff
MS-RequestId: 17a2658e-d2cc-439b-a2f0-2aefd9344fbc
MS-CV: WtFy3zI8V0u2lnT9.0
MS-ServerId: 020021921
Date: Wed, 25 Jan 2017 23:01:08 GMT

{
    "id": "cf3b0e37-be0b-4cdd-b584-d1a97d98a922",
    "referenceCustomerId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "billingCycle": "Annual",
    "lineItems": [{
            "lineItemNumber": 0,
            "offerId": "195416C1-3447-423A-B37B-EE59A99A19C4",
            "subscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
            "friendlyName": "new offer purchase",
            "quantity": 5,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        {
            "lineItemNumber": 1,
            "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "subscriptionId": "69829602-C219-40FD-A3D5-4150FCA41A19",
            "friendlyName": "Some friendly name",
            "quantity": 2,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/69829602-C219-40FD-A3D5-4150FCA41A19",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2017-01-25T14:53:12.093-08:00",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/orders/cf3b0e37-be0b-4cdd-b584-d1a97d98a922",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "eyJpZCI6ImNmM2IwZTM3LWJlMGItNGNkZC1iNTg0LWQxYTk3ZDk4YTkyMiIsInZlcnNpb24iOjJ9",
        "objectType": "Order"
    }
}
```