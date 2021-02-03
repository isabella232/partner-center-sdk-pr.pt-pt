---
title: Criar um plano Azure
description: Os desenvolvedores podem comprar, criar e gerir planos Azure programáticamente usando APIs do Partner Center.
ms.date: 01/02/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: mowrim
ms.author: mowrim
ms.openlocfilehash: 372b94ac7217899ca560cf943bf11a7e8906872d
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769314"
---
# <a name="create-an-azure-plan"></a>Criar um plano Azure

**Aplica-se a:**

* Partner Center

Você pode comprar, criar e gerir um plano Azure usando as APIs do Partner Center. O processo é semelhante à criação de uma subscrição do Microsoft Azure (MS-AZR-0145P). Tem de [obter o item do catálogo para o plano Azure,](#get-the-catalog-item-for-azure-plan)em seguida, criar e enviar uma [encomenda](#create-and-submit-an-order).

## <a name="prerequisites"></a>Pré-requisitos

* [Credenciais de autenticação do Partner Center.](partner-center-authentication.md) Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.
* O identificador de clientes. Se não tiver o identificador de um cliente, siga os passos na [Obter uma lista de clientes.](get-a-list-of-customers.md) Em alternativa, inscreva-se no Partner Center, escolha o cliente na lista de clientes, selecione **Conta** e guarde o seu **ID Microsoft**.
* [Confirmação da aceitação pelo cliente do Acordo de Cliente da Microsoft](/partner-center/confirm-customer-agreement).

## <a name="get-the-catalog-item-for-azure-plan"></a>Obtenha o item do catálogo para o plano Azure

Antes de poder criar um plano Azure para um cliente, tem de recuperar o item de catálogo correspondente. Pode recuperar o item do catálogo utilizando as APIs do catálogo do Partner Center existentes com os seguintes modelos de recursos.

* **[Produto](product-resources.md#product)**: Uma construção de agrupamento para bens ou serviços puriáveis. Um produto em si não é um item purivel.
* **[SKU](product-resources.md#sku)**: Uma unidade de armazenamento de stock (SKU) em baixo de um produto. Os SKUs representam as diferentes formas do produto.
* **[Disponibilidade](product-resources.md#availability)**: Uma configuração na qual um SKU está disponível para compra (como país, moeda ou segmento da indústria).

Para obter o item do catálogo para um plano Azure, complete os seguintes passos:

1. Identifique e recupere o identificador *de produto* para o plano Azure. Siga os passos em [Obter uma lista de produtos](get-a-list-of-products.md) e especifique o **targetView** como **MicrosoftAzure**. (Se já conhece o identificador do *produto* para o plano Azure, pode seguir os passos em [Obter um produto utilizando o ID do produto.)](get-a-product-by-id.md)

2. Recupere o **SKU** do produto para o plano Azure. Siga os passos em [Obter uma lista de SKUs para um produto](get-a-list-of-skus-for-a-product.md). Se já conhece o identificador SKU para o plano Azure, pode seguir os passos em [Get a SKU usando o SKU ID.](get-a-sku-by-id.md)

3. Recupere a **disponibilidade** do SKU para o plano Azure. Siga os passos em [Obter uma lista de disponibilidades para um SKU](get-a-list-of-availabilities-for-a-sku.md). Se já conhece o identificador para a disponibilidade de que necessita, pode seguir os passos em [Obter uma disponibilidade usando o ID de disponibilidade.](get-an-availability-by-id.md) *Certifique-se de que nota o valor da propriedade **CatalogItemId** da disponibilidade para o plano Azure. Vai precisar deste valor para criar uma encomenda.*

## <a name="create-and-submit-an-order"></a>Criar e submeter uma encomenda

Para submeter a sua encomenda para um plano Azure, siga estes passos:

1. [Crie um carrinho](create-a-cart.md) para guardar a coleção de itens de catálogo que pretende comprar. Ao criar um [carrinho,](cart-resources.md#cart)os [itens](cart-resources.md#cartlineitem) da linha do carrinho são automaticamente agrupados com base no que pode ser comprado em conjunto na mesma [ordem](order-resources.md#order). (Também pode [atualizar um carrinho.)](update-a-cart.md)

2. [Confira o carrinho,](checkout-a-cart.md)que resulta na criação de uma [encomenda.](order-resources.md#order)

## <a name="get-order-details"></a>Obter detalhes da encomenda

Pode [recuperar os detalhes de uma encomenda individual utilizando o ID da encomenda](get-an-order-by-id.md). Também pode [obter uma lista de todas as encomendas para um cliente específico.](get-all-of-a-customer-s-orders.md)

>[!NOTE]
>Após a entrega de uma encomenda, há um atraso de até 15 minutos antes da encomenda aparecer na lista de pedidos do cliente.

## <a name="manage-azure-plans"></a>Gerir planos Azure

Após o processo ser processado com sucesso, será criado um recurso **de Subscrição** do Partner Center para o plano Azure. Pode utilizar os seguintes métodos para gerir os recursos **de subscrição** do Partner Center para gerir o plano Azure:

* [Obter as subscrições de um cliente](get-all-of-a-customer-s-subscriptions.md)
* [Obter uma lista de subscrições por encomenda](get-a-list-of-subscriptions-by-order.md)

Quando um plano Azure é criado no Partner Center, uma subscrição de utilização Azure correspondente também é criada em Azure. Também pode criar subscrições adicionais de utilização do Azure ao abrigo do mesmo plano Azure utilizando Azure Portal e Azure APIs. Pode obter os identificadores de todas as subscrições de utilização do Azure associadas a um plano Azure seguindo os passos em [Obter uma lista de direitos Azure para subscrição do Partner Center](get-a-list-of-azure-entitlements-for-subscription.md)

## <a name="lifecycle-management"></a>Gestão do ciclo de vida

Pode suspender um plano Azure existente seguindo os passos em [Suspender uma subscrição](suspend-a-subscription.md).

*Só pode suspender um plano Azure existente se deixar de ter quaisquer ativos de utilização associados a ele, incluindo subscrições de uso Azure e reservas Azure.*

Para obter detalhes sobre como desativar as subscrições de utilização do [Azure, consulte a AZure API na gestão do ciclo de vida por subscrição](/rest/api/resources/subscriptions).

Para remover as reservas existentes do Azure, você deve [cancelar as reservas.](/partner-center/azure-reservations-manage#cancel-or-exchange-a-reservation)
Depois de suspender um plano Azure, pode reativá-lo.

Para obter detalhes sobre como reativar um plano Azure, consulte [Reativar uma subscrição suspensa](reactivate-a-suspended-a-subscription.md)

## <a name="transition-existing-csp-offers-to-azure-plan"></a>Fazer a transição de ofertas de CSP existentes para o plano do Azure 

Não pode criar um plano do Azure para um cliente existente com uma subscrição do Microsoft Azure (MS-AZR-0145P). No entanto, pode [fazer a transição de um cliente do CSP existente que o Azure oferece para os serviços do Azure no plano do Azure](/partner-center/azure-plan-transition) na nova experiência de comércio do programa CSP no Centro de Parceiros. Para fazer a transição de um cliente existente, utilize as APIs de atualização do produto para seguir estes passos:

* [Verifique se o cliente é elegível para uma transição para o plano do Azure](get-eligibility-for-product-upgrade.md)
* [Inicie a atualização do produto para o cliente](create-product-upgrade-entity.md)
* [Verifique o estado da atualização do produto](get-product-upgrade-status.md)

## <a name="azure-spending"></a>Despesas do Azure

Pode acompanhar [os gastos do Azure](azure-spending.md) consultando os resumos de utilização e registos de utilização detalhados utilizando os seguintes métodos:

* [Obter resumo de utilização do parceiro](get-a-partner-usage-summary.md)
* [Obter todos os registos de utilização do cliente para um parceiro](get-a-customer-s-usage-records.md)
* [Obter resumo de utilização do cliente](get-a-customer-usage-summary.md)
* [Obter todos os registos de utilização da subscrição de um cliente](get-a-customer-subscription-s-usage-records.md)
* [Obter resumo de utilização da subscrição](get-a-customer-subscription-usage-summary.md)
* [Obter dados de utilização da subscrição por recurso](get-a-customer-subscription-resource-usage-records.md)
* [Obter dados de utilização da subscrição por medidor](get-a-customer-subscription-meter-usage-records.md)
* [Obter recursos de registo de utilização do medidor](meter-usage-resources.md)
* [Obter recursos de registo de utilização do recurso](resource-usage-resources.md)

Também pode definir e gerir o orçamento de utilização do cliente utilizando os seguintes métodos:

* [Obter orçamento de utilização do cliente](get-a-customer-s-usage-spending-budget.md)
* [Atualizar orçamento de utilização do cliente](update-a-customer-s-usage-spending-budget.md)

## <a name="invoice-and-reconciliation"></a>Fatura e reconciliação

Pode gerir faturas e dados de reconciliação utilizando os seguintes métodos:

* [Obter uma coleção de faturas](get-a-collection-of-invoices.md)
* [Obter ligações de estimativa da fatura](get-invoice-estimate-links.md)
* [Obtenha fatura por ID](get-invoice-by-id.md)
* [Obter declaração da fatura](get-invoice-statement.md)
* [Obter resumos de faturas](get-invoice-summaries.md)
* [Obter itens de linha do consumo cobrado na fatura](get-invoice-billed-consumption-lineitems.md)
* [Obter itens de linha do consumo não cobrado na fatura](get-invoice-unbilled-consumption-lineitems.md)
* [Obtenha itens de linha de reconhecimento faturados](get-invoiceline-items.md)
* [Obter itens de linha de reconciliação não cobrados na fatura](get-invoice-unbilled-recon-lineitems.md)
