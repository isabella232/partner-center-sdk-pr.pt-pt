---
title: Acordo recursos de metadados
description: A coleção de recursos AgreementMetadata descreve tipos de acordo que os parceiros podem usar para fornecer confirmação da aceitação do cliente.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 36ba2aa2f78552dc9a835168b5bbd5b6a3ce47f3
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768839"
---
# <a name="agreement-metadata-resources"></a><span data-ttu-id="35636-103">Acordo recursos de metadados</span><span class="sxs-lookup"><span data-stu-id="35636-103">Agreement metadata resources</span></span>

<span data-ttu-id="35636-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="35636-104">**Applies to:**</span></span>

- <span data-ttu-id="35636-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="35636-105">Partner Center</span></span>

<span data-ttu-id="35636-106">O recurso **AgreementMetaData** é atualmente suportado pelo Partner Center apenas na nuvem pública da *Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="35636-106">The **AgreementMetaData** resource is currently supported by Partner Center only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="35636-107">Este recurso não é aplicável a:</span><span class="sxs-lookup"><span data-stu-id="35636-107">This resource isn't applicable to:</span></span>

- <span data-ttu-id="35636-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="35636-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="35636-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="35636-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="35636-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="35636-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="35636-111">A recolha **AgreementMetaData** fornece metadados sobre todos os tipos de contrato.</span><span class="sxs-lookup"><span data-stu-id="35636-111">The **AgreementMetaData** collection provides metadata about all the agreement types.</span></span> <span data-ttu-id="35636-112">Os parceiros podem usar esta coleção para fornecer a confirmação da aceitação pelo cliente de acordos.</span><span class="sxs-lookup"><span data-stu-id="35636-112">Partners can use this collection to provide confirmation of customer acceptance of agreements.</span></span> <span data-ttu-id="35636-113">A recolha **AgreementMetaData** devolve metadados para ambos os tipos de acordos **(Microsoft Cloud Agreement** e **Microsoft Customer Agreement**).</span><span class="sxs-lookup"><span data-stu-id="35636-113">The **AgreementMetaData** collection returns metadata for both agreement types (**Microsoft Cloud Agreement** and **Microsoft Customer Agreement**).</span></span>

## <a name="agreementmetadata"></a><span data-ttu-id="35636-114">AgreementMetaData</span><span class="sxs-lookup"><span data-stu-id="35636-114">AgreementMetaData</span></span>

<span data-ttu-id="35636-115">Os metadados do acordo devolvidos incluem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="35636-115">Agreement metadata returned includes the following properties:</span></span>

| <span data-ttu-id="35636-116">Propriedade</span><span class="sxs-lookup"><span data-stu-id="35636-116">Property</span></span>      | <span data-ttu-id="35636-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="35636-117">Type</span></span>               | <span data-ttu-id="35636-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="35636-118">Description</span></span>                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| <span data-ttu-id="35636-119">templateId</span><span class="sxs-lookup"><span data-stu-id="35636-119">templateId</span></span>    | <span data-ttu-id="35636-120">string</span><span class="sxs-lookup"><span data-stu-id="35636-120">string</span></span>             | <span data-ttu-id="35636-121">Identificador único de um modelo de acordo.</span><span class="sxs-lookup"><span data-stu-id="35636-121">Unique identifier of an agreement template.</span></span>                                       |
| <span data-ttu-id="35636-122">tipo</span><span class="sxs-lookup"><span data-stu-id="35636-122">type</span></span>          | <span data-ttu-id="35636-123">string</span><span class="sxs-lookup"><span data-stu-id="35636-123">string</span></span>             | <span data-ttu-id="35636-124">Tipo de acordo.</span><span class="sxs-lookup"><span data-stu-id="35636-124">Agreement type.</span></span> <span data-ttu-id="35636-125">Atualmente, os valores suportados incluem **o MicrosoftCloudAgreement** e **o MicrosoftCustomerAgreement** (pré-visualização).</span><span class="sxs-lookup"><span data-stu-id="35636-125">Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement** (preview).</span></span> |
| <span data-ttu-id="35636-126">agreementLink</span><span class="sxs-lookup"><span data-stu-id="35636-126">agreementLink</span></span> | <span data-ttu-id="35636-127">string</span><span class="sxs-lookup"><span data-stu-id="35636-127">string</span></span>             | <span data-ttu-id="35636-128">URL para o modelo de contrato.</span><span class="sxs-lookup"><span data-stu-id="35636-128">URL for the agreement template.</span></span>                                                    |
