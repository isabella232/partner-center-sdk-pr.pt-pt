---
title: Criar um carrinho com suplementos
description: Saiba como utilizar as APIs do Partner Center para adicionar uma encomenda de clientes com suplementos através de um carrinho. O artigo partilha pré-requisitos e passos para criar um carrinho com suplementos.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 81c41405a2f56eb4d1d3447d14b93e05d550cc70
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770130"
---
# <a name="create-a-cart-with-add-ons-to-a-customer-order"></a>Criar um carrinho com suplementos a uma encomenda de clientes

**Aplica-se a:**

- Partner Center

Pode comprar suplementos através de um carrinho. Para obter mais informações sobre o que está atualmente disponível para vender, consulte [as ofertas do Partner no programa Cloud Solution Provider](/partner-center/csp-offers).

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Um carrinho permite a compra de uma oferta base e os seus suplementos correspondentes. Siga estes passos para criar um carrinho:

1. Instantiizar um objeto [**do Carrinho.**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart)

2. Crie uma lista de objetos [**CartLineItem**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) que representam a(s) oferta base, e atribua a lista à propriedade [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) do carrinho.

3. Sob o item da linha de cada oferta base, povoar a lista de **AddOnItems com outros objetos** **CartLineItem** que cada um representa um addon que será comprado contra essa oferta base.

4. Obtenha uma interface para as operações de carrinhos utilizando o [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) para ligar para o método [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface da propriedade **Cart.**

5. Por fim, ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) ou [**Criar Async**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) para criar o carrinho.

### <a name="c-example"></a>Exemplo \# C

```csharp
// IAggregatePartner partnerOperations;
// string customerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "A_base_offer_ID",
                FriendlyName = "Myofferpurchase",
                Quantity = 3,
                BillingCycle = BillingCycleType.Monthly,
                AddonItems = new List<CartLineItem>
                {
                    new CartLineItem
                    {
                        Id = 1,
                        CatalogItemId = "An_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 2,
                    },
                    new CartLineItem
                    {
                        Id = 2,
                        CatalogItemId = "Another_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 3
                    }
                }
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

Siga estas medidas para criar um carrinho que permita a compra de complementos(s) contra subscrições de base existentes):

1. Crie um **Carrinho** com um novo **CartLineItem** contendo o ID de subscrição na propriedade **ProvisioningContext** com a chave "ParentSubscriptionId".

2. Chame o método **Criar** ou **Criar Async.**

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "An_addon_item_ID",
                ProvisioningContext = new Dictionary<string, string>
                {
                    {
                        "ParentSubscriptionId", "An_existing_subscription_Id"
                    }
                },
                Quantity = 1,
                BillingCycle = BillingCycleType.Annual,
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(selectedCustomerId).Carts.Create(cart);
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts HTTP/1.1                        |

#### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de percurso para identificar o cliente.

| Nome            | Tipo     | Necessário | Descrição                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **id cliente** | string   | Sim      | Um id de cliente formatado GUID que identifica o cliente.             |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades do [Carrinho](cart-resources.md) no corpo de pedido.

| Propriedade              | Tipo             | Necessário        | Descrição |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| ID                    | cadeia (de carateres)           | No              | Um identificador de carrinhos que é fornecido após a criação bem sucedida do carrinho.                                  |
| criaçãoTimeStamp     | DateTime         | Não              | A data em que o carrinho foi criado, em formato de data- hora. Aplicado após a criação bem sucedida do carrinho.         |
| últimampadatimestamp de Tempos | DateTime         | Não              | A data em que o carrinho foi atualizado pela última vez, em formato de data-hora. Aplicado após a criação bem sucedida do carrinho.    |
| expiraçãoTimeStamp   | DateTime         | Não              | A data em que o carrinho expirará, em formato de data-hora.  Aplicado após a criação bem sucedida do carrinho.            |
| últimoModifiedUser      | cadeia (de carateres)           | No              | O utilizador que atualizou pela última vez o carrinho. Aplicado após a criação bem sucedida do carrinho.                             |
| lineitems             | Matriz de objetos | Sim             | Uma matriz de recursos [CartLineItem.](cart-resources.md#cartlineitem)                                             |

Esta tabela descreve as propriedades [do CartLineItem](cart-resources.md#cartlineitem) no corpo de pedido.

| Propriedade             | Tipo                             | Descrição                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID                   | string                           | Um identificador único para um item de linha de carrinho. Aplicado após a criação bem sucedida do carrinho.                                                                   |
| catalogId            | string                           | O identificador de artigos de catálogo.                                                                                                                          |
| nome amigável         | string                           | Opcional. O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.                                                                 |
| quantidade             | int                              | O número de licenças ou instâncias.                                                                                                                  |
| currencyCode         | string                           | O código da moeda.                                                                                                                                    |
| billingCycle         | Objeto                           | O tipo de ciclo de faturação definido para o período atual.                                                                                                 |
| participantes         | Lista de pares de cordas de objeto      | Uma coleção de PartnerId on Record (MPNID) na compra.                                                                                          |
| provisionamentoContexto  | Cadeia de<do dicionário,> de cordas       | Um contexto utilizado para o provisionamento da oferta.                                                                                                             |
| orderGroup           | string                           | Um grupo para indicar quais os itens que podem ser colocados juntos.                                                                                               |
| addonItems           | Lista de **objetos CartLineItem** | Uma coleção de itens de linha de carrinhos para addons que serão adquiridos para a subscrição base que resulta da compra do item da linha do carrinho dos pais. |
| erro                | Objeto                           | Aplicado após o carrinho é criado em caso de erro.                                                                                                    |

### <a name="request-example-new-base-subscription"></a>Exemplo de pedido (nova subscrição base)

O exemplo REST que se segue mostra como criar um carrinho com itens adicionais para uma nova subscrição base.

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "FriendlyName":"Myofferpurchase",
            "Quantity":3,
            "BillingCycle":"monthly",
            "AddonItems": [
                {
                    "Id":1,
                    "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "Quantity":2,
                    "BillingCycle":"monthly"
                },
                {
                    "Id":2,
                    "CatalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "Quantity":3,
                    "BillingCycle":"monthly"
                }
            ]
        }
    ]
}
```

#### <a name="request-example-existing-base-subscription"></a>Exemplo de pedido (subscrição base existente)

O exemplo REST a seguir mostra como anexar suplementos a uma subscrição base existente.

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "Quantity":1,
            "BillingCycle":"annual",
            "ProvisioningContext":{"ParentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"}
        }
    ]
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve o recurso [cart](cart-resources.md) povoado no corpo de resposta.

#### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

#### <a name="response-example-new-base-subscription"></a>Exemplo de resposta (nova subscrição base)

```http
HTTP/1.1 201 Created
Content-Length: 958
Content-Type: application/json
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:29:05 GMT

{
    "id":"dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
    "creationTimestamp":"2018-11-01T22:29:03.6900182Z",
    "lastModifiedTimestamp":"2018-11-01T22:29:03.6900182Z",
    "expirationTimestamp":"2018-11-01T22:44:05.0025799Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "friendlyName":"Myofferpurchase",
            "quantity":3,
            "currencyCode":"USD",
            "billingCycle":"monthly",
            "orderGroup":"OMS-0",
            "addonItems": [
                {
                    "id":1,
                    "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "quantity":2,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                },
                {
                    "id":2,
                    "catalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "quantity":3,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                }
            ]
        }
],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```

#### <a name="response-example-existing-base-subscription"></a>Exemplo de resposta (subscrição base existente)

```http
HTTP/1.1 201 Created
Content-Length: 707
Content-Type: application/json
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:46:18 GMT

{
    "id":"4d927e27-93d1-448b-abe5-819b66ecca22",
    "creationTimestamp":"2018-11-01T22:46:16.2996364Z",
    "lastModifiedTimestamp":"2018-11-01T22:46:16.2996364Z",
    "expirationTimestamp":"2018-11-01T23:01:18.7543264Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "quantity":1,
            "currencyCode":"USD",
            "billingCycle":"annual",
            "provisioningContext": {
                "parentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"
            },
            "orderGroup":"OMS-0"
        }
    ],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/4d927e27-93d1-448b-abe5-819b66ecca22",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```
