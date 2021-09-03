---
title: Obter uma lista de produtos (por cliente)
description: Pode utilizar um identificador de clientes para obter uma coleção de produtos por cliente.
ms.assetid: ''
ms.date: 02/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 1f3f38271b97ceba143c819ec03758ad1b9c0d3b
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123455766"
---
# <a name="get-a-list-of-products-by-customer"></a>Obter uma lista de produtos (por cliente)

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Pode utilizar os seguintes métodos para obter uma coleção de produtos para um cliente existente.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido                                                                                                              |
|--------|--------------------------------------------------------------------------------------------------------------------------|
| POST   | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/produtos?targetView={targetView} HTTP/1.1 |

#### <a name="request-uri-parameters"></a>Solicite parâmetros URI

| Nome               | Tipo | Necessário | Descrição                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | GUID | Yes | O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente. |
| **targetView** | string | Yes | Identifica a visão do catálogo. Os valores suportados são: <br/><br/>**Azure,** que inclui todos os itens Azure<br/><br/>**AzureReservations**, que inclui todos os itens de reserva Azure<br/><br/>**AzureReservationsVM,** que inclui todos os itens de reserva de máquina virtual (VM)<br/><br/>**AzureReservationsSQL,** que inclui todos os itens de reserva SQL<br/><br/>**AzureReservationsCosmosDb,** que inclui todos os itens de reserva da base de dados cosmos<br/><br/>**MicrosoftAzure**, que inclui itens para subscrições Microsoft Azure **(MS-AZR-0145P)** e planos Azure<br/><br/>**OnlineServices**, que inclui todos os itens de serviço online. Este targetView inclui marketplace comercial, serviços baseados em licenças transdicionais e novos serviços baseados em licenças de comércio<br/><br/>**Software**, que inclui todos os itens de software<br/><br/>**SoftwareSUSELinux,** que inclui todos os itens SUSE Linux de software<br/><br/>**SoftwarePerpetual,** que inclui todos os itens de software perpétuos<br/><br/>**SoftwareSubscriptions**, que inclui todos os itens de subscrição de software  |

### <a name="request-header"></a>Cabeçalho do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

Pedido de uma lista de produtos à base de uso da Azure disponíveis para um determinado cliente. Os produtos para Microsoft Azure (MS-AZR-0145P) e planos Azure serão devolvidos para clientes em nuvem pública:

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products?targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```
#### <a name="new-commerce-license-based-services"></a>Novos serviços baseados em licenças de comércio

> [!Note] 
> As novas alterações ao Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365

Siga este exemplo para obter uma lista de produtos por país para novos serviços baseados em licenças de comércio como parte da nova experiência de comércio experiência técnica pré-visualização. Novos serviços baseados em licenças de comércio serão identificados por id e displayNames valores do **OnlineServicesNCE**. Veja o exemplo de resposta abaixo.

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products?targetView=OnlineServices HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a>Resposta de repouso

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

Este método devolve os seguintes códigos de erro:

| Código de Estado HTTP | Código de erro   | Description                     |
|------------------|--------------|---------------------------------|
| 403 | 400036 | Não é permitido o acesso ao targetView solicitado. |

### <a name="response-example-for-microsoft-azure-and-azure-plan"></a>Exemplo de resposta para Microsoft Azure e plano Azure

```http
HTTP/1.1 200 OK
Content-Length: 1909
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cad955c2-8efc-47fe-b112-548ff002ba18
MS-RequestId: ae7288e2-2673-4ad4-8c12-7aad818d5949

{
    "totalCount": 2,
    "items": [
        {
            "id": "MS-AZR-0145P",
            "productId": "9DEA7946-EC2C-441E-9FFD-E3B275F7E838",
            "title": "Microsoft Azure",
            "description": "Azure Cloud Solution Provider offer for Partner and Resellers",
            "minimumQuantity": 1,
            "maximumQuantity": 1,
            "isTrial": false,
            "supportedBillingCycles": [
                "monthly"
            ],
            "purchasePrerequisites": [
                "MicrosoftCloudAgreement"
            ],
            "actions": [
                "Refund"
            ],
            "dynamicAttributes": {
                "isMicrosoftProduct": true,
                "billingType": "usage",
                "category": "Enterprise",
                "isAddon": false,
                "prerequisiteSkus": [],
                "rank": 1413,
                "hasAddOns": false,
                "isAutoRenewable": false,
                "upgradeTargetOffers": null,
                "conversionTargetOffers": [],
                "unitType": "Usage-based",
                "limitUnitOfMeasure": "None",
                "limit": 0,
                "reselleeQualifications": [],
                "resellerQualifications": []
            },
            "links": {
                "availabilities": {
                    "uri": "/products/9DEA7946-EC2C-441E-9FFD-E3B275F7E838/skus/MS-AZR-0145P/availabilities?country=US&targetSegment=Commercial",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/9DEA7946-EC2C-441E-9FFD-E3B275F7E838/skus/MS-AZR-0145P?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
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
                    "uri": "/products/DZH318Z0BPS6/skus/0001/availabilities?country=US&targetSegment=Commercial",
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
    ],
    "links": {
        "self": {
            "uri": "/customers/e2a0c0f3-0f74-4d1c-808c-dfa511481913/products/all/skus?targetView=MicrosoftAzure&targetSegment=Commercial",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
### <a name="response-example-for-new-commerce-license-based-services"></a>Exemplo de resposta para novos serviços baseados em licenças de comércio

> [!Note] 
> As novas alterações ao Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365

```http
{
  "totalCount": 19,
  "items": [{
      "id": "CFQ7TTC0LH18",
      "title": "Microsoft 365 Business Basic",
      "description": "Best for businesses that need professional email, cloud file storage, and online meetings & chat. Desktop versions of Office apps like Excel, Word, and PowerPoint not included. For businesses with up to 300 employees.",
      "productType": {
        "id": "OnlineServicesNCE",
        "displayName": "OnlineServicesNCE"
      },
      "isMicrosoftProduct": true,
      "publisherName": "Microsoft Corporation",
      "links": {
        "skus": {
          "uri": "/products/CFQ7TTC0LH18/skus?country=US",
          "method": "GET",
          "headers": []
        },
        "self": {
          "uri": "/products/CFQ7TTC0LH18?country=US",
          "method": "GET",
          "headers": []
        }
      }
    },
    ...
  ],
  "links": {
    "self": {
      "uri": "/products?country=US&targetView=OnlineServices",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Collection"
  }
}
```
