---
title: Recursos de utilização do cliente
description: Recursos para clientes com subscrições baseadas em uso e orçamentos de utilização mensal (incluindo CustomerMonthlyUsageRecord, CustomerUsageSummary, PartnerUsageSummary e SpendingBudget).
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ec82fcfe6c08a8ad55dd1fb48984859b954dd3c8
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768792"
---
# <a name="customer-usage-resources"></a>Recursos de utilização do cliente

**Aplica-se a:**

- Partner Center
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Os clientes com subscrições baseadas em uso podem ter um orçamento de utilização mensal. Este orçamento estabelece um limite para o uso máximo do cliente e permite ao parceiro acompanhar o seu uso ao longo do tempo.

> [!NOTE]
> Os números de utilização do cliente são estimativas (não valores finais), que não devem ser usadas para efeitos de faturação.

## <a name="customermonthlyusagerecord"></a>CustomerMonthlyUsageRecord

**CustomerMonthlyUsageRecord** representa o custo monetário estimado do uso de um cliente no mês em curso.

| Propriedade         | Tipo               | Descrição                                                              |
|------------------|--------------------|--------------------------------------------------------------------------|
| Orçamento           | GastosOrçamento     | O orçamento de despesas atribuído ao cliente.                          |
| Por centoUsed      | decimal             | A percentagem utilizada fora do orçamento atribuído.                        |
| ResourceId       | string             | O identificador único do recurso.                                   |
| ResourceName     | string             | O nome do recurso.                                                |
| TotalCost        | decimal             | O custo total estimado de utilização dos recursos na subscrição.|
| CurrencyLocale   | string             | Local de moeda do cliente. Disponível para subscrições Microsoft Azure (MS-AZR-0145P).            |
| CurrencyCode     | string             | Recebe ou define o código de moeda. Disponível para planos Azure.           |
| USDTotalCost     | decimal             | Obtém ou define o custo total estimado em USD. Disponível para planos Azure.                                         |
| IsUpgraded       | bool             | Obtém ou define um valor que indique se a subscrição Azure do cliente está atualizada. O valor **verdadeiro** representa clientes que têm um plano Azure.                         |
| LastModifiedDate (Carga incremental: LastModifiedDate) | date               | A data em que os dados de utilização foram modificados pela última vez.                               |
| Atributos       | RecursosTributos | Os metadados correspondem ao registo de utilização.               |

## <a name="customerusagesummary"></a>CustomerUsageSummary

**CustomerUsageSummary** representa um resumo do uso do cliente durante todo um período de faturação.

| Propriedade         | Tipo               | Descrição                                                                                                      |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------|
| Orçamento           | GastosOrçamento     | O orçamento de despesas atribuído ao cliente.                                                                  |
| ResourceId       | string             | O identificador único do recurso. No contexto do CustomerMonthlyUsageRecord, este id é o id do cliente. |
| ResourceName     | string             | O nome do recurso. No contexto do CustomerMonthlyUsageRecord, este é o nome do cliente.               |
| BillingStartDate | date               | A data de início do período de faturação em curso.                                                                    |
| BillingEndDate   | date               | A data final do período de faturação em curso.                                                                      |
| TotalCost        | decimal             | O custo total estimado de utilização dos recursos na subscrição.                                         |
| CurrencyLocale   | string             | Local de moeda do cliente. Disponível para subscrições Microsoft Azure (MS-AZR-0145P).                                         |
| CurrencyCode     | string             | Recebe ou define o código de moeda. Disponível para planos Azure.                                         |
| USDTotalCost     | decimal             | Obtém ou define o custo total estimado em USD. Disponível para recursos de subscrição do plano Azure.                                         |
| LastModifiedDate (Carga incremental: LastModifiedDate) | date               | A data em que os dados de utilização foram modificados pela última vez.                                                                       |
| Ligações            | RecursosLinks      | Os links de recursos correspondentes ao resumo de utilização.                                                           |
| Atributos       | RecursosTributos | Os metadados atribuem-se ao resumo de utilização.                                                      |

## <a name="partnerusagesummary"></a>PartnerUsageSummary

**PartnerUsageSummary** representa um resumo ao nível do parceiro do orçamento de utilização para todos os clientes.

| Propriedade         | Tipo               | Descrição                                                                                                      |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------|
| E-mailsToNotify   | matriz de cadeias (de carateres)   | A lista de endereços de e-mail para notificações.                                                                   |
| CustomerOverBudget | número inteiro          | O número de clientes que estão acima do orçamento.                                                                    |
| ClientesTrendingOver | número inteiro       | O número de clientes que estão perto de ultrapassar o orçamento.                                                     |
| ClientesWithUsageBasedSubscriptions  | número inteiro | O número de clientes com uma subscrição baseada em uso.                                               |
| ResourceId       | string             | O identificador único do recurso. No contexto do CustomerMonthlyUsageRecord, este id é o id do cliente. |
| ResourceName     | string             | O nome do recurso. No contexto do CustomerMonthlyUsageRecord, este é o nome do cliente.               |
| BillingStartDate | date               | A data de início do período de faturação em curso.                                                                    |
| BillingEndDate   | date               | A data final do período de faturação em curso.                                                                      |
| TotalCost        | decimal             | O custo total estimado de todo o uso do cliente com base no uso atual desde o início do período de faturação.      |
| CurrencyLocale   | string             | O local da moeda.                                                                                             |
| LastModifiedDate (Carga incremental: LastModifiedDate) | date               | A data em que os dados de utilização foram modificados pela última vez.                                                                       |
| Ligações            | RecursosLinks      | Os links de recursos correspondentes ao resumo de utilização.                                                           |
| Atributos       | RecursosTributos | Os metadados atribuem-se ao resumo de utilização.                                                      |

## <a name="spendingbudget"></a>GastosOrçamento

**Gastos O Orçamento** representa o orçamento atribuído a este cliente para subscrições baseadas em uso.

| Propriedade   | Tipo               | Descrição                                                                                         |
|------------|--------------------|-----------------------------------------------------------------------------------------------------|
| Montante     | decimal             | O orçamento atribuído. Se o valor for nulo, não há orçamento de despesas atribuído a este cliente. |
| Atributos | RecursosTributos | Os metadados atribuem ao orçamento.                                                |
