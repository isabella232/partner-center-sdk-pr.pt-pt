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
# <a name="direct-signing-direct-acceptance-status-of-a-customer-agreement"></a><span data-ttu-id="0b6af-103">Estatuto de assinatura direta (aceitação direta) de um contrato de cliente</span><span class="sxs-lookup"><span data-stu-id="0b6af-103">Direct signing (direct acceptance) status of a customer agreement</span></span>

<span data-ttu-id="0b6af-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="0b6af-104">**Applies to:**</span></span>

- <span data-ttu-id="0b6af-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="0b6af-105">Partner Center</span></span>

<span data-ttu-id="0b6af-106">O recurso **DirectSignedCustomerAgreementStatus** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0b6af-106">The **DirectSignedCustomerAgreementStatus** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="0b6af-107">Este recurso não é *aplicável* a:</span><span class="sxs-lookup"><span data-stu-id="0b6af-107">This resource is *not applicable* to:</span></span>

- <span data-ttu-id="0b6af-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="0b6af-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="0b6af-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="0b6af-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="0b6af-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0b6af-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0b6af-111">O recurso **DirectSignedCustomerAgreementStatus** representa o estatuto da aceitação direta de um contrato com o cliente.</span><span class="sxs-lookup"><span data-stu-id="0b6af-111">The **DirectSignedCustomerAgreementStatus** resource represents the status of the direct acceptance of a customer agreement.</span></span>

## <a name="directsignedcustomeragreementstatus"></a><span data-ttu-id="0b6af-112">DirectSignedCustomerAgreementStatus</span><span class="sxs-lookup"><span data-stu-id="0b6af-112">DirectSignedCustomerAgreementStatus</span></span>

<span data-ttu-id="0b6af-113">Um recurso **DirectSignedCustomerAgreementStatus** inclui as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="0b6af-113">A **DirectSignedCustomerAgreementStatus** resource includes the following properties:</span></span>

| <span data-ttu-id="0b6af-114">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0b6af-114">Property</span></span>       | <span data-ttu-id="0b6af-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="0b6af-115">Type</span></span>   | <span data-ttu-id="0b6af-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b6af-116">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0b6af-117">isSigned</span><span class="sxs-lookup"><span data-stu-id="0b6af-117">isSigned</span></span> | <span data-ttu-id="0b6af-118">boolean</span><span class="sxs-lookup"><span data-stu-id="0b6af-118">boolean</span></span> | <span data-ttu-id="0b6af-119">Indica se o contrato de cliente foi assinado diretamente (aceite) pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="0b6af-119">Indicates if the customer agreement has been directly signed (accepted) by the customer.</span></span> |
