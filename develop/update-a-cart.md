---
title: Atualizar um carrinho
description: Como atualizar um pedido para um cliente em um carrinho.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 79dcd58e5a967aad9160777805102683087becc74c655b2de990cd1bfd4ef3c8
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115990159"
---
# <a name="update-a-cart"></a>Atualizar um carrinho

Como atualizar um pedido para um cliente em um carrinho.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Uma identificação do carrinho para um carrinho existente.

## <a name="c"></a>C\#

Para atualizar uma encomenda para um cliente, obtenha o carrinho utilizando o método **Get()** passando os IDs do cliente e do carrinho utilizando a função **ById().** Faça as alterações necessárias no carrinho. Agora ligue para o método **Put** utilizando iDs de cliente e carrinho usando o método **ById().**

Por fim, ligue para o método **Put()** ou **PutAsync** para criar a encomenda.

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Get();

cart.LineItems.ToArray()[0].Quantity++;

var updatedCart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Put(cart);
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts/{cart-id} HTTP/1.1              |

### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros de trajetória para identificar o cliente e especifique o carrinho a atualizar.

| Nome            | Tipo     | Necessário | Descrição                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **id cliente** | string   | Yes      | Um id de cliente formatado GUID que identifica o cliente.             |
| **cart-id**     | string   | Yes      | Um carro-id formatado GUID que identifica o carrinho.                     |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades do [Carrinho](cart-resources.md) no corpo de pedido.

| Propriedade              | Tipo             | Necessário        | Descrição                                                                                               |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| ID                    | string           | No              | Um identificador de carrinhos que é fornecido após a criação bem sucedida do carrinho.                                  |
| criaçãoTimeStamp     | DateTime         | No              | A data em que o carrinho foi criado, em formato de data- hora. Aplicado após a criação bem sucedida do carrinho.        |
| últimampadatimestamp de Tempos | DateTime         | No              | A data em que o carrinho foi atualizado pela última vez, em formato de data-hora. Aplicado após a criação bem sucedida do carrinho.    |
| expiraçãoTimeStamp   | DateTime         | No              | A data em que o carrinho expirará, em formato de data-hora.  Aplicado após a criação bem sucedida do carrinho.            |
| últimoModifiedUser      | cadeia (de carateres)           | No              | O utilizador que atualizou pela última vez o carrinho. Aplicado após a criação bem sucedida do carrinho.                             |
| lineitems             | Matriz de objetos | Yes             | Uma matriz de recursos [CartLineItem.](cart-resources.md#cartlineitem)                                               |

Esta tabela descreve as propriedades [do CartLineItem](cart-resources.md#cartlineitem) no corpo de pedido.

| Propriedade             | Tipo                        | Necessário     | Descrição                                                                                        |
|----------------------|-----------------------------|--------------|----------------------------------------------------------------------------------------------------|
| ID                   | string                      | No           | Um identificador único para um item de linha de carrinho. Aplicado após a criação bem sucedida do carrinho.                |
| catalogId            | string                      | Yes          | O identificador de artigos de catálogo.                                                                       |
| nome amigável         | cadeia (de carateres)                      | No           | Opcional. O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.              |
| quantidade             | int                         | Yes          | O número de licenças ou instâncias.     |
| currencyCode         | cadeia (de carateres)                      | No           | O código da moeda.                                                                                 |
| billingCycle         | Objeto                      | Yes          | O tipo de ciclo de faturação definido para o período atual.                                              |
| participantes         | Lista de pares de cordas de objeto | No           | Uma coleção de participantes na compra.                                                      |
| provisionamentoContexto  | Cadeia de<do dicionário,> de cordas  | No           | Um contexto utilizado para o provisionamento da oferta.                                                          |
| orderGroup           | cadeia (de carateres)                      | No           | Um grupo para indicar quais os itens que podem ser colocados juntos.                                            |
| erro                | Objeto                      | No           | Aplicado após o carrinho é criado em caso de erro.                                                 |

### <a name="request-example"></a>Exemplo de pedido

```http
PUT /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/65faf57b-0205-47ee-92b3-08dcf233ea73/ HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 496
Expect: 100-continue

{
    {
        "Id":"b4c8fdea-cbe4-4d17-9576-13fcacbf9605",
        "CreationTimestamp":"2018-03-15T17:15:02.3840528Z",
        "LastModifiedTimestamp":"2018-03-15T17:15:02.3840528Z",
        "ExpirationTimestamp":"0001-01-01T00:00:00",
        "LastModifiedUser":"2713ccd7-ea3b-470a-9cfb-451d5d0482cc",
        "LineItems":[
            {
                "Id":0,
                "CatalogItemId":"DG7GMGF0DWTL:0001:DG7GMGF0DSJB",
                "FriendlyName":"A_sample_Azure_RI",
                "Quantity":2,
                "BillingCycle":"one_time",
                "ProvisioningContext": {
                    "SubscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
                    "Scope": "shared",
                    "Duration": "1Year"
                }
            }
        ],
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve o recurso [cart](cart-resources.md) povoado no corpo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 201 Created
Content-Length: 764
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
X-Locale: en-US,en-US
MS-CV: sF/wRa2ih0CzbABc.0
MS-ServerId: 000001
Date: Thu, 15 Mar 2018 17:15:01 GMT
{
    "id": "b4c8fdea-cbe4-4d17-9576-13fcacbf9605",
    "creationTimestamp": "2018-03-15T17:15:02.3840528Z",
    "lastModifiedTimestamp": "2018-03-15T17:15:02.3840528Z",
    "lastModifiedUser": "2713ccd7-ea3b-470a-9cfb-451d5d0482cc",
    "lineItems": [
        {
            "id": 0,
            "catalogItemId": "DG7GMGF0DWTL:0001:DG7GMGF0DSJB",
            "friendlyName": "A_sample_Azure_RI",
            "quantity": 2,
            "currencyCode": "USD",
            "billingCycle": "one_time",
            "ProvisioningContext": {
                "subscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
                "scope": "shared",
                "duration": "1Year"
            }
            "orderGroup": "0"
        }
    ],
    "links": {
        "self": {
            "uri": "/v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/b4c8fdea-cbe4-4d17-9576-13fcacbf9605/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Cart"
    }
}
```
