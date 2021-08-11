---
title: Recursos de requisitos de segurança de parceiros
description: Compreenda detalhes de autenticação de vários fatores (MFA) para satisfazer os Requisitos de Segurança dos Parceiros.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
ms.openlocfilehash: 6377dbde574edd1b8d8058f7b8e88ae6497d615b9237bbda91e9c4617486b569
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997894"
---
# <a name="partner-security-requirements-resources"></a>Recursos de requisitos de segurança dos parceiros

Este artigo ajuda-o a compreender detalhes de adoção de autenticação de vários fatores (MFA), para ajudar a sua organização a cumprir o estatuto de requisito de segurança do parceiro. 

## <a name="portal-request-without-mfa"></a>Pedido de portal sem MFA

Indicar um utilizador que acede ao portal Partner Center sem autenticação MFA.

| Propriedade                            | Tipo            | Descrição                           |
|-------------------------------------|-----------------|---------------------------------------|
| ObjectId                            | string          | ID de objeto de utilizador                        |
| TenantId                            | string          | ID do inquilino do CSP                         |
| Upn                                 | string          | Nome principal do utilizador                   |
| LastNonMfaCompliantLoginDateTime    | datetime        | Login de utilizadores de última hora sem MFA |


## <a name="api-request-summarized-by-application"></a>Pedido de API resumido por Aplicação

Um resumo do pedido de API feito pela APP + Credencial do utilizador, agregado por data de pedido e ID de aplicação.

| Propriedade                            | Tipo            | Description               |
|-------------------------------------|-----------------|---------------------------|
| LoginDate                           | datetime        | Data de pedido da API          |
| MfaCompliantRequestCount            | long            | Contagem de pedidos com MFA    |
| TotalRequestCount                   | long            | Contagem total de pedidos       |
| ApplicationID                       | string          | O ID da aplicação        |
| ApplicationName                     | string          | O nome da candidatura      |


## <a name="api-request-details"></a>Detalhes do pedido da API

Pedido de API feito pela APP + Credencial do Utilizador. 

| Propriedade                            | Tipo            | Description                              |
|-------------------------------------|-----------------|------------------------------------------|
| RequestId                           | string          | MS-RequestId                             |
| CorrelationId                       | string          | MS-CorrelationId                         |
| OperationName                       | string          | O caminho da API com método de pedido         |
| Hora do Pedido                     | DateTime        | O tempo de pedido da API                     |
| IpAddress                           | string          | Endereço IP de origem                        |
| ObjectId                            | string          | ID do objeto do utilizador                           |
| TenantId                            | string          | ID do inquilino do CSP                            |
| Upn                                 | string          | Nome principal do utilizador                      |
| ApplicationID                       | string          | A sua candidatura                         |
| MfaCompliant                        | bool            | Indicar o pedido com ou sem MFA |
