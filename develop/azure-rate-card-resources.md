---
title: Cartão de taxa Azure - preços atuais do Azure
description: Saiba como usar o Cartão Azure Rate para obter em tempo real, preços correntes para ofertas Azure na sua região. O Cartão Azure Rate é acedido através da API do Partner Center REST.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 52b9a9bea59690a8185a381647498de69a1476b1a4d4e8d632c5d13382776114
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991219"
---
# <a name="azure-rate-card-resources-to-get-real-time-current-azure-prices-on-azure-offers-in-your-region"></a>Recursos de cartão de tarifa Azure para obter em tempo real, preços atuais do Azure em ofertas Azure na sua região

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

O Cartão Azure Rate oferece preços em tempo real para ofertas Azure. Os preços do Azure são dinâmicos e mudam frequentemente. A Microsoft publica atualizações no Partner Center, mas a API REST fornece a forma mais rápida de os parceiros Fornecedor de Soluções em Nuvem obterem os preços atuais.

Para acompanhar o uso e ajudar a prever a sua fatura mensal e as faturas para clientes individuais, pode combinar uma consulta de Cartão de Tarifa para [Obter preços para Microsoft Azure](get-prices-for-microsoft-azure.md) com um pedido para obter os [registos de utilização de um cliente para o Azure.](get-a-customer-s-utilization-record-for-azure.md)

Os preços diferem por mercado e por moeda, e esta API tem em conta a localização. Por padrão, a API utiliza as definições de perfil do seu parceiro no Partner Center e no seu idioma do navegador, e essas definições são personalizáveis. A consciência da localização é especialmente relevante se você gerir vendas em vários mercados a partir de um único escritório centralizado.

## <a name="azureratecard"></a>AzureRateCard

Descreve as propriedades de um recurso de cartão Azure Rate.

| Propriedade      | Tipo                                      | Description                                                       |
|---------------|-------------------------------------------|-------------------------------------------------------------------|
| moeda      | string                                    | A moeda em que as taxas são fornecidas.                     |
| isTaxIncluded | boolean                                   | Todas as tarifas são pré-impostos, por isso esta propriedade retorna como `false` . |
| região        | string                                    | A cultura em que a informação dos recursos está localizada.       |
| contadores        | matriz de objetos                          | Matriz de objetos [AzureMeter.](#azuremeter)                       |
| ofertaTerms    | matriz de objetos                          | Matriz de objetos [AzureOfferTerm.](#azureofferterm)               |
| atributos    | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados. Contém `"objectType": "AzureRateCard"`   |

### <a name="operations-on-the-azureratecard-resource"></a>Operações no recurso AzureRateCard

- [Obter preços do Microsoft Azure](get-prices-for-microsoft-azure.md)

## <a name="azuremeter"></a>AzureMeter

| Propriedade         | Tipo             | Descrição                                                                                   |
|------------------|------------------|-----------------------------------------------------------------------------------------------|
| ID               | string           | O identificador único do Metro.                                                                    |
| name             | string           | Nome amigável do medidor.                                                                   |
| taxas            | objeto           | Taxas de contador. A chave é a quantidade do medidor (cadeia) e o valor é a taxa do contador (número). |
| etiquetas             | matriz de cadeias (de carateres) | Etiquetas de contadores opcionais. Esta matriz pode estar vazia.                                                 |
| categoria         | string           | Categoria do recurso.                                                                     |
| subcategoria      | string           | Subcategoria do recurso.                                                                 |
| region           | string           | Região da identificação.                                                                             |
| unit             | string           | O tipo de quantidade (horas, bytes, etc.)                                                     |
| includedQuantity | número           | Quantidade de contadores que está incluída gratuitamente.                                               |
| eficazDate    | string           | A data em que este contador está em vigor.                                                             |

## <a name="azureofferterm"></a>AzureOfferTerm

| Propriedade         | Tipo             | Descrição                             |
|------------------|------------------|-----------------------------------------|
| name             | string           | Nome amigável do termo de oferta.        |
| desconto         | número           | O desconto aplicado, se houver.           |
| Meteridas excluídas | matriz de cadeias (de carateres) | Medidores excluídos da oferta, se houver. |
| eficazDate    | string           | A data da oferta está em vigor.        |
