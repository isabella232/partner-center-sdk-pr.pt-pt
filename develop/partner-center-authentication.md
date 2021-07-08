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
# <a name="partner-center-authentication"></a>Partner Center authentication (Autenticação do Centro de Parceiros)

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

O Centro de Parceiros utiliza o Azure Active Directory para autenticação. Ao interagir com o módulo do PowerShell, o SDK ou a API do Centro de Parceiros, tem de configurar corretamente uma aplicação do Azure Active Directory e, em seguida, pedir um token de acesso. Os tokens de acesso obtidos apenas através de app ou app + autenticação do utilizador podem ser utilizados com o Centro de Parceiros. No entanto, há dois itens importantes que precisam de ser considerados

- Utilize a autenticação de vários fatores ao aceder à API do Centro Parceiro utilizando a app + autenticação do utilizador. Para obter mais informações sobre esta alteração, consulte [Ativar o modelo de aplicação seguro](enable-secure-app-model.md).

- Nem todas as operações da aplicação de suporte API do Partner Center apenas autenticam. Existem certos cenários em que será necessário utilizar a app + a autenticação do utilizador. De acordo com o *título pré-requisitos* de cada [artigo,](scenarios.md)encontrará documentação que indique se apenas a autenticação da app, app + autenticação do utilizador, ou ambos são suportados.

## <a name="initial-setup"></a>Configuração inicial

1. Para começar, tem de se certificar de que tem uma conta principal do Partner Center e uma conta de parceiro de integração. Para obter mais informações, consulte [configurar contas do Partner Center para acesso a API.](set-up-api-access-in-partner-center.md) Tome nota do ID e Secret da App Azure AAD (o segredo do cliente é necessário para a identificação apenas da App) tanto para a sua conta primária como para a sua conta de areia de integração.

2. Inscreva-se no Azure AD a partir do portal Azure. Nas **permissões a outras aplicações,** descreva permissões para **Windows Azure Ative Directory** a **Permissões Delegadas**, e selecione **tanto o Access the directy como utilizador inscrito** e iniciar **sessão e ler o perfil do utilizador.**

3. No portal Azure, **adicione a aplicação**. Procure por "Microsoft Partner Center", que é a aplicação Microsoft Partner Center. Desa estatudo as **permissões delegadas** para aceder à **API do Centro de Parceiros de Acesso**. Se estiver a utilizar o Partner Center para o Microsoft Cloud Germany ou o Partner Center para Microsoft Cloud for US Government, este passo é obrigatório. Se estiver a utilizar o exemplo global do Partner Center, este passo é opcional. Os Parceiros CSP podem usar a funcionalidade de Gestão de Aplicações no portal Partner Center para contornar este passo para o Exemplo global do Partner Center.

## <a name="app-only-authentication"></a>Autenticação apenas para aplicativos

Se quiser utilizar a autenticação apenas para aplicações para aceder ao módulo Partner Center REST API, .NET API, Java API ou PowerShell, então pode fazê-lo utilizando as seguintes instruções.

## <a name="net-app-only-authentication"></a>.NET (autenticação apenas para aplicações)

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

## <a name="java-app-only-authentication"></a>Java (autenticação apenas para aplicações)

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

## <a name="rest-app-only-authentication"></a>REST (autenticação apenas para aplicações)

### <a name="rest-request"></a>Pedido de DESCANSO

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

### <a name="rest-response"></a>Resposta do REST

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Pragma: no-cache
Content-Type: application/json; charset=utf-8
Expires: -1
Content-Length: 1406

{"token_type":"Bearer","expires_in":"3600","ext_expires_in":"3600","expires_on":"1546469802","not_before":"1546465902","resource":"https://graph.windows.net","access_token":"value-has-been-removed"}
```

## <a name="app--user-authentication"></a>App + Autenticação do utilizador

Historicamente, a [concessão de credenciais de senha do proprietário](https://tools.ietf.org/html/rfc6749#section-4.3) de recursos tem sido usada para solicitar um token de acesso para uso com o módulo Partner Center REST API, .NET API, Java API ou PowerShell. Este método foi utilizado para solicitar um sinal de acesso a Azure Ative Directory utilizando um identificador de clientes e credenciais de utilizador. No entanto, esta abordagem deixará de funcionar porque o Partner Center requer autenticação de vários fatores, quando se utiliza a app + autenticação do utilizador. Para cumprir este requisito, a Microsoft introduziu uma estrutura segura e escalável para autenticar parceiros Fornecedor de Soluções em Nuvem (CSP) e fornecedores de painéis de controlo (CPV) utilizando a autenticação de vários fatores. Este quadro é conhecido como o Modelo de Aplicação Segura, e é composto por um processo de consentimento e um pedido de acesso a um token usando um token de atualização.

### <a name="partner-consent"></a>Consentimento do parceiro

O processo de consentimento do parceiro é um processo interativo em que o parceiro autentica usando a autenticação de vários fatores, consente com a aplicação, e um token de atualização é armazenado num repositório seguro, como Azure Key Vault. Recomendamos que seja utilizada uma conta dedicada para efeitos de integração para este processo.

> [!IMPORTANT]
> A solução de autenticação multi-factor adequada deve ser ativada para a conta de serviço utilizada no processo de consentimento do parceiro. Se não for, então o token de atualização resultante não estará em conformidade com os requisitos de segurança.

### <a name="samples-for-app--user-authentication"></a>Amostras para App + Autenticação do Utilizador

O processo de consentimento do parceiro pode ser realizado de várias maneiras. Para ajudar os parceiros a entender como realizar cada operação necessária, desenvolvemos as seguintes amostras. Ao implementar a solução adequada no seu ambiente, é importante que desenvolva uma solução que seja uma reclamação com os seus padrões de codificação e políticas de segurança.

## <a name="net-appuser-authentication"></a>.NET (app+autenticação do utilizador)

O projeto de amostra [de consentimento do parceiro](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) demonstra como utilizar um website desenvolvido usando ASP.NET para capturar o consentimento, solicitar um token de atualização e armazená-lo de forma segura no Cofre da Chave Azure. Execute os seguintes passos para criar os pré-requisitos necessários para esta amostra.

1. Crie uma instância do Cofre de Chaves Azure utilizando o portal Azure ou os seguintes comandos PowerShell. Antes de executar o comando, certifique-se de modificar os valores dos parâmetros em conformidade. O nome do cofre deve ser único.

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    Para obter mais informações sobre a criação de um Cofre de Chaves Azure, consulte [Quickstart: set and retrieve a secret from Azure Key Vault using the Azure Portal](/azure/key-vault/quick-create-portal) or [Quickstart: set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell). Então, prepara-me e recupera um segredo.

2. Crie uma Aplicação AD Azure e uma chave utilizando o portal Azure ou os seguintes comandos.

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    Certifique-se de tomar nota do identificador de aplicações e dos valores secretos porque serão usados nos degraus abaixo.

3. Conceda à nova aplicação AD Azure, a leitura de segredos de leitura, utilizando o portal Azure ou os seguintes comandos.

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. Crie uma aplicação AD Azure que esteja configurada para o Partner Center. Execute as seguintes ações para completar este passo.

    - Navegue para a funcionalidade de gestão de [aplicações](https://partner.microsoft.com/pcv/apiintegration/appmanagement) do Painel de Instrumentos do Centro de Parceiros
    - *Selecione Adicionar uma nova aplicação web* para criar uma nova aplicação AD Azure.

    Certifique-se de documentar o ID da *app,**ID da conta*** e valores *chave* porque serão usados nos degraus abaixo.

5. Clone o repositório [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) utilizando Visual Studio ou o seguinte comando.

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

6. Abra o projeto *PartnerConsent* encontrado no `Partner-Center-DotNet-Samples\secure-app-model\keyvault` diretório.

7. Povoar as definições de aplicação encontradas no [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)

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
    > Informações sensíveis, como segredos de aplicações, não devem ser armazenadas em ficheiros de configuração. Foi feito aqui porque este é um pedido de amostra. Com a sua aplicação de produção recomendamos vivamente que utilize a autenticação baseada em certificados. Para mais informações, consulte [as credenciais de Certificado para autenticação de pedidos.]( /azure/active-directory/develop/active-directory-certificate-credentials)

8. Quando executar este projeto de amostra, irá pedir-lhe autenticação. Após autenticação com sucesso, é solicitado um token de acesso à Azure AD. A informação devolvida do Azure AD inclui um token de atualização que é armazenado no caso configurado de Azure Key Vault.

## <a name="java-appuser-authentication"></a>Java (app+autenticação do utilizador)

O projeto de amostra [de consentimento do parceiro](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) demonstra como utilizar um website desenvolvido usando JSP para capturar o consentimento, solicitar um token de atualização e loja segura em Azure Key Vault. Execute o seguinte para criar os pré-requisitos necessários para esta amostra.

1. Crie uma instância do Cofre de Chaves Azure utilizando o portal Azure ou os seguintes comandos PowerShell. Antes de executar o comando, certifique-se de modificar os valores dos parâmetros em conformidade. O nome do cofre deve ser único.

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    Para obter mais informações sobre a criação de um Cofre de Chaves Azure, consulte [Quickstart: set and retrieve a secret from Azure Key Vault using the Azure Portal](/azure/key-vault/quick-create-portal) or [Quickstart: set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).

2. Crie uma Aplicação AD Azure e uma chave utilizando o portal Azure ou os seguintes comandos.

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    Certifique-se de documentar o identificador de aplicações e valores secretos porque eles serão usados nos passos abaixo.

3. Conceda à recém-criada aplicação AD AD, as permissões de segredos de leitura usando o portal Azure ou os seguintes comandos.

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. Crie uma aplicação AD Azure que esteja configurada para o Partner Center. Execute o seguinte para completar este passo.

    - Navegue para a funcionalidade de gestão de [aplicações](https://partner.microsoft.com/pcv/apiintegration/appmanagement) do Painel de Instrumentos do Centro de Parceiros
    - *Selecione Adicionar uma nova aplicação web* para criar uma nova aplicação AD Azure.

    Certifique-se de documentar o ID da *app,**ID da conta*** e valores *chave* porque serão usados nos degraus abaixo.

5. Clone o repositório [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) usando o seguinte comando

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

6. Abra o projeto *PartnerConsent* encontrado no `Partner-Center-Java-Samples\secure-app-model\keyvault` diretório.

7. Povoar as definições de aplicação encontradas no ficheiro [web.xml](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml)

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
    > Informações sensíveis, como segredos de aplicações, não devem ser armazenadas em ficheiros de configurações. Foi feito aqui porque este é um pedido de amostra. Com a sua aplicação de produção, recomendamos vivamente que utilize a autenticação baseada em certificados. Para obter mais informações, consulte [a autenticação do Certificado de Cofre chave.](https://github.com/Azure-Samples/key-vault-java-certificate-authentication)

8. Quando executar este projeto de amostra, irá pedir-lhe autenticação. Após autenticação com sucesso, é solicitado um token de acesso à Azure AD. A informação devolvida do Azure AD inclui um token de atualização que é armazenado no caso configurado de Azure Key Vault.

## <a name="cloud-solution-provider-authentication"></a>autenticação Fornecedor de Soluções em Nuvem

Fornecedor de Soluções em Nuvem parceiros podem usar o token de atualização obtido através do processo de consentimento do [parceiro.](#partner-consent)

### <a name="samples-for-cloud-solution-provider-authentication"></a>Amostras para autenticação Fornecedor de Soluções em Nuvem

Para ajudar os parceiros a entender como realizar cada operação necessária, desenvolvemos as seguintes amostras. Ao implementar a solução adequada no seu ambiente, é importante que desenvolva uma solução que seja uma reclamação com os seus padrões de codificação e políticas de segurança.

## <a name="net-csp-authentication"></a>.NET (autenticação CSP)

1. Se ainda não o fez, execute o processo de consentimento do [parceiro](#partner-consent).

2. Clone o repositório [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) utilizando Visual Studio ou o seguinte comando

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. Abra o `CSPApplication` projeto encontrado no `Partner-Center-DotNet-Samples\secure-app-model\keyvault` diretório.

4. Atualize as definições de aplicação encontradas no ficheiro [App.config.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config)

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

5. Desaprove os valores adequados para as variáveis **PartnerId** e **CustomerId** encontradas no ficheiro [.cs Programa.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs)

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. Ao executar este projeto de amostra, obtém o token de atualização obtido durante o processo de consentimento do parceiro. Em seguida, solicita um sinal de acesso para interagir com o Partner Center SDK em nome do parceiro. Por último, solicita um token de acesso para interagir com a Microsoft Graph em nome do cliente especificado.

## <a name="java-csp-authentication"></a>Java (autenticação CSP)

1. Se ainda não o fez, execute o processo de consentimento do [parceiro.](#partner-consent)

2. Clone o repositório [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) utilizando Visual Studio ou o seguinte comando

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. Abra o `cspsample` projeto encontrado no `Partner-Center-Java-Samples\secure-app-model\keyvault` diretório.

4. Atualize as definições de aplicação encontradas no ficheiro [application.properties.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties)

     ```java
    azuread.authority=https://login.microsoftonline.com
    keyvault.baseurl=
    keyvault.clientId=
    keyvault.clientSecret=
    partnercenter.accountId=
    partnercenter.clientId=
    partnercenter.clientSecret=
    ```

5. Ao executar este projeto de amostra, obtém o token de atualização obtido durante o processo de consentimento do parceiro. Em seguida, solicita um sinal de acesso para interagir com o Partner Center SDK em nome do parceiro.

6. Opcional - descompromete as chamadas da função *RunAzureTask* e *RunGraphTask* se quiser ver como interagir com o Azure Resource Manager e a Microsoft Graph em nome do cliente.

## <a name="control-panel-provider-authentication"></a>Autenticação do Provedor do Painel de Controlo

Os fornecedores de painéis de controlo precisam de ter cada parceiro que suportem a executar o processo de consentimento do [parceiro.](#partner-consent) Uma vez concluída a atualização obtida através desse processo é utilizada para aceder à API do Partner Center REST e à API .NET.

### <a name="samples-for-cloud-panel-provider-authentication"></a>Amostras para autenticação do Fornecedor de Painéis de Nuvem

Para ajudar os fornecedores de painéis de controlo a entender como realizar cada operação necessária, desenvolvemos as seguintes amostras. Ao implementar a solução adequada no seu ambiente, é importante que desenvolva uma solução que seja uma reclamação com os seus padrões de codificação e políticas de segurança.

## <a name="net-cpv-authentication"></a>.NET (autenticação cpv)

1. Desenvolver e implementar um processo para Fornecedor de Soluções em Nuvem parceiros fornecer o consentimento adequado. Para obter mais informações um exemplo, consulte [o consentimento do parceiro.](#partner-consent)

    > [!IMPORTANT]
    > As credenciais de utilizador de um parceiro Fornecedor de Soluções em Nuvem não devem ser armazenadas. O token de atualização obtido através do processo de consentimento do parceiro deve ser armazenado e usado para solicitar fichas de acesso para interagir com qualquer API da Microsoft.

2. Clone o repositório [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) utilizando Visual Studio ou o seguinte comando

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. Abra o `CPVApplication` projeto encontrado no `Partner-Center-DotNet-Samples\secure-app-model\keyvault` diretório.

4. Atualize as definições de aplicação encontradas no ficheiro [App.config.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config)

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

5. Desaprove os valores adequados para as variáveis **PartnerId** e **CustomerId** encontradas no ficheiro [.cs Programa.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs)

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. Ao executar este projeto de amostra, obtém o token de atualização para o parceiro especificado. Em seguida, solicita um token de acesso para o Centro de Parceiros e Azure AD Graph em nome do parceiro. A próxima tarefa que executa é a supressão e criação de autorizações para o inquilino do cliente. Uma vez que não existe qualquer relação entre o fornecedor do painel de controlo e o cliente, estas permissões precisam de ser adicionadas usando a API do Partner Center. O exemplo que se segue mostra como fazê-lo.

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

Após estas permissões terem sido estabelecidas, a amostra executa operações utilizando a Azure AD Graph em nome do cliente.

## <a name="java-cpv-authentication"></a>Java (autenticação cpv)

1. Desenvolver e implementar um processo para Fornecedor de Soluções em Nuvem parceiros fornecer o consentimento adequado. Para mais informações e um exemplo, consulte o consentimento do [parceiro.](#partner-consent)

    > [!IMPORTANT]
    > As credenciais de utilizador de um parceiro Fornecedor de Soluções em Nuvem não devem ser armazenadas. O token de atualização obtido através do processo de consentimento do parceiro deve ser armazenado e usado para solicitar fichas de acesso para interagir com qualquer API da Microsoft.

2. Clone o repositório [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) usando o seguinte comando

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. Abra o `cpvsample` projeto encontrado no `Partner-Center-Java-Samples\secure-app-model\keyvault` diretório.

4. Atualize as definições de aplicação encontradas no ficheiro [application.properties.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties)

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

    O valor para o `partnercenter.displayName` deve ser o nome de exibição da sua aplicação de mercado.

5. Desaprove os valores adequados para as variáveis **PartnerId** e **customerId** encontradas no ficheiro [.java Programa.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java)

    ```java
    partnerId = "SPECIFY-THE-PARTNER-TENANT-ID-HERE";
    customerId = "SPECIFY-THE-CUSTOMER-TENANT-ID-HERE";
    ```

6. Ao executar este projeto de amostra, obtém o token de atualização para o parceiro especificado. Em seguida, solicita um token de acesso para aceder ao Partner Center em nome do parceiro. A próxima tarefa que executa é a supressão e criação de autorizações para o inquilino do cliente. Uma vez que não existe qualquer relação entre o fornecedor do painel de controlo e o cliente, estas permissões precisam de ser adicionadas usando a API do Partner Center. O exemplo a seguir mostra como conceder as permissões.

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

Descompromete as chamadas da função *RunAzureTask* e *RunGraphTask* se quiser ver como interagir com o Azure Resource Manager e a Microsoft Graph em nome do cliente.
