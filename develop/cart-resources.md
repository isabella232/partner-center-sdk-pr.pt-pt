---
title: Recursos de carrinhos
description: Um parceiro coloca um pedido num carrinho quando um cliente quer comprar uma subscrição a partir de uma lista de ofertas.
ms.date: 08/26/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 08085dde1b43f20b6f6bf707120dd87c48816aba
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974153"
---
# <a name="cart-resources"></a>Recursos de carrinhos

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Um parceiro coloca uma encomenda quando um cliente quer comprar uma subscrição a partir de uma lista de ofertas.

## <a name="cart"></a>Carrinho

Descreve um carrinho.

| Propriedade              | Tipo             | Description                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| ID                    | string           | Um identificador de carrinhos que é fornecido após a criação bem sucedida do carrinho.                               |
| criaçãoTimeStamp     | DateTime         | A data em que o carrinho foi criado, em formato de data- hora. Aplicado após a criação bem sucedida do carrinho.      |
| últimampadatimestamp de Tempos | DateTime         | A data em que o carrinho foi atualizado pela última vez, em formato de data-hora. Aplicado após a criação bem sucedida do carrinho. |
| expiraçãoTimeStamp   | DateTime         | A data em que o carrinho expirará, em formato de data-hora. Aplicado após a criação bem sucedida do carrinho.          |
| últimoModifiedUser      | string           | O utilizador que atualizou pela última vez o carrinho. Aplicado após a criação bem sucedida do carrinho.                          |
| lineitems             | Matriz de objetos | Uma matriz de recursos [CartLineItem.](#cartlineitem)                                                   |
| status                | string           | O estado do carrinho. Os valores possíveis são "Ative" (pode ser atualizado/submetido) e "Ordenado" (já foi apresentado). |

## <a name="cartlineitem"></a>CartLineItem

Representa um item contido num carrinho.

| Propriedade             | Tipo                             | Description                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID                   | string                           | Um identificador único para um item de linha de carrinho. Aplicado após a criação bem sucedida do carrinho.                                                                   |
| catalogItemId        | string                           | O identificador de artigos de catálogo.                                                                                                                          |
| nome amigável         | string                           | Opcional. O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.                                                                 |
| quantidade             | int                              | O número de licenças ou instâncias.                                                                                                                  |
| currencyCode         | string                           | O código da moeda.                                                                                                                                    |
| billingCycle         | Objeto                           | O tipo de ciclo de faturação definido para o período atual.                                                                                                 |
| termoDuração         | string                           | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são P1M (1 mês), P1Y (1 ano) e P3Y (3 anos).                                |
| participantes         | Lista de pares de cordas de objeto      | Uma coleção de PartnerId on Record (MPN ID) na compra.                                                                                          |
| provisionamentoContexto  | Cadeia de<do dicionário,> de cordas       | Contexto adicional utilizado no fornecimento do artigo adquirido. Para determinar quais os valores necessários para um determinado item, consulte a propriedade de ProvisioningVariables do SKU. |
| orderGroup           | string                           | Um grupo para indicar quais os itens que podem ser submetidos em conjunto na mesma ordem.                                                                          |
| addonItems           | Lista de **objetos CartLineItem** | Uma coleção de itens de linha de carrinho para addons. Estes itens serão adquiridos para a subscrição base que resulta da compra do item da linha do carrinho de raiz. |
| erro                | Objeto                           | Aplicado após o carrinho é criado se ocorrer um erro.                                                                                                    |
| renovaTo             | Matriz de objetos                 | Uma variedade de [recursos Renovados.](#renewsto)                                                                            |

## <a name="renewsto"></a>RenovarTo

Representa um item contido num item da linha do carrinho.

| Propriedade              | Tipo             | Necessário        | Descrição |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termoDuração          | cadeia (de carateres)           | No              | Uma representação ISO 8601 da duração do período de renovação. Os valores suportados atuais são **P1M** (1 mês) e **P1Y** (1 ano). |

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

## <a name="carterror"></a>CartError

Representa um erro que ocorre após a criação de um carrinho.

| Propriedade         | Tipo                                   | Description                                                                                   |
|------------------|----------------------------------------|-----------------------------------------------------------------------------------------------|
| errorCode        | [Códigos de erro do Centro de Parceiros](error-codes.md) | O tipo de erro do carrinho.                                                                       |
| erroDescrição | string                                 | A descrição do erro, incluindo quaisquer notas sobre valores suportados, valores predefinidos ou limites. |

## <a name="cartcheckoutresult"></a>CartCheckoutResult

Representa o resultado de um check-out de carrinho.

| Propriedade    | Tipo                                              | Description                     |
|-------------|---------------------------------------------------|---------------------------------|
| encomendas      | Lista de objetos [da Ordem.](order-resources.md#order)         | A coleção de ordens.       |
| orderErrors | Lista de objetos [OrderError.](#ordererror) | A recolha de erros de ordem. |

## <a name="ordererror"></a>OrderError

Representa um erro que ocorre durante um check-out do carrinho quando uma encomenda é criada.

| Propriedade     | Tipo   | Description                                     |
|--------------|--------|-------------------------------------------------|
| orderGroupId | string | O grupo de pedidos identificação da ordem com o erro. |
| code         | int    | O código de erro.                                 |
| descrição  | string | A descrição do erro.                   |
