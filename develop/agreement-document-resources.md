---
title: Recursos documentais do acordo
description: O recurso AgreementDocument é um documento de acordo da Microsoft para pré-visualização e download. É suportado pelo Partner Center na nuvem pública da Microsoft.
ms.date: 08/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 1a81da4f75594f241669db831125bd437872561c
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025671"
---
# <a name="agreement-document-resources-supported-by-partner-center-in-the-microsoft-public-cloud"></a><span data-ttu-id="c94db-104">Recursos documentais do acordo apoiados pelo Partner Center na nuvem pública da Microsoft</span><span class="sxs-lookup"><span data-stu-id="c94db-104">Agreement document resources supported by Partner Center in the Microsoft public cloud</span></span>

<span data-ttu-id="c94db-105">**Aplica-se a**: Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="c94db-105">**Applies to**: Partner Center</span></span>

<span data-ttu-id="c94db-106">**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c94db-106">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c94db-107">O recurso **AgreementDocument** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c94db-107">The **AgreementDocument** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="c94db-108">O recurso **AgreementDocument** representa um documento de acordo da Microsoft que está disponível para pré-visualização e download.</span><span class="sxs-lookup"><span data-stu-id="c94db-108">The **AgreementDocument** resource represents a Microsoft agreement document that is available for preview and download.</span></span>

## <a name="agreementdocument"></a><span data-ttu-id="c94db-109">AcordoDocument</span><span class="sxs-lookup"><span data-stu-id="c94db-109">AgreementDocument</span></span>

<span data-ttu-id="c94db-110">Um recurso **AgreementDocument** inclui as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c94db-110">An **AgreementDocument** resource includes the following properties:</span></span>

| <span data-ttu-id="c94db-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c94db-111">Property</span></span>       | <span data-ttu-id="c94db-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="c94db-112">Type</span></span>   | <span data-ttu-id="c94db-113">Description</span><span class="sxs-lookup"><span data-stu-id="c94db-113">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c94db-114">país</span><span class="sxs-lookup"><span data-stu-id="c94db-114">country</span></span> | <span data-ttu-id="c94db-115">string</span><span class="sxs-lookup"><span data-stu-id="c94db-115">string</span></span> | <span data-ttu-id="c94db-116">O país ou o mercado a que este documento se aplica.</span><span class="sxs-lookup"><span data-stu-id="c94db-116">The country or market to which this document applies.</span></span> |
| <span data-ttu-id="c94db-117">language</span><span class="sxs-lookup"><span data-stu-id="c94db-117">language</span></span> | <span data-ttu-id="c94db-118">string</span><span class="sxs-lookup"><span data-stu-id="c94db-118">string</span></span> | <span data-ttu-id="c94db-119">A língua em que este documento está localizado.</span><span class="sxs-lookup"><span data-stu-id="c94db-119">The language in which this document is localized.</span></span> |
| <span data-ttu-id="c94db-120">displayUri</span><span class="sxs-lookup"><span data-stu-id="c94db-120">displayUri</span></span> | <span data-ttu-id="c94db-121">string</span><span class="sxs-lookup"><span data-stu-id="c94db-121">string</span></span> | <span data-ttu-id="c94db-122">Um link para pré-visualizar o documento do contrato num browser.</span><span class="sxs-lookup"><span data-stu-id="c94db-122">A link to preview the agreement document in a browser.</span></span>  |
| <span data-ttu-id="c94db-123">downloadUri</span><span class="sxs-lookup"><span data-stu-id="c94db-123">downloadUri</span></span> |<span data-ttu-id="c94db-124">string</span><span class="sxs-lookup"><span data-stu-id="c94db-124">string</span></span> | <span data-ttu-id="c94db-125">Um link para descarregar o documento do contrato (em formato Microsoft Word).</span><span class="sxs-lookup"><span data-stu-id="c94db-125">A link to download the agreement document (in Microsoft Word format).</span></span> |
