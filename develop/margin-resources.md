---
title: Recursos de margem
description: Recursos que representam margens. Inclui recursos para descrever as margens.
ms.date: 09/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 83ea2f95c72f4e5074e3396ef226462b5b007878
ms.sourcegitcommit: deb3207935fb5a74df515ed0fd4ffec90e6a143c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/07/2021
ms.locfileid: "129646422"
---
# <a name="margin-resources"></a>Recursos de margem

Recursos que representam margens disponíveis. Inclui recursos para descrever uma margem.  

O Fornecedor independente de Software (ISV) pode criar descontos ou margens para fornecedores específicos de soluções cloud (CSPs). Abaixo estão os recursos que representam e descrevem as margens.
                
## <a name="margin"></a>Margin                   
                        
Representa uma margem aval para uma determinada CSP.
                
| Nome            | Tipo            | Descrição                               |
|-----------------|-----------------|-------------------------------------------|
| ID              | string          | Identificador único para a margem.         |
| margemPercentage | número         | Um desconto percentual aplicado ao preço de venda a retalho da CSP.  |
| productId       | string          | O ID do produto está disponível para.   |
| produtoT    | string          | O título do produto a margem está disponível para. |
| productType     | string          | O tipo de produto para o qual a margem está disponível.   |
| publisherName   | string          | O nome do ISV que criou a margem.  |
| skuId           | string          | A margem do SKU ID está disponível para.  |
| skuTitle        | string          | O título SKU a margem está disponível para. |
| startDate       | string          | A data de início da margem está disponível. |
| endDate         | string          | A data final em que a margem está disponível. |
| status          | string          | Estado que indicia se a margem está disponível. |
| statusDate      | string          | A data em que o estado foi atualizado pela última vez. |

## <a name="definitions"></a>Definições

Diferentes tipos de artefactos que descrevem margens.                    

| Nome            | Descrição          |
|-----------------|----------------------|
| Margin |  Define uma margem individual.  |    
| MarginSearchResponse |  Define os dados de resposta à margem.  |  
        
## <a name="related-documentation"></a>Documentação relacionada

- [Margens na visão geral do Partner Center](/partner-center/csp-commercial-marketplace-margins)
- [Comprar ofertas do marketplace](/partner-center/csp-commercial-marketplace-purchase)
- [Gerir ofertas do marketplace](/partner-center/csp-commercial-marketplace-manage)
- [Obtenha uma lista de margens](get-margins.md)
- [Faça o download de uma lista de margens](download-margins.md)
