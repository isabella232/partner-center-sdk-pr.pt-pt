---
title: Obter uma lista de disponibilidade para um SKU (por país)
description: Como obter uma coleção de disponibilidades para o produto especificado e SKU por país de cliente.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b97a4ce85b5edd9de1301a577988f8c54096ebeb
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769122"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-country"></a>Obter uma lista de disponibilidade para um SKU (por país)

**Aplica-se a:**

- Partner Center

Este artigo descreve como obter uma coleção de disponibilidades em um determinado país para um produto especificado e SKU.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um identificador de produto.

- Um identificador SKU.

- Um país.

## <a name="c"></a>C\#

Para obter a lista de [disponibilidades](product-resources.md#availability) para um [SKU:](product-resources.md#sku)

1. Siga os passos em [Get a SKU by ID](get-a-sku-by-id.md) para obter a interface para uma determinada sku's operations.

2. A partir da interface SKU, selecione a propriedade **Availabilities** para obter uma interface com as operações para disponibilidades.

3. (Opcional) Utilize o método **ByTargetSegment()** para filtrar as disponibilidades por segmento alvo.

4. Ligue **para Get()** ou **GetAsync para** recuperar uma coleção das disponibilidades para este SKU.

``` csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string targetSegment;
string productIdForAzureReservation;
string skuIdForAzureReservation;

// Get the availabilities.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.Get();

// Get the availabilities, filtered by target segment.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.BySegment(targetSegment).Get();

// Get the availabilities for an Azure reservation product and sku which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ById(skuIdForAzureReservation).Availabilities.ByReservationScope("AzurePlan").Get();

// Get the availabilities for an Azure reservation product and sku which are applicable to Azure plans only.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ById(skuIdForAzureReservation).Availabilities.Get();

```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment} HTTP/1.1     |

### <a name="uri-parameters"></a>Parâmetros URI

Use os seguintes parâmetros de caminho e consulta para obter uma lista de disponibilidades para um SKU.

| Nome                   | Tipo     | Necessário | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| id produto             | string   | Sim      | Uma corda que identifica o produto.                           |
| sku-id                 | string   | Sim      | Uma corda que identifica o SKU.                               |
| código de país           | string   | Sim      | Uma identificação país/região.                                            |
| segmento-alvo         | cadeia (de carateres)   | No       | Uma corda que identifica o segmento alvo utilizado para a filtragem. |
| reservationScope | cadeia (de carateres)   | No | Ao consultar uma lista de disponibilidades para um SKU de Reserva Azure, especifique `reservationScope=AzurePlan` para obter uma lista de disponibilidades aplicáveis ao AzurePlan. Exclua este parâmetro para obter uma lista de disponibilidades aplicáveis às subscrições do Microsoft Azure (MS-AZR-0145P).  |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-examples"></a>Solicitar exemplos

#### <a name="availabilities-for-sku-by-country"></a>Disponibilidades para SKU por país

Siga este exemplo para obter uma lista de disponibilidades para um dado SKU por país:

```http
GET http:// api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
```

#### <a name="availabilities-for-vm-reservations-azure-plan"></a>Disponibilidades para reservas VM (plano Azure)

Siga este exemplo para obter uma lista de disponibilidades por país para Azure VM reserva SKUs. Este exemplo é para os SKUs que se aplicam aos planos Azure:

```http
GET https://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="availabilities-for-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Disponibilidades para reservas VM para subscrições microsoft Azure (MS-AZR-0145P)

Siga este exemplo para obter uma lista de disponibilidades por país para reservas Azure VM que são aplicáveis às subscrições do Microsoft Azure (MS-AZR-0145P).

```http
GET https://api.partnercenter.microsoft.com/v1/productsDZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureAzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [**de Disponibilidade.**](product-resources.md#availability)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter uma lista completa, consulte [os códigos de erro do Partner Center](error-codes.md).

Este método devolve os seguintes códigos de erro:

| Código de Estado HTTP     | Código de erro   | Descrição                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| 403                  | 400030       | Não é permitido o acesso ao **objetivo solicitado.**                                                     |

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58,83b644b5-e54a-4bdc-b354-f96c525b3c58
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02,70324727-62d8-4195-8f99-70ea25058d02
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNRXHNrdXNcMDAwMVxhdmFpbGFiaWxpdGllcw==?=
X-Powered-By: ASP.NET
Date: Wed, 14 Mar 2018 22:19:37 GMT
Content-Length: 808

{
    "totalCount": 1,
    "items": [
        {
            "id": "DZH318XZXVNF",
            "productId": "DZH318Z0BQ3Q",
            "skuId": "0001",
            "catalogItemId": "DZH318Z0BQ3Q:0001:DZH318XZXVNF",
            "defaultCurrency": {
                "code": "USD",
                "symbol": "$"
            },
            "segment": "commercial",
            "country": "US",
            "isPurchasable": true,
            "isRenewable": false,
            "terms": [{
                "duration": "P1Y",
                "description": "1 Year Prepaid"
            }],
            "product": { ... },
            "sku": { ... },
            "links": {
                "self": {
                    "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318Z0HMKQ?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetSegment=commercial",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
