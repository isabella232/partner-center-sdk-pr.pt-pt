---
title: Recursos de registo de utilização de recursos
description: Pode utilizar o recurso ResourceUsageRecord para descrever o custo monetário estimado da utilização do nível de recursos de uma subscrição no ciclo de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b330c49518bc12a63f2be731eef5c57884f5b15b706ce4007bbdf1a7bb8fab0e
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996942"
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
