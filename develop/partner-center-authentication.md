---
title: Partner Center authentication (Autenticação do Centro de Parceiros)
description: O Partner Center utiliza o Azure AD para autenticação e para utilizar as APIs do Centro De Parceiros deve configurar corretamente as suas definições de autenticação.
ms.date: 11/13/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-csp
ms.openlocfilehash: 46ef9c6bc151c368281e943b7d24ebc07e34b66d
ms.sourcegitcommit: 64c498d3571f2287305968890578bc7396779621
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2020
ms.locfileid: "97770288"
---
# <a name="partner-center-authentication"></a><span data-ttu-id="f2d3e-103">Partner Center authentication (Autenticação do Centro de Parceiros)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-103">Partner Center authentication</span></span>

<span data-ttu-id="f2d3e-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="f2d3e-104">**Applies to:**</span></span>

- <span data-ttu-id="f2d3e-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="f2d3e-105">Partner Center</span></span>
- <span data-ttu-id="f2d3e-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="f2d3e-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="f2d3e-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="f2d3e-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="f2d3e-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="f2d3e-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="f2d3e-109">O Centro de Parceiros utiliza o Azure Active Directory para autenticação.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-109">Partner Center uses Azure Active Directory for authentication.</span></span> <span data-ttu-id="f2d3e-110">Ao interagir com o módulo do PowerShell, o SDK ou a API do Centro de Parceiros, tem de configurar corretamente uma aplicação do Azure Active Directory e, em seguida, pedir um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-110">When interacting with the Partner Center API, SDK, or PowerShell module you must correctly configure an Azure AD application and then request an access token.</span></span> <span data-ttu-id="f2d3e-111">Os tokens de acesso obtidos apenas através de app ou app + autenticação do utilizador podem ser utilizados com o Centro de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-111">Access tokens obtained using app only or app + user authentication can be used with the Partner Center.</span></span> <span data-ttu-id="f2d3e-112">No entanto, há dois itens importantes que precisam de ser considerados</span><span class="sxs-lookup"><span data-stu-id="f2d3e-112">However, there are two important items that need to be considered</span></span>

- <span data-ttu-id="f2d3e-113">Utilize a autenticação de vários fatores ao aceder à API do Centro Parceiro utilizando a app + autenticação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-113">Use multi-factor authentication when accessing the Partner Center API using app + user authentication.</span></span> <span data-ttu-id="f2d3e-114">Para obter mais informações sobre esta alteração, consulte [Ativar o modelo de aplicação seguro](enable-secure-app-model.md).</span><span class="sxs-lookup"><span data-stu-id="f2d3e-114">For more information regarding this change, see [Enable secure application model](enable-secure-app-model.md).</span></span>

- <span data-ttu-id="f2d3e-115">Nem todas as operações da aplicação de suporte API do Partner Center apenas autenticam.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-115">Not all of the operations the Partner Center API support app only authentication.</span></span> <span data-ttu-id="f2d3e-116">Existem certos cenários em que será necessário utilizar a app + a autenticação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-116">There are certain scenarios where you'll be required to use app + user authentication.</span></span> <span data-ttu-id="f2d3e-117">De acordo com o *título pré-requisitos* de cada [artigo,](scenarios.md)encontrará documentação que indique se apenas a autenticação da app, app + autenticação do utilizador, ou ambos são suportados.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-117">Under the *Prerequisites* heading on each [article](scenarios.md), you'll find documentation that states whether app only authentication, app + user authentication, or both are supported.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="f2d3e-118">Configuração inicial</span><span class="sxs-lookup"><span data-stu-id="f2d3e-118">Initial setup</span></span>

1. <span data-ttu-id="f2d3e-119">Para começar, tem de se certificar de que tem uma conta principal do Partner Center e uma conta de parceiro de integração.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-119">To begin, you need to make sure that you have both a primary Partner Center account, and an integration sandbox Partner Center account.</span></span> <span data-ttu-id="f2d3e-120">Para obter mais informações, consulte [configurar contas do Partner Center para acesso a API.](set-up-api-access-in-partner-center.md)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-120">For more information, see [Set up Partner Center accounts for API access](set-up-api-access-in-partner-center.md).</span></span> <span data-ttu-id="f2d3e-121">Tome nota do ID e Secret da App Azure AAD (o segredo do cliente é necessário para a identificação apenas da App) tanto para a sua conta primária como para a sua conta de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-121">Make note of the Azure AAD App registration ID and Secret (client secret is required for App only identification) for both your primary account and your integration sandbox account.</span></span>

2. <span data-ttu-id="f2d3e-122">Inscreva-se no Azure AD a partir do portal Azure.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-122">Sign in to Azure AD from the Azure portal.</span></span> <span data-ttu-id="f2d3e-123">Nas **permissões a outras aplicações,** descreva permissões para **o Windows Azure Ative Directory** para **Permissões Delegadas**, e selecione **tanto Aceda ao diretório como utilizador inscrito** e faça o **sessão e leia o perfil do utilizador.**</span><span class="sxs-lookup"><span data-stu-id="f2d3e-123">In **permissions to other applications**, set permissions for **Windows Azure Active Directory** to **Delegated Permissions**, and select both **Access the directory as the signed-in user** and **Sign in and read user profile**.</span></span>

3. <span data-ttu-id="f2d3e-124">No portal Azure, **adicione a aplicação**.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-124">In the Azure portal, **Add application**.</span></span> <span data-ttu-id="f2d3e-125">Procure por "Microsoft Partner Center", que é a aplicação Microsoft Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-125">Search for "Microsoft Partner Center", which is the Microsoft Partner Center application.</span></span> <span data-ttu-id="f2d3e-126">Desa estatudo as **permissões delegadas** para aceder à **API do Centro de Parceiros de Acesso**.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-126">Set the **Delegated Permissions** to **Access Partner Center API**.</span></span> <span data-ttu-id="f2d3e-127">Se estiver a utilizar o Partner Center para o Microsoft Cloud Germany ou o Partner Center para o Microsoft Cloud para o Governo dos EUA, este passo é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-127">If you are using Partner Center for Microsoft Cloud Germany or Partner Center for Microsoft Cloud for US Government, this step is mandatory.</span></span> <span data-ttu-id="f2d3e-128">Se estiver a utilizar o exemplo global do Partner Center, este passo é opcional.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-128">If you are using Partner Center global instance, this step is optional.</span></span> <span data-ttu-id="f2d3e-129">Os Parceiros CSP podem usar a funcionalidade de Gestão de Aplicações no portal Partner Center para contornar este passo para o Exemplo global do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-129">CSP Partners can use the App Management feature in the Partner Center portal to bypass this step for Partner Center global instance.</span></span>

## <a name="app-only-authentication"></a><span data-ttu-id="f2d3e-130">Autenticação apenas para aplicativos</span><span class="sxs-lookup"><span data-stu-id="f2d3e-130">App-only authentication</span></span>

<span data-ttu-id="f2d3e-131">Se quiser utilizar a autenticação apenas para aplicações para aceder ao módulo Partner Center REST API, .NET API, Java API ou PowerShell, então pode fazê-lo aproveitando as seguintes instruções.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-131">If you would like to use app-only authentication to access the Partner Center REST API, .NET API, Java API, or PowerShell module then you can do so by leveraging the following instructions.</span></span>

## <a name="net-app-only-authentication"></a><span data-ttu-id="f2d3e-132">.NET (autenticação apenas para aplicações)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-132">.NET (app-only authentication)</span></span>

```csharp
public static IAggregatePartner GetPartnerCenterTokenUsingAppCredentials()
{
    IPartnerCredentials partnerCredentials =
        PartnerCredentials.Instance.GenerateByApplicationCredentials(
            PartnerApplicationConfiguration.ApplicationId,
            PartnerApplicationConfiguration.ApplicationSecret,
            PartnerApplicationConfiguration.ApplicationDomain);

    // Create operations instance with partnerCredentials.
    return PartnerService.Instance.CreatePartnerOperations(partnerCredentials);
}
```

## <a name="java-app-only-authentication"></a><span data-ttu-id="f2d3e-133">Java (autenticação apenas para aplicações)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-133">Java (app-only authentication)</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

```java
public IAggregatePartner getAppPartnerOperations()
{
    IPartnerCredentials appCredentials =
        PartnerCredentials.getInstance().generateByApplicationCredentials(
        PartnerApplicationConfiguration.getApplicationId(),
        PartnerApplicationConfiguration.getApplicationSecret(),
        PartnerApplicationConfiguration.getApplicationDomain());

    return PartnerService.getInstance().createPartnerOperations( appCredentials );
}
```

## <a name="rest-app-only-authentication"></a><span data-ttu-id="f2d3e-134">REST (autenticação apenas para aplicações)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-134">REST (app-only authentication)</span></span>

### <a name="rest-request"></a><span data-ttu-id="f2d3e-135">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f2d3e-135">REST request</span></span>

```http
POST https://login.microsoftonline.com/{tenantId}/oauth2/token HTTP/1.1
Accept: application/json
return-client-request-id: true
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Host: login.microsoftonline.com
Content-Length: 194
Expect: 100-continue

resource=https%3A%2F%2Fgraph.windows.net&client_id={client-id-here}&client_secret={client-secret-here}&grant_type=client_credentials
```

### <a name="rest-response"></a><span data-ttu-id="f2d3e-136">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f2d3e-136">REST response</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Pragma: no-cache
Content-Type: application/json; charset=utf-8
Expires: -1
Content-Length: 1406

{"token_type":"Bearer","expires_in":"3600","ext_expires_in":"3600","expires_on":"1546469802","not_before":"1546465902","resource":"https://graph.windows.net","access_token":"value-has-been-removed"}
```

## <a name="app--user-authentication"></a><span data-ttu-id="f2d3e-137">App + Autenticação do utilizador</span><span class="sxs-lookup"><span data-stu-id="f2d3e-137">App + User authentication</span></span>

<span data-ttu-id="f2d3e-138">Historicamente, a [concessão de credenciais de senha do proprietário de recursos](https://tools.ietf.org/html/rfc6749#section-4.3) tem sido usada para solicitar um token de acesso para uso com o módulo Partner Center REST API, .NET API, Java API ou PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-138">Historically the [resource owner password credentials grant](https://tools.ietf.org/html/rfc6749#section-4.3) has been used to request an access token for use with the Partner Center REST API, .NET API, Java API, or PowerShell module.</span></span> <span data-ttu-id="f2d3e-139">Este método foi utilizado para solicitar um token de acesso do Azure Ative Directory utilizando um identificador de clientes e credenciais de utilizador.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-139">That method was used to request an access token from Azure Active Directory using a client identifier and user credentials.</span></span> <span data-ttu-id="f2d3e-140">No entanto, esta abordagem deixará de funcionar porque o Partner Center requer autenticação de vários fatores, quando se utiliza a app + autenticação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-140">However, this approach will no longer work because Partner Center requires multi-factor authentication, when using app + user authentication.</span></span> <span data-ttu-id="f2d3e-141">Para cumprir este requisito, a Microsoft introduziu um quadro seguro e escalável para autenticar parceiros do Cloud Solution Provider (CSP) e fornecedores de painéis de controlo (CPV) utilizando a autenticação de vários fatores.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-141">To comply with this requirement Microsoft has introduced a secure, scalable framework for authenticating Cloud Solution Provider (CSP) partners and control panel vendors (CPV) using multi-factor authentication.</span></span> <span data-ttu-id="f2d3e-142">Este quadro é conhecido como o Modelo de Aplicação Segura, e é composto por um processo de consentimento e um pedido de acesso a um token usando um token de atualização.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-142">This framework is known as the Secure Application Model, and it is composed of a consent process and a request for an access token using a refresh token.</span></span>

### <a name="partner-consent"></a><span data-ttu-id="f2d3e-143">Consentimento do parceiro</span><span class="sxs-lookup"><span data-stu-id="f2d3e-143">Partner consent</span></span>

<span data-ttu-id="f2d3e-144">O processo de consentimento do parceiro é um processo interativo em que o parceiro autentica usando a autenticação de vários fatores, consente com a aplicação, e um token de atualização é armazenado num repositório seguro, como Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-144">The partner consent process is an interactive process where the partner authenticates using multi-factor authentication, consents to the application, and a refresh token is stored in a secure repository such as Azure Key Vault.</span></span> <span data-ttu-id="f2d3e-145">Recomendamos que seja utilizada uma conta dedicada para efeitos de integração para este processo.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-145">We recommend that a dedicated account for integration purposes be used for this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2d3e-146">A solução de autenticação multi-factor adequada deve ser ativada para a conta de serviço utilizada no processo de consentimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-146">The appropriate multi-factor authentication solution should be enabled for the service account used in the partner consent process.</span></span> <span data-ttu-id="f2d3e-147">Se não for, então o token de atualização resultante não estará em conformidade com os requisitos de segurança.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-147">If it isn't then the resulting refresh token will not be compliant with security requirements.</span></span>

### <a name="samples-for-app--user-authentication"></a><span data-ttu-id="f2d3e-148">Amostras para App + Autenticação do Utilizador</span><span class="sxs-lookup"><span data-stu-id="f2d3e-148">Samples for App + User authentication</span></span>

<span data-ttu-id="f2d3e-149">O processo de consentimento do parceiro pode ser realizado de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-149">The partner consent process can be performed in a number of ways.</span></span> <span data-ttu-id="f2d3e-150">Para ajudar os parceiros a entender como realizar cada operação necessária, desenvolvemos as seguintes amostras.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-150">To help partners understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="f2d3e-151">Ao implementar a solução adequada no seu ambiente, é importante que desenvolva uma solução que seja uma reclamação com os seus padrões de codificação e políticas de segurança.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-151">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-appuser-authentication"></a><span data-ttu-id="f2d3e-152">.NET (app+autenticação do utilizador)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-152">.NET (app+user authentication)</span></span>

<span data-ttu-id="f2d3e-153">O projeto de amostra [de consentimento do parceiro](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) demonstra como utilizar um website desenvolvido usando ASP.NET para capturar o consentimento, solicitar um token de atualização e armazená-lo de forma segura no Cofre da Chave Azure.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-153">The [partner consent](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) sample project demonstrates how to utilize a website developed using ASP.NET to capture consent, request a refresh token, and securely store it in Azure Key Vault.</span></span> <span data-ttu-id="f2d3e-154">Execute os seguintes passos para criar os pré-requisitos necessários para esta amostra.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-154">Perform the following steps to create the required prerequisites for this sample.</span></span>

1. <span data-ttu-id="f2d3e-155">Crie uma instância do Cofre de Chaves Azure utilizando o portal Azure ou os seguintes comandos PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-155">Create an instance of Azure Key Vault using the Azure portal or the following PowerShell commands.</span></span> <span data-ttu-id="f2d3e-156">Antes de executar o comando, certifique-se de modificar os valores dos parâmetros em conformidade.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-156">Before executing the command, be sure to modify the parameter values accordingly.</span></span> <span data-ttu-id="f2d3e-157">O nome do cofre deve ser único.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-157">The vault name must be unique.</span></span>

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    <span data-ttu-id="f2d3e-158">Para obter mais informações sobre a criação de um Cofre de Chaves Azure, consulte [Quickstart: set and retrieve a secret from Azure Key Vault using the Azure Portal](/azure/key-vault/quick-create-portal) or [Quickstart: set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span><span class="sxs-lookup"><span data-stu-id="f2d3e-158">For more information about creating an Azure Key Vault, see [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/quick-create-portal) or [Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span></span> <span data-ttu-id="f2d3e-159">Então, prepara-me e recupera um segredo.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-159">Then set and retrieve a secret.</span></span>

2. <span data-ttu-id="f2d3e-160">Crie uma Aplicação AD Azure e uma chave utilizando o portal Azure ou os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-160">Create an Azure AD Application and a key using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    <span data-ttu-id="f2d3e-161">Certifique-se de tomar nota do identificador de aplicações e dos valores secretos porque serão usados nos degraus abaixo.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-161">Be sure to make note of the application identifier and secret values because they'll be used in the steps below.</span></span>

3. <span data-ttu-id="f2d3e-162">Conceda à nova aplicação AD Azure, a leitura de segredos de leitura, utilizando o portal Azure ou os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-162">Grant the newly create Azure AD application the read secrets permissions using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. <span data-ttu-id="f2d3e-163">Crie uma aplicação AD Azure que esteja configurada para o Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-163">Create an Azure AD application that is configured for Partner Center.</span></span> <span data-ttu-id="f2d3e-164">Execute as seguintes ações para completar este passo.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-164">Perform the following actions to complete this step.</span></span>

    - <span data-ttu-id="f2d3e-165">Navegue para a funcionalidade de gestão de [aplicações](https://partner.microsoft.com/pcv/apiintegration/appmanagement) do Painel de Instrumentos do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="f2d3e-165">Browse to the [App management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) feature of the Partner Center Dashboard</span></span>
    - <span data-ttu-id="f2d3e-166">Clique *em Adicionar nova aplicação web* para criar uma nova aplicação AD Azure.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-166">Click *Add new web app* to create a new Azure AD application.</span></span>

    <span data-ttu-id="f2d3e-167">Certifique-se de documentar o ID da *app,\*\*ID da conta*\*\* e valores *chave* porque serão usados nos degraus abaixo.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-167">Be sure to document the *App ID*, \*Account ID\*\*, and *Key* values because they'll be used in the steps below.</span></span>

5. <span data-ttu-id="f2d3e-168">Clone o repositório [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) utilizando o Visual Studio ou o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-168">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command.</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

6. <span data-ttu-id="f2d3e-169">Abra o projeto *PartnerConsent* encontrado no `Partner-Center-DotNet-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-169">Open the *PartnerConsent* project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

7. <span data-ttu-id="f2d3e-170">Povoar as definições de aplicação encontradas no [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-170">Populate the application settings found in the [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)</span></span>

    ```xml
    <!-- AppID that represents CSP application -->
    <add key="ida:CSPApplicationId" value="" />
    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:CSPApplicationSecret" value="" />

    <!--
        Endpoint address for the instance of Azure KeyVault. This is
        the DNS Name for the instance of Key Vault that you provisioned.
     -->
    <add key="KeyVaultEndpoint" value="" />

    <!-- App ID that is given access for KeyVault to store refresh tokens -->
    <add key="ida:KeyVaultClientId" value="" />

    <!--
        Please use certificate as your client secret and deploy the certificate
        to your environment. The following application secret is for sample
        application only. please do not use secret directly from the config file.
    -->
    <add key="ida:KeyVaultClientSecret" value="" />
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="f2d3e-171">Informações sensíveis, como segredos de aplicações, não devem ser armazenadas em ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-171">Sensitive information such as application secrets should not be stored in configuration files.</span></span> <span data-ttu-id="f2d3e-172">Foi feito aqui porque este é um pedido de amostra.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-172">It was done here because this is a sample application.</span></span> <span data-ttu-id="f2d3e-173">Com a sua aplicação de produção recomendamos vivamente que utilize a autenticação baseada em certificados.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-173">With your production application we strongly recommend that you use certificate-based authentication.</span></span> <span data-ttu-id="f2d3e-174">Para mais informações, consulte [as credenciais de Certificado para autenticação de pedidos.]( /azure/active-directory/develop/active-directory-certificate-credentials)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-174">For more information, see [Certificate credentials for application authentication]( /azure/active-directory/develop/active-directory-certificate-credentials).</span></span>

8. <span data-ttu-id="f2d3e-175">Quando executar este projeto de amostra, irá pedir-lhe autenticação.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-175">When you run this sample project, it will prompt you for authentication.</span></span> <span data-ttu-id="f2d3e-176">Após autenticação com sucesso, é solicitado um token de acesso à Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-176">After successfully authenticating, an access token is requested from Azure AD.</span></span> <span data-ttu-id="f2d3e-177">A informação devolvida do Azure AD inclui um token de atualização que é armazenado no caso configurado de Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-177">The information returned from Azure AD includes a refresh token that is stored in the configured instance of Azure Key Vault.</span></span>

## <a name="java-appuser-authentication"></a><span data-ttu-id="f2d3e-178">Java (app+autenticação do utilizador)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-178">Java (app+user authentication)</span></span>

<span data-ttu-id="f2d3e-179">O projeto de amostra [de consentimento do parceiro](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) demonstra como utilizar um website desenvolvido usando JSP para capturar o consentimento, solicitar um token de atualização e loja segura em Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-179">The [partner consent](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) sample project demonstrates how to utilize a website developed using JSP to capture consent, request a refresh token, and secure store in Azure Key Vault.</span></span> <span data-ttu-id="f2d3e-180">Execute o seguinte para criar os pré-requisitos necessários para esta amostra.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-180">Perform the following to create the required prerequisites for this sample.</span></span>

1. <span data-ttu-id="f2d3e-181">Crie uma instância do Cofre de Chaves Azure utilizando o portal Azure ou os seguintes comandos PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-181">Create an instance of Azure Key Vault using the Azure portal or the following PowerShell commands.</span></span> <span data-ttu-id="f2d3e-182">Antes de executar o comando, certifique-se de modificar os valores dos parâmetros em conformidade.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-182">Before executing the command, be sure to modify the parameter values accordingly.</span></span> <span data-ttu-id="f2d3e-183">O nome do cofre deve ser único.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-183">The vault name must be unique.</span></span>

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    <span data-ttu-id="f2d3e-184">Para obter mais informações sobre a criação de um Cofre de Chaves Azure, consulte [Quickstart: set and retrieve a secret from Azure Key Vault using the Azure Portal](/azure/key-vault/quick-create-portal) or [Quickstart: set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span><span class="sxs-lookup"><span data-stu-id="f2d3e-184">For more information about creating an Azure Key Vault, see [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/quick-create-portal) or [Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span></span>

2. <span data-ttu-id="f2d3e-185">Crie uma Aplicação AD Azure e uma chave utilizando o portal Azure ou os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-185">Create an Azure AD Application and a key using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    <span data-ttu-id="f2d3e-186">Certifique-se de documentar o identificador de aplicações e valores secretos porque eles serão usados nos passos abaixo.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-186">Be sure to document the application identifier and secret values because they'll be used in the steps below.</span></span>

3. <span data-ttu-id="f2d3e-187">Conceda à recém-criada aplicação AD AD, as permissões de segredos de leitura usando o portal Azure ou os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-187">Grant the newly created Azure AD application the read secrets permissions using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. <span data-ttu-id="f2d3e-188">Crie uma aplicação AD Azure que esteja configurada para o Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-188">Create an Azure AD application that is configured for Partner Center.</span></span> <span data-ttu-id="f2d3e-189">Execute o seguinte para completar este passo.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-189">Perform the following to complete this step.</span></span>

    - <span data-ttu-id="f2d3e-190">Navegue para a funcionalidade de gestão de [aplicações](https://partner.microsoft.com/pcv/apiintegration/appmanagement) do Painel de Instrumentos do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="f2d3e-190">Browse to the [App management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) feature of the Partner Center Dashboard</span></span>
    - <span data-ttu-id="f2d3e-191">Clique *em Adicionar nova aplicação web* para criar uma nova aplicação AD Azure.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-191">Click *Add new web app* to create a new Azure AD application.</span></span>

    <span data-ttu-id="f2d3e-192">Certifique-se de documentar o ID da *app,\*\*ID da conta*\*\* e valores *chave* porque serão usados nos degraus abaixo.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-192">Be sure to document the *App ID*, \*Account ID\*\*, and *Key* values because they'll be used in the steps below.</span></span>

5. <span data-ttu-id="f2d3e-193">Clone o repositório [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) usando o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="f2d3e-193">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

6. <span data-ttu-id="f2d3e-194">Abra o projeto *PartnerConsent* encontrado no `Partner-Center-Java-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-194">Open the *PartnerConsent* project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

7. <span data-ttu-id="f2d3e-195">Povoar as definições de aplicação encontradas no ficheiro [web.xml](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-195">Populate the application settings found in the [web.xml](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml) file</span></span>

    ```xml
    <filter>
        <filter-name>AuthenticationFilter</filter-name>
        <filter-class>com.microsoft.store.samples.partnerconsent.security.AuthenticationFilter</filter-class>
        <init-param>
            <param-name>client_id</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>client_secret</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>keyvault_base_url</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>keyvault_client_id</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>keyvault_client_secret</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>keyvault_certifcate_path</param-name>
            <param-value></param-value>
        </init-param>
    </filter>
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="f2d3e-196">Informações sensíveis, como segredos de aplicações, não devem ser armazenadas em ficheiros de configurações.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-196">Sensitive information such as application secrets should not be stored in configurations files.</span></span> <span data-ttu-id="f2d3e-197">Foi feito aqui porque este é um pedido de amostra.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-197">It was done here because this is a sample application.</span></span> <span data-ttu-id="f2d3e-198">Com a sua aplicação de produção, recomendamos vivamente que utilize a autenticação baseada em certificados.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-198">With your production application, we strongly recommend that you use certificate based authenticate.</span></span> <span data-ttu-id="f2d3e-199">Para obter mais informações, consulte [a autenticação do Certificado de Cofre chave.](https://github.com/Azure-Samples/key-vault-java-certificate-authentication)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-199">For more information, see [Key Vault Certificate authentication](https://github.com/Azure-Samples/key-vault-java-certificate-authentication).</span></span>

8. <span data-ttu-id="f2d3e-200">Quando executar este projeto de amostra, irá pedir-lhe autenticação.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-200">When you run this sample project, it will prompt you for authentication.</span></span> <span data-ttu-id="f2d3e-201">Após autenticação com sucesso, é solicitado um token de acesso à Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-201">After successfully authenticating, an access token is requested from Azure AD.</span></span> <span data-ttu-id="f2d3e-202">A informação devolvida do Azure AD inclui um token de atualização que é armazenado no caso configurado de Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-202">The information returned from Azure AD includes a refresh token that is stored in the configured instance of Azure Key Vault.</span></span>

## <a name="cloud-solution-provider-authentication"></a><span data-ttu-id="f2d3e-203">Autenticação do Fornecedor de Soluções de Nuvem</span><span class="sxs-lookup"><span data-stu-id="f2d3e-203">Cloud Solution Provider authentication</span></span>

<span data-ttu-id="f2d3e-204">Os parceiros do Cloud Solution Provider podem utilizar o token de atualização obtido através do processo de consentimento do [parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-204">Cloud Solution Provider partners can use the refresh token obtained through the [partner consent](#partner-consent) process.</span></span>

### <a name="samples-for-cloud-solution-provider-authentication"></a><span data-ttu-id="f2d3e-205">Amostras para autenticação do Fornecedor de Solução Cloud</span><span class="sxs-lookup"><span data-stu-id="f2d3e-205">Samples for Cloud Solution Provider authentication</span></span>

<span data-ttu-id="f2d3e-206">Para ajudar os parceiros a entender como realizar cada operação necessária, desenvolvemos as seguintes amostras.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-206">To help partners understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="f2d3e-207">Ao implementar a solução adequada no seu ambiente, é importante que desenvolva uma solução que seja uma reclamação com os seus padrões de codificação e políticas de segurança.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-207">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-csp-authentication"></a><span data-ttu-id="f2d3e-208">.NET (autenticação CSP)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-208">.NET (CSP authentication)</span></span>

1. <span data-ttu-id="f2d3e-209">Se ainda não o fez, execute o processo de consentimento do [parceiro](#partner-consent).</span><span class="sxs-lookup"><span data-stu-id="f2d3e-209">If you have not already done so, perform the [partner consent process](#partner-consent).</span></span>

2. <span data-ttu-id="f2d3e-210">Clone o repositório [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) usando o Visual Studio ou o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="f2d3e-210">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. <span data-ttu-id="f2d3e-211">Abra o `CSPApplication` projeto encontrado no `Partner-Center-DotNet-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-211">Open the `CSPApplication` project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="f2d3e-212">Atualize as definições de aplicação encontradas no ficheiro [App.config.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-212">Update the application settings found in the [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config) file.</span></span>

    ```xml
    <!-- AppID that represents CSP application -->
    <add key="ida:CSPApplicationId" value="" />
    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:CSPApplicationSecret" value="" />

    <!-- Endpoint address for the instance of Azure KeyVault -->
    <add key="KeyVaultEndpoint" value="" />

    <!-- AppID that is given access for keyvault to store the refresh tokens -->
    <add key="ida:KeyVaultClientId" value="" />

    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:KeyVaultClientSecret" value="" />
    ```

5. <span data-ttu-id="f2d3e-213">Desaprove os valores adequados para as variáveis **PartnerId** e **CustomerId** encontradas no ficheiro [Program.cs.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-213">Set the appropriate values for the **PartnerId** and **CustomerId** variables found in the [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs) file.</span></span>

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. <span data-ttu-id="f2d3e-214">Ao executar este projeto de amostra, obtém o token de atualização obtido durante o processo de consentimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-214">When you run this sample project, it obtains the refresh token obtained during the partner consent process.</span></span> <span data-ttu-id="f2d3e-215">Em seguida, solicita um sinal de acesso para interagir com o Partner Center SDK em nome do parceiro.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-215">Then, it requests an access token to interact with the Partner Center SDK on the partner's behalf.</span></span> <span data-ttu-id="f2d3e-216">Por último, solicita um token de acesso para interagir com o Microsoft Graph em nome do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-216">Finally, it requests an access token to interact with Microsoft Graph on behalf of the specified customer.</span></span>

## <a name="java-csp-authentication"></a><span data-ttu-id="f2d3e-217">Java (autenticação CSP)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-217">Java (CSP authentication)</span></span>

1. <span data-ttu-id="f2d3e-218">Se ainda não o fez, execute o processo de consentimento do [parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-218">If you have not done so already, perform the [partner consent process](#partner-consent).</span></span>

2. <span data-ttu-id="f2d3e-219">Clone o repositório [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) usando o Visual Studio ou o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="f2d3e-219">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. <span data-ttu-id="f2d3e-220">Abra o `cspsample` projeto encontrado no `Partner-Center-Java-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-220">Open the `cspsample` project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="f2d3e-221">Atualize as definições de aplicação encontradas no ficheiro [application.properties.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-221">Update the application settings found in the [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties) file.</span></span>

     ```java
    azuread.authority=https://login.microsoftonline.com
    keyvault.baseurl=
    keyvault.clientId=
    keyvault.clientSecret=
    partnercenter.accountId=
    partnercenter.clientId=
    partnercenter.clientSecret=
    ```

5. <span data-ttu-id="f2d3e-222">Ao executar este projeto de amostra, obtém o token de atualização obtido durante o processo de consentimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-222">When you run this sample project, it obtains the refresh token obtained during the partner consent process.</span></span> <span data-ttu-id="f2d3e-223">Em seguida, solicita um sinal de acesso para interagir com o Partner Center SDK em nome do parceiro.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-223">Then, it requests an access token to interact with the Partner Center SDK on the partner's behalf.</span></span>

6. <span data-ttu-id="f2d3e-224">Opcional - descompromete as chamadas da função *RunAzureTask* e *RunGraphTask* se quiser ver como interagir com o Azure Resource Manager e o Microsoft Graph em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-224">Optional - uncomment the *RunAzureTask* and *RunGraphTask* function calls if you want to see how to interact with Azure Resource Manager and Microsoft Graph on behalf of the customer.</span></span>

## <a name="control-panel-provider-authentication"></a><span data-ttu-id="f2d3e-225">Autenticação do Provedor do Painel de Controlo</span><span class="sxs-lookup"><span data-stu-id="f2d3e-225">Control Panel Provider authentication</span></span>

<span data-ttu-id="f2d3e-226">Os fornecedores de painéis de controlo precisam de ter cada parceiro que suportem a executar o processo de consentimento do [parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-226">Control panel vendors need to have each partner they support perform the [partner consent](#partner-consent) process.</span></span> <span data-ttu-id="f2d3e-227">Uma vez concluída a atualização obtida através desse processo é utilizada para aceder à API do Partner Center REST e à API .NET.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-227">Once that is completed the refresh token obtained through that process is used to access the Partner Center REST API and .NET API.</span></span>

### <a name="samples-for-cloud-panel-provider-authentication"></a><span data-ttu-id="f2d3e-228">Amostras para autenticação do Fornecedor de Painéis de Nuvem</span><span class="sxs-lookup"><span data-stu-id="f2d3e-228">Samples for Cloud Panel Provider authentication</span></span>

<span data-ttu-id="f2d3e-229">Para ajudar os fornecedores de painéis de controlo a entender como realizar cada operação necessária, desenvolvemos as seguintes amostras.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-229">To help control panel vendors understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="f2d3e-230">Ao implementar a solução adequada no seu ambiente, é importante que desenvolva uma solução que seja uma reclamação com os seus padrões de codificação e políticas de segurança.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-230">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-cpv-authentication"></a><span data-ttu-id="f2d3e-231">.NET (autenticação cpv)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-231">.NET (CPV authentication)</span></span>

1. <span data-ttu-id="f2d3e-232">Desenvolver e implementar um processo para os parceiros do Cloud Solution Provider fornecerem o consentimento adequado.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-232">Develop and deploy a process for Cloud Solution Provider partners to provide the appropriate consent.</span></span> <span data-ttu-id="f2d3e-233">Para obter mais informações um exemplo, consulte [o consentimento do parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-233">For more information an example, see [partner consent](#partner-consent).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f2d3e-234">As credenciais de utilizador de um parceiro Cloud Solution Provider não devem ser armazenadas.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-234">User credentials from a Cloud Solution Provider partner should not be stored.</span></span> <span data-ttu-id="f2d3e-235">O token de atualização obtido através do processo de consentimento do parceiro deve ser armazenado e usado para solicitar fichas de acesso para interagir com qualquer API da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-235">The refresh token obtained through the partner consent process should be stored and used to request access tokens for interacting with any Microsoft API.</span></span>

2. <span data-ttu-id="f2d3e-236">Clone o repositório [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) usando o Visual Studio ou o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="f2d3e-236">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. <span data-ttu-id="f2d3e-237">Abra o `CPVApplication` projeto encontrado no `Partner-Center-DotNet-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-237">Open the `CPVApplication` project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="f2d3e-238">Atualize as definições de aplicação encontradas no ficheiro [App.config.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-238">Update the application settings found in the [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config) file.</span></span>

    ```xml
    <!-- AppID that represents Control panel vendor application -->
    <add key="ida:CPVApplicationId" value="" />

    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:CPVApplicationSecret" value="" />

    <!-- Endpoint address for the instance of Azure KeyVault -->
    <add key="KeyVaultEndpoint" value="" />

    <!-- AppID that is given access for keyvault to store the refresh tokens -->
    <add key="ida:KeyVaultClientId" value="" />

    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:KeyVaultClientSecret" value="" />
    ```

5. <span data-ttu-id="f2d3e-239">Desaprove os valores adequados para as variáveis **PartnerId** e **CustomerId** encontradas no ficheiro [Program.cs.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-239">Set the appropriate values for the **PartnerId** and **CustomerId** variables found in the [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs) file.</span></span>

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. <span data-ttu-id="f2d3e-240">Ao executar este projeto de amostra, obtém o token de atualização para o parceiro especificado.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-240">When you run this sample project, it obtains the refresh token for the specified partner.</span></span> <span data-ttu-id="f2d3e-241">Em seguida, solicita um token de acesso para aceder ao Partner Center e ao Azure AD Graph em nome do parceiro.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-241">Then, it requests an access token to access Partner Center and Azure AD Graph on behalf of the partner.</span></span> <span data-ttu-id="f2d3e-242">A próxima tarefa que executa é a supressão e criação de autorizações para o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-242">The next task it performs is the deletion and creation of permission grants into the customer tenant.</span></span> <span data-ttu-id="f2d3e-243">Uma vez que não existe qualquer relação entre o fornecedor do painel de controlo e o cliente, estas permissões precisam de ser adicionadas usando a API do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-243">Since there's no relationship between the control panel vendor and the customer, these permissions need to be added using the Partner Center API.</span></span> <span data-ttu-id="f2d3e-244">O exemplo que se segue mostra como fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-244">The following example shows how to accomplish that.</span></span>

    ```csharp
    JObject contents = new JObject
    {
        // Provide your application display name
        ["displayName"] = "CPV Marketplace",

        // Provide your application id
        ["applicationId"] = CPVApplicationId,

        // Provide your application grants
        ["applicationGrants"] = new JArray(
            JObject.Parse("{\"enterpriseApplicationId\": \"00000002-0000-0000-c000-000000000000\", \"scope\":\"Domain.ReadWrite.All,User.ReadWrite.All,Directory.Read.All\"}"), // for Azure AD Graph access,  Directory.Read.All
            JObject.Parse("{\"enterpriseApplicationId\": \"797f4846-ba00-4fd7-ba43-dac1f8f63013\", \"scope\":\"user_impersonation\"}")) // for Azure Resource Manager access
    };

    /**
     * The following steps have to be performed once per customer tenant if your application is
     * a control panel vendor application and requires customer tenant Azure AD Graph access.
     **/

    // delete the previous grant into customer tenant
    JObject consentDeletion = await ApiCalls.DeleteAsync(
        tokenPartnerResult.Item1,
        string.Format("https://api.partnercenter.microsoft.com/v1/customers/{0}/applicationconsents/{1}", CustomerId, CPVApplicationId));

    // create new grants for the application given the setting in application grants payload.
    JObject consentCreation = await ApiCalls.PostAsync(
        tokenPartnerResult.Item1,
        string.Format("https://api.partnercenter.microsoft.com/v1/customers/{0}/applicationconsents", CustomerId),
        contents.ToString());
    ```

<span data-ttu-id="f2d3e-245">Após estas permissões terem sido estabelecidas, a amostra executa operações utilizando o Azure AD Graph em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-245">After these permissions have been established, the sample performs operations using Azure AD Graph on behalf of the customer.</span></span>

## <a name="java-cpv-authentication"></a><span data-ttu-id="f2d3e-246">Java (autenticação cpv)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-246">Java (CPV authentication)</span></span>

1. <span data-ttu-id="f2d3e-247">Desenvolver e implementar um processo para os parceiros do Cloud Solution Provider fornecerem o consentimento adequado.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-247">Develop and deploy a process for Cloud Solution Provider partners to provide the appropriate consent.</span></span> <span data-ttu-id="f2d3e-248">Para mais informações e um exemplo, consulte o consentimento do [parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-248">For more information and an example, see the [partner consent](#partner-consent).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f2d3e-249">As credenciais de utilizador de um parceiro Cloud Solution Provider não devem ser armazenadas.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-249">User credentials from a Cloud Solution Provider partner should not be stored.</span></span> <span data-ttu-id="f2d3e-250">O token de atualização obtido através do processo de consentimento do parceiro deve ser armazenado e usado para solicitar fichas de acesso para interagir com qualquer API da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-250">The refresh token obtained through the partner consent process should be stored and used to request access tokens for interacting with any Microsoft API.</span></span>

2. <span data-ttu-id="f2d3e-251">Clone o repositório [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) usando o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="f2d3e-251">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. <span data-ttu-id="f2d3e-252">Abra o `cpvsample` projeto encontrado no `Partner-Center-Java-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-252">Open the `cpvsample` project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="f2d3e-253">Atualize as definições de aplicação encontradas no ficheiro [application.properties.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-253">Update the application settings found in the [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties) file.</span></span>

    ```java
    azuread.authority=https://login.microsoftonline.com
    keyvault.baseurl=
    keyvault.clientId=
    keyvault.clientSecret=
    partnercenter.accountId=
    partnercenter.clientId=
    partnercenter.clientSecret=
    partnercenter.displayName=
    ```

    <span data-ttu-id="f2d3e-254">O valor para o `partnercenter.displayName` deve ser o nome de exibição da sua aplicação de mercado.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-254">The value for the `partnercenter.displayName` should be the display name of your marketplace application.</span></span>

5. <span data-ttu-id="f2d3e-255">Desaprove os valores adequados para as variáveis **PartnerId** e **customerId** encontradas no ficheiro [.java Programa.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java)</span><span class="sxs-lookup"><span data-stu-id="f2d3e-255">Set the appropriate values for the **partnerId** and **customerId** variables found in the [Program.java](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java) file.</span></span>

    ```java
    partnerId = "SPECIFY-THE-PARTNER-TENANT-ID-HERE";
    customerId = "SPECIFY-THE-CUSTOMER-TENANT-ID-HERE";
    ```

6. <span data-ttu-id="f2d3e-256">Ao executar este projeto de amostra, obtém o token de atualização para o parceiro especificado.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-256">When you run this sample project, it obtains the refresh token for the specified partner.</span></span> <span data-ttu-id="f2d3e-257">Em seguida, solicita um token de acesso para aceder ao Partner Center em nome do parceiro.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-257">Then, it requests an access token to access Partner Center on behalf of the partner.</span></span> <span data-ttu-id="f2d3e-258">A próxima tarefa que executa é a supressão e criação de autorizações para o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-258">The next task it performs is the deletion and creation of permission grants into the customer tenant.</span></span> <span data-ttu-id="f2d3e-259">Uma vez que não existe qualquer relação entre o fornecedor do painel de controlo e o cliente, estas permissões precisam de ser adicionadas usando a API do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-259">Since there's no relationship between the control panel vendor and the customer, these permissions need to be added using the Partner Center API.</span></span> <span data-ttu-id="f2d3e-260">O exemplo a seguir mostra como conceder as permissões.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-260">The following example shows how to grant the permissions.</span></span>

    ```java
    ApplicationGrant azureAppGrant = new ApplicationGrant();

    azureAppGrant.setEnterpriseApplication("797f4846-ba00-4fd7-ba43-dac1f8f63013");
    azureAppGrant.setScope("user_impersonation");

    ApplicationGrant graphAppGrant = new ApplicationGrant();

    graphAppGrant.setEnterpriseApplication("00000002-0000-0000-c000-000000000000");
    graphAppGrant.setScope("Domain.ReadWrite.All,User.ReadWrite.All,Directory.Read.All");

    ApplicationConsent consent = new ApplicationConsent();

    consent.setApplicationGrants(Arrays.asList(azureAppGrant, graphAppGrant));
    consent.setApplicationId(properties.getProperty(PropertyName.PARTNER_CENTER_CLIENT_ID));
    consent.setDisplayName(properties.getProperty(PropertyName.PARTNER_CENTER_DISPLAY_NAME));

    // Deletes the existing grant into the customer it is present.
    partnerOperations.getServiceClient().delete(
        partnerOperations,
        new TypeReference<ApplicationConsent>(){},
        MessageFormat.format(
            "customers/{0}/applicationconsents/{1}",
            customerId,
            properties.getProperty(PropertyName.PARTNER_CENTER_CLIENT_ID)));

    // Consent to the defined applications and the respective scopes.
    partnerOperations.getServiceClient().post(
        partnerOperations,
        new TypeReference<ApplicationConsent>(){},
        MessageFormat.format(
            "customers/{0}/applicationconsents",
            customerId),
        consent);
    ```

<span data-ttu-id="f2d3e-261">Descompromete as chamadas da função *RunAzureTask* e *RunGraphTask* se quiser ver como interagir com o Azure Resource Manager e o Microsoft Graph em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="f2d3e-261">Uncomment the *RunAzureTask* and *RunGraphTask* function calls if you want to see how to interact with Azure Resource Manager and Microsoft Graph on behalf of the customer.</span></span>
