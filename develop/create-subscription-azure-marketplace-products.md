---
title: Criar uma subscrição para produtos de mercado comercial
description: Os desenvolvedores podem criar e gerir uma subscrição de produtos de marketplace comercial usando APIs do Partner Center.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df2a3707e00ba36a11c404b102304c08d105244e
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768810"
---
# <a name="create-a-subscription-for-commercial-marketplace-products"></a>Criar uma subscrição para produtos de mercado comercial

**Aplica-se a:**

* Partner Center

Pode criar uma subscrição para produtos de marketplace comercial utilizando APIs do Partner Center. Você deve [obter uma lista de ofertas para um mercado,](#get-a-list-of-offers-for-a-market)criar e enviar uma [encomenda](#create-and-submit-an-order) para uma subscrição de mercado comercial, em seguida, recuperar um link [de ativação](#get-activation-link).

Também pode [realizar gestão de ciclo de vida](#lifecycle-management) e gerir [faturas](#invoice-and-reconciliation) para estas subscrições.

## <a name="prerequisites"></a>Pré-requisitos

* [Credenciais de autenticação do Partner Center.](partner-center-authentication.md) Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.
* O identificador de clientes. Se não tiver o identificador de um cliente, siga os passos na [Obter uma lista de clientes.](get-a-list-of-customers.md) Em alternativa, inscreva-se no Partner Center, escolha o cliente na lista de clientes, selecione **Conta** e guarde o seu **ID Microsoft**.

## <a name="get-a-list-of-offers-for-a-market"></a>Obter uma lista de ofertas para um mercado

Pode consultar as ofertas disponíveis para um mercado utilizando os seguintes modelos API do Partner Center:

* **[Produto](product-resources.md#product)**: Uma construção de agrupamento para bens ou serviços puriáveis. Um produto em si não é um item purivel.
* **[SKU](product-resources.md#sku)**: Uma unidade de armazenamento de stock (SKU) em baixo de um produto. Estes representam as diferentes formas do produto.
* **[Disponibilidade](product-resources.md#availability)**: Uma configuração na qual um SKU está disponível para compra (como país, moeda ou segmento da indústria).

Antes de adquirir uma reserva Azure, complete os seguintes passos:

1. Identifique e recupere o produto e o SKU que pretende comprar. Se já conhece o ID do Produto e o ID SKU, selecione-os.

    * [Obtenha uma lista de produtos](get-a-list-of-products.md)
    * [Obtenha um produto usando o ID do produto](get-a-product-by-id.md)
    * [Obtenha uma lista de SKUs para um produto](get-a-list-of-skus-for-a-product.md)
    * [Obtenha um SKU usando o SKU ID](get-a-sku-by-id.md)

    > [!NOTE]
    > Pode identificar produtos de mercado comercial através da sua propriedade **ProductType** de **"Azure"** e da sua propriedade **subType** de **"SaaS".**

2. Se os SKUs estiverem marcados com um pré-requisito **do InventárioCheck,** [verifique o inventário de um SKU](check-inventory.md).

    > [!NOTE]
    > Neste momento, não existem produtos de mercado comercial que suportem a verificação de inventário ou estejam marcados com um pré-requisito **do InventárioCheck.**

3. Recupere a disponibilidade para o SKU. Necessitará do **CatalogItemId** da disponibilidade ao esemcrutinar a encomenda, que poderá obter através das seguintes APIs:

    * [Obtenha uma lista de disponibilidades para um SKU](get-a-list-of-availabilities-for-a-sku.md)
    * [Obtenha uma disponibilidade usando o ID de disponibilidade](get-an-availability-by-id.md)

## <a name="create-and-submit-an-order"></a>Criar e submeter uma encomenda

Para submeter a sua ordem de reserva Azure, siga estes passos:

1. [Crie um carrinho](create-a-cart.md) para guardar a coleção de itens de catálogo que pretende comprar. Ao criar um [carrinho,](cart-resources.md#cart)os [itens](cart-resources.md#cartlineitem) da linha do carrinho são automaticamente agrupados com base no que pode ser comprado em conjunto na mesma [ordem](order-resources.md#order). (Também pode [atualizar um carrinho.)](update-a-cart.md)
2. [Confira o carrinho,](checkout-a-cart.md)que resulta na criação de uma [encomenda.](order-resources.md#order)

### <a name="get-order-details"></a>Obter detalhes da encomenda

Pode [recuperar os detalhes de uma encomenda individual utilizando o ID da encomenda](get-an-order-by-id.md). Também pode [obter uma lista de todas as encomendas para um cliente específico.](get-all-of-a-customer-s-orders.md)

> [!NOTE]
> Após a entrega de uma encomenda, há um atraso de até 15 minutos antes da encomenda aparecer na lista de pedidos do cliente.

## <a name="get-activation-link"></a>Obtenha ligação de ativação

O parceiro ou cliente deve ativar subscrições de produtos Azure Marketplace. Pode [obter um link de ativação por linha de encomenda](get-activation-link-by-order-line-item.md). Também pode [obter uma subscrição por ID,](get-a-subscription-by-id.md)enumerando depois a propriedade **Links** para criar uma ligação de ativação.

## <a name="lifecycle-management"></a>Gestão do ciclo de vida

Pode gerir o ciclo de vida das suas subscrições a produtos de mercado comercial utilizando os seguintes métodos:

* [Cancelar uma subscrição de marketplace comercial](cancel-an-azure-marketplace-subscription.md)
* [Permitir ou desativar novamente a autoria para uma subscrição de mercado comercial](update-autorenew-for-an-azure-marketplace-subscription.md)

## <a name="quantity-management"></a>Gestão de quantidades

A quantidade de uma subscrição de mercado comercial deve estar dentro dos limites definidos pelo seu [SKU](product-resources.md#sku) associado (ver os **atributos mínimos deQuantidade** equantidade).  Para atualizar a quantidade de uma subscrição de mercado comercial, utilize o seguinte método:

* [Alterar a quantidade de uma subscrição](change-the-quantity-of-a-subscription.md)

## <a name="invoice-and-reconciliation"></a>Fatura e reconciliação

Pode gerir [faturas de clientes](invoice-resources.md) (incluindo taxas para subscrições de produtos de mercado comercial) utilizando os seguintes métodos:

* [Obtenha faturas de produtos da linha de consumo de mercado comercial](get-invoice-billed-consumption-lineitems.md)
* [Obter ligações de estimativa da fatura](get-invoice-estimate-links.md)
* [Obter faturas sem faturas de produtos de linha de consumo de mercado comercial](get-invoice-unbilled-consumption-lineitems.md)
* [Obtenha itens de linha de reconciliação sem faturação](get-invoice-unbilled-recon-lineitems.md)

## <a name="test-using-integration-sandbox-account"></a>Teste utilizando a conta de caixa de areia de integração

Na produção, depois de ter criado uma subscrição de produtos SaaS de marketplace comercial, precisa de recuperar uma ligação de ativação personalizada do Partner Center e visitar o site da editora para concluir o processo de configuração. A faturação da subscrição só começará depois de a configuração estar concluída.

No ambiente da caixa de areia da CSP, não existe integração com os ISVs. Se tentar recuperar uma ligação de ativação do Partner Center, será devolvido um link falso. Não é possível utilizar este link falso para completar o processo de configuração no site da editora. Para utilizar a conta de sandbox de integração para testar a faturação para subscrições de produtos SaaS de marketplace comercial, utilize o seguinte método para ativar a subscrição. A faturação da subscrição começará após a ativação bem sucedida:

* [Ativar uma subscrição de sandbox para produtos de mercado comercial](activate-sandbox-subscription-azure-marketplace-products.md)

