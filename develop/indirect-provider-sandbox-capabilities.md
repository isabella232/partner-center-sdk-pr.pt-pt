---
title: Capacidades de fornecedor indireto CSP na Caixa de Areia
description: Os fornecedores indiretos podem criar revendedores indiretos na Caixa de Areia para efeitos de teste.
ms.date: 05/20/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vinayks-ms
ms.author: vinayks
ms.openlocfilehash: bd0f38103e6b6f93ab5da386042b00801b683ccd
ms.sourcegitcommit: 1aeaa12705a5945b8aab6bca254fedebd9c8bc4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/21/2021
ms.locfileid: "110244608"
---
# <a name="csp-indirect-provider-sandbox-capabilities-for-creating-indirect-reseller-accounts"></a><span data-ttu-id="f3d24-103">Capacidades de caixa de areia do fornecedor CSP indireto para criar contas de revendedores indiretos</span><span class="sxs-lookup"><span data-stu-id="f3d24-103">CSP Indirect provider sandbox capabilities for creating Indirect reseller accounts</span></span> 

<span data-ttu-id="f3d24-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="f3d24-104">**Applies to**</span></span>

- <span data-ttu-id="f3d24-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="f3d24-105">Partner Center</span></span>

<span data-ttu-id="f3d24-106">**Funções adequadas**</span><span class="sxs-lookup"><span data-stu-id="f3d24-106">**Appropriate roles**</span></span>

- <span data-ttu-id="f3d24-107">Fornecedor indireto</span><span class="sxs-lookup"><span data-stu-id="f3d24-107">Indirect provider</span></span>

<span data-ttu-id="f3d24-108">Os Fornecedores Indiretos CSP podem criar uma conta de Areia De Revendedor Indireto CSP através da sua própria conta De sandbox Tier 2 no portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f3d24-108">CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account via through their own Tier 2 Sandbox account in Partner Center portal.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="f3d24-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f3d24-109">Prerequisites</span></span> 

<span data-ttu-id="f3d24-110">Credenciais de caixa de areia Partner Center Indirete Provider (Nível 2).</span><span class="sxs-lookup"><span data-stu-id="f3d24-110">Partner Center Indirect Provider (Tier 2) sandbox credentials.</span></span> <span data-ttu-id="f3d24-111">O cenário sandbox suporta a autenticação com as credenciais autónomas da App e app+User.</span><span class="sxs-lookup"><span data-stu-id="f3d24-111">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span> 
 

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a><span data-ttu-id="f3d24-112">Sandbox Indireto Provider – Criar Revendedor Indireto Sandbox utilizando a interface de utilizador do Partner Center</span><span class="sxs-lookup"><span data-stu-id="f3d24-112">Sandbox Indirect Provider – Create Sandbox Indirect Reseller using the Partner Center user interface</span></span> 

 <span data-ttu-id="f3d24-113">Esta é uma funcionalidade única da Sandbox que permite aos Fornecedores Indiretos da Sandbox a capacidade de criar a conta Sandbox Indirect Reseller através do portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f3d24-113">This is a Sandbox- only feature that allows Sandbox Indirect Providers the ability to create Sandbox Indirect Reseller account through the Partner Center portal.</span></span>

<span data-ttu-id="f3d24-114">Os seguintes cenários são o que os fornecedores indiretos podem fazer para revendedores indiretos em Sandbox através da interface de utilizador do Partner Center:</span><span class="sxs-lookup"><span data-stu-id="f3d24-114">The following scenarios are what Indirect providers can do for indirect resellers in Sandbox through the Partner Center user interface:</span></span> 

1. <span data-ttu-id="f3d24-115">Os Fornecedores Indiretos CSP podem criar uma conta de Sandbox de Revendedor Indireto CSP através da sua própria conta De sandbox Tier 2 no portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f3d24-115">CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center portal.</span></span>
2. <span data-ttu-id="f3d24-116">Os revendedores indiretos da CSP podem ver o cliente por Fornecedores Indiretos.</span><span class="sxs-lookup"><span data-stu-id="f3d24-116">CSP Indirect Resellers can view customer by Indirect Providers.</span></span> 

1. <span data-ttu-id="f3d24-117">Os Revendedores Indiretos CSP podem gerir a conta do cliente utilizando permissões de administração delegadas.</span><span class="sxs-lookup"><span data-stu-id="f3d24-117">CSP Indirect Resellers  can manage the customer account using delegated admin permissions.</span></span>

1. <span data-ttu-id="f3d24-118">Os Fornecedores Indiretos da CSP podem convidar revendedores indiretos da CSP.</span><span class="sxs-lookup"><span data-stu-id="f3d24-118">CSP Indirect Providers can invite CSP Indirect Resellers.</span></span>
 
1. <span data-ttu-id="f3d24-119">Os Fornecedores Indiretos CSP podem eliminar uma conta de Sandbox de Revendedor Indireto CSP através da sua própria conta De sandbox Tier 2 no portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f3d24-119">CSP Indirect Providers can delete a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center portal.</span></span>

    <span data-ttu-id="f3d24-120">a.</span><span class="sxs-lookup"><span data-stu-id="f3d24-120">a.</span></span>  <span data-ttu-id="f3d24-121">Quando o Sandbox Indirect Provider elimina a relação com o Revendedor Indireto Sandbox.</span><span class="sxs-lookup"><span data-stu-id="f3d24-121">When Sandbox Indirect Provider deletes relationship with Sandbox Indirect Reseller.</span></span>

    <span data-ttu-id="f3d24-122">b.</span><span class="sxs-lookup"><span data-stu-id="f3d24-122">b.</span></span>  <span data-ttu-id="f3d24-123">Verifique se o Revendedor Indireto tem alguma outra relação com outros fornecedores.</span><span class="sxs-lookup"><span data-stu-id="f3d24-123">Check if the Indirect Reseller has any other relationship with other providers.</span></span> <span data-ttu-id="f3d24-124">Em caso afirmativo, apenas a relação com esse fornecedor indireto específico será removida.</span><span class="sxs-lookup"><span data-stu-id="f3d24-124">If so, only the relationship with that specific Indirect provider will be removed.</span></span>

    <span data-ttu-id="f3d24-125">c.</span><span class="sxs-lookup"><span data-stu-id="f3d24-125">c.</span></span> <span data-ttu-id="f3d24-126">Se essa é a única relação para o IR, então o IR será apagado.</span><span class="sxs-lookup"><span data-stu-id="f3d24-126">If that is the only relationship for the IR, then the IR will be deleted.</span></span>

1. <span data-ttu-id="f3d24-127">O CSP Indirect Provider pode eliminar um Revendedor Indireto CSP.</span><span class="sxs-lookup"><span data-stu-id="f3d24-127">CSP Indirect Provider can delete a CSP Indirect Reseller.</span></span>

    <span data-ttu-id="f3d24-128">a.</span><span class="sxs-lookup"><span data-stu-id="f3d24-128">a.</span></span> <span data-ttu-id="f3d24-129">Esta é uma funcionalidade apenas para Sandbox que permite aos Fornecedores Indiretos da Sandbox a capacidade de eliminar revendedores indiretos sandbox.</span><span class="sxs-lookup"><span data-stu-id="f3d24-129">This is a Sandbox-only feature that allows Sandbox Indirect Providers the ability to delete Sandbox Indirect Resellers.</span></span>
     
1. <span data-ttu-id="f3d24-130">Pré-requisitos para a eliminação de um Revendedor Indireto Sandbox:</span><span class="sxs-lookup"><span data-stu-id="f3d24-130">Pre-requisites for deleting a Sandbox Indirect Reseller:</span></span>

    1. <span data-ttu-id="f3d24-131">Suspender as assinaturas para cada cliente da Sandbox Reseller Indirect.</span><span class="sxs-lookup"><span data-stu-id="f3d24-131">Suspend the subscriptions for each customer of Sandbox Indirect Reseller.</span></span>

    1. <span data-ttu-id="f3d24-132">Elimine todos os clientes do Revendedor Indireto.</span><span class="sxs-lookup"><span data-stu-id="f3d24-132">Delete all customers of Indirect Reseller.</span></span>

1. <span data-ttu-id="f3d24-133">Limite de 5 Revendedores Indiretos sandbox permitidos por Sandbox Indirect Provider.</span><span class="sxs-lookup"><span data-stu-id="f3d24-133">Limit of 5 Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> <span data-ttu-id="f3d24-134">Uma vez eliminado o revendedor Sandbox Indirect, a quota será reposta.</span><span class="sxs-lookup"><span data-stu-id="f3d24-134">Once the Sandbox Indirect reseller is deleted, the quota will be reset.</span></span>

### <a name="pre-requisites"></a><span data-ttu-id="f3d24-135">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f3d24-135">Pre-requisites</span></span>

- <span data-ttu-id="f3d24-136">Limite de 5 Revendedores Indiretos sandbox permitidos por Sandbox Indirect Provider.</span><span class="sxs-lookup"><span data-stu-id="f3d24-136">Limit of 5 Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> 

- <span data-ttu-id="f3d24-137">O mesmo ID MPN pode ser usado para criar várias contas de Sandbox de Revendedor Indireto se o país MPN ID e o país de Sandbox de Revendedor Indireto forem os mesmos.</span><span class="sxs-lookup"><span data-stu-id="f3d24-137">Same MPN ID can be used to create multiple Indirect Reseller Sandbox accounts if MPN ID country and Indirect Reseller Sandbox country are same.</span></span> <span data-ttu-id="f3d24-138">Se tiver um ID MPN de teste disponível, pode usá-lo, ou pode obter uma lista de IDs MPN através do nosso [canal Yammer.]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 )</span><span class="sxs-lookup"><span data-stu-id="f3d24-138">If you have a test MPN ID available, you can use it, or you can get a list of MPN IDs through our [Yammer channel]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ).</span></span> <span data-ttu-id="f3d24-139">Se não tiver acesso a Yammer, o Yammer pedir-lhe-á para solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="f3d24-139">If you don’t have access to Yammer, Yammer will ask you to request access.</span></span>
 
- <span data-ttu-id="f3d24-140">Apenas 75 clientes são permitidos por Sandbox Indireto Fornecedor</span><span class="sxs-lookup"><span data-stu-id="f3d24-140">Only 75 customers are allowed per Sandbox Indirect Provider</span></span>

## <a name="create-csp-indirect-reseller-sandbox-account"></a><span data-ttu-id="f3d24-141">Criar conta CSP Reseller Sandbox</span><span class="sxs-lookup"><span data-stu-id="f3d24-141">Create CSP Indirect Reseller Sandbox account</span></span>

1. <span data-ttu-id="f3d24-142">Inscreva-se no Partner Center através da sua conta De sandbox Tier 2.</span><span class="sxs-lookup"><span data-stu-id="f3d24-142">Sign into Partner Center via your Tier 2 Sandbox account.</span></span> 

2. <span data-ttu-id="f3d24-143">Navegue para Revendedores Indiretos a partir do menu esquerdo.</span><span class="sxs-lookup"><span data-stu-id="f3d24-143">Navigate to Indirect Resellers from the left menu.</span></span> 

3. <span data-ttu-id="f3d24-144">Clique no botão "Adicionar Reseller Sandbox".</span><span class="sxs-lookup"><span data-stu-id="f3d24-144">Click on “Add Reseller Sandbox” button.</span></span> 

4. <span data-ttu-id="f3d24-145">Preencha o formulário de inscrição de conta.</span><span class="sxs-lookup"><span data-stu-id="f3d24-145">Fill the account enrollment form.</span></span> <span data-ttu-id="f3d24-146">É autoexplicativo, mas lembre-se que está a criar uma conta Sandbox para um Revendedor Indireto.</span><span class="sxs-lookup"><span data-stu-id="f3d24-146">It's self-explanatory but remember you are creating a Sandbox account for an Indirect Reseller.</span></span> <span data-ttu-id="f3d24-147">Esta conta não será submetida a verificação e será ativada assim que terminar a inscrição na conta.</span><span class="sxs-lookup"><span data-stu-id="f3d24-147">This account won't undergo vetting and will be activated as soon as you finish the account enrollment.</span></span>  

5. <span data-ttu-id="f3d24-148">Assim que a conta for criada, obterá as credenciais de Administração Global para a conta de caixa de areia Do Revendedor Indireto no portal.</span><span class="sxs-lookup"><span data-stu-id="f3d24-148">Once the account is created, you will get the Global Admin credentials for the Indirect Reseller sandbox account on the portal.</span></span> <span data-ttu-id="f3d24-149">Lembre-se de guardá-lo imediatamente, caso contrário, não poderá inscrever-se como uma Caixa de Areia De Revendedor Indireto.</span><span class="sxs-lookup"><span data-stu-id="f3d24-149">Remember to save it immediately,  otherwise, you won't be able to sign in as an Indirect Reseller Sandbox.</span></span> 

6. <span data-ttu-id="f3d24-150">Inscreva-se e inscreva-se novamente no Partner Center utilizando as novas credenciais para Reseller Indirect Sandbox.</span><span class="sxs-lookup"><span data-stu-id="f3d24-150">Sign out and sign in again to Partner Center using the new credentials for Indirect Reseller Sandbox.</span></span> <span data-ttu-id="f3d24-151">Explore as capacidades que pode fazer como Revendedor Indireto.</span><span class="sxs-lookup"><span data-stu-id="f3d24-151">Explore the capabilities you can do as an Indirect Reseller.</span></span> <span data-ttu-id="f3d24-152">Algumas coisas são:</span><span class="sxs-lookup"><span data-stu-id="f3d24-152">Some things are :</span></span>  

    - <span data-ttu-id="f3d24-153">Gerir perfis</span><span class="sxs-lookup"><span data-stu-id="f3d24-153">Manage profiles</span></span>  

    - <span data-ttu-id="f3d24-154">Gerir utilizadores e funções</span><span class="sxs-lookup"><span data-stu-id="f3d24-154">Manage users and roles</span></span> 

    - <span data-ttu-id="f3d24-155">Gerir Fornecedores Indiretos</span><span class="sxs-lookup"><span data-stu-id="f3d24-155">Manage Indirect Providers</span></span> 

    - <span data-ttu-id="f3d24-156">Gerir clientes da CSP Sandbox</span><span class="sxs-lookup"><span data-stu-id="f3d24-156">Manage CSP Sandbox customers</span></span> 

    - <span data-ttu-id="f3d24-157">Gerir relações</span><span class="sxs-lookup"><span data-stu-id="f3d24-157">Manage relationships</span></span>
    
     
## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a><span data-ttu-id="f3d24-158">Sandbox Indireto Provider – Eliminar o Revendedor Indireto sandbox utilizando a interface de utilizador do Partner Center</span><span class="sxs-lookup"><span data-stu-id="f3d24-158">Sandbox Indirect Provider – Delete Sandbox Indirect Reseller using the Partner Center user interface</span></span>

 <span data-ttu-id="f3d24-159">Esta é uma funcionalidade única da Sandbox que permite aos Fornecedores Indiretos da Sandbox a capacidade de eliminar uma conta de Revendedor Indireto Sandbox existente através do portal Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f3d24-159">This is a Sandbox only feature that allows Sandbox Indirect Providers an ability to delete an existing Sandbox Indirect Reseller account via Partner Center portal.</span></span> 

### <a name="pre-requisites-to-delete-sandbox-indirect-reseller"></a><span data-ttu-id="f3d24-160">Pré-requisitos para eliminar o revendedor indireto da caixa de areia:</span><span class="sxs-lookup"><span data-stu-id="f3d24-160">Pre-requisites to delete sandbox Indirect reseller:</span></span>

<span data-ttu-id="f3d24-161">Uma conta de Sandbox de Revendedor Indireto CSP existente associada à sua própria conta de Sandbox CSP Indirect Provider Tier-2.</span><span class="sxs-lookup"><span data-stu-id="f3d24-161">An existing CSP Indirect Reseller Sandbox account associated with your own CSP Indirect Provider Tier-2 Sandbox account.</span></span>  
 

## <a name="delete-csp-indirect-reseller-sandbox-account"></a><span data-ttu-id="f3d24-162">Eliminar conta de revendedor indireto CSP</span><span class="sxs-lookup"><span data-stu-id="f3d24-162">Delete CSP Indirect Reseller Sandbox account</span></span>

1. <span data-ttu-id="f3d24-163">Inscreva-se no Partner Center utilizando a sua conta De sandbox Tier 2.</span><span class="sxs-lookup"><span data-stu-id="f3d24-163">Sign into Partner Center using your Tier 2 Sandbox account.</span></span> 

2. <span data-ttu-id="f3d24-164">Navegue para Revendedores Indiretos a partir do menu esquerdo.</span><span class="sxs-lookup"><span data-stu-id="f3d24-164">Navigate to Indirect Resellers from the left menu.</span></span> 

3. <span data-ttu-id="f3d24-165">Clique em Eliminar O Link **de Caixa de Areia de Revendedor** ao lado da conta de Vendar Indireto que pretende eliminar.</span><span class="sxs-lookup"><span data-stu-id="f3d24-165">Click on **Delete Reseller Sandbox** link next to the Indirect Reseller Sandbox account you want to delete.</span></span> <span data-ttu-id="f3d24-166">A conta Descovendor Indireto Sandbox será permanentemente eliminada e não pode ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="f3d24-166">The Indirect Reseller Sandbox account will be permanently deleted and cannot be recovered.</span></span> 

## <a name="api-references"></a><span data-ttu-id="f3d24-167">Referências de API</span><span class="sxs-lookup"><span data-stu-id="f3d24-167">API references</span></span>

- <span data-ttu-id="f3d24-168">Criar Revendedor Indireto</span><span class="sxs-lookup"><span data-stu-id="f3d24-168">Create Indirect Reseller</span></span> 
- <span data-ttu-id="f3d24-169">Eliminar Revendedor Indireto</span><span class="sxs-lookup"><span data-stu-id="f3d24-169">Delete Indirect Reseller</span></span> 

 

 