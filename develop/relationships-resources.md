---
title: Recursos de relacionamento
description: Descreve recursos relacionados com relacionamentos.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7dba1e99a6c97c759e3c61cde1e7565faa2ef4d1
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445736"
---
# <a name="relationships-resources"></a>Recursos de relacionamento

Descreve recursos relacionados com relacionamentos.

## <a name="partnerrelationship"></a>ParceriaRelação

Representa uma relação entre dois parceiros.

| Propriedade         | Tipo                                                           | Description                                                                                                                                    |
|------------------|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| ID               | string                                                         | O identificador do parceiro. O identificador do parceiro especifica o id do inquilino do parceiro que está no lado destinatário (a partir) da relação. |
| localização         | string                                                         | A localização do parceiro.                                                                                                                   |
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
