---
title: Registar detalhes da aplicação para Partner Center para Microsoft National Cloud
description: Saiba como e por que os desenvolvedores de aplicativos para Partner Center para a Microsoft National Cloud devem registar detalhes sobre a sua aplicação com Azure AD através do portal Azure.
MS-HAID:
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_cloud\_germany
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_national\_clouds
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 887cb71c752ac5d9c61398536711545c19cc7600
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770144"
---
# <a name="register-app-details-for-partner-center-for-microsoft-national-cloud-through-the-azure-portal"></a><span data-ttu-id="eb25f-103">Registar detalhes da aplicação para Partner Center para a Microsoft National Cloud através do portal Azure</span><span class="sxs-lookup"><span data-stu-id="eb25f-103">Register app details for Partner Center for Microsoft National Cloud through the Azure portal</span></span>

<span data-ttu-id="eb25f-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="eb25f-104">**Applies to:**</span></span>

- <span data-ttu-id="eb25f-105">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="eb25f-105">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="eb25f-106">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="eb25f-106">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="eb25f-107">Os desenvolvedores devem registar detalhes sobre a sua aplicação com Azure AD através do portal Azure.</span><span class="sxs-lookup"><span data-stu-id="eb25f-107">Developers must register details about their app with Azure AD through the Azure portal.</span></span> <span data-ttu-id="eb25f-108">Isto ajuda a garantir que apenas as aplicações especificadas são capazes de se conectar aos dados do parceiro e do cliente.</span><span class="sxs-lookup"><span data-stu-id="eb25f-108">This helps ensure that only specified apps are able to connect to partner and customer data.</span></span>

<span data-ttu-id="eb25f-109">Para partner center for Microsoft Cloud for US Government, você deve atualmente gerir aplicações através do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb25f-109">For Partner Center for Microsoft Cloud for US Government, you currently must manage apps through PowerShell.</span></span> <span data-ttu-id="eb25f-110">Para obter mais informações, consulte a documentação de referência da [Azure PowerShell](/powershell/module/Azuread/#applications).</span><span class="sxs-lookup"><span data-stu-id="eb25f-110">For more information, see the [Azure PowerShell reference documentation](/powershell/module/Azuread/#applications).</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="eb25f-111">Esteja ciente dos seguintes requisitos adicionais quando criar uma aplicação para Partner Center para Microsoft Cloud Germany ou Partner Center for Microsoft Cloud para o Governo dos EUA.</span><span class="sxs-lookup"><span data-stu-id="eb25f-111">Be aware of the following additional requirements when you create an app for Partner Center for Microsoft Cloud Germany or Partner Center for Microsoft Cloud for US Government.</span></span>

## <a name="web-apps"></a><span data-ttu-id="eb25f-112">Web Apps</span><span class="sxs-lookup"><span data-stu-id="eb25f-112">Web apps</span></span>

<span data-ttu-id="eb25f-113">Para aplicações web, utilize os seguintes procedimentos para registar o seu ID de aplicação.</span><span class="sxs-lookup"><span data-stu-id="eb25f-113">For web apps, use the following procedures to register your application ID.</span></span>

### <a name="create-or-update-web-app"></a><span data-ttu-id="eb25f-114">Criar ou atualizar aplicativo web</span><span class="sxs-lookup"><span data-stu-id="eb25f-114">Create or update web app</span></span>

1. <span data-ttu-id="eb25f-115">Navegue para o [portal Azure - Página de registos de aplicações](https://go.microsoft.com/fwlink/?linkid=2083908) para registar a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="eb25f-115">Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app.</span></span> <span data-ttu-id="eb25f-116">Inicie sessão no portal do Azure com uma conta profissional ou escolar ou uma conta pessoal da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eb25f-116">Sign in to the Azure portal using either a work or school account or a personal Microsoft account.</span></span>

2. <span data-ttu-id="eb25f-117">Selecione **Novo registo**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-117">Select **New registration**.</span></span> <span data-ttu-id="eb25f-118">Para obter mais informações, consulte [Quickstart: Registe uma aplicação com a plataforma de identidade microsoft](/azure/active-directory/develop/quickstart-register-app).</span><span class="sxs-lookup"><span data-stu-id="eb25f-118">For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).</span></span>

### <a name="configure-api-access-permissions-for-web-app"></a><span data-ttu-id="eb25f-119">Configure permissões de acesso da API para aplicação web</span><span class="sxs-lookup"><span data-stu-id="eb25f-119">Configure API access permissions for web app</span></span>

1. <span data-ttu-id="eb25f-120">Escolha a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="eb25f-120">Choose your app.</span></span> <span data-ttu-id="eb25f-121">Aceda às **Definições** da aplicação Web.</span><span class="sxs-lookup"><span data-stu-id="eb25f-121">Go to **Settings** of the Web app.</span></span>

2. <span data-ttu-id="eb25f-122">Na secção **de Acesso API,** escolha **permissões necessárias**</span><span class="sxs-lookup"><span data-stu-id="eb25f-122">In **API Access** section, choose **Required permissions**</span></span>

3. <span data-ttu-id="eb25f-123">Para permissões de diretório ativo do Windows Azure:</span><span class="sxs-lookup"><span data-stu-id="eb25f-123">For Windows Azure Active directory permissions:</span></span>

    1. <span data-ttu-id="eb25f-124">Escolha **permissões do Windows Azure Ative Directory**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-124">Choose **Windows Azure Active Directory permissions**.</span></span>

    2. <span data-ttu-id="eb25f-125">Nas **permissões de Aplicações,** selecione Ler dados do diretório.</span><span class="sxs-lookup"><span data-stu-id="eb25f-125">In **Applications permissions**, select Read directory data.</span></span>

    3. <span data-ttu-id="eb25f-126">Guarde as permissões.</span><span class="sxs-lookup"><span data-stu-id="eb25f-126">Save the permissions.</span></span>

4. <span data-ttu-id="eb25f-127">Note o ID da aplicação na secção **Propriedades** da sua aplicação web.</span><span class="sxs-lookup"><span data-stu-id="eb25f-127">Note the application ID in the **Properties** section of your web app.</span></span>

### <a name="add-a-secret-key-to-your-app"></a><span data-ttu-id="eb25f-128">Adicione uma chave secreta à sua aplicação</span><span class="sxs-lookup"><span data-stu-id="eb25f-128">Add a secret key to your app</span></span>

1. <span data-ttu-id="eb25f-129">Aceda à secção **Chaves** da sua aplicação web.</span><span class="sxs-lookup"><span data-stu-id="eb25f-129">Go to the **Keys** section of your web app.</span></span>

2. <span data-ttu-id="eb25f-130">Introduza a descrição da chave e selecione a duração de 1 ou 2 anos, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="eb25f-130">Enter key description and select duration as 1 or 2 years, as you need.</span></span>

3. <span data-ttu-id="eb25f-131">Guarde e copie o valor da chave secreta.</span><span class="sxs-lookup"><span data-stu-id="eb25f-131">Save and copy the secret key value.</span></span> <span data-ttu-id="eb25f-132">**Este valor não será mostrado novamente uma vez que sai desta página.**</span><span class="sxs-lookup"><span data-stu-id="eb25f-132">**This value will not be shown again once you leave this page.**</span></span>

<span data-ttu-id="eb25f-133">Deve ter os seguintes detalhes da configuração da aplicação web:</span><span class="sxs-lookup"><span data-stu-id="eb25f-133">You should have the following details from the web app configuration:</span></span>

- <span data-ttu-id="eb25f-134">ID da Aplicação</span><span class="sxs-lookup"><span data-stu-id="eb25f-134">Application ID</span></span>
- <span data-ttu-id="eb25f-135">Segredo da aplicação</span><span class="sxs-lookup"><span data-stu-id="eb25f-135">Application secret</span></span>

### <a name="register-the-web-app-in-partner-center"></a><span data-ttu-id="eb25f-136">Registe a aplicação Web no Partner Center</span><span class="sxs-lookup"><span data-stu-id="eb25f-136">Register the Web app in Partner Center</span></span>

1. <span data-ttu-id="eb25f-137">Faça login em [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com) .</span><span class="sxs-lookup"><span data-stu-id="eb25f-137">Log in to [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com).</span></span>

2. <span data-ttu-id="eb25f-138">Escolha **o Dashboard,** escolha **as Definições de Conta** e, em seguida, escolha a **Gestão de Aplicações.**</span><span class="sxs-lookup"><span data-stu-id="eb25f-138">Choose **Dashboard**, then choose **Account Settings**, then choose **App Management**.</span></span>

3. <span data-ttu-id="eb25f-139">Na secção **Aplicação Web,** escolha **registar a aplicação existente.**</span><span class="sxs-lookup"><span data-stu-id="eb25f-139">In the **Web App** section, choose **Register existing app**.</span></span>

4. <span data-ttu-id="eb25f-140">Selecione a aplicação web que criou no portal Azure.</span><span class="sxs-lookup"><span data-stu-id="eb25f-140">Select the web app you created in Azure portal.</span></span>

5. <span data-ttu-id="eb25f-141">Escolha **registar a sua aplicação.**</span><span class="sxs-lookup"><span data-stu-id="eb25f-141">Choose **register your app**.</span></span>

## <a name="native-apps"></a><span data-ttu-id="eb25f-142">Aplicações nativas</span><span class="sxs-lookup"><span data-stu-id="eb25f-142">Native apps</span></span>

<span data-ttu-id="eb25f-143">As aplicações nativas não precisam de ser registadas no Partner Center.</span><span class="sxs-lookup"><span data-stu-id="eb25f-143">Native apps do not need to be registered to Partner Center.</span></span> <span data-ttu-id="eb25f-144">Mas estas aplicações precisam de ser configuradas para fornecer acesso às APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="eb25f-144">But these apps need to be configured to provide access to Partner Center APIs.</span></span>

>[!NOTE]
><span data-ttu-id="eb25f-145">Antes de criar uma aplicação nativa no portal Azure, inicie sessão no Partner Center utilizando as credenciais de utilizador do inquilino do parceiro.</span><span class="sxs-lookup"><span data-stu-id="eb25f-145">Before creating a native app in the Azure portal, log in into Partner Center using the admin user credentials from the partner tenant.</span></span> <span data-ttu-id="eb25f-146">Isto cria as configurações no arrendatário para permitir permissões de aplicações.</span><span class="sxs-lookup"><span data-stu-id="eb25f-146">This creates the settings on the tenant to enable app permissions.</span></span>

### <a name="create-native-app"></a><span data-ttu-id="eb25f-147">Criar aplicativo nativo</span><span class="sxs-lookup"><span data-stu-id="eb25f-147">Create native app</span></span>

1. <span data-ttu-id="eb25f-148">Navegue para o [portal Azure - Página de registos de aplicações](https://go.microsoft.com/fwlink/?linkid=2083908) para registar a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="eb25f-148">Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app.</span></span> <span data-ttu-id="eb25f-149">Inicie sessão no portal do Azure com uma conta profissional ou escolar ou uma conta pessoal da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eb25f-149">Sign in to the Azure portal using either a work or school account or a personal Microsoft account.</span></span>

2. <span data-ttu-id="eb25f-150">Selecione **Novo registo**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-150">Select **New registration**.</span></span> <span data-ttu-id="eb25f-151">Para obter mais informações, consulte [Quickstart: Registe uma aplicação com a plataforma de identidade microsoft](/azure/active-directory/develop/quickstart-register-app).</span><span class="sxs-lookup"><span data-stu-id="eb25f-151">For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).</span></span>

### <a name="configure-api-access-permissions-for-native-app"></a><span data-ttu-id="eb25f-152">Configure permissões de acesso da API para app nativa</span><span class="sxs-lookup"><span data-stu-id="eb25f-152">Configure API access permissions for native app</span></span>

1. <span data-ttu-id="eb25f-153">Escolha a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="eb25f-153">Choose your app.</span></span> <span data-ttu-id="eb25f-154">Ir para **Definições**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-154">Go to **Settings**.</span></span>

2. <span data-ttu-id="eb25f-155">No Acesso API, escolha **permissões necessárias.**</span><span class="sxs-lookup"><span data-stu-id="eb25f-155">In API Access, choose **Required permissions**.</span></span>

3. <span data-ttu-id="eb25f-156">Escolha **permissões do Windows Azure Ative Directory**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-156">Choose **Windows Azure Active Directory permissions**.</span></span> <span data-ttu-id="eb25f-157">Nas **permissões delegadas,** selecione estas permissões:</span><span class="sxs-lookup"><span data-stu-id="eb25f-157">In **Delegated permissions**, select these permissions:</span></span>

    - <span data-ttu-id="eb25f-158">**Iniciar sessão e ler o perfil de utilizador**</span><span class="sxs-lookup"><span data-stu-id="eb25f-158">**Sign in and read user profile**</span></span>
    - <span data-ttu-id="eb25f-159">**Ler os dados do diretório**</span><span class="sxs-lookup"><span data-stu-id="eb25f-159">**Read directory data**</span></span>
    - <span data-ttu-id="eb25f-160">**Aceder ao diretório como o utilizador com sessão iniciada**</span><span class="sxs-lookup"><span data-stu-id="eb25f-160">**Access the directory as the signed-in user**</span></span>
    - <span data-ttu-id="eb25f-161">**Leia todos os grupos**</span><span class="sxs-lookup"><span data-stu-id="eb25f-161">**Read all groups**</span></span>

4. <span data-ttu-id="eb25f-162">Guarde as permissões.</span><span class="sxs-lookup"><span data-stu-id="eb25f-162">Save the permissions.</span></span>

5. <span data-ttu-id="eb25f-163">Escolha **Adicionar** as **permissões requeridas.**</span><span class="sxs-lookup"><span data-stu-id="eb25f-163">Choose **Add** in **Required permissions**.</span></span>

6. <span data-ttu-id="eb25f-164">Escolha **Selecionar uma API**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-164">Choose **Select an API**.</span></span>

    1. <span data-ttu-id="eb25f-165">Na caixa de pesquisa, insira o **Microsoft Partner Center** e selecione-o na lista de resultados.</span><span class="sxs-lookup"><span data-stu-id="eb25f-165">In the search box, enter **Microsoft Partner Center** and select it from the results list.</span></span>

    2. <span data-ttu-id="eb25f-166">Escolha **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-166">Choose **Select**.</span></span>

7. <span data-ttu-id="eb25f-167">Escolha **Permissões Selecione**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-167">Choose **Select permissions**.</span></span>

    1. <span data-ttu-id="eb25f-168">Selecione **Access Partner Center PPE**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-168">Select **Access Partner Center PPE**.</span></span>
    
    2. <span data-ttu-id="eb25f-169">Escolha **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-169">Choose **Select**.</span></span>

8. <span data-ttu-id="eb25f-170">Selecione **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="eb25f-170">Choose **Done**.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="eb25f-171">Note o ID da aplicação nas propriedades da sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="eb25f-171">Note the application ID in the Properties of your app.</span></span>

<span data-ttu-id="eb25f-172">Não precisa de registar aplicações nativas no Partner Center, no entanto a aplicação nativa deve ser administrada.</span><span class="sxs-lookup"><span data-stu-id="eb25f-172">You do not need to register native apps in Partner Center, however the native app must be admin consented .</span></span> <span data-ttu-id="eb25f-173">Note o ID da aplicação da sua aplicação nativa.</span><span class="sxs-lookup"><span data-stu-id="eb25f-173">Note the application ID of your native app.</span></span>
