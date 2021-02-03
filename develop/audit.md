---
title: Operações de auditoria da atividade do Partner Center
description: Saiba mais sobre o tipo de operações de auditoria do Partner Center API que pode usar para obter um registo da atividade do Partner Center.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 019bebe40c43f6ee1c2ac7da381a86ca190702d4
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2020
ms.locfileid: "97769992"
---
# <a name="audit-operations-available-via-partner-center-api-that-show-a-record-of-partner-center-activity"></a>Operações de auditoria disponíveis através da Partner Center API que mostram um registo da atividade do Partner Center

As APIs do Partner Center fornecem funcionalidades de auditoria para que possa obter um registo da atividade do Partner Center.

Pode obter registos de auditoria para os 30 dias anteriores a partir da data atual, ou para um intervalo de datas especificado por incluir a data de início e/ou a data final. Note-se, no entanto, que por razões de desempenho a disponibilidade de dados de registo de atividade está limitada aos 90 dias anteriores. Os pedidos com uma data de início superior a 90 dias antes da data atual receberão uma exceção de mau pedido (código de erro: 400) e uma mensagem apropriada.

## <a name="retrieve-audit-records"></a>Recuperar registos de auditoria

Obtenha registos históricos de auditoria detalhados das operações realizadas por um utilizador ou aplicação de um parceiro:

- [Obter um registo da atividade do Centro de Parceiros](get-a-record-of-partner-center-activity-by-user.md)
- [Recursos de auditoria](auditing-resources.md)