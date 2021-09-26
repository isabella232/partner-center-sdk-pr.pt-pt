---
title: Verifique a elegibilidade da promoção
description: Verifique se uma transação de clientes é elegível para uma determinada promoção.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: ad3346ddca0438c0011e2c6fd03c3ec00b1a1fe3
ms.sourcegitcommit: 7be22de808a10fa2d05577d6497086c8ca3f678a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128716010"
---
# <a name="verify-promotion-eligibility"></a>Verificar elegibilidade para a promoção

**Aplica-se a**

- Partner Center

**Funções adequadas**

- Administrador global
- Agente administrativo

> [!Note] 
> As novas mudanças de Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da Microsoft 365 e dynamics 365 novas experiências de comércio de pré-visualização técnica.

Os parters podem verificar se uma transação de clientes é elegível para uma determinada promoção. Este método devolve *True* se a transação do cliente for elegível para uma determinada promoção. Os parceiros podem verificar a elegibilidade antes de submeter uma transação para garantir que a promoção será aplicada.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- A elegibilidade inclui a disponibilidade de sku do produto que está a ser comprada, o ID de promoção a ser avaliado, a quantidade, duração do prazo e ciclo de faturação da transação.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **PUBLICAR**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customerId}/promotionEligibilities HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de consulta para devolver as promoções disponíveis.

| Nome                    | Tipo     | Necessário | Descrição                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **customerId**  | **string** | Y        | O valor é um cliente-inquilino-id formatado pelo GUID, que é um identificador que lhe permite especificar um cliente.          |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

O corpo inclui uma coleção de PromoçõesEligibilidadesRequestItems. Esta tabela descreve as propriedades para uma [PromoçãoEligibilidadesRequestItem](promotion-resources.md#promotioneligibilitiesrequestitem).

| Propriedade        | Tipo             | Necessário        | Descrição                                                                                               |
|-----------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| catalogItemId   | string           | Yes             | O identificador de artigos de catálogo.                         |
| quantidade        | int | Yes        | O número de licenças ou instâncias.                 |
| termoDuração    | DateTime         | Yes             | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são P1M (um mês), P1Y (um ano) e P3Y (três anos).   |
| billingCycle    | string | Yes     | O valor que indica o tipo de ciclo de faturação.   |
| promotionId     | string           | Yes             | O identificador de artigos de promoção.                       | 

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/46632f71-f052-4384-8f84-4cdb6c12c2a1/promotionEligibilities HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US

{
    "items": [
        {
            "catalogItemId": "CFQ7TTC0KZ59:0001:CFQ7TTC0KZ59",
            "quantity": 1,
            "termDuration": "P1Y",
            "billingCycle": "Monthly",
            "promotionId": " CFQ7TTC0HL8W:0001:CFQ7TTC0K59M"
        }
    ]
}

```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma recolha de resultados de elegibilidade.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e mais informações de depurações. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e mais parâmetros. Para obter a lista completa, consulte [Códigos de Erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "totalCount": 1,
    "items": [
        {
            "catalogItemId": "CFQ7TTC0KZ59:0001:CFQ7TTC0KZ59",
            "quantity": 1,
            "termDuration": "P1Y",
            "billingCycle": "Monthly",
            "eligibilities": [
                {
                    "promotionId": "CFQ9TTC0HH4R:0001:CFQ8HGC0K77G",
                    "isEligible": false,
                    "errors": [
                        {
                            "type": "SeatCount",
                            "minRequiredSeats": 25,
                            "maxRequiredSeats": 500
                        },
                        {
                            "type": "Term",
                            "eligibleTerms": [
                                {
                                    "duration": "P3Y",
                                    "billingCycle": "Monthly"
                                }
                            ]
                        },
                        {
                            "type": "FirstPurchase"
                        }
                    ]
                }
            ],
            "attributes": {
                "objectType": "PromotionEligibilities"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

