---
title: Obtenha a disponibilidade por ID
description: Obtém a disponibilidade para o produto especificado e SKU usando um ID de disponibilidade.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: c31bc12d8d484cc8042f36aa865145600d9e6738
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760203"
---
# <a name="get-the-availability-by-id"></a>Obtenha a disponibilidade por ID

Obtém a disponibilidade para o produto especificado e SKU usando um ID de disponibilidade.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Uma identificação de produto.

- Um SKU ID.

- Uma identificação de disponibilidade.

## <a name="c"></a>C\#

Para obter detalhes de uma [disponibilidade](product-resources.md#availability)específica, comece por usar os passos em [Get a SKU by ID](get-a-sku-by-id.md) para obter a interface para uma determinada [sku's](product-resources.md#sku) operations. A partir da interface resultante, selecione a propriedade **Availabilities** para obter uma interface com as operações disponíveis para Disponibilidades. Depois disso, passe o ID de disponibilidade para o método **ById()** para obter as operações para essa disponibilidade específica e, em seguida, ligue para **Get()** ou **GetAsync()** para recuperar os detalhes da disponibilidade.

```csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string availabilityId;

// Get the availability details.
var availability = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.ById(availabilityId).Get();
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Para obter detalhes de uma [disponibilidade](product-resources.md#availability)específica, comece por usar os passos em [Get a SKU by ID](get-a-sku-by-id.md) para obter a interface para uma determinada [sku's](product-resources.md#sku) operations. A partir da interface resultante, selecione a função **getAvailabilities** para obter uma interface com as operações disponíveis para Disponibilidades. Depois disso, passe o ID de disponibilidade para a função **byId()** para obter as operações para essa disponibilidade específica e, em seguida, ligue para a função **get()** para recuperar os detalhes da disponibilidade.

```java
IAggregatePartner partnerOperations;
String countryCode;
String productId;
String skuId;
String availabilityId;

// Get the availability details.
Availability availability = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().byId(skuId).getAvailabilities().byId(availabilityId).get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Para obter detalhes de uma [disponibilidade](product-resources.md#availability)específica, execute a [**Oferta de Produtos de Produtos de Parceiros**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) e especifique os parâmetros **AvailabilityId**, **CountryCode,** **ProductId** e **SkuId** para recuperar os detalhes da disponibilidade.

```powershell
Get-PartnerProductAvailability -Product $productId -SkuId $skuId -AvailabilityId $availabilityId
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code} HTTP/1.1         |

### <a name="uri-parameter"></a>Parâmetro URI

Use os seguintes parâmetros de caminho e consulta para obter uma disponibilidade específica usando um ID de disponibilidade.

| Nome                   | Tipo     | Necessário | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| id produto             | string   | Yes      | Uma corda formatada GUID que identifica o produto.            |
| sku-id                 | string   | Yes      | Uma corda formatada GUID que identifica o SKU.                |
| disponibilidade id        | string   | Yes      | Uma cadeia formatada GUID que identifica a disponibilidade.       |
| código de país           | string   | Yes      | Uma identificação país/região.                                            |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318XZXPHL?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 2e12a576-ded5-437e-a5ec-dbfbcbd1624c
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém um recurso [Availability.](product-resources.md#availability)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

Este método devolve os seguintes códigos de erro:

| Código de Estado HTTP     | Código de erro   | Description                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| 404                  | 400013       | O produto não foi encontrado.                                                                                    |
| 404                  | 400018       | O SKU não foi encontrado.                                                                                        |
| 404                  | 400019       | Disponibilidade não encontrada.                                                                                   |

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58,83b644b5-e54a-4bdc-b354-f96c525b3c58
MS-RequestId: 2e12a576-ded5-437e-a5ec-dbfbcbd1624c,2e12a576-ded5-437e-a5ec-dbfbcbd1624c
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNRXHNrdXNcMDAwMVxhdmFpbGFiaWxpdGllc1xEWkgzMThaMEhNS1E=?=
X-Powered-By: ASP.NET
Date: Wed, 14 Mar 2018 22:19:43 GMT
Content-Length: 440

{
    "id": "DZH318XZXPHL",
    "productId": "DZH318Z0BQ3Q",
    "skuId": "0001",
    "catalogItemId": "DZH318Z0BQ3Q:0001:DZH318XZXPHL",
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
            "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318XZXPHL?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
