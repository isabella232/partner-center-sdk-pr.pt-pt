---
title: Recursos de atualização do produto
description: Você pode usar vários recursos relacionados com atualizações de produtos partner center para um plano Azure. Estes incluem ProductUpgradeRequest, ProductUpgradesEligibility, ProductUpgradesStatus, UpgradesLineItem, UpgradeProduct e ErrorDetails.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d8975f0a135c88796a21f8abab944e53181f591e
ms.sourcegitcommit: faea78fe3264cbafc2b02c04d98d5ce30e992124
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274620"
---
# <a name="product-upgrade-resources"></a>Recursos de atualização do produto

**Aplica-se a:**

- Partner Center

Pode utilizar os seguintes recursos para obter informações sobre atualizações de produtos do Partner Center a partir de uma subscrição do Microsoft Azure (MS-AZR-0145P) para um plano Azure.

## <a name="productupgraderequest"></a>ProdutoUpgradeRequest

O recurso **ProductUpgradesRequest** fornece informações sobre o objeto de pedido de atualização do produto.

| Propriedade      | Tipo                                                          | Descrição                                                |
|---------------|---------------------------------------------------------------|------------------------------------------------------------|
| customerId    | string                                                        | Uma cadeia formatada pelo GUID que identifica o cliente.      |
| produtoAmily | string                                                        | A família de produtos para a qual a atualização é solicitada. |
| atributos    | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                   |

## <a name="productupgradeseligibility"></a>Melhoria do Produto

O recurso **ProductUpgradesEligibility** fornece informações sobre a elegibilidade do cliente para a atualização de um produto.

| Propriedade      | Tipo                                                          | Descrição                                                                      |
|---------------|---------------------------------------------------------------|----------------------------------------------------------------------------------|
| customerId    | string                                                        | Uma cadeia formatada pelo GUID que identifica o cliente.                            |
| produtoAmily | string                                                        | A família de produtos para a qual a atualização é solicitada.                       |
| isEligível    | bool                                                          | O valor bool indica se o cliente é elegível para atualização solicitada. |
| upgradeId     | string                                                        | O ID de upgrade se um upgrade de produto para uma família dada já está no lugar.        |
| reason        | string                                                        | A razão pela qual o cliente não é elegível para atualização do produto.                |
| produtoAmily | string                                                        | A família de produtos para a qual a atualização é solicitada.                       |
| atributos    | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                                         |

## <a name="productupgradesstatus"></a>ProdutoUpgradesStatus

O **recurso ProductUpgradesStatus** fornece informações sobre o estado de uma atualização do produto.

| Propriedade | Tipo   | Descrição                                          |
|----------|--------|------------------------------------------------------|
| Id       | string | Uma cadeia formatada pelo GUID que identifica a atualização. |
| produtoAmily       | string                                                         | A família de produtos para a qual a atualização é solicitada.
| status              | string                                                         | O estado da atualização do produto.
| lineitems           | matriz de [recursos UpgradesLineItem](#upgradeslineitem)       | Uma série de objetos que fornecem informações sobre os detalhes da atualização de cada item de linha que fazia parte do corpo de pedido.
| erroDetails        | [Recurso ErrorDetails](#errordetails)                         | Os detalhes de erro para a atualização solicitados.
| atributos          | [RecursosTributos](utility-resources.md#resourceattributes)  | Os atributos dos metadados. |

## <a name="upgradeslineitem"></a>UpgradesLineItem

O recurso **UpgradesLineItem** descreve o estado dos detalhes da atualização do produto para cada item de linha do pedido.

| Propriedade      | Tipo                                                          | Descrição                                       |
|---------------|---------------------------------------------------------------|---------------------------------------------------|
| fonteProduto | [Objeto upgrade-produto](#upgradeproduct)                      | Informação do produto de origem a ser atualizado. |
| targetProduct | [Objeto upgrade-produto](#upgradeproduct)                      | Informação da atualização do posto de produto alvo.   |
| atualizadoDate  | cadeia no formato de data-hora UTC                                | A data em que a subscrição foi atualizada.           |
| status        | string                                                        | O estado da atualização do produto.                |
| erroDetails  | [Recurso ErrorDetails](#errordetails)                        | Os detalhes de erro para a atualização solicitados.          |
| atributos    | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                          |

## <a name="upgradeproduct"></a>UpgradeProduto

O recurso **UpgradeProduct** fornece informações sobre o produto que está a ser atualizado.

| Propriedade   | Tipo                                                          | Descrição                                          |
|------------|---------------------------------------------------------------|------------------------------------------------------|
| ID         | string                                                        | Uma corda formatada guid que identifica o produto. |
| name       | string                                                        | O nome amigável do produto a ser atualizado.         |
| atributos | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                             |

## <a name="errordetails"></a>ErrorDetails

O recurso **ErrorDetails** fornece detalhes sobre erros durante o processo de atualização.

| Propriedade   | Tipo                                                          | Descrição                                       |
|------------|---------------------------------------------------------------|---------------------------------------------------|
| code       | string                                                        | Um código de erro quando a atualização do produto falha.      |
| message    | string                                                        | A mensagem de erro quando a atualização do produto falha. |
| atributos | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                          |
