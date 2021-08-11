---
title: Fazer uma compra única
description: Como fazer uma compra única de software e produtos de reserva, tais como subscrições de software, software perpétuo e Azure Reserved Virtual Machine (VM) Instances, usando a API do Partner Center.
ms.date: 10/09/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: baf0b5d4aaa8957874ab019359aca2662a76194387e0cd06999b0bb329076c80
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994443"
---
# <a name="make-a-one-time-purchase"></a>Fazer uma compra única

**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud for US Government

Como fazer uma compra única de software e produtos de reserva, tais como subscrições de software, software perpétuo e Azure Reserved Virtual Machine (VM) Instances, usando a API do Partner Center.

> [!NOTE]
> As subscrições de software não estão disponíveis nos seguintes mercados:
>
> | Mercados indisponíveis            | Mercados indisponíveis (continuado...) | Mercados indisponíveis (continuado...)      |
> |--------------------------------|-----------------------------------|------------------------------------------|
> | Ilhas Åland                  | Gronelândia                         | Papua-Nova Guiné                         |
> | Samoa Americana                 | Granada                           | Ilhas Pitcairn                         |
> | Andorra                        | Guadalupe                        | Reunião                                  |
> | Anguila                       | Guame                              | Federação Russa                       |
> | Antártica                     | Guernesey                          | Saba                                     |
> | Antígua e Barbuda            | Guiné                            | São Bartolomeu                         |
> | Aruba                          | Guiné-Bissau                     | Santa Lúcia                              |
> | Benim                          | Guiana                            | São Martinho (Saint Martin)                             |
> | Butão                         | Haiti                             | São Pedro e Miquelão                |
> | Bonaire                        | Ilhas Heard e McDonald | São Vicente e Granadinas         |
> | Ilha Bouvet                  | Ilha de Man                       | Samoa                                    |
> | Brasil                         | Jan Mayen                         | São Marino                               |
> | Território Britânico do Oceano Índico | Jersey                            | São Tomé e Príncipe                    |
> | Ilhas Virgens Britânicas         | Quiribáti                          | Seicheles                               |
> | Burkina Faso                   | Kosovo                            | Serra Leoa                             |
> | Burundi                        | Laos                              | Santo Eustáquio                           |
> | Camboja                       | Lesoto                           | São Martinho (Sint Maarten)                             |
> | República Centro-Africana       | Libéria                           | Ilhas Salomão                          |
> | Chade                           | Madagáscar                        | Somália                                  |
> | China                          | Maláui                            | Ilhas Geórgia do Sul e Sandwich do Sul |
> | Ilha do Natal               | Maldivas                          | Sudão do Sul                              |
> | Ilhas dos Cocos (Keeling)        | Mali                              | Santa Helena, Ascensão, Tristão da Cunha   |
> | Comoros                        | Ilhas Marshall                  | Suriname                                 |
> | Congo                          | Martinica                        | Svalbard                                 |
> | República Democrática do Congo                    | Mauritânia                        | Suazilândia                                |
> | Ilhas Cook                   | Maiote                           | Timor-Leste                              |
> | Jibuti                       | Micronésia                        | Togo                                     |
> | Dominica                       | Montserrate                        | Toquelau                                  |
> | Guiné Equatorial              | Moçambique                        | Tonga                                    |
> | Eritreia                        | Mianmar                           | Ilhas Turcas e Caicos                 |
> | Ilhas Falkland (Malvinas)               | Nauru                             | Tuvalu                                   |
> | Guiana Francesa                  | Nova Caledónia                     | Ilhas Desondo dos EUA                    |
> | Polinésia Francesa               | Níger                             | Vanuatu                                  |
> | Territórios Austrais Franceses    | Niuê                              | Cidade do Vaticano                             |
> | Gabão                          | Ilha Norfolk                    | Wallis e Futuna                        |
> | Gâmbia                         | Ilhas Marianas do Norte          | Iémen                                    |
> | Gibraltar                      | Palau                             | &nbsp;                                   |
>
&nbsp;
> [!NOTE]
> Para adquirir software perpétuo, deve ter sido previamente qualificado. Contacte o suporte para mais informações.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="making-a-one-time-purchase"></a>Fazer uma compra única

Para efetuar uma compra única, utilize os seguintes passos:

1. [Enablement](#enablement) - (Apenas Azure Reserved VM Instance) Registe uma subscrição ativa da CSP Azure para permitir a aquisição de qualquer produto de reserva.

2. [Discovery](#discovery) - Encontre e selecione os produtos e SKUs que pretende comprar e verificar a sua disponibilidade.

3. [Submissão de encomenda](#order-submission) - Crie um carrinho de compras com os itens na sua encomenda e envie-o.

4. [Obtenha detalhes](#get-order-details) da encomenda - Reveja os detalhes de uma encomenda, todas as encomendas para um cliente, ou veja as encomendas por tipo de ciclo de faturação.

Depois de ter feito a sua compra única, os seguintes cenários mostram-lhe como gerir o ciclo de vida dos seus produtos, obtendo informações sobre os seus direitos e como recuperar declarações de saldo, faturas e resumos de faturas.

- [Gestão do ciclo de vida](#lifecycle-management)

- [Fatura e reconciliação](#invoice-and-reconciliation)

## <a name="enablement"></a>Enablement

Uma vez identificada a subscrição ativa a que pretende adicionar a Azure Reserved VM Instance, deve registar a subscrição de modo a que esteja ativada. Para registar um recurso [de Subscrição](subscription-resources.md) existente para que esteja ativado, consulte [Registar uma subscrição](register-a-subscription.md).

Após o registo da sua subscrição, deverá confirmar que o processo de registo está concluído verificando o estado de registo. Para fazer este passo, consulte [o estado de registo de assinatura](get-subscription-registration-status.md).

## <a name="discovery"></a>Deteção

Uma vez ativada a subscrição, está pronto para selecionar produtos e SKUs e verificar a sua disponibilidade utilizando os seguintes modelos API do Partner Center:

- [Produto](product-resources.md#product) - Uma construção de agrupamento para bens ou serviços puriáveis. Um produto por si só não é um item purivel.

- [SKU](product-resources.md#sku) - Uma unidade de armazenamento de stock (SKU) em baixo de um produto. Os SKUs representam as diferentes formas do produto.

- [Disponibilidade](product-resources.md#availability) - Uma configuração na qual um SKU está disponível para compra (como país, moeda e segmento da indústria).

Antes de efetuar uma compra única, complete os seguintes passos:

1. Identifique e recupere o Produto e SKU que pretende comprar. Você pode fazer este passo listando os produtos e SKUs primeiro, ou se você já conhece os IDs do produto e SKU, selecionando-os.

   - [Obtenha uma lista de produtos](get-a-list-of-products.md)
   - [Obtenha um produto usando o ID do produto](get-a-product-by-id.md)
   - [Obtenha uma lista de SKUs para um produto](get-a-list-of-skus-for-a-product.md)
   - [Obtenha um SKU usando o SKU ID](get-a-sku-by-id.md)

2. Verifique o inventário de um SKU. Este passo só é necessário para os SKUs que estão marcados com um pré-requisito **do InventárioCheck.**

   - [Verificar Inventário](check-inventory.md)

3. Recupere a [disponibilidade](product-resources.md#availability) para o [SKU.](product-resources.md#sku) Necessitará do **CatalogItemId** da disponibilidade ao fazer a encomenda. Para obter este valor, utilize uma das seguintes APIs:

   - [Obtenha uma lista de disponibilidades para um SKU](get-a-list-of-availabilities-for-a-sku.md)
   - [Obtenha uma disponibilidade usando o ID de disponibilidade](get-an-availability-by-id.md)

## <a name="order-submission"></a>Submissão de encomendas

Para submeter a sua encomenda, siga estes passos:

1. Crie um carrinho para guardar a coleção de itens de catálogo que pretende comprar. Quando cria um [Carrinho,](cart-resources.md)os [itens](cart-resources.md#cartlineitem) da linha do carrinho são automaticamente agrupados com base no que pode ser comprado juntos na mesma [Ordem](order-resources.md).

   - [Criar um carrinho de compras](create-a-cart.md)
   - [Atualize um carrinho de compras](update-a-cart.md)

2. Olha para o carrinho. A verificação de um carrinho resulta na criação de uma [Ordem.](order-resources.md)

   - [Check-out do carrinho](checkout-a-cart.md)

## <a name="get-order-details"></a>Obter detalhes da encomenda

Uma vez criado o seu pedido, pode recuperar os detalhes de uma encomenda individual usando o ID da encomenda, ou obter uma lista de encomendas para um cliente. Há um atraso de até 15 minutos entre o momento em que uma encomenda é submetida e quando aparecerá numa lista de encomendas de um cliente.

- Para obter os detalhes de uma encomenda individual usando o ID da encomenda. Veja, [obtenha uma ordem por identificação.](get-an-order-by-id.md)

- Para obter uma lista de encomendas para um cliente que usa a identificação do cliente. Veja, [obtenha todas as ordens de um cliente.](get-all-of-a-customer-s-orders.md)

- Para obter uma lista de encomendas para um cliente por tipo de ciclo de [faturação,](product-resources.md#billingcycletype) permite-lhe listar encomendas (taxas únicas) e encomendas anuais ou mensais cobradas separadamente. Veja, [obtenha uma lista de encomendas por cliente e tipo de ciclo de faturação](get-a-list-of-orders-by-customer-and-billing-cycle-type.md).

## <a name="lifecycle-management"></a>Gestão do ciclo de vida

Como parte da gestão do ciclo de vida das suas compras únicas no Partner Center, pode obter informações sobre os seus [Direitos](entitlement-resources.md)e obter detalhes da reserva usando o ID da encomenda de reservas. Por exemplo, como fazê-lo, consulte [obter direitos](get-a-collection-of-entitlements.md).

## <a name="invoice-and-reconciliation"></a>Fatura e reconciliação

Os seguintes cenários mostram-lhe como visualizar programaticamente as [faturas](invoice-resources.md)do seu cliente, e obter os saldos e resumos da sua conta que incluem encargos pontuais.

### <a name="balance-and-payment"></a>Saldo e pagamento

Para obter o saldo da conta corrente no seu tipo de moeda padrão que é um saldo de encargos recorrentes e pontuais, consulte [obter o saldo da sua conta corrente](get-the-reseller-s-current-account-balance.md)

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
