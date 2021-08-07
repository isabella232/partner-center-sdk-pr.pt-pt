---
title: Recursos de utilizador
description: Descreve um utilizador individual do Partner Center, as suas informações pessoais e de conta e as permissões que têm dentro do Partner Center.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8c91e3509d86c8817da30c8ad0d96a2b1b6eec7697e43b47d3dfb96055cac632
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989224"
---
# <a name="user-resources"></a>Recursos de utilizador

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Descreve um utilizador individual do Partner Center, as suas informações pessoais e de conta e as permissões que têm dentro do Partner Center.

## <a name="user"></a>Utilizador

Descreve um utilizador individual.

| Propriedade              | Tipo                                                           | Descrição                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID                    | string                                                         | O identificador de utilizador.                                                                                                                                                                                                       |
| userPrincipalName     | string                                                         | O identificador principal do utilizador.                                                                                                                                                                                             |
| nomePróprio             | string                                                         | O primeiro nome do utilizador.                                                                                                                                                                                                |
| apelido              | string                                                         | O último nome do utilizador.                                                                                                                                                                                                 |
| displayName           | string                                                         | O nome apresentado do utilizador.                                                                                                                                                                                            |
| passwordProfile       | [PasswordProfile](utility-resources.md#passwordprofile)       | O perfil de senha do utilizador.                                                                                                                                                                                               |
| número de telefone           | string                                                         | O número de telefone do utilizador.                                                                                                                                                                                                   |
| últimadutóriaSyncTime | cadeia no formato de hora de data UTC                                 | A última vez que essa informação para este utilizador foi sincronizada entre Azure Ative Directory e no local Ative Directory. Um valor de hora de data só aparece se a Azure AD Ligação sincronização estiver ativada. Caso contrário, o valor é nulo. |
| userDomainType        | string                                                         | O tipo de domínio do utilizador: "nenhum", "gerido", ou "federado".                                                                                                                                                                   |
| state                 | string                                                         | O estado do utilizador: "ativo", "inativo" (para um utilizador eliminado).                                                                                                                                                          |
| softDeletionTime      | cadeia no formato de hora de data UTC                                 | Representa o início do período de 30 dias após o qual os dados associados a um utilizador eliminado são permanentemente eliminados e, portanto, irrecuperáveis.                                                                          |
| ligações                 | [RecursosLinks](utility-resources.md#resourcelinks)           | Os recursos ligam-se.                                                                                                                                                                                                        |
| atributos            | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                                                                                                                                                                                   |

## <a name="customeruser"></a>CustomerUser

Descreve um utilizador do cliente.

| Propriedade              | Tipo                                                           | Description                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| usageLocation         | string                                                         | O local onde o utilizador pretende utilizar a licença.                                                                                                                                                                    |
| ID                    | string                                                         | O identificador de utilizador.                                                                                                                                                                                                       |
| userPrincipalName     | string                                                         | O identificador principal do utilizador.                                                                                                                                                                                             |
| nomePróprio             | string                                                         | O primeiro nome do utilizador.                                                                                                                                                                                                |
| apelido              | string                                                         | O último nome do utilizador.                                                                                                                                                                                                 |
| displayName           | string                                                         | O nome apresentado do utilizador.                                                                                                                                                                                            |
| imutávelId           | string                                                         | A identificação imutável do utilizador.                                                                                                                                                                                              |
| passwordProfile       | [PasswordProfile](utility-resources.md#passwordprofile)       | O perfil de senha do utilizador.                                                                                                                                                                                               |
| número de telefone           | string                                                         | O número de telefone do utilizador.                                                                                                                                                                                                   |
| últimadutóriaSyncTime | cadeia no formato de hora de data UTC                                 | A última vez que essa informação para este utilizador foi sincronizada entre Azure Ative Directory e no local Ative Directory. Um valor de hora de data só aparece se a Azure AD Ligação sincronização estiver ativada. Caso contrário, o valor é nulo. |
| userDomainType        | string                                                         | O tipo de domínio do utilizador: "nenhum", "gerido", ou "federado".                                                                                                                                                                   |
| state                 | string                                                         | O estado do utilizador: "ativo", "inativo" (para um utilizador eliminado).                                                                                                                                                          |
| softDeletionTime      | cadeia no formato de hora de data UTC                                 | Representa o início do período de 30 dias após o qual os dados associados a um utilizador eliminado são permanentemente eliminados e, portanto, irrecuperáveis.                                                                          |
| ligações                 | [RecursosLinks](utility-resources.md#resourcelinks)           | Os recursos ligam-se.                                                                                                                                                                                                        |
| atributos            | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                                                                                                                                                                                   |

## <a name="usercredentials"></a>UserCredentials

Descreve as credenciais de inscrição de um utilizador.

| Propriedade | Tipo                                               | Description                          |
|----------|----------------------------------------------------|--------------------------------------|
| userName | string                                             | O nome do utilizador.                |
| palavra-passe | [SecureString](utility-resources.md#securestring) | A senha do utilizador é armazenada de forma segura. |

## <a name="usermember"></a>UserMember

Descreve as informações dos membros de um utilizador.

| Propriedade          | Tipo                                                           | Description                        |
|-------------------|----------------------------------------------------------------|------------------------------------|
| displayName       | string                                                         | O nome apresentado para o utilizador.   |
| userPrincipalName | string                                                         | O nome do diretor do utilizador.    |
| roleId            | string                                                         | O identificador do papel do utilizador. |
| ID                | string                                                         | O identificador do membro.      |
| atributos        | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.           |

