---
title: Registar detalhes da aplicação para Partner Center para Microsoft National Cloud
description: Saiba como e por que os desenvolvedores de aplicativos para Partner Center para a Microsoft National Cloud devem registar detalhes sobre a sua aplicação com Azure AD através do portal Azure.
MS-HAID:
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_cloud\_germany
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_national\_clouds
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 93d46a17bc26e9586e5e773bdf934653a571367f
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973456"
---
# <a name="register-app-details-for-partner-center-for-microsoft-national-cloud-through-the-azure-portal"></a><span data-ttu-id="2825b-103">Registar detalhes da aplicação para Partner Center para a Microsoft National Cloud através do portal Azure</span><span class="sxs-lookup"><span data-stu-id="2825b-103">Register app details for Partner Center for Microsoft National Cloud through the Azure portal</span></span>

<span data-ttu-id="2825b-104">**Aplica-se a**: Partner Center for Microsoft Cloud Germany | Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2825b-104">**Applies to**: Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2825b-105">Os desenvolvedores devem registar detalhes sobre a sua aplicação com Azure AD através do portal Azure.</span><span class="sxs-lookup"><span data-stu-id="2825b-105">Developers must register details about their app with Azure AD through the Azure portal.</span></span> <span data-ttu-id="2825b-106">Isto ajuda a garantir que apenas as aplicações especificadas são capazes de se conectar aos dados do parceiro e do cliente.</span><span class="sxs-lookup"><span data-stu-id="2825b-106">This helps ensure that only specified apps are able to connect to partner and customer data.</span></span>

<span data-ttu-id="2825b-107">Para o Partner Center for Microsoft Cloud for US Government, atualmente tem de gerir aplicações através do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2825b-107">For Partner Center for Microsoft Cloud for US Government, you currently must manage apps through PowerShell.</span></span> <span data-ttu-id="2825b-108">Para mais informações, consulte a [documentação de referência Azure PowerShell.](/powershell/module/Azuread/#applications)</span><span class="sxs-lookup"><span data-stu-id="2825b-108">For more information, see the [Azure PowerShell reference documentation](/powershell/module/Azuread/#applications).</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="2825b-109">Esteja ciente dos seguintes requisitos adicionais quando criar uma aplicação para Partner Center para Microsoft Cloud Germany ou Partner Center for Microsoft Cloud for US Government.</span><span class="sxs-lookup"><span data-stu-id="2825b-109">Be aware of the following additional requirements when you create an app for Partner Center for Microsoft Cloud Germany or Partner Center for Microsoft Cloud for US Government.</span></span>

## <a name="web-apps"></a><span data-ttu-id="2825b-110">Web Apps</span><span class="sxs-lookup"><span data-stu-id="2825b-110">Web apps</span></span>

<span data-ttu-id="2825b-111">Para aplicações web, utilize os seguintes procedimentos para registar o seu ID de aplicação.</span><span class="sxs-lookup"><span data-stu-id="2825b-111">For web apps, use the following procedures to register your application ID.</span></span>

### <a name="create-or-update-web-app"></a><span data-ttu-id="2825b-112">Criar ou atualizar aplicativo web</span><span class="sxs-lookup"><span data-stu-id="2825b-112">Create or update web app</span></span>

1. <span data-ttu-id="2825b-113">Navegue para o [portal Azure - Página de registos de aplicações](https://go.microsoft.com/fwlink/?linkid=2083908) para registar a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="2825b-113">Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app.</span></span> <span data-ttu-id="2825b-114">Inicie sessão no portal do Azure com uma conta profissional ou escolar ou uma conta pessoal da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2825b-114">Sign in to the Azure portal using either a work or school account or a personal Microsoft account.</span></span>

2. <span data-ttu-id="2825b-115">Selecione **Novo registo**.</span><span class="sxs-lookup"><span data-stu-id="2825b-115">Select **New registration**.</span></span> <span data-ttu-id="2825b-116">Para mais informações, consulte [Quickstart: Registe uma aplicação com o plataforma de identidades da Microsoft](/azure/active-directory/develop/quickstart-register-app).</span><span class="sxs-lookup"><span data-stu-id="2825b-116">For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).</span></span>

### <a name="configure-api-access-permissions-for-web-app"></a><span data-ttu-id="2825b-117">Configure permissões de acesso da API para aplicação web</span><span class="sxs-lookup"><span data-stu-id="2825b-117">Configure API access permissions for web app</span></span>

1. <span data-ttu-id="2825b-118">Escolha a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="2825b-118">Choose your app.</span></span> <span data-ttu-id="2825b-119">Vá a **Definições** da aplicação Web.</span><span class="sxs-lookup"><span data-stu-id="2825b-119">Go to **Settings** of the Web app.</span></span>

2. <span data-ttu-id="2825b-120">Na secção **de Acesso API,** escolha **permissões necessárias**</span><span class="sxs-lookup"><span data-stu-id="2825b-120">In **API Access** section, choose **Required permissions**</span></span>

3. <span data-ttu-id="2825b-121">Para Windows permissões de diretório Azure Ative:</span><span class="sxs-lookup"><span data-stu-id="2825b-121">For Windows Azure Active directory permissions:</span></span>

    1. <span data-ttu-id="2825b-122">Escolha **permissões Windows Azure Ative Directory.**</span><span class="sxs-lookup"><span data-stu-id="2825b-122">Choose **Windows Azure Active Directory permissions**.</span></span>

    2. <span data-ttu-id="2825b-123">Nas **permissões de Aplicações,** selecione Ler dados do diretório.</span><span class="sxs-lookup"><span data-stu-id="2825b-123">In **Applications permissions**, select Read directory data.</span></span>

    3. <span data-ttu-id="2825b-124">Guarde as permissões.</span><span class="sxs-lookup"><span data-stu-id="2825b-124">Save the permissions.</span></span>

4. <span data-ttu-id="2825b-125">Note o ID da aplicação na secção **Propriedades** da sua aplicação web.</span><span class="sxs-lookup"><span data-stu-id="2825b-125">Note the application ID in the **Properties** section of your web app.</span></span>

### <a name="add-a-secret-key-to-your-app"></a><span data-ttu-id="2825b-126">Adicione uma chave secreta à sua aplicação</span><span class="sxs-lookup"><span data-stu-id="2825b-126">Add a secret key to your app</span></span>

1. <span data-ttu-id="2825b-127">Aceda à secção **Chaves** da sua aplicação web.</span><span class="sxs-lookup"><span data-stu-id="2825b-127">Go to the **Keys** section of your web app.</span></span>

2. <span data-ttu-id="2825b-128">Introduza a descrição da chave e selecione a duração de 1 ou 2 anos, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="2825b-128">Enter key description and select duration as 1 or 2 years, as you need.</span></span>

3. <span data-ttu-id="2825b-129">Guarde e copie o valor da chave secreta.</span><span class="sxs-lookup"><span data-stu-id="2825b-129">Save and copy the secret key value.</span></span> <span data-ttu-id="2825b-130">**Este valor não será mostrado novamente uma vez que sai desta página.**</span><span class="sxs-lookup"><span data-stu-id="2825b-130">**This value will not be shown again once you leave this page.**</span></span>

<span data-ttu-id="2825b-131">Deve ter os seguintes detalhes da configuração da aplicação web:</span><span class="sxs-lookup"><span data-stu-id="2825b-131">You should have the following details from the web app configuration:</span></span>

- <span data-ttu-id="2825b-132">ID da aplicação</span><span class="sxs-lookup"><span data-stu-id="2825b-132">Application ID</span></span>
- <span data-ttu-id="2825b-133">Segredo da aplicação</span><span class="sxs-lookup"><span data-stu-id="2825b-133">Application secret</span></span>

### <a name="register-the-web-app-in-partner-center"></a><span data-ttu-id="2825b-134">Registe a aplicação Web no Partner Center</span><span class="sxs-lookup"><span data-stu-id="2825b-134">Register the Web app in Partner Center</span></span>

1. <span data-ttu-id="2825b-135">Inicie sessão em [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="2825b-135">Sign in to [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com).</span></span>

2. <span data-ttu-id="2825b-136">Escolha **o Dashboard,** escolha **Definições Conta** e escolha a **Gestão de Aplicações.**</span><span class="sxs-lookup"><span data-stu-id="2825b-136">Choose **Dashboard**, then choose **Account Settings**, then choose **App Management**.</span></span>

3. <span data-ttu-id="2825b-137">Na secção **Aplicação Web,** escolha **registar a aplicação existente.**</span><span class="sxs-lookup"><span data-stu-id="2825b-137">In the **Web App** section, choose **Register existing app**.</span></span>

4. <span data-ttu-id="2825b-138">Selecione a aplicação web que criou no portal Azure.</span><span class="sxs-lookup"><span data-stu-id="2825b-138">Select the web app you created in Azure portal.</span></span>

5. <span data-ttu-id="2825b-139">Escolha **registar a sua aplicação.**</span><span class="sxs-lookup"><span data-stu-id="2825b-139">Choose **register your app**.</span></span>

## <a name="native-apps"></a><span data-ttu-id="2825b-140">Aplicações nativas</span><span class="sxs-lookup"><span data-stu-id="2825b-140">Native apps</span></span>

<span data-ttu-id="2825b-141">As aplicações nativas não precisam de ser registadas no Partner Center.</span><span class="sxs-lookup"><span data-stu-id="2825b-141">Native apps do not need to be registered to Partner Center.</span></span> <span data-ttu-id="2825b-142">Mas estas aplicações precisam de ser configuradas para fornecer acesso às APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="2825b-142">But these apps need to be configured to provide access to Partner Center APIs.</span></span>

>[!NOTE]
><span data-ttu-id="2825b-143">Antes de criar uma aplicação nativa no portal Azure, inicie sessão no Partner Center utilizando as credenciais de utilizador do inquilino do parceiro.</span><span class="sxs-lookup"><span data-stu-id="2825b-143">Before creating a native app in the Azure portal, log in into Partner Center using the admin user credentials from the partner tenant.</span></span> <span data-ttu-id="2825b-144">Isto cria as configurações no arrendatário para permitir permissões de aplicações.</span><span class="sxs-lookup"><span data-stu-id="2825b-144">This creates the settings on the tenant to enable app permissions.</span></span>

### <a name="create-native-app"></a><span data-ttu-id="2825b-145">Criar aplicativo nativo</span><span class="sxs-lookup"><span data-stu-id="2825b-145">Create native app</span></span>

1. <span data-ttu-id="2825b-146">Navegue para o [portal Azure - Página de registos de aplicações](https://go.microsoft.com/fwlink/?linkid=2083908) para registar a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="2825b-146">Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app.</span></span> <span data-ttu-id="2825b-147">Inicie sessão no portal do Azure com uma conta profissional ou escolar ou uma conta pessoal da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2825b-147">Sign in to the Azure portal using either a work or school account or a personal Microsoft account.</span></span>

2. <span data-ttu-id="2825b-148">Selecione **Novo registo**.</span><span class="sxs-lookup"><span data-stu-id="2825b-148">Select **New registration**.</span></span> <span data-ttu-id="2825b-149">Para mais informações, consulte [Quickstart: Registe uma aplicação com o plataforma de identidades da Microsoft](/azure/active-directory/develop/quickstart-register-app).</span><span class="sxs-lookup"><span data-stu-id="2825b-149">For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).</span></span>

### <a name="configure-api-access-permissions-for-native-app"></a><span data-ttu-id="2825b-150">Configure permissões de acesso da API para app nativa</span><span class="sxs-lookup"><span data-stu-id="2825b-150">Configure API access permissions for native app</span></span>

1. <span data-ttu-id="2825b-151">Escolha a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="2825b-151">Choose your app.</span></span> <span data-ttu-id="2825b-152">Vai para **Definições.**</span><span class="sxs-lookup"><span data-stu-id="2825b-152">Go to **Settings**.</span></span>

2. <span data-ttu-id="2825b-153">No Acesso API, escolha **permissões necessárias.**</span><span class="sxs-lookup"><span data-stu-id="2825b-153">In API Access, choose **Required permissions**.</span></span>

3. <span data-ttu-id="2825b-154">Escolha **permissões Windows Azure Ative Directory.**</span><span class="sxs-lookup"><span data-stu-id="2825b-154">Choose **Windows Azure Active Directory permissions**.</span></span> <span data-ttu-id="2825b-155">Nas **permissões delegadas,** selecione estas permissões:</span><span class="sxs-lookup"><span data-stu-id="2825b-155">In **Delegated permissions**, select these permissions:</span></span>

    - <span data-ttu-id="2825b-156">**Iniciar sessão e ler o perfil de utilizador**</span><span class="sxs-lookup"><span data-stu-id="2825b-156">**Sign in and read user profile**</span></span>
    - <span data-ttu-id="2825b-157">**Ler os dados do diretório**</span><span class="sxs-lookup"><span data-stu-id="2825b-157">**Read directory data**</span></span>
    - <span data-ttu-id="2825b-158">**Aceder ao diretório como o utilizador com sessão iniciada**</span><span class="sxs-lookup"><span data-stu-id="2825b-158">**Access the directory as the signed-in user**</span></span>
    - <span data-ttu-id="2825b-159">**Leia todos os grupos**</span><span class="sxs-lookup"><span data-stu-id="2825b-159">**Read all groups**</span></span>

4. <span data-ttu-id="2825b-160">Guarde as permissões.</span><span class="sxs-lookup"><span data-stu-id="2825b-160">Save the permissions.</span></span>

5. <span data-ttu-id="2825b-161">Escolha **Adicionar** as **permissões requeridas.**</span><span class="sxs-lookup"><span data-stu-id="2825b-161">Choose **Add** in **Required permissions**.</span></span>

6. <span data-ttu-id="2825b-162">Escolha **Selecionar uma API**.</span><span class="sxs-lookup"><span data-stu-id="2825b-162">Choose **Select an API**.</span></span>

    1. <span data-ttu-id="2825b-163">Na caixa de pesquisa, insira o **Microsoft Partner Center** e selecione-o na lista de resultados.</span><span class="sxs-lookup"><span data-stu-id="2825b-163">In the search box, enter **Microsoft Partner Center** and select it from the results list.</span></span>

    2. <span data-ttu-id="2825b-164">Escolha **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="2825b-164">Choose **Select**.</span></span>

7. <span data-ttu-id="2825b-165">Escolha **Permissões Selecione**.</span><span class="sxs-lookup"><span data-stu-id="2825b-165">Choose **Select permissions**.</span></span>

    1. <span data-ttu-id="2825b-166">Selecione **Access Partner Center PPE**.</span><span class="sxs-lookup"><span data-stu-id="2825b-166">Select **Access Partner Center PPE**.</span></span>
    
    2. <span data-ttu-id="2825b-167">Escolha **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="2825b-167">Choose **Select**.</span></span>

8. <span data-ttu-id="2825b-168">Selecione **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="2825b-168">Choose **Done**.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="2825b-169">Note o ID da aplicação nas propriedades da sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="2825b-169">Note the application ID in the Properties of your app.</span></span>

<span data-ttu-id="2825b-170">Não precisa de registar aplicações nativas no Partner Center, no entanto a aplicação nativa deve ser aprovada por administração.</span><span class="sxs-lookup"><span data-stu-id="2825b-170">You do not need to register native apps in Partner Center, however the native app must be admin consented.</span></span> <span data-ttu-id="2825b-171">Note o ID da aplicação da sua aplicação nativa.</span><span class="sxs-lookup"><span data-stu-id="2825b-171">Note the application ID of your native app.</span></span>
