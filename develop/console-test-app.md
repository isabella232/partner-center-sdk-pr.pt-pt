---
title: Aplicação de teste da consola
description: Esta aplicação de teste de consola fornece código de amostra para todos os cenários suportados pelas APIs do Partner Center. Também pode usá-lo para testar.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e82bac3ccc22d0e7cf898e5b2d2e002c622584ae
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769181"
---
# <a name="console-test-app"></a><span data-ttu-id="ecad6-104">Aplicação de teste da consola</span><span class="sxs-lookup"><span data-stu-id="ecad6-104">Console test app</span></span>

<span data-ttu-id="ecad6-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="ecad6-105">**Applies to:**</span></span>

- <span data-ttu-id="ecad6-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="ecad6-106">Partner Center</span></span>
- <span data-ttu-id="ecad6-107">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="ecad6-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="ecad6-108">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="ecad6-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="ecad6-109">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ecad6-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ecad6-110">A aplicação de teste de consola é fornecida em C# e Java, fornece códigos de amostra para todos os cenários suportados pelas APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="ecad6-110">The console test app is provided in C# and Java, it provides sample codes for all of the scenarios supported by the Partner Center APIs.</span></span> <span data-ttu-id="ecad6-111">Também pode usá-lo para testar.</span><span class="sxs-lookup"><span data-stu-id="ecad6-111">You can also use it for testing.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="ecad6-112">Obter o código</span><span class="sxs-lookup"><span data-stu-id="ecad6-112">Get the code</span></span>

<span data-ttu-id="ecad6-113">Descarregue o código de amostra para a aplicação de teste da consola.</span><span class="sxs-lookup"><span data-stu-id="ecad6-113">Download the sample code for the console test app.</span></span>

## <a name="net"></a><span data-ttu-id="ecad6-114">.NET</span><span class="sxs-lookup"><span data-stu-id="ecad6-114">.NET</span></span>

<span data-ttu-id="ecad6-115">[Descarregue o código de amostra](https://go.microsoft.com/fwlink/p/?LinkId=746682) e modifique-o conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="ecad6-115">[Download the sample code](https://go.microsoft.com/fwlink/p/?LinkId=746682) and modify it as necessary.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ecad6-116">Antes de construir a aplicação, atualize os valores no ficheiro *App.config* para refletir a informação de autenticação AD AZure que criou na [autenticação do Partner Center.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="ecad6-116">Before you build the application, update the values in the *App.config* file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ecad6-117">Especificamente, deve utilizar as definições da sua conta de caixa de areia de integração durante o desenvolvimento precoce ou para testar na produção.</span><span class="sxs-lookup"><span data-stu-id="ecad6-117">Specifically, you should use your integration sandbox account settings during early development or for testing in production.</span></span>

<span data-ttu-id="ecad6-118">De **acordo com os cenários,** os *App.config* ficheiros, pode definir parâmetros que serão automaticamente transmitidos para os cenários que executou.</span><span class="sxs-lookup"><span data-stu-id="ecad6-118">Under **ScenarioSettings** in the *App.config* file, you can set parameters that will be automatically passed into the scenarios that you run.</span></span>

<span data-ttu-id="ecad6-119">Para modificar a lista de cenários que são executados, comente linhas no **IPartnerScenario \[ \] mainScenarios** ou num método individual **Get Scenarios** encontrado no ficheiro *Program.cs.*</span><span class="sxs-lookup"><span data-stu-id="ecad6-119">To modify the list of scenarios that are run, comment out lines in **IPartnerScenario\[\] mainScenarios** or in an individual **Get Scenarios** method found in the *Program.cs* file.</span></span>

## <a name="java"></a><span data-ttu-id="ecad6-120">Java</span><span class="sxs-lookup"><span data-stu-id="ecad6-120">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="ecad6-121">[Descarregue o código de amostra](https://go.microsoft.com/fwlink/p/?LinkId=2026887) e modifique-o conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="ecad6-121">[Download the sample code](https://go.microsoft.com/fwlink/p/?LinkId=2026887) and modify it as necessary.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ecad6-122">Antes de construir a aplicação, atualize os valores no *SamplesConfigurations.jsno* ficheiro para refletir a informação de autenticação AD AZure que criou na [autenticação do Partner Center.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="ecad6-122">Before you build the application, update the values in the *SamplesConfigurations.json* file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ecad6-123">Especificamente, deve utilizar as definições da sua conta de caixa de areia de integração durante o desenvolvimento precoce ou para testar na produção.</span><span class="sxs-lookup"><span data-stu-id="ecad6-123">Specifically, you should use your integration sandbox account settings during early development or for testing in production.</span></span>

<span data-ttu-id="ecad6-124">Nos **cenários As definições** no *SamplesConfiguration.jsno* ficheiro, pode definir parâmetros que serão automaticamente transmitidos para os cenários que executou.</span><span class="sxs-lookup"><span data-stu-id="ecad6-124">Under **ScenarioSettings** in the *SamplesConfiguration.json* file, you can set parameters that will be automatically passed into the scenarios that you run.</span></span>

<span data-ttu-id="ecad6-125">Para modificar a lista de cenários que são executados, comente linhas no **iPartnerScenario \[ \] mainScenarios** ou num método individual **Get Scenarios** encontrado no ficheiro *.java Programa.*</span><span class="sxs-lookup"><span data-stu-id="ecad6-125">To modify the list of scenarios that are run, comment out lines in **IPartnerScenario\[\] mainScenarios** or in an individual **Get Scenarios** method found in the *Program.java* file.</span></span>

## <a name="what-to-change"></a><span data-ttu-id="ecad6-126">O que mudar</span><span class="sxs-lookup"><span data-stu-id="ecad6-126">What to change</span></span>

<span data-ttu-id="ecad6-127">Utilize as seguintes listas para determinar o que alterar ou não no código de amostra.</span><span class="sxs-lookup"><span data-stu-id="ecad6-127">Use the following lists to determine what to change or not change in the sample code.</span></span>

### <a name="partnerservicesettings"></a><span data-ttu-id="ecad6-128">PartnerServiceSettings</span><span class="sxs-lookup"><span data-stu-id="ecad6-128">PartnerServiceSettings</span></span>

<span data-ttu-id="ecad6-129">Para **PartnerServiceSettings,** não mude:</span><span class="sxs-lookup"><span data-stu-id="ecad6-129">For **PartnerServiceSettings**, don't change:</span></span>

- <span data-ttu-id="ecad6-130">**PartnerServiceApiEndpoint**</span><span class="sxs-lookup"><span data-stu-id="ecad6-130">**PartnerServiceApiEndpoint**</span></span>
- <span data-ttu-id="ecad6-131">**AutenticaçãoAuthorityEndpoint**</span><span class="sxs-lookup"><span data-stu-id="ecad6-131">**AuthenticationAuthorityEndpoint**</span></span>
- <span data-ttu-id="ecad6-132">**Ponto de GraphEndpoint**</span><span class="sxs-lookup"><span data-stu-id="ecad6-132">**GraphEndpoint**</span></span>
- <span data-ttu-id="ecad6-133">**CommonDomain**</span><span class="sxs-lookup"><span data-stu-id="ecad6-133">**CommonDomain**</span></span>

<span data-ttu-id="ecad6-134">Todas estas definições são necessárias para que as chamadas de API da amostra funcionem corretamente.</span><span class="sxs-lookup"><span data-stu-id="ecad6-134">All of these settings are necessary for the sample API calls to properly function.</span></span>

### <a name="userauthentication"></a><span data-ttu-id="ecad6-135">UtilizadoresAuferição</span><span class="sxs-lookup"><span data-stu-id="ecad6-135">UserAuthentication</span></span>

<span data-ttu-id="ecad6-136">Para a Concessão de **Privacidade do Utilizador,** é-lhe exigido que altere:</span><span class="sxs-lookup"><span data-stu-id="ecad6-136">For **UserAuthentication**, you're required to change:</span></span>

- <span data-ttu-id="ecad6-137">**ApplicationId** (o seu ID de aplicação Azure Ative Directory usado para login)</span><span class="sxs-lookup"><span data-stu-id="ecad6-137">**ApplicationId** (your Azure Active Directory application ID used for login)</span></span>
- <span data-ttu-id="ecad6-138">**Nome do Utilizador** (o seu nome de utilizador de diretório ativo)</span><span class="sxs-lookup"><span data-stu-id="ecad6-138">**UserName** (your active directory username)</span></span>
- <span data-ttu-id="ecad6-139">**Palavra-passe** (a sua senha de diretório ativa).</span><span class="sxs-lookup"><span data-stu-id="ecad6-139">**Password** (your active directory password).</span></span>

<span data-ttu-id="ecad6-140">Não mude:</span><span class="sxs-lookup"><span data-stu-id="ecad6-140">Don't change:</span></span>

- <span data-ttu-id="ecad6-141">**ResourceUrl**</span><span class="sxs-lookup"><span data-stu-id="ecad6-141">**ResourceUrl**</span></span>
- <span data-ttu-id="ecad6-142">**RedirectUrl**</span><span class="sxs-lookup"><span data-stu-id="ecad6-142">**RedirectUrl**</span></span>

### <a name="appauthentication"></a><span data-ttu-id="ecad6-143">AppAuthentication</span><span class="sxs-lookup"><span data-stu-id="ecad6-143">AppAuthentication</span></span>

<span data-ttu-id="ecad6-144">Para **a AppAuthentication,** é obrigado a alterar:</span><span class="sxs-lookup"><span data-stu-id="ecad6-144">For **AppAuthentication**, you're required to change:</span></span>

- <span data-ttu-id="ecad6-145">**ApplicationId** (o ID da sua aplicação de diretório ativo usado para login de aplicações)</span><span class="sxs-lookup"><span data-stu-id="ecad6-145">**ApplicationId** (your active directory application ID used for application login)</span></span>
- <span data-ttu-id="ecad6-146">**ApplicationSecret** (o segredo da sua aplicação de diretório ativo usado para login de aplicações)</span><span class="sxs-lookup"><span data-stu-id="ecad6-146">**ApplicationSecret** (your active directory application secret used for application login)</span></span>
- <span data-ttu-id="ecad6-147">**Domínio** (o seu domínio de diretório ativo no qual a aplicação está hospedada)</span><span class="sxs-lookup"><span data-stu-id="ecad6-147">**Domain** (your active directory domain on which the application is hosted)</span></span>

### <a name="scenariosettings"></a><span data-ttu-id="ecad6-148">CenárioS</span><span class="sxs-lookup"><span data-stu-id="ecad6-148">ScenarioSettings</span></span>

<span data-ttu-id="ecad6-149">Para **cenáriosSettings,** não mude:</span><span class="sxs-lookup"><span data-stu-id="ecad6-149">For **ScenarioSettings**, don't change:</span></span>

- <span data-ttu-id="ecad6-150">**CustomerDomainS sufixo** (o sufixo de domínio utilizado na criação de um novo cliente)</span><span class="sxs-lookup"><span data-stu-id="ecad6-150">**CustomerDomainSuffix** (the domain suffix used when creating a new customer)</span></span>

<span data-ttu-id="ecad6-151">Definições opcionais.</span><span class="sxs-lookup"><span data-stu-id="ecad6-151">Optional settings.</span></span> <span data-ttu-id="ecad6-152">Se deixada em branco, esta informação terá de ser inserida quando executar um cenário, se necessário):</span><span class="sxs-lookup"><span data-stu-id="ecad6-152">If left blank, this information will need to be inputted when running a scenario where necessary):</span></span>

- <span data-ttu-id="ecad6-153">**CustomerIdToDelete** (o ID do cliente utilizado para a eliminação)</span><span class="sxs-lookup"><span data-stu-id="ecad6-153">**CustomerIdToDelete** (the ID of the customer used for deletion)</span></span>
- <span data-ttu-id="ecad6-154">**Predefinição DeCustomerId** (o ID do cliente para utilizar em cenários relacionados com o cliente)</span><span class="sxs-lookup"><span data-stu-id="ecad6-154">**DefaultCustomerId** (the customer ID to use in customer-related scenarios)</span></span>
- <span data-ttu-id="ecad6-155">**DefaultInvoiceID** (o ID da fatura a utilizar em cenários de fatura)</span><span class="sxs-lookup"><span data-stu-id="ecad6-155">**DefaultInvoiceID** (the invoice ID to use in invoice scenarios)</span></span>
- <span data-ttu-id="ecad6-156">**PartnerMpnId** (o parceiro MPN ID para usar em cenários de parceiros indiretos)</span><span class="sxs-lookup"><span data-stu-id="ecad6-156">**PartnerMpnId** (the partner MPN ID to use in indirect partner scenarios)</span></span>
- <span data-ttu-id="ecad6-157">**DefaultServiceRequestId** (o ID de pedido de serviço para usar em cenários de pedido de serviço)</span><span class="sxs-lookup"><span data-stu-id="ecad6-157">**DefaultServiceRequestId** (the service request ID to use in service request scenarios)</span></span>
- <span data-ttu-id="ecad6-158">**DefaultSupportTopicID** (o ID tópico de suporte a utilizar em cenários de pedido de serviço)</span><span class="sxs-lookup"><span data-stu-id="ecad6-158">**DefaultSupportTopicID** (the support topic ID to use in service request scenarios)</span></span>
- <span data-ttu-id="ecad6-159">**DefaultOfferID** (o ID de oferta para usar em cenários de oferta)</span><span class="sxs-lookup"><span data-stu-id="ecad6-159">**DefaultOfferID** (the offer ID to use in offer scenarios)</span></span>
- <span data-ttu-id="ecad6-160">**PredefiniçãoOrderID** (o ID de encomenda a ser utilizado em cenários de ordem)</span><span class="sxs-lookup"><span data-stu-id="ecad6-160">**DefaultOrderID** (the order ID to use in order scenarios)</span></span>
- <span data-ttu-id="ecad6-161">**DefaultSubscriptionID** (o ID de subscrição a utilizar em cenários de subscrição)</span><span class="sxs-lookup"><span data-stu-id="ecad6-161">**DefaultSubscriptionID** (the subscription ID to use in subscription scenarios)</span></span>

<span data-ttu-id="ecad6-162">Opcional para mudar.</span><span class="sxs-lookup"><span data-stu-id="ecad6-162">Optional to change.</span></span> <span data-ttu-id="ecad6-163">Todas estas definições especificam a quantidade de entradas por página ao recuperar o conteúdo paged:</span><span class="sxs-lookup"><span data-stu-id="ecad6-163">All of these settings specify the amount of entries per page when retrieving paged content:</span></span>

- <span data-ttu-id="ecad6-164">**CustomerPageSize**</span><span class="sxs-lookup"><span data-stu-id="ecad6-164">**CustomerPageSize**</span></span>
- <span data-ttu-id="ecad6-165">**FaturaSagensSize**</span><span class="sxs-lookup"><span data-stu-id="ecad6-165">**InvoicePageSize**</span></span>
- <span data-ttu-id="ecad6-166">**ServiceRequestPageSize**</span><span class="sxs-lookup"><span data-stu-id="ecad6-166">**ServiceRequestPageSize**</span></span>
- <span data-ttu-id="ecad6-167">**DefaultOffofferPageSize**</span><span class="sxs-lookup"><span data-stu-id="ecad6-167">**DefaultOfferPageSize**</span></span>
- <span data-ttu-id="ecad6-168">**SubscriçãoPagesize**</span><span class="sxs-lookup"><span data-stu-id="ecad6-168">**SubscriptionPageSize**</span></span>
