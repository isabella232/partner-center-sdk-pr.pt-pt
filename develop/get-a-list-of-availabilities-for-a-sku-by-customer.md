---
title: Obter uma lista de disponibilidade para um SKU (por cliente)
description: Você pode obter uma coleção de disponibilidades para um produto especificado e SKU pelo cliente usando os identificadores de cliente, produto e SKU.
ms.assetid: ''
ms.date: 02/16/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 0fe1c078509d408d677387980020656dd655e567
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123455972"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-customer"></a>Obter uma lista de disponibilidade para um SKU (por cliente)

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Pode utilizar os seguintes métodos para obter uma coleção de disponibilidades para um produto especificado e sKU disponível para um determinado cliente.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um identificador de produto **(id produto).**

- Um identificador SKU **(sku-id).**

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido                                                                                                                 |
|--------|-----------------------------------------------------------------------------------------------------------------------------|
| POST   | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/produtos/{product-id}/skus/{sku-id} HTTP/1.1 |

### <a name="request-uri-parameters"></a>Solicite parâmetros URI

| Nome               | Tipo | Necessário | Descrição                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| cliente-inquilino-id | GUID | Yes | O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente. |
| id produto | string | Yes | Uma corda que identifica o produto. |
| sku-id | string | Yes | Uma corda que identifica o SKU. |

### <a name="request-header"></a>Cabeçalho do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products/DZH318Z0BPS6/skus/0001/availabilities HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a>Resposta do REST

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

Este método devolve os seguintes códigos de erro:

| Código de Estado HTTP | Código de erro | Description |
|------------------|------------|-------------|
| 404 | 400013 | O produto-mãe não foi encontrado. |

### <a name="response-example-for-azure-plan"></a>Exemplo de resposta para plano Azure

```http
HTTP/1.1 200 OK
Content-Length: 1909
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cad955c2-8efc-47fe-b112-548ff002ba18
MS-RequestId: ae7288e2-2673-4ad4-8c12-7aad818d5949
{
    "id": "0001",
    "productId": "DZH318Z0BPS6",
    "title": "Microsoft Azure plan",
    "description": "Microsoft Azure plan (MS-AZR-0017G)",
    "minimumQuantity": 1,
    "maximumQuantity": 1,
    "isTrial": false,
    "supportedBillingCycles": [
        "one_time"
    ],
    "purchasePrerequisites": [
        "MicrosoftCustomerAgreement"
    ],
    "inventoryVariables": [],
    "provisioningVariables": [],
    "actions": [
        "Refund"
    ],
    "dynamicAttributes": {
        "isMicrosoftProduct": true,
        "pilotProgram": "modernazurepilot"
    },
    "links": {
        "availabilities": {
            "uri": "/products/DZH318Z0BPS6/skus/0001/availabilities?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BPS6/skus/0001?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
### <a name="response-example-for-new-commerce-license-based-services"></a>Exemplo de resposta para novos serviços baseados em licenças de comércio

> [!Note] 
> As novas alterações ao Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365

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
    "id": "CFQ7TTC0K971",
    "productId": "CFQ7TTC0LH18",
    "skuId": "0001",
    "catalogItemId": "CFQ7TTC0LH18:0001:CFQ7TTC0K971",
    "defaultCurrency": {
        "code": "USD",
        "symbol": "$"
    },
    "segment": "commercial",
    "country": "US",
    "isPurchasable": true,
    "isRenewable": true, 
    "renewalInstructions": [
        {
            "applicableTermIds": [
                "5aeco6mffyxo"
            ],
            "renewalOptions": [
                {
                    "renewToId": "CFQ7TTC0LH18:0001",
                    "isAutoRenewable": true
                }
            ]
        },
     …
    ],
    "terms": [
        {
            "id": "5aeco6mffyxo",
            "duration": "P1Y",
            "description": "One-Year commitment for monthly/yearly billing",
            "billingCycle": "Annual",
            "cancellationPolicies": [
                {
                    "refundOptions": [
                        {
                            "sequenceId": 0,
                            "type": "Full",
                            "expiresAfter": "P1D"
                        }
                    ]
                }
            ]
        },
       …
    ],
    "links": {
        "self": {
            "uri": "/products/CFQ7TTC0LH18/skus/0001/availabilities/CFQ7TTC0K971?country=US",
            "method": "GET",
            "headers": []
        }
    },
        "links": {
            "availabilities": {
                "uri": "/products/CFQ7TTC0LH18/skus/0001/availabilities?country=US",
                "method": "GET",
                "headers": []
            },
            "self": {
                "uri": "/products/CFQ7TTC0LH18/skus/0001?country=US",
                "method": "GET",
                "headers": []
            }
        }
    }
}
```
