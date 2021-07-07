---
title: Recursos de registo de utilização de recursos
description: Pode utilizar o recurso ResourceUsageRecord para descrever o custo monetário estimado da utilização do nível de recursos de uma subscrição no ciclo de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: eb626b9d4cb4c57a07f45bcf7b914f534e62ab68
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446586"
---
# <a name="resource-usage-record-resources"></a>Recursos de registo de utilização de recursos

Pode utilizar o recurso **ResourceUsageRecord** para descrever o custo monetário estimado da utilização do nível de recursos de uma subscrição no ciclo de faturação atual.

## <a name="resourceusagerecord"></a>ResourceUsageRecord

| Propriedade          | Tipo               | Description                                                                                                                                                                                                |
|-------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SubscriptionId    | string             | Recebe ou define o identificador de assinatura. Para Microsoft Azure (MS-AZR-0145P), este valor é o identificador de subscrição de comércio. Para os planos Azure, este valor é o identificador do plano Azure). |
| RecursosUri       | string             | Recebe ou define o recurso URI."                                                                                                                                                                            |
| ResourceType      | string             | Recebe ou define o tipo de recurso.                                                                                                                                                                            |
| Direitodid     | string             | Obtém ou define o identificador de direito (o identificador de assinatura Azure).                                                                                                                               |
| Nome de Direito   | string             | Recebe ou define o nome do direito.                                                                                                                                                                         |
| ResourceGroupName | double             | Obtém ou define o nome do grupo de recursos.                                                                                                                                                                      |
| Name              | string             | O nome do recurso.                                                                                                                                                                                  |
| ResourceName      | string             | Recebe ou define o nome do recurso.                                                                                                                                                                     |
| TotalCost         | decimal            | Obtém ou define o uso total estimado do custo.                                                                                                                                                               |
| CurrencyCode      | string             | Recebe ou define o código de moeda.                                                                                                                                                                            |
| USDTotalCost      | decimal            | Obtém ou define o custo total estimado em USD.                                                                                                                                                              |
| LastModifiedDate (Carga incremental: LastModifiedDate)  | string             | O dia (em formato de data) que este disco foi modificado pela última vez.                                                                                                                                          |
| Atributos        | RecursosTributos | Os metadados atribuem correspondentes ao recurso.                                                                                                                                                     |
