---
title: Recursos de licença
description: Descreve recursos relacionados com licenças.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e6d91110dcec8a873e77cb02bdb77f6335e27989201ea68eebf904c5159964c5
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996585"
---
# <a name="license-resources"></a>Recursos de licença

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Descreve recursos relacionados com licenças.

## <a name="license"></a>Licença

Descreve uma licença de utilizador.

>[!NOTE]
>Sem apoio no Partner Center operado pela 21Vianet.

| Propriedade     | Tipo                                                           | Description                                                    |
|--------------|----------------------------------------------------------------|----------------------------------------------------------------|
| planos de serviço | matriz de recursos Do Plano de Serviço                                 | A recolha de planos de serviço que correspondem à licença |
| produtoSKU   | ProductSku                                                     | O sku do produto que corresponde à licença.        |
| atributos   | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados atribuem correspondentes à licença.          |

## <a name="licenseupdate"></a>LicenseUpdate

Fornece informações usadas para atribuir ou remover licenças de um utilizador.

| Propriedade         | Tipo                                                           | Description                                               |
|------------------|----------------------------------------------------------------|-----------------------------------------------------------|
| licensestoAssign | matriz de objetos                                               | Conjunto de [objetos de assinatura de licença.](#licenseassignment) |
| licençasToRemove | matriz de cadeias (de carateres)                                               | O produto identificadores SKU das licenças para remover.    |
| licençasAaviões  | matriz de objetos                                               | Conjunto de objetos de [aviso de licença.](#licensewarning)       |
| atributos       | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                  |

## <a name="licenseassignment"></a>Assinatura de Licença

Fornece informações necessárias para uma operação de atualização de licença.

| Propriedade      | Tipo             | Description                                                                |
|---------------|------------------|----------------------------------------------------------------------------|
| Planos excluídos | matriz de cadeias (de carateres) | Os identificadores do plano de serviço devem ser excluídos da disponibilidade para o utilizador. |
| skuId         | string           | O identificador SKU do produto para a licença.                                |

## <a name="licensewarning"></a>Licença De Aviso

Contém informações de aviso que ocorreram durante uma operação de atualização da licença.

| Propriedade     | Tipo             | Description                                         |
|--------------|------------------|-----------------------------------------------------|
| code         | string           | O código de aviso.                                   |
| message      | string           | A mensagem de aviso.                                |
| planos de serviço | matriz de cadeias (de carateres) | Os nomes do plano de serviço associados ao aviso. |

## <a name="productsku"></a>ProductSku

Descreve detalhes do produto.

| Propriedade       | Tipo             | Descrição                                         |
|----------------|------------------|-----------------------------------------------------|
| ID             | string           | O identificador de produto.                             |
| name           | string           | O identificador principal do utilizador.                      |
| skuPartNumber  | string           | O nome de número de peça SKU para o produto. Por exemplo, para Office 365 Plano E3, este valor é `EnterprisePack` . Esta propriedade pode ser usada no lugar de ID se o ID não estiver disponível.                |
| targetType     | string           | O tipo alvo do produto. Esta propriedade identifica se o produto é aplicável a um `User` ou um `Tenant` .                                                                    |
| licenseGroupId | string           | Identifica através de um identificador de grupo a autoridade ou serviço que gere a licença de produtoSku. Os produtos são segregados em grupos de licenças para uma melhor gestão.<br/><br/>                                                                                     `group1`- Todos os produtos cujas licenças podem ser geridas por Azure Ative Directory (AAD).<br/><br/>                                            `group2`- Minecraft licenças de produtos.                                         |

## <a name="serviceplan"></a>Plano de Serviços

Identifica um serviço implantável dentro de um produto SKU. Um produto pode ter muitos planos de serviço.

| Propriedade         | Tipo   | Descrição                                                                                                       |
|------------------|--------|-------------------------------------------------------------------------------------------------------------------|
| ID               | string | O identificador do plano de serviço.                                                                                      |
| displayName      | string | O nome de exibição localizado para o plano de serviço.                                                                  |
| nome de serviço      | string | O nome de serviço.                                                                                                 |
| capacidadeSestatus | string | O estado do plano de serviço do plano de serviço.                                                                      |
| targetType       | string | O tipo alvo do plano de serviço. Este imóvel identifica se o produto é aplicável a um "Utilizador" ou a um "Inquilino". |

## <a name="subscribedsku"></a>SubscritoSku

Descreve um produto subscrito propriedade de um inquilino.

| Propriedade         | Tipo                                                           | Description                                                                                       |
|------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| unidades disponíveis   | número inteiro                                                        | O número de unidades disponíveis para atribuição. Este valor é calculado como unidades totais - unidades consumidas. |
| unidades ativas      | número inteiro                                                        | O número de unidades ativas para a atribuição.                                                        |
| consumidoSUnits    | número inteiro                                                        | O número de unidades consumidas.                                                                     |
| unidades suspensas   | número inteiro                                                        | O número de unidades suspensas.                                                                    |
| totalUnits       | número inteiro                                                        | O número total de unidades. Este valor é calculado como a soma das unidades ativas e de aviso.         |
| advertênciaS     | número inteiro                                                        | O número de unidades de aviso.                                                                      |
| produtoSku       | ProductSku                                                     | O sku do produto.                                                                                  |
| planos de serviço     | matriz de recursos Do Plano de Serviço                                 | A recolha de planos de serviço de um produto.                                                     |
| capacidadeSestatus | string                                                         | O estado de sku de um produto.                                                                      |
| atributos       | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados atribuem correspondentes ao recurso.                                            |
