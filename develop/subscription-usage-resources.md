---
title: Recursos de utilização de subscrição
description: Os recursos de utilização da subscrição descrevem subscrições com faturação baseada no uso. Estas subscrições têm registos de utilização diários e mensais, juntamente com um resumo de utilização para cada período de pagamento.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e8af4e9b8a4660b5bc9d287ece258dca9aa9ba7a749cfdc89e9c9b47e4af61b1
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115990278"
---
# <a name="subscription-usage-resources"></a>Recursos de utilização de subscrição

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Pode utilizar os seguintes recursos de utilização da subscrição para obter informações de utilização para uma subscrição específica com faturação baseada em uso. Estas subscrições têm registos de utilização diários e mensais, juntamente com um resumo de utilização para cada período de pagamento.

## <a name="subscriptiondailyusagerecord"></a>SubscriçãoDailyUsageRecord

*O **recurso SubscriptionDailyUsageRecord** é obsoleto e pode produzir resultados imprecisos. Recomendamos que atualize as suas aplicações para utilizar as APIs descritas nos [registos de utilização de um cliente para a Azure](get-a-customer-s-utilization-record-for-azure.md) e [obtenha preços para Microsoft Azure.](get-prices-for-microsoft-azure.md)*

O **recurso SubscriptionDailyUsageRecord** descreve o quanto uma subscrição é usada num único dia.

| Propriedade         | Tipo               | Description                                                                                   |
|------------------|--------------------|-----------------------------------------------------------------------------------------------|
| DataSUSed         | string             | O dia, em formato de data- hora, que a subscrição foi usada.                                 |
| ResourceId       | string             | O GUID. A identificação única do recurso.                                                          |
| ResourceName     | string             | O nome do recurso.                                                                     |
| TotalCost        | decimal             | O custo total estimado da utilização dos recursos na subscrição no dia especificado.     |
| CurrencyLocale   | string             | O local em que a subscrição foi utilizada determina a moeda a utilizar na fatura. |
| LastModifiedDate (Carga incremental: LastModifiedDate) | string             | O dia, em formato de data- hora, que este disco foi modificado pela última vez.                             |
| Atributos       | RecursosTributos | Os metadados atribuem correspondentes ao recurso.                                        |

## <a name="subscriptionmonthlyusagerecord"></a>SubscriçãoMonthlyUsageRecord

O **recurso SubscriptionMonthlyUsageRecord** descreve o quanto uma subscrição é usada num único mês.

| Propriedade         | Tipo               | Description                                                                                   |
|------------------|--------------------|-----------------------------------------------------------------------------------------------|
| Estado           | string             | O estado da subscrição: "nenhum", "ativo", "suspenso", ou "eliminado".                  |
| PartnerOnRecord  | string             | "A MPN ID do sócio em registo."                                                        |
| OfferId          | string             | O GUID. O ID da oferta relacionada com esta subscrição.                                       |
| Id               | string             | O GUID. O ID da subscrição ou recurso.                                                 |
| Name             | string             | O nome da subscrição ou recurso.                                                     |
| TotalCost        | decimal             | O custo total estimado da utilização dos recursos na subscrição no mês especificado.   |
| CurrencyLocale   | string             | O local em que a subscrição foi utilizada determina a moeda a utilizar na fatura. Disponível para Microsoft Azure (MS-AZR-0145P) subscrições. |
| CurrencyCode     | string             | Recebe ou define o código de moeda. Disponível para recursos de subscrição do plano Azure.                                         |
| USDTotalCost     | decimal             | Obtém ou define o custo total estimado em USD. Disponível para planos Azure.                                         |
| LastModifiedDate (Carga incremental: LastModifiedDate) | string             | O dia, em formato de data- hora, que este disco foi modificado pela última vez.                             |
| Atributos       | RecursosTributos | Os metadados atribuem correspondentes ao recurso.                                        |

## <a name="subscriptionusagesummary"></a>SubscriçãoUsageSummary

O **recurso SubscriptionUsageSummary** descreve o quanto uma subscrição específica foi utilizada no período de faturação atual.

| Propriedade         | Tipo               | Description                                                                                                            |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------------|
| ResourceId       | string             | O GUID. O ID da subscrição ou recurso. No contexto do CustomerMonthlyUsageRecord, este ID é o ID do cliente. |
| ResourceName     | string             | O nome da subscrição ou recurso. No contexto do CustomerMonthlyUsageRecord, este nome é o nome do cliente. |
| BillingStartDate | data               | A data de início do período de faturação atual, em formato de data-hora.                                                     |
| BillingEndDate   | data               | A data final do período de faturação atual, em formato de data-hora.                                                       |
| TotalCost        | double             | O custo total estimado da utilização dos recursos na subscrição durante o período de faturação especificado.               |
| CurrencyLocale   | string             | O local em que a subscrição foi utilizada determina a moeda a utilizar na fatura. Disponível para Microsoft Azure (MS-AZR-0145P) subscrições. |
| CurrencyCode   | string             | Recebe ou define o código de moeda. Disponível para planos Azure.                                         |
| USDTotalCost   | decimal             | Obtém ou define o custo total estimado em USD. Disponível para recursos de subscrição do plano Azure.                                         |
| LastModifiedDate (Carga incremental: LastModifiedDate) | string             | O dia, em formato de data- hora, que este disco foi modificado pela última vez.                                                      |
| Ligações            | RecursosLinks      | As ligações de recursos correspondentes ao SubscriptionUsageSummary.                                                      |
| Atributos       | RecursosTributos | Os atributos de metadados correspondentes ao SubscriptionUsageSummary.                                                 |
