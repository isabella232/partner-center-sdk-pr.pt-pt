---
title: Verifique o inventário
description: Saiba como usar as APIs do Partner Center para verificar o inventário para obter um conjunto específico de itens de catálogo. Pode fazê-lo para identificar os produtos de um cliente ou SKUs.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6921760abc0b95aff820467e84b3e8e9435731cd
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770087"
---
# <a name="check-the-inventory-of-catalog-items-using-partner-center-apis"></a>Verifique o inventário de itens de catálogo usando APIs do Partner Center

**Aplica-se a:**

- Partner Center

Como verificar o inventário para obter um conjunto específico de itens de catálogo.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Uma ou mais identificações de produtos. Opcionalmente, os IDs SKU também podem ser especificados.

- Qualquer contexto adicional necessário para verificar o inventário dos SKU(s) referenciados pelo produto fornecido/SKU ID(s). Estes requisitos podem variar por tipo de produto/SKU e podem ser determinados a partir da propriedade [Da SKU's](product-resources.md#sku) **InventoryVariables.**

## <a name="c"></a>C\#

Para verificar o inventário, construa um objeto [InventoryCheckRequest](product-resources.md#inventorycheckrequest) utilizando um objeto [InventoryItem](product-resources.md#inventoryitem) para cada item a ser verificado. Em seguida, utilize um acessório **IAggregatePartner.Extensions,** passe-o para **o Produto** e, em seguida, selecione o país utilizando o método **ByCountry().** Por fim, ligue para o método **CheckInventory()** com o seu objeto **InventoryCheckRequest.**

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string subscriptionId;
string countryCode;
string productId;

// Build the inventory check request details object.
var inventoryCheckRequest = new InventoryCheckRequest()
{
    TargetItems = new InventoryItem[]{ new InventoryItem { ProductId = productId } },
    InventoryContext = new Dictionary<string, string>()
    {
      { "customerId", customerId },
      { "azureSubscriptionId", subscriptionId }
      { "armRegionName", armRegionName }
    }
};

// Get the inventory results.
var inventoryResults = partnerOperations.Extensions.Product.ByCountry(countryCode).CheckInventory(inventoryCheckRequest);
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/extensions/product/checkInventory?country={country-code} HTTP/1.1                        |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para verificar o inventário.

| Nome                   | Tipo     | Necessário | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| código de país           | string   | Sim      | Uma identificação país/região.                                            |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Os detalhes do pedido de inventário, constituído por um recurso [InventoryCheckRequest](product-resources.md#inventorycheckrequest) contendo um ou mais recursos [do InventárioItem.](product-resources.md#inventoryitem)

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/extensions/product/checkinventory?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: d1b1981a-e088-4610-870a-eebec96d6bcd
MS-CorrelationId: 4acb26a1-3536-4081-bc7d-092869a4961a
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json

{"TargetItems":[{"ProductId":"DZH318Z0BQ3P"}],"InventoryContext":{"customerId":"d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d","azureSubscriptionId":"3A231FBE-37FE-4410-93FD-730D3D5D4C75","armRegionName":"Europe"}}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o corpo de resposta contém uma coleção de objetos [InventoryItem](product-resources.md#inventoryitem) povoados com os detalhes da restrição, se algum for aplicável.

>[!NOTE]
>Se uma entrada InventoryItem representar um item que não foi encontrado no catálogo, não será incluído na coleção de saída.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 1021
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4acb26a1-3536-4081-bc7d-092869a4961a
MS-RequestId: d1b1981a-e088-4610-870a-eebec96d6bcd
X-Locale: en-US
[
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "0039",
        "isRestricted": true,
        "restrictions": [
            {
                "reasonCode": "NotAvailableForSubscription",
                "description": "Restriction identified of type 'Location' with values 'japanwest'.",
                "properties": {
                    "type": "Location",
                    "values": "japanwest"
                }
            }
        ]
    },
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "0038",
        "isRestricted": true,
        "restrictions": [
            {
                "reasonCode": "NotAvailableForSubscription",
                "description": "Restriction identified of type 'Location' with values 'japanwest'.",
                "properties": {
                    "type": "Location",
                    "values": "japanwest"
                }
            }
        ]
    },
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "000S",
        "isRestricted": false,
        "restrictions": []
    },
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "0011",
        "isRestricted": false,
        "restrictions": []
    }
]
```
