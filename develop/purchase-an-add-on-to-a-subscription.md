---
title: Comprar um suplemento para uma subscrição
description: Como comprar um suplemento a uma subscrição existente.
ms.date: 11/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 975a2516bccdc6274bfec5d6a3286a649fc4f808
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769656"
---
# <a name="purchase-an-add-on-to-a-subscription"></a>Comprar um suplemento para uma subscrição

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros do Microsoft Cloud for US Government

Como comprar um suplemento a uma subscrição existente.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de assinatura. Esta é a subscrição existente para a compra de uma oferta de complemento.

- Um ID de oferta que identifica a oferta de compra.

## <a name="purchasing-an-add-on-through-code"></a>Compra de um código add-on através

Ao adquirir um complemento a uma subscrição está a atualizar a ordem de subscrição original com a encomenda para o add-on. No seguinte, customerId é o ID do cliente, subscriçãoId é o ID de subscrição, e addOnOfferId é o ID de oferta para o add-on.

Eis os passos:

1.  Obtenha uma interface para as operações para a subscrição.

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2.  Utilize essa interface para instantaneaizar um objeto de subscrição. Isto dá-lhe os detalhes da subscrição dos pais, incluindo o id do pedido.

    ``` csharp
    var parentSubscription = subscriptionOperations.Get();
    ```

3.  Instantaneamente um novo objeto [**da Ordem.**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) Esta instância de encomenda é utilizada para atualizar a encomenda original utilizada para a compra da subscrição. Adicione um item de linha única à ordem que representa o addon.
    ``` csharp
    var orderToUpdate = new Order()
    {
        ReferenceCustomerId = customerId,
        LineItems = new List<OrderLineItem>()
        {
            new OrderLineItem()
            {
                LineItemNumber = 0,
                OfferId = addOnOfferId,
                FriendlyName = "Some friendly name",
                Quantity = 2,
                ParentSubscriptionId = subscriptionId
            }
        }
    };
    ```

4.  Atualize a encomenda original para a subscrição com a nova encomenda para o add-on.
    ``` csharp
    Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
    ```

## <a name="c"></a>C\#

Para adquirir um addon, comece por obter uma interface para as operações de subscrição, ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente, e o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para identificar a subscrição que tem a oferta adicional. Utilize essa [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) para recuperar os detalhes da subscrição chamando [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get). Por que precisa dos detalhes da subscrição? Porque precisa do pedido de identificação da ordem de subscrição. Esta é a ordem para ser atualizado com o addon.

Em seguida, instantânea um novo objeto [**de Encomenda**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) e povoa-o com uma única instância [**LineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) que contém a informação para identificar o addon, como mostrado no seguinte corte de código. Utilizará este novo objeto para atualizar a ordem de subscrição com o addon. Por fim, ligue para o método [**Patch**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.patch) para atualizar a ordem de subscrição, depois de primeiro identificar o cliente com [**iAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) e a encomenda com [**Encomendas.ById**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid).

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;
// string addOnOfferId;

// Get an interface to the operations for the subscription.
var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);

// Get the parent subscription details.
var parentSubscription = subscriptionOperations.Get();

// In order to buy an add-on subscription for this offer, we need to patch/update the order through which the base offer was purchased
// by creating an order object with a single line item which represents the add-on offer purchase.
var orderToUpdate = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            LineItemNumber = 0,
            OfferId = addOnOfferId,
            FriendlyName = "Some friendly name",
            Quantity = 2,
            ParentSubscriptionId = subscriptionId
        }
    }
};

// Update the order to apply the add on purchase.
Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
```

**Amostra**: [App de teste de consola](console-test-app.md). **Projeto**: Partner Center SDK Samples **Class**: AddSubscriptionAddOn.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método    | URI do pedido                                                                                              |
|-----------|----------------------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/orders/{order-id} HTTP/1.1 |

### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros para identificar o cliente e encomendar.

| Nome                   | Tipo     | Necessário | Descrição                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | O valor é um **design de cliente-inquilino-inquilino** formatado guid que identifica o cliente. |
| **ordem id**           | **guid** | Y        | O identificador da ordem.                                                              |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

As tabelas seguintes descrevem as propriedades no corpo de pedido.

## <a name="order"></a>Encomenda

| Nome                | Tipo             | Necessário | Descrição                                          |
|---------------------|------------------|----------|------------------------------------------------------|
| Id                  | string           | N        | A identificação da ordem.                                        |
| ReferênciaStotomerIda | string           | Y        | A identificação do cliente.                                     |
| LineItems           | matriz de objetos | Y        | Uma variedade de objetos [OrderLineItem.](#orderlineitem) |
| Encontro de Criação        | string           | N        | A data em que a encomenda foi criada, em formato de data-hora. |
| Atributos          | objeto           | N        | Contém "ObjectType": "Order".                      |

## <a name="orderlineitem"></a>OrderLineItem

| Nome                 | Tipo   | Necessário | Descrição                                                  |
|----------------------|--------|----------|--------------------------------------------------------------|
| LineItemNumber       | número | Y        | O número do item da linha, a começar por 0.                       |
| OfferId              | string | Y        | A identificação da oferta do add-on.                                  |
| SubscriptionId       | string | N        | O ID da subscrição adicionada adquirida.                 |
| ParentSubscriptionId | string | Y        | O ID da subscrição dos pais que tem a oferta de complemento. |
| FriendlyName         | string | N        | O nome amigável para este item de linha.                        |
| Quantidade             | número | Y        | O número de licenças.                                      |
| PartnerIdOnRecord    | string | N        | A identificação da MPN do sócio do registo.                         |
| Atributos           | objeto | N        | Contém "ObjectType": "OrderLineItem".                      |

### <a name="request-example"></a>Exemplo de pedido

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
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "SubscriptionId": null,
            "ParentSubscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
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

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [os Códigos de Erro do Centro de Parceiros](error-codes.md).

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
    "billingCycle": "none",
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
        }, {
            "lineItemNumber": 1,
            "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "subscriptionId": "968BA1CF-C146-4ADF-A300-308DCF718EEE",
            "friendlyName": "Some friendly name",
            "quantity": 2,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/968BA1CF-C146-4ADF-A300-308DCF718EEE",
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
