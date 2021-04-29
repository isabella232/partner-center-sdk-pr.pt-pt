---
title: Cancelar uma encomenda da caixa de areia de integração
description: Saiba como usar as APIs do Partner Center para cancelar diferentes tipos de pedidos de subscrição a partir de contas de caixas de areia de integração.
ms.date: 04/28/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c3bf862c62804a56e6f73dd3ec36d2e9eb65f997
ms.sourcegitcommit: f59a9311c8a37d45695caf74794ec1697426acc9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/29/2021
ms.locfileid: "108210024"
---
# <a name="cancel-an-order-from-the-integration-sandbox-using-partner-center-apis"></a>Cancelar uma encomenda da caixa de areia de integração usando APIs do Partner Center

**Aplica-se a:**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Este artigo descreve como usar as APIs do Partner Center para cancelar diferentes tipos de ordens de subscrição a partir de contas de caixas de areia de integração. Tais encomendas podem incluir instâncias reservadas, software e marketplace comercial Software como uma ordem de subscrição de Serviço (SaaS).

>[!NOTE] 
>Tenha em atenção que os cancelamentos de instâncias reservadas ou encomendas de subscrição saaS de marketplace comercial só são possíveis a partir de contas de sandbox de integração. Quaisquer encomendas de caixas de areia com mais de 60 dias não podem ser canceladas do Partner Center. Se precisar de assistência, contacte o Partner Center Support. 

Para cancelar as ordens de produção de software através da API, utilize [as compras de cancelamento de software](cancel-software-purchases.md).
Também pode cancelar as ordens de produção de software através do dashboard usando [cancelar uma compra](/partner-center/csp-software-subscriptions).

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Uma conta parceira de sandbox de integração com um cliente com uma instância reservada ativa / software / encomendas de subscrição saaS de terceiros.

## <a name="c"></a>C\#

Para cancelar uma encomenda da caixa de areia de integração, passe as credenciais da sua conta para o [**`CreatePartnerOperations`**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) método para obter uma interface para obter [**`IPartner`**](/dotnet/api/microsoft.store.partnercenter.ipartner) operações de parceiro.

Para selecionar uma [determinada Encomenda](order-resources.md#order), utilize as operações do parceiro e ligue com [**`Customers.ById()`**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) o identificador do cliente para especificar o cliente, seguido pelo **`Orders.ById()`** identificador de encomendas para especificar a encomenda e, **`Get`** finalmente, ou método para **`GetAsync`** recuperá-la.

Desave o [**`Order.Status`**](order-resources.md#order) imóvel `cancelled` e utilize o método para atualizar a **`Patch()`** encomenda.

``` csharp
// IPartnerCredentials tipAccountCredentials;
// Customer tenant Id to be deleted.
// string customerTenantId;

IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

// Cancel order
var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Get();
order.Status = "cancelled";
order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Patch(order);

```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método     | URI do pedido                                                                            |
|------------|----------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/orders/{order-id} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para eliminar um cliente.

| Nome                   | Tipo     | Necessário | Descrição                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor. |
| **ordem id** | **string** | Y        | O valor é uma cadeia que denota os IDs de encomenda que precisam de ser cancelados. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

```http
{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "status": "cancelled",
}
```

### <a name="request-example"></a>Exemplo de pedido

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/orders/<order-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd

{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "status": "cancelled",
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve a encomenda cancelada.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 866
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "alternateId": "11fc4bdfd47a",
    "referenceCustomerId": "bd59b416-37f9-4d8f-8df3-5750111fc615",
    "billingCycle": "one_time",
    "currencyCode": "USD",
    "currencySymbol": "$",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0DWT0:0001:DG7GMGF0DSQR",
            "termDuration": "",
            "transactionType": "New",
            "friendlyName": "Microsoft Identity Manager 2016 - 1 User CAL",
            "quantity": 1,
            "links": {
                "product": {
                    "uri": "/products/DG7GMGF0DWT0?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DG7GMGF0DWT0/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DG7GMGF0DWT0/skus/0001/availabilities/DG7GMGF0DSQR?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2019-02-21T17:56:21.1335741Z",
    "status": "cancelled",
    "transactionType": "UserPurchase",
    "attributes": {
        "objectType": "Order"
    }
}
```
