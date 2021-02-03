---
title: Recursos de utilizador
description: Descreve um utilizador individual do Partner Center, as suas informações pessoais e de conta e as permissões que têm dentro do Partner Center.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0c88b9b65dfb925712ff85fb42d34251cca6e0b5
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768708"
---
# <a name="user-resources"></a>Recursos de utilizador

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Descreve um utilizador individual do Partner Center, as suas informações pessoais e de conta e as permissões que têm dentro do Partner Center.

## <a name="user"></a>User

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
| últimadutóriaSyncTime | cadeia no formato de hora de data UTC                                 | A última vez que essa informação para este utilizador foi sincronizada entre o Azure Ative Directory e o Ative Directory no local. Um valor de hora de data só aparece se a sincronização do Azure AD Connect estiver ativada. Caso contrário, o valor é nulo. |
| userDomainType        | string                                                         | O tipo de domínio do utilizador: "nenhum", "gerido", ou "federado".                                                                                                                                                                   |
| state                 | string                                                         | O estado do utilizador: "ativo", "inativo" (para um utilizador eliminado).                                                                                                                                                          |
| softDeletionTime      | cadeia no formato de hora de data UTC                                 | Representa o início do período de trinta dias após o qual os dados associados a um utilizador eliminado são permanentemente eliminados e, portanto, irrecuperáveis.                                                                          |
| ligações                 | [RecursosLinks](utility-resources.md#resourcelinks)           | Os recursos ligam-se.                                                                                                                                                                                                        |
| atributos            | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                                                                                                                                                                                   |

## <a name="customeruser"></a>CustomerUser

Descreve um utilizador do cliente.

| Propriedade              | Tipo                                                           | Descrição                                                                                                                                                                                                                |
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
| últimadutóriaSyncTime | cadeia no formato de hora de data UTC                                 | A última vez que essa informação para este utilizador foi sincronizada entre o Azure Ative Directory e o Ative Directory no local. Um valor de hora de data só aparece se a sincronização do Azure AD Connect estiver ativada. Caso contrário, o valor é nulo. |
| userDomainType        | string                                                         | O tipo de domínio do utilizador: "nenhum", "gerido", ou "federado".                                                                                                                                                                   |
| state                 | string                                                         | O estado do utilizador: "ativo", "inativo" (para um utilizador eliminado).                                                                                                                                                          |
| softDeletionTime      | cadeia no formato de hora de data UTC                                 | Representa o início do período de trinta dias após o qual os dados associados a um utilizador eliminado são permanentemente eliminados e, portanto, irrecuperáveis.                                                                          |
| ligações                 | [RecursosLinks](utility-resources.md#resourcelinks)           | Os recursos ligam-se.                                                                                                                                                                                                        |
| atributos            | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                                                                                                                                                                                   |

## <a name="usercredentials"></a>UserCredentials

Descreve as credenciais de login de um utilizador.

| Propriedade | Tipo                                               | Descrição                          |
|----------|----------------------------------------------------|--------------------------------------|
| userName | string                                             | O nome do utilizador.                |
| palavra-passe | [SecureString](utility-resources.md#securestring) | A senha do utilizador é armazenada de forma segura. |

## <a name="usermember"></a>UserMember

Descreve as informações dos membros de um utilizador.

| Propriedade          | Tipo                                                           | Descrição                        |
|-------------------|----------------------------------------------------------------|------------------------------------|
| displayName       | string                                                         | O nome apresentado para o utilizador.   |
| userPrincipalName | string                                                         | O nome do diretor do utilizador.    |
| roleId            | string                                                         | O identificador do papel do utilizador. |
| ID                | string                                                         | O identificador do membro.      |
| atributos        | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.           |

