---
title: Azure gasta recursos da API
description: Saiba como os parceiros da CSP podem usar as APIs do Partner Center para visualizar e gerir os gastos e utilização do parceiro e cliente Azure contra o seu orçamento.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8b51ccbcdaee18b6d5b3bd1b9531a64b22c8bac5a9d95e6cf94291ee802ed5d9
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115992403"
---
# <a name="azure-spending-api-resources-to-manage-partner-or-customer-spending-and-usage-against-a-budget"></a>Azure gasta recursos de API para gerir gastos de parceiros ou clientes e uso contra um orçamento 

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Fornecedor de Soluções em Nuvem parceiros (CSP) podem ver e gerir os seus gastos de Azure através de APIs do Partner Center. Também podem visualizar programáticamente os gastos dos seus clientes contra um orçamento de despesas da Azure.

Para obter mais informações, consulte [cenários em que os parceiros da CSP podem utilizar as APIs do Partner Center para gerir contas e encomendas de clientes e parceiros.](scenarios.md)

## <a name="partner-usage-management"></a>Gestão de utilização de parceiros

- [Obtenha um resumo de utilização do parceiro](get-a-partner-usage-summary.md) utilizando o recurso **PartnerUsageSummary**
- [Obtenha registos de utilização para todos os clientes](get-a-customer-s-usage-records.md) que utilizem o recurso **CustomerMonthlyUsageRecord**

## <a name="customer-usage-management"></a>Gestão do uso do cliente

- [Obtenha o resumo de utilização de um cliente](get-a-customer-usage-summary.md) utilizando o recurso **CustomerUsageSummary**
- [Obtenha todos os registos de utilização de subscrição para um cliente](get-a-customer-subscription-s-usage-records.md) utilizando o recurso **SubscriptionMonthlyUsageRecord**

## <a name="subscription-usage-management"></a>Gestão de utilização de assinaturas

- [Obtenha um resumo de utilização por subscrição](get-a-customer-subscription-usage-summary.md) utilizando o recurso **SubscriptionUsageSummary**
- [Obtenha todos os registos mensais de utilização de uma subscrição](get-all-monthly-usage-records-for-a-subscription.md) utilizando o recurso **AzureResourceMonthlyUsageRecord**
- [Obtenha dados de utilização para uma subscrição por recurso](get-a-customer-subscription-resource-usage-records.md) utilizando o recurso **ResourceUsageRecord**
- [Obtenha dados de utilização para uma subscrição por medidor](get-a-customer-subscription-meter-usage-records.md) utilizando o recurso **MeterUsageRecord**

## <a name="azure-spending-budget-management"></a>Gestão orçamental de gastos Azure

- [Obtenha o orçamento de utilização de um cliente](get-a-customer-s-usage-spending-budget.md) utilizando o recurso **CustomerUsageSummary**
- [Atualizar o orçamento de utilização de um cliente](update-a-customer-s-usage-spending-budget.md) utilizando o recurso **CustomerUsageSummary**
