---
title: O estado de assinatura direta (aceitação direta) de um contrato de cliente.
description: O recurso DirectSignedCustomerAgreementStatus representa o estatuto da assinatura direta (aceitação direta) de um contrato com o cliente.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 3ca272e81a91d0f27b8c01104f6b26230327b772517b76268dbfc5014830b915
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115995191"
---
# <a name="direct-signing-direct-acceptance-status-of-a-customer-agreement"></a>Estatuto de assinatura direta (aceitação direta) de um contrato de cliente

**Aplica-se a**: Centro de Parceiros

**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

O recurso **DirectSignedCustomerAgreementStatus** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.

O recurso **DirectSignedCustomerAgreementStatus** representa o estatuto da aceitação direta de um contrato com o cliente.

## <a name="directsignedcustomeragreementstatus"></a>DirectSignedCustomerAgreementStatus

Um recurso **DirectSignedCustomerAgreementStatus** inclui as seguintes propriedades:

| Propriedade       | Tipo   | Description                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| isSigned | boolean | Indica se o contrato de cliente foi assinado diretamente (aceite) pelo cliente. |
