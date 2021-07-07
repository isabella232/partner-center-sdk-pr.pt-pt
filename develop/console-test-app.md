---
title: Aplicação de teste da consola
description: Esta aplicação de teste de consola fornece código de amostra para todos os cenários suportados pelas APIs do Partner Center. Também pode usá-lo para testar.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b35167104deeede50107d59fca6112c10dc7b4bf
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974034"
---
# <a name="console-test-app"></a><span data-ttu-id="18910-104">Aplicação de teste da consola</span><span class="sxs-lookup"><span data-stu-id="18910-104">Console test app</span></span>

<span data-ttu-id="18910-105">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="18910-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="18910-106">A aplicação de teste de consola é fornecida em C# e Java, fornece códigos de amostra para todos os cenários suportados pelas APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="18910-106">The console test app is provided in C# and Java, it provides sample codes for all of the scenarios supported by the Partner Center APIs.</span></span> <span data-ttu-id="18910-107">Também pode usá-lo para testar.</span><span class="sxs-lookup"><span data-stu-id="18910-107">You can also use it for testing.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="18910-108">Obter o código</span><span class="sxs-lookup"><span data-stu-id="18910-108">Get the code</span></span>

<span data-ttu-id="18910-109">Descarregue o código de amostra para a aplicação de teste da consola.</span><span class="sxs-lookup"><span data-stu-id="18910-109">Download the sample code for the console test app.</span></span>

## <a name="net"></a><span data-ttu-id="18910-110">.NET</span><span class="sxs-lookup"><span data-stu-id="18910-110">.NET</span></span>

<span data-ttu-id="18910-111">[Descarregue o código de amostra](https://go.microsoft.com/fwlink/p/?LinkId=746682) e modifique-o conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="18910-111">[Download the sample code](https://go.microsoft.com/fwlink/p/?LinkId=746682) and modify it as necessary.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18910-112">Antes de construir a aplicação, atualize os valores no ficheiro *App.config* para refletir a informação de autenticação AD AZure que criou na [autenticação do Partner Center.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="18910-112">Before you build the application, update the values in the *App.config* file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="18910-113">Especificamente, deve utilizar as definições da sua conta de caixa de areia de integração durante o desenvolvimento precoce ou para testar na produção.</span><span class="sxs-lookup"><span data-stu-id="18910-113">Specifically, you should use your integration sandbox account settings during early development or for testing in production.</span></span>

<span data-ttu-id="18910-114">De **acordo com os cenários,** os *App.config* ficheiros, pode definir parâmetros que serão automaticamente transmitidos para os cenários que executou.</span><span class="sxs-lookup"><span data-stu-id="18910-114">Under **ScenarioSettings** in the *App.config* file, you can set parameters that will be automatically passed into the scenarios that you run.</span></span>

<span data-ttu-id="18910-115">Para modificar a lista de cenários que são executados, comente linhas no **IPartnerScenario \[ \] mainScenarios** ou num método individual **Get Scenarios** encontrado no ficheiro *.cs Programa.*</span><span class="sxs-lookup"><span data-stu-id="18910-115">To modify the list of scenarios that are run, comment out lines in **IPartnerScenario\[\] mainScenarios** or in an individual **Get Scenarios** method found in the *Program.cs* file.</span></span>

## <a name="java"></a><span data-ttu-id="18910-116">Java</span><span class="sxs-lookup"><span data-stu-id="18910-116">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="18910-117">[Descarregue o código de amostra](https://go.microsoft.com/fwlink/p/?LinkId=2026887) e modifique-o conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="18910-117">[Download the sample code](https://go.microsoft.com/fwlink/p/?LinkId=2026887) and modify it as necessary.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18910-118">Antes de construir a aplicação, atualize os valores no *SamplesConfigurations.jsno* ficheiro para refletir a informação de autenticação AD AZure que criou na [autenticação do Partner Center.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="18910-118">Before you build the application, update the values in the *SamplesConfigurations.json* file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="18910-119">Especificamente, deve utilizar as definições da sua conta de caixa de areia de integração durante o desenvolvimento precoce ou para testar na produção.</span><span class="sxs-lookup"><span data-stu-id="18910-119">Specifically, you should use your integration sandbox account settings during early development or for testing in production.</span></span>

<span data-ttu-id="18910-120">Nos **cenários As definições** no *SamplesConfiguration.jsno* ficheiro, pode definir parâmetros que serão automaticamente transmitidos para os cenários que executou.</span><span class="sxs-lookup"><span data-stu-id="18910-120">Under **ScenarioSettings** in the *SamplesConfiguration.json* file, you can set parameters that will be automatically passed into the scenarios that you run.</span></span>

<span data-ttu-id="18910-121">Para modificar a lista de cenários que são executados, comente linhas no **iPartnerScenario \[ \] mainScenarios** ou num método individual **Get Scenarios** encontrado no ficheiro *.java Programa.*</span><span class="sxs-lookup"><span data-stu-id="18910-121">To modify the list of scenarios that are run, comment out lines in **IPartnerScenario\[\] mainScenarios** or in an individual **Get Scenarios** method found in the *Program.java* file.</span></span>

## <a name="what-to-change"></a><span data-ttu-id="18910-122">O que mudar</span><span class="sxs-lookup"><span data-stu-id="18910-122">What to change</span></span>

<span data-ttu-id="18910-123">Utilize as seguintes listas para determinar o que alterar ou não no código de amostra.</span><span class="sxs-lookup"><span data-stu-id="18910-123">Use the following lists to determine what to change or not change in the sample code.</span></span>

### <a name="partnerservicesettings"></a><span data-ttu-id="18910-124">PartnerServiceSettings</span><span class="sxs-lookup"><span data-stu-id="18910-124">PartnerServiceSettings</span></span>

<span data-ttu-id="18910-125">Para **PartnerServiceSettings,** não mude:</span><span class="sxs-lookup"><span data-stu-id="18910-125">For **PartnerServiceSettings**, don't change:</span></span>

- <span data-ttu-id="18910-126">**PartnerServiceApiEndpoint**</span><span class="sxs-lookup"><span data-stu-id="18910-126">**PartnerServiceApiEndpoint**</span></span>
- <span data-ttu-id="18910-127">**AutenticaçãoAuthorityEndpoint**</span><span class="sxs-lookup"><span data-stu-id="18910-127">**AuthenticationAuthorityEndpoint**</span></span>
- <span data-ttu-id="18910-128">**Ponto de GraphEndpoint**</span><span class="sxs-lookup"><span data-stu-id="18910-128">**GraphEndpoint**</span></span>
- <span data-ttu-id="18910-129">**CommonDomain**</span><span class="sxs-lookup"><span data-stu-id="18910-129">**CommonDomain**</span></span>

<span data-ttu-id="18910-130">Todas estas definições são necessárias para que as chamadas de API da amostra funcionem corretamente.</span><span class="sxs-lookup"><span data-stu-id="18910-130">All of these settings are necessary for the sample API calls to properly function.</span></span>

### <a name="userauthentication"></a><span data-ttu-id="18910-131">UtilizadoresAuferição</span><span class="sxs-lookup"><span data-stu-id="18910-131">UserAuthentication</span></span>

<span data-ttu-id="18910-132">Para a Concessão de **Privacidade do Utilizador,** é-lhe exigido que altere:</span><span class="sxs-lookup"><span data-stu-id="18910-132">For **UserAuthentication**, you're required to change:</span></span>

- <span data-ttu-id="18910-133">**ApplicationId** (o seu ID de aplicação Azure Ative Directory utilizado para login)</span><span class="sxs-lookup"><span data-stu-id="18910-133">**ApplicationId** (your Azure Active Directory application ID used for login)</span></span>
- <span data-ttu-id="18910-134">**Nome do Utilizador** (o seu nome de utilizador de diretório ativo)</span><span class="sxs-lookup"><span data-stu-id="18910-134">**UserName** (your active directory username)</span></span>
- <span data-ttu-id="18910-135">**Palavra-passe** (a sua senha de diretório ativa).</span><span class="sxs-lookup"><span data-stu-id="18910-135">**Password** (your active directory password).</span></span>

<span data-ttu-id="18910-136">Não mude:</span><span class="sxs-lookup"><span data-stu-id="18910-136">Don't change:</span></span>

- <span data-ttu-id="18910-137">**ResourceUrl**</span><span class="sxs-lookup"><span data-stu-id="18910-137">**ResourceUrl**</span></span>
- <span data-ttu-id="18910-138">**RedirectUrl**</span><span class="sxs-lookup"><span data-stu-id="18910-138">**RedirectUrl**</span></span>

### <a name="appauthentication"></a><span data-ttu-id="18910-139">AppAuthentication</span><span class="sxs-lookup"><span data-stu-id="18910-139">AppAuthentication</span></span>

<span data-ttu-id="18910-140">Para **a AppAuthentication,** é obrigado a alterar:</span><span class="sxs-lookup"><span data-stu-id="18910-140">For **AppAuthentication**, you're required to change:</span></span>

- <span data-ttu-id="18910-141">**ApplicationId** (o ID da sua aplicação de diretório ativo usado para login de aplicações)</span><span class="sxs-lookup"><span data-stu-id="18910-141">**ApplicationId** (your active directory application ID used for application login)</span></span>
- <span data-ttu-id="18910-142">**ApplicationSecret** (o segredo da sua aplicação de diretório ativo usado para login de aplicações)</span><span class="sxs-lookup"><span data-stu-id="18910-142">**ApplicationSecret** (your active directory application secret used for application login)</span></span>
- <span data-ttu-id="18910-143">**Domínio** (o seu domínio de diretório ativo no qual a aplicação está hospedada)</span><span class="sxs-lookup"><span data-stu-id="18910-143">**Domain** (your active directory domain on which the application is hosted)</span></span>

### <a name="scenariosettings"></a><span data-ttu-id="18910-144">CenárioS</span><span class="sxs-lookup"><span data-stu-id="18910-144">ScenarioSettings</span></span>

<span data-ttu-id="18910-145">Para **cenáriosSettings,** não mude:</span><span class="sxs-lookup"><span data-stu-id="18910-145">For **ScenarioSettings**, don't change:</span></span>

- <span data-ttu-id="18910-146">**CustomerDomainS sufixo** (o sufixo de domínio utilizado na criação de um novo cliente)</span><span class="sxs-lookup"><span data-stu-id="18910-146">**CustomerDomainSuffix** (the domain suffix used when creating a new customer)</span></span>

<span data-ttu-id="18910-147">Definições opcionais.</span><span class="sxs-lookup"><span data-stu-id="18910-147">Optional settings.</span></span> <span data-ttu-id="18910-148">Se deixada em branco, esta informação terá de ser inserida quando executar um cenário, se necessário):</span><span class="sxs-lookup"><span data-stu-id="18910-148">If left blank, this information will need to be inputted when running a scenario where necessary):</span></span>

- <span data-ttu-id="18910-149">**CustomerIdToDelete** (o ID do cliente utilizado para a eliminação)</span><span class="sxs-lookup"><span data-stu-id="18910-149">**CustomerIdToDelete** (the ID of the customer used for deletion)</span></span>
- <span data-ttu-id="18910-150">**Predefinição DeCustomerId** (o ID do cliente para utilizar em cenários relacionados com o cliente)</span><span class="sxs-lookup"><span data-stu-id="18910-150">**DefaultCustomerId** (the customer ID to use in customer-related scenarios)</span></span>
- <span data-ttu-id="18910-151">**DefaultInvoiceID** (o ID da fatura a utilizar em cenários de fatura)</span><span class="sxs-lookup"><span data-stu-id="18910-151">**DefaultInvoiceID** (the invoice ID to use in invoice scenarios)</span></span>
- <span data-ttu-id="18910-152">**PartnerMpnId** (o parceiro MPN ID para usar em cenários de parceiros indiretos)</span><span class="sxs-lookup"><span data-stu-id="18910-152">**PartnerMpnId** (the partner MPN ID to use in indirect partner scenarios)</span></span>
- <span data-ttu-id="18910-153">**DefaultServiceRequestId** (o ID de pedido de serviço para usar em cenários de pedido de serviço)</span><span class="sxs-lookup"><span data-stu-id="18910-153">**DefaultServiceRequestId** (the service request ID to use in service request scenarios)</span></span>
- <span data-ttu-id="18910-154">**DefaultSupportTopicID** (o ID tópico de suporte a utilizar em cenários de pedido de serviço)</span><span class="sxs-lookup"><span data-stu-id="18910-154">**DefaultSupportTopicID** (the support topic ID to use in service request scenarios)</span></span>
- <span data-ttu-id="18910-155">**DefaultOfferID** (o ID de oferta para usar em cenários de oferta)</span><span class="sxs-lookup"><span data-stu-id="18910-155">**DefaultOfferID** (the offer ID to use in offer scenarios)</span></span>
- <span data-ttu-id="18910-156">**PredefiniçãoOrderID** (o ID de encomenda a ser utilizado em cenários de ordem)</span><span class="sxs-lookup"><span data-stu-id="18910-156">**DefaultOrderID** (the order ID to use in order scenarios)</span></span>
- <span data-ttu-id="18910-157">**DefaultSubscriptionID** (o ID de subscrição a utilizar em cenários de subscrição)</span><span class="sxs-lookup"><span data-stu-id="18910-157">**DefaultSubscriptionID** (the subscription ID to use in subscription scenarios)</span></span>

<span data-ttu-id="18910-158">Opcional para mudar.</span><span class="sxs-lookup"><span data-stu-id="18910-158">Optional to change.</span></span> <span data-ttu-id="18910-159">Todas estas definições especificam a quantidade de entradas por página ao recuperar o conteúdo paged:</span><span class="sxs-lookup"><span data-stu-id="18910-159">All of these settings specify the amount of entries per page when retrieving paged content:</span></span>

- <span data-ttu-id="18910-160">**CustomerPageSize**</span><span class="sxs-lookup"><span data-stu-id="18910-160">**CustomerPageSize**</span></span>
- <span data-ttu-id="18910-161">**FaturaSagensSize**</span><span class="sxs-lookup"><span data-stu-id="18910-161">**InvoicePageSize**</span></span>
- <span data-ttu-id="18910-162">**ServiceRequestPageSize**</span><span class="sxs-lookup"><span data-stu-id="18910-162">**ServiceRequestPageSize**</span></span>
- <span data-ttu-id="18910-163">**DefaultOffofferPageSize**</span><span class="sxs-lookup"><span data-stu-id="18910-163">**DefaultOfferPageSize**</span></span>
- <span data-ttu-id="18910-164">**SubscriçãoPagesize**</span><span class="sxs-lookup"><span data-stu-id="18910-164">**SubscriptionPageSize**</span></span>
