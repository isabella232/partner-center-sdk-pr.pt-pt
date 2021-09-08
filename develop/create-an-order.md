---
title: Criar uma encomenda de clientes
description: Saiba como usar as APIs do Partner Center para criar uma encomenda para um cliente. O artigo inclui pré-requisitos, passos e exemplos.
ms.date: 09/06/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 232888ee798b4579246bbfd787e049f9f6e2e8a3
ms.sourcegitcommit: 5f27733d7c984c29f71c8b9c8ba5f89753eeabc4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2021
ms.locfileid: "123557257"
---
# <a name="create-an-order-for-a-customer-using-partner-center-apis"></a>Criar uma encomenda para um cliente que utilize APIs do Partner Center

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud for US Government

A criação de uma **encomenda de produtos de instância VM reservados da Azure** aplica-se *apenas* a:

- Partner Center

Para obter informações sobre o que está atualmente disponível para vender, consulte [as ofertas do Partner no programa Fornecedor de Soluções em Nuvem.](/partner-center/csp-offers)

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um identificador de oferta.

## <a name="c"></a>C\#

Para criar uma encomenda para um cliente:

1. Instantiar um objeto [**de Encomenda**](order-resources.md) e definir a propriedade **ReferenceCustomerID** para o ID do cliente para gravar o cliente.

2. Crie uma lista de objetos [**OrderLineItem**](order-resources.md#orderlineitem) e atribua a lista à propriedade **LineItems** da encomenda. Cada item da linha de encomenda contém a informação de compra para uma oferta. Deve ter pelo menos um item de linha de encomenda.

3. Obtenha uma interface para encomendar operações. Primeiro, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente. Em seguida, recupere a interface da propriedade [**Encomendas.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders)

4. Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) ou [**Criar Aync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) e passe no objeto [**Encomenda.**](order-resources.md)

5. Para completar o atestado e incluir revendedores adicionais, consulte as seguintes amostras de pedido e resposta:

### <a name="request-example"></a>Exemplo de pedido

``` csharp
{
    "PartnerOnRecordAttestationAccepted":true, 
    "lineItems": [
        {
            "offerId": "CFQ7TTC0LH0Z:0001:CFQ7TTC0K18P",
            "quantity": 1,
            "lineItemNumber": 0,
            "PartnerIdOnRecord": "873452",
            "AdditionalPartnerIdsOnRecord":["4847383","873452"]
        }
    ],
    "billingCycle": "monthly"
}
```

### <a name="response-example"></a>Exemplo de resposta

``` csharp
{
    "id": "5cf72f146967",
    "alternateId": "5cf72f146967",
    "referenceCustomerId": "f81d98dd-c2f4-499e-a194-5619e260344e",
    "billingCycle": "monthly",
    "currencyCode": "USD",
    "currencySymbol": "$",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "CFQ7TTC0LH0Z:0001:CFQ7TTC0K18P",
            "subscriptionId": "fcddfa52-1da8-4529-d347-50ea51e1e7be",
            "termDuration": "P1M",
            "transactionType": "New",
            "friendlyName": "AI Builder Capacity add-on",
            "quantity": 1,
            "partnerIdOnRecord": "873452",
            "additionalPartnerIdsOnRecord": [
                "4847383",
                "873452"
            ],
            "links": {
                "product": {
                    "uri": "/products/CFQ7TTC0LH0Z?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/CFQ7TTC0LH0Z/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/CFQ7TTC0LH0Z/skus/0001/availabilities/CFQ7TTC0K18P?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2021-08-17T18:13:11.3122226Z",
    "status": "pending",
    "transactionType": "UserPurchase",
    "links": {
        "self": {
            "uri": "/customers/f81d98dd-c2f4-499e-a194-5619e260344e/orders/5cf72f146967",
            "method": "GET",
            "headers": []
        },
        "provisioningStatus": {
            "uri": "/customers/f81d98dd-c2f4-499e-a194-5619e260344e/orders/5cf72f146967/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "patchOperation": {
            "uri": "/customers/f81d98dd-c2f4-499e-a194-5619e260344e/orders/5cf72f146967",
            "method": "PATCH",
            "headers": []
        }
    },
    "client": {},
    "attributes": {
        "objectType": "Order"
    }
}

```

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string offerId;

var order = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            OfferId = offerId,
            FriendlyName = "new offer purchase",
            Quantity = 1,
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", "5198C069-3DAA-403A-8660-5BE11BFD12EE" },
                { "scope", "shared" },
                { "duration", "3Years" }
            }
        }
    }
};

var createdOrder = partnerOperations.Customers.ById(customerId).Orders.Create(order);
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: CreateOrder.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                            |
|----------|----------------------------------------------------------------------------------------|
| **PUBLICAR** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/encomendas HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

Utilize o seguinte parâmetro de percurso para identificar o cliente.

| Nome        | Tipo   | Necessário | Descrição                                                |
|-------------|--------|----------|------------------------------------------------------------|
| id cliente | string | Yes      | Um id de cliente formatado GUID que identifica o cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

#### <a name="order"></a>Encomenda

Esta tabela descreve as propriedades da [Ordem](order-resources.md) no organismo de pedido.

| Propriedade             | Tipo                        | Necessário                        | Descrição                                                                   |
|----------------------|-----------------------------|---------------------------------|-------------------------------------------------------------------------------|
| ID                   | string                      | No                              | Um identificador de ordem que é fornecido após a criação bem sucedida da ordem.   |
| referênciaStomerId  | cadeia (de carateres)                      | No                              | O identificador de clientes. |
| billingCycle         | cadeia (de carateres)                      | No                              | Indica a frequência com que o parceiro é faturado para esta encomenda. Os valores suportados são os nomes dos membros encontrados no [BillingCycleType](product-resources.md#billingcycletype). O padrão é "Mensal" ou "OneTime" na criação da ordem. Este campo é aplicado após a criação bem sucedida da ordem. |
| lineitems            | matriz de recursos [OrderLineItem](order-resources.md#orderlineitem) | Yes      | Uma lista itemada das ofertas que o cliente está a comprar, incluindo a quantidade.        |
| currencyCode         | cadeia (de carateres)                      | No                              | Só para ler. A moeda utilizada na eção da encomenda. Aplicado após a criação bem sucedida da ordem.           |
| criaçãoDate         | datetime                    | No                              | Só para ler. A data em que a encomenda foi criada, em formato de data-hora. Aplicado após a criação bem sucedida da ordem.                                   |
| status               | cadeia (de carateres)                      | No                              | Só para ler. O estado da ordem.  Os valores suportados são os nomes dos membros encontrados no [OrderStatus](order-resources.md#orderstatus).        |
| ligações                | [Pedidos](utility-resources.md#resourcelinks)              | No                              | Os links de recursos correspondentes à Ordem. |
| atributos           | [RecursosTributos](utility-resources.md#resourceattributes) | No                              | Os metadados atribuem correspondentes à Ordem. |
| PartnerOnRecordAttestationAccepted | Booleano | Yes | Confirma a conclusão do Attestation |


#### <a name="orderlineitem"></a>OrderLineItem

Esta tabela descreve as propriedades [orderLineItem](order-resources.md#orderlineitem) no organismo de pedido.

>[!NOTE]
>O parceiroIdOnRecord só deve ser fornecido quando um fornecedor indireto faz uma encomenda em nome de um revendedor indireto. É utilizado para armazenar o ID da Rede de Parceiros microsoft apenas do revendedor indireto (nunca o ID do fornecedor indireto).

| Nome                 | Tipo   | Necessário | Descrição                                                                                                                                                                                                                                |
|----------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| lineItemNumber       | int    | Yes      | Cada item de linha da coleção obtém um número de linha único, contando de 0 a 1.                                                                                                                                                 |
| offerId              | string | Yes      | O identificador da oferta.                                                                                                                                                                                                                      |
| subscriptionId       | cadeia (de carateres) | No       | O identificador de assinatura.                                                                                                                                                                                                               |
| parentSubscriptionId | cadeia (de carateres) | No       | Opcional. A identificação da subscrição dos pais numa oferta de complemento. Aplica-se apenas ao PATCH.                                                                                                                                                     |
| nome amigável         | cadeia (de carateres) | No       | Opcional. O nome amigável para a subscrição definida pelo parceiro para ajudar a desambiguar.                                                                                                                                              |
| quantidade             | int    | Yes      | O número de licenças para uma assinatura baseada em licença.                                                                                                                                                                                   |
| partnerIdOnRecord    | cadeia (de carateres) | No       | Quando um fornecedor indireto estoende uma encomenda em nome de um revendedor indireto, povoe este campo apenas com o ID MPN do **revendedor indireto** (nunca o ID do fornecedor indireto). Isto garante uma contabilização adequada dos incentivos. |
| provisionamentoContexto  | Cadeia de<do dicionário,> de cordas                | No       |  Informação necessária para o provisionamento de alguns itens no catálogo. A propriedade de ProvisioningVariables num SKU indica quais propriedades são necessárias para itens específicos no catálogo.                  |
| ligações                | [OrderLineItemLinks](order-resources.md#orderlineitemlinks) | No       |  Só para ler. As ligações de recursos correspondentes ao item da linha Encomenda.  |
| atributos           | [RecursosTributos](utility-resources.md#resourceattributes) | No       | Os metadados atribuem correspondentes ao OrderLineItem. |
| renovaTo             | Matriz de objetos                          | No    |Uma variedade de [recursos Renovados.](order-resources.md#renewsto)                                                                            |
| AttestationAccepted             | bool                 | No   |  Indica acordo para oferecer ou sku condições. Requerido apenas para ofertas ou skus onde a SkuAttestationProperties ou OfferAttestationProperties aplicam Attestation é Verdadeira.          |
| PartnerIdsOnRecord adicional | String | No | Quando um fornecedor indireto estoende uma encomenda em nome de um revendedor indireto, povoe este campo apenas com o ID MPN do **revendedor indireto Adicional** (nunca o ID do fornecedor indireto). Não são aplicáveis incentivos a estes revendedores adicionais. Só podem ser introduzidos um máximo de 5 Revendedores Indiretos. Estes são apenas os parceiros aplicáveis que transacionam nos países da UE/EFTA. |

##### <a name="renewsto"></a>RenovarTo

Esta tabela descreve as propriedades [Renovações](order-resources.md#renewsto) No corpo de pedido.

| Propriedade              | Tipo             | Necessário        | Descrição |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termoDuração          | cadeia (de carateres)           | No              | Uma representação ISO 8601 da duração do período de renovação. Os valores suportados atuais são **P1M** (1 mês) e **P1Y** (1 ano). |

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Length: 691
Content-Type: application/json

{
  "BillingCycle": "one_time",
  "CurrencyCode": "USD",
  "LineItems": [
    {
      "LineItemNumber": 0,
      "ProvisioningContext": {
        "subscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
        "scope": "shared",
        "duration": "1Year"
      },
      "OfferId": "DZH318Z0BQ4B:0047:DZH318Z0DSM8",
      "FriendlyName": "A_sample_Azure_RI",
      "Quantity": 1
    }
  ]
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o método devolve um recurso [da Ordem](order-resources.md) no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 201 Created
Content-Length: 788
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b593cbb7-b358-4b31-81fc-e60b9c277a7f
MS-RequestId: 025f4c19-217f-49d6-a056-391902c62fb3
Date: Thu, 15 Mar 2018 22:30:02 GMT

{
  "id": "Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1",
  "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
  "billingCycle": "one_time",
  "currencyCode": "USD",
  "lineItems": [
    {
        "lineItemNumber": 0,
        "offerId": "84A03D81-6B37-4D66-8D4A-FAEA24541538",
        "friendlyName": "A_sample_Azure_RI",
        "quantity": 1,
        "links": {
            "sku": {
                "uri": "/products/DZH318Z0BQ4B/skus/0047?country=US",
                "method": "GET",
                "headers": []
            }
        }
    } ],
    "creationDate": "2018-03-15T22:30:02.085152Z",
    "status": "pending",
    "links": {
        "provisioningStatus": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Order"
    }
}
```
