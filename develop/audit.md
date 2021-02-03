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
# <a name="audit-operations-available-via-partner-center-api-that-show-a-record-of-partner-center-activity"></a><span data-ttu-id="6c87d-103">Operações de auditoria disponíveis através da Partner Center API que mostram um registo da atividade do Partner Center</span><span class="sxs-lookup"><span data-stu-id="6c87d-103">Audit operations available via Partner Center API that show a record of Partner Center activity</span></span>

<span data-ttu-id="6c87d-104">As APIs do Partner Center fornecem funcionalidades de auditoria para que possa obter um registo da atividade do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="6c87d-104">The Partner Center APIs provide auditing features so you can get a record of Partner Center activity.</span></span>

<span data-ttu-id="6c87d-105">Pode obter registos de auditoria para os 30 dias anteriores a partir da data atual, ou para um intervalo de datas especificado por incluir a data de início e/ou a data final.</span><span class="sxs-lookup"><span data-stu-id="6c87d-105">You can retrieve audit records for the previous 30 days from the current date, or for a date range specified by including the start date and/or the end date.</span></span> <span data-ttu-id="6c87d-106">Note-se, no entanto, que por razões de desempenho a disponibilidade de dados de registo de atividade está limitada aos 90 dias anteriores.</span><span class="sxs-lookup"><span data-stu-id="6c87d-106">Note, however, that for performance reasons activity log data availability is limited to the previous 90 days.</span></span> <span data-ttu-id="6c87d-107">Os pedidos com uma data de início superior a 90 dias antes da data atual receberão uma exceção de mau pedido (código de erro: 400) e uma mensagem apropriada.</span><span class="sxs-lookup"><span data-stu-id="6c87d-107">Requests with a start date greater than 90 days prior to the current date will receive a bad request exception (error code: 400) and an appropriate message.</span></span>

## <a name="retrieve-audit-records"></a><span data-ttu-id="6c87d-108">Recuperar registos de auditoria</span><span class="sxs-lookup"><span data-stu-id="6c87d-108">Retrieve audit records</span></span>

<span data-ttu-id="6c87d-109">Obtenha registos históricos de auditoria detalhados das operações realizadas por um utilizador ou aplicação de um parceiro:</span><span class="sxs-lookup"><span data-stu-id="6c87d-109">Get detailed historical audit records of operations performed by a partner user or application:</span></span>

- [<span data-ttu-id="6c87d-110">Obter um registo da atividade do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="6c87d-110">Get a record of Partner Center activity</span></span>](get-a-record-of-partner-center-activity-by-user.md)
- [<span data-ttu-id="6c87d-111">Recursos de auditoria</span><span class="sxs-lookup"><span data-stu-id="6c87d-111">Auditing resources</span></span>](auditing-resources.md)