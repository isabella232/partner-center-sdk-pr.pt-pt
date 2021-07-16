---
title: Set up API access in Partner Center (Configurar o acesso da API no Centro de Parceiros)
description: Configurar contas para o desenvolvimento contra o Partner Center SDK e testar na caixa de areia de integração.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: db7d9bba34abadc907910c68c4a5583ed1f530f4
ms.sourcegitcommit: de1e68545d37d7fa1862788f7fa8c84a9c4f2795
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282097"
---
# <a name="set-up-api-access-in-partner-center"></a>Set up API access in Partner Center (Configurar o acesso da API no Centro de Parceiros)

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud for US Government | Centro de Parceiros para Microsoft Cloud Germany

Este artigo descreve as contas que precisa de desenvolver contra o Partner Center SDK. Este artigo também explica como criar uma [conta de caixa de areia de integração](#integration-sandbox-account) e testar na caixa de areia de integração.

>[!NOTE]
>Para ter acesso a APIs, o seu inquilino deve ser inquilino da CSP e deve ser um fornecedor indireto ou um parceiro de conta direto.

## <a name="account-definitions"></a>Definições de conta

Para ajudá-lo a integrar e testar a sua integração API, o Partner Center suporta dois tipos de contas:

### <a name="primary-partner-account"></a>Conta do Parceiro Primário

Esta conta é onde cria encomendas reais para clientes reais. Se efec se fizer quaisquer alterações ou transações quando estiver assinado na conta principal, utilizando o Partner Center SDK ou o Partner Dashboard UI, serão tratados como encomendas oficiais para clientes reais. Eles serão refletidos na sua fatura, e a sua empresa é responsável por pagá-las.

### <a name="integration-sandbox-account"></a>Conta de sandbox de integração

Esta conta destina-se a testar o seu código e a sua integração com as APIs do Partner Center antes de o implementar amplamente. As alterações e transações que efeção quando estiver assinado na conta de caixa de areia de integração aparecerão na sua fatura, no entanto, não tem de pagar o valor da fatura. A fatura pdf terá um aviso de isenção como "NÃO PAGAR. ESTA É UMA FATURA DE CAIXA DE AREIA E NÃO É NECESSÁRIA NENHUMA AÇÃO."

A conta de integração sandbox e a conta principal atuam de forma independente, e não partilham contas de administração, contas de utilizador, clientes, encomendas, subscrições ou outros dados.

A caixa de areia de integração suporta transações com um número limitado de clientes, encomendas, subscrições, licenças, etc.

Por política, as contas de caixa de areia de integração são apenas para efeitos de testes de integração.

Por predefinição, não existe nenhuma conta de sandbox de integração. Tem de criar um se pretender utilizar o Partner Center SDK.

## <a name="set-up-your-accounts"></a>Configurar as suas contas

Esta secção descreve como configurar uma conta principal do Parceiro e uma conta de areia de integração para o Partner Center SDK.

### <a name="create-an-integration-sandbox"></a>Criar uma caixa de areia de integração

1. Inscreva-se no Partner Dashboard com uma conta de administração global (a sua conta principal de Parceiro.)

2. A partir do menu **Definições** (ícone de engrenagem), escolha **as definições de Conta**.

3. Escolha **o separador caixa de areia integração.**

    >[!NOTE]
    >Se não vir uma opção de caixa de areia integração, pode não ter uma conta de administração global. Também pode estar a usar uma conta de caixa de areia de integração e já foi criada uma caixa de areia de integração.

4. Introduza as informações de contacto para a conta de administração da caixa de areia de integração. Em seguida, escolha **Criar conta**. Aguarde alguns minutos por uma mensagem de confirmação de que a conta foi criada.

5. Depois de ver a mensagem de confirmação, inscreva-se no Partner Dashboard.

6. Volte a entrar com a sua nova conta de administração de caixas de areia de integração. Certifique-se de que utiliza o formato **username@domain** para as suas credenciais juntamente com a palavra-passe que especificou.

7. Escolha **Configurar conta** acima **das tarefas correntes** para completar a configuração da conta de caixa de areia.

### <a name="enable-api-access"></a>Permitir o acesso à API

Quando a sua conta estiver configurada, tem de ativar o acesso à API para poder utilizar o SDK do Centro de Parceiros com o sandbox de integração. Precisa de ativar o acesso à API separadamente para a sua conta de Parceiro principal e a conta de sandbox de integração.

1. Inscreva-se no Partner Dashboard utilizando uma conta de administração global.

2. A partir do menu **Definições** (ícone de engrenagem), selecione **definições de Conta**.

3. Na página **de definições** de Conta, escolha **a gestão da App.**

4. Se ainda não tiver uma aplicação existente, adicione uma nova aplicação web. Se tiver uma aplicação web existente, escolha o botão **'Adicionar' ao tecla.**

5. Copie as informações de registo de aplicações, especialmente a **Chave** se estiver a criar uma aplicação web e armazená-la num local seguro.

6. Assine fora do Partner Dashboard.

7. Volte a entrar com a sua conta de caixa de areia de integração. Repita os passos 2-5 para permitir o acesso da API na caixa de areia de integração.

## <a name="write-and-test-code"></a>Escrever e testar código

Pode escrever código e código de teste na caixa de areia de integração. Você precisará das seguintes informações para configurar a [autenticação do Partner Center](partner-center-authentication.md) com Azure AD.

| Nome do item | Localização do item |
| --------- | ------------- |
| ID de aplicativo / ID do cliente | A partir do menu **Definições** (ícone de engrenagem), selecione **definições de Conta**. Na página **de definições de Conta,** selecione **Gestão de Aplicações.** O ID da aplicação/ID do cliente está listado como **iD da aplicação registada.** |
| Chave | Se criou uma aplicação web na secção [Enable API,](#enable-api-access)esta é a chave que guardou no passo 5. |
| Domínio | O domínio para a caixa de areia de integração. |

## <a name="run-tested-code"></a>Executar código testado

Para utilizar a sua solução com dados reais do cliente, tem de mudar das credenciais de caixa de areia de integração para as credenciais da sua conta principal do Parceiro.

Quando estiver pronto para usar o seu código testado na sua conta principal do Parceiro, tem de obter um sinal de segurança AZure. Este token de segurança baseia-se na aplicação, chave e domínio do Partner Center (em vez da sua aplicação de caixa de areia de integração, chave e domínio).

1. Siga os passos na [autenticação do Partner Center](partner-center-authentication.md) para obter um token de segurança AZure AD usando as credenciais do Centro de Parceiros Primários. (Já seguiu estes passos para obter um sinal de segurança Azure AD para a sua caixa de areia de integração.)

2. Substitua o token de segurança de integração no seu código com o novo token de segurança para a sua conta principal do Parceiro.
