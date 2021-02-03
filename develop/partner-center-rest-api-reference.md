---
title: Referência da API REST do Centro de Parceiros
description: Saiba como os parceiros da CSP podem usar as APIs do Partner Center REST para integrar o seu CRM e software de faturação com os sistemas da Microsoft para gerir melhor as contas dos clientes.
ms.date: 11/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 3f83b2b73c3480f76646cae4fcbbcbacd31d4b3f
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "97769943"
---
# <a name="partner-center-rest-api-reference-to-rest-urls-rest-headers-rest-resources-and-rest-events"></a><span data-ttu-id="493cd-103">Referência API do Partner Center REST a URLs REST, cabeçalhos REST, recursos REST e eventos REST</span><span class="sxs-lookup"><span data-stu-id="493cd-103">Partner Center REST API reference to REST URLs, REST headers, REST resources, and REST events</span></span>

<span data-ttu-id="493cd-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="493cd-104">**Applies to:**</span></span>

- <span data-ttu-id="493cd-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="493cd-105">Partner Center</span></span>
- <span data-ttu-id="493cd-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="493cd-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="493cd-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="493cd-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="493cd-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="493cd-108">Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="partner-center-rest-api"></a><span data-ttu-id="493cd-109">Centro Parceiro REST API</span><span class="sxs-lookup"><span data-stu-id="493cd-109">Partner Center REST API</span></span>

<span data-ttu-id="493cd-110">A API do Partner Center REST ajuda os parceiros Cloud Solution Provider (CSP) a integrarem o seu software de CRM ou de faturação existente com os sistemas microsoft que gerem contas de clientes, escamam encomendas, gerem subscrições e lidam com pedidos de suporte.</span><span class="sxs-lookup"><span data-stu-id="493cd-110">The Partner Center REST API helps Cloud Solution Provider (CSP) partners integrate their existing CRM or billing software with the Microsoft systems that manage customer accounts, place orders, manage subscriptions, and handle support requests.</span></span>

<span data-ttu-id="493cd-111">Para obter mais informações sobre o que a API pode fazer, incluindo o código de amostra, consulte o tópico [Scenarios,](scenarios.md) incluindo a visão geral de fundo.</span><span class="sxs-lookup"><span data-stu-id="493cd-111">For more information about what the API can do, including sample code, see the [Scenarios](scenarios.md) topic, including the background overview.</span></span>

<span data-ttu-id="493cd-112">Antes de começar a codificar, leia o tema [Get start.](get-started.md)</span><span class="sxs-lookup"><span data-stu-id="493cd-112">Before you begin coding, read the [Get started](get-started.md) topic.</span></span> <span data-ttu-id="493cd-113">Este artigo contém informações sobre a criação das suas contas de teste e de produção, o funcionamento da autenticação e a procura do código de amostra.</span><span class="sxs-lookup"><span data-stu-id="493cd-113">This article contains information about setting up your test and production accounts, getting authentication working, and finding the sample code.</span></span>

## <a name="topics"></a><span data-ttu-id="493cd-114">Tópicos</span><span class="sxs-lookup"><span data-stu-id="493cd-114">Topics</span></span>

| <span data-ttu-id="493cd-115">Tópico</span><span class="sxs-lookup"><span data-stu-id="493cd-115">Topic</span></span> | <span data-ttu-id="493cd-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="493cd-116">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="493cd-117">URLs REST do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="493cd-117">Partner Center REST URLs</span></span>](partner-center-rest-urls.md) | <span data-ttu-id="493cd-118">Define os pontos finais da API REST para diferentes versões do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="493cd-118">Defines the REST API endpoints for different versions of Partner Center.</span></span> |
| [<span data-ttu-id="493cd-119">Cabeçalhos REST do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="493cd-119">Partner Center REST headers</span></span>](headers.md) | <span data-ttu-id="493cd-120">Define os cabeçalhos de pedido e resposta utilizados pela API REST.</span><span class="sxs-lookup"><span data-stu-id="493cd-120">Defines the request and response headers used by the REST API.</span></span> |
| [<span data-ttu-id="493cd-121">Recursos REST do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="493cd-121">Partner Center REST resources</span></span>](partner-center-rest-resources.md) | <span data-ttu-id="493cd-122">Define as construções JSON que representam os objetos necessários para utilizar a API REST.</span><span class="sxs-lookup"><span data-stu-id="493cd-122">Defines the JSON constructs that represent the objects needed to use the REST API.</span></span> |
| [<span data-ttu-id="493cd-123">Eventos REST do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="493cd-123">Partner Center REST events</span></span>](partner-center-webhook-events.md) | <span data-ttu-id="493cd-124">Define os eventos de mudança de recursos REST que são suportados por webhooks partner Center.</span><span class="sxs-lookup"><span data-stu-id="493cd-124">Defines the REST resource change events that are supported by Partner Center webhooks.</span></span> |
| [<span data-ttu-id="493cd-125">Regiões e idiomas suportados pelo Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="493cd-125">Partner Center supported languages and locales</span></span>](partner-center-supported-languages-and-locales.md) | <span data-ttu-id="493cd-126">Lista os códigos locais, idiomas e de país/região que são suportados nas APIs do Centro de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="493cd-126">Lists the locales, languages, and country/region codes that are supported in the Partner Center APIs.</span></span> |
| [<span data-ttu-id="493cd-127">Webhooks do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="493cd-127">Partner Center webhooks</span></span>](partner-center-webhooks.md) | <span data-ttu-id="493cd-128">Como receber eventos, autenticar uma chamada e utilizar as APIs do Partner Center para criar, visualizar e atualizar um registo de eventos.</span><span class="sxs-lookup"><span data-stu-id="493cd-128">How to receive events, authenticate a callback, and use the Partner Center webhook APIs to create, view, and update an event registration.</span></span> |