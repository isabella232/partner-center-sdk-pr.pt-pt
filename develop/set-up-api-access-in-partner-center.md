---
title: Set up API access in Partner Center (Configurar o acesso da API no Centro de Parceiros)
description: Configurar contas para o desenvolvimento contra o Partner Center SDK e testar na caixa de areia de integração.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 873ff2ff9cecbfa92429958d3bfe2aa79fc3ad9a
ms.sourcegitcommit: d5de47c08ba661ba5de4935caa6843d7c2c91710
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2020
ms.locfileid: "97769416"
---
# <a name="set-up-api-access-in-partner-center"></a><span data-ttu-id="30069-103">Set up API access in Partner Center (Configurar o acesso da API no Centro de Parceiros)</span><span class="sxs-lookup"><span data-stu-id="30069-103">Set up API access in Partner Center</span></span>

<span data-ttu-id="30069-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="30069-104">**Applies to:**</span></span>

- <span data-ttu-id="30069-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="30069-105">Partner Center</span></span>
- <span data-ttu-id="30069-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="30069-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="30069-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="30069-107">Partner Center for Microsoft Cloud for US Government</span></span>
- <span data-ttu-id="30069-108">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="30069-108">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="30069-109">Este artigo descreve as contas que precisa de desenvolver contra o Partner Center SDK.</span><span class="sxs-lookup"><span data-stu-id="30069-109">This article describes the accounts you need to develop against the Partner Center SDK.</span></span> <span data-ttu-id="30069-110">Este artigo também explica como criar uma [conta de caixa de areia de integração](#integration-sandbox-account) e testar na caixa de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-110">This article also explains how to create an [integration sandbox account](#integration-sandbox-account) and test in the integration sandbox.</span></span>

>[!NOTE]
><span data-ttu-id="30069-111">Para ter acesso a APIs, o seu inquilino deve ser inquilino da CSP e deve ser um fornecedor indireto ou um parceiro de conta direto.</span><span class="sxs-lookup"><span data-stu-id="30069-111">To get access to APIs, your tenant must be a CSP tenant and you must be either an indirect provider or a Direct bill partner.</span></span>

## <a name="account-definitions"></a><span data-ttu-id="30069-112">Definições de conta</span><span class="sxs-lookup"><span data-stu-id="30069-112">Account definitions</span></span>

<span data-ttu-id="30069-113">Para ajudá-lo a integrar e testar a sua integração API, o Partner Center suporta dois tipos de contas:</span><span class="sxs-lookup"><span data-stu-id="30069-113">To help you integrate and test your API integration, Partner Center supports two kinds of accounts:</span></span>

### <a name="primary-partner-account"></a><span data-ttu-id="30069-114">Conta do Parceiro Primário</span><span class="sxs-lookup"><span data-stu-id="30069-114">Primary Partner account</span></span>

<span data-ttu-id="30069-115">Esta conta é onde cria encomendas reais para clientes reais.</span><span class="sxs-lookup"><span data-stu-id="30069-115">This account is where you create real orders for real customers.</span></span> <span data-ttu-id="30069-116">Se efec se fizer quaisquer alterações ou transações quando estiver assinado na conta principal, utilizando o Partner Center SDK ou o Partner Dashboard UI, serão tratados como encomendas oficiais para clientes reais.</span><span class="sxs-lookup"><span data-stu-id="30069-116">If you make any changes or transactions when you are signed in to the primary account, by using either the Partner Center SDK or the Partner Dashboard UI, they will be treated as official orders for real customers.</span></span> <span data-ttu-id="30069-117">Eles serão refletidos na sua fatura, e a sua empresa é responsável por pagá-las.</span><span class="sxs-lookup"><span data-stu-id="30069-117">They will be reflected in your invoice, and your company is responsible for paying for them.</span></span>

### <a name="integration-sandbox-account"></a><span data-ttu-id="30069-118">Conta de sandbox de integração</span><span class="sxs-lookup"><span data-stu-id="30069-118">Integration sandbox account</span></span>

<span data-ttu-id="30069-119">Esta conta destina-se a testar o seu código e a sua integração com as APIs do Partner Center antes de o implementar amplamente.</span><span class="sxs-lookup"><span data-stu-id="30069-119">This account is for testing your code and its integration with the Partner Center APIs before you deploy it broadly.</span></span> <span data-ttu-id="30069-120">As alterações e transações que efeção quando estiver assinado na conta de caixa de areia de integração aparecerão na sua fatura, no entanto, não tem de pagar o valor da fatura.</span><span class="sxs-lookup"><span data-stu-id="30069-120">Changes and transactions you make when you are signed into the integration sandbox account will appear in your invoice, however, you do not have to pay the invoice amount.</span></span> <span data-ttu-id="30069-121">A fatura pdf terá um aviso de isenção como "NÃO PAGAR.</span><span class="sxs-lookup"><span data-stu-id="30069-121">Invoice pdf will have a disclaimer as "DO NOT PAY.</span></span> <span data-ttu-id="30069-122">ESTA É UMA FATURA DE CAIXA DE AREIA E NÃO É NECESSÁRIA NENHUMA AÇÃO."</span><span class="sxs-lookup"><span data-stu-id="30069-122">THIS IS A SANDBOX INVOICE AND NO ACTION IS REQUIRED."</span></span>

<span data-ttu-id="30069-123">A conta de integração sandbox e a conta principal atuam de forma independente, e não partilham contas de administração, contas de utilizador, clientes, encomendas, subscrições ou outros dados.</span><span class="sxs-lookup"><span data-stu-id="30069-123">The integration sandbox account and the primary account act independently, and do not share admin accounts, user accounts, customers, orders, subscriptions, or other data.</span></span>

<span data-ttu-id="30069-124">A caixa de areia de integração suporta transações com um número limitado de clientes, encomendas, subscrições, licenças, etc.</span><span class="sxs-lookup"><span data-stu-id="30069-124">The integration sandbox supports transactions with a limited number of customers, orders, subscriptions, licenses, etc.</span></span>

<span data-ttu-id="30069-125">Por política, as contas de caixa de areia de integração são apenas para efeitos de testes de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-125">By policy, integration sandbox accounts are for integration testing purposes only.</span></span>

<span data-ttu-id="30069-126">Por predefinição, não existe nenhuma conta de sandbox de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-126">By default, there is no integration sandbox account.</span></span> <span data-ttu-id="30069-127">Tem de criar um se pretender utilizar o Partner Center SDK.</span><span class="sxs-lookup"><span data-stu-id="30069-127">You must create one yourself if you plan to use the Partner Center SDK.</span></span>

## <a name="set-up-your-accounts"></a><span data-ttu-id="30069-128">Configurar as suas contas</span><span class="sxs-lookup"><span data-stu-id="30069-128">Set up your accounts</span></span>

<span data-ttu-id="30069-129">Esta secção descreve como configurar uma conta principal do Parceiro e uma conta de areia de integração para o Partner Center SDK.</span><span class="sxs-lookup"><span data-stu-id="30069-129">This section describes how to set up a primary Partner account and an integration sandbox account for the Partner Center SDK.</span></span>

### <a name="create-an-integration-sandbox"></a><span data-ttu-id="30069-130">Criar uma caixa de areia de integração</span><span class="sxs-lookup"><span data-stu-id="30069-130">Create an integration sandbox</span></span>

1. <span data-ttu-id="30069-131">Inscreva-se no Partner Dashboard com uma conta de administração global (a sua conta principal de Parceiro.)</span><span class="sxs-lookup"><span data-stu-id="30069-131">Sign in to Partner Dashboard with a global admin account (your primary Partner account.)</span></span>

2. <span data-ttu-id="30069-132">A partir do menu **Definições** (ícone de engrenagem), escolha **as definições de Parceiro**.</span><span class="sxs-lookup"><span data-stu-id="30069-132">From the **Settings** menu (gear icon), choose **Partner settings**.</span></span>

3. <span data-ttu-id="30069-133">Escolha **o separador caixa de areia integração.**</span><span class="sxs-lookup"><span data-stu-id="30069-133">Choose **Integration sandbox** tab.</span></span>

    >[!NOTE]
    ><span data-ttu-id="30069-134">Se não vir uma opção de caixa de areia integração, pode não ter uma conta de administração global.</span><span class="sxs-lookup"><span data-stu-id="30069-134">If you don't see an Integration sandbox option, you might not have a global admin account.</span></span> <span data-ttu-id="30069-135">Também pode estar a usar uma conta de caixa de areia de integração e já foi criada uma caixa de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-135">You also might be using an integration sandbox account and an integration sandbox has already been set up.</span></span>

4. <span data-ttu-id="30069-136">Introduza as informações de contacto para a conta de administração da caixa de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-136">Enter the contact information for the integration sandbox admin account.</span></span> <span data-ttu-id="30069-137">Em seguida, escolha **Criar conta**.</span><span class="sxs-lookup"><span data-stu-id="30069-137">Then, choose **Create account**.</span></span> <span data-ttu-id="30069-138">Aguarde alguns minutos por uma mensagem de confirmação de que a conta foi criada.</span><span class="sxs-lookup"><span data-stu-id="30069-138">Wait a few minutes for a confirmation message that the account has been created.</span></span>

5. <span data-ttu-id="30069-139">Depois de ver a mensagem de confirmação, inscreva-se no Partner Dashboard.</span><span class="sxs-lookup"><span data-stu-id="30069-139">After you see the confirmation message, sign out of Partner Dashboard.</span></span>

6. <span data-ttu-id="30069-140">Volte a entrar com a sua nova conta de administração de caixas de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-140">Sign back in with your new integration sandbox admin account.</span></span> <span data-ttu-id="30069-141">Certifique-se de que utiliza o formato **username@domain** para as suas credenciais juntamente com a palavra-passe que acabou de especificar.</span><span class="sxs-lookup"><span data-stu-id="30069-141">Be sure to use the format **username@domain** for your credentials along with the password that you just specified.</span></span>

7. <span data-ttu-id="30069-142">Escolha **Configurar conta** acima **das tarefas correntes** para completar a configuração da conta de caixa de areia.</span><span class="sxs-lookup"><span data-stu-id="30069-142">Choose **Set Up Account** above **Current Tasks** to complete the sandbox account setup.</span></span>

### <a name="enable-api-access"></a><span data-ttu-id="30069-143">Permitir o acesso à API</span><span class="sxs-lookup"><span data-stu-id="30069-143">Enable API access</span></span>

<span data-ttu-id="30069-144">Quando a sua conta estiver configurada, tem de ativar o acesso à API para poder utilizar o SDK do Centro de Parceiros com o sandbox de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-144">After your account is set up, you must enable API access before you can use the Partner Center SDK with the integration sandbox.</span></span> <span data-ttu-id="30069-145">Precisa de ativar o acesso à API separadamente para a sua conta de Parceiro principal e a conta de sandbox de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-145">You need to enable access to the API separately for both your primary Partner account and your integration sandbox account.</span></span>

1. <span data-ttu-id="30069-146">Inscreva-se no Partner Dashboard utilizando uma conta de administração global.</span><span class="sxs-lookup"><span data-stu-id="30069-146">Sign into Partner Dashboard using a global admin account.</span></span>

2. <span data-ttu-id="30069-147">A partir do menu **Definições** (ícone de engrenagem), selecione **as definições de Parceiro**.</span><span class="sxs-lookup"><span data-stu-id="30069-147">From the **Settings** menu (gear icon), select **Partner settings**.</span></span>

3. <span data-ttu-id="30069-148">Na página **de definições** de Conta, escolha **a gestão da App.**</span><span class="sxs-lookup"><span data-stu-id="30069-148">On the **Account settings** page, choose **App management**.</span></span>

4. <span data-ttu-id="30069-149">Se ainda não tiver uma aplicação existente, adicione uma nova aplicação web.</span><span class="sxs-lookup"><span data-stu-id="30069-149">If you do not already have an existing app, add a new web app.</span></span> <span data-ttu-id="30069-150">Se tiver uma aplicação web existente, escolha o botão **'Adicionar' ao tecla.**</span><span class="sxs-lookup"><span data-stu-id="30069-150">If you have an existing web app, choose the **Add key** button.</span></span>

5. <span data-ttu-id="30069-151">Copie as informações de registo de aplicações, especialmente a **Chave** se estiver a criar uma aplicação web e armazená-la num local seguro.</span><span class="sxs-lookup"><span data-stu-id="30069-151">Copy the app registration information, especially the **Key** if you're creating a web app, and store it in a safe place.</span></span>

6. <span data-ttu-id="30069-152">Assine fora do Partner Dashboard.</span><span class="sxs-lookup"><span data-stu-id="30069-152">Sign out of Partner Dashboard.</span></span>

7. <span data-ttu-id="30069-153">Volte a entrar com a sua conta de caixa de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-153">Sign back in with your integration sandbox account.</span></span> <span data-ttu-id="30069-154">Repita os passos 2-5 para permitir o acesso da API na caixa de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-154">Repeat steps 2-5 to enable API access in the integration sandbox.</span></span>

## <a name="write-and-test-code"></a><span data-ttu-id="30069-155">Escrever e testar código</span><span class="sxs-lookup"><span data-stu-id="30069-155">Write and test code</span></span>

<span data-ttu-id="30069-156">Pode escrever código e código de teste na caixa de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-156">You can write code and test code in the integration sandbox.</span></span> <span data-ttu-id="30069-157">Você precisará das seguintes informações para configurar a [autenticação do Partner Center](partner-center-authentication.md) com Azure AD.</span><span class="sxs-lookup"><span data-stu-id="30069-157">You'll need the following information to [set up Partner Center authentication](partner-center-authentication.md) with Azure AD.</span></span>

| <span data-ttu-id="30069-158">Nome do item</span><span class="sxs-lookup"><span data-stu-id="30069-158">Item name</span></span> | <span data-ttu-id="30069-159">Localização do item</span><span class="sxs-lookup"><span data-stu-id="30069-159">Item location</span></span> |
| --------- | ------------- |
| <span data-ttu-id="30069-160">ID de aplicativo / ID do cliente</span><span class="sxs-lookup"><span data-stu-id="30069-160">App ID / Client ID</span></span> | <span data-ttu-id="30069-161">A partir do menu **Definições** (ícone de engrenagem), selecione **as definições de Parceiro**.</span><span class="sxs-lookup"><span data-stu-id="30069-161">From the **Settings** menu (gear icon), select **Partner settings**.</span></span> <span data-ttu-id="30069-162">Na página **de definições de Conta,** selecione **Gestão de Aplicações.**</span><span class="sxs-lookup"><span data-stu-id="30069-162">On the **Account settings** page, select **App Management**.</span></span> <span data-ttu-id="30069-163">O ID da aplicação/ID do cliente está listado como **iD da aplicação registada.**</span><span class="sxs-lookup"><span data-stu-id="30069-163">The App ID/Client ID is listed as the **Registered application App ID**.</span></span> |
| <span data-ttu-id="30069-164">Chave</span><span class="sxs-lookup"><span data-stu-id="30069-164">Key</span></span> | <span data-ttu-id="30069-165">Se criou uma aplicação web na secção [Enable API,](#enable-api-access)esta é a chave que guardou no passo 5.</span><span class="sxs-lookup"><span data-stu-id="30069-165">If you created a web app in the section [Enable API access](#enable-api-access), this is the key that you saved in step 5.</span></span> |
| <span data-ttu-id="30069-166">Domínio</span><span class="sxs-lookup"><span data-stu-id="30069-166">Domain</span></span> | <span data-ttu-id="30069-167">O domínio para a caixa de areia de integração.</span><span class="sxs-lookup"><span data-stu-id="30069-167">The domain for the integration sandbox.</span></span> |

## <a name="run-tested-code"></a><span data-ttu-id="30069-168">Executar código testado</span><span class="sxs-lookup"><span data-stu-id="30069-168">Run tested code</span></span>

<span data-ttu-id="30069-169">Para utilizar a sua solução com dados reais do cliente, tem de mudar das credenciais de caixa de areia de integração para as credenciais da sua conta principal do Parceiro.</span><span class="sxs-lookup"><span data-stu-id="30069-169">To use your solution with real customer data, you must change from your integration sandbox credentials to your primary Partner account credentials.</span></span>

<span data-ttu-id="30069-170">Quando estiver pronto para usar o seu código testado na sua conta principal do Parceiro, tem de obter um sinal de segurança AZure.</span><span class="sxs-lookup"><span data-stu-id="30069-170">When you're ready to use your tested code in your primary Partner account, you must get an Azure AD security token.</span></span> <span data-ttu-id="30069-171">Este token de segurança baseia-se na aplicação, chave e domínio do Partner Center (em vez da sua aplicação de caixa de areia de integração, chave e domínio).</span><span class="sxs-lookup"><span data-stu-id="30069-171">This security token is based on your Partner Center app, key and domain (instead of your integration sandbox app, key and domain).</span></span>

1. <span data-ttu-id="30069-172">Siga os passos na [autenticação do Partner Center](partner-center-authentication.md) para obter um token de segurança AZure AD usando as credenciais do Centro de Parceiros Primários.</span><span class="sxs-lookup"><span data-stu-id="30069-172">Follow the steps in [Partner Center authentication](partner-center-authentication.md) to get an Azure AD security token using your primary Partner Center credentials.</span></span> <span data-ttu-id="30069-173">(Já seguiu estes passos para obter um sinal de segurança Azure AD para a sua caixa de areia de integração.)</span><span class="sxs-lookup"><span data-stu-id="30069-173">(You previously followed these steps to get an Azure AD security token for your integration sandbox.)</span></span>

2. <span data-ttu-id="30069-174">Substitua o token de segurança de integração no seu código com o novo token de segurança para a sua conta principal do Parceiro.</span><span class="sxs-lookup"><span data-stu-id="30069-174">Replace the integration security token in your code with the new security token for your primary Partner account.</span></span>
