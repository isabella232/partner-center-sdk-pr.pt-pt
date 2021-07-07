---
title: Azure gasta recursos da API
description: Saiba como os parceiros da CSP podem usar as APIs do Partner Center para visualizar e gerir os gastos e utilização do parceiro e cliente Azure contra o seu orçamento.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 472554de1c354559d5bc4b21959c109467891806
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974323"
---
# <a name="azure-spending-api-resources-to-manage-partner-or-customer-spending-and-usage-against-a-budget"></a><span data-ttu-id="9c972-103">Azure gasta recursos de API para gerir gastos de parceiros ou clientes e uso contra um orçamento</span><span class="sxs-lookup"><span data-stu-id="9c972-103">Azure spending API resources to manage partner or customer spending and usage against a budget</span></span> 

<span data-ttu-id="9c972-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9c972-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9c972-105">Fornecedor de Soluções em Nuvem parceiros (CSP) podem ver e gerir os seus gastos de Azure através de APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="9c972-105">Cloud Solution Provider (CSP) partners can view and manage their Azure spending through Partner Center APIs.</span></span> <span data-ttu-id="9c972-106">Também podem visualizar programáticamente os gastos dos seus clientes contra um orçamento de despesas da Azure.</span><span class="sxs-lookup"><span data-stu-id="9c972-106">They can also programmatically view their customers' spending against an Azure spending budget.</span></span>

<span data-ttu-id="9c972-107">Para obter mais informações, consulte [cenários em que os parceiros da CSP podem utilizar as APIs do Partner Center para gerir contas e encomendas de clientes e parceiros.](scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="9c972-107">For more information, see [scenarios in which CSP partners can use the Partner Center APIs to manage customer and partner accounts and orders](scenarios.md).</span></span>

## <a name="partner-usage-management"></a><span data-ttu-id="9c972-108">Gestão de utilização de parceiros</span><span class="sxs-lookup"><span data-stu-id="9c972-108">Partner usage management</span></span>

- <span data-ttu-id="9c972-109">[Obtenha um resumo de utilização do parceiro](get-a-partner-usage-summary.md) utilizando o recurso **PartnerUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="9c972-109">[Get a partner usage summary](get-a-partner-usage-summary.md) using the **PartnerUsageSummary** resource</span></span>
- <span data-ttu-id="9c972-110">[Obtenha registos de utilização para todos os clientes](get-a-customer-s-usage-records.md) que utilizem o recurso **CustomerMonthlyUsageRecord**</span><span class="sxs-lookup"><span data-stu-id="9c972-110">[Get usage records for all customers](get-a-customer-s-usage-records.md) using the **CustomerMonthlyUsageRecord** resource</span></span>

## <a name="customer-usage-management"></a><span data-ttu-id="9c972-111">Gestão do uso do cliente</span><span class="sxs-lookup"><span data-stu-id="9c972-111">Customer usage management</span></span>

- <span data-ttu-id="9c972-112">[Obtenha o resumo de utilização de um cliente](get-a-customer-usage-summary.md) utilizando o recurso **CustomerUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="9c972-112">[Get a customer's usage summary](get-a-customer-usage-summary.md) using the **CustomerUsageSummary** resource</span></span>
- <span data-ttu-id="9c972-113">[Obtenha todos os registos de utilização de subscrição para um cliente](get-a-customer-subscription-s-usage-records.md) utilizando o recurso **SubscriptionMonthlyUsageRecord**</span><span class="sxs-lookup"><span data-stu-id="9c972-113">[Get all subscription usage records for a customer](get-a-customer-subscription-s-usage-records.md) using the **SubscriptionMonthlyUsageRecord** resource</span></span>

## <a name="subscription-usage-management"></a><span data-ttu-id="9c972-114">Gestão de utilização de assinaturas</span><span class="sxs-lookup"><span data-stu-id="9c972-114">Subscription usage management</span></span>

- <span data-ttu-id="9c972-115">[Obtenha um resumo de utilização por subscrição](get-a-customer-subscription-usage-summary.md) utilizando o recurso **SubscriptionUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="9c972-115">[Get a subscription usage summary](get-a-customer-subscription-usage-summary.md) using the **SubscriptionUsageSummary** resource</span></span>
- <span data-ttu-id="9c972-116">[Obtenha todos os registos mensais de utilização de uma subscrição](get-all-monthly-usage-records-for-a-subscription.md) utilizando o recurso **AzureResourceMonthlyUsageRecord**</span><span class="sxs-lookup"><span data-stu-id="9c972-116">[Get all monthly usage records for a subscription](get-all-monthly-usage-records-for-a-subscription.md) using the **AzureResourceMonthlyUsageRecord** resource</span></span>
- <span data-ttu-id="9c972-117">[Obtenha dados de utilização para uma subscrição por recurso](get-a-customer-subscription-resource-usage-records.md) utilizando o recurso **ResourceUsageRecord**</span><span class="sxs-lookup"><span data-stu-id="9c972-117">[Get usage data for a subscription by resource](get-a-customer-subscription-resource-usage-records.md) using the **ResourceUsageRecord** resource</span></span>
- <span data-ttu-id="9c972-118">[Obtenha dados de utilização para uma subscrição por medidor](get-a-customer-subscription-meter-usage-records.md) utilizando o recurso **MeterUsageRecord**</span><span class="sxs-lookup"><span data-stu-id="9c972-118">[Get usage data for a subscription by meter](get-a-customer-subscription-meter-usage-records.md) using the **MeterUsageRecord** resource</span></span>

## <a name="azure-spending-budget-management"></a><span data-ttu-id="9c972-119">Gestão orçamental de gastos Azure</span><span class="sxs-lookup"><span data-stu-id="9c972-119">Azure spending budget management</span></span>

- <span data-ttu-id="9c972-120">[Obtenha o orçamento de utilização de um cliente](get-a-customer-s-usage-spending-budget.md) utilizando o recurso **CustomerUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="9c972-120">[Get a customer's usage budget](get-a-customer-s-usage-spending-budget.md) using the **CustomerUsageSummary** resource</span></span>
- <span data-ttu-id="9c972-121">[Atualizar o orçamento de utilização de um cliente](update-a-customer-s-usage-spending-budget.md) utilizando o recurso **CustomerUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="9c972-121">[Update a customer's usage budget](update-a-customer-s-usage-spending-budget.md) using the **CustomerUsageSummary** resource</span></span>
