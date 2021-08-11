---
title: Recursos de auditoria
description: Saiba mais sobre recursos de auditoria da API do Partner Center, como o AuditRecord, que pode usar para obter um registo da atividade do Partner Center.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 50c90f7e7a5dfb274044fafab87818c7ac8428124ca9072770cc5fd9fa3806d5
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994664"
---
# <a name="auditing-resources-that-help-you-get-a-record-of-partner-center-activity"></a>Auditar recursos que o ajudam a obter um registo da atividade do Partner Center

Pode utilizar os seguintes recursos com operações de auditoria.

## <a name="auditrecord"></a>AuditoriaRecord

Representa um registo de uma operação realizada por um utilizador ou aplicação de um parceiro.

| Propriedade | Tipo | Description |
| --- | --- | ---|
| customerId | string | Uma cadeia formatada pelo GUID que identifica o cliente. |
| nome do cliente | string | O nome do cliente. |
| userPrincipalName | string | O nome principal do utilizador ou identificador do utilizador. Tipicamente, esta propriedade é um nome de login estilo Internet para um utilizador em um formato de endereço de e-mail baseado no RFC 822 padrão da Internet. |
| applicationId | string | Uma corda que identifica a aplicação que realizou a operação. |
| resourceType | string | O tipo de recurso agido pela operação. Valores possíveis: `customer` , , , , , , , , `customer_user` , , , , `order` , , `subscription` , `license` , `third_party_add_on` `mpn_association` `transfer` `application` `application_credential` `partner_user` `partner_relationship` `partner_customer_dap` , `customer_directory_role` |
| recursoOldValue | string | O valor antigo do recurso. |
| recursoNewValue | string | O novo valor do recurso. |
| operationType | string | O tipo de operação realizada. Valores possíveis: `update_customer_qualification` `update_subscription` , , [ contas `upgrade_subscription` de `convert_trial_subscription` `add_customer` `update_customer_billing_profile` `update_customer_partner_contract_company_name` `update_customer_spending_budget` `delete_customer` integração de caixas de areia), `remove_partner_customer_relationship` `create_order` `update_order` `create_customer_user` `delete_customer_user` `update_customer_user` `update_customer_user_licenses` `reset_customer_user_password` `update_customer_user_principal_name` `restore_customer_user` `create_mpn_association` `update_mpn_association` `update_sfb_customer_user_licenses` `update_transfer` `create_partner_relationship` `register_application` `unregister_application` `add_application_credential` `remove_application_credential` `create_partner_user` `update_partner_user` `create_self_serve_policy` `update_self_serve_policy` `create_self_serve_policy` `delete_self_serve_policy` `remove_partner_relationship` `delete_tip_customer` `create_related_referral` `update_related_referral` `create_referral` `update_referral` `get_software_key` `get_software_download_link` `increase_spending_limit` `ready_invoice` `create_agreement` `extend_relationship` `create_transfer` `dap_admin_relationship_approved` `dap_admin_relationship_terminated` `add_user_member` `remove_user_member` , |
| operaçãoDate | cadeia no formato de data-hora UTC | A data e a hora em que a operação foi realizada. |
| operaçõesStatus | string | O estado da operação a ser auditado. Valores possíveis: `succeeded` , ou , o que significa que a `failed` `progress` operação ainda está em curso. |
| personalizadoData  | matriz de objetos | Informação adicional. Cada objeto contém dois pares de valor-chave JSON: o primeiro é `key` e um valor de corda, o segundo é e um valor de `value` corda. O número de objetos na matriz depende do tipo de operação que foi realizado. |
| atributos | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados. |
