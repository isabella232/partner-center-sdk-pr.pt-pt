---
title: Introdução
description: O Partner Center SDK inclui uma API gerida e uma API REST para os parceiros usarem para gerir dados de clientes, subscrição e encomenda.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b5d05f26d63574ef876519091dc1c33c05f36e25
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548758"
---
# <a name="get-started"></a><span data-ttu-id="16341-103">Introdução</span><span class="sxs-lookup"><span data-stu-id="16341-103">Get started</span></span>

<span data-ttu-id="16341-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="16341-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="16341-105">O Partner Center SDK inclui uma API gerida e uma API REST para os parceiros usarem para gerir dados de clientes, subscrição e encomenda.</span><span class="sxs-lookup"><span data-stu-id="16341-105">The Partner Center SDK includes a managed API and a REST API for partners to use to manage customer, subscription, and order data.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="16341-106">Obter o código</span><span class="sxs-lookup"><span data-stu-id="16341-106">Get the code</span></span>

[<span data-ttu-id="16341-107">Descarregue o Partner Center SDK</span><span class="sxs-lookup"><span data-stu-id="16341-107">Download the Partner Center SDK</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=746681)

> [!NOTE]
> <span data-ttu-id="16341-108">O acesso da API ao Partner Center para revendedores indiretos não é um cenário suportado.</span><span class="sxs-lookup"><span data-stu-id="16341-108">API access to Partner Center for indirect resellers isn't a supported scenario.</span></span>

## <a name="determine-your-version-of-partner-center"></a><span data-ttu-id="16341-109">Determine a sua versão do Partner Center</span><span class="sxs-lookup"><span data-stu-id="16341-109">Determine your version of Partner Center</span></span>

<span data-ttu-id="16341-110">Algumas versões do Partner Center não têm todo o SDK disponível.</span><span class="sxs-lookup"><span data-stu-id="16341-110">Some versions of Partner Center do not have the entire SDK available.</span></span> <span data-ttu-id="16341-111">Para obter mais informações, consulte [Developing for Partner Center for Microsoft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md).</span><span class="sxs-lookup"><span data-stu-id="16341-111">For more information, see [Developing for Partner Center for Microsoft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md).</span></span>

## <a name="get-the-samples"></a><span data-ttu-id="16341-112">Pegue as amostras</span><span class="sxs-lookup"><span data-stu-id="16341-112">Get the samples</span></span>

<span data-ttu-id="16341-113">Para obter mais informações sobre os snippets C#, amostras DE REST e a aplicação da amostra, consulte [as amostras do Partner Center](partner-center-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16341-113">For more information about C# snippets, REST samples, and the sample app, see [Partner Center samples](partner-center-samples.md).</span></span>

## <a name="test-vs-production"></a><span data-ttu-id="16341-114">Teste vs. produção</span><span class="sxs-lookup"><span data-stu-id="16341-114">Test vs. production</span></span>

<span data-ttu-id="16341-115">Enquanto está inicialmente a escrever e a testar o seu código, deverá utilizar a sua conta de caixa de areia de integração (e os tokens correspondentes) para que não incorre acidentalmente em novas taxas que a sua empresa é responsável pelo pagamento.</span><span class="sxs-lookup"><span data-stu-id="16341-115">While you are initially writing and testing your code, you should use your integration sandbox account (and the corresponding tokens) so that you don't accidentally incur new charges that your company is responsible for paying.</span></span> <span data-ttu-id="16341-116">Para obter mais informações sobre este ambiente de teste, consulte [Configurar o acesso a API no Partner Center.](set-up-api-access-in-partner-center.md)</span><span class="sxs-lookup"><span data-stu-id="16341-116">For more information about this testing environment, see [Set up API access in Partner Center](set-up-api-access-in-partner-center.md).</span></span>

<span data-ttu-id="16341-117">Quando a sua solução for testada e pronta a ser utilizada em contas reais de clientes, terá de atualizar as suas fichas para que esteja a utilizar uma aplicação de cliente AD Azure e segredo que corresponda à sua conta do Centro de Parceiros Primários.</span><span class="sxs-lookup"><span data-stu-id="16341-117">When your solution is tested and ready to use on real customer accounts, you'll have to update your tokens so that you're using an Azure AD client app and secret that correspond to your Primary Partner Center account.</span></span>

<span data-ttu-id="16341-118">Para obter dicas e sugestões sobre testes e depurações, incluindo mais informações sobre o Test-in-Production (TiP) e a Caixa de Areia integração, consulte [Teste e depuragem](test-and-debug.md).</span><span class="sxs-lookup"><span data-stu-id="16341-118">For tips and suggestions about testing and debugging, including more information about Test-in-Production (TiP) and the Integration Sandbox, see [Test and debug](test-and-debug.md).</span></span>

## <a name="configure-your-authentication"></a><span data-ttu-id="16341-119">Configure a sua autenticação</span><span class="sxs-lookup"><span data-stu-id="16341-119">Configure your authentication</span></span>

<span data-ttu-id="16341-120">Para configurar a sua autenticação AZure AD para que possa utilizar as APIs do Centro Parceiro, consulte a [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="16341-120">To configure your Azure AD authentication so that you can use the Partner Center APIs, see [Partner Center authentication](partner-center-authentication.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16341-121">A Microsoft está a introduzir um quadro seguro e escalável para autenticar parceiros de soluções de nuvem (CSP) e fornecedores de painéis de controlo (CPV) através da arquitetura de autenticação de vários fatores Microsoft Azure (MFA).</span><span class="sxs-lookup"><span data-stu-id="16341-121">Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and control panel vendors (CPV) through the Microsoft Azure multi-factor authentication (MFA) architecture.</span></span>
<span data-ttu-id="16341-122">O Partner Center utiliza o Azure AD para autenticação e para utilizar as APIs do Centro De Parceiros deve configurar corretamente as suas definições de autenticação.</span><span class="sxs-lookup"><span data-stu-id="16341-122">Partner Center uses Azure AD for authentication, and to use the Partner Center APIs you must configure your authentication settings correctly.</span></span>
>
> <span data-ttu-id="16341-123">Para obter mais informações, consulte [Ativar o modelo de aplicação seguro.](enable-secure-app-model.md)</span><span class="sxs-lookup"><span data-stu-id="16341-123">For more information, see [Enable secure application model](enable-secure-app-model.md).</span></span>

## <a name="get-help"></a><span data-ttu-id="16341-124">Obter ajuda</span><span class="sxs-lookup"><span data-stu-id="16341-124">Get help</span></span>

<span data-ttu-id="16341-125">Os parceiros podem obter apoio no [grupo de Yammer do Partner Center SDK](https://go.microsoft.com/fwlink/p/?LinkID=717360).</span><span class="sxs-lookup"><span data-stu-id="16341-125">Partners can get support at the [Partner Center SDK Yammer group](https://go.microsoft.com/fwlink/p/?LinkID=717360).</span></span> <span data-ttu-id="16341-126">Para obter uma ajuda mais personalizada, os desenvolvedores podem usar os seus benefícios de suporte MPN ou Premier Support.</span><span class="sxs-lookup"><span data-stu-id="16341-126">To get more personalized help, developers can use their MPN support benefits or Premier Support.</span></span>

## <a name="join-the-partner-center-api-and-sdk-early-adopter-program"></a><span data-ttu-id="16341-127">Aderir ao Programa Early Adopter da API e SDK do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="16341-127">Join the Partner Center API and SDK Early Adopter Program</span></span>

<span data-ttu-id="16341-128">Para saber como pode colaborar com a Microsoft no desenvolvimento de funcionalidades e capacidades do Parceiro, consulte [o Programa de API e SDK Early Adopter](early-adopter-program.md)do Partner Center .</span><span class="sxs-lookup"><span data-stu-id="16341-128">To find out how you can collaborate with Microsoft on the development of Partner features and capabilities, see [Join the Partner Center API and SDK Early Adopter Program](early-adopter-program.md).</span></span>
