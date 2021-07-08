---
title: Referência da API REST do Centro de Parceiros
description: Saiba como os parceiros da CSP podem usar as APIs do Partner Center REST para integrar o seu CRM e software de faturação com os sistemas da Microsoft para gerir melhor as contas dos clientes.
ms.date: 11/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 18621fdb94f91f066b69a11f7d557410d653787e
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548044"
---
# <a name="partner-center-rest-api-reference-to-rest-urls-rest-headers-rest-resources-and-rest-events"></a><span data-ttu-id="4598e-103">Referência API do Partner Center REST a URLs REST, cabeçalhos REST, recursos REST e eventos REST</span><span class="sxs-lookup"><span data-stu-id="4598e-103">Partner Center REST API reference to REST URLs, REST headers, REST resources, and REST events</span></span>

<span data-ttu-id="4598e-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4598e-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="partner-center-rest-api"></a><span data-ttu-id="4598e-105">Centro Parceiro REST API</span><span class="sxs-lookup"><span data-stu-id="4598e-105">Partner Center REST API</span></span>

<span data-ttu-id="4598e-106">A API do Partner Center REST ajuda os parceiros Fornecedor de Soluções em Nuvem (CSP) a integrarem o seu software de CRM ou de faturação existente com os sistemas microsoft que gerem contas de clientes, escamam encomendas, gerem subscrições e lidam com pedidos de suporte.</span><span class="sxs-lookup"><span data-stu-id="4598e-106">The Partner Center REST API helps Cloud Solution Provider (CSP) partners integrate their existing CRM or billing software with the Microsoft systems that manage customer accounts, place orders, manage subscriptions, and handle support requests.</span></span>

<span data-ttu-id="4598e-107">Para obter mais informações sobre o que a API pode fazer, incluindo o código de amostra, consulte o tópico [Scenarios,](scenarios.md) incluindo a visão geral de fundo.</span><span class="sxs-lookup"><span data-stu-id="4598e-107">For more information about what the API can do, including sample code, see the [Scenarios](scenarios.md) topic, including the background overview.</span></span>

<span data-ttu-id="4598e-108">Antes de começar a codificar, leia o tema [Get start.](get-started.md)</span><span class="sxs-lookup"><span data-stu-id="4598e-108">Before you begin coding, read the [Get started](get-started.md) topic.</span></span> <span data-ttu-id="4598e-109">Este artigo contém informações sobre a criação das suas contas de teste e de produção, o funcionamento da autenticação e a procura do código de amostra.</span><span class="sxs-lookup"><span data-stu-id="4598e-109">This article contains information about setting up your test and production accounts, getting authentication working, and finding the sample code.</span></span>

<span data-ttu-id="4598e-110">Para obter um guia de referência que explique cada API, consulte [a API do Partner Center REST](/rest/api/partner-center-rest/).</span><span class="sxs-lookup"><span data-stu-id="4598e-110">For a reference guide explaining each API, see [Partner Center REST API](/rest/api/partner-center-rest/).</span></span>

## <a name="topics"></a><span data-ttu-id="4598e-111">Tópicos</span><span class="sxs-lookup"><span data-stu-id="4598e-111">Topics</span></span>

| <span data-ttu-id="4598e-112">Tópico</span><span class="sxs-lookup"><span data-stu-id="4598e-112">Topic</span></span> | <span data-ttu-id="4598e-113">Description</span><span class="sxs-lookup"><span data-stu-id="4598e-113">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="4598e-114">Centro Parceiro REST API</span><span class="sxs-lookup"><span data-stu-id="4598e-114">Partner Center REST API</span></span>](/rest/api/partner-center-rest/) | <span data-ttu-id="4598e-115">Referência de cada API REST disponível para Partner Center.</span><span class="sxs-lookup"><span data-stu-id="4598e-115">Reference of each REST API available for Partner Center.</span></span> |
| [<span data-ttu-id="4598e-116">URLs REST do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="4598e-116">Partner Center REST URLs</span></span>](partner-center-rest-urls.md) | <span data-ttu-id="4598e-117">Define os pontos finais da API REST para diferentes versões do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="4598e-117">Defines the REST API endpoints for different versions of Partner Center.</span></span> |
| [<span data-ttu-id="4598e-118">Cabeçalhos REST do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="4598e-118">Partner Center REST headers</span></span>](headers.md) | <span data-ttu-id="4598e-119">Define os cabeçalhos de pedido e resposta utilizados pela API REST.</span><span class="sxs-lookup"><span data-stu-id="4598e-119">Defines the request and response headers used by the REST API.</span></span> |
| [<span data-ttu-id="4598e-120">Recursos REST do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="4598e-120">Partner Center REST resources</span></span>](partner-center-rest-resources.md) | <span data-ttu-id="4598e-121">Define as construções JSON que representam os objetos necessários para utilizar a API REST.</span><span class="sxs-lookup"><span data-stu-id="4598e-121">Defines the JSON constructs that represent the objects needed to use the REST API.</span></span> |
| [<span data-ttu-id="4598e-122">Eventos REST do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="4598e-122">Partner Center REST events</span></span>](partner-center-webhook-events.md) | <span data-ttu-id="4598e-123">Define os eventos de mudança de recursos REST que são suportados por webhooks partner Center.</span><span class="sxs-lookup"><span data-stu-id="4598e-123">Defines the REST resource change events that are supported by Partner Center webhooks.</span></span> |
| [<span data-ttu-id="4598e-124">Regiões e idiomas suportados pelo Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="4598e-124">Partner Center supported languages and locales</span></span>](partner-center-supported-languages-and-locales.md) | <span data-ttu-id="4598e-125">Lista os códigos locais, idiomas e de país/região que são suportados nas APIs do Centro de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="4598e-125">Lists the locales, languages, and country/region codes that are supported in the Partner Center APIs.</span></span> |
| [<span data-ttu-id="4598e-126">Webhooks do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="4598e-126">Partner Center webhooks</span></span>](partner-center-webhooks.md) | <span data-ttu-id="4598e-127">Como receber eventos, autenticar uma chamada e utilizar as APIs do Partner Center para criar, visualizar e atualizar um registo de eventos.</span><span class="sxs-lookup"><span data-stu-id="4598e-127">How to receive events, authenticate a callback, and use the Partner Center webhook APIs to create, view, and update an event registration.</span></span> |
