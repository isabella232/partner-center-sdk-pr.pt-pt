---
title: Oferecer recursos
description: Descreve um produto listado no catálogo de revendedores que podem oferecer aos seus clientes.
ms.date: 03/15/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bcc5b60b7d1e3e13c38bd4014a81c2af254daa1d01ef33351b680463c3fee4a6
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997911"
---
# <a name="offer-resources"></a>Oferecer recursos

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Descreve um produto listado no catálogo de revendedores que podem oferecer aos seus clientes.

## <a name="offer"></a>Oferta

| Propriedade                    | Tipo                      | Descrição                                                                                                                                                                |
|-----------------------------|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID                          | string                    | O identificador da oferta.                                                                                           |
| name                        | string                    | O nome da oferta.                                                                                                 |
| descrição                 | string                    | Uma descrição da oferta.                                                                                     |
| mínimoQuantidade             | int                       | A quantidade mínima disponível.                                                                                 |
| máximaQuantidade             | int                       | A quantidade máxima disponível.                                                                                 |
| ordem                        | int                       | O ranking de oferta ou prioridade em comparação com outras categorias na mesma linha de produtos. Esta propriedade só deve ser definida se houver mais do que uma oferta para uma determinada linha de produtos.  |
| uri                         | string                    | A oferta URI.                                                                                                  |
| região                      | string                    | O local em que a oferta se aplica.                                                                          |
| país                     | string                    | O país/região onde a oferta se aplica.                                                                    |
| categoria                    | [OfertaCategoria](#offercategory)           | A categoria da oferta.                                                                   |
| limiteUOfMeasure          | string                    | Um valor que indica o tipo de limitação de compra. Valores possíveis incluem:<br/> "Nenhuma" - Não existem restrições ao número de subscrições com base na oferta adquirida.<br/> "Simultâneo" - O número de subscrições que podem existir no cliente inquilino num dado momento, isto inclui subscrições que estão ativas ou canceladas. Este valor aplica-se principalmente às ofertas de pequenas empresas onde as contagens de licença são inferiores a 300. As assinaturas desreserionadas não contam.<br/> "LifeTime" - O número de subscrições que podem existir para o resto da vida do cliente inquilino. Este valor é mais aplicável aos Ensaios. As assinaturas desreserionadas não contam.      |
| limit                       | int                       | O número de subscrições que podem ser adquiridas desta oferta com base no limite Deseuro.                |
| pré-requisitosOffers          | string                    | As ofertas pré-requisitos.                                                                                        |
| isAddOn                     | boolean                   | Um valor que indica se este caso é um adutivo.                                                           |
| hasAddOns                   | boolean                   | Um valor que indique se esta oferta tem algum adôntões.                                                           |
| está Disponível Para a Compra      | boolean                   | Um valor que indique se este caso está disponível para compra.                                             |
| billing                     | string                    | Especifica o tipo de faturação para a compra de artigo de linha: "nenhum", "uso" ou "licença".                           |
| suportadosBillingCycles      | matriz de cadeias (de carateres)          | Indica os ciclos de faturação suportados para esta oferta. Valores suportados são os nomes dos membros encontrados no [BillingCycleType](product-resources.md#billingcycletype)   |
| isAutoRenewable             | boolean                   | Um valor que indica se a oferta renova automaticamente.                                                      |
| upgradeTargetOffers         | matriz de cadeias (de carateres)          | A lista de ofertas para as seguintes.                                                          |
| conversãoTargetOffers      | matriz de cadeias (de carateres)          | A lista de ofertas para as que esta oferta pode ser convertida.                                                         |
| reselleeQualificações      | matriz de cadeias (de carateres)          | As qualificações exigidas pelo cliente para que um parceiro adquiram a oferta para esse cliente.     |
| revendorQualificações      | matriz de cadeias (de carateres)          | As qualificações exigidas pelo parceiro para adquirir a oferta para um cliente.                       |
| salesGroupId                | string                    | Uma corda usada para agrupar ofertas em ordens separadas.                                                             |
| isTrial                     | boolean                   | Um valor que indica se esta é uma oferta de julgamento.                                                               |
| produto                     | [Produto de oferta](#offerproduct)           | Recebe o produto de oferta.                                                                           |
| unitType                    | string                    | O tipo da unidade.                                                                                      |
| ligações                       | [OfferLinks](#offerlinks)               | A ligação "saiba mais".                                                                    |
| atributos                  | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados atribuem correspondentes à oferta.                         |
| AttestationProperties       | [AttestationProperties](#attestationproperties) | As propriedades do atestado para um SKU.                   |

## <a name="offercategory"></a>OfertaCategoria

Descreve a categorização de uma oferta. Isto inclui o grau ou prioridade desta categoria de oferta em comparação com outros da mesma linha de produtos.

| Propriedade   | Tipo                                                           | Descrição                                                                                                                                                                |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID         | string                                                         | O identificador de categoria.                                                                                                                                                   |
| name       | string                                                         | O nome da categoria.                                                                                                                                                         |
| ordem       | int                                                            | O grau de categoria ou prioridade em comparação com outras categorias na mesma oferta. Esta propriedade só deve ser definida se houver mais de uma categoria de oferta para uma oferta dada. |
| região     | string                                                         | O local em que a oferta se aplica.                                                                                                                        |
| país    | string                                                         | O país/região onde a oferta se aplica.                                                                                                                   |
| ligações      | [RecursosLinks](utility-resources.md#resourcelinks)           | As ligações de recursos correspondentes à Lista de Estrangeiros.                                                                                                                     |
| atributos | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos de metadados correspondentes à Lista de Ofertas.                                                                                                                |

## <a name="offerlinks"></a>OfferLinks

Contém links para aprender mais informações sobre a oferta.

| Propriedade  | Tipo | Description                 |
|-----------|------|-----------------------------|
| aprender Mais | Ligação | A ligação "aprender mais".      |
| self      | Ligação | O auto-URI                |
| seguinte      | Ligação | A próxima página de artigos.     |
| anterior  | Ligação | A página anterior dos artigos. |

## <a name="offerproduct"></a>Produto de oferta

Um produto ou serviço que pode ter mais do que uma oferta associada a ele, cada um com diferentes conjuntos de funcionalidades e direcionados para diferentes necessidades do cliente.

| Propriedade | Tipo   | Description              |
|----------|--------|--------------------------|
| Id       | string | O identificador de categoria. |
| Name     | string | O nome da categoria.       |
| Unidade     | string | A unidade de produtos.        |

## <a name="attestationproperties"></a>AttestationProperties

Representa um tipo de atestado e se for necessário para compra.

| Propriedade              | Tipo                                        | Description                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| attestationType              | string                                      | Indica o tipo de atestado. Para Windows 365 o valor é o Windows365. Windows texto de atestado 365 é "Entendo que cada pessoa que usa Windows 365 Negócios com Windows Hybrid Benefit também precisa de ter uma cópia válida de Windows 10/11 Pro instalada no seu dispositivo de trabalho primário." |
| impor Attestation           | boolean                                      | Indica se o atestado é necessário para compra.           |

