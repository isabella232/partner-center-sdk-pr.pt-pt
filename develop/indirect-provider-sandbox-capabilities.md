---
title: Capacidades de fornecedor indireto CSP na Caixa de Areia
description: Os fornecedores indiretos podem criar revendedores indiretos na Caixa de Areia para efeitos de teste.
ms.date: 05/20/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vinayks-ms
ms.author: vinayks
ms.openlocfilehash: da35dadd4e13247e923259a1cf3a67852f4b9e00
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445906"
---
# <a name="csp-indirect-provider-sandbox-capabilities-for-creating-indirect-reseller-accounts"></a><span data-ttu-id="e1bd8-103">Capacidades de caixa de areia do fornecedor CSP indireto para criar contas de revendedores indiretos</span><span class="sxs-lookup"><span data-stu-id="e1bd8-103">CSP Indirect provider sandbox capabilities for creating Indirect reseller accounts</span></span> 

<span data-ttu-id="e1bd8-104">**Funções adequadas**: Prestador indireto</span><span class="sxs-lookup"><span data-stu-id="e1bd8-104">**Appropriate roles**: Indirect provider</span></span>

<span data-ttu-id="e1bd8-105">Os Fornecedores Indiretos CSP podem criar uma conta de Areia De Revendedor Indireto CSP através da sua própria conta De sandbox Tier 2 no portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-105">CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account via through their own Tier 2 Sandbox account in Partner Center portal.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="e1bd8-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e1bd8-106">Prerequisites</span></span> 

<span data-ttu-id="e1bd8-107">Credenciais de caixa de areia Partner Center Indirete Provider (Nível 2).</span><span class="sxs-lookup"><span data-stu-id="e1bd8-107">Partner Center Indirect Provider (Tier 2) sandbox credentials.</span></span> <span data-ttu-id="e1bd8-108">O cenário sandbox suporta a autenticação com as credenciais autónomas da App e app+User.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-108">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span> 
 

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a><span data-ttu-id="e1bd8-109">Sandbox Indireto Provider – Criar Revendedor Indireto Sandbox utilizando a interface de utilizador do Partner Center</span><span class="sxs-lookup"><span data-stu-id="e1bd8-109">Sandbox Indirect Provider – Create Sandbox Indirect Reseller using the Partner Center user interface</span></span> 

 <span data-ttu-id="e1bd8-110">Esta é uma funcionalidade apenas para Sandbox que permite aos Fornecedores Indiretos da Sandbox a capacidade de criar uma conta de Revendedor Indireto Sandbox através do portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-110">This is a Sandbox-only feature that allows Sandbox Indirect Providers the ability to create a Sandbox Indirect Reseller account through the Partner Center portal.</span></span>

<span data-ttu-id="e1bd8-111">Os seguintes cenários são o que os fornecedores indiretos podem fazer para revendedores indiretos em Sandbox através da interface de utilizador do Partner Center:</span><span class="sxs-lookup"><span data-stu-id="e1bd8-111">The following scenarios are what Indirect providers can do for indirect resellers in Sandbox through the Partner Center user interface:</span></span> 

1. <span data-ttu-id="e1bd8-112">Os Fornecedores Indiretos CSP podem criar uma conta de Sandbox de Revendedor Indireto CSP através da sua própria conta De sandbox Tier 2 no portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-112">CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center portal.</span></span>
2. <span data-ttu-id="e1bd8-113">Os revendedores indiretos da CSP podem ver o cliente por Fornecedores Indiretos.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-113">CSP Indirect Resellers can view customer by Indirect Providers.</span></span> 

1. <span data-ttu-id="e1bd8-114">Os Revendedores Indiretos CSP podem gerir a conta do cliente utilizando permissões de administração delegadas.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-114">CSP Indirect Resellers can manage the customer account using delegated admin permissions.</span></span>

1. <span data-ttu-id="e1bd8-115">Os Fornecedores Indiretos da CSP podem convidar revendedores indiretos da CSP.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-115">CSP Indirect Providers can invite CSP Indirect Resellers.</span></span>
 
1. <span data-ttu-id="e1bd8-116">Os Fornecedores Indiretos CSP podem eliminar uma conta de Sandbox de Revendedor Indireto CSP através da sua própria conta De sandbox Tier 2 no portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-116">CSP Indirect Providers can delete a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center portal.</span></span>

    <span data-ttu-id="e1bd8-117">a.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-117">a.</span></span>  <span data-ttu-id="e1bd8-118">Quando o Sandbox Indirect Provider eliminar a relação com o Revendedor Indireto Sandbox, verifique se o Revendedor Indireto tem alguma outra relação com outros fornecedores.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-118">When Sandbox Indirect Provider deletes the relationship with Sandbox Indirect Reseller, check if the Indirect Reseller has any other relationship with other providers.</span></span> <span data-ttu-id="e1bd8-119">Em caso afirmativo, apenas a relação com esse fornecedor indireto específico será removida.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-119">If so, only the relationship with that specific Indirect provider will be removed.</span></span>

    <span data-ttu-id="e1bd8-120">c.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-120">c.</span></span> <span data-ttu-id="e1bd8-121">Se esta for a única relação para o Revendedor Indireto, então o Revendedor Indireto será eliminado.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-121">If that is the only relationship for the Indirect Reseller, then the Indirect Reseller will be deleted.</span></span>

1. <span data-ttu-id="e1bd8-122">Os Fornecedores Indiretos CSP podem eliminar um Revendedor Indireto CSP.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-122">CSP Indirect Providers can delete a CSP Indirect Reseller.</span></span>

    <span data-ttu-id="e1bd8-123">a.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-123">a.</span></span> <span data-ttu-id="e1bd8-124">Esta é uma funcionalidade apenas para Sandbox que permite aos Fornecedores Indiretos da Sandbox a capacidade de eliminar revendedores indiretos sandbox.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-124">This is a Sandbox-only feature that allows Sandbox Indirect Providers the ability to delete Sandbox Indirect Resellers.</span></span>
     
1. <span data-ttu-id="e1bd8-125">Pré-requisitos para a eliminação de um Revendedor Indireto Sandbox:</span><span class="sxs-lookup"><span data-stu-id="e1bd8-125">Pre-requisites for deleting a Sandbox Indirect Reseller:</span></span>

    1. <span data-ttu-id="e1bd8-126">Suspender as assinaturas para cada cliente da Sandbox Reseller Indirect.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-126">Suspend the subscriptions for each customer of Sandbox Indirect Reseller.</span></span>

    1. <span data-ttu-id="e1bd8-127">Elimine todos os clientes do Revendedor Indireto.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-127">Delete all customers of Indirect Reseller.</span></span>

1. <span data-ttu-id="e1bd8-128">Limite de cinco Revendedores Indiretos Sandbox permitidos por Sandbox Indirect Provider.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-128">Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> <span data-ttu-id="e1bd8-129">Uma vez eliminado o revendedor Sandbox Indirect, a quota será reposta.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-129">Once the Sandbox Indirect reseller is deleted, the quota will be reset.</span></span>

### <a name="pre-requisites"></a><span data-ttu-id="e1bd8-130">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e1bd8-130">Pre-requisites</span></span>

- <span data-ttu-id="e1bd8-131">Limite de cinco Revendedores Indiretos Sandbox permitidos por Sandbox Indirect Provider.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-131">Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> 

- <span data-ttu-id="e1bd8-132">O mesmo ID MPN pode ser usado para criar várias contas de Sandbox de Revendedor Indireto se o país MPN ID e o país de Sandbox de Revendedor Indireto forem os mesmos.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-132">Same MPN ID can be used to create multiple Indirect Reseller Sandbox accounts if MPN ID country and Indirect Reseller Sandbox country are same.</span></span> <span data-ttu-id="e1bd8-133">Se tiver um ID MPN de teste disponível, pode usá-lo, ou pode obter uma lista de IDs MPN através do nosso [canal Yammer]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ).</span><span class="sxs-lookup"><span data-stu-id="e1bd8-133">If you have a test MPN ID available, you can use it, or you can get a list of MPN IDs through our [Yammer channel]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ).</span></span> <span data-ttu-id="e1bd8-134">Se não tiver acesso a Yammer, Yammer lhe pedirá acesso.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-134">If you don’t have access to Yammer, Yammer will ask you to request access.</span></span>
 
- <span data-ttu-id="e1bd8-135">Apenas 75 clientes são permitidos por Sandbox Indireto Fornecedor</span><span class="sxs-lookup"><span data-stu-id="e1bd8-135">Only 75 customers are allowed per Sandbox Indirect Provider</span></span>

## <a name="create-csp-indirect-reseller-sandbox-account"></a><span data-ttu-id="e1bd8-136">Criar conta CSP Reseller Sandbox</span><span class="sxs-lookup"><span data-stu-id="e1bd8-136">Create CSP Indirect Reseller Sandbox account</span></span>

1. <span data-ttu-id="e1bd8-137">Inscreva-se no Partner Center através da sua conta De sandbox Tier 2.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-137">Sign into Partner Center via your Tier 2 Sandbox account.</span></span> 

2. <span data-ttu-id="e1bd8-138">Navegue para Revendedores Indiretos a partir do menu esquerdo.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-138">Navigate to Indirect Resellers from the left menu.</span></span> 

3. <span data-ttu-id="e1bd8-139">Selecione o botão **Add Reseller Sandbox.**</span><span class="sxs-lookup"><span data-stu-id="e1bd8-139">Select the **Add Reseller Sandbox** button.</span></span> 

4. <span data-ttu-id="e1bd8-140">Preencha o formulário de inscrição de conta.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-140">Fill the account enrollment form.</span></span> <span data-ttu-id="e1bd8-141">É autoexplicativo, mas lembre-se que está a criar uma conta Sandbox para um Revendedor Indireto.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-141">It's self-explanatory but remember you are creating a Sandbox account for an Indirect Reseller.</span></span> <span data-ttu-id="e1bd8-142">Esta conta não será submetida a verificação e será ativada assim que terminar a inscrição na conta.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-142">This account won't undergo vetting and will be activated as soon as you finish the account enrollment.</span></span>  

5. <span data-ttu-id="e1bd8-143">Assim que a conta for criada, obterá as credenciais de Administração Global para a conta de caixa de areia Do Revendedor Indireto no portal.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-143">Once the account is created, you will get the Global Admin credentials for the Indirect Reseller sandbox account on the portal.</span></span> <span data-ttu-id="e1bd8-144">Lembre-se de guardá-lo imediatamente, caso contrário, não poderá inscrever-se como uma Caixa de Areia De Revendedor Indireto.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-144">Remember to save it immediately,  otherwise, you won't be able to sign in as an Indirect Reseller Sandbox.</span></span> 

6. <span data-ttu-id="e1bd8-145">Inscreva-se e inscreva-se novamente no Partner Center utilizando as novas credenciais para Reseller Indirect Sandbox.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-145">Sign out and sign in again to Partner Center using the new credentials for Indirect Reseller Sandbox.</span></span> <span data-ttu-id="e1bd8-146">Explore as capacidades que pode fazer como Revendedor Indireto.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-146">Explore the capabilities you can do as an Indirect Reseller.</span></span> <span data-ttu-id="e1bd8-147">Algumas coisas são:</span><span class="sxs-lookup"><span data-stu-id="e1bd8-147">Some things are:</span></span>  

    - <span data-ttu-id="e1bd8-148">Gerir perfis</span><span class="sxs-lookup"><span data-stu-id="e1bd8-148">Manage profiles</span></span>  

    - <span data-ttu-id="e1bd8-149">Gerir utilizadores e funções</span><span class="sxs-lookup"><span data-stu-id="e1bd8-149">Manage users and roles</span></span> 

    - <span data-ttu-id="e1bd8-150">Gerir Fornecedores Indiretos</span><span class="sxs-lookup"><span data-stu-id="e1bd8-150">Manage Indirect Providers</span></span> 

    - <span data-ttu-id="e1bd8-151">Gerir clientes da CSP Sandbox</span><span class="sxs-lookup"><span data-stu-id="e1bd8-151">Manage CSP Sandbox customers</span></span> 

    - <span data-ttu-id="e1bd8-152">Gerir relações</span><span class="sxs-lookup"><span data-stu-id="e1bd8-152">Manage relationships</span></span>
    
     
## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a><span data-ttu-id="e1bd8-153">Sandbox Indireto Provider – Eliminar o Revendedor Indireto sandbox utilizando a interface de utilizador do Partner Center</span><span class="sxs-lookup"><span data-stu-id="e1bd8-153">Sandbox Indirect Provider – Delete Sandbox Indirect Reseller using the Partner Center user interface</span></span>

 <span data-ttu-id="e1bd8-154">Esta é uma funcionalidade única da Sandbox que permite aos Fornecedores Indiretos da Sandbox a capacidade de eliminar uma conta de Revendedor Indireto Sandbox existente através do portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-154">This is a Sandbox only feature that allows Sandbox Indirect Providers an ability to delete an existing Sandbox Indirect Reseller account via Partner Center portal.</span></span> 

### <a name="pre-requisites-to-delete-sandbox-indirect-reseller"></a><span data-ttu-id="e1bd8-155">Pré-requisitos para eliminar o revendedor indireto da caixa de areia:</span><span class="sxs-lookup"><span data-stu-id="e1bd8-155">Pre-requisites to delete sandbox Indirect reseller:</span></span>

<span data-ttu-id="e1bd8-156">Uma conta de Sandbox de Revendedor Indireto CSP existente associada à sua própria conta de Sandbox CSP Indirect Provider Tier-2.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-156">An existing CSP Indirect Reseller Sandbox account associated with your own CSP Indirect Provider Tier-2 Sandbox account.</span></span>  
 

## <a name="delete-csp-indirect-reseller-sandbox-account"></a><span data-ttu-id="e1bd8-157">Eliminar conta de revendedor indireto CSP</span><span class="sxs-lookup"><span data-stu-id="e1bd8-157">Delete CSP Indirect Reseller Sandbox account</span></span>

1. <span data-ttu-id="e1bd8-158">Inscreva-se no Partner Center utilizando a sua conta De sandbox Tier 2.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-158">Sign into Partner Center using your Tier 2 Sandbox account.</span></span> 

2. <span data-ttu-id="e1bd8-159">Navegue para Revendedores Indiretos a partir do menu esquerdo.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-159">Navigate to Indirect Resellers from the left menu.</span></span> 

3. <span data-ttu-id="e1bd8-160">Selecione o link **'Delete Reseller Sandbox'** ao lado da conta Descoventer a caixa de areia indireta que pretende eliminar.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-160">Select the **Delete Reseller Sandbox** link next to the Indirect Reseller Sandbox account you want to delete.</span></span> <span data-ttu-id="e1bd8-161">A conta Descovendor Indireto Sandbox será permanentemente eliminada e não pode ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="e1bd8-161">The Indirect Reseller Sandbox account will be permanently deleted and cannot be recovered.</span></span> 

## <a name="api-references"></a><span data-ttu-id="e1bd8-162">Referências de API</span><span class="sxs-lookup"><span data-stu-id="e1bd8-162">API references</span></span>

- <span data-ttu-id="e1bd8-163">Criar Revendedor Indireto</span><span class="sxs-lookup"><span data-stu-id="e1bd8-163">Create Indirect Reseller</span></span> 
- <span data-ttu-id="e1bd8-164">Eliminar Revendedor Indireto</span><span class="sxs-lookup"><span data-stu-id="e1bd8-164">Delete Indirect Reseller</span></span> 

 

 