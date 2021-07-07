---
title: Recursos de transfereelegibilidade
description: Um parceiro pode criar uma transferência quando um cliente solicita a sua subscrição com o parceiro para ser transferido para outro parceiro.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8f121d499abffb4c4dda688c2a91c25f83d2e863
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530213"
---
# <a name="transfereligibility-resources"></a>Recursos de transfereelegibilidade

Um parceiro pode criar uma transferência quando um cliente solicita a sua subscrição com o parceiro para ser transferido para outro parceiro. Utilize a TransferEligibility para verificar se uma subscrição é elegível para ser transferida.

## <a name="transfereligibility"></a>Transfereligibilidade

Descreve uma transferência Eelegibilidade.

| Propriedade              | Tipo             | Description                                                                              |
|-----------------------|------------------|------------------------------------------------------------------------------------------|
| ID                    | string           | O identificador de assinatura do cliente.                                                  |
| isEligível            | bool             | Indica se a subscrição é elegível para a transferência.                         |
| Razão                | string           | A razão pela qual a propriedade explica por que a subscrição não é elegível para transferência. |