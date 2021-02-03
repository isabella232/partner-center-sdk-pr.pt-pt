---
title: Criar pedido de cliente para revendedor indireto
description: Saiba como utilizar as APIs do Partner Center para criar uma encomenda para um cliente de um revendedor indireto. O artigo inclui pré-requisitos, passos e exmplicas.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f72ecec8d82e6b8a1bc53c277206cafd7d8a4e03
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770152"
---
# <a name="create-an-order-for-a-customer-of-an-indirect-reseller"></a>Criar uma encomenda para um cliente de um revendedor indireto

**Aplica-se a:**

- Partner Center

Como criar uma encomenda para um cliente de um revendedor indireto.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- O identificador de oferta do item para comprar.

- O identificador do inquilino do revendedor indireto.

## <a name="c"></a>C\#

Para criar uma encomenda para um cliente de um revendedor indireto:

1. Obtenha uma coleção dos revendedores indiretos que têm uma relação com o parceiro inscrito.

2. Obtenha uma variável local para o item na coleção que corresponda ao ID do revendedor indireto. Este passo ajuda-o a aceder à propriedade [**mpnId**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationship.mpnid) do revendedor quando cria a encomenda.

3. Instantiar um objeto [**de Encomenda**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) e definir a propriedade [**ReferenceCustomerID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.referencecustomerid) ao identificador do cliente de forma a registar o cliente.

4. Crie uma lista de objetos [**OrderLineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) e atribua a lista à propriedade [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.lineitems) da encomenda. Cada item da linha de encomenda contém a informação de compra para uma oferta. Certifique-se de que preenche a propriedade [**PartnerIdOnRecord**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem.partneridonrecord) em cada item de linha com o ID MPN do revendedor indireto. Deve ter pelo menos um item de linha de encomenda.

5. Obtenha uma interface para encomendar operações ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface a partir da propriedade [**Encomendas.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders)

6. Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) ou [**Criar Aync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) para criar a ordem.

### <a name="c-example"></a>Exemplo \# C

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string offerId;
// string indirectResellerId;

// Get the indirect resellers with a relationship to the signed-in partner.
var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);

// Find the matching reseller in the collection.
var selectedIndirectReseller = (indirectResellers != null && indirectResellers.Items.Any()) ?
    indirectResellers.Items.FirstOrDefault(reseller => reseller.Id.Equals(indirectResellerId, StringComparison.OrdinalIgnoreCase)) :
    null;

// Prepare the order and populate the PartnerIdOnRecord with the reseller&#39;s Microsoft Partner Network Id.
var order = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            OfferId = offerId,
            FriendlyName = "New offer purchase.",
            Quantity = 5,
            PartnerIdOnRecord = selectedIndirectReseller != null ? selectedIndirectReseller.MpnId : null
        }
    }
};

// Place the order.
var createdOrder = partnerOperations.Customers.ById(customerId).Orders.Create(order);
```

**Amostra**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: PlaceOrderForCustomer.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                            |
|----------|----------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/encomendas HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

Utilize o seguinte parâmetro de percurso para identificar o cliente.

| Nome        | Tipo   | Necessário | Descrição                                           |
|-------------|--------|----------|-------------------------------------------------------|
| id cliente | string | Sim      | Uma cadeia formatada GUID que identifica o cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

#### <a name="order"></a>Encomenda

Esta tabela descreve as propriedades da **Ordem** no organismo de pedido.

| Nome | Tipo | Necessário | Descrição |
| ---- | ---- | -------- | ----------- |
| ID | cadeia (de carateres) | No | Um identificador de ordem que é fornecido após a criação bem sucedida da ordem. |
| referênciaStomerId | string | Sim | O identificador de clientes. |
| billingCycle | cadeia (de carateres) | No | A frequência com que o parceiro é cobrado por esta ordem. O padrão é &quot; mensal e é aplicado após a &quot; criação bem sucedida da ordem. Os valores suportados são os nomes dos membros encontrados no [**BillingCycleType**](/dotnet/api/microsoft.store.partnercenter.models.offers.billingcycletype). Nota: a funcionalidade anual de faturação ainda não está disponível em geral. O apoio à faturação anual está para breve. |
| lineitems | matriz de objetos | Sim | Uma série de recursos [**orderLineItem.**](#orderlineitem) |
| criaçãoDate | cadeia (de carateres) | No | A data em que a encomenda foi criada, em formato de data-hora. Aplicado após a criação bem sucedida da ordem. |
| atributos | objeto | Não | Contém "ObjectType": "Order". |

#### <a name="orderlineitem"></a>OrderLineItem

Esta tabela descreve as propriedades **orderLineItem** no organismo de pedido.

| Nome | Tipo | Necessário | Descrição |
| ---- | ---- | -------- | ----------- |
| lineItemNumber | int | Sim | Cada item de linha da coleção obtém um número de linha único, contando de 0 a 1. |
| offerId | string | Sim | O identificador da oferta. |
| subscriptionId | cadeia (de carateres) | No | O identificador de assinatura. |
| parentSubscriptionId | cadeia (de carateres) | No | Opcional. A identificação da subscrição dos pais numa oferta de complemento. Aplica-se apenas ao PATCH. |
| nome amigável | cadeia (de carateres) | No | Opcional. O nome amigável para a subscrição definida pelo parceiro para ajudar a desambiguar. |
| quantidade | int | Sim | O número de licenças para uma assinatura baseada em licença. |
| partnerIdOnRecord | cadeia (de carateres) | No | Quando um fornecedor indireto estoende uma encomenda em nome de um revendedor indireto, povoe este campo apenas com o ID MPN do **revendedor indireto** (nunca o ID do fornecedor indireto). Isto garante uma contabilização adequada dos incentivos. **A não prestação do ID MPN do revendedor não faz com que a ordem falhe. No entanto, o revendedor não é registado e, consequentemente, os cálculos de incentivos podem não incluir a venda.** |
| atributos | objeto | Não | Contém "ObjectType":"OrderLineItem". |

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/orders HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 02109f46-3ff2-4be4-9f37-b2eb6d58d542
MS-CorrelationId: 85195ae6-3de5-4978-abd4-7be2fbfe4c84
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 410
Expect: 100-continue

{
    "Id": null,
    "ReferenceCustomerId": "c501c3c4-d776-40ef-9ecf-9cefb59442c1",
    "BillingCycle": "unknown",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "SubscriptionId": null,
            "ParentSubscriptionId": null,
            "FriendlyName": "New offer purchase.",
            "Quantity": 5,
            "PartnerIdOnRecord": "4847383",
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

Se for bem sucedido, o organismo de resposta contém o recurso [de Encomenda](order-resources.md) povoada.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 201 Created
Content-Length: 831
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 85195ae6-3de5-4978-abd4-7be2fbfe4c84
MS-RequestId: 02109f46-3ff2-4be4-9f37-b2eb6d58d542
MS-CV: Nd3Oum/L5EywtKQK.0
MS-ServerId: 020021921
Date: Mon, 10 Apr 2017 23:02:24 GMT

{
    "id": "3eddcac6-63b2-4c40-b0b6-f47e18301492",
    "referenceCustomerId": "c501c3c4-d776-40ef-9ecf-9cefb59442c1",
    "billingCycle": "monthly",
    "lineItems": [{
            "lineItemNumber": 0,
            "offerId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "subscriptionId": "42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
            "friendlyName": "New offer purchase.",
            "quantity": 5,
            "partnerIdOnRecord": "4847383",
            "links": {
                "subscription": {
                    "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/subscriptions/42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2017-04-10T16:02:25.983-07:00",
    "links": {
        "self": {
            "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/orders/3eddcac6-63b2-4c40-b0b6-f47e18301492",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "eyJpZCI6IjNlZGRjYWM2LTYzYjItNGM0MC1iMGI2LWY0N2UxODMwMTQ5MiIsInZlcnNpb24iOjF9",
        "objectType": "Order"
    }
}
```
