---
title: Recursos documentais do acordo
description: O recurso AgreementDocument é um documento de acordo da Microsoft para pré-visualização e download. É suportado pelo Partner Center na nuvem pública da Microsoft.
ms.date: 08/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 4805d25b0838bf922b81bebd998810c3f6a809c3
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2020
ms.locfileid: "97770028"
---
# <a name="agreement-document-resources-supported-by-partner-center-in-the-microsoft-public-cloud"></a><span data-ttu-id="c1237-104">Recursos documentais do acordo apoiados pelo Partner Center na nuvem pública da Microsoft</span><span class="sxs-lookup"><span data-stu-id="c1237-104">Agreement document resources supported by Partner Center in the Microsoft public cloud</span></span>

<span data-ttu-id="c1237-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="c1237-105">**Applies to:**</span></span>

- <span data-ttu-id="c1237-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="c1237-106">Partner Center</span></span>

<span data-ttu-id="c1237-107">O recurso **AgreementDocument** é atualmente suportado pelo Partner Center apenas na nuvem pública da *Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="c1237-107">The **AgreementDocument** resource is currently supported by Partner Center only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="c1237-108">Este recurso não é aplicável a:</span><span class="sxs-lookup"><span data-stu-id="c1237-108">This resource not applicable to:</span></span>

- <span data-ttu-id="c1237-109">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="c1237-109">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="c1237-110">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="c1237-110">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="c1237-111">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c1237-111">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c1237-112">O recurso **AgreementDocument** representa um documento de acordo da Microsoft que está disponível para pré-visualização e download.</span><span class="sxs-lookup"><span data-stu-id="c1237-112">The **AgreementDocument** resource represents a Microsoft agreement document that is available for preview and download.</span></span>

## <a name="agreementdocument"></a><span data-ttu-id="c1237-113">AcordoDocument</span><span class="sxs-lookup"><span data-stu-id="c1237-113">AgreementDocument</span></span>

<span data-ttu-id="c1237-114">Um recurso **AgreementDocument** inclui as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c1237-114">An **AgreementDocument** resource includes the following properties:</span></span>

| <span data-ttu-id="c1237-115">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c1237-115">Property</span></span>       | <span data-ttu-id="c1237-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="c1237-116">Type</span></span>   | <span data-ttu-id="c1237-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1237-117">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c1237-118">país</span><span class="sxs-lookup"><span data-stu-id="c1237-118">country</span></span> | <span data-ttu-id="c1237-119">string</span><span class="sxs-lookup"><span data-stu-id="c1237-119">string</span></span> | <span data-ttu-id="c1237-120">O país ou o mercado a que este documento se aplica.</span><span class="sxs-lookup"><span data-stu-id="c1237-120">The country or market to which this document applies.</span></span> |
| <span data-ttu-id="c1237-121">language</span><span class="sxs-lookup"><span data-stu-id="c1237-121">language</span></span> | <span data-ttu-id="c1237-122">string</span><span class="sxs-lookup"><span data-stu-id="c1237-122">string</span></span> | <span data-ttu-id="c1237-123">A língua em que este documento está localizado.</span><span class="sxs-lookup"><span data-stu-id="c1237-123">The language in which this document is localized.</span></span> |
| <span data-ttu-id="c1237-124">displayUri</span><span class="sxs-lookup"><span data-stu-id="c1237-124">displayUri</span></span> | <span data-ttu-id="c1237-125">string</span><span class="sxs-lookup"><span data-stu-id="c1237-125">string</span></span> | <span data-ttu-id="c1237-126">Um link para pré-visualizar o documento do contrato num browser.</span><span class="sxs-lookup"><span data-stu-id="c1237-126">A link to preview the agreement document in a browser.</span></span>  |
| <span data-ttu-id="c1237-127">downloadUri</span><span class="sxs-lookup"><span data-stu-id="c1237-127">downloadUri</span></span> |<span data-ttu-id="c1237-128">string</span><span class="sxs-lookup"><span data-stu-id="c1237-128">string</span></span> | <span data-ttu-id="c1237-129">Um link para descarregar o documento do contrato (no formato Microsoft Word).</span><span class="sxs-lookup"><span data-stu-id="c1237-129">A link to download the agreement document (in Microsoft Word format).</span></span> |
