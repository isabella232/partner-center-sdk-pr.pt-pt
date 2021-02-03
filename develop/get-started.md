---
title: Introdução
description: O Partner Center SDK inclui uma API gerida e uma API REST para os parceiros usarem para gerir dados de clientes, subscrição e encomenda.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9c2af1e11dbda19489a27e37c7f3de8ede90fd1c
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769056"
---
# <a name="get-started"></a><span data-ttu-id="5fc6c-103">Introdução</span><span class="sxs-lookup"><span data-stu-id="5fc6c-103">Get started</span></span>

<span data-ttu-id="5fc6c-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="5fc6c-104">**Applies To**</span></span>

- <span data-ttu-id="5fc6c-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="5fc6c-105">Partner Center</span></span>
- <span data-ttu-id="5fc6c-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="5fc6c-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="5fc6c-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="5fc6c-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="5fc6c-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5fc6c-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5fc6c-109">O Partner Center SDK inclui uma API gerida e uma API REST para os parceiros usarem para gerir dados de clientes, subscrição e encomenda.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-109">The Partner Center SDK includes a managed API and a REST API for partners to use to manage customer, subscription, and order data.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="5fc6c-110">Obter o código</span><span class="sxs-lookup"><span data-stu-id="5fc6c-110">Get the code</span></span>

[<span data-ttu-id="5fc6c-111">Descarregue o Partner Center SDK</span><span class="sxs-lookup"><span data-stu-id="5fc6c-111">Download the Partner Center SDK</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=746681)

> [!NOTE]
> <span data-ttu-id="5fc6c-112">O acesso da API ao Partner Center para revendedores indiretos não é um cenário suportado.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-112">API access to Partner Center for indirect resellers isn't a supported scenario.</span></span>

## <a name="determine-your-version-of-partner-center"></a><span data-ttu-id="5fc6c-113">Determine a sua versão do Partner Center</span><span class="sxs-lookup"><span data-stu-id="5fc6c-113">Determine your version of Partner Center</span></span>

<span data-ttu-id="5fc6c-114">Algumas versões do Partner Center não têm todo o SDK disponível.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-114">Some versions of Partner Center do not have the entire SDK available.</span></span> <span data-ttu-id="5fc6c-115">Para obter mais informações, consulte [Developing for Partner Center for Microsoft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md).</span><span class="sxs-lookup"><span data-stu-id="5fc6c-115">For more information, see [Developing for Partner Center for Microsoft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md).</span></span>

## <a name="get-the-samples"></a><span data-ttu-id="5fc6c-116">Pegue as amostras</span><span class="sxs-lookup"><span data-stu-id="5fc6c-116">Get the samples</span></span>

<span data-ttu-id="5fc6c-117">Para obter mais informações sobre os snippets C#, amostras DE REST e a aplicação da amostra, consulte [as amostras do Partner Center](partner-center-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5fc6c-117">For more information about C# snippets, REST samples, and the sample app, see [Partner Center samples](partner-center-samples.md).</span></span>

## <a name="test-vs-production"></a><span data-ttu-id="5fc6c-118">Teste vs. produção</span><span class="sxs-lookup"><span data-stu-id="5fc6c-118">Test vs. production</span></span>

<span data-ttu-id="5fc6c-119">Enquanto está inicialmente a escrever e a testar o seu código, deverá utilizar a sua conta de caixa de areia de integração (e os tokens correspondentes) para que não incorre acidentalmente em novas taxas que a sua empresa é responsável pelo pagamento.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-119">While you are initially writing and testing your code, you should use your integration sandbox account (and the corresponding tokens) so that you don't accidentally incur new charges that your company is responsible for paying.</span></span> <span data-ttu-id="5fc6c-120">Para obter mais informações sobre este ambiente de teste, consulte [Configurar o acesso a API no Partner Center.](set-up-api-access-in-partner-center.md)</span><span class="sxs-lookup"><span data-stu-id="5fc6c-120">For more information about this testing environment, see [Set up API access in Partner Center](set-up-api-access-in-partner-center.md).</span></span>

<span data-ttu-id="5fc6c-121">Quando a sua solução for testada e pronta a ser utilizada em contas reais de clientes, terá de atualizar as suas fichas para que esteja a utilizar uma aplicação de cliente AD Azure e segredo que corresponda à sua conta do Centro de Parceiros Primários.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-121">When your solution is tested and ready to use on real customer accounts, you'll have to update your tokens so that you're using an Azure AD client app and secret that correspond to your Primary Partner Center account.</span></span>

<span data-ttu-id="5fc6c-122">Para obter dicas e sugestões sobre testes e depurações, incluindo mais informações sobre o Test-in-Production (TiP) e a Caixa de Areia integração, consulte [Teste e depuragem](test-and-debug.md).</span><span class="sxs-lookup"><span data-stu-id="5fc6c-122">For tips and suggestions about testing and debugging, including more information about Test-in-Production (TiP) and the Integration Sandbox, see [Test and debug](test-and-debug.md).</span></span>

## <a name="configure-your-authentication"></a><span data-ttu-id="5fc6c-123">Configure a sua autenticação</span><span class="sxs-lookup"><span data-stu-id="5fc6c-123">Configure your authentication</span></span>

<span data-ttu-id="5fc6c-124">Para configurar a sua autenticação AZure AD para que possa utilizar as APIs do Centro Parceiro, consulte a [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5fc6c-124">To configure your Azure AD authentication so that you can use the Partner Center APIs, see [Partner Center authentication](partner-center-authentication.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fc6c-125">A Microsoft está a introduzir um quadro seguro e escalável para autenticar parceiros de soluções de nuvem (CSP) e fornecedores de painéis de controlo (CPV) através da arquitetura de autenticação multi-factor (MFA) do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-125">Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and control panel vendors (CPV) through the Microsoft Azure multi-factor authentication (MFA) architecture.</span></span>
<span data-ttu-id="5fc6c-126">O Partner Center utiliza o Azure AD para autenticação e para utilizar as APIs do Centro De Parceiros deve configurar corretamente as suas definições de autenticação.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-126">Partner Center uses Azure AD for authentication, and to use the Partner Center APIs you must configure your authentication settings correctly.</span></span>
>
> <span data-ttu-id="5fc6c-127">Para obter mais informações, consulte [Ativar o modelo de aplicação seguro.](enable-secure-app-model.md)</span><span class="sxs-lookup"><span data-stu-id="5fc6c-127">For more information, see [Enable secure application model](enable-secure-app-model.md).</span></span>

## <a name="get-help"></a><span data-ttu-id="5fc6c-128">Obter ajuda</span><span class="sxs-lookup"><span data-stu-id="5fc6c-128">Get help</span></span>

<span data-ttu-id="5fc6c-129">Os parceiros podem obter apoio no [grupo Partner Center SDK Yammer](https://go.microsoft.com/fwlink/p/?LinkID=717360).</span><span class="sxs-lookup"><span data-stu-id="5fc6c-129">Partners can get support at the [Partner Center SDK Yammer group](https://go.microsoft.com/fwlink/p/?LinkID=717360).</span></span> <span data-ttu-id="5fc6c-130">Para obter uma ajuda mais personalizada, os desenvolvedores podem usar os seus benefícios de suporte MPN ou Premier Support.</span><span class="sxs-lookup"><span data-stu-id="5fc6c-130">To get more personalized help, developers can use their MPN support benefits or Premier Support.</span></span>

## <a name="join-the-partner-center-api-and-sdk-early-adopter-program"></a><span data-ttu-id="5fc6c-131">Aderir ao Programa Early Adopter da API e SDK do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="5fc6c-131">Join the Partner Center API and SDK Early Adopter Program</span></span>

<span data-ttu-id="5fc6c-132">Para saber como pode colaborar com a Microsoft no desenvolvimento de funcionalidades e capacidades do Parceiro, consulte [o Programa de API e SDK Early Adopter](early-adopter-program.md)do Partner Center .</span><span class="sxs-lookup"><span data-stu-id="5fc6c-132">To find out how you can collaborate with Microsoft on the development of Partner features and capabilities, see [Join the Partner Center API and SDK Early Adopter Program](early-adopter-program.md).</span></span>
