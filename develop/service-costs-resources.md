---
title: Recursos de custos de serviço
description: Descreve recursos relacionados com serviços adquiridos por um cliente.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8c1e3a05be89eee12d708a3a37e008ec7fa42358eaec7e1f020aaa47e44b452c
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996143"
---
# <a name="service-costs-resources"></a>Recursos de custos de serviço

Descreve recursos relacionados com serviços adquiridos por um cliente.

## <a name="servicecostssummary"></a>ServiceCostsSummary

**O ServiceCostsSummary** contém um resumo que agrega todos os serviços adquiridos pelo cliente especificado durante o período de faturação.

| Propriedade | Tipo | Description |
| -------- | ---- | ----------- |
| detalhes | matriz de [objetos ServiceCostsSummaryDetail](#servicecostssummarydetail) | A lista de detalhes de custo de serviço, distinguida pelo tipo de fatura.|
| ligações | [RecursosLinks](utility-resources.md#resourcelinks) | Os recursos ligam-se. |
| atributos | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados. |

> [!IMPORTANT]
> **Os campos da mesa seguinte estão a ser depreciados.** Para recuperar resumos de custos de serviço recorrentes e únicos, utilize o campo **de detalhes.** O campo **de detalhes** é descrito na tabela anterior. Consulte os valores de dados correspondentes do campo de **detalhes,** mas não os campos de nível de raiz.

| Propriedade | Tipo | Description |
| -------- | ---- | ----------- |
| billingStartDate | data | O início do período de faturação. |
| billingEndDate | data | O fim do período de faturação. |
| pré-xTotal | double | O total de pré-impostos de todos os custos para o cliente. |
| imposto  | double | O imposto total incorrido em todos os itens adquiridos pelo cliente. |
| afterTaxTotal | double | O custo total líquido de todos os itens adquiridos pelo cliente. |
| currencyCode | string | Representa a moeda utilizada para os custos. |
| moedaSymbol | string | O símbolo da moeda usado para os custos. |
| customerId | string | A identificação do cliente que fez a compra. |

## <a name="servicecostssummarydetail"></a>ServiceCostsSummaryDetail

**ServiceCostsSummaryDetail** descreve um resumo do custo de serviço que agrega todos os serviços adquiridos pelo cliente especificado durante o período de faturação (de faturas recorrentes ou pontuais).

| Propriedade | Tipo | Description |
| -------- | ---- | ----------- |
| faturaType | string | A faturaType que o custo de serviço resumo foi gerado. |
| resumo | [ServiceCostsSummary](#servicecostssummary) | O resumo do custo de serviço agregado por um cliente sob um tipo de fatura. |

## <a name="servicecostlineitem"></a>ServiceCostLineItem

**O ServiceCostLineItem** descreve um único item comprado pelo cliente.

> [!IMPORTANT]
> As seguintes propriedades *aplicam-se apenas aos* itens da linha de custos de serviço em que o produto é uma *compra única*: **produtoId**, **produtoName,** **skuId,** **skuName,** **availabilityId,** **publisherId,** **publisherName,** **termAndBillingCycle,** **discountDetails**. Estas propriedades *não se aplicam a* itens de linha de serviço onde o produto é uma compra *recorrente.* Por exemplo, estas propriedades *não se aplicam* a Office 365 e Azure baseados em subscrições.

| Propriedade                 | Tipo                           | Description                                                          |
|--------------------------|--------------------------------|----------------------------------------------------------------------|
| startDate                | cadeia no formato de data-hora UTC | A data de início da acusação.                                       |
| endDate                  | cadeia no formato de data-hora UTC | A data final para a acusação.                                         |
| subscriçãoSDemê-se | string                         | O nome amigável para a assinatura.                              |
| subscriptionId           | string                         | O identificador de assinatura.                                         |
| orderId                  | string                         | O identificador da ordem.                                                |
| offerId                  | string                         | O identificador da oferta.                                                |
| oferecerName                | string                         | O nome da oferta.                                                      |
| revendedorMPNId            | string                         | Usado apenas em cenários de parceiros de dois níveis. Refere-se ao identificador MPN. |
| chargeType               | string                         | O tipo de carga associado.                                          |
| quantidade                 | número                         | A quantidade de unidades utilizadas ou adquiridas.                             |
| unitPrice                | número                         | O preço por unidade.                                                  |
| pré-xTotal              | número                         | A taxa total por este item antes de impostos.                         |
| imposto                      | número                         | A carga fiscal total incorrida por este item.                         |
| afterTaxTotal            | número                         | O custo total líquido deste item.                                    |
| currencyCode             | string                         | Representa a moeda utilizada para os custos.                          |
| moedaSymbol           | string                         | O símbolo da moeda usado para os custos.                              |
| customerId               | string                         | A identificação do cliente que fez a compra.                          |
| nome do cliente             | string                         | O nome do cliente que fez a compra.                        |
| faturaNumber            | string                         | O número de fatura a que esta linha pertence.                   |
| productId                | string                         | O identificador de produto.                                              |
| skuId                    | string                         | O identificador Sku.                                                  |
| disponibilidadeid           | string                         | O identificador de disponibilidade.                                         |
| produtoName              | string                         | O nome do produto.                                                    |
| skuName                  | string                         | O nome sku.                                                        |
| publisherName            | string                         | O nome da editora.                                                  |
| publisherId              | string                         | O identificador de editores.                                            |
| termoAndBillingCycle      | string                         | O termo e o ciclo de faturação.                                          |
| descontoDesdetas          | string                         | Os detalhes do desconto.                                                |

## <a name="servicecostssummarylinks"></a>ServiceCostsSummaryLinks

| Propriedade             | Tipo                               | Description                         |
|----------------------|------------------------------------|-------------------------------------|
| serviçoCostLineItems | [Ligação](utility-resources.md#link) | O URI para recuperar os itens de linha. |
| self                 | [Ligação](utility-resources.md#link) | O auto-URI.                       |
