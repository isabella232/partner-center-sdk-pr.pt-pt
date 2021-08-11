---
title: Recursos de política de autosserviço
description: Um parceiro define políticas de autosserviço para um cliente.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ffca78481572e201d3ef9f488e7d594a9c1176249b4415a347b488f4b9b81c51
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996772"
---
# <a name="selfservepolicy-resource"></a>Recurso SelfServePolicy

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

| Propriedade             | Tipo|Description|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| SelfServeEntityType  | string                           | A entidade a quem foi concedido acesso, valores aceites: Cliente.                                 |
| TenantID             | string                           | O identificador de inquilino da entidade que tem acesso.                                   |

## <a name="grantor"></a>Grantor

Representa o concededor que concede as permissões.

| Propriedade             | Tipo|Description|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| GrantorType          | string                           | O bolseiro que concede acesso, valores aceites: BillToPartner.                               |
| TenantID             | string                           | O identificador de inquilino da entidade que concede acesso.                                       |


## <a name="permission"></a>Permissão

Representa uma permissão na política de autosserviço.

| Propriedade             | Tipo|Description|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| Recurso             | string                           | O acesso ao recurso também está a ser concedido: AzureReservedInstances.                          |
| Ação               | string                           | O acesso à ação está a ser concedido para: Compra                                           |
