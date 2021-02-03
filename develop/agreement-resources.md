---
title: Recursos do acordo
description: O recurso Do Acordo representa um acordo de cliente em nuvem da Microsoft com detalhes da certificação fornecida pelo parceiro.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: d964b1c7c6d70814ef68e48f05611ecbb113c8fe
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2020
ms.locfileid: "97770021"
---
# <a name="agreement-resources-representing-a-microsoft-cloud-customer-agreement"></a><span data-ttu-id="2a55f-103">Recursos do acordo que representam um acordo de cliente na nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="2a55f-103">Agreement resources representing a Microsoft cloud customer agreement</span></span>

<span data-ttu-id="2a55f-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="2a55f-104">**Applies to:**</span></span>

- <span data-ttu-id="2a55f-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="2a55f-105">Partner Center</span></span>

<span data-ttu-id="2a55f-106">O recurso **Do Acordo** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2a55f-106">The **Agreement** resource is currently supported by Partner Center in the Microsoft public cloud only.</span></span> <span data-ttu-id="2a55f-107">Não é aplicável a:</span><span class="sxs-lookup"><span data-stu-id="2a55f-107">It isn't applicable to:</span></span>

- <span data-ttu-id="2a55f-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="2a55f-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="2a55f-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="2a55f-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="2a55f-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2a55f-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2a55f-111">O recurso **Do Acordo** representa um acordo de cliente na nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2a55f-111">The **Agreement** resource represents a Microsoft cloud customer agreement.</span></span>

## <a name="agreement"></a><span data-ttu-id="2a55f-112">Contrato</span><span class="sxs-lookup"><span data-stu-id="2a55f-112">Agreement</span></span>

<span data-ttu-id="2a55f-113">O recurso **do Acordo** representa os detalhes da certificação fornecida pelo parceiro.</span><span class="sxs-lookup"><span data-stu-id="2a55f-113">The **Agreement** resource represents the details of certification provided by the partner.</span></span>

| <span data-ttu-id="2a55f-114">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2a55f-114">Property</span></span>       | <span data-ttu-id="2a55f-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="2a55f-115">Type</span></span>   | <span data-ttu-id="2a55f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a55f-116">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2a55f-117">userId</span><span class="sxs-lookup"><span data-stu-id="2a55f-117">userId</span></span>         | <span data-ttu-id="2a55f-118">string</span><span class="sxs-lookup"><span data-stu-id="2a55f-118">string</span></span>                         | <span data-ttu-id="2a55f-119">Identificador de objetos do utilizador registado no inquilino parceiro que está a fornecer confirmação em nome da organização parceira.</span><span class="sxs-lookup"><span data-stu-id="2a55f-119">Object identifier of the logged-in user in the partner tenant who is providing confirmation on behalf of the partner organization.</span></span> <span data-ttu-id="2a55f-120">Ao utilizar a autenticação App+User para criar um recurso Do Acordo, o Partner Center obtém automaticamente o valor de atributo **userId** a partir do token App+User.</span><span class="sxs-lookup"><span data-stu-id="2a55f-120">When using App+User authentication to create an Agreement resource, Partner Center automatically derives the **userId** attribute value from the App+User token.</span></span>                                                                             |
| <span data-ttu-id="2a55f-121">principalContact</span><span class="sxs-lookup"><span data-stu-id="2a55f-121">primaryContact</span></span> | [<span data-ttu-id="2a55f-122">Contacto</span><span class="sxs-lookup"><span data-stu-id="2a55f-122">Contact</span></span>](./utility-resources.md#contact) | <span data-ttu-id="2a55f-123">Informação sobre o utilizador da organização do cliente que aceitou o acordo, incluindo:  **primeiro Nome,** **último Nome,** **e-mail** e **telefoneNumber** (opcional).</span><span class="sxs-lookup"><span data-stu-id="2a55f-123">Information about the user from the customer organization that accepted the agreement, including:  **firstName**, **lastName**, **email**, and **phoneNumber** (optional).</span></span> |
| <span data-ttu-id="2a55f-124">dataA acordado</span><span class="sxs-lookup"><span data-stu-id="2a55f-124">dateAgreed</span></span>     | <span data-ttu-id="2a55f-125">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="2a55f-125">string in UTC date time format</span></span> | <span data-ttu-id="2a55f-126">A data em que o cliente aceitou o contrato.</span><span class="sxs-lookup"><span data-stu-id="2a55f-126">The date when the customer accepted the agreement.</span></span>                                 |
| <span data-ttu-id="2a55f-127">templateId</span><span class="sxs-lookup"><span data-stu-id="2a55f-127">templateId</span></span>     |<span data-ttu-id="2a55f-128">string</span><span class="sxs-lookup"><span data-stu-id="2a55f-128">string</span></span>                          | <span data-ttu-id="2a55f-129">Identificador único do contrato que o cliente aceitou.</span><span class="sxs-lookup"><span data-stu-id="2a55f-129">Unique identifier of the agreement that the customer accepted.</span></span> |
| <span data-ttu-id="2a55f-130">tipo</span><span class="sxs-lookup"><span data-stu-id="2a55f-130">type</span></span>           |<span data-ttu-id="2a55f-131">string</span><span class="sxs-lookup"><span data-stu-id="2a55f-131">string</span></span>                          | <span data-ttu-id="2a55f-132">Tipo de acordo.</span><span class="sxs-lookup"><span data-stu-id="2a55f-132">Agreement type.</span></span> <span data-ttu-id="2a55f-133">Atualmente, os valores suportados incluem **o MicrosoftCloudAgreement** e **o MicrosoftCustomerAgreement**.</span><span class="sxs-lookup"><span data-stu-id="2a55f-133">Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement**.</span></span>|
| <span data-ttu-id="2a55f-134">agreementLink</span><span class="sxs-lookup"><span data-stu-id="2a55f-134">agreementLink</span></span>  | <span data-ttu-id="2a55f-135">string</span><span class="sxs-lookup"><span data-stu-id="2a55f-135">string</span></span>                         | <span data-ttu-id="2a55f-136">URL para o modelo de contrato.</span><span class="sxs-lookup"><span data-stu-id="2a55f-136">URL for the agreement template.</span></span>                                                    |
