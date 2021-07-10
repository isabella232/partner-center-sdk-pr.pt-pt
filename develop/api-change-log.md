---
title: Registo de alterações da API REST do Centro de Parceiros
description: Esta página lista alterações nas APIs do Centro Parceiro REST
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.topic: reference
ms.date: 12/15/2020
ms.openlocfilehash: d4f7f034a36a26b6219086ca952b189f7a313ef7
ms.sourcegitcommit: 51237e7e98d71a7e0590b4d6a4034b6409542126
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/09/2021
ms.locfileid: "113572000"
---
# <a name="december-2020-changes-to-partner-center-rest-apis"></a><span data-ttu-id="91ab0-103">Alterações de dezembro de 2020 para Parceiro Centro REST APIs</span><span class="sxs-lookup"><span data-stu-id="91ab0-103">December 2020 changes to Partner Center REST APIs</span></span>

<span data-ttu-id="91ab0-104">Consulte aqui as alterações às APIs do Partner Center REST.</span><span class="sxs-lookup"><span data-stu-id="91ab0-104">Check here for changes to Partner Center REST APIs.</span></span>

## <a name="enhancements-to-education-pricing-eligibility-apis"></a><span data-ttu-id="91ab0-105">Melhorias nos preços da educação APIs de elegibilidade</span><span class="sxs-lookup"><span data-stu-id="91ab0-105">Enhancements to education pricing Eligibility APIs</span></span>



### <a name="what-has-changed"></a><span data-ttu-id="91ab0-106">O que mudou?</span><span class="sxs-lookup"><span data-stu-id="91ab0-106">What has changed?</span></span>

<span data-ttu-id="91ab0-107">Atualmente, a API do Partner Center dispõe de qualificações GET e PUT para verificar a elegibilidade dos clientes da Educação.</span><span class="sxs-lookup"><span data-stu-id="91ab0-107">Currently, the Partner Center API has GET and PUT qualifications to verify Education customers’ eligibility.</span></span> <span data-ttu-id="91ab0-108">Não haverá alterações na API de Qualificação GET.</span><span class="sxs-lookup"><span data-stu-id="91ab0-108">There will be no changes to the GET Qualification API.</span></span> <span data-ttu-id="91ab0-109">No entanto, adicionámos um caso de retorno à API de Qualificação PUT.</span><span class="sxs-lookup"><span data-stu-id="91ab0-109">However, we’ve added a return case to the PUT Qualification API.</span></span>

- <span data-ttu-id="91ab0-110">GET - não muda.</span><span class="sxs-lookup"><span data-stu-id="91ab0-110">GET - doesn't change.</span></span>
- <span data-ttu-id="91ab0-111">PUT - o caso de devolução será adicionado.</span><span class="sxs-lookup"><span data-stu-id="91ab0-111">PUT - return case will be added.</span></span>

<span data-ttu-id="91ab0-112">Estas APIs serão reformadas no final de fevereiro de 2021, para serem substituídas por novas APIs, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="91ab0-112">These APIs will be retired at the end of February 2021, to be replaced by new APIs as described below.</span></span>

### <a name="scenarios-impacted"></a><span data-ttu-id="91ab0-113">Cenários impactados:</span><span class="sxs-lookup"><span data-stu-id="91ab0-113">Scenarios impacted:</span></span>

<span data-ttu-id="91ab0-114">Elegibilidade do cliente para preços de educação em SKUs selecionados</span><span class="sxs-lookup"><span data-stu-id="91ab0-114">Customer eligibility for education pricing on select SKUs</span></span>

### <a name="detail-descriptions"></a><span data-ttu-id="91ab0-115">Descrições de detalhes</span><span class="sxs-lookup"><span data-stu-id="91ab0-115">Detail descriptions</span></span>

<span data-ttu-id="91ab0-116">Serão introduzidas duas novas APIs de Qualificações GET e POST.</span><span class="sxs-lookup"><span data-stu-id="91ab0-116">Two new GET and POST Qualifications APIs will be introduced.</span></span> <span data-ttu-id="91ab0-117">As novas APIs utilizarão **qualificações,** não **qualificações.**</span><span class="sxs-lookup"><span data-stu-id="91ab0-117">The new APIs will be using **Qualifications**, not **Qualification**.</span></span> <span data-ttu-id="91ab0-118">As APIs estarão disponíveis para testes no FY21 Q22.</span><span class="sxs-lookup"><span data-stu-id="91ab0-118">The APIs will be available for testing in FY21 Q2.</span></span>

#### <a name="get-qualifications"></a><span data-ttu-id="91ab0-119">Obter Qualificações</span><span class="sxs-lookup"><span data-stu-id="91ab0-119">GET Qualifications</span></span>

```http
GET {customer_id}/qualifications
```

#### <a name="response-example"></a><span data-ttu-id="91ab0-120">Exemplo de resposta:</span><span class="sxs-lookup"><span data-stu-id="91ab0-120">Response example:</span></span>

```json
{
  "Qualification": "Education",
  "VettingStatus": "Denied",
  "VettingReason": "Not an education customer",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

#### <a name="response-fields"></a><span data-ttu-id="91ab0-121">Campos de resposta:</span><span class="sxs-lookup"><span data-stu-id="91ab0-121">Response fields:</span></span> 

- <span data-ttu-id="91ab0-122">Valores de VettingStatus: Aprovado, Negado, InReview, etc.</span><span class="sxs-lookup"><span data-stu-id="91ab0-122">VettingStatus values: Approved, Denied, InReview, etc.</span></span>

- <span data-ttu-id="91ab0-123">Valores vetingReason:</span><span class="sxs-lookup"><span data-stu-id="91ab0-123">VettingReason values:</span></span>
   - <span data-ttu-id="91ab0-124">Não um Cliente de Educação</span><span class="sxs-lookup"><span data-stu-id="91ab0-124">Not an Education Customer</span></span>
   - <span data-ttu-id="91ab0-125">Não mais um Cliente de Educação</span><span class="sxs-lookup"><span data-stu-id="91ab0-125">No longer an Education Customer</span></span>
   - <span data-ttu-id="91ab0-126">Não um cliente de educação - após revisão</span><span class="sxs-lookup"><span data-stu-id="91ab0-126">Not an Education Customer - After Review</span></span>
   - <span data-ttu-id="91ab0-127">Restrito ser cliente de educação</span><span class="sxs-lookup"><span data-stu-id="91ab0-127">Restricted being an Education Customer</span></span>
   - <span data-ttu-id="91ab0-128">Não um domínio académico</span><span class="sxs-lookup"><span data-stu-id="91ab0-128">Not an Academic Domain</span></span>
   - <span data-ttu-id="91ab0-129">Não é uma biblioteca elegível</span><span class="sxs-lookup"><span data-stu-id="91ab0-129">Not an eligible Library</span></span>
   - <span data-ttu-id="91ab0-130">Não é um museu elegível.</span><span class="sxs-lookup"><span data-stu-id="91ab0-130">Not an eligible Museum</span></span>
 
#### <a name="post-qualifications"></a><span data-ttu-id="91ab0-131">Qualificações POST</span><span class="sxs-lookup"><span data-stu-id="91ab0-131">POST Qualifications</span></span>

```http
POST {customer_id}/qualifications
    [
            "Qualification": "Education"
    ]
```

#### <a name="response-example"></a><span data-ttu-id="91ab0-132">Exemplo de resposta:</span><span class="sxs-lookup"><span data-stu-id="91ab0-132">Response example:</span></span>

```JSON
{
  "Qualification": "Education",
  "VettingStatus": "InReview",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

## <a name="next-steps"></a><span data-ttu-id="91ab0-133">Passos seguintes</span><span class="sxs-lookup"><span data-stu-id="91ab0-133">Next steps</span></span>

[<span data-ttu-id="91ab0-134">Referência da API REST do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="91ab0-134">Partner Center REST API reference</span></span>](partner-center-rest-api-reference.md)
