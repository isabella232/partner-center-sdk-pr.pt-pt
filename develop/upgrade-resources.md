---
title: Atualizar recursos
description: Descreve os recursos utilizados para atualizar um utilizador de uma subscrição de origem para uma subscrição-alvo.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4c57994d1b1e7659df5e6448578422f6d9c21fee
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529822"
---
# <a name="upgrade-resources"></a>Atualizar recursos

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Descreve os recursos utilizados para atualizar um utilizador de uma subscrição de origem para uma subscrição-alvo.

## <a name="upgrade"></a>Atualizar

Descreve o comportamento de um recurso de upgrade individual.

| Propriedade      | Tipo                   | Description                                                                                  |
|---------------|------------------------|----------------------------------------------------------------------------------------------|
| TargetOffer   | Oferta                  | A oferta da subscrição do alvo.                                                        |
| Atualização DeType   | string                 | O tipo de upgrade: "nenhum", \_ "upgrade apenas", ou "upgrade \_ com transferência de \_ \_ licença".         |
| Iselegível    | boolean                | Identifica se a atualização pode ser realizada.                                                  |
| Quantidade      | número inteiro                | A quantidade da nova oferta a ser comprada. Predefinições na quantidade de subscrição de origem. |
| UpgradeErrors | matriz de UpgradeErrors | As razões para a atualização não pode ser realizada, se aplicável.                                      |
| Atributos    | RecursosTributos     | Os atributos de metadados correspondentes à atualização.                                        |

## <a name="upgradeerror"></a>UpgradeError

Descreve uma razão pela qual uma atualização não pode ser realizada.

| Propriedade          | Tipo               | Description                                                                                                                                                                                                                                                                                                                                                                                     |
|-------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Código              | string             | O código de erro associado à questão: "outros", "permissões de administração delegadas \_ \_ \_ desativadas", "estado de subscrição \_ não \_ \_ ativo", "tipos de \_ \_ \_ serviços contraditórios", "conflitos de concordância", "contexto de utilizador \_ \_ necessário", "complemento de subscrição \_ \_ \_ presente", "subscrição \_ não tem \_ \_ \_ \_ quaisquer caminhos de \_ upgrade", "oferta de alvo de subscrição \_ não \_ \_ \_ encontrada", ou "subscrição \_ não \_ prevista". |
| Description       | cadeia (de carateres)             | Texto amigável descrevendo o erro.                                                                                                                                                                                                                                                                                                                                                             |
| Detalhes adicionais | string             | Detalhes adicionais sobre o erro.                                                                                                                                                                                                                                                                                                                                                         |
| Atributos        | RecursosTributos | Os metadados correspondem ao erro.                                                                                                                                                                                                                                                                                                                                             |

## <a name="upgraderesult"></a>UpgradeResult

Descreve o resultado do processo de atualização da subscrição.

| Propriedade             | Tipo                        | Description                                                                          |
|----------------------|-----------------------------|--------------------------------------------------------------------------------------|
| SourceSubscriptionId | string                      | O identificador da assinatura de origem.                                           |
| TargetSubscriptionID | string                      | O identificador da assinatura do alvo.                                           |
| Atualização DeType          | string                      | O tipo de upgrade: "nenhum", \_ "upgrade apenas", ou "upgrade \_ com transferência de \_ \_ licença". |
| UpgradeErrors        | matriz de UpgradeErrors      | Erros encontrados ao tentar executar a atualização, se aplicável.           |
| Licenciadorores        | matriz de UserLicenseErrrors | Erros encontrados durante a tentativa de migrar licenças de utilizador, se aplicável.          |
| Atributos           | RecursosTributos          | Os metadados atribuem correspondentes à licença.                                |

## <a name="userlicenseerror"></a>UserLicenseError

Descreve erros decorrentes da transferência falhada da licença de utilizador.

| Propriedade     | Tipo                   | Description                                                               |
|--------------|------------------------|---------------------------------------------------------------------------|
| UserObjectId | string                 | O único identificado do objeto do utilizador.                                 |
| Name         | string                 | O nome do utilizador.                                                     |
| E-mail        | string                 | O e-mail do utilizador.                                                    |
| Erros       | matriz de ServiceFaults | Uma lista de exceções lançadas ao tentar realizar transferência de licença de utilizador. |
| Atributos   | RecursosTributos     | Os metadados atribuem correspondentes à licença.                     |

