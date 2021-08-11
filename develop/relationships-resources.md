---
title: Recursos de relacionamento
description: Descreve recursos relacionados com relacionamentos.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bbbc973679ae80c3ad6b9d67945c6fbcb087789484939b67f8d8a6b538ce7d37
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997095"
---
# <a name="relationships-resources"></a>Recursos de relacionamento

Descreve recursos relacionados com relacionamentos.

## <a name="partnerrelationship"></a>ParceriaRelação

Representa uma relação entre dois parceiros.

| Propriedade         | Tipo                                                           | Descrição                                                                                                                                    |
|------------------|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| ID               | string                                                         | O identificador do parceiro. O identificador do parceiro especifica o id do inquilino do parceiro que está no lado destinatário (a partir) da relação. |
| localização         | cadeia (de carateres)                                                         | A localização do parceiro.                                                                                                                   |
| mpnId            | string                                                         | O identificador da Microsoft Partner Network (MPN) do parceiro.                                                                                 |
| name             | string                                                         | O nome do parceiro.                                                                                                                       |
| relaçãoType | string                                                         | O tipo de relacionamento.                                                                                                                      |
| state            | string                                                         | O estado da relação (por `active` exemplo).                                                                                                 |
| atributos       | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                                                                                                       |

## <a name="relationshiprequest"></a>RelacionamentoRequest

Fornece o URL através do qual um cliente pode estabelecer uma relação com um parceiro.

| Propriedade   | Tipo                                                           | Description                   |
|------------|----------------------------------------------------------------|-------------------------------|
| url        | string                                                         | A URL de pedido de relacionamento. |
| atributos | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.      |
