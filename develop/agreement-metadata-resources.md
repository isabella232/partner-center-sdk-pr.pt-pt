---
title: Acordo recursos de metadados
description: A coleção de recursos AgreementMetadata descreve tipos de acordo que os parceiros podem usar para fornecer confirmação da aceitação do cliente.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: b930e3691b9d269ddb8d76ae18b6b26a217123c0
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025636"
---
# <a name="agreement-metadata-resources"></a><span data-ttu-id="c3d4f-103">Acordo recursos de metadados</span><span class="sxs-lookup"><span data-stu-id="c3d4f-103">Agreement metadata resources</span></span>

<span data-ttu-id="c3d4f-104">**Aplica-se a**: Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="c3d4f-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="c3d4f-105">**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c3d4f-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c3d4f-106">O recurso **AgreementMetaData** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c3d4f-106">The **AgreementMetaData** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span> 

<span data-ttu-id="c3d4f-107">A recolha **AgreementMetaData** fornece metadados sobre todos os tipos de contrato.</span><span class="sxs-lookup"><span data-stu-id="c3d4f-107">The **AgreementMetaData** collection provides metadata about all the agreement types.</span></span> <span data-ttu-id="c3d4f-108">Os parceiros podem usar esta coleção para fornecer a confirmação da aceitação pelo cliente de acordos.</span><span class="sxs-lookup"><span data-stu-id="c3d4f-108">Partners can use this collection to provide confirmation of customer acceptance of agreements.</span></span> <span data-ttu-id="c3d4f-109">A recolha **AgreementMetaData** devolve metadados para ambos os tipos de acordos **(Microsoft Cloud Agreement** e **Microsoft Customer Agreement**).</span><span class="sxs-lookup"><span data-stu-id="c3d4f-109">The **AgreementMetaData** collection returns metadata for both agreement types (**Microsoft Cloud Agreement** and **Microsoft Customer Agreement**).</span></span>

## <a name="agreementmetadata"></a><span data-ttu-id="c3d4f-110">AgreementMetaData</span><span class="sxs-lookup"><span data-stu-id="c3d4f-110">AgreementMetaData</span></span>

<span data-ttu-id="c3d4f-111">Os metadados do acordo devolvidos incluem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c3d4f-111">Agreement metadata returned includes the following properties:</span></span>

| <span data-ttu-id="c3d4f-112">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c3d4f-112">Property</span></span>      | <span data-ttu-id="c3d4f-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="c3d4f-113">Type</span></span>               | <span data-ttu-id="c3d4f-114">Description</span><span class="sxs-lookup"><span data-stu-id="c3d4f-114">Description</span></span>                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| <span data-ttu-id="c3d4f-115">templateId</span><span class="sxs-lookup"><span data-stu-id="c3d4f-115">templateId</span></span>    | <span data-ttu-id="c3d4f-116">string</span><span class="sxs-lookup"><span data-stu-id="c3d4f-116">string</span></span>             | <span data-ttu-id="c3d4f-117">Identificador único de um modelo de acordo.</span><span class="sxs-lookup"><span data-stu-id="c3d4f-117">Unique identifier of an agreement template.</span></span>                                       |
| <span data-ttu-id="c3d4f-118">tipo</span><span class="sxs-lookup"><span data-stu-id="c3d4f-118">type</span></span>          | <span data-ttu-id="c3d4f-119">string</span><span class="sxs-lookup"><span data-stu-id="c3d4f-119">string</span></span>             | <span data-ttu-id="c3d4f-120">Tipo de acordo.</span><span class="sxs-lookup"><span data-stu-id="c3d4f-120">Agreement type.</span></span> <span data-ttu-id="c3d4f-121">Atualmente, os valores suportados incluem **o MicrosoftCloudAgreement** e **o MicrosoftCustomerAgreement** (pré-visualização).</span><span class="sxs-lookup"><span data-stu-id="c3d4f-121">Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement** (preview).</span></span> |
| <span data-ttu-id="c3d4f-122">agreementLink</span><span class="sxs-lookup"><span data-stu-id="c3d4f-122">agreementLink</span></span> | <span data-ttu-id="c3d4f-123">string</span><span class="sxs-lookup"><span data-stu-id="c3d4f-123">string</span></span>             | <span data-ttu-id="c3d4f-124">URL para o modelo de contrato.</span><span class="sxs-lookup"><span data-stu-id="c3d4f-124">URL for the agreement template.</span></span>                                                    |
