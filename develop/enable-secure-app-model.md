---
title: Ativar o modelo de aplicação seguro
description: Proteja o centro de parceiros e as aplicações do painel de controlo.
ms.date: 01/20/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 9974237f7d4234b782a5b17a65fd52b9024315f848b721c73f4e1d59b69b2930
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994800"
---
# <a name="enabling-the-secure-application-model-framework"></a>Enabling the Secure Application Model framework (Ativar a arquitetura do Modelo de Aplicação Segura)

A Microsoft está a introduzir uma estrutura segura e escalável para autenticar parceiros de soluções de nuvem (CSP) e fornecedores de painéis de controlo (CPV) através da arquitetura de autenticação multi-factor (MFA) Microsoft Azure Ative Directory.

Pode utilizar o novo modelo para elevar a segurança para chamadas de integração da API do Partner Center. Isto ajudará todas as partes (incluindo Microsoft, parceiros CSP e CPVs) a proteger as suas infraestruturas e dados dos clientes contra riscos de segurança.

## <a name="scope"></a>Âmbito

Este artigo diz respeito aos seguintes intervenientes:

- CPVs
  - Um CPV é um fornecedor de software independente que desenvolve aplicações a serem utilizadas por parceiros CSP para integração com as APIs do Centro de Parceiros.
  - Um CPV não é um parceiro CSP com acesso direto ao dashboard ou às APIs do Centro de Parceiros.

- Os fornecedores indiretos da CSP e os parceiros diretos da CSP que estão a utilizar o ID + a autenticação do utilizador e a integrar-se diretamente com as APIs do Partner Center.

## <a name="security-requirements"></a>Requisitos de segurança

Para obter informações sobre os requisitos de segurança, consulte [os Requisitos de Segurança do Parceiro.](/partner-center/partner-security-requirements)

## <a name="secure-application-model"></a>Modelo de aplicação segura

As aplicações do marketplace precisam de personificar os privilégios dos parceiros CSP para chamar APIs da Microsoft. Os ataques de segurança a estas aplicações sensíveis podem levar ao compromisso dos dados dos clientes.

Para uma visão geral e detalhes sobre o novo quadro de autenticação, descarregue o [documento-quadro Do Modelo de Aplicação Segura.](https://assetsprod.microsoft.com/secure-application-model-guide.pdf) Este documento abrange princípios e boas práticas para tornar as aplicações de mercado sustentáveis e robustas a partir de compromissos de segurança.

## <a name="samples"></a>Amostras

Os seguintes documentos de visão geral e código de amostra descrevem como os parceiros podem implementar o quadro do Modelo de Aplicação Segura:

- [Documento geral do CPV](https://assetsprod.microsoft.com/cpv-partner-application-overview.pdf)
- [Documento de visão geral da CSP](https://assetsprod.microsoft.com/csp-partner-application-overview.pdf)
- [.AMOSTRAS LÍQUIDAS](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)
- [Amostras de Java](https://github.com/microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model)

    [!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

- [Instruções e amostras de REPOUSO](#rest)
- [Instruções e amostras powerShell](#powershell)

## <a name="rest"></a>REST

Para então fazer chamadas REST com o quadro do Modelo de Aplicação Segura com código de amostra, siga estes passos:

1. [Criar uma aplicação Web](#create-a-web-app)

2. [Obtenha um código de autorização](#get-authorization-code)

3. [Obter um token refrescante](#get-refresh-token)

4. [Obter um token de acesso](#get-access-token)

5. [Faça uma chamada à API do Centro de Parceiros](#make-partner-center-api-calls)

> [!TIP]
> Pode utilizar o módulo Partner Center PowerShell para obter um código de autorização e um token de atualização. Pode escolher esta opção no lugar dos passos 2 e 3. Para obter mais informações, consulte a [secção PowerShell e os exemplos](#powershell).

### <a name="create-a-web-app"></a>Criar uma aplicação Web

Tem de criar e registar uma aplicação web no Partner Center antes de e fazer chamadas REST.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).

2. Crie uma aplicação Azure Ative Directory (Azure AD).

3. Forneça permissões de candidatura delegadas aos seguintes recursos, *dependendo dos requisitos da sua aplicação.* Se necessário, pode adicionar mais permissões delegadas para recursos de aplicação.

   1. **Microsoft Partner Center** (alguns inquilinos mostram isto como **SampleBECApp)**

   2. **APIs de gestão de Azure** (se estiver a planear ligar para a Azure APIs)

   3. **Microsoft Azure Active Directory**

4. Certifique-se de que o URL inicial da sua aplicação está definido para um ponto final onde uma aplicação web ao vivo está em execução. Esta aplicação terá de aceitar o código de [autorização](#get-authorization-code) a partir da chamada de login Azure AD. Por exemplo, no código de exemplo na [secção seguinte,](#get-authorization-code)a aplicação web está em execução `https://localhost:44395/` em .

5. Note as seguintes informações a partir das definições da sua aplicação web em Azure AD:

   - ID da aplicação
   - Segredo da aplicação

> [!NOTE]
> Recomenda-se a [utilização de um certificado como segredo de aplicação.](/azure/active-directory/develop/active-directory-certificate-credentials) No entanto, também pode criar uma chave de aplicação no portal Azure. O código [de](#get-authorization-code) amostra na secção seguinte utiliza uma chave de aplicação.

### <a name="get-authorization-code"></a>Obter código de autorização

Tem de obter um código de autorização para que a sua aplicação web aceite a partir da chamada de login Azure AD:

1. Faça login no Azure AD no seguinte URL: [https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1) . Certifique-se de que faz login na conta de utilizador a partir da qual fará chamadas API do Partner Center (como um agente administrativo ou conta de agente de vendas).

2. Substitua **o ID da aplicação Ad** (GUID) pela aplicação Azure.id.

3. Quando solicitado, inicie sessão com a sua conta de utilizador com MFA configurada.

4. Quando solicitado, introduza informações adicionais de MFA (número de telefone ou endereço de e-mail) para verificar o seu login.

5. Depois de iniciar sessão, o navegador irá redirecionar a chamada para o ponto final da sua aplicação web com o seu código de autorização. Por exemplo, o seguinte código de amostra redireciona para `https://localhost:44395/` .

#### <a name="authorization-code-call-trace"></a>Traço de chamada de código de autorização

```http
POST https://localhost:44395/ HTTP/1.1
Origin: https://login.microsoftonline.com
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Referrer: https://login.microsoftonline.com/kmsi
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Cookie: OpenIdConnect.nonce.hOMjjrivcxzuI4YqAw4uYC%2F%2BILFk4%2FCx3kHTHP3lBvA%3D=dHVyRXdlbk9WVUZFdlFONVdiY01nNEpUc0JRR0RiYWFLTHhQYlRGNl9VeXJqNjdLTGV3cFpIWFg1YmpnWVdQUURtN0dvMkdHS2kzTm02NGdQS09veVNEbTZJMDk1TVVNYkczYmstQmlKUzFQaTBFMEdhNVJGVHlES2d3WGlCSlVlN1c2UE9sd2kzckNrVGN2RFNULWdHY2JET3RDQUxSaXRfLXZQdG00RnlUM0E1TUo1YWNKOWxvQXRwSkhRYklQbmZUV3d3eHVfNEpMUUthMFlQUFgzS01RS2NvMXYtbnV4UVJOYkl4TTN0cw%3D%3D

code=AuthorizationCodeValue&id_token=IdTokenValue&<rest of properties for state>
```

### <a name="get-refresh-token"></a>Obter token refresh

Em seguida, deve utilizar o seu código de autorização para obter um token de atualização:

1. Faça uma chamada POST para o ponto final de login Azure AD `https://login.microsoftonline.com/CSPTenantID/oauth2/token` com o código de autorização. Por exemplo, consulte a seguinte [chamada de amostra](#sample-refresh-call).

2. Reparem no token de atualização que é devolvido.

3. Guarde o token refresh no Azure Key Vault. Para mais informações, consulte a documentação da [API key Vault](/rest/api/keyvault/).

> [!IMPORTANT]
> O token de atualização deve ser [armazenado como um segredo](/rest/api/keyvault/setsecret/setsecret) no Key Vault.

#### <a name="sample-refresh-call"></a>Chamada de atualização de amostra

Pedido de espaço reservado:

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 966
Expect: 100-continue
```

Corpo do pedido:

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id&client_secret=Application-Secret&grant_type=authorization_code&code=AuthorizationCodeValue
```

Resposta do espaço reservado:

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

Corpo de resposta:

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3599","ext_expires_in":"3599","expires_on":"1547579127","not_before":"1547575227","resource":"https://api.partnercenter.microsoft.com","access_token":"Access
```

### <a name="get-access-token"></a>Obter ficha de acesso

Tem de obter um token de acesso antes de poder fazer chamadas para as APIs do Centro de Parceiros. Você deve usar um token de atualização para obter um token de acesso porque os tokens de acesso geralmente têm uma vida útil muito limitada (por exemplo, menos de uma hora).

Pedido de espaço reservado:

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 1212
Expect: 100-continue
```

Corpo do pedido:

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id &client_secret= Application-Secret&grant_type=refresh_token&refresh_token=RefreshTokenVlaue&scope=openid
```

Resposta do espaço reservado:

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

Corpo de resposta:

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3600","ext_expires_in":"3600","expires_on":"1547581389","not_before":"1547577489","resource":"https://api.partnercenter.microsoft.com","access_token":"AccessTokenValue","id_token":"IDTokenValue"}
```

### <a name="make-partner-center-api-calls"></a>Faça chamadas API do Centro Parceiro

Você deve usar o seu token de acesso para ligar para as APIs do Centro Parceiro. Consulte a chamada de exemplo a seguir.

#### <a name="example-partner-center-api-call"></a>Chamada API do Centro parceiro de exemplo

```http
GET https://api.partnercenter.microsoft.com/v1/customers/CustomerTenantId/users HTTP/1.1
Authorization: Bearer AccessTokenValue
Accept: application/json
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Pode utilizar o [módulo PowerShell do Partner Center](https://www.powershellgallery.com/packages/PartnerCenter) para reduzir a infraestrutura necessária para trocar um código de autorização para um token de acesso. Este método é opcional para fazer [chamadas de Partner Center REST](#rest).

Para obter mais informações sobre este processo, consulte a documentação [Secure App Model](/powershell/partnercenter/secure-app-model) PowerShell.

1. Instale os módulos AD AD e Partner Center PowerShell.

    ```powershell
    Install-Module AzureAD
    ```

    ```powershell
    Install-Module PartnerCenter
    ```

2. Utilize o comando **[New-PartnerAccessToken](/powershell/module/partnercenter/new-partneraccesstoken)** para executar o processo de consentimento e capturar o token de atualização necessário.

    ```powershell
    $credential = Get-Credential

    $token = New-PartnerAccessToken -ApplicationId 'xxxx-xxxx-xxxx-xxxx' -Scopes 'https://api.partnercenter.microsoft.com/user_impersonation' -ServicePrincipal -Credential $credential -Tenant 'yyyy-yyyy-yyyy-yyyy' -UseAuthorizationCode
    ```

    > [!NOTE]
    > O parâmetro **ServicePrincipal** é utilizado com o comando **New-PartnerAccessToken** porque está a ser utilizada uma aplicação AD Azure com um tipo de **Web/API.** Este tipo de aplicação requer que um identificador de clientes e segredo seja incluído no pedido de token de acesso. Quando o comando **Get-Credential** for invocado, será solicitado que introduza um nome de utilizador e senha. Introduza o identificador de aplicação como o nome de utilizador. Insira o segredo da aplicação como senha. Quando o comando **New-PartnerAccessToken** for invocado, será solicitado a introduzir novamente credenciais. Insira as credenciais para a conta de serviço que está a usar. Esta conta de serviço deve ser uma conta parceira com permissões apropriadas.

3. Copie o valor simbólico da atualização.

    ```powershell
    $token.RefreshToken | clip
    ```

Deve armazenar o valor simbólico da atualização num repositório seguro, como o Azure Key Vault. Para obter mais informações sobre como alavancar o módulo de aplicação seguro com o PowerShell, consulte o artigo [de autenticação de vários fatores.](/powershell/partnercenter/multi-factor-auth)
