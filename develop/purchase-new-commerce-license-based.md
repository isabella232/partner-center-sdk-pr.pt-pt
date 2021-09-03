---
title: Comprar novos serviços baseados em licenças de comércio
description: Os desenvolvedores podem comprar, criar e gerir novos serviços baseados em licenças de comércio usando as APIs do Partner Center.
ms.date: 02/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: dd3aebdb0a670449d3a39f67fc2ad6c7ef8df8e5
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123457334"
---
# <a name="purchasing-new-commerce-license-based-services"></a>Aquisição de novos serviços baseados em licenças de comércio

**Aplica-se a:**

* Partner Center

> [!Note] 
> As novas alterações de Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.

Você pode comprar, criar e gerir novos serviços baseados em licenças de comércio usando as APIs do Partner Center. O processo é semelhante ao plano Azure e às ofertas do Marketplace.

## <a name="prerequisites"></a>Pré-requisitos

* [Credenciais de autenticação do Partner Center.](partner-center-authentication.md) A nova experiência de comércio suporta a autenticação com credenciais autónomas de App e App+User.
* O identificador de clientes. Se não tiver o identificador de um cliente, siga os passos na [Obter uma lista de clientes.](get-a-list-of-customers.md) Em alternativa, inscreva-se no Partner Center, escolha o cliente na lista de clientes, selecione **Conta** e guarde o seu **ID Microsoft**.
* [Confirmação da aceitação pelo cliente do Acordo de Cliente da Microsoft](/partner-center/confirm-customer-agreement).

## <a name="get-the-catalog-item-for-new-commerce-license-based-services"></a>Obtenha o item do catálogo para novos serviços baseados em licenças de comércio

Você precisa recuperar novos itens de catálogo de serviços baseados em licenças de comércio. Recupere os itens de catálogo utilizando as APIs do catálogo do Partner Center existentes com os seguintes modelos de recursos:

* **[Produto](product-resources.md#product)**: Uma construção de agrupamento para bens ou serviços puriáveis. Um produto em si não é um item purivel.
* **[SKU](product-resources.md#sku)**: Uma unidade de armazenamento de stock (SKU) em baixo de um produto. Os SKUs representam as diferentes formas do produto.
* **[Disponibilidade](product-resources.md#availability)**: Uma configuração na qual um SKU está disponível para compra (como país, moeda ou segmento da indústria).

Para obter os itens de catálogo para novos serviços baseados em licenças de comércio:

1. Siga os passos em [Obter uma lista de produtos](get-a-list-of-products.md) para produtos e especificar o **targetView** como **OnlineServices**. (Se já conhece o identificador de produto para a oferta que pretende comprar, pode seguir os passos em [Obter um produto usando o ID do produto.)](get-a-product-by-id.md)

2. Recupere o **SKU** do produto para a oferta que procura. Siga os passos em [Obter uma lista de SKUs para um produto](get-a-list-of-skus-for-a-product.md). (Se já conhece o identificador SKU para a oferta que deseja, pode seguir os passos em [Get a SKU usando o SKU ID](get-a-sku-by-id.md) em vez disso.)

3. Recupere a **disponibilidade** do SKU para a oferta. Ofertas diferentes suportam termos específicos. Alguns SKUs têm mais de uma disponibilidade. Siga os passos em [Obter uma lista de disponibilidades para um SKU](get-a-list-of-availabilities-for-a-sku.md). (Se já conhece o identificador para a disponibilidade de que necessita, pode seguir os passos em [Obter uma disponibilidade utilizando o ID de disponibilidade.)](get-an-availability-by-id.md) *Certifique-se de que nota o valor da propriedade **CatalogItemId** da disponibilidade para a oferta. Necessitará deste valor para criar uma encomenda.*

## <a name="create-and-submit-an-order"></a>Criar e submeter uma encomenda

Para submeter a sua encomenda para um plano Azure (incluindo novas ordens de comércio), siga estes passos:

1. [Crie um carrinho](create-a-cart.md) para guardar a coleção de itens de catálogo que pretende comprar. Ao criar um [carrinho,](cart-resources.md#cart)os [itens](cart-resources.md#cartlineitem) da linha do carrinho são automaticamente agrupados com base no que pode ser comprado em conjunto na mesma [ordem](order-resources.md#order). (Também pode [atualizar um carrinho.)](update-a-cart.md)

2. [Confira o carrinho,](checkout-a-cart.md)que resulta na criação de uma [encomenda.](order-resources.md#order)

## <a name="get-order-details"></a>Obter detalhes da encomenda

Pode [recuperar os detalhes de uma encomenda individual utilizando o ID da encomenda](get-an-order-by-id.md). Também pode [obter uma lista de todas as encomendas para um cliente específico.](get-all-of-a-customer-s-orders.md)

>[!NOTE]
>Depois de submeter uma encomenda, há um atraso de até 15 minutos antes da encomenda aparecer na lista de pedidos do cliente. Atualmente, os parceiros da UE só podem comprar novas ofertas de comércio para: 1. Novos clientes 2. Clientes existentes que não possuam um plano Azure pré-existente, mercado, subscrições de software ou software perpétuo numa moeda diferente da moeda do país do parceiro.

## <a name="manage-new-commerce-subscriptions"></a>Gerir novas subscrições de comércio

Após o processo ser processado com sucesso, será criado um recurso **de Subscrição** do Partner Center para o plano Azure. Pode utilizar os seguintes métodos para gerir os recursos **de subscrição** do Partner Center para gerir o plano Azure:

* [Obter as subscrições de um cliente](get-all-of-a-customer-s-subscriptions.md)
* [Obter uma lista de subscrições por encomenda](get-a-list-of-subscriptions-by-order.md)

Há diferenças e novas capacidades específicas para o novo comércio.

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
