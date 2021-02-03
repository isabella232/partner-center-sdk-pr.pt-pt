---
title: Recursos de direito
description: Descreve recursos relacionados com o direito.
ms.date: 01/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 428ac6f8b4d67894092119a6246279045a04dac0
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769301"
---
# <a name="entitlement-resources"></a>Recursos de direito

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

## <a name="entitlement"></a>Elegibilidade

Este recurso representa os produtos a que o cliente tem o direito de utilizar devido à compra de parceiros em itens do catálogo.

| Propriedade | Tipo | Descrição |
|----------|------|-------------|
| referenciador | [Pedido de Referência](#referenceorder) | A referência da ordem que resultou no direito. |
| productId | string | ID do produto. |
| skuID | string | A identificação do SKU. |
| quantidade | int | A quantidade de direitos (exclui direitos não preenchidos/transferidos). |
| quantidadeDetails | IEnumerable<[QuantityDetail](#quantitydetail)> | A lista dos dados da quantidade de direitos (número de itens e estado de cada quantidade). |
| DireitoTipo | string | O tipo de direito. (Atualizado para cadeia a partir de [EntitlementType](#entitlementtype) em SDK 1.8.) |
| intituladoArfacts | [Artefacto](#artifact)<IEnumerable> | A lista de artefactos associados ao direito. |
| Incluindo Sentimentos | [Direito](#artifact)<IEnumerable> | A lista de direitos, que são implicitamente incluídos como resultado da compra do ProductId /SkuId do catálogo. |
| ExpiraçãoDate | cadeia no formato de data-hora UTC  | A data de validade do direito (se aplicável). |

## <a name="referenceorder"></a>Pedido de Referência

A referência da ordem de um direito.

| Propriedade | Tipo | Descrição |
|----------|------|-------------|
| ID | string | A identificação da ordem referenciada. |
| lineItemId | string | A identificação do item da linha de encomenda referenciada. |
| alternateId | string | A identificação alternativa do item da linha de encomenda referenciada. |

## <a name="quantitydetail"></a>QuantidadeDetail

Representa os detalhes de uma quantidade de direito.

| Propriedade | Tipo | Descrição |
|----------|------|-------------|
| quantidade | int | O número de itens. |
| status | string | O estado da quantidade. |

## <a name="entitlementtype"></a>DireitoType

> [!IMPORTANT]
> Prectado em SDK v1.9

Um [Enum](/dotnet/api/system.enum) com valores que indicam o tipo de direito.

| Valor | Descrição |
|-------|-------------|
| Software | Indica o tipo de direito relacionado com o software. |
| VirtualMachineReservedInstance | Indica o tipo de direito relacionado com Azure Reserved Virtual Machine Instances. |

## <a name="artifact"></a>Artefacto

O artefacto associado ao direito.

| Propriedade | Tipo | Descrição |
|----------|------|-------------|
| artefactoType | string | O tipo de artefacto. (Atualizado para cadeia a partir de [ArtifactType](#artifacttype) em SDK V1.8) |
| dynamicAttributes | Cadeia de &lt; dicionário, objeto&gt; | Atributos dinâmicos que contêm valores específicos de artefactos. Por exemplo, quando artefactosType = "alienação", esta propriedade conterá "reservationType" = "virtualmachines" ou "reservationType" = "sqldatabases" denotando a caixa reservada da máquina virtual ou a instância reservada do Azure SQL. (Disponível a partir de SDK v1.9) |

## <a name="artifacttype"></a>ArtefactoType

> [!IMPORTANT]
> Prectado em SDK v1.9

Um [Enum](/dotnet/api/system.enum) com valores que indicam o tipo de artefacto de direito.

| Valor                          | Descrição                                                                             |
|--------------------------------| ----------------------------------------------------------------------------------------|
| VirtualMachineReservedInstance | Indica que o artefacto ajuda com a recuperação de Azure Reserved Virtual Machine Instances. |

## <a name="reservedinstanceartifact"></a>AlieninstanceArtifact

O artefacto associado a um direito de Instância Reservada Azure. Herda da classe [Artefacto.](#artifact)

| Propriedade   | Tipo                           | Descrição                                        |
|------------|--------------------------------|----------------------------------------------------|
| associar       | [Ligação](./utility-resources.md#link) | A ligação para obter todos os detalhes de artefactos associados.   |
| recursoID | string                         | A identificação da ordem ou recurso de reserva Azure. |

## <a name="reservedinstanceartifactdetails"></a>ReservaInstanceArtifactDetails

Representa a entidade devolvida após a invocação do elo de artefacto Azure Reserved Instance.

|   Propriedade   |           Tipo           |                          Descrição                          |
|--------------|--------------------------|---------------------------------------------------------------|
|     tipo     |          string          |                     O tipo de artefacto.                     |
| reservas | IEnumerable<Reservation> | Indica o identificador de recurso Azure ou de pedido de reserva. |

## <a name="reservation"></a>Reserva

Representa uma reserva individual.

| Propriedade          | Tipo                           | Descrição                                                        |
|-------------------|--------------------------------|--------------------------------------------------------------------|
| reservationId     | string                         | A identificação da reserva.                                         |
| telescópioType         | string                         | O tipo de âmbito associado à reserva de máquina virtual. |
| displayName       | string                         | O nome de exibição da reserva.                               |
| appliedScopes     | IEnumerable                    | A lista de âmbitos aplicados associados à reserva. (Disponível apenas quando o âmbitoType não é partilhado.) |
| quantidade          | int                            | O número de máquinas virtuais na reserva.                 |
| expiraçãoDateTime    | cadeia no formato de data-hora UTC | A data de validade da reserva.                                |
| efetivaMenteDa hora | cadeia no formato de data-hora UTC | A data efetiva da reserva.                             |
| ProvisioningState | string                         | O estado de provisionamento da reserva.                         |

## <a name="virtualmachinereservedinstanceartifact"></a>VirtualMachineReservedInstanceArtifact

> [!IMPORTANT]
> Prectado em SDK v1.9

O artefacto associado a um direito de instância virtual reservada do Azure. Herda da classe [Artefacto.](#artifact)

| Propriedade   | Tipo                              | Descrição                                        |
|------------|-----------------------------------|----------------------------------------------------|
| associar       | [Ligação](utility-resources.md#link) | A ligação para obter todos os detalhes de artefactos associados.   |
| recursoID | string                            | A identificação da ordem ou recurso de reserva Azure. |

## <a name="virtualmachinereservedinstanceartifactdetails"></a>VirtualMachineReservedInstanceArtifactDetails

> [!IMPORTANT]
> Prectado em SDK v1.9

Representa a entidade devolvida após a invocação do link de artefactos Azure Reserved Virtual Machine Instance.

| Propriedade                    | Tipo                                                                 | Descrição           |
|-----------------------------|----------------------------------------------------------------------|-----------------------|
| tipo                        | [ArtefactoType](#artifacttype)                                        | O tipo de artefacto. |
| virtualMachineReservações  | IEnumerable<[VirtualMachineReservation](#virtualmachinereservation)> | Indica o identificador de recurso Azure ou de pedido de reserva. |

## <a name="virtualmachinereservation"></a>Conservação virtual

> [!IMPORTANT]
> Prectado em SDK v1.9

Representa uma reserva individual de máquina virtual.

|     Propriedade      |              Tipo              |                                                Descrição                                                 |
|-------------------|--------------------------------|------------------------------------------------------------------------------------------------------------|
|   reservationId   |             string             |                                         A identificação da reserva.                                         |
|     telescópioType     |             string             |                     O tipo de âmbito associado à reserva de máquina virtual.                     |
|    displayName    |             string             |                                    O nome de exibição da reserva.                                    |
|   appliedScopes   |      IEnumerable<string>       | A lista de âmbitos aplicados associados à reserva. (Disponível apenas quando o âmbitoType não é partilhado.) |
|     quantidade      |              int               |                             O número de máquinas virtuais na reserva.                             |
|  expiraçãoDateTime   | cadeia no formato de data-hora UTC |                                    A data de validade da reserva.                                     |
| efetivaMenteDa hora | cadeia no formato de data-hora UTC |                                   A data efetiva da reserva.                                   |
| ProvisioningState |             string             |                                 O estado de provisionamento da reserva.                                 |
