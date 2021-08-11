---
title: Gerir pagamentos usando a API do Serviço de Pagamento
description: Saiba como utilizar o Partner Center Payout Service API para aceder aos dados do pagamento
ms.date: 06/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: jasongroce
ms.author: sabaja
ms.openlocfilehash: b9bdc6da64a79f4f35466fb62662b086a8e1ab3cadc99c7ca685303752f9d166
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996333"
---
# <a name="manage-payouts-using-the-payout-service-api"></a>Gerir pagamentos usando a API do Serviço de Pagamento

Este artigo explica como pode aceder aos dados do pagamento através das APIs do Serviço de Pagamento em vez da UI do Partner Center. Estas APIs fornecem uma forma programática de fornecer a capacidade da funcionalidade de [dados de Exportação](https://partner.microsoft.com/dashboard/payouts/reports/incentiveexport) no Partner Center.

## <a name="available-apis"></a>APIs disponíveis

Consulte todas as APIs disponíveis nos [Pagamentos de Parceiros.](/rest/api/partner-center/partner-payouts)

## <a name="prerequisites"></a>Pré-requisitos

- [Registe uma aplicação com AAD/Microsoft Identity](/graph/auth-register-app-v2) no portal Azure e adicione os proprietários e funções apropriados à aplicação.
- Instale [Visual Studio](https://visualstudio.microsoft.com/downloads/).

## <a name="register-an-application-with-the-microsoft-identity-platform"></a>Registar uma aplicação na plataforma de identidade da Microsoft

O [plataforma de identidades da Microsoft](/azure/active-directory/develop/v2-overview) ajuda-o a construir aplicações que os seus utilizadores e clientes podem iniciar sação para utilizar as suas identidades ou contas sociais da Microsoft, e fornecer acesso autorizado às suas próprias APIs ou APIs da Microsoft, como a Microsoft Graph.

1. Inicie sessão no [portal do Azure](https://portal.azure.com/) com uma conta profissional ou escolar ou uma conta pessoal da Microsoft.

   Se a sua conta lhe der acesso a mais de um inquilino, selecione a sua conta no canto superior direito e desa cosite a sua sessão de portal para o inquilino AD AZure correto.

2. No painel de navegação à esquerda, selecione o serviço Azure Ative Directory, depois **as inscrições da App,** depois **nova inscrição.** Aparece a página **de inscrição do Registo.**

   :::image type="content" source="./images/manage-payouts/new-app-registration.png" alt-text="Screenshot mostrando ao Registo um ecrã de aplicação no portal Azure.":::

3. Insira as informações de registo do seu pedido:

   - Nome: Introduza um nome significativo da aplicação que será apresentado aos utilizadores da aplicação.
   - Tipos de conta suportados: Selecione quais as contas que a sua candidatura irá suportar.

    | **Tipos de conta suportados**                             | **Descrição**                                                                                            |
    |---------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
    | Apenas contas neste diretório organizacional          | Selecione esta opção se estiver a criar uma aplicação de linha de negócio (LOB). Esta opção não está disponível se não estiver a registar a aplicação num diretório. Esta opção mapeia para o inquilino único do Azure AD.  Esta opção é o padrão, a menos que esteja a registar a aplicação fora de um diretório. Nos casos em que a aplicação é registada fora de um diretório, a predefinição é contas da Microsoft pessoais e de multi-inquilino do Azure AD.             |
    | Contas em qualquer diretório organizacional                | Selecione esta opção se quiser visar todos os clientes comerciais ou pedagógicos.  Esta opção mapeia para um multi-inquilino único do Azure AD. Se registou a aplicação como inquilino único do Azure AD, pode atualizá-la para multi-inquilino do Azure AD e voltar ao inquilino único através do painel Autenticação.                                                                                                                                                  |
    | Contas em qualquer diretório organizacional e contas Microsoft pessoais | Selecione esta opção para visar o maior conjunto de clientes. Esta opção mapeia para contas da Microsoft pessoais e de multi-inquilino do Azure AD.  Se registou a aplicação como multi-inquilino e contas pessoais da Microsoft, não poderá alterar esta seleção na UI. Em vez disso, tem de utilizar o editor de manifesto de aplicação para alterar os tipos de conta suportados.                                                                          |

   - *(opcional)* Redirecione URI: Selecione o tipo de aplicação que está a construir, cliente Web ou Público (mobile & desktop) e, em seguida, introduza o URI de redirecionamento (ou URL de resposta) para a sua aplicação. (O URL de redirecionamento é para onde a resposta de autenticação será enviada após a autenticação do utilizador.) 

      Para aplicações Web, indique o URL base da sua aplicação. Por exemplo, `http://localhost:31544` pode ser o URL de uma aplicação Web em execução no seu computador local. Os utilizadores utilizariam este URL para iniciar sessão numa aplicação de cliente Web.
      Para aplicações cliente públicas, indique o URI utilizado pelo Azure AD para devolver respostas de token. Introduza um valor específico para a aplicação, por exemplo `myapp://auth`.

4. Selecione **Registar**. A Azure AD atribui um ID de aplicação único (cliente) à sua aplicação, e as cargas de página geral da aplicação.

   :::image type="content" source="./images/manage-payouts/register-an-application.png" alt-text=">de texto alt<":::

5. Se quiser adicionar capacidades à sua aplicação, pode selecionar outras opções de configuração, incluindo branding, certificados e segredos, permissões API e muito mais.

## <a name="platform-specific-properties"></a>Propriedades específicas da plataforma

A tabela a seguir mostra as propriedades que precisa de configurar e copiar para diferentes tipos de apps. **Atribuído** significa que deve utilizar o valor atribuído pela Azure AD.

| Tipo de aplicação              | Plataforma | ID da Aplicação (cliente) | Segredo do Cliente | Redirecionar URI/URL | Flow implícito                                                         |
|-----------------------|----------|-------------------------|---------------|------------------|-----------------------------------------------------------------------|
| Nativo/Móvel         | Nativa   | Atribuído                | No            | Atribuído         | No                                                                    |
| Aplicação Web               | Web      | Atribuído                | Yes           | Yes              | O ID aberto opcional Ligação o middleware usa o fluxo híbrido por padrão (Sim) |
| App de página única (SPA) | Web      | Atribuído                | Yes           | Yes              | Sim SPAs usar ID aberto Ligação Flow implícito                            |
| Serviço/Daemon        | Web      | Atribuído                | Yes           | Yes              | No                                                                    |

## <a name="create-a-service-principal"></a>Criar um principal de serviço

Para aceder aos recursos na sua subscrição, tem de atribuir uma função à aplicação. Para ajudar a decidir qual o papel que oferece as permissões certas para a aplicação, consulte [as funções incorporadas do Azure.](/azure/role-based-access-control/built-in-roles)

> [!NOTE]
> Pode definir o âmbito ao nível da subscrição, grupo de recursos ou recurso. As permissões são herdadas para níveis mais baixos de âmbito. Por exemplo, adicionar uma aplicação à função Reader para um grupo de recursos significa que pode ler o grupo de recursos e quaisquer recursos que contenha.

1. No portal Azure, selecione o nível de âmbito para atribuir a aplicação. Por exemplo, para atribuir uma função no âmbito de subscrição, procurar e selecionar **Subscrições**, ou selecionar **Subscrições** na página inicial.

   :::image type="content" source="./images/manage-payouts/search-for-subscriptions.png" alt-text="Screenshot mostrando a pesquisa do ecrã de Subscrições.":::

2. Selecione a subscrição para atribuir o pedido.

   :::image type="content" source="./images/manage-payouts/internal-testing-subscription.png" alt-text="Screenshot mostrando o ecrã de subscrições com bandeira de teste interno definido para verdadeiro.":::

> [!NOTE]
> Se não vir a subscrição que procura, selecione o filtro global de subscrições e certifique-se de que a subscrição desejada está selecionada para o portal.

3. Selecione **o controlo de acesso (IAM)** e, em seguida, selecione Adicionar a atribuição de **função**.

4. Selecione a função que deseja atribuir à aplicação. Por exemplo, para permitir que a aplicação execute ações como reiniciar, iniciar e parar instâncias, selecione a função Contribuinte. Leia mais sobre [as funções disponíveis.](/azure/role-based-access-control/built-in-roles)

   Por predefinição, as aplicações AD do Azure não são apresentadas nas opções disponíveis. Para encontrar a sua aplicação, procure no nome e selecione-o a partir dos resultados. Na imagem abaixo, `example-app` está a aplicação AAD que registou.

   :::image type="content" source="./images/manage-payouts/add-role-assignment.png" alt-text="Screenshot mostrando a interface do utilizador para adicionar uma atribuição de função para uma aplicação de teste.":::

5. Selecione **Guardar**. Pode então ver a sua aplicação na lista de utilizadores com uma função para esse âmbito.

   Pode começar a usar o seu principal de serviço para executar os seus scripts ou aplicações. Para gerir as permissões do seu principal serviço, consulte o estado de consentimento do utilizador, reveja permissões, consulte informações de inscrição e muito mais), consulte as suas aplicações Enterprise no [portal Azure](https://portal.azure.com).

## <a name="set-up-api-permissions"></a>Configurar permissões API

Esta secção fornece instruções sobre como configurar as permissões de API necessárias. Para obter mais informações sobre a configuração das permissões de API do Partner Center, consulte [a autenticação da API do Parceiro.](/partner/develop/api-authentication)

**Conceder autorização para Graph API**

1. Abra as [inscrições](https://go.microsoft.com/fwlink/?linkid=2083908) da App no portal Azure.

2. Selecione uma aplicação ou [crie uma aplicação](/azure/active-directory/develop/quickstart-register-app) se ainda não tiver uma.

3. Na página geral da aplicação, em **Gestão,** selecione **Permissões API,** em seguida, **Adicione uma permissão**.

4. Selecione **Microsoft Graph** da lista de APIs disponíveis.

5. Selecione **permissões delegadas** e adicione permissões necessárias. Para mais informações, consulte [o acesso à aplicação Configure.](/azure/active-directory/develop/quickstart-configure-app-access-web-apis)

   :::image type="content" source="./images/manage-payouts/graph-request-api-permissions.png" alt-text="Screenshot mostrando o ecrã de permissões de pedido no portal Azure com a Microsoft Graph selecionado.":::

**Consentimento para acesso da API ao Partner Center API através da app AAD**

6. Para a sua aplicação, selecione **permissões API**, então, a partir do ecrã de permissões da API request, selecione **Adicionar uma permissão**, em **seguida, APIs a minha organização usa**.

7. Pesquisa rumo à **Microsoft Partner (Microsoft Dev Center) API (4990cffe-04e8-4e8b-808a-1175604b879f)**.

   :::image type="content" source="./images/manage-payouts/partner-api-request-permissions.png" alt-text="Screenshot mostrando o ecrã de permissões API com o Microsoft Partner selecionado.":::

8. Desa estade as permissões delegadas no **Centro de Parceiros.**

   :::image type="content" source="./images/manage-payouts/partner-api-request-permissions.png" alt-text="Screenshot mostrando as permissões delegadas selecionadas para Partner Center no ecrã de permissões da API de pedido.":::

9. Conceder **consentimento para as** APIs.

   :::image type="content" source="./images/manage-payouts/api-permissions.png" alt-text="Screenshot mostrando o toggle para consentimento de administrador no ecrã de permissões API.":::

   Verifique se o consentimento do Administrador está ativado no ecrã de estado do consentimento do Administrador.

   :::image type="content" source="./images/manage-payouts/admin-consent-verification.png" alt-text="Screenshot mostrando o ecrã de estado do consentimento do administrador":::

10. Na secção **autenticação,** certifique-se de que a opção **de fluxos de cliente público** está definida para **Sim**.

    :::image type="content" source="./images/manage-payouts/allow-public-client-flows.png" alt-text="Screenshot mostrando o ecrã de autenticação com Permitir fluxos de clientes públicos definidos para Sim.":::

## <a name="run-the-sample-code-in-visual-studio"></a>Executar o código de amostra em Visual Studio

O código de amostra que mostra como a API pode ser usada para o histórico de pagamentos e transações [encontra-se no partner-Center-Payout-APIs](https://github.com/microsoft/Partner-Center-Payout-APIs) GitHub repo.

### <a name="sample-code-notes"></a>Notas de código de amostra

- A configuração dos segredos e certificados do Cliente, tal como discutido na Autenticação: Não é necessária duas opções de [como criar um principal de serviço no portal Azure.](/azure/active-directory/develop/howto-create-service-principal-portal)
- As contas com autenticação multifactor (MFA) não são suportadas atualmente e causarão um erro.
- A API de pagamento suporta apenas credenciais baseadas no utilizador/palavra-passe.

## <a name="next-steps"></a>Passos seguintes

- [Utilizar o portal para criar uma aplicação e um principal de serviço do Azure AD que possam aceder aos recursos](/azure/active-directory/develop/howto-create-service-principal-portal)
- [Registar uma aplicação na plataforma de identidade da Microsoft](/graph/auth-register-app-v2)
- [Configurar uma aplicação do cliente para aceder a uma API web](/azure/active-directory/develop/quickstart-configure-app-access-web-apis)
