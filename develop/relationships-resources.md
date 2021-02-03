---
title: Recursos de relacionamento
description: Descreve recursos relacionados com relacionamentos.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c5701414bd704b375dc23859b920609d5a975d9f
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768876"
---
# <a name="relationships-resources"></a>Recursos de relacionamento

**Aplica-se a**

- Partner Center

Descreve recursos relacionados com relacionamentos.

## <a name="partnerrelationship"></a>ParceriaRelação

Representa uma relação entre dois parceiros.

| Propriedade         | Tipo                                                           | Descrição                                                                                                                                    |
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

| Propriedade   | Tipo                                                           | Descrição                   |
|------------|----------------------------------------------------------------|-------------------------------|
| url        | string                                                         | A URL de pedido de relacionamento. |
| atributos | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.      |
