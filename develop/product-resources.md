---
title: Recursos de produtos
description: Recursos que representam bens ou serviços puráveis. Inclui recursos para descrever o tipo e forma do produto (SKU), e para verificar a disponibilidade do produto num inventário.
ms.date: 02/16/2016
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 20e2d7bcaf1041f186f0723d7ff453bebbe46dd2
ms.sourcegitcommit: f112efee7344d739bdbf385adba0c554ea2a63e3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439366"
---
# <a name="products-resources"></a>Recursos de produtos

Recursos que representam bens ou serviços puráveis. Inclui recursos para descrever o tipo e forma do produto (SKU), e para verificar a disponibilidade do produto num inventário.

## <a name="product"></a>Produto

Representa um bem ou serviço purivel. Um produto por si só não é um item puriável.

| Propriedade           | Tipo                          | Descrição                                                              |
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

| Propriedade        | Tipo                          | Descrição                                                                          |
|-----------------|-------------------------------|--------------------------------------------------------------------------------------|
| ID              | string                        | O tipo de identificador.                                                                 |
| displayName     | string                        | O nome de exibição deste tipo.                                                      |
| subTipo         | [ItemType](#itemtype)         | Opcional. Um objeto que descreve uma categorização do subtipo para este tipo de item.     |

## <a name="productlinks"></a>Ligações de Produtos

Contém uma lista de links para um [Produto.](#product)

| Propriedade        | Tipo                                                          | Descrição                                          |
|-----------------|---------------------------------------------------------------|------------------------------------------------------|
| skus            | [Ligação](utility-resources.md#link)                             | A ligação para o acesso aos SKUs subjacentes.          |
| ligações           | [RecursosLinks](utility-resources.md#resourcelinks)           | As ligações de recursos contidas neste recurso.   |

## <a name="sku"></a>Sku

Representa uma unidade de armazenamento de stock (SKU) em um produto. Estes representam as diferentes formas do produto.

| Propriedade               | Tipo             | Descrição                                                                           |
|------------------------|------------------|---------------------------------------------------------------------------------------|
| ID                     | string           | A identificação deste SKU. Este ID é único apenas no contexto do seu produto-mãe. |
| título                  | string           | O título do SKU.                                                                 |
| descrição            | string           | A descrição do SKU.                                                           |
| productId              | string           | O ID do [produto-mãe](#product) que contém este SKU.                      |
| mínimoQuantidade        | int              | A quantidade mínima permitida para compra.                                            |
| máximaQuantidade        | int              | A quantidade máxima permitida para compra.                                            |
| isTrial                | bool             | Indica se este SKU é um item de teste.                                           |
| suportadosBillingCycles | matriz de cadeias (de carateres) | A lista de ciclos de faturação suportados para este SKU. Os valores suportados são os nomes dos membros encontrados no [BillingCycleType](#billingcycletype). |
| aquisiçãoPrerequites  | matriz de cadeias (de carateres) | A lista de etapas ou ações pré-requisitos que são necessárias antes da compra deste artigo. Os valores suportados são:<br/>  "InventoryCheck" - Indica que o inventário do artigo deve ser avaliado antes de tentar comprar este item.<br/> "AzureSubscriptionRegistration" - Indica que é necessária uma subscrição Azure e deve ser registada antes de tentar comprar este artigo.  |
| inventárioVariables     | matriz de cadeias (de carateres) | A lista de variáveis necessárias para executar uma verificação de inventário neste item. Os valores suportados são:<br/> "CustomerId" - A identificação do cliente para a a que a compra seria.<br/> "AzureSubscriptionId" - O ID da subscrição Azure que seria usado para uma compra de reserva Azure.</br> "ArmRegionName" - A região para a qual verificar o inventário. Este valor deve coincidir com o "ArmRegionName" dos DynamicAttributes do SKU. |
| provisionamentoVariables  | matriz de cadeias (de carateres) | A lista de variáveis que devem ser fornecidas no contexto de provisionamento de um item da [linha do carrinho](cart-resources.md#cartlineitem) na compra deste item. Os valores suportados são:<br/> Âmbito - O âmbito para uma compra de reserva Azure: "Single", "Shared".<br/> "SubscriptionId" - O ID da subscrição Azure que seria usado para uma compra de reserva Azure.<br/> "Duração" - A duração da reserva Azure: "1 Ano", "3º Ano".  |
| dynamicAttributes      | pares chave/valor  | O dicionário de propriedades dinâmicas que se aplicam a este item. As propriedades deste dicionário são dinâmicas e podem mudar sem aviso prévio. Não deve criar fortes dependências de chaves específicas existentes no valor deste imóvel.    |
| ligações                  | [RecursosLinks](utility-resources.md#resourcelinks) | As ligações de recursos contidas no SKU.                   |
| AttestationProperties                  | [AttestationProperties](#attestationproperties) | As propriedades do atestado para um SKU.                   |
| tipo de consumo                  | string | Só está disponível se o sku apoiar o consumo, como *excesso de idade.*               |

## <a name="dynamic-sku-attributes"></a>Atributos Dinâmicos SKU

Imóveis notáveis relevantes para novos produtos e serviços baseados em licenças de comércio.

> [!Note] 
> As novas alterações ao Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365

| Propriedade        | Tipo                        | Descrição                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------------------------------|
|temConstratas|boolean|Descreve se o SKU contém activosContraints|
|isAddon|boolean|Descreve se o SKU é um complemento|
|pré-requisitoSkus|matriz de cadeias (de carateres)|Descreve produtos e skus o add on pode trabalhar com|
|upgradeTargetOffers|matriz de cadeias (de carateres)|Uma lista de produtos e skus o item pode atualizar para|
|conversõesInstruções|lista de conversõesInstructs|Lista de instruções aplicáveis às operações de conversação|

## <a name="availability"></a>Disponibilidade

Representa uma configuração em que um SKU está disponível para compra (como país, moeda e segmento da indústria).

| Propriedade        | Tipo                        | Descrição                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------------------------------|
| ID              | string                        | O ID para esta disponibilidade. Este ID é único apenas no contexto do seu [produto-mãe](#product) e [SKU.](#sku) **Nota** Esta identificação pode mudar com o tempo. Só deve confiar neste valor num curto espaço de tempo após a sua recuperação.  |
| productId       | string                        | O ID do [produto](#product) que contém esta disponibilidade.           |
| skuId           | string                        | O ID do [SKU](#sku) que contém esta disponibilidade.                   |
| catalogItemId   | string                        | O identificador único para este item no catálogo. Este é o ID que deve ser povoado nas propriedades [OrderLineItem.OfferId](order-resources.md#orderlineitem) ou [CartLineItem.CatalogItemId](cart-resources.md#cartlineitem) ao comprar o [SKU-mãe.](#sku) **Nota** Esta identificação pode mudar com o tempo. Só deve confiar neste valor num curto espaço de tempo após a sua recuperação. Só deve ser acedido e utilizado no momento da compra.  |
| incumprimentoSidade | string                        | A moeda predefinida suportada para esta disponibilidade.                               |
| segmento         | string                        | O segmento da indústria para esta disponibilidade. Os valores suportados são: Comercial, Educação, Governo, Não Lucrativo. |
| país         | string                                              | O país ou região (em formato de código de país ISO) onde esta disponibilidade se aplica. |
| isCompessível   | bool                                                | Indica se esta disponibilidade é purável. |
| isRenewable     | bool                                                | Indica se esta disponibilidade é renovável. |
| RenovaçãoInstruções     | RenovaçãoInstrução                                              | Representa instruções de renovação para uma determinada disponibilidade. |
| produto      | [Produto](#product)               | O produto a que esta disponibilidade corresponde. |
| sku          | [Sku](#sku)            | O SKU esta disponibilidade corresponde a. |
| termos           | matriz de recursos [de prazo](#term)  | A recolha de termos que são aplicáveis a esta disponibilidade. |
| ligações           | [RecursosLinks](utility-resources.md#resourcelinks) | As ligações de recursos contidas na disponibilidade. |

## <a name="renewal-instruction"></a>Instrução de renovação

> [!Note] 
> As novas alterações ao Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365
> 

Representa instruções de renovação para uma determinada disponibilidade.

| Propriedade        | Tipo                        | Descrição                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------|
| aplicaçãoTermIds       | matriz de cadeias (de carateres)                       | IDs de prazo as instruções se aplicam a |
| Opções de Renovação       | matriz de RenovaçãoOption                     | Opções que definem renovações |

## <a name="renewaloption"></a>Renovação    

> [!Note] 
> As novas alterações ao Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365
> 

Representa instruções de renovação para uma determinada disponibilidade.

| Propriedade        | Tipo                        | Descrição                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------|
| renovarToId       | String       | Representa o produto e sku para renovar para |
| isAutoRenewable       | Booleano       | Se a disponibilidade pode ou não ser renovada automaticamente |

## <a name="term"></a>Termo

Representa um termo para o qual a disponibilidade pode ser adquirida.

| Propriedade              | Tipo                                        | Descrição                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| duration              | string                                      | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são P1M (1 mês), P1Y (1 ano) e P3Y (3 anos). |
| descrição           | string                                      | A descrição do termo.           |

## <a name="inventorycheckrequest"></a>InventárioCheckRequest

Representa um pedido de verificação do inventário em certos itens de catálogo.

| Propriedade         | Tipo                                                | Descrição                                                                                 |
|------------------|-----------------------------------------------------|---------------------------------------------------------------------------------------------|
| targetItems      | matriz de [InventoryItem](#inventoryitem)            | A lista de itens de catálogo que o cheque de inventário irá avaliar.                           |
| inventárioContexto | pares chave/valor                                     | O dicionário de valores de contexto necessários para a realização do(s) verificação de inventário. Cada [SKU](#sku) dos produtos definirá quais os valores (se houver) necessários para realizar esta operação.  |
| ligações            | [RecursosLinks](utility-resources.md#resourcelinks) | As ligações de recursos contidas no pedido de verificação de inventário.                            |

## <a name="inventoryitem"></a>InventárioItem

Representa um único item numa operação de verificação de inventário. Este recurso é utilizado para especificar os itens-alvo num pedido de entrada e é também utilizado para representar os resultados da operação de verificação de inventário.

| Propriedade         | Tipo                                                              | Descrição                                                                      |
|------------------|-------------------------------------------------------------------|----------------------------------------------------------------------------------|
| productId        | string                                                            | (Obrigatório) A identificação do [produto.](#product)                            |
| skuId            | string                                                            | A identificação do [SKU.](#sku) Ao utilizar este recurso como entrada para um pedido de inventário, este valor é opcional. Se este valor não for fornecido, todos os SKUs ao abrigo do produto serão considerados como itens-alvo da operação de verificação de inventário.      |
| isRestrited     | bool                                                              | Indica se este item foi encontrado com um inventário restrito.            |
| Restrições     | matriz de [InventárioRestriction](#inventoryrestriction)            | Os detalhes de quaisquer restrições que sejam encontradas para este item. Esta propriedade só será povoada se **forRestricted** = "true". |

## <a name="inventoryrestriction"></a>InventárioRestrics

Representa os detalhes de uma restrição de inventário. Isto só é aplicável para os resultados da saída de verificação de inventário, não para pedidos de entrada.

| Propriedade         | Tipo                  | Descrição                                                                                 |
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

## <a name="attestationproperties"></a>AttestationProperties

Representa um tipo de atestado e se for necessário para compra.

| Propriedade              | Tipo                                        | Descrição                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| attestationType              | string                                      | Indica o tipo de atestado. Para Windows 365 o valor é o Windows365. Windows texto de atestado 365 é "Entendo que cada pessoa que usa Windows 365 Negócios com Windows Hybrid Benefit também precisa de ter uma cópia válida de Windows 10/11 Pro instalada no seu dispositivo de trabalho primário." |
| impor Attestation           | boolean                                      | Indica se o atestado é necessário para compra.           |
