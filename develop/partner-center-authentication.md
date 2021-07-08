---
title: Partner Center authentication (Autenticação do Centro de Parceiros)
description: O Partner Center utiliza o Azure AD para autenticação e para utilizar as APIs do Centro De Parceiros deve configurar corretamente as suas definições de autenticação.
ms.date: 11/13/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-csp
ms.openlocfilehash: e54feba7ea727bb7f7eff8de76dcdf28c8a453ee
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548078"
---
# <a name="partner-center-authentication"></a><span data-ttu-id="75393-103">Partner Center authentication (Autenticação do Centro de Parceiros)</span><span class="sxs-lookup"><span data-stu-id="75393-103">Partner Center authentication</span></span>

<span data-ttu-id="75393-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="75393-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="75393-105">O Centro de Parceiros utiliza o Azure Active Directory para autenticação.</span><span class="sxs-lookup"><span data-stu-id="75393-105">Partner Center uses Azure Active Directory for authentication.</span></span> <span data-ttu-id="75393-106">Ao interagir com o módulo do PowerShell, o SDK ou a API do Centro de Parceiros, tem de configurar corretamente uma aplicação do Azure Active Directory e, em seguida, pedir um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="75393-106">When interacting with the Partner Center API, SDK, or PowerShell module you must correctly configure an Azure AD application and then request an access token.</span></span> <span data-ttu-id="75393-107">Os tokens de acesso obtidos apenas através de app ou app + autenticação do utilizador podem ser utilizados com o Centro de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="75393-107">Access tokens obtained using app only or app + user authentication can be used with the Partner Center.</span></span> <span data-ttu-id="75393-108">No entanto, há dois itens importantes que precisam de ser considerados</span><span class="sxs-lookup"><span data-stu-id="75393-108">However, there are two important items that need to be considered</span></span>

- <span data-ttu-id="75393-109">Utilize a autenticação de vários fatores ao aceder à API do Centro Parceiro utilizando a app + autenticação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="75393-109">Use multi-factor authentication when accessing the Partner Center API using app + user authentication.</span></span> <span data-ttu-id="75393-110">Para obter mais informações sobre esta alteração, consulte [Ativar o modelo de aplicação seguro](enable-secure-app-model.md).</span><span class="sxs-lookup"><span data-stu-id="75393-110">For more information regarding this change, see [Enable secure application model](enable-secure-app-model.md).</span></span>

- <span data-ttu-id="75393-111">Nem todas as operações da aplicação de suporte API do Partner Center apenas autenticam.</span><span class="sxs-lookup"><span data-stu-id="75393-111">Not all of the operations the Partner Center API support app only authentication.</span></span> <span data-ttu-id="75393-112">Existem certos cenários em que será necessário utilizar a app + a autenticação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="75393-112">There are certain scenarios where you'll be required to use app + user authentication.</span></span> <span data-ttu-id="75393-113">De acordo com o *título pré-requisitos* de cada [artigo,](scenarios.md)encontrará documentação que indique se apenas a autenticação da app, app + autenticação do utilizador, ou ambos são suportados.</span><span class="sxs-lookup"><span data-stu-id="75393-113">Under the *Prerequisites* heading on each [article](scenarios.md), you'll find documentation that states whether app only authentication, app + user authentication, or both are supported.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="75393-114">Configuração inicial</span><span class="sxs-lookup"><span data-stu-id="75393-114">Initial setup</span></span>

1. <span data-ttu-id="75393-115">Para começar, tem de se certificar de que tem uma conta principal do Partner Center e uma conta de parceiro de integração.</span><span class="sxs-lookup"><span data-stu-id="75393-115">To begin, you need to make sure that you have both a primary Partner Center account, and an integration sandbox Partner Center account.</span></span> <span data-ttu-id="75393-116">Para obter mais informações, consulte [configurar contas do Partner Center para acesso a API.](set-up-api-access-in-partner-center.md)</span><span class="sxs-lookup"><span data-stu-id="75393-116">For more information, see [Set up Partner Center accounts for API access](set-up-api-access-in-partner-center.md).</span></span> <span data-ttu-id="75393-117">Tome nota do ID e Secret da App Azure AAD (o segredo do cliente é necessário para a identificação apenas da App) tanto para a sua conta primária como para a sua conta de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="75393-117">Make note of the Azure AAD App registration ID and Secret (client secret is required for App only identification) for both your primary account and your integration sandbox account.</span></span>

2. <span data-ttu-id="75393-118">Inscreva-se no Azure AD a partir do portal Azure.</span><span class="sxs-lookup"><span data-stu-id="75393-118">Sign in to Azure AD from the Azure portal.</span></span> <span data-ttu-id="75393-119">Nas **permissões a outras aplicações,** descreva permissões para **Windows Azure Ative Directory** a **Permissões Delegadas**, e selecione **tanto o Access the directy como utilizador inscrito** e iniciar **sessão e ler o perfil do utilizador.**</span><span class="sxs-lookup"><span data-stu-id="75393-119">In **permissions to other applications**, set permissions for **Windows Azure Active Directory** to **Delegated Permissions**, and select both **Access the directory as the signed-in user** and **Sign in and read user profile**.</span></span>

3. <span data-ttu-id="75393-120">No portal Azure, **adicione a aplicação**.</span><span class="sxs-lookup"><span data-stu-id="75393-120">In the Azure portal, **Add application**.</span></span> <span data-ttu-id="75393-121">Procure por "Microsoft Partner Center", que é a aplicação Microsoft Partner Center.</span><span class="sxs-lookup"><span data-stu-id="75393-121">Search for "Microsoft Partner Center", which is the Microsoft Partner Center application.</span></span> <span data-ttu-id="75393-122">Desa estatudo as **permissões delegadas** para aceder à **API do Centro de Parceiros de Acesso**.</span><span class="sxs-lookup"><span data-stu-id="75393-122">Set the **Delegated Permissions** to **Access Partner Center API**.</span></span> <span data-ttu-id="75393-123">Se estiver a utilizar o Partner Center para o Microsoft Cloud Germany ou o Partner Center para Microsoft Cloud for US Government, este passo é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="75393-123">If you are using Partner Center for Microsoft Cloud Germany or Partner Center for Microsoft Cloud for US Government, this step is mandatory.</span></span> <span data-ttu-id="75393-124">Se estiver a utilizar o exemplo global do Partner Center, este passo é opcional.</span><span class="sxs-lookup"><span data-stu-id="75393-124">If you are using Partner Center global instance, this step is optional.</span></span> <span data-ttu-id="75393-125">Os Parceiros CSP podem usar a funcionalidade de Gestão de Aplicações no portal Partner Center para contornar este passo para o Exemplo global do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="75393-125">CSP Partners can use the App Management feature in the Partner Center portal to bypass this step for Partner Center global instance.</span></span>

## <a name="app-only-authentication"></a><span data-ttu-id="75393-126">Autenticação apenas para aplicativos</span><span class="sxs-lookup"><span data-stu-id="75393-126">App-only authentication</span></span>

<span data-ttu-id="75393-127">Se quiser utilizar a autenticação apenas para aplicações para aceder ao módulo Partner Center REST API, .NET API, Java API ou PowerShell, então pode fazê-lo utilizando as seguintes instruções.</span><span class="sxs-lookup"><span data-stu-id="75393-127">If you would like to use app-only authentication to access the Partner Center REST API, .NET API, Java API, or PowerShell module then you can do so by using the following instructions.</span></span>

## <a name="net-app-only-authentication"></a><span data-ttu-id="75393-128">.NET (autenticação apenas para aplicações)</span><span class="sxs-lookup"><span data-stu-id="75393-128">.NET (app-only authentication)</span></span>

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

## <a name="java-app-only-authentication"></a><span data-ttu-id="75393-129">Java (autenticação apenas para aplicações)</span><span class="sxs-lookup"><span data-stu-id="75393-129">Java (app-only authentication)</span></span>

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

## <a name="rest-app-only-authentication"></a><span data-ttu-id="75393-130">REST (autenticação apenas para aplicações)</span><span class="sxs-lookup"><span data-stu-id="75393-130">REST (app-only authentication)</span></span>

### <a name="rest-request"></a><span data-ttu-id="75393-131">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="75393-131">REST request</span></span>

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

### <a name="rest-response"></a><span data-ttu-id="75393-132">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="75393-132">REST response</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Pragma: no-cache
Content-Type: application/json; charset=utf-8
Expires: -1
Content-Length: 1406

{"token_type":"Bearer","expires_in":"3600","ext_expires_in":"3600","expires_on":"1546469802","not_before":"1546465902","resource":"https://graph.windows.net","access_token":"value-has-been-removed"}
```

## <a name="app--user-authentication"></a><span data-ttu-id="75393-133">App + Autenticação do utilizador</span><span class="sxs-lookup"><span data-stu-id="75393-133">App + User authentication</span></span>

<span data-ttu-id="75393-134">Historicamente, a [concessão de credenciais de senha do proprietário](https://tools.ietf.org/html/rfc6749#section-4.3) de recursos tem sido usada para solicitar um token de acesso para uso com o módulo Partner Center REST API, .NET API, Java API ou PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75393-134">Historically, the [resource owner password credentials grant](https://tools.ietf.org/html/rfc6749#section-4.3) has been used to request an access token for use with the Partner Center REST API, .NET API, Java API, or PowerShell module.</span></span> <span data-ttu-id="75393-135">Este método foi utilizado para solicitar um sinal de acesso a Azure Ative Directory utilizando um identificador de clientes e credenciais de utilizador.</span><span class="sxs-lookup"><span data-stu-id="75393-135">That method was used to request an access token from Azure Active Directory using a client identifier and user credentials.</span></span> <span data-ttu-id="75393-136">No entanto, esta abordagem deixará de funcionar porque o Partner Center requer autenticação de vários fatores, quando se utiliza a app + autenticação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="75393-136">However, this approach will no longer work because Partner Center requires multi-factor authentication, when using app + user authentication.</span></span> <span data-ttu-id="75393-137">Para cumprir este requisito, a Microsoft introduziu uma estrutura segura e escalável para autenticar parceiros Fornecedor de Soluções em Nuvem (CSP) e fornecedores de painéis de controlo (CPV) utilizando a autenticação de vários fatores.</span><span class="sxs-lookup"><span data-stu-id="75393-137">To comply with this requirement Microsoft has introduced a secure, scalable framework for authenticating Cloud Solution Provider (CSP) partners and control panel vendors (CPV) using multi-factor authentication.</span></span> <span data-ttu-id="75393-138">Este quadro é conhecido como o Modelo de Aplicação Segura, e é composto por um processo de consentimento e um pedido de acesso a um token usando um token de atualização.</span><span class="sxs-lookup"><span data-stu-id="75393-138">This framework is known as the Secure Application Model, and it is composed of a consent process and a request for an access token using a refresh token.</span></span>

### <a name="partner-consent"></a><span data-ttu-id="75393-139">Consentimento do parceiro</span><span class="sxs-lookup"><span data-stu-id="75393-139">Partner consent</span></span>

<span data-ttu-id="75393-140">O processo de consentimento do parceiro é um processo interativo em que o parceiro autentica usando a autenticação de vários fatores, consente com a aplicação, e um token de atualização é armazenado num repositório seguro, como Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="75393-140">The partner consent process is an interactive process where the partner authenticates using multi-factor authentication, consents to the application, and a refresh token is stored in a secure repository such as Azure Key Vault.</span></span> <span data-ttu-id="75393-141">Recomendamos que seja utilizada uma conta dedicada para efeitos de integração para este processo.</span><span class="sxs-lookup"><span data-stu-id="75393-141">We recommend that a dedicated account for integration purposes be used for this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75393-142">A solução de autenticação multi-factor adequada deve ser ativada para a conta de serviço utilizada no processo de consentimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="75393-142">The appropriate multi-factor authentication solution should be enabled for the service account used in the partner consent process.</span></span> <span data-ttu-id="75393-143">Se não for, então o token de atualização resultante não estará em conformidade com os requisitos de segurança.</span><span class="sxs-lookup"><span data-stu-id="75393-143">If it isn't then the resulting refresh token will not be compliant with security requirements.</span></span>

### <a name="samples-for-app--user-authentication"></a><span data-ttu-id="75393-144">Amostras para App + Autenticação do Utilizador</span><span class="sxs-lookup"><span data-stu-id="75393-144">Samples for App + User authentication</span></span>

<span data-ttu-id="75393-145">O processo de consentimento do parceiro pode ser realizado de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="75393-145">The partner consent process can be performed in a number of ways.</span></span> <span data-ttu-id="75393-146">Para ajudar os parceiros a entender como realizar cada operação necessária, desenvolvemos as seguintes amostras.</span><span class="sxs-lookup"><span data-stu-id="75393-146">To help partners understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="75393-147">Ao implementar a solução adequada no seu ambiente, é importante que desenvolva uma solução que seja uma reclamação com os seus padrões de codificação e políticas de segurança.</span><span class="sxs-lookup"><span data-stu-id="75393-147">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-appuser-authentication"></a><span data-ttu-id="75393-148">.NET (app+autenticação do utilizador)</span><span class="sxs-lookup"><span data-stu-id="75393-148">.NET (app+user authentication)</span></span>

<span data-ttu-id="75393-149">O projeto de amostra [de consentimento do parceiro](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) demonstra como utilizar um website desenvolvido usando ASP.NET para capturar o consentimento, solicitar um token de atualização e armazená-lo de forma segura no Cofre da Chave Azure.</span><span class="sxs-lookup"><span data-stu-id="75393-149">The [partner consent](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) sample project demonstrates how to utilize a website developed using ASP.NET to capture consent, request a refresh token, and securely store it in Azure Key Vault.</span></span> <span data-ttu-id="75393-150">Execute os seguintes passos para criar os pré-requisitos necessários para esta amostra.</span><span class="sxs-lookup"><span data-stu-id="75393-150">Perform the following steps to create the required prerequisites for this sample.</span></span>

1. <span data-ttu-id="75393-151">Crie uma instância do Cofre de Chaves Azure utilizando o portal Azure ou os seguintes comandos PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75393-151">Create an instance of Azure Key Vault using the Azure portal or the following PowerShell commands.</span></span> <span data-ttu-id="75393-152">Antes de executar o comando, certifique-se de modificar os valores dos parâmetros em conformidade.</span><span class="sxs-lookup"><span data-stu-id="75393-152">Before executing the command, be sure to modify the parameter values accordingly.</span></span> <span data-ttu-id="75393-153">O nome do cofre deve ser único.</span><span class="sxs-lookup"><span data-stu-id="75393-153">The vault name must be unique.</span></span>

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    <span data-ttu-id="75393-154">Para obter mais informações sobre a criação de um Cofre de Chaves Azure, consulte [Quickstart: set and retrieve a secret from Azure Key Vault using the Azure Portal](/azure/key-vault/quick-create-portal) or [Quickstart: set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span><span class="sxs-lookup"><span data-stu-id="75393-154">For more information about creating an Azure Key Vault, see [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/quick-create-portal) or [Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span></span> <span data-ttu-id="75393-155">Então, prepara-me e recupera um segredo.</span><span class="sxs-lookup"><span data-stu-id="75393-155">Then set and retrieve a secret.</span></span>

2. <span data-ttu-id="75393-156">Crie uma Aplicação AD Azure e uma chave utilizando o portal Azure ou os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="75393-156">Create an Azure AD Application and a key using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    <span data-ttu-id="75393-157">Certifique-se de tomar nota do identificador de aplicações e dos valores secretos porque serão usados nos degraus abaixo.</span><span class="sxs-lookup"><span data-stu-id="75393-157">Be sure to make note of the application identifier and secret values because they'll be used in the steps below.</span></span>

3. <span data-ttu-id="75393-158">Conceda à nova aplicação AD Azure, a leitura de segredos de leitura, utilizando o portal Azure ou os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="75393-158">Grant the newly create Azure AD application the read secrets permissions using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. <span data-ttu-id="75393-159">Crie uma aplicação AD Azure que esteja configurada para o Partner Center.</span><span class="sxs-lookup"><span data-stu-id="75393-159">Create an Azure AD application that is configured for Partner Center.</span></span> <span data-ttu-id="75393-160">Execute as seguintes ações para completar este passo.</span><span class="sxs-lookup"><span data-stu-id="75393-160">Perform the following actions to complete this step.</span></span>

    - <span data-ttu-id="75393-161">Navegue para a funcionalidade de gestão de [aplicações](https://partner.microsoft.com/pcv/apiintegration/appmanagement) do Painel de Instrumentos do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="75393-161">Browse to the [App management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) feature of the Partner Center Dashboard</span></span>
    - <span data-ttu-id="75393-162">*Selecione Adicionar uma nova aplicação web* para criar uma nova aplicação AD Azure.</span><span class="sxs-lookup"><span data-stu-id="75393-162">Select *Add new web app* to create a new Azure AD application.</span></span>

    <span data-ttu-id="75393-163">Certifique-se de documentar o ID da *app,\*\*ID da conta*\*\* e valores *chave* porque serão usados nos degraus abaixo.</span><span class="sxs-lookup"><span data-stu-id="75393-163">Be sure to document the *App ID*, \*Account ID\*\*, and *Key* values because they'll be used in the steps below.</span></span>

5. <span data-ttu-id="75393-164">Clone o repositório [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) utilizando Visual Studio ou o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="75393-164">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command.</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

6. <span data-ttu-id="75393-165">Abra o projeto *PartnerConsent* encontrado no `Partner-Center-DotNet-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="75393-165">Open the *PartnerConsent* project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

7. <span data-ttu-id="75393-166">Povoar as definições de aplicação encontradas no [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)</span><span class="sxs-lookup"><span data-stu-id="75393-166">Populate the application settings found in the [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)</span></span>

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
    > <span data-ttu-id="75393-167">Informações sensíveis, como segredos de aplicações, não devem ser armazenadas em ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="75393-167">Sensitive information such as application secrets should not be stored in configuration files.</span></span> <span data-ttu-id="75393-168">Foi feito aqui porque este é um pedido de amostra.</span><span class="sxs-lookup"><span data-stu-id="75393-168">It was done here because this is a sample application.</span></span> <span data-ttu-id="75393-169">Com a sua aplicação de produção recomendamos vivamente que utilize a autenticação baseada em certificados.</span><span class="sxs-lookup"><span data-stu-id="75393-169">With your production application we strongly recommend that you use certificate-based authentication.</span></span> <span data-ttu-id="75393-170">Para mais informações, consulte [as credenciais de Certificado para autenticação de pedidos.]( /azure/active-directory/develop/active-directory-certificate-credentials)</span><span class="sxs-lookup"><span data-stu-id="75393-170">For more information, see [Certificate credentials for application authentication]( /azure/active-directory/develop/active-directory-certificate-credentials).</span></span>

8. <span data-ttu-id="75393-171">Quando executar este projeto de amostra, irá pedir-lhe autenticação.</span><span class="sxs-lookup"><span data-stu-id="75393-171">When you run this sample project, it will prompt you for authentication.</span></span> <span data-ttu-id="75393-172">Após autenticação com sucesso, é solicitado um token de acesso à Azure AD.</span><span class="sxs-lookup"><span data-stu-id="75393-172">After successfully authenticating, an access token is requested from Azure AD.</span></span> <span data-ttu-id="75393-173">A informação devolvida do Azure AD inclui um token de atualização que é armazenado no caso configurado de Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="75393-173">The information returned from Azure AD includes a refresh token that is stored in the configured instance of Azure Key Vault.</span></span>

## <a name="java-appuser-authentication"></a><span data-ttu-id="75393-174">Java (app+autenticação do utilizador)</span><span class="sxs-lookup"><span data-stu-id="75393-174">Java (app+user authentication)</span></span>

<span data-ttu-id="75393-175">O projeto de amostra [de consentimento do parceiro](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) demonstra como utilizar um website desenvolvido usando JSP para capturar o consentimento, solicitar um token de atualização e loja segura em Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="75393-175">The [partner consent](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) sample project demonstrates how to utilize a website developed using JSP to capture consent, request a refresh token, and secure store in Azure Key Vault.</span></span> <span data-ttu-id="75393-176">Execute o seguinte para criar os pré-requisitos necessários para esta amostra.</span><span class="sxs-lookup"><span data-stu-id="75393-176">Perform the following to create the required prerequisites for this sample.</span></span>

1. <span data-ttu-id="75393-177">Crie uma instância do Cofre de Chaves Azure utilizando o portal Azure ou os seguintes comandos PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75393-177">Create an instance of Azure Key Vault using the Azure portal or the following PowerShell commands.</span></span> <span data-ttu-id="75393-178">Antes de executar o comando, certifique-se de modificar os valores dos parâmetros em conformidade.</span><span class="sxs-lookup"><span data-stu-id="75393-178">Before executing the command, be sure to modify the parameter values accordingly.</span></span> <span data-ttu-id="75393-179">O nome do cofre deve ser único.</span><span class="sxs-lookup"><span data-stu-id="75393-179">The vault name must be unique.</span></span>

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    <span data-ttu-id="75393-180">Para obter mais informações sobre a criação de um Cofre de Chaves Azure, consulte [Quickstart: set and retrieve a secret from Azure Key Vault using the Azure Portal](/azure/key-vault/quick-create-portal) or [Quickstart: set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span><span class="sxs-lookup"><span data-stu-id="75393-180">For more information about creating an Azure Key Vault, see [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/quick-create-portal) or [Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span></span>

2. <span data-ttu-id="75393-181">Crie uma Aplicação AD Azure e uma chave utilizando o portal Azure ou os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="75393-181">Create an Azure AD Application and a key using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    <span data-ttu-id="75393-182">Certifique-se de documentar o identificador de aplicações e valores secretos porque eles serão usados nos passos abaixo.</span><span class="sxs-lookup"><span data-stu-id="75393-182">Be sure to document the application identifier and secret values because they'll be used in the steps below.</span></span>

3. <span data-ttu-id="75393-183">Conceda à recém-criada aplicação AD AD, as permissões de segredos de leitura usando o portal Azure ou os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="75393-183">Grant the newly created Azure AD application the read secrets permissions using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. <span data-ttu-id="75393-184">Crie uma aplicação AD Azure que esteja configurada para o Partner Center.</span><span class="sxs-lookup"><span data-stu-id="75393-184">Create an Azure AD application that is configured for Partner Center.</span></span> <span data-ttu-id="75393-185">Execute o seguinte para completar este passo.</span><span class="sxs-lookup"><span data-stu-id="75393-185">Perform the following to complete this step.</span></span>

    - <span data-ttu-id="75393-186">Navegue para a funcionalidade de gestão de [aplicações](https://partner.microsoft.com/pcv/apiintegration/appmanagement) do Painel de Instrumentos do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="75393-186">Browse to the [App management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) feature of the Partner Center Dashboard</span></span>
    - <span data-ttu-id="75393-187">*Selecione Adicionar uma nova aplicação web* para criar uma nova aplicação AD Azure.</span><span class="sxs-lookup"><span data-stu-id="75393-187">Select *Add new web app* to create a new Azure AD application.</span></span>

    <span data-ttu-id="75393-188">Certifique-se de documentar o ID da *app,\*\*ID da conta*\*\* e valores *chave* porque serão usados nos degraus abaixo.</span><span class="sxs-lookup"><span data-stu-id="75393-188">Be sure to document the *App ID*, \*Account ID\*\*, and *Key* values because they'll be used in the steps below.</span></span>

5. <span data-ttu-id="75393-189">Clone o repositório [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) usando o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="75393-189">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

6. <span data-ttu-id="75393-190">Abra o projeto *PartnerConsent* encontrado no `Partner-Center-Java-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="75393-190">Open the *PartnerConsent* project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

7. <span data-ttu-id="75393-191">Povoar as definições de aplicação encontradas no ficheiro [web.xml](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml)</span><span class="sxs-lookup"><span data-stu-id="75393-191">Populate the application settings found in the [web.xml](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml) file</span></span>

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
    > <span data-ttu-id="75393-192">Informações sensíveis, como segredos de aplicações, não devem ser armazenadas em ficheiros de configurações.</span><span class="sxs-lookup"><span data-stu-id="75393-192">Sensitive information such as application secrets should not be stored in configurations files.</span></span> <span data-ttu-id="75393-193">Foi feito aqui porque este é um pedido de amostra.</span><span class="sxs-lookup"><span data-stu-id="75393-193">It was done here because this is a sample application.</span></span> <span data-ttu-id="75393-194">Com a sua aplicação de produção, recomendamos vivamente que utilize a autenticação baseada em certificados.</span><span class="sxs-lookup"><span data-stu-id="75393-194">With your production application, we strongly recommend that you use certificate based authenticate.</span></span> <span data-ttu-id="75393-195">Para obter mais informações, consulte [a autenticação do Certificado de Cofre chave.](https://github.com/Azure-Samples/key-vault-java-certificate-authentication)</span><span class="sxs-lookup"><span data-stu-id="75393-195">For more information, see [Key Vault Certificate authentication](https://github.com/Azure-Samples/key-vault-java-certificate-authentication).</span></span>

8. <span data-ttu-id="75393-196">Quando executar este projeto de amostra, irá pedir-lhe autenticação.</span><span class="sxs-lookup"><span data-stu-id="75393-196">When you run this sample project, it will prompt you for authentication.</span></span> <span data-ttu-id="75393-197">Após autenticação com sucesso, é solicitado um token de acesso à Azure AD.</span><span class="sxs-lookup"><span data-stu-id="75393-197">After successfully authenticating, an access token is requested from Azure AD.</span></span> <span data-ttu-id="75393-198">A informação devolvida do Azure AD inclui um token de atualização que é armazenado no caso configurado de Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="75393-198">The information returned from Azure AD includes a refresh token that is stored in the configured instance of Azure Key Vault.</span></span>

## <a name="cloud-solution-provider-authentication"></a><span data-ttu-id="75393-199">autenticação Fornecedor de Soluções em Nuvem</span><span class="sxs-lookup"><span data-stu-id="75393-199">Cloud Solution Provider authentication</span></span>

<span data-ttu-id="75393-200">Fornecedor de Soluções em Nuvem parceiros podem usar o token de atualização obtido através do processo de consentimento do [parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="75393-200">Cloud Solution Provider partners can use the refresh token obtained through the [partner consent](#partner-consent) process.</span></span>

### <a name="samples-for-cloud-solution-provider-authentication"></a><span data-ttu-id="75393-201">Amostras para autenticação Fornecedor de Soluções em Nuvem</span><span class="sxs-lookup"><span data-stu-id="75393-201">Samples for Cloud Solution Provider authentication</span></span>

<span data-ttu-id="75393-202">Para ajudar os parceiros a entender como realizar cada operação necessária, desenvolvemos as seguintes amostras.</span><span class="sxs-lookup"><span data-stu-id="75393-202">To help partners understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="75393-203">Ao implementar a solução adequada no seu ambiente, é importante que desenvolva uma solução que seja uma reclamação com os seus padrões de codificação e políticas de segurança.</span><span class="sxs-lookup"><span data-stu-id="75393-203">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-csp-authentication"></a><span data-ttu-id="75393-204">.NET (autenticação CSP)</span><span class="sxs-lookup"><span data-stu-id="75393-204">.NET (CSP authentication)</span></span>

1. <span data-ttu-id="75393-205">Se ainda não o fez, execute o processo de consentimento do [parceiro](#partner-consent).</span><span class="sxs-lookup"><span data-stu-id="75393-205">If you have not already done so, perform the [partner consent process](#partner-consent).</span></span>

2. <span data-ttu-id="75393-206">Clone o repositório [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) utilizando Visual Studio ou o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="75393-206">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. <span data-ttu-id="75393-207">Abra o `CSPApplication` projeto encontrado no `Partner-Center-DotNet-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="75393-207">Open the `CSPApplication` project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="75393-208">Atualize as definições de aplicação encontradas no ficheiro [App.config.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config)</span><span class="sxs-lookup"><span data-stu-id="75393-208">Update the application settings found in the [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config) file.</span></span>

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

5. <span data-ttu-id="75393-209">Desaprove os valores adequados para as variáveis **PartnerId** e **CustomerId** encontradas no ficheiro [.cs Programa.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs)</span><span class="sxs-lookup"><span data-stu-id="75393-209">Set the appropriate values for the **PartnerId** and **CustomerId** variables found in the [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs) file.</span></span>

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. <span data-ttu-id="75393-210">Ao executar este projeto de amostra, obtém o token de atualização obtido durante o processo de consentimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="75393-210">When you run this sample project, it obtains the refresh token obtained during the partner consent process.</span></span> <span data-ttu-id="75393-211">Em seguida, solicita um sinal de acesso para interagir com o Partner Center SDK em nome do parceiro.</span><span class="sxs-lookup"><span data-stu-id="75393-211">Then, it requests an access token to interact with the Partner Center SDK on the partner's behalf.</span></span> <span data-ttu-id="75393-212">Por último, solicita um token de acesso para interagir com a Microsoft Graph em nome do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="75393-212">Finally, it requests an access token to interact with Microsoft Graph on behalf of the specified customer.</span></span>

## <a name="java-csp-authentication"></a><span data-ttu-id="75393-213">Java (autenticação CSP)</span><span class="sxs-lookup"><span data-stu-id="75393-213">Java (CSP authentication)</span></span>

1. <span data-ttu-id="75393-214">Se ainda não o fez, execute o processo de consentimento do [parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="75393-214">If you have not done so already, perform the [partner consent process](#partner-consent).</span></span>

2. <span data-ttu-id="75393-215">Clone o repositório [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) utilizando Visual Studio ou o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="75393-215">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. <span data-ttu-id="75393-216">Abra o `cspsample` projeto encontrado no `Partner-Center-Java-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="75393-216">Open the `cspsample` project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="75393-217">Atualize as definições de aplicação encontradas no ficheiro [application.properties.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties)</span><span class="sxs-lookup"><span data-stu-id="75393-217">Update the application settings found in the [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties) file.</span></span>

     ```java
    azuread.authority=https://login.microsoftonline.com
    keyvault.baseurl=
    keyvault.clientId=
    keyvault.clientSecret=
    partnercenter.accountId=
    partnercenter.clientId=
    partnercenter.clientSecret=
    ```

5. <span data-ttu-id="75393-218">Ao executar este projeto de amostra, obtém o token de atualização obtido durante o processo de consentimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="75393-218">When you run this sample project, it obtains the refresh token obtained during the partner consent process.</span></span> <span data-ttu-id="75393-219">Em seguida, solicita um sinal de acesso para interagir com o Partner Center SDK em nome do parceiro.</span><span class="sxs-lookup"><span data-stu-id="75393-219">Then, it requests an access token to interact with the Partner Center SDK on the partner's behalf.</span></span>

6. <span data-ttu-id="75393-220">Opcional - descompromete as chamadas da função *RunAzureTask* e *RunGraphTask* se quiser ver como interagir com o Azure Resource Manager e a Microsoft Graph em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="75393-220">Optional - uncomment the *RunAzureTask* and *RunGraphTask* function calls if you want to see how to interact with Azure Resource Manager and Microsoft Graph on behalf of the customer.</span></span>

## <a name="control-panel-provider-authentication"></a><span data-ttu-id="75393-221">Autenticação do Provedor do Painel de Controlo</span><span class="sxs-lookup"><span data-stu-id="75393-221">Control Panel Provider authentication</span></span>

<span data-ttu-id="75393-222">Os fornecedores de painéis de controlo precisam de ter cada parceiro que suportem a executar o processo de consentimento do [parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="75393-222">Control panel vendors need to have each partner they support perform the [partner consent](#partner-consent) process.</span></span> <span data-ttu-id="75393-223">Uma vez concluída a atualização obtida através desse processo é utilizada para aceder à API do Partner Center REST e à API .NET.</span><span class="sxs-lookup"><span data-stu-id="75393-223">Once that is completed the refresh token obtained through that process is used to access the Partner Center REST API and .NET API.</span></span>

### <a name="samples-for-cloud-panel-provider-authentication"></a><span data-ttu-id="75393-224">Amostras para autenticação do Fornecedor de Painéis de Nuvem</span><span class="sxs-lookup"><span data-stu-id="75393-224">Samples for Cloud Panel Provider authentication</span></span>

<span data-ttu-id="75393-225">Para ajudar os fornecedores de painéis de controlo a entender como realizar cada operação necessária, desenvolvemos as seguintes amostras.</span><span class="sxs-lookup"><span data-stu-id="75393-225">To help control panel vendors understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="75393-226">Ao implementar a solução adequada no seu ambiente, é importante que desenvolva uma solução que seja uma reclamação com os seus padrões de codificação e políticas de segurança.</span><span class="sxs-lookup"><span data-stu-id="75393-226">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-cpv-authentication"></a><span data-ttu-id="75393-227">.NET (autenticação cpv)</span><span class="sxs-lookup"><span data-stu-id="75393-227">.NET (CPV authentication)</span></span>

1. <span data-ttu-id="75393-228">Desenvolver e implementar um processo para Fornecedor de Soluções em Nuvem parceiros fornecer o consentimento adequado.</span><span class="sxs-lookup"><span data-stu-id="75393-228">Develop and deploy a process for Cloud Solution Provider partners to provide the appropriate consent.</span></span> <span data-ttu-id="75393-229">Para obter mais informações um exemplo, consulte [o consentimento do parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="75393-229">For more information an example, see [partner consent](#partner-consent).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="75393-230">As credenciais de utilizador de um parceiro Fornecedor de Soluções em Nuvem não devem ser armazenadas.</span><span class="sxs-lookup"><span data-stu-id="75393-230">User credentials from a Cloud Solution Provider partner should not be stored.</span></span> <span data-ttu-id="75393-231">O token de atualização obtido através do processo de consentimento do parceiro deve ser armazenado e usado para solicitar fichas de acesso para interagir com qualquer API da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="75393-231">The refresh token obtained through the partner consent process should be stored and used to request access tokens for interacting with any Microsoft API.</span></span>

2. <span data-ttu-id="75393-232">Clone o repositório [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) utilizando Visual Studio ou o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="75393-232">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. <span data-ttu-id="75393-233">Abra o `CPVApplication` projeto encontrado no `Partner-Center-DotNet-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="75393-233">Open the `CPVApplication` project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="75393-234">Atualize as definições de aplicação encontradas no ficheiro [App.config.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config)</span><span class="sxs-lookup"><span data-stu-id="75393-234">Update the application settings found in the [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config) file.</span></span>

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

5. <span data-ttu-id="75393-235">Desaprove os valores adequados para as variáveis **PartnerId** e **CustomerId** encontradas no ficheiro [.cs Programa.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs)</span><span class="sxs-lookup"><span data-stu-id="75393-235">Set the appropriate values for the **PartnerId** and **CustomerId** variables found in the [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs) file.</span></span>

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. <span data-ttu-id="75393-236">Ao executar este projeto de amostra, obtém o token de atualização para o parceiro especificado.</span><span class="sxs-lookup"><span data-stu-id="75393-236">When you run this sample project, it obtains the refresh token for the specified partner.</span></span> <span data-ttu-id="75393-237">Em seguida, solicita um token de acesso para o Centro de Parceiros e Azure AD Graph em nome do parceiro.</span><span class="sxs-lookup"><span data-stu-id="75393-237">Then, it requests an access token to access Partner Center and Azure AD Graph on behalf of the partner.</span></span> <span data-ttu-id="75393-238">A próxima tarefa que executa é a supressão e criação de autorizações para o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="75393-238">The next task it performs is the deletion and creation of permission grants into the customer tenant.</span></span> <span data-ttu-id="75393-239">Uma vez que não existe qualquer relação entre o fornecedor do painel de controlo e o cliente, estas permissões precisam de ser adicionadas usando a API do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="75393-239">Since there's no relationship between the control panel vendor and the customer, these permissions need to be added using the Partner Center API.</span></span> <span data-ttu-id="75393-240">O exemplo que se segue mostra como fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="75393-240">The following example shows how to accomplish that.</span></span>

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

<span data-ttu-id="75393-241">Após estas permissões terem sido estabelecidas, a amostra executa operações utilizando a Azure AD Graph em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="75393-241">After these permissions have been established, the sample performs operations using Azure AD Graph on behalf of the customer.</span></span>

## <a name="java-cpv-authentication"></a><span data-ttu-id="75393-242">Java (autenticação cpv)</span><span class="sxs-lookup"><span data-stu-id="75393-242">Java (CPV authentication)</span></span>

1. <span data-ttu-id="75393-243">Desenvolver e implementar um processo para Fornecedor de Soluções em Nuvem parceiros fornecer o consentimento adequado.</span><span class="sxs-lookup"><span data-stu-id="75393-243">Develop and deploy a process for Cloud Solution Provider partners to provide the appropriate consent.</span></span> <span data-ttu-id="75393-244">Para mais informações e um exemplo, consulte o consentimento do [parceiro.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="75393-244">For more information and an example, see the [partner consent](#partner-consent).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="75393-245">As credenciais de utilizador de um parceiro Fornecedor de Soluções em Nuvem não devem ser armazenadas.</span><span class="sxs-lookup"><span data-stu-id="75393-245">User credentials from a Cloud Solution Provider partner should not be stored.</span></span> <span data-ttu-id="75393-246">O token de atualização obtido através do processo de consentimento do parceiro deve ser armazenado e usado para solicitar fichas de acesso para interagir com qualquer API da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="75393-246">The refresh token obtained through the partner consent process should be stored and used to request access tokens for interacting with any Microsoft API.</span></span>

2. <span data-ttu-id="75393-247">Clone o repositório [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) usando o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="75393-247">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. <span data-ttu-id="75393-248">Abra o `cpvsample` projeto encontrado no `Partner-Center-Java-Samples\secure-app-model\keyvault` diretório.</span><span class="sxs-lookup"><span data-stu-id="75393-248">Open the `cpvsample` project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="75393-249">Atualize as definições de aplicação encontradas no ficheiro [application.properties.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties)</span><span class="sxs-lookup"><span data-stu-id="75393-249">Update the application settings found in the [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties) file.</span></span>

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

    <span data-ttu-id="75393-250">O valor para o `partnercenter.displayName` deve ser o nome de exibição da sua aplicação de mercado.</span><span class="sxs-lookup"><span data-stu-id="75393-250">The value for the `partnercenter.displayName` should be the display name of your marketplace application.</span></span>

5. <span data-ttu-id="75393-251">Desaprove os valores adequados para as variáveis **PartnerId** e **customerId** encontradas no ficheiro [.java Programa.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java)</span><span class="sxs-lookup"><span data-stu-id="75393-251">Set the appropriate values for the **partnerId** and **customerId** variables found in the [Program.java](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java) file.</span></span>

    ```java
    partnerId = "SPECIFY-THE-PARTNER-TENANT-ID-HERE";
    customerId = "SPECIFY-THE-CUSTOMER-TENANT-ID-HERE";
    ```

6. <span data-ttu-id="75393-252">Ao executar este projeto de amostra, obtém o token de atualização para o parceiro especificado.</span><span class="sxs-lookup"><span data-stu-id="75393-252">When you run this sample project, it obtains the refresh token for the specified partner.</span></span> <span data-ttu-id="75393-253">Em seguida, solicita um token de acesso para aceder ao Partner Center em nome do parceiro.</span><span class="sxs-lookup"><span data-stu-id="75393-253">Then, it requests an access token to access Partner Center on behalf of the partner.</span></span> <span data-ttu-id="75393-254">A próxima tarefa que executa é a supressão e criação de autorizações para o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="75393-254">The next task it performs is the deletion and creation of permission grants into the customer tenant.</span></span> <span data-ttu-id="75393-255">Uma vez que não existe qualquer relação entre o fornecedor do painel de controlo e o cliente, estas permissões precisam de ser adicionadas usando a API do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="75393-255">Since there's no relationship between the control panel vendor and the customer, these permissions need to be added using the Partner Center API.</span></span> <span data-ttu-id="75393-256">O exemplo a seguir mostra como conceder as permissões.</span><span class="sxs-lookup"><span data-stu-id="75393-256">The following example shows how to grant the permissions.</span></span>

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

<span data-ttu-id="75393-257">Descompromete as chamadas da função *RunAzureTask* e *RunGraphTask* se quiser ver como interagir com o Azure Resource Manager e a Microsoft Graph em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="75393-257">Uncomment the *RunAzureTask* and *RunGraphTask* function calls if you want to see how to interact with Azure Resource Manager and Microsoft Graph on behalf of the customer.</span></span>
