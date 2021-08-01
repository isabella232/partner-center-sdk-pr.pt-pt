---
title: Criar um carrinho
description: Saiba como usar as APIs do Partner Center para adicionar um pedido para um cliente num carrinho. O tópico inclui informações sobre a criação de um carrinho e quaisquer pré-requisitos.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: d23c162b5eddd0fbe91b11faafa5c4debfb7a4a8
ms.sourcegitcommit: 59950cf131440786779c8926be518c2dc4bc4030
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2021
ms.locfileid: "115009193"
---
# <a name="create-a-cart-with-a-customer-order"></a>Criar um carrinho com uma encomenda de cliente

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Pode adicionar um pedido para um cliente num carrinho. Para obter mais informações sobre o que está atualmente disponível para vender, consulte [as ofertas do Partner no programa Fornecedor de Soluções em Nuvem.](/partner-center/csp-offers)

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Para criar uma encomenda para um cliente:

1. Instantiizar um objeto do Carrinho.

2. Crie uma lista de objetos **CartLineItem** e atribua a lista à propriedade lineItems do carrinho. Cada item da linha do carrinho contém a informação de compra de um produto. Deve ter pelo menos um item de linha de carrinho.

3. Obtenha uma interface para as operações de carrinhos ligando para o método **IAggregatePartner.Customers.ById** com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface da propriedade **Cart.**

4. Ligue para o método **Criar** ou **Criar** Para criar o carrinho.

### <a name="c-example"></a>Exemplo \# C

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

var cart = new Cart()
{
    LineItems = new List<CartLineItem>()
    {
        new CartLineItem()
        {
      /* Microsoft Azure Subscription */
            Id = 0,
            CatalogItemId = "MS-AZR-0145P",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1Y"
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 1,
            CatalogItemId = "DZH318Z0BQ36:004G:DZH318Z08C0S",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P1Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 2,
            CatalogItemId = "DZH318Z0BQ36:004J:DZH318Z08B8X",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P3Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Perpetual Software */
            Id = 3,
            CatalogItemId = "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime
        },
        new CartLineItem()
        {
      /* SaaS */
            Id = 4,
            CatalogItemId = "DZH318Z0BXWC:0002:DZH318Z0BMRV",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1M"
        },
        new CartLineItem()
        {
      /* SaaS Free Trial */
            Id = 5,
            CatalogItemId = "DZH318Z0C0WF:0001:DZH318Z0BP69",
            Quantity = 10,
            BillingCycle = BillingCycleType.None,
            TermDuration = "P1M",
            RenewsTo = new RenewsTo
            {
                TermDuration = "P1Y"
            }
        }
    }
};

cart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Para criar uma encomenda para um cliente:

1. Instantiizar um objeto do Carrinho.

2. Crie uma lista de objetos **CartLineItem** e atribua a lista aos itens de linha do carrinho. Cada item da linha do carrinho contém a informação de compra de um produto. Deve ter pelo menos um item de linha de carrinho.

3. Obtenha uma interface para as operações de carrinhos ligando para o **IAggregatePartner.getCustomers ().função byId** com o ID do cliente para identificar o cliente e, em seguida, recuperar a interface da função **getCart.**

4. Ligue para a função **criar** o carrinho.

## <a name="java-example"></a>Exemplo de Java

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String subscriptionId;
// String catalogItemId;

CartLineItem lineItem = new CartLineItem();

lineItem.setBillingCycle(BillingCycleType.OneTime);
lineItem.setCatalogItemId(catalogItemId);
lineItem.setFriendlyName("Sample RI Purchase");
lineItem.setQuantity(1);

Map<String, String> provisioningContext = new HashMap<String,String>();

provisioningContext.put("duration", "3Years");
provisioningContext.put("scope", "shared");
provisioningContext.put("subscriptionId", subscriptionId);

lineItem.setProvisioningContext(provisioningContext);

List<CartLineItem> lineItemList = new ArrayList<CartLineItem>();
lineItemList.add(lineItem);

Cart cart = new Cart();
cart.setLineItems(lineItemList);

Cart cartCreated = partnerOperations.getCustomers().byId(customerId).getCarts().create(cart);
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Para criar uma encomenda para um cliente:

1. Instantiizar um objeto do Carrinho.

2. Crie uma lista de objetos **CartLineItem** e atribua a lista aos itens de linha do carrinho. Cada item da linha do carrinho contém a informação de compra de um produto. Deve ter pelo menos um item de linha de carrinho.

3. Execute o comando [**New PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) para criar o carrinho.

```powershell
# $customerId
# $subscriptionId
# $catalogItemId

$lineItem = New-Object -TypeName Microsoft.Store.PartnerCenter.PowerShell.Models.Carts.PSCartLineItem

$lineItem.BillingCycle = 'OneTime'
$lineItem.CatalogItemId = $catalogItemId
$lineItem.FriendlyName = 'Sample RI Purchase'
$lineItem.ProvisioningContext.Add('duration', '1Year')
$lineItem.ProvisioningContext.Add('scope', 'shared')
$lineItem.ProvisioningContext.Add('subscriptionId', $subsciptionId)
$lineItem.Quantity = 10

New-PartnerCustomerCart -CustomerId $customerId -LineItems $lineItem
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/carts HTTP/1.1                        |

### <a name="uri-parameter"></a>Parâmetro URI

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
| lineitems             | Matriz de objetos | Sim             | Uma matriz de recursos [CartLineItem.](cart-resources.md#cartlineitem)                                     |

Esta tabela descreve as propriedades [do CartLineItem](cart-resources.md#cartlineitem) no corpo de pedido.

|      Propriedade       |            Tipo             | Necessário |                                                                                         Descrição                                                                                         |
|---------------------|-----------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         ID          |           cadeia (de carateres)            |    No    |                                                     Um identificador único para um item de linha de carrinho. Aplicado após a criação bem sucedida do carrinho.                                                     |
|      catalogId      |           string            |   Sim    |                                                                                O identificador de artigos de catálogo.                                                                                 |
|    nome amigável     |           cadeia (de carateres)            |    No    |                                                    Opcional. O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.                                                    |
|      quantidade       |             int             |   Sim    |                                                                            O número de licenças ou instâncias.                                                                             |
|    currencyCode     |           cadeia (de carateres)            |    No    |                                                                                     O código da moeda.                                                                                      |
|    billingCycle     |           Objeto            |   Sim    |                                                                    O tipo de ciclo de faturação definido para o período atual.                                                                    |
|    participantes     | Lista de pares de cordas de objeto |    Não    |                                                                Uma coleção de PartnerId on Record (MPNID) na compra.                                                                 |
| provisionamentoContexto | Cadeia de<do dicionário,> de cordas  |    Não    | Informação necessária para o provisionamento de alguns itens no catálogo. A propriedade de ProvisioningVariables num SKU indica quais propriedades são necessárias para itens específicos no catálogo. |
|     orderGroup      |           cadeia (de carateres)            |    No    |                                                                   Um grupo para indicar quais os itens que podem ser colocados juntos.                                                                   |
|        erro        |           Objeto            |    Não    |                                                                     Aplicado após o carrinho é criado se houver um erro.                                                                      |
|     renovaTo        | Matriz de objetos            |    Não    |                                                    Uma variedade de [recursos Renovados.](cart-resources.md#renewsto)                                                                            |
|     AttestationAccepted        | Booleano            |    Não    |                                                   Indica acordo para oferecer ou sku condições. Requerido apenas para ofertas ou skus onde a SkuAttestationProperties ou OfferAttestationProperties aplicam Attestation é Verdadeira.                                                                             |

Esta tabela descreve as propriedades [Renovações](cart-resources.md#renewsto) No corpo de pedido.

| Propriedade              | Tipo             | Necessário        | Descrição |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termoDuração          | cadeia (de carateres)           | No              | Uma representação ISO 8601 da duração do período de renovação. Os valores suportados atuais são **P1M** (1 mês) e **P1Y** (1 ano). |

### <a name="request-example"></a>Exemplo de pedido

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts HTTP/1.1
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
  "lineItems": [
    {
    /* Microsoft Azure Subscription */
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1Y"
    },
    {
    /* Azure Reserved Instance */
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      }
    },
    {
    /* Azure Reserved Instance */
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "single"
      }
    },
    {
    /* Perpetual Software */
      "id": 3,
      "catalogItemId": "DG7GMGF0DWTL:0001:DG7GMGF0DSFM",
      "quantity": 1,
      "billingCycle": "one_time"
    },
    {
    /* SaaS */
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1M"
    },
  {
    /* SaaS Free Trial */
       "id": 5,
       "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
       "quantity": 10,
       "billingCycle": "none",
       "termDuration": "P1M",
       "renewsTo": {
         "termDuration": "P1Y"
       }
    }
  ]
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
  "id": "3655b1a0-b1c9-4268-9824-577fdbc4d0be",
  "creationTimestamp": "2019-01-16T00:45:41.6062996Z",
  "lastModifiedTimestamp": "2019-01-16T00:45:41.6062996Z",
  "expirationTimestamp": "2019-01-16T01:00:54.4188497Z",
  "lastModifiedUser": "1824b7fc-2fac-4478-b177-66823c40ab75",
  "status": "Active",
  "lineItems": [
    {
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1Y",
      "orderGroup": "OMS-0"
    },
    {
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 3,
      "catalogItemId": "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "orderGroup": "0"
    },
    {
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1M",
      "orderGroup": "1"
    },
  {
      "id": 5,
      "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
      "quantity": 10,
      "currencyCode": "USD",
      "billingCycle": "none",
      "termDuration": "P1M",
      "renewsTo": {
  "termDuration": "P1Y"
      },
    "orderGroup": "2"
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/28045616-f6b9-462f-9701-0d89b5e65c44/carts/3655b1a0-b1c9-4268-9824-577fdbc4d0be",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Cart"
  }
}
```
