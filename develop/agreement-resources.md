---
title: Recursos do acordo
description: O recurso Do Acordo representa um acordo de cliente em nuvem da Microsoft com detalhes da certificação fornecida pelo parceiro.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 5fa196e711d9ff899b61ba20e75edd92749165e5
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025627"
---
# <a name="agreement-resources-representing-a-microsoft-cloud-customer-agreement"></a><span data-ttu-id="79ad0-103">Recursos do acordo que representam um acordo de cliente na nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="79ad0-103">Agreement resources representing a Microsoft cloud customer agreement</span></span>

<span data-ttu-id="79ad0-104">**Aplica-se a**: Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="79ad0-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="79ad0-105">**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="79ad0-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="79ad0-106">O recurso **Do Acordo** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="79ad0-106">The **Agreement** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="79ad0-107">O recurso **Do Acordo** representa um acordo de cliente na nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="79ad0-107">The **Agreement** resource represents a Microsoft cloud customer agreement.</span></span>

## <a name="agreement"></a><span data-ttu-id="79ad0-108">Contrato</span><span class="sxs-lookup"><span data-stu-id="79ad0-108">Agreement</span></span>

<span data-ttu-id="79ad0-109">O recurso **do Acordo** representa os detalhes da certificação fornecida pelo parceiro.</span><span class="sxs-lookup"><span data-stu-id="79ad0-109">The **Agreement** resource represents the details of certification provided by the partner.</span></span>

| <span data-ttu-id="79ad0-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="79ad0-110">Property</span></span>       | <span data-ttu-id="79ad0-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="79ad0-111">Type</span></span>   | <span data-ttu-id="79ad0-112">Description</span><span class="sxs-lookup"><span data-stu-id="79ad0-112">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="79ad0-113">userId</span><span class="sxs-lookup"><span data-stu-id="79ad0-113">userId</span></span>         | <span data-ttu-id="79ad0-114">string</span><span class="sxs-lookup"><span data-stu-id="79ad0-114">string</span></span>                         | <span data-ttu-id="79ad0-115">Identificador de objetos do utilizador registado no inquilino parceiro que está a fornecer confirmação em nome da organização parceira.</span><span class="sxs-lookup"><span data-stu-id="79ad0-115">Object identifier of the logged-in user in the partner tenant who is providing confirmation on behalf of the partner organization.</span></span> <span data-ttu-id="79ad0-116">Ao utilizar a autenticação App+User para criar um recurso Do Acordo, o Partner Center obtém automaticamente o valor de atributo **userId** a partir do token App+User.</span><span class="sxs-lookup"><span data-stu-id="79ad0-116">When using App+User authentication to create an Agreement resource, Partner Center automatically derives the **userId** attribute value from the App+User token.</span></span>                                                                             |
| <span data-ttu-id="79ad0-117">principalContact</span><span class="sxs-lookup"><span data-stu-id="79ad0-117">primaryContact</span></span> | [<span data-ttu-id="79ad0-118">Contacto</span><span class="sxs-lookup"><span data-stu-id="79ad0-118">Contact</span></span>](./utility-resources.md#contact) | <span data-ttu-id="79ad0-119">Informação sobre o utilizador da organização do cliente que aceitou o acordo, incluindo:  **primeiro Nome,** **último Nome,** **e-mail** e **telefoneNumber** (opcional).</span><span class="sxs-lookup"><span data-stu-id="79ad0-119">Information about the user from the customer organization that accepted the agreement, including:  **firstName**, **lastName**, **email**, and **phoneNumber** (optional).</span></span> |
| <span data-ttu-id="79ad0-120">dataA acordado</span><span class="sxs-lookup"><span data-stu-id="79ad0-120">dateAgreed</span></span>     | <span data-ttu-id="79ad0-121">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="79ad0-121">string in UTC date time format</span></span> | <span data-ttu-id="79ad0-122">A data em que o cliente aceitou o contrato.</span><span class="sxs-lookup"><span data-stu-id="79ad0-122">The date when the customer accepted the agreement.</span></span>                                 |
| <span data-ttu-id="79ad0-123">templateId</span><span class="sxs-lookup"><span data-stu-id="79ad0-123">templateId</span></span>     |<span data-ttu-id="79ad0-124">string</span><span class="sxs-lookup"><span data-stu-id="79ad0-124">string</span></span>                          | <span data-ttu-id="79ad0-125">Identificador único do contrato que o cliente aceitou.</span><span class="sxs-lookup"><span data-stu-id="79ad0-125">Unique identifier of the agreement that the customer accepted.</span></span> |
| <span data-ttu-id="79ad0-126">tipo</span><span class="sxs-lookup"><span data-stu-id="79ad0-126">type</span></span>           |<span data-ttu-id="79ad0-127">string</span><span class="sxs-lookup"><span data-stu-id="79ad0-127">string</span></span>                          | <span data-ttu-id="79ad0-128">Tipo de acordo.</span><span class="sxs-lookup"><span data-stu-id="79ad0-128">Agreement type.</span></span> <span data-ttu-id="79ad0-129">Atualmente, os valores suportados incluem **o MicrosoftCloudAgreement** e **o MicrosoftCustomerAgreement**.</span><span class="sxs-lookup"><span data-stu-id="79ad0-129">Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement**.</span></span>|
| <span data-ttu-id="79ad0-130">agreementLink</span><span class="sxs-lookup"><span data-stu-id="79ad0-130">agreementLink</span></span>  | <span data-ttu-id="79ad0-131">string</span><span class="sxs-lookup"><span data-stu-id="79ad0-131">string</span></span>                         | <span data-ttu-id="79ad0-132">URL para o modelo de contrato.</span><span class="sxs-lookup"><span data-stu-id="79ad0-132">URL for the agreement template.</span></span>                                                    |
