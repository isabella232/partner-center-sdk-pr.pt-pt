---
title: Recursos de transfereelegibilidade
description: Um parceiro cria uma transferência quando um cliente quer que a sua subscrição com o parceiro seja transferida para outro parceiro.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: dcac5724a1f708bc540a3aac7ce74b2eda60a296
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768960"
---
# <a name="transfereligibility-resources"></a><span data-ttu-id="a7298-103">Recursos de transfereelegibilidade</span><span class="sxs-lookup"><span data-stu-id="a7298-103">TransferEligibility resources</span></span>

<span data-ttu-id="a7298-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="a7298-104">**Applies to:**</span></span>

- <span data-ttu-id="a7298-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="a7298-105">Partner Center</span></span>

<span data-ttu-id="a7298-106">Um parceiro cria uma transferência quando um cliente quer que a sua subscrição com o parceiro seja transferida para outro parceiro.</span><span class="sxs-lookup"><span data-stu-id="a7298-106">A partner creates a transfer when a customer wants their subscription with the partner to be transferred to another partner.</span></span>

## <a name="transfereligibility"></a><span data-ttu-id="a7298-107">Transfereligibilidade</span><span class="sxs-lookup"><span data-stu-id="a7298-107">TransferEligibility</span></span>

<span data-ttu-id="a7298-108">Descreve uma transferência Eelegibilidade.</span><span class="sxs-lookup"><span data-stu-id="a7298-108">Describes a transferEligibility.</span></span>

| <span data-ttu-id="a7298-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a7298-109">Property</span></span>              | <span data-ttu-id="a7298-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="a7298-110">Type</span></span>             | <span data-ttu-id="a7298-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7298-111">Description</span></span>                                                                              |
|-----------------------|------------------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="a7298-112">ID</span><span class="sxs-lookup"><span data-stu-id="a7298-112">id</span></span>                    | <span data-ttu-id="a7298-113">string</span><span class="sxs-lookup"><span data-stu-id="a7298-113">string</span></span>           | <span data-ttu-id="a7298-114">O identificador de assinatura do cliente.</span><span class="sxs-lookup"><span data-stu-id="a7298-114">The customer's subscription identifier.</span></span>                                                  |
| <span data-ttu-id="a7298-115">isEligível</span><span class="sxs-lookup"><span data-stu-id="a7298-115">isEligible</span></span>            | <span data-ttu-id="a7298-116">bool</span><span class="sxs-lookup"><span data-stu-id="a7298-116">bool</span></span>             | <span data-ttu-id="a7298-117">Indica se a subscrição é elegível para a transferência.</span><span class="sxs-lookup"><span data-stu-id="a7298-117">Indicates whether the subscription is eligible for the transfer.</span></span>                         |
| <span data-ttu-id="a7298-118">Razão</span><span class="sxs-lookup"><span data-stu-id="a7298-118">Reason</span></span>                | <span data-ttu-id="a7298-119">string</span><span class="sxs-lookup"><span data-stu-id="a7298-119">string</span></span>           | <span data-ttu-id="a7298-120">A razão pela qual a propriedade explica por que a subscrição não é elegível para transferência.</span><span class="sxs-lookup"><span data-stu-id="a7298-120">The reason property explains why the subscription isn't eligible for transfer.</span></span> |