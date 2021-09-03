---
title: Recursos de subscrição
description: Os recursos de subscrição podem fornecer mais informações sobre subscrições ao longo do ciclo de vida, tais como suporte, reembolsos, direitos Azure.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c898f9673525cf0ba32619b7c7b16f91311a81c7
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123456813"
---
# <a name="subscription-resources"></a>Recursos de subscrição

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Uma subscrição permite que um cliente utilize um serviço por um certo período de tempo. Nem todos os campos se aplicarão a todas as subscrições. Muitos campos só se aplicam em determinados pontos do ciclo de vida, como se uma subscrição for suspensa ou cancelada.

## <a name="subscription"></a>Subscrição

>[!NOTE]
>O recurso **de subscrição** tem um limite de taxa de 500 pedidos por minuto por identificador de inquilino.

O recurso **de subscrição** representa o ciclo de vida de uma subscrição e inclui propriedades que definem os estados ao longo do ciclo de vida da subscrição.

| Propriedade             | Tipo                                                          | Descrição                                                                                                                                                                   |
|----------------------|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID                   | string                                                        | O identificador de assinatura.                                                                                                                                                  |
| offerId              | string                                                        | O identificador da oferta.                                                                                                                                                         |
| direitodida        | string                                                        | O identificador de direito (um ID de assinatura Azure).                                                                                                                        |
| oferecerName            | string                                                        | O nome da oferta.                                                                                                                                                               |
| nome amigável         | string                                                        | O nome amigável para a subscrição definida pelo parceiro para ajudar a desambiguar.                                                                                           |
| quantidade             | número                                                        | A quantidade. Por exemplo, em caso de faturação baseada em licença, esta propriedade está definida para a contagem de licenças.                                                            |
| unitType             | string                                                        | As unidades que definem a quantidade para a subscrição.                                                                                                                             |
| parentSubscriptionId | string                                                        | Recebe ou define o identificador de assinatura dos pais.                                                                                                                              |
| criaçãoDate         | string                                                        | Obtém ou define a data de criação, em formato de data-hora.                                                                                                                          |
| effectiveStartDate   | cadeia no formato de hora de data UTC                                | Obtém ou define a data de início efetiva para esta subscrição, em formato de data-hora. É usado para datar uma subscrição migrada ou para alinhá-la com outra.                |
| compromissoEndDate    | cadeia no formato de hora de data UTC                                | A data limite de compromisso para esta subscrição, em formato de data-hora. Para as assinaturas que não são autorrenováveis, esta é uma data muito, muito distante no futuro.       |
| status               | string                                                        | O estado de subscrição: "nenhum", "ativo", "pendente", "suspenso", "caducado" ou "eliminado".                                                                                                         |
| autoRenewEnabled     | boolean                                                       | Obtém um valor que indique se a subscrição é renovada automaticamente.                                                                                                    |
| billingType          | string                                                        | Especifica como a subscrição é faturada: "nenhuma", "utilização" ou "licença".                                                                                                      |
| billingCycle         | string                                                        | Indica a frequência com que o parceiro é faturado para esta encomenda. Os valores suportados são os nomes dos membros encontrados no [**BillingCycleType**](product-resources.md#billingcycletype). |
| tem Sapos Evitáveis | boolean                                                       | Obtém ou define um valor que indique se a subscrição tem complementos puráveis.                                                                                             |
| isTrial              | boolean                                                       | Um valor que indica se se trata de uma subscrição experimental.                                                                                                                      |
| isMicrosoftProduct   | boolean                                                       | Um valor que indica se se trata de um produto Microsoft.                                                                                                                       |
| publisherName        | string                                                        | O nome da editora.                                                                                                                                                           |
| ações              | matriz de cadeias (de carateres)                                              | Recebe ou define as ações que são permitidas. Valores possíveis: "editar", "cancelar"                                                                                                  |
| partnerId            | string                                                        | O ID MPN do revendedor de registos, usado no modelo de parceiro indireto.                                                                                                     |
| suspensãoReasons    | matriz de cadeias (de carateres)                                              | Só para ler. Se a assinatura foi suspensa, indica porquê.                                                                                                                  |
| contraçãoType         | string                                                        | Só para ler. O tipo de contrato: "subscrição", "productKey" ou "redemptionCode".                                                                                           |
| reembolsoOpções        | matriz de recursos de [restituiçãoOpstion](#refundoption)   | Só para ler. O conjunto de opções de reembolso disponíveis para esta subscrição.                                                                                              |
| ligações                | [Ligações de Subscrição](#subscriptionlinks)                       | Obtém ou define os links de subscrição.                                                                                                                                          |
| orderId              | string                                                        | O ID da encomenda que foi feita para iniciar a subscrição.                                                                                                                |
| termoDuração         | string                                                        | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são **P1M** (1 mês), **P1Y** (1 ano) e **P3Y** (3 anos).                                                        |
| atributos           | [RecursosTributos](utility-resources.md#resourceattributes) | Os metadados atribuem correspondentes à subscrição.                                                                                                                    |
| renovaçãoTermDuration  | string                                                        | Uma representação ISO 8601 da duração do termo. Os valores suportados atuais são **P1M** (1 mês) e **P1Y** (1 ano).                                                        |
| ProdutoType  | [ItemType](product-resources.md#itemtype)                             | Só para ler. O tipo de produto para o qual a subscrição é para.     |

## <a name="subscriptionlinks"></a>Ligações de Subscrição

O recurso **SubscriptionLinks** descreve a recolha de links anexados a um recurso de subscrição.

| Propriedade           | Tipo                               | Description                           |
|--------------------|------------------------------------|---------------------------------------|
| oferta              | [Ligação](utility-resources.md#link) | Recebe ou define a oferta.               |
| parentalidadeSubscrição | [Ligação](utility-resources.md#link) | Recebe ou define a subscrição dos pais. |
| produto            | [Ligação](utility-resources.md#link) | Obtém o produto associado à subscrição. |
| sku                | [Ligação](utility-resources.md#link) | Obtém o sku do produto associado à subscrição. |
| disponibilidade       | [Ligação](utility-resources.md#link) | Obtém a disponibilidade de sku do produto associada à subscrição. |
| activaçãoLinks    | [Ligação](utility-resources.md#link) | Obtém a lista de links de ativação associados à subscrição. |
| self               | [Ligação](utility-resources.md#link) | O auto-URI.                         |
| seguinte               | [Ligação](utility-resources.md#link) | A próxima página de artigos.               |
| anterior           | [Ligação](utility-resources.md#link) | A página anterior dos artigos.           |

## <a name="subscriptionprovisioningstatus"></a>SubscriçãoProvisioningStatus

O recurso **SubscriptionProvisioningStatus** fornece informações sobre o estado de provisão de uma subscrição.

| Propriedade   | Tipo                                                           | Description                                                          |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------|
| skuId      | string                                                         | Uma corda formatada GUID que identifica o produto SKU.             |
| status     | string                                                         | Indica o estado de provisionamento: "sucesso", "pendente" ou "falhado". |
| quantidade   | número                                                         | Fornece a quantidade de subscrição após o provisionamento.               |
| endDate    | cadeia no formato de hora de data UTC                                 | A data final da subscrição.                                    |
| atributos | [RecursosTributos](utility-resources.md#resourceattributes)  | Os atributos dos metadados.                                             |

## <a name="subscriptionregistrationstatus"></a>SubscriçãoRegistrationStatus

O **recurso SubscriptionRegistrationStatus** descreve a recolha de links anexados a um recurso de subscrição.

| Propriedade           | Tipo                               | Description                                                                           |
|--------------------|------------------------------------|---------------------------------------------------------------------------------------|
| subscriptionId     | string                             | O identificador de assinatura.                                                          |
| status             | string                             | Indica o estado de inscrição: "registado", "registo", ou "não registado".    |

## <a name="supportcontact"></a>SupportContact

O recurso **SupportContact** representa um contacto de suporte para a subscrição de um cliente.

| Propriedade        | Tipo                                                           | Description                                                                     |
|-----------------|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| supportTenantId | string                                                         | Uma corda formatada GUID que indica o identificador de inquilino do contacto de suporte. |
| supportMpnId    | string                                                         | O identificador da Microsoft Partner Network (MPN) do contacto.                       |
| name            | string                                                         | O nome do contacto de apoio.                                                |
| ligações           | [RecursosLinks](utility-resources.md#resourcelinks)            | Os links relacionados com o contacto de suporte.                                              |
| atributos      | [RecursosTributos](utility-resources.md#resourceattributes)  | Os atributos dos metadados. Contém "objectType": " SupportContact".              |

## <a name="registersubscription"></a>Inscrição de registos

O recurso **RegisterSubscription** devolve um link que pode ser usado para consultar o estado de registo de uma subscrição. O estado de registo é devolvido no organismo de resposta de um pedido aceite com sucesso para registar uma assinatura Azure.

| Propriedade                | Tipo                               | Description                                                                           |
|-------------------------|------------------------------------|---------------------------------------------------------------------------------------|
| httpResponseMessage     | objeto                             | Devoluções HTTP Status Code 202 "Aceito", com um cabeçalho de localização contendo um link para consultar o estado de registo. Por exemplo, `"/customers/{customer-id}/subscriptions/{subscription-id}/registrationstatus"` |

## <a name="refundoption"></a>RestituiçãoOption

O recurso **RefundOption** representa uma possível opção de reembolso para a subscrição.

| Propriedade          | Tipo | Descrição                                                                         |
|-------------------|--------|-------------------------------------------------------------------------------------|
| tipo | string | O tipo de reembolso. Os valores suportados são "Parcial" e "Completo" |
| expira Depois      | cadeia no formato de hora de data UTC | A hora de tempo quando esta opção expirar. Se nulo, isto significa que não tem expiração. |

## <a name="azureentitlement"></a>AzureEntitlement

O recurso **AzureEntitlement** representa os direitos Azure para a subscrição.

| Propriedade          | Tipo | Descrição                                                                         |
|-------------------|--------|-------------------------------------------------------------------------------------|
| ID | string | O identificador de direitos |
| nome amigável      | string | O nome amigável do direito. |
| status | string | O estatuto de direito. |
| subscriptionId | string | O identificador de assinatura a que pertence o direito pertence. |
