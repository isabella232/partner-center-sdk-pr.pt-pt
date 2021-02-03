---
title: Recursos do cliente
description: Recursos do cliente que representam um cliente ou revendedor.
ms.date: 11/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: fbd72ab5710876ba303fd1e30e6e552ecf89c5cd
ms.sourcegitcommit: 741cfa8585901de207c2e5da5eeebe26db0b0ad1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/18/2020
ms.locfileid: "97770046"
---
# <a name="customer-resources"></a>Recursos do cliente

**Aplica-se a:**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

## <a name="customer"></a>Customer

O recurso **Cliente** representa um cliente ou revendedor. Em geral, um recurso ao cliente pode ser qualquer pessoa, funcionário ou organização que deseje fazer negócios com a Microsoft e os revendedores da Microsoft. Os clientes também têm um perfil da empresa e um perfil de faturação.

>[!NOTE]
>O recurso **Cliente** tem um limite de taxa de 500 pedidos por minuto por identificador de inquilino.

| Propriedade              | Tipo                                                             | Descrição                                                                                                                                  |
|-----------------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| ID                    | string                                                           | A identificação do cliente.                                                                                                                             |
| commerceId            | string                                                           | A identificação do comércio.                                                                                                                             |
| empresaProfile        | [CustomerCompanyProfile](#customercompanyprofile)                | Informações adicionais sobre a empresa ou organização.                                                                                    |
| billingProfile        | [CustomerBillingProfile](#customerbillingprofile)                | Informação adicional usada para faturação.                                                                                                     |
| relationshipToPartner | string                                                           | Define o programa de licenciamento que o parceiro utiliza para este cliente: "nenhum", "revendedor", "conselheiro", "sindicalização" ou "suporte à \_ microsoft". |
| permitir DelegatedAccess  | boolean                                                          | Se o parceiro foi concedido privilégios de administração delegados por este cliente. Esta propriedade só está disponível quando se recebe um cliente por ID, não por lista.                                                         |
| userCredentis       | [UserCredentials](user-resources.md#usercredentials) | As credenciais de utilizador.                                                                                                                        |
| customDomains         | matriz de cadeias (de carateres)                                                 | Lista de domínios personalizados de um cliente.                                                                                                        |
| PartnerId associado   | string                                                           | O revendedor indireto associado a esta conta de cliente. Este valor só pode ser definido por parceiros CSP indiretos.                              |
| ligações                 | [RecursosLinks](utility-resources.md#resourcelinks)             | As ligações de recursos contidas no perfil.                                                                                             |
| atributos            | [RecursosTributos](utility-resources.md#resourceattributes)   | Os metadados correspondem ao perfil.                                                                                        |

## <a name="customercompanyprofile"></a>CustomerCompanyProfile

O **recurso CustomerCompanyProfile** é informação adicional sobre a empresa ou organização.

| Propriedade    | Tipo                                                           | Descrição                                                                       |
|-------------|----------------------------------------------------------------|-----------------------------------------------------------------------------------|
| inquilinoId    | string                                                         | O identificador de inquilino do cliente para a Azure AD. Isto também é chamado de MicrosoftID. |
| domínio      | string                                                         | O nome do cliente, como contoso.onmicrosoft.com.                             |
| nome da empresa | string                                                         | O nome da empresa ou organização.                                          |
| ligações       | [RecursosLinks](utility-resources.md#resourcelinks)           | As ligações de recursos contidas no perfil.                                  |
| atributos  | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados correspondem ao perfil.                             |

|organizaçãoRegistrationNumber| Corda| Número de registo da organização do cliente (também referido como número INN em determinados países). Apenas necessário para a empresa/organização do cliente localizada nos seguintes países. Arménia(AM), Azerbaijão(AZ), Bielorrússia (BY), Hungria (HU), Cazaquistão (KZ), Quirguistão(KG), Moldávia (MD), Rússia(RU), Tajiquistão(TJ), Uzhbequistão(UZ), Ucrânia (UA). Para a empresa/organização do cliente localizada noutros países, esta não deve ser especificada.|


## <a name="customerbillingprofile"></a>CustomerBillingProfile

O **recurso CustomerBillingProfile** é informação adicional utilizada para faturar o cliente.

| Propriedade       | Tipo                                                           | Descrição                                                                                                                                            |
|----------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID             | string                                                         | O identificador de perfil.                                                                                                                                |
| nomePróprio      | string                                                         | O primeiro nome do contacto de faturação na empresa do cliente. Esta é a pessoa a quem as faturas e outras comunicações de faturação serão direcionadas. |
| apelido       | string                                                         | O último nome do contacto de faturação.                                                                                                                  |
| e-mail          | string                                                         | O endereço de e-mail do contacto de faturação                                                                                                                    |
| cultura        | string                                                         | A sua cultura preferida para a comunicação e a moeda, como "en-us".                                                                               |
| language       | string                                                         | A sua linguagem preferida para a comunicação.                                                                                                            |
| nome da empresa    | string                                                         | O nome da empresa ou organização.                                                                                                               |
| defaultAddress | [Endereço](utility-resources.md#address)                       | O endereço para o qual as notas são enviadas, onde funciona o contacto de faturação.                                                                                   |
| ligações          | [RecursosLinks](utility-resources.md#resourcelinks)           | As ligações de recursos contidas no perfil.                                                                                                       |
| atributos     | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados correspondem ao perfil.                                                                                                  |

## <a name="customerrelationshiprequest"></a>CustomerRelationshipRequest

O recurso **CustomerRelationshipRequest** contém o URL utilizado pelo cliente para estabelecer uma relação de revendedor com um parceiro.

| Propriedade   | Tipo                                                           | Descrição                                                              |
|------------|----------------------------------------------------------------|--------------------------------------------------------------------------|
| url        | string                                                         | O URL utilizado pelo cliente para estabelecer uma relação com um parceiro. |
| atributos | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados atribuem correspondentes ao pedido de relacionamento.       |