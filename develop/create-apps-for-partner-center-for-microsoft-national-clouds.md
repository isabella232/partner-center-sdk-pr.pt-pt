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
# <a name="register-app-details-for-partner-center-for-microsoft-national-cloud-through-the-azure-portal"></a>Registar detalhes da aplicação para Partner Center para a Microsoft National Cloud através do portal Azure

**Aplica-se a**: Partner Center for Microsoft Cloud Germany | Centro de Parceiros para Microsoft Cloud for US Government

Os desenvolvedores devem registar detalhes sobre a sua aplicação com Azure AD através do portal Azure. Isto ajuda a garantir que apenas as aplicações especificadas são capazes de se conectar aos dados do parceiro e do cliente.

Para o Partner Center for Microsoft Cloud for US Government, atualmente tem de gerir aplicações através do PowerShell. Para mais informações, consulte a [documentação de referência Azure PowerShell.](/powershell/module/Azuread/#applications)

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Esteja ciente dos seguintes requisitos adicionais quando criar uma aplicação para Partner Center para Microsoft Cloud Germany ou Partner Center for Microsoft Cloud for US Government.

## <a name="web-apps"></a>Web Apps

Para aplicações web, utilize os seguintes procedimentos para registar o seu ID de aplicação.

### <a name="create-or-update-web-app"></a>Criar ou atualizar aplicativo web

1. Navegue para o [portal Azure - Página de registos de aplicações](https://go.microsoft.com/fwlink/?linkid=2083908) para registar a sua aplicação. Inicie sessão no portal do Azure com uma conta profissional ou escolar ou uma conta pessoal da Microsoft.

2. Selecione **Novo registo**. Para mais informações, consulte [Quickstart: Registe uma aplicação com o plataforma de identidades da Microsoft](/azure/active-directory/develop/quickstart-register-app).

### <a name="configure-api-access-permissions-for-web-app"></a>Configure permissões de acesso da API para aplicação web

1. Escolha a sua aplicação. Vá a **Definições** da aplicação Web.

2. Na secção **de Acesso API,** escolha **permissões necessárias**

3. Para Windows permissões de diretório Azure Ative:

    1. Escolha **permissões Windows Azure Ative Directory.**

    2. Nas **permissões de Aplicações,** selecione Ler dados do diretório.

    3. Guarde as permissões.

4. Note o ID da aplicação na secção **Propriedades** da sua aplicação web.

### <a name="add-a-secret-key-to-your-app"></a>Adicione uma chave secreta à sua aplicação

1. Aceda à secção **Chaves** da sua aplicação web.

2. Introduza a descrição da chave e selecione a duração de 1 ou 2 anos, conforme necessário.

3. Guarde e copie o valor da chave secreta. **Este valor não será mostrado novamente uma vez que sai desta página.**

Deve ter os seguintes detalhes da configuração da aplicação web:

- ID da aplicação
- Segredo da aplicação

### <a name="register-the-web-app-in-partner-center"></a>Registe a aplicação Web no Partner Center

1. Inicie sessão em [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com).

2. Escolha **o Dashboard,** escolha **Definições Conta** e escolha a **Gestão de Aplicações.**

3. Na secção **Aplicação Web,** escolha **registar a aplicação existente.**

4. Selecione a aplicação web que criou no portal Azure.

5. Escolha **registar a sua aplicação.**

## <a name="native-apps"></a>Aplicações nativas

As aplicações nativas não precisam de ser registadas no Partner Center. Mas estas aplicações precisam de ser configuradas para fornecer acesso às APIs do Partner Center.

>[!NOTE]
>Antes de criar uma aplicação nativa no portal Azure, inicie sessão no Partner Center utilizando as credenciais de utilizador do inquilino do parceiro. Isto cria as configurações no arrendatário para permitir permissões de aplicações.

### <a name="create-native-app"></a>Criar aplicativo nativo

1. Navegue para o [portal Azure - Página de registos de aplicações](https://go.microsoft.com/fwlink/?linkid=2083908) para registar a sua aplicação. Inicie sessão no portal do Azure com uma conta profissional ou escolar ou uma conta pessoal da Microsoft.

2. Selecione **Novo registo**. Para mais informações, consulte [Quickstart: Registe uma aplicação com o plataforma de identidades da Microsoft](/azure/active-directory/develop/quickstart-register-app).

### <a name="configure-api-access-permissions-for-native-app"></a>Configure permissões de acesso da API para app nativa

1. Escolha a sua aplicação. Vai para **Definições.**

2. No Acesso API, escolha **permissões necessárias.**

3. Escolha **permissões Windows Azure Ative Directory.** Nas **permissões delegadas,** selecione estas permissões:

    - **Iniciar sessão e ler o perfil de utilizador**
    - **Ler os dados do diretório**
    - **Aceder ao diretório como o utilizador com sessão iniciada**
    - **Leia todos os grupos**

4. Guarde as permissões.

5. Escolha **Adicionar** as **permissões requeridas.**

6. Escolha **Selecionar uma API**.

    1. Na caixa de pesquisa, insira o **Microsoft Partner Center** e selecione-o na lista de resultados.

    2. Escolha **Selecionar**.

7. Escolha **Permissões Selecione**.

    1. Selecione **Access Partner Center PPE**.
    
    2. Escolha **Selecionar**.

8. Selecione **Concluído**.

>[!IMPORTANT]
> Note o ID da aplicação nas propriedades da sua aplicação.

Não precisa de registar aplicações nativas no Partner Center, no entanto a aplicação nativa deve ser aprovada por administração. Note o ID da aplicação da sua aplicação nativa.
