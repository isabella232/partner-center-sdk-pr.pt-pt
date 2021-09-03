---
title: Recursos de transição
description: Descreve os recursos utilizados para a transição de novas subscrições de comércio.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 44867be3823414ab43957e789c0cd29aef44d956
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123457327"
---
# <a name="transition-resources"></a>Recursos de transição

**Aplica-se a**

- Partner Center

**Funções adequadas**

- Administrador global
- Agente administrativo

> [!Note] 
> As novas alterações de Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.

Descreve os recursos utilizados para a transição de uma nova subscrição de comércio para outra.

## <a name="transitioneliblity"></a>TransiçãoEliblidade

Descreve o comportamento de um recurso de transição de subscrição individual.

| Propriedade          | Tipo                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| CatalogItemId | string                  | O id do catálogo que está a ser verificado. |
| Título  | string                  | O título da SKU. |
| Description | cadeia (de carateres)                  | A descrição do SKU. |
| Quantidade | número inteiro                 | A quantidade da nova oferta a ser comprada. |
| Elegibilidade | lista de TransitionEligibilityDetail | Uma lista de detalhes de elegibilidade de transição. | 

## <a name="transitioneligibilitydetail"></a>TransiçãoEligibilityDetail

Descreve o comportamento de um recurso de detalhes de elegibilidade de transição individual.

| Propriedade          | Tipo                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| Iselegível | boolean | Devolve a elegibilidade é válida ou não. |
| Tipo de Transição | Tipo de Transição | O tipo de transição. Pode ser transition_with_license_transfer ou transition_only. |
| Erros | Lista de TransitErrors | Os metadados correspondem ao erro. |

## <a name="transition"></a>Transição

Descreve o comportamento de um recurso de transição de subscrição individual.

| Propriedade          | Tipo                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| FromCatalogItemId | string                  | O id do item do catálogo. |
| ToCatalogItemId   | string                  | O id do artigo para catálogo. |
| ToSubscriptionId  | string                  | O ID de assinatura Para. Isto só é preenchido se a subscrição mudar. Atualmente apenas o Legacy Upgrade precisa disto, mas a transição parcial moderna também. |
| Quantidade          | número inteiro                 | A quantidade que está a ser transitada para o item do catálogo-alvo. |
| Tipo de Transição    | string              | O tipo de transição. Valores possíveis - transition_only, transition_with_license_transfer.   |
| Eventos            | lista de TransitionEvents | Os acontecimentos da transição. |

## <a name="transitionevent"></a>Transição

Descreve uma razão pela qual uma atualização não pode ser realizada.

| Propriedade          | Tipo               | Descrição                                                                                                                                                                                                                                                                                                                                                                                     |
|-------------------|--------------------|------------------------------------------------------------------------------|
| Name | string | O nome do evento de transição. Valores possíveis Conversão ou LicençaSatribuição. |
| Estado | string  | O estado do evento de transição. Valores possíveis InProgress, Concluído ou Falhado.  |
| CarimboDeDataEHora | DateTime | O calendário utc do evento. |
| Erros | Lista de TransitErrors | Os metadados correspondem ao erro. |

## <a name="transitionerror"></a>TransitError

Representa um erro para a elegibilidade da transferência de assinatura. Fornece uma razão pela qual uma transição não pode ser realizada.

| Propriedade          | Tipo               | Description                                                                                                                                                                                                                                                                                                                                                                                     |
|-------------------|--------------------|--------------------------------------------------------------|
| Código | TransiçãoErrorCode | O código de erro associado ao problema. |
| Description | cadeia (de carateres)  | Texto amigável descrevendo o erro. |

