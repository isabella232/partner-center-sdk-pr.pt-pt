---
title: Recursos de perfil
description: Descreve o comportamento dos perfis de um Cloud Solution Provider.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e0561278995f4f9747320866b51de57efea8f712
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769662"
---
# <a name="profile-resources"></a>Recursos de perfil

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Descreve o comportamento dos perfis de um Cloud Solution Provider.

## <a name="billingprofile"></a>BillingProfile

Descreve o perfil de faturação de um parceiro.

| Propriedade            | Tipo                                                           | Descrição                                                 |
|---------------------|----------------------------------------------------------------|-------------------------------------------------------------|
| nome da empresa         | string                                                         | O nome da empresa de faturação.                                   |
| address             | [Endereço](utility-resources.md#address)                       | O endereço de endereço de faturação da empresa ou organização. |
| principalContact      | [Contacto](utility-resources.md#contact)                       | O principal contacto para a empresa ou organização.        |
| purchaseOrderNumber | string                                                         | O número de pedido de compra da empresa ou da organização.        |
| taxId               | string                                                         | A identificação fiscal da empresa ou da organização.                       |
| billingCurrency     | string                                                         | A moeda utilizada pela empresa ou organização.           |
| perfilType         | string                                                         | O tipo de perfil do parceiro.                                   |
| ligações               | [RecursosLinks](utility-resources.md#resourcelinks)           | Os links de recursos correspondentes ao perfil.            |
| atributos          | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados correspondem ao perfil.       |

## <a name="legalbusinessprofile"></a>LegalBusinessProfile

Descreve o perfil de negócio legal de um parceiro.

| Propriedade               | Tipo                                                           | Descrição                                                                                                                                                          |
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| nome da empresa            | string                                                         | O nome da empresa legal.                                                                                                                                              |
| address                | [Endereço](utility-resources.md#address)                       | O endereço da empresa ou organização.                                                                                                                          |
| principalContact         | [Contacto](utility-resources.md#contact)                       | O principal contacto para a empresa ou organização.                                                                                                                 |
| empresaApproverAddress | [Endereço](utility-resources.md#address)                       | O endereço do aprovador da empresa.                                                                                                                                        |
| empresaApproverEmail   | string                                                         | O e-mail aprovador da empresa.                                                                                                                                          |
| vettingStatus          | string                                                         | O estado de verificação. Este valor é a representação de uma das cordas encontradas em [**VettingStatus**](/dotnet/api/microsoft.store.partnercenter.models.partners.vettingstatus).           |
| verificaçãoSubStatus       | string                                                         | O sub-estado de verificação. Este valor é a representação de uma das cordas encontradas no [**VettingSubStatus**](/dotnet/api/microsoft.store.partnercenter.models.partners.vettingsubstatus). |
| perfilType            | string                                                         | O tipo de perfil do parceiro.                                                                                                                                            |
| ligações                  | [RecursosLinks](utility-resources.md#resourcelinks)           | Os links de recursos correspondentes ao perfil.                                                                                                                     |
| atributos             | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados correspondem ao perfil.                                                                                                                |

## <a name="mpnprofile"></a>MpnProfile

Descreve o perfil da Microsoft Partner Network de um parceiro.

| Propriedade    | Tipo                                                           | Descrição                                           |
|-------------|----------------------------------------------------------------|-------------------------------------------------------|
| nome parceiro | string                                                         | A empresa ou o nome da organização.                     |
| mpnId       | string                                                         | O ID da Rede de Parceiros da Microsoft.                     |
| perfilType | string                                                         | O tipo de perfil do parceiro.                             |
| ligações       | [RecursosLinks](utility-resources.md#resourcelinks)           | Os links de recursos correspondentes ao perfil.      |
| atributos  | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados correspondem ao perfil. |

## <a name="organizationprofile"></a>OrganizaçãoProfile

Descreve o perfil de organização de um parceiro.

| Propriedade       | Tipo                                                           | Descrição                                                            |
|----------------|----------------------------------------------------------------|------------------------------------------------------------------------|
| ID             | string                                                         | A organização identifica.                                                 |
| nome da empresa    | string                                                         | O nome da empresa ou organização.                               |
| defaultAddress | [Endereço](utility-resources.md#address)                       | O endereço padrão da empresa ou organização.                    |
| inquilinoId       | string                                                         | O identificador do inquilino.                                                 |
| domínio         | string                                                         | O domínio da empresa ou da organização.                                  |
| e-mail          | string                                                         | Recebe ou define a subscrição dos pais.                                  |
| language       | string                                                         | A linguagem preferida para a comunicação.                              |
| cultura        | string                                                         | A cultura preferida para a comunicação e a moeda, como "en-us". |
| perfilType    | string                                                         | O tipo de perfil do parceiro.                                              |
| ligações          | [RecursosLinks](utility-resources.md#resourcelinks)           | Os links de recursos correspondentes ao perfil.                       |
| atributos     | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados correspondem ao perfil.                  |

## <a name="supportprofile"></a>SupportProfile

Descreve o perfil de suporte de um parceiro.

| Propriedade    | Tipo                                                           | Descrição                                           |
|-------------|----------------------------------------------------------------|-------------------------------------------------------|
| e-mail       | string                                                         | O endereço de e-mail associado ao perfil.        |
| telefone   | string                                                         | O número de telefone associado ao perfil.         |
| site     | string                                                         | O site de apoio.                                  |
| perfilType | string                                                         | O tipo de perfil do parceiro.                             |
| ligações       | [RecursosLinks](utility-resources.md#resourcelinks)           | Os links de recursos correspondentes ao perfil.      |
| atributos  | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados correspondem ao perfil. |

