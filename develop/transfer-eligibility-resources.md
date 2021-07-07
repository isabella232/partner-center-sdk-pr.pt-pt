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
# <a name="transfereligibility-resources"></a><span data-ttu-id="5c392-103">Recursos de transfereelegibilidade</span><span class="sxs-lookup"><span data-stu-id="5c392-103">TransferEligibility resources</span></span>

<span data-ttu-id="5c392-104">Um parceiro pode criar uma transferência quando um cliente solicita a sua subscrição com o parceiro para ser transferido para outro parceiro.</span><span class="sxs-lookup"><span data-stu-id="5c392-104">A partner can create a transfer when a customer requests their subscription with the partner to be transferred to another partner.</span></span> <span data-ttu-id="5c392-105">Utilize a TransferEligibility para verificar se uma subscrição é elegível para ser transferida.</span><span class="sxs-lookup"><span data-stu-id="5c392-105">Use TransferEligibility to check whether a subscription is eligible to be transferred.</span></span>

## <a name="transfereligibility"></a><span data-ttu-id="5c392-106">Transfereligibilidade</span><span class="sxs-lookup"><span data-stu-id="5c392-106">TransferEligibility</span></span>

<span data-ttu-id="5c392-107">Descreve uma transferência Eelegibilidade.</span><span class="sxs-lookup"><span data-stu-id="5c392-107">Describes a transferEligibility.</span></span>

| <span data-ttu-id="5c392-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5c392-108">Property</span></span>              | <span data-ttu-id="5c392-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="5c392-109">Type</span></span>             | <span data-ttu-id="5c392-110">Description</span><span class="sxs-lookup"><span data-stu-id="5c392-110">Description</span></span>                                                                              |
|-----------------------|------------------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="5c392-111">ID</span><span class="sxs-lookup"><span data-stu-id="5c392-111">id</span></span>                    | <span data-ttu-id="5c392-112">string</span><span class="sxs-lookup"><span data-stu-id="5c392-112">string</span></span>           | <span data-ttu-id="5c392-113">O identificador de assinatura do cliente.</span><span class="sxs-lookup"><span data-stu-id="5c392-113">The customer's subscription identifier.</span></span>                                                  |
| <span data-ttu-id="5c392-114">isEligível</span><span class="sxs-lookup"><span data-stu-id="5c392-114">isEligible</span></span>            | <span data-ttu-id="5c392-115">bool</span><span class="sxs-lookup"><span data-stu-id="5c392-115">bool</span></span>             | <span data-ttu-id="5c392-116">Indica se a subscrição é elegível para a transferência.</span><span class="sxs-lookup"><span data-stu-id="5c392-116">Indicates whether the subscription is eligible for the transfer.</span></span>                         |
| <span data-ttu-id="5c392-117">Razão</span><span class="sxs-lookup"><span data-stu-id="5c392-117">Reason</span></span>                | <span data-ttu-id="5c392-118">string</span><span class="sxs-lookup"><span data-stu-id="5c392-118">string</span></span>           | <span data-ttu-id="5c392-119">A razão pela qual a propriedade explica por que a subscrição não é elegível para transferência.</span><span class="sxs-lookup"><span data-stu-id="5c392-119">The reason property explains why the subscription isn't eligible for transfer.</span></span> |