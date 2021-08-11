---
title: Recursos de transfereelegibilidade
description: Um parceiro pode criar uma transferência quando um cliente solicita a sua subscrição com o parceiro para ser transferido para outro parceiro.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ffe72aa04de17cf6e45e49e9fdbec8ba08da2deed89f5d54425a17825c91a53a
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996653"
---
# <a name="transfereligibility-resources"></a>Recursos de transfereelegibilidade

Um parceiro pode criar uma transferência quando um cliente solicita a sua subscrição com o parceiro para ser transferido para outro parceiro. Utilize a TransferEligibility para verificar se uma subscrição é elegível para ser transferida.

## <a name="transfereligibility"></a>Transfereligibilidade

Descreve uma transferência Eelegibilidade.

| Propriedade              | Tipo             | Descrição                                                                              |
|-----------------------|------------------|------------------------------------------------------------------------------------------|
| ID                    | string           | O identificador de assinatura do cliente.                                                  |
| isEligível            | bool             | Indica se a subscrição é elegível para a transferência.                         |
| Razão                | string           | A razão pela qual a propriedade explica por que a subscrição não é elegível para transferência. |