---
title: O estado de assinatura direta (aceitação direta) de um contrato de cliente.
description: O recurso DirectSignedCustomerAgreementStatus representa o estatuto da assinatura direta (aceitação direta) de um contrato com o cliente.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 9c4fd12ac3319057f3c4034aa0c8d93dcda726c6
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768797"
---
# <a name="direct-signing-direct-acceptance-status-of-a-customer-agreement"></a>Estatuto de assinatura direta (aceitação direta) de um contrato de cliente

**Aplica-se a:**

- Partner Center

O recurso **DirectSignedCustomerAgreementStatus** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.

Este recurso não é *aplicável* a:

- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

O recurso **DirectSignedCustomerAgreementStatus** representa o estatuto da aceitação direta de um contrato com o cliente.

## <a name="directsignedcustomeragreementstatus"></a>DirectSignedCustomerAgreementStatus

Um recurso **DirectSignedCustomerAgreementStatus** inclui as seguintes propriedades:

| Propriedade       | Tipo   | Descrição                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| isSigned | boolean | Indica se o contrato de cliente foi assinado diretamente (aceite) pelo cliente. |
