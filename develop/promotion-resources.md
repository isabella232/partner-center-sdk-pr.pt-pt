---
title: Recursos de promoção
description: Descreve os recursos para promoções aplicadas a transações para novas subscrições de comércio.
ms.date: 09/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 6a0b38576f5756a127fe6ba787f970db9ac59be3
ms.sourcegitcommit: 7be22de808a10fa2d05577d6497086c8ca3f678a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128716011"
---
# <a name="promotions-resources"></a>Recursos de promoção

**Aplica-se a**

- Partner Center

**Funções adequadas**

- Administrador global
- Agente administrativo

> [!Note] 
> As novas mudanças de Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da Microsoft 365 e dynamics 365 novas experiências de comércio de pré-visualização técnica.

Descreve os recursos para promoções aplicadas a transações para novas subscrições de comércio.

## <a name="promotion"></a>Promotion

Desconto aplicado na compra de um produto SKU se os critérios de elegibilidade forem cumpridos.

| Propriedade          | Tipo                    | Descrição                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| ID | string                  | O identificador de promoção. |
| name | string                  | O nome amigável da promoção. |
| descrição | string                  | Uma descrição da promoção. |
| startDate | string | A data de início para a aplicação da promoção. |
| endDate | string  | A data de fim para a promoção é aplicável. |
| Produtos necessários | lista de Produtos Necessários | Produtos, detalhes SKU e políticas de preços para a qual a promoção é aplicável. | 
| propriedades | lista de propriedades | Propriedades para a promoção, incluindo se a promoção é autoaplicável. | 

## <a name="requiredproducts"></a>Produtos Necessários

Produtos, detalhes SKU e políticas de preços para a qual a promoção é aplicável.

| Propriedade          | Tipo                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| productId| string | Um identificador do produto para o qual a promoção está disponível. |
| skuId | string | Um identificador do SKU a promoção está disponível para. |
| termo | Termo | Um termo que inclui duração de prazo e ciclo de faturação para o qual a promoção está disponível. |
| preçosPolícias| Lista de preçosPolícias | Uma lista de políticas que definem os tipos e valores de desconto de promoção. |

## <a name="term"></a>Termo

Representa um termo para o qual a promoção pode ser adquirida.

| Propriedade          | Tipo                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| duration          | string                  | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são P1M (um mês), P1Y (um ano) e P3Y (três anos). 
| billingCycle      | string | Descreve com que frequência a promoção será aplicada à faturação. Os valores podem incluir Mensal, Anual, OneTime ou Desconhecido. | 

## <a name="pricingpolicies"></a>PreçosPolícias

Descreva os tipos e valores de desconto de promoção.

| Propriedade          | Tipo               | Descrição                                                                  |          
|-------------------|--------------------|------------------------------------------------------------------------------|
| tipo | string | Descreva se o desconto se baseia em percentagens ou descontos de taxa fixa. |
| valor | cadeia (de carateres)  | Define o valor do desconto aplicado. |

## <a name="properties"></a>Propriedades

Propriedades para a promoção.

| Propriedade          | Tipo               | Description                                        |
|-------------------|--------------------|----------------------------------------------------|
| isAutoApplicable  | bool  | Indica se a promoção é aplicada automaticamente ou se precisa de ser passada pelo parceiro. |


## <a name="promotioneligibilitiesrequestitem"></a>PromoçãoEligibilitiesRequestItem

Imóveis que representam uma transação e a elegibilidade de uma promoção.

| Propriedade          | Tipo               | Descrição                                        |
|-------------------|--------------------|----------------------------------------------------|
| ID | int| O identificador de elegibilidade de promoções. |
| catalogItemId | string | O identificador de item de catálogo a que a promoção será aplicada. Inclui iD de produto, ID SKU e ID de disponibilidade. |
| quantidade | int | O número de licenças ou instâncias. |
| termoDuração | string | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são P1M (um mês), P1Y (um ano) e P3Y (três anos). |
| billingCycle | string | Descreve com que frequência a promoção será aplicada à faturação. Os valores podem incluir Mensal, Anual, OneTime ou Desconhecido. | 
| promotionID | string | O identificador de promoção. |

## <a name="promotioneligibilities"></a>PromoçãoEligibilidades

Uma lista de produtos, SKUs, e as suas elegibilidades de promoção.

| Propriedade          | Tipo               | Descrição                                        |
|-------------------|--------------------|----------------------------------------------------|
| ID | int| O identificador de elegibilidade de promoções. |
| catalogItemId | string | O identificador de item de catálogo a que a promoção será aplicada. Inclui ID do produto, ID SKU e ID de disponibilidade. |
| quantidade | int | O número de licenças ou instâncias. |
| termoDuração | string | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são P1M (um mês), P1Y (um ano) e P3Y (três anos). |
| billingCycle | string | Descreve com que frequência a promoção será aplicada à faturação. Os valores podem incluir Mensal, Anual, OneTime ou Desconhecido. | 
| elegibilidade | Lista de PromoçõesEigibilidades | Representa uma lista de resultados de elegibilidade de promoção. |

## <a name="promotioneligibility"></a>Promoção

Uma lista de produtos, SKUs, e as suas elegibilidades de promoção.

| Propriedade          | Tipo               | Description                                        |
|-------------------|--------------------|----------------------------------------------------|
| promotionId | string | O identificador de promoção. |
| isEligível | bool | Descreve se a promoção é elegível para o item de pedido de elegibilidade dado. |
| erros | Lista de PromoçõesEligibilityErrors | Erros que descrevem porque é que um pedido de elegibilidade de promoção não era elegível. | 

## <a name="promotioneligibilityerror"></a>PromoçãoEligibilityError

Explica porque é que um pedido de elegibilidade de promoção não era elegível. 

| Propriedade          | Tipo               | Descrição                                        |
|-------------------|--------------------|----------------------------------------------------|
| tipo | string | Os tipos de erro de elegibilidade da promoção podem incluir InvalidCatalogItemId, InvalidPromotion, PrerequisiteProductOwnership, RedemptionLimit, SeatCount, OfferPurchasedPreviously ou Term. |
| descrição | string | Descreve se a promoção é elegível para o item de pedido de elegibilidade dado. |

## <a name="redemptionlimitpromotioneligibilityerror"></a>RedemptionLimitPromotionEligibilityError

Inclui detalhes sobre o porquê do limite de resgate ter sido ultrapassado.

| Propriedade          | Tipo               | Description                                        |
|-------------------|--------------------|----------------------------------------------------|
| maxPromotionRedemptionCount | int | O número máximo de vezes que uma promoção pode ser adquirido. |
| restantesPromotionRedemptionCount| int | O número restante de vezes que uma promoção pode ser adquirida. |

## <a name="seatcountpromotioneligibilityerror"></a>SeatCountPromotionEligibilityError

Inclui detalhes sobre o porquê do limite de contagem de assentos ter sido ultrapassado. Ambos os valores são nulos.

| Propriedade          | Tipo               | Description                                        |
|-------------------|--------------------|----------------------------------------------------|
| mínimosRequiredSeats | int? | As licenças mínimas que uma promoção irá suportar. |
| máximoRequiredSeats | int? | As licenças máximas que uma promoção irá suportar. |

## <a name="termpromotioneligibilityerror"></a>TermoPromotionEligibilityError

Inclui detalhes sobre o porquê do termo de promoção não ter sido aceite.

| Propriedade          | Tipo               | Description                                        |
|-------------------|--------------------|----------------------------------------------------|
| estão elegíveis | PromoçãoTerm | Os termos elegíveis que uma promoção apoiará. |

## <a name="promotionterm"></a>PromoçãoTerm

Inclui detalhes sobre o porquê do limite de contagem de assentos ter sido ultrapassado.

| Propriedade          | Tipo               | Description                                        |
|-------------------|--------------------|----------------------------------------------------|
| billingCycle | string | Descreve com que frequência a promoção será aplicada à faturação. Os valores podem incluir Mensal, Anual, OneTime ou Desconhecido. |
| duration | string | Duração do termo a ser adquirido. |




