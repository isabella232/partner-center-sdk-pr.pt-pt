---
title: Loja Web para clientes CSP
description: Este código do site da amostra mostra uma loja online funcionando para os clientes comprarem subscrições de produtos Microsoft.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d68f17d707731f426cb980a566b6478790d3507c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973337"
---
# <a name="csp-customer-web-storefront"></a><span data-ttu-id="d640b-103">Loja Web para clientes CSP</span><span class="sxs-lookup"><span data-stu-id="d640b-103">CSP customer web storefront</span></span>

<span data-ttu-id="d640b-104">**Aplica-se a**: Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="d640b-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="d640b-105">**Não se aplica a**: Partner Center for Microsoft Cloud Germany | Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d640b-105">**Does not apply to**: Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d640b-106">Esta aplicação de amostra aplica-se apenas à instância global do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d640b-106">This sample app applies only to the global instance of Partner Center.</span></span>

<span data-ttu-id="d640b-107">A [loja Partner Center](https://github.com/Microsoft/Partner-Center-Storefront) é um site de **amostras** para uma loja online que os clientes podem usar para comprar subscrições de produtos microsoft.</span><span class="sxs-lookup"><span data-stu-id="d640b-107">The [Partner Center storefront](https://github.com/Microsoft/Partner-Center-Storefront) is a **sample website** for an online store that customers can use to buy subscriptions to Microsoft products.</span></span> <span data-ttu-id="d640b-108">Pode modificar este **código de amostra** para seu próprio uso para [configurar as ofertas,](#configure-offers) [adicionar branding,](#configure-branding)e [adicionar um método de pagamento](#configure-payment-types).</span><span class="sxs-lookup"><span data-stu-id="d640b-108">You can modify this **sample code** for your own use to [configure the offers](#configure-offers), [add branding](#configure-branding), and [add a payment method](#configure-payment-types).</span></span>

## <a name="sample-code"></a><span data-ttu-id="d640b-109">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="d640b-109">Sample code</span></span>

<span data-ttu-id="d640b-110">Descarregue o código de amostra da [loja Partner Center](https://github.com/Microsoft/Partner-Center-Storefront) a partir de GitHub.</span><span class="sxs-lookup"><span data-stu-id="d640b-110">Download the [Partner Center storefront sample code](https://github.com/Microsoft/Partner-Center-Storefront) from GitHub.</span></span>

## <a name="configure-authentication"></a><span data-ttu-id="d640b-111">Configurar a autenticação</span><span class="sxs-lookup"><span data-stu-id="d640b-111">Configure authentication</span></span>

<span data-ttu-id="d640b-112">Antes de construir a aplicação, atualize os seguintes valores no ficheiro Web.config para refletir a informação de autenticação AD AZure que criou na [autenticação do Partner Center.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="d640b-112">Before you build the application, update the following values in the Web.config file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d640b-113">Deve utilizar as definições da sua conta de caixa de areia de integração durante o desenvolvimento precoce ou para testes em produção (TiP).</span><span class="sxs-lookup"><span data-stu-id="d640b-113">You should use your integration sandbox account settings during early development or for testing in production (TiP).</span></span>

- <span data-ttu-id="d640b-114">**partnerCenter.applicationD**</span><span class="sxs-lookup"><span data-stu-id="d640b-114">**partnerCenter.applicationId**</span></span>
- <span data-ttu-id="d640b-115">**partnerCenter.applicationSecret**</span><span class="sxs-lookup"><span data-stu-id="d640b-115">**partnerCenter.applicationSecret**</span></span>
- <span data-ttu-id="d640b-116">**partnerCenter.domain**</span><span class="sxs-lookup"><span data-stu-id="d640b-116">**partnerCenter.domain**</span></span>
- <span data-ttu-id="d640b-117">**webPortal.clientId**</span><span class="sxs-lookup"><span data-stu-id="d640b-117">**webPortal.clientId**</span></span>
- <span data-ttu-id="d640b-118">**webPortal.clientSecret**</span><span class="sxs-lookup"><span data-stu-id="d640b-118">**webPortal.clientSecret**</span></span>
- <span data-ttu-id="d640b-119">**webPortal.domínio**</span><span class="sxs-lookup"><span data-stu-id="d640b-119">**webPortal.domain**</span></span>
- <span data-ttu-id="d640b-120">**webPortal.azureStorageConnectionString**</span><span class="sxs-lookup"><span data-stu-id="d640b-120">**webPortal.azureStorageConnectionString**</span></span>

## <a name="configure-offers"></a><span data-ttu-id="d640b-121">Configure ofertas</span><span class="sxs-lookup"><span data-stu-id="d640b-121">Configure offers</span></span>

<span data-ttu-id="d640b-122">Pode configurar o conjunto de ofertas **(MicrosoftOffer)** no **OfferCatalogViewModel**.</span><span class="sxs-lookup"><span data-stu-id="d640b-122">You can configure the set of offers (**MicrosoftOffer**) in the **OfferCatalogViewModel**.</span></span>

## <a name="configure-branding"></a><span data-ttu-id="d640b-123">Configurar a marca</span><span class="sxs-lookup"><span data-stu-id="d640b-123">Configure branding</span></span>

<span data-ttu-id="d640b-124">Este site de amostras rastreia as seguintes informações da empresa e da marca em *BrandingConfiguration.cs* e *PortalBranding.cs*:</span><span class="sxs-lookup"><span data-stu-id="d640b-124">This sample website tracks the following company and brand information in *BrandingConfiguration.cs* and *PortalBranding.cs*:</span></span>

- <span data-ttu-id="d640b-125">Nome da organização</span><span class="sxs-lookup"><span data-stu-id="d640b-125">Organization name</span></span>
- <span data-ttu-id="d640b-126">Logotipo da organização</span><span class="sxs-lookup"><span data-stu-id="d640b-126">Organization logo</span></span>
- <span data-ttu-id="d640b-127">Imagem de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="d640b-127">Header image</span></span>
- <span data-ttu-id="d640b-128">Acordo de privacidade</span><span class="sxs-lookup"><span data-stu-id="d640b-128">Privacy agreement</span></span>
- <span data-ttu-id="d640b-129">E-mail de contacto</span><span class="sxs-lookup"><span data-stu-id="d640b-129">Contact email</span></span>
- <span data-ttu-id="d640b-130">Número de telefone de contato</span><span class="sxs-lookup"><span data-stu-id="d640b-130">Contact phone number</span></span>
- <span data-ttu-id="d640b-131">E-mail de apoio</span><span class="sxs-lookup"><span data-stu-id="d640b-131">Support email</span></span>
- <span data-ttu-id="d640b-132">Número de telefone de suporte</span><span class="sxs-lookup"><span data-stu-id="d640b-132">Support phone number</span></span>

### <a name="configure-payment-types"></a><span data-ttu-id="d640b-133">Configurar tipos de pagamento</span><span class="sxs-lookup"><span data-stu-id="d640b-133">Configure payment types</span></span>

<span data-ttu-id="d640b-134">A aplicação utiliza atualmente um gateway PayPal, implementado no *PayPalGateway.cs*.</span><span class="sxs-lookup"><span data-stu-id="d640b-134">The app currently uses a PayPal gateway, implemented in *PayPalGateway.cs*.</span></span>