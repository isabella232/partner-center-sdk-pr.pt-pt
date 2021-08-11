---
title: Comprar itens do catálogo
description: Como adquirir itens de catálogo utilizando a API do Partner Center.
ms.date: 07/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 34560ceff2721a805d50cd4bf0702f6e7cf6f473db3f38ee52ea439b7355b786
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997348"
---
# <a name="purchase-catalog-items"></a>Comprar itens do catálogo

O seguinte cenário demonstra o processo genérico de compra de artigos do catálogo através da API do Partner Center.

## <a name="discovery"></a>Deteção

Selecione produtos e Unidades de Armazenamento (SKUs) e verifique a sua disponibilidade utilizando os seguintes modelos API do Partner Center:

- [Produto](product-resources.md#product) - Uma construção de agrupamento para bens ou serviços puriáveis. Um produto por si só não é um item purivel.
- [SKU](product-resources.md#sku) - Um SKU purável sob um produto. Estes representam as diferentes formas do produto.
- [Disponibilidade](product-resources.md#availability) - Uma configuração na qual um SKU está disponível para compra (como país, moeda e segmento da indústria).

Para adquirir um artigo no catálogo, complete os seguintes passos:

1. Identifique e recupere o Produto e SKU que pretende comprar.

   - [Obtenha uma lista de produtos](get-a-list-of-products.md)
   - [Obtenha um produto usando o ID do produto](get-a-product-by-id.md)
   - [Obtenha uma lista de SKUs para um produto](get-a-list-of-skus-for-a-product.md)
   - [Obtenha um SKU usando o SKU ID](get-a-sku-by-id.md)

2. Verifique o inventário de um SKU. Este passo é apenas necessário para SKUs que são marcados com um valor **InventárioCheck** na [propriedade de compraPrerequisites.](product-resources.md#sku)

   - [Verificar Inventário](check-inventory.md)

3. Recupere a [disponibilidade](product-resources.md#availability) para o [SKU.](product-resources.md#sku) Necessitará do **CatalogItemId** da disponibilidade ao fazer a encomenda. Para obter este valor, utilize uma das seguintes APIs:

   - [Obtenha uma lista de disponibilidades para um SKU](get-a-list-of-availabilities-for-a-sku.md)
   - [Obtenha uma disponibilidade usando o ID de disponibilidade](get-an-availability-by-id.md)

## <a name="order-submission"></a>Submissão de encomendas

Para submeter a sua encomenda de artigo de catálogo, faça o seguinte:

1. Crie um [Carrinho](cart-resources.md) para guardar a coleção de itens de catálogo que pretende comprar. Quando cria um carrinho, os [itens](cart-resources.md#cartlineitem) da linha do carrinho são automaticamente agrupados com base no que pode ser comprado juntos na mesma [Ordem](order-resources.md).

   - [Criar um carrinho de compras](create-a-cart.md)
   - [Atualize um carrinho de compras](update-a-cart.md)

2. Olha para o carrinho. A verificação de um carrinho resulta na criação de uma [Ordem.](order-resources.md)

   - [Check-out do carrinho](checkout-a-cart.md)

## <a name="get-order-details"></a>Obter detalhes da encomenda

Pode recuperar os detalhes de uma encomenda individual utilizando o ID da encomenda ou obter uma lista de encomendas para um cliente. Há um atraso de até 15 minutos entre o momento em que uma encomenda é submetida e quando aparecerá numa lista de encomendas de um cliente.

- Consulte [obter uma encomenda por ID](get-an-order-by-id.md) para obter os detalhes de uma encomenda individual usando os IDs de encomenda.

- Consulte [todas as ordens de um cliente](get-all-of-a-customer-s-orders.md) para obter uma lista de encomendas para um cliente que utilize a identificação do cliente.

- Consulte obter uma lista de encomendas por cliente e tipo de ciclo de [faturação](get-a-list-of-orders-by-customer-and-billing-cycle-type.md) para obter uma lista de encomendas para um cliente por tipo de ciclo de [faturação,](product-resources.md#billingcycletype) permitindo-lhe listar as encomendas de artigos de catálogo (taxas pontuais) e encomendas anuais ou mensais faturadas separadamente.

## <a name="lifecycle-management"></a>Gestão do ciclo de vida

Como parte da gestão do ciclo de vida dos seus itens de catálogo no Partner Center, pode obter informações sobre o seu item de catálogo [Direitos](entitlement-resources.md), e obter detalhes da reserva usando o ID da encomenda de reservas. Por exemplo, como fazê-lo, consulte [obter direitos](get-a-collection-of-entitlements.md).   

## <a name="invoice-and-reconciliation"></a>Fatura e reconciliação

Os seguintes cenários mostram-lhe como visualizar programaticamente as [faturas](invoice-resources.md)do seu cliente, e obter os saldos e resumos da sua conta que incluem taxas únicas para itens de catálogo.

### <a name="balance-and-payment"></a>Saldo e pagamento

Para obter o saldo da conta corrente no seu tipo de moeda padrão que é um saldo de encargos recorrentes e pontuais (item de catálogo), consulte [obter o saldo da sua conta corrente](get-the-reseller-s-current-account-balance.md).

### <a name="multi-currency-balance-and-payment"></a>Balança e pagamento multi-moedas

Para obter o saldo da sua conta corrente e uma recolha de resumos de faturas contendo um resumo da fatura com encargos recorrentes e pontuais para cada um dos tipos de moeda do seu cliente, consulte [resumos](get-invoice-summaries.md)da fatura .

### <a name="invoices"></a>Faturas

Para obter uma coleção de faturas que mostrem taxas recorrentes e pontuais, consulte [obter uma coleção de faturas.](get-a-collection-of-invoices.md) 

### <a name="single-invoice"></a>Fatura Única

Para obter uma fatura específica utilizando o ID da fatura, consulte [obter uma fatura por ID](get-invoice-by-id.md).  

### <a name="reconciliation"></a>Reconciliação

Para obter uma recolha de detalhes de item da linha de fatura (itens de linha de reconciliação) para um ID de fatura específico, consulte [obter itens de linha de fatura](get-invoiceline-items.md).  

### <a name="download-an-invoice-as-a-pdf"></a>Faça o download de uma fatura como UM PDF

Para obter uma declaração de fatura em formulário PDF utilizando um ID de fatura, consulte [uma declaração de fatura](get-invoice-statement.md).
