---
title: Recursos do acordo
description: O recurso Do Acordo representa um acordo de cliente em nuvem da Microsoft com detalhes da certificação fornecida pelo parceiro.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: d964b1c7c6d70814ef68e48f05611ecbb113c8fe
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2020
ms.locfileid: "97770021"
---
# <a name="agreement-resources-representing-a-microsoft-cloud-customer-agreement"></a>Recursos do acordo que representam um acordo de cliente na nuvem da Microsoft

**Aplica-se a:**

- Partner Center

O recurso **Do Acordo** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft. Não é aplicável a:

- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

O recurso **Do Acordo** representa um acordo de cliente na nuvem da Microsoft.

## <a name="agreement"></a>Contrato

O recurso **do Acordo** representa os detalhes da certificação fornecida pelo parceiro.

| Propriedade       | Tipo   | Descrição                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| userId         | string                         | Identificador de objetos do utilizador registado no inquilino parceiro que está a fornecer confirmação em nome da organização parceira. Ao utilizar a autenticação App+User para criar um recurso Do Acordo, o Partner Center obtém automaticamente o valor de atributo **userId** a partir do token App+User.                                                                             |
| principalContact | [Contacto](./utility-resources.md#contact) | Informação sobre o utilizador da organização do cliente que aceitou o acordo, incluindo:  **primeiro Nome,** **último Nome,** **e-mail** e **telefoneNumber** (opcional). |
| dataA acordado     | cadeia no formato de hora de data UTC | A data em que o cliente aceitou o contrato.                                 |
| templateId     |string                          | Identificador único do contrato que o cliente aceitou. |
| tipo           |string                          | Tipo de acordo. Atualmente, os valores suportados incluem **o MicrosoftCloudAgreement** e **o MicrosoftCustomerAgreement**.|
| agreementLink  | string                         | URL para o modelo de contrato.                                                    |
