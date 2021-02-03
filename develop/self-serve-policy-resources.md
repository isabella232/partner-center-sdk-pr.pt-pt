---
title: Recursos de política de autosserviço
description: Um parceiro define políticas de autosserviço para um cliente.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 04daf6aaeb69153c4139941188f53dbab8979969
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768953"
---
# <a name="selfservepolicy-resource"></a>Recurso SelfServePolicy

**Aplica-se a:**

- Partner Center

Um parceiro define políticas de autosserviço para um cliente.

## <a name="selfservepolicy"></a>AutoServePolicy

Descreve um carrinho.

| Propriedade              | Tipo             | Descrição                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| ID                    | string           | Um identificador de política de autosserviço que é fornecido após a criação bem sucedida da política de autosserviço.     |
| SelfServeEntity       | SelfServeEntity  | A entidade self-serve a quem está a ser concedido acesso.                                                     |
| Grantor               | Grantor          | O concededor que está a conceder acesso.                                                                    |
| Permissões           | Matriz de Permissão| Um conjunto de recursos [de permissão.](#permission)                                                                     |

## <a name="selfserveentity"></a>SelfServeEntity

Representa a entidade que recebe permissões.

| Propriedade             | Tipo|Descrição|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| SelfServeEntityType  | string                           | A entidade a quem foi concedido acesso, valores aceites: Cliente.                                 |
| TenantID             | string                           | O identificador de inquilino da entidade que tem acesso.                                   |

## <a name="grantor"></a>Grantor

Representa o concededor que concede as permissões.

| Propriedade             | Tipo|Descrição|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| GrantorType          | string                           | O bolseiro que concede acesso, valores aceites: BillToPartner.                               |
| TenantID             | string                           | O identificador de inquilino da entidade que concede acesso.                                       |


## <a name="permission"></a>Permissão

Representa uma permissão na política de autosserviço.

| Propriedade             | Tipo|Descrição|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| Recurso             | string                           | O acesso ao recurso também está a ser concedido: AzureReservedInstances.                          |
| Ação               | string                           | O acesso à ação está a ser concedido para: Compra                                           |
