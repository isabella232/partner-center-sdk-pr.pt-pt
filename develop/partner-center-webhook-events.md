---
title: Eventos webhook do Partner Center
description: Documentação para todos os eventos Webhook suportados pelo Partner Center.
ms.date: 04/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 5358aab8efdd68ad52c583936304f99ffae12708
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769248"
---
# <a name="partner-center-webhook-events"></a>Eventos webhook do Partner Center

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Os eventos webhook do Partner Center são eventos de mudança de recursos entregues sob a forma de POSTs HTTP para um URL registado. Para receber um evento do Partner Center, você hospeda uma chamada onde o Partner Center pode POST o evento. O evento está assinado digitalmente para que possa validar que foi enviado do Partner Center.

Para obter informações sobre como receber eventos, autente uma chamada e utilize as APIs do Partner Center para criar, visualizar e atualizar um registo de [eventos, consulte o Partner Center Webhooks](partner-center-webhooks.md).

## <a name="supported-events"></a>Eventos Apoiados

Os seguintes eventos webhook são suportados pelo Partner Center.

### <a name="test-event"></a>Evento de Teste

Este evento permite-lhe auto-a bordo e testar o seu registo solicitando um evento de teste e, em seguida, rastreando o seu progresso. Poderá ver as mensagens de falha que estão a ser recebidas da Microsoft enquanto tenta entregar o evento. Isto só se aplicará a eventos "criados por testes" e os dados com mais de 7 dias serão purgados.

>[!NOTE]
>Existe um limite de aceleração de 2 pedidos por minuto ao publicar um evento criado pelo teste.

#### <a name="properties"></a>Propriedades

| Propriedade                  | Tipo                               | Descrição                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | O nome do evento. No formulário {recurso}-{ação}. Para este evento, o valor é "criado no teste".                                          |
| RecursosUri               | URI                                | O URI para obter o recurso. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/registration/validationEvents/{{CorrelationId}} |
| ResourceName              | string                             | O nome do recurso que irá desencadear o evento. Para este evento, o valor é "teste".                                  |
| AuditUri                  | URI                                | (Opcional) O URI para obter o registo de auditoria, se é que existe. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}} |
| ResourceChangeUtcDate     | corda no formato de data-hora UTC | A data e a hora em que ocorreu a alteração de recursos.                                                         |

#### <a name="example"></a>Exemplo

```json
{
    "EventName": "test-created",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/{{CorrelationId}}",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

### <a name="subscription-updated-event"></a>Evento Atualizado de Assinatura

Este evento é levantado quando a subscrição especificada muda. Um evento atualizado de subscrição é gerado quando há uma alteração interna para além de quando as alterações são feitas através da API do Centro Parceiro.  Este evento só será gerado quando houver alterações ao nível do comércio, por exemplo, quando o número de licenças for alterado e quando o estado da subscrição mudar. Não será gerado quando os recursos forem criados dentro da subscrição.

>[!NOTE]
>Há um atraso de até 48 horas entre a hora em que uma subscrição muda e quando o evento Atualizado de Subscrição é ativado.

#### <a name="properties"></a>Propriedades

| Propriedade                  | Tipo                               | Descrição                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | O nome do evento. No formulário {recurso}-{ação}. Para este evento, o valor é "atualizado por subscrição".                                  |
| RecursosUri               | URI                                | O URI para obter o recurso. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/customers/{CustomerId}}/subscrições/{{SubscriptionId}}" |
| ResourceName              | string                             | O nome do recurso que irá desencadear o evento. Para este evento, o valor é "subscrição".                          |
| AuditUri                  | URI                                | (Opcional) O URI para obter o registo de auditoria, se é que existe. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}} |
| ResourceChangeUtcDate     | corda no formato de data-hora UTC | A data e a hora em que ocorreu a alteração de recursos.                                                         |

#### <a name="example"></a>Exemplo

```json
{
    "EventName": "subscription-updated",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/customers/{{CustomerId}}/subscriptions/{{SubscriptionId}}",
    "ResourceName": "subscription",
    "AuditUri": "https://api.partnercenter.microsoft.com/v1/auditrecords/{{AuditId}}",
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

### <a name="threshold-exceeded-event"></a>Evento Excededo limiar

Este evento é aumentado quando a quantidade de utilização do Microsoft Azure para qualquer cliente excede o seu orçamento de gastos de utilização (o seu limiar). Para obter mais informações, consulte [Desconfiem de um orçamento de gastos Azure para os seus clientes/parceiro-centro/set-an-azure-spend-budget-for-your-customers).

#### <a name="properties"></a>Propriedades

| Propriedade                  | Tipo                               | Descrição                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | O nome do evento. No formulário {recurso}-{ação}. Para este evento, o valor é "usagerecords-thresholdExceeded".                                  |
| RecursosUri               | URI                                | O URI para obter o recurso. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/customers/usagerecords" |
| ResourceName              | string                             | O nome do recurso que irá desencadear o evento. Para este evento, o valor é "registos de uso".                          |
| AuditUri                  | URI                                | (Opcional) O URI para obter o registo de auditoria, se é que existe. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}} |
| ResourceChangeUtcDate     | corda no formato de data-hora UTC | A data e a hora em que ocorreu a alteração de recursos.                                                         |

#### <a name="example"></a>Exemplo

```json
{
    "EventName": "usagerecords-thresholdExceeded",
    "ResourceUri": "https://api.partnercenter.microsoft.com/v1/customers/usagerecords",
    "ResourceName": "usagerecords",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### <a name="referral-created-event"></a>Evento Criado de Referência

Este evento é levantado quando a referência é criada.

#### <a name="properties"></a>Propriedades

| Propriedade                  | Tipo                               | Descrição                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | O nome do evento. No formulário {recurso}-{ação}. Para este evento, o valor é "criado por referenciação".                                  |
| RecursosUri               | URI                                | O URI para obter o recurso. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/engagements/v1/referrals/{{ReferralID} |
| ResourceName              | string                             | O nome do recurso que irá desencadear o evento. Para este evento, o valor é "referenciação".                          |
| AuditUri                  | URI                                | (Opcional) O URI para obter o registo de auditoria, se é que existe. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}} |
| ResourceChangeUtcDate     | corda no formato de data-hora UTC | A data e a hora em que ocorreu a alteração de recursos.                                                         |

#### <a name="example"></a>Exemplo

```json
{
    "EventName": "referral-created",
    "ResourceUri": "https://api.partnercenter.microsoft.com/engagements/v1/referrals/{{ReferralID}}",
    "ResourceName": "referral",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### <a name="referral-updated-event"></a>Evento Atualizado de Encaminhamento

Este evento é levantado quando a referência é atualizada.

#### <a name="properties"></a>Propriedades

| Propriedade                  | Tipo                               | Descrição                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName                 | string                             | O nome do evento. No formulário {recurso}-{ação}. Para este evento, o valor é "atualizado com referência".                                  |
| RecursosUri               | URI                                | O URI para obter o recurso. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/engagements/v1/referrals/{{ReferralID} |
| ResourceName              | string                             | O nome do recurso que irá desencadear o evento. Para este evento, o valor é "referenciação".                          |
| AuditUri                  | URI                                | (Opcional) O URI para obter o registo de auditoria, se é que existe. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}} |
| ResourceChangeUtcDate     | corda no formato de data-hora UTC | A data e a hora em que ocorreu a alteração de recursos.                                                         |

#### <a name="example"></a>Exemplo

```json
{
    "EventName": "referral-updated",
    "ResourceUri": "https://api.partnercenter.microsoft.com/engagements/v1/referrals/{{ReferralID}}",
    "ResourceName": "referral",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### <a name="invoice-ready-event"></a>Evento pronto para faturas

Este evento é levantado quando a nova fatura estiver pronta.

| Propriedade                  | Tipo                               | Descrição                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| EventName | string | O nome do evento. No formulário {recurso}-{ação}. Para este evento, o valor está "pronto para faturar". |
| RecursosUri | URI | O URI para obter o recurso. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{{{FaturaId} |
| ResourceName | string | O nome do recurso que irá desencadear o evento. Para este evento, o valor é "fatura". |
| AuditUri |  URI | (Opcional) O URI para obter o registo de auditoria, se é que existe. Utiliza a sintaxe: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}") |
| ResourceChangeUtcDate | corda no formato de data-hora UTC | A data e a hora em que ocorreu a alteração de recursos. |

#### <a name="example"></a>Exemplo

```json
{
    "EventName": "invoice-ready",
    "ResourceUri": "https://api.partnercenter.microsoft.com/v1/invoices/{{InvoiceId}}",
    "ResourceName": "invoice",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}

```
