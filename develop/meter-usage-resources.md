---
title: Recurso de registo de utilização do medidor
description: Pode utilizar o recurso MeterUsageRecord para descrever o custo monetário estimado da utilização do nível do medidor de uma subscrição no ciclo de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8c02c859d1d8ba3edd236d83d3056cb82533f7e8
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768857"
---
# <a name="meter-usage-record-resource"></a>Recurso de registo de utilização do medidor

**Aplica-se a:**

- Partner Center

Pode utilizar o recurso **MeterUsageRecord** para descrever o custo monetário estimado da utilização do nível do medidor de uma subscrição no ciclo de faturação atual.

## <a name="meterusagerecord"></a>MedidorUsageRecord

| Propriedade         | Tipo               | Descrição                                                                                   |
|------------------|--------------------|-----------------------------------------------------------------------------------------------|
| SubscriptionId           | string             | Um GUID correspondente ao identificador de um recurso de [subscrição](subscription-resources.md#subscription)partner Center, que representa uma subscrição do Microsoft Azure (MS-AZR-0145P) ou um plano Azure. Para as subscrições do Microsoft Azure (MS-AZR-0145P), este valor é o identificador de subscrição de comércio. Para os recursos de subscrição do plano Azure, este valor é o identificador do plano Azure.                  |
| MeterId  | string             | Recebe ou define o identificador do medidor.                                                        |
| MeterName          | string             | Recebe ou define o nome do medidor.                                       |
| Categoria               | string             | Obtém ou define a categoria de recurso Azure.                                                 |
| Subcategoria             | string             |  Obtém ou define a subcategoria de recurso Azure.                                                     |
| QuantidadeUsed        | decimal             | Obtém ou define a quantidade do recurso Azure utilizado.   |
| Unidade   | string             | Obtém ou define a unidade de medida para o recurso Azure. |
| TotalCost   | decimal             | Obtém ou define o custo total estimado de utilização. |
| CurrencyLocale   | string             | O local onde a assinatura foi utilizada. Esta propriedade determina a moeda que é usada na fatura. Esta propriedade está disponível para subscrições microsoft Azure (MS-AZR-0145P). |
| CurrencyCode   | string             | Recebe ou define o código de moeda. Esta propriedade está disponível para planos Azure.                                         |
| USDTotalCost   | decimal             | Obtém ou define o custo total estimado em USD. Esta propriedade está disponível para planos Azure.                                         |
| LastModifiedDate (Carga incremental: LastModifiedDate) | string             | O dia (em formato de data) que este disco foi modificado pela última vez.                             |
| Atributos       | RecursosTributos | Os metadados atribuem correspondentes ao recurso.                                        |                                           |
