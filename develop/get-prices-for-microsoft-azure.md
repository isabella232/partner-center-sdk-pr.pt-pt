---
title: Obter preços do Microsoft Azure
description: Como obter um Cartão Azure Rate com preços em tempo real para uma oferta Azure. Os preços do Azure são bastante dinâmicos e mudam frequentemente.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8b69e9e3d8e6e4c4e447b308c890c4c054e6a1e5221bb523a5caca041d1ea115
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989114"
---
# <a name="get-prices-for-microsoft-azure"></a>Obter preços do Microsoft Azure

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Como obter um [Cartão Azure Rate](azure-rate-card-resources.md) com preços em tempo real para uma oferta Azure. Os preços do Azure são bastante dinâmicos e mudam frequentemente.

Para acompanhar o uso e ajudar a prever a sua fatura mensal e as faturas para clientes individuais, pode combinar esta consulta do Cartão Azure Rate para obter preços para Microsoft Azure com um pedido de [obter os registos de utilização de um cliente para o Azure](get-a-customer-s-utilization-record-for-azure.md).

Os preços diferem por mercado e por moeda, e esta API tem em conta a localização. Por padrão, a API utiliza as definições de perfil do seu parceiro no Partner Center e no seu idioma do navegador, e essas definições são personalizáveis. A consciência da localização é especialmente relevante se você gerir vendas em vários mercados a partir de um único escritório centralizado. Para obter mais informações, consulte [os parâmetros URI.](#uri-parameters)

## <a name="c"></a>C\#

Para obter o Cartão Azure Rate, ligue para o método [**IAzureRateCard.Get**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.get) para devolver um recurso [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) que contenha os preços Azure.

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.Get();
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: GetAzureRateCard.cs

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Para obter o Cartão Azure Rate, ligue para o **IAzureRateCard.obter** função para devolver detalhes do cartão de retorno que contenham os preços do Azure.

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Para obter o Cartão Azure, execute o comando [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) para devolver os detalhes do cartão de retorno que contenham os preços do Azure.

```powershell
Get-PartnerAzureRateCard
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                        |
|---------|--------------------------------------------------------------------|
| **GET** | *{baseURL}*/v1/ratecards/azure?currency={currency}&região={região} |

### <a name="uri-parameters"></a>Parâmetros URI

| Nome     | Tipo   | Necessário | Descrição                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| moeda | cadeia (de carateres) | No       | Código ISO de três letras opcionais para a moeda em que serão fornecidas as taxas de recursos (por `EUR` exemplo). A predefinição é `USD`. |
| region   | cadeia (de carateres) | No       | Código opcional iso país/região de duas letras que indica o mercado onde a oferta é adquirida (por `FR` exemplo). A predefinição é `US`.        |

Pode incluir o [cabeçalho](headers.md#rest-request-headers) X-Locale opcional no seu pedido. Se não incluir o cabeçalho X-Locale, o valor predefinido ("en-US") é utilizado.

- Se fornecer parâmetros de moeda e região no seu pedido, o valor do X-Locale é usado para determinar a linguagem da resposta.

- Se não fornecer parâmetros de região e moeda no seu pedido, o valor do X-Locale é usado para determinar a região, a moeda e a língua da resposta.

### <a name="request-header"></a>Cabeçalho do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/ratecards/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07ced227-3f32-4eeb-8062-f0bef849a9bc
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>Resposta do REST

Se o pedido for bem sucedido, devolve um recurso [de Cartão Azure Rate.](azure-rate-card-resources.md)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 1545508
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57b25659-fc00-4215-87e7-2b09bac6845d
MS-RequestId: 870118d0-adbb-41a3-82d2-a3d45ade3c73
MS-CV: CYBB8PXMsEukJBIn.0
MS-ServerId: 201021413
Date: Wed, 01 Feb 2017 00:13:45 GMT

{
    "locale": "en",
    "currency": "USD",
    "isTaxIncluded": false,
    "meters": [{
            "id": "4b836326-7e19-46e6-8bce-1b19bb6cd91e",
            "name": "Unlimited Data - 1 Gbps",
            "rates": {
                "0": 7395.0
            },
            "tags": [],
            "category": "Networking",
            "subcategory": "ExpressRoute",
            "region": "Zone 2",
            "unit": "Connections",
            "includedQuantity": 0.0,
            "effectiveDate": "2015-09-01T00:00:00Z"
        }, {
            "id": "1e8f6d9f-8b40-4c97-80cc-cff87a290a93",
            "name": "Compute Hours",
            "rates": {
                "0": 3.9729
            },
            "tags": [],
            "category": "Cloud Services",
            "subcategory": "Standard_L16 Cloud Services",
            "region": "AU East",
            "unit": "1 Hour",
            "includedQuantity": 0.0,
            "effectiveDate": "2016-09-01T00:00:00Z"
        }, {
            "id": "7a2639ce-ae47-4413-9837-6b4f4b78be3d",
            "name": "Compute Hours",
            "rates": {
                "0": 0.1122
            },
            "tags": [],
            "category": "Virtual Machines",
            "subcategory": "Standard_D1_v2 VM (Windows)",
            "region": "BR South",
            "unit": "Hours",
            "includedQuantity": 0.0,
            "effectiveDate": "2017-01-01T00:00:00Z"
        }
    ],
    "offerTerms": [{
            "name": "Overage discount",
            "discount": 0.15,
            "excludedMeterIds": ["53cc0061-0fe2-4249-bf62-e1008c811f5c", "c82dbd27-c978-43a7-ad41-525a90d8962b"],
            "effectiveDate": "2014-01-01T00:00:00"
        }
    ],
    "attributes": {
        "objectType": "AzureRateCard"
    }
}
```
