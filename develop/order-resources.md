---
title: Recursos de encomenda
description: Um parceiro coloca uma encomenda quando um cliente quer comprar uma subscrição a partir de uma lista de ofertas.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9db07337a98214b4aaa93e2c8b43b84702249b77
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769230"
---
# <a name="order-resources"></a>Recursos de encomenda

**Aplica-se a:**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Um parceiro coloca uma encomenda quando um cliente quer comprar uma subscrição a partir de uma lista de ofertas.

>[!NOTE]
>O recurso Ordem tem um limite de taxa de 500 pedidos por minuto por identificador de inquilino.

## <a name="order"></a>Encomenda

Descreve a ordem de um parceiro.

| Propriedade           | Tipo                                               | Descrição                                                 |
|--------------------|----------------------------------------------------|-------------------------------------------------------------|
| ID                 | string                                             | Um identificador de ordem que é fornecido após a criação bem sucedida da ordem.                                   |
| alternateId        | string                                             | Um identificador amigável para a ordem.                                                                          |
|referênciaStomerId | string                                             | O identificador de clientes. |
| billingCycle       | string                                             | Indica a frequência com que o parceiro é faturado para esta encomenda. Os valores suportados são os nomes dos membros encontrados no [BillingCycleType](product-resources.md#billingcycletype). O padrão é "Mensal" ou "OneTime" na criação da ordem. Este campo é aplicado após a criação bem sucedida da ordem. |
| tipo de transação    | string                                             | Só para ler. O tipo de transação da encomenda. Os valores suportados são 'UserPurchase', 'SystemPurchase' ou 'SystemBilling' |
| lineitems          | matriz de recursos [OrderLineItem](#orderlineitem) | Uma lista itemada das ofertas que o cliente está a comprar, incluindo a quantidade.        |
| currencyCode       | string                                             | Só para ler. A moeda utilizada na eção da encomenda. Aplicado após a criação bem sucedida da ordem.           |
| moedaSymbol     | string                                             | Só para ler. O símbolo da moeda associado ao código cambial. |
| criaçãoDate       | datetime                                           | Só para ler. A data em que a encomenda foi criada, em formato de data-hora. Aplicado após a criação bem sucedida da ordem.                                   |
| status             | string                                             | Só para ler. O estado da ordem.  Os valores suportados são os nomes dos membros encontrados no [**OrderStatus**](#orderstatus).        |
| ligações              | [Pedidos](utility-resources.md#resourcelinks)           | Os links de recursos correspondentes à Ordem.            |
| atributos         | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados atribuem correspondentes à Ordem.       |

## <a name="orderlineitem"></a>OrderLineItem

Uma encomenda contém uma lista de ofertas itemizada, e cada item é representado como um OrderLineItem.

| Propriedade             | Tipo                                      | Descrição                                                                                                                                                                                                                                |
|----------------------|-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| lineItemNumber       | int                                       | Cada item de linha da coleção obtém um número de linha único, contando de 0 a 1.                                                                                                                                                 |
| offerId              | string                                    | A identificação da oferta.                                                                                                                                                                                                                       |
| subscriptionId       | string                                    | A identificação da assinatura.                                                                                                                                                                                                                |
| parentSubscriptionId | string                                    | Opcional. A identificação da subscrição dos pais numa oferta de complemento. Aplica-se apenas ao PATCH.                                                                                                                                                     |
| nome amigável         | string                                    | Opcional. O nome amigável para a subscrição definida pelo parceiro para ajudar a desambiguar.                                                                                                                                              |
| quantidade             | int                                       | O número de licenças ou instâncias.                                                                                                                                                                                |
| termoDuração         | string                                    | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são **P1M** (1 mês), **P1Y** (1 ano) e **P3Y** (3 anos).                               |
| tipo de transação      | string                                    | Só para ler. O tipo de transação do item da linha. Os Valores Suportados são 'novos', 'renovar', 'addQuantity', 'removerQuantity', 'cancelar', 'converter', ou 'customerCredit'. |
| partnerIdOnRecord    | string                                    | Quando um fornecedor indireto estoende uma encomenda em nome de um revendedor indireto, povoe este campo apenas com o ID MPN do **revendedor indireto** (nunca o ID do fornecedor indireto). Isto garante uma contabilização adequada dos incentivos. |
| provisionamentoContexto  | Cadeia de<do dicionário,> de cordas            | Informação necessária para o provisionamento de alguns itens no catálogo. A propriedade de ProvisioningVariables num SKU indica quais propriedades são necessárias para itens específicos no catálogo.                                                                                                                                               |
| ligações                | [OrderLineItemLinks](#orderlineitemlinks) | Só para ler. As ligações de recursos correspondentes ao item da linha de encomenda.                                                                                                                                                                                |
| renovaTo             | [RenovarTo](#renewsto)                         |Detalhes da duração do prazo de renovação.                                                                           |

## <a name="renewsto"></a>RenovarTo

Representa os detalhes da duração do prazo de renovação.

| Propriedade              | Tipo             | Necessário        | Descrição |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termoDuração          | cadeia (de carateres)           | No              | Uma representação ISO 8601 da duração do período de renovação. Os valores suportados atuais são **P1M** (1 mês) e **P1Y** (1 ano). |

## <a name="orderlinks"></a>Pedidos

Representa as ligações de recursos correspondentes à ordem.

| Propriedade           | Tipo                                         | Descrição                                                                   |
|--------------------|----------------------------------------------|-------------------------------------------------------------------------------|
| provisionamentoStatus | [Ligação](utility-resources.md#link)            | Quando povoado, a ligação para recuperar o estado de provisionamento da encomenda.       |
| self               | [Ligação](utility-resources.md#link)            | O link para recuperar o recurso da encomenda.                                      |

## <a name="orderlineitemlinks"></a>OrderLineItemLinks

Representa a subscrição completa associada à encomenda.

| Propriedade           | Tipo                                         | Descrição                                                                          |
|--------------------|----------------------------------------------|--------------------------------------------------------------------------------------|
| provisionamentoStatus | [Ligação](utility-resources.md#link)            | Quando povoado, o link para recuperar o estado de [provisionamento](#orderlineitemprovisioningstatus) do item da linha.       |
| sku                | [Ligação](utility-resources.md#link)            | O link para recuperar informações do SKU para o item do catálogo comprado.                    |
| subscrição       | [Ligação](utility-resources.md#link)            | Quando povoado, a ligação à informação completa da subscrição.                       |
| activaçãoLinks    | [Ligação](utility-resources.md#link)            | Quando povoado, o recurso GET para links para ativar a subscrição.             |

## <a name="orderstatus"></a>Ordem Estatísticas

Um [Enum/dotnet/api/system.enum) com valores que indicam o estado da ordem.

| Valor              | Posição     | Descrição                                     |
|--------------------|--------------|-------------------------------------------------|
| desconhecido            | 0            | Inicializador Enum.                               |
| concluído          | 1            | Indica que a encomenda está completa.          |
| pendente            | 2            | Indica que a ordem ainda está pendente.      |
| cancelado          | 3            | Indica que a encomenda foi cancelada.    |

## <a name="orderlineitemprovisioningstatus"></a>OrderLineItemProvisioningStatus

Representa o estatuto de provisionamento de um [OrderLineItem](#orderlineitem).

| Propriedade                        | Tipo                                | Descrição                                                                                |
|------------------------------------|-------------------------------------|--------------------------------------------------------------------------------------------|
| lineItemNumber                  | int                                 | O número único da linha do item da linha de encomenda. Os valores variam de 0 a 1.             |
| status                          | string                              | O estado de provisionamento do item da linha de encomenda. Os valores incluem:</br>"Cumprido": O cumprimento da encomenda é concluído com sucesso e o utilizador poderá utilizar as reservas</br>"Não cumprido": Não cumprido devido a cancelamento</br>"PrefulfillmentPending": O seu pedido ainda está a ser processado, o cumprimento ainda não está completo |
| quantidadeProvisioningInformation | Lista<[QuantityProvisioningStatus](#quantityprovisioningstatus)> | Uma lista de informações sobre o estado de provisão da quantidade para o item da linha de encomenda. |

## <a name="quantityprovisioningstatus"></a>QuantidadeProvisãoStatus

Representa o estatuto de provisionamento por quantidade.

| Propriedade                           | Tipo                                         | Descrição                                          |
|------------------------------------|----------------------------------------------|------------------------------------------------------|
| quantidade                           | int                                          | O número de itens.                                 |
| status                             | string                                       | O estado do número de artigos.                   |
