---
title: Recursos de produtos
description: Recursos que representam bens ou serviços puráveis. Inclui recursos para descrever o tipo e forma do produto (SKU), e para verificar a disponibilidade do produto num inventário.
ms.date: 04/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1d536cb78c070bd06f4ab9434e066e51fb4c008c
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445889"
---
# <a name="products-resources"></a>Recursos de produtos

Recursos que representam bens ou serviços puráveis. Inclui recursos para descrever o tipo e forma do produto (SKU), e para verificar a disponibilidade do produto num inventário.

## <a name="product"></a>Produto

Representa um bem ou serviço purivel. Um produto por si só não é um item purivel.

| Propriedade           | Tipo                          | Description                                                              |
|--------------------|-------------------------------|--------------------------------------------------------------------------|
| ID                 | string                        | A identificação deste produto.                                                 |
| título              | string                        | O título do produto.                                                       |
| descrição        | string                        | A descrição do produto.                                                 |
| productType        | [ItemType](#itemtype)         | Um objeto que descreve o tipo de categorização deste produto.     |
| isMicrosoftProduct | bool                          | Indica se se trata de um produto Microsoft.                          |
| publisherName      | string                        | O nome do editor do produto, se disponível.                          |
| ligações              | [Ligações de Produtos](#productlinks) | As ligações de recursos contidas no produto.                         |

## <a name="itemtype"></a>TipoItem

Representa o tipo de produto.

| Propriedade        | Tipo                          | Description                                                                          |
|-----------------|-------------------------------|--------------------------------------------------------------------------------------|
| ID              | string                        | O tipo de identificador.                                                                 |
| displayName     | string                        | O nome de exibição deste tipo.                                                      |
| subtiType         | [ItemType](#itemtype)         | Opcional. Um objeto que descreve uma categorização do subtipo para este tipo de item.     |

## <a name="productlinks"></a>Ligações de Produtos

Contém uma lista de links para um [Produto.](#product)

| Propriedade        | Tipo                                                          | Description                                          |
|-----------------|---------------------------------------------------------------|------------------------------------------------------|
| skus            | [Ligação](utility-resources.md#link)                             | A ligação para o acesso aos SKUs subjacentes.          |
| ligações           | [RecursosLinks](utility-resources.md#resourcelinks)           | As ligações de recursos contidas neste recurso.   |

## <a name="sku"></a>Sku

Representa uma unidade de armazenamento de stock (SKU) em um produto. Estes representam as diferentes formas do produto.

| Propriedade               | Tipo             | Description                                                                           |
|------------------------|------------------|---------------------------------------------------------------------------------------|
| ID                     | string           | A identificação deste SKU. Este ID é único apenas no contexto do seu produto-mãe. |
| título                  | string           | O título do SKU.                                                                 |
| descrição            | string           | A descrição do SKU.                                                           |
| productId              | string           | A identificação do [produto-mãe](#product) que contém este SKU.                      |
| mínimoQuantidade        | int              | A quantidade mínima permitida para compra.                                            |
| máximaQuantidade        | int              | A quantidade máxima permitida para compra.                                            |
| isTrial                | bool             | Indica se este SKU é um item de teste.                                           |
| suportadosBillingCycles | matriz de cadeias (de carateres) | A lista de ciclos de faturação suportados para este SKU. Os valores suportados são os nomes dos membros encontrados no [BillingCycleType](#billingcycletype). |
| aquisiçãoPrerequites  | matriz de cadeias (de carateres) | A lista de etapas ou ações pré-requisitos que são necessárias antes da compra deste artigo. Os valores suportados são:<br/>  "InventoryCheck" - Indica que o inventário do artigo deve ser avaliado antes de tentar comprar este item.<br/> "AzureSubscriptionRegistration" - Indica que é necessária uma subscrição Azure e deve ser registada antes de tentar comprar este artigo.  |
| inventárioVariables     | matriz de cadeias (de carateres) | A lista de variáveis necessárias para executar uma verificação de inventário neste item. Os valores suportados são:<br/> "CustomerId" - A identificação do cliente para a a compra.<br/> "AzureSubscriptionId" - O ID da subscrição Azure que seria usado para uma compra de reserva Azure.</br> "ArmRegionName" - A região para a qual verificar o inventário. Este valor deve coincidir com o "ArmRegionName" dos DynamicAttributes do SKU. |
| provisionamentoVariables  | matriz de cadeias (de carateres) | A lista de variáveis que devem ser fornecidas no contexto de provisionamento de um item da [linha do carrinho](cart-resources.md#cartlineitem) na compra deste item. Os valores suportados são:<br/> Âmbito - O âmbito para uma compra de reserva Azure: "Single", "Shared".<br/> "SubscriptionId" - O ID da subscrição Azure que seria usado para uma compra de reserva Azure.<br/> "Duração" - A duração da reserva Azure: "1Year", "3Year".  |
| dynamicAttributes      | pares chave/valor  | O dicionário de propriedades dinâmicas que se aplicam a este item. As propriedades deste dicionário são dinâmicas e podem mudar sem aviso prévio. Não deve criar fortes dependências de chaves específicas existentes no valor deste imóvel.    |
| ligações                  | [RecursosLinks](utility-resources.md#resourcelinks) | As ligações de recursos contidas no SKU.                   |

## <a name="availability"></a>Disponibilidade

Representa uma configuração em que um SKU está disponível para compra (como país, moeda e segmento da indústria).

| Propriedade        | Tipo                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------------------------------|
| ID              | string                        | O ID para esta disponibilidade. Este ID é único apenas no contexto do seu [produto-mãe](#product) e [SKU.](#sku) **Nota** Esta identificação pode mudar com o tempo. Só deve confiar neste valor num curto espaço de tempo após a sua recuperação.  |
| productId       | string                        | O ID do [produto](#product) que contém esta disponibilidade.           |
| skuId           | string                        | O ID do [SKU](#sku) que contém esta disponibilidade.                   |
| catalogItemId   | string                        | O identificador único para este item no catálogo. Este é o ID que deve ser povoado nas propriedades [OrderLineItem.OfferId](order-resources.md#orderlineitem) ou [CartLineItem.CatalogItemId](cart-resources.md#cartlineitem) ao comprar o [SKU-mãe](#sku). **Nota** Esta identificação pode mudar com o tempo. Só deve confiar neste valor num curto espaço de tempo após a sua recuperação. Só deve ser acedido e utilizado no momento da compra.  |
| incumprimentoSidade | string                        | A moeda predefinida suportada para esta disponibilidade.                               |
| segmento         | string                        | O segmento da indústria para esta disponibilidade. Os valores suportados são: Comercial, Educação, Governo, Não-Lucrativo. |
| país         | string                                              | O país ou região (em formato de código de país ISO) onde esta disponibilidade se aplica. |
| isComprável   | bool                                                | Indica se esta disponibilidade é purável. |
| é Reemnovável     | bool                                                | Indica se esta disponibilidade é renovável. |
| produto      | [Produto](#product)               | O produto a que esta disponibilidade corresponde. |
| sku          | [Sku](#sku)            | O SKU esta disponibilidade corresponde a. |
| termos           | matriz de recursos [de prazo](#term)  | A recolha de termos aplicáveis a esta disponibilidade. |
| ligações           | [RecursosLinks](utility-resources.md#resourcelinks) | As ligações de recursos contidas na disponibilidade. |

## <a name="term"></a>Termo

Representa um termo para o qual a disponibilidade pode ser adquirida.

| Propriedade              | Tipo                                        | Description                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| duration              | string                                      | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são P1M (1 mês), P1Y (1 ano) e P3Y (3 anos). |
| descrição           | string                                      | A descrição do termo.           |

## <a name="inventorycheckrequest"></a>InventárioCheckRequest

Representa um pedido de verificação do inventário contra certos itens de catálogo.

| Propriedade         | Tipo                                                | Description                                                                                 |
|------------------|-----------------------------------------------------|---------------------------------------------------------------------------------------------|
| targetItems      | matriz de [InventoryItem](#inventoryitem)            | A lista de itens de catálogo que o cheque de inventário irá avaliar.                           |
| inventárioContexto | pares chave/valor                                     | O dicionário de valores de contexto necessários para a realização do(s) verificação de inventário. Cada [SKU](#sku) dos produtos definirá quais os valores (se houver) necessários para realizar esta operação.  |
| ligações            | [RecursosLinks](utility-resources.md#resourcelinks) | As ligações de recursos contidas no pedido de verificação de inventário.                            |

## <a name="inventoryitem"></a>InventárioItem

Representa um único item numa operação de verificação de inventário. Este recurso é utilizado para especificar os itens-alvo num pedido de entrada e é também utilizado para representar os resultados da operação de verificação de inventário.

| Propriedade         | Tipo                                                              | Description                                                                      |
|------------------|-------------------------------------------------------------------|----------------------------------------------------------------------------------|
| productId        | string                                                            | (Obrigatório) A identificação do [produto.](#product)                            |
| skuId            | string                                                            | A identificação do [SKU.](#sku) Ao utilizar este recurso como entrada para um pedido de inventário, este valor é opcional. Se este valor não for fornecido, todos os SKUs ao abrigo do produto serão considerados como itens-alvo da operação de verificação de inventário.      |
| isRestrited     | bool                                                              | Indica se este item foi encontrado com um inventário restrito.            |
| Restrições     | matriz de [InventárioRestriction](#inventoryrestriction)            | Os detalhes de quaisquer restrições que sejam encontradas para este item. Esta propriedade só será povoada se **forRestricted** = "true". |

## <a name="inventoryrestriction"></a>InventárioRestricação

Representa os detalhes de uma restrição de inventário. Isto só é aplicável para os resultados da verificação de inventário, não para pedidos de entrada.

| Propriedade         | Tipo                  | Description                                                                                 |
|------------------|-----------------------|---------------------------------------------------------------------------------------------|
| reasonCode       | string                | O código que identifica o motivo da restrição.                                    |
| descrição      | string                | A descrição da restrição de inventário.                                               |
| propriedades       | pares chave/valor       | O dicionário de propriedades que podem fornecer mais detalhes sobre a restrição.           |

## <a name="billingcycletype"></a>BillingCycleType

Um [Enum/dotnet/api/system.enum) com valores que indicam um tipo de ciclo de faturação.

| Valor              | Posição     | Description                                                                                |
|--------------------|--------------|--------------------------------------------------------------------------------------------|
| Desconhecido            | 0            | Inicializador Enum.                                                                          |
| Mensalmente            | 1            | Indica que o parceiro será cobrado mensalmente.                                        |
| Anuais             | 2            | Indica que o parceiro será cobrado anualmente.                                       |
| Nenhuma               | 3            | Indica que o parceiro não será carregado. Este valor pode ser utilizado para itens de ensaio.    |
| OneTime            | 4            | Indica que o parceiro será carregado uma vez.                                       |
