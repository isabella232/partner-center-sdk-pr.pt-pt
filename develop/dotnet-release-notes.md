---
title: Parceiro Center .NET SDK notas de lançamento
description: Notas de lançamento para a versão mais recente do Partner Center .NET SDK.
ms.date: 07/07/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c1532d48c00550f5eb437ed0164d6a1f7bb340dd
ms.sourcegitcommit: 53c94db33b09c30e762b842c4275b2b531dba932
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/09/2021
ms.locfileid: "113522639"
---
# <a name="net-sdk-release-notes"></a><span data-ttu-id="dda88-103">.NET SDK notas de lançamento</span><span class="sxs-lookup"><span data-stu-id="dda88-103">.NET SDK release notes</span></span>

<span data-ttu-id="dda88-104">As seguintes notas de lançamento estão disponíveis para novas versões do [Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter).</span><span class="sxs-lookup"><span data-stu-id="dda88-104">The following release notes are available for new versions of [Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter).</span></span> <span data-ttu-id="dda88-105">Pode encontrar [amostras .NET SDK](https://github.com/Microsoft/Partner-Center-DotNet-Samples) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="dda88-105">You can find [.NET SDK samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) on GitHub.</span></span> <span data-ttu-id="dda88-106">Pode encontrar a [referência API do Partner Center .NET](/dotnet/api/?view=partnercenter-dotnet-latest&preserve-view=true) no Browser .NET API.</span><span class="sxs-lookup"><span data-stu-id="dda88-106">You can find the [Partner Center .NET API reference](/dotnet/api/?view=partnercenter-dotnet-latest&preserve-view=true) in the .NET API Browser.</span></span>

## <a name="version-201"></a><span data-ttu-id="dda88-107">Versão 2.0.1</span><span class="sxs-lookup"><span data-stu-id="dda88-107">Version 2.0.1</span></span>

<span data-ttu-id="dda88-108">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/2.0.1) v2.0.1 é agora disponibilidade geral.</span><span class="sxs-lookup"><span data-stu-id="dda88-108">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/2.0.1) v2.0.1 is now general availability.</span></span> <span data-ttu-id="dda88-109">Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="dda88-109">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="dda88-110">As seguintes alterações estão incluídas nesta versão:</span><span class="sxs-lookup"><span data-stu-id="dda88-110">The following changes are included in this version:</span></span>

> [!NOTE]
> <span data-ttu-id="dda88-111">Algumas das alterações introduzidas no âmbito da New Commerce Experiences ("NCE") que estão atualmente disponíveis com base apenas no convite aos parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365.</span><span class="sxs-lookup"><span data-stu-id="dda88-111">Some of changes introduced as part of New Commerce Experiences (“NCE”) which are currently available based on invitation only to partners who are part of the M365/D365 new commerce experience technical preview.</span></span> <span data-ttu-id="dda88-112">Os parceiros que não fazem parte da pré-visualização privada de novo comércio não devem notar impactos e devem ser retro compatíveis.</span><span class="sxs-lookup"><span data-stu-id="dda88-112">Partners who are not part of New commerce private preview should not notice impacts and should be backward compatible.</span></span>

### <a name="common"></a><span data-ttu-id="dda88-113">Common</span><span class="sxs-lookup"><span data-stu-id="dda88-113">Common</span></span>
* <span data-ttu-id="dda88-114">Alteração na referência à biblioteca de autenticação – A referência é alterada de Azure Ative Directory Biblioteca de Autenticação[(ADAL)](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)para a Biblioteca de Autenticação do Microsoft[(MSAL)](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet)</span><span class="sxs-lookup"><span data-stu-id="dda88-114">Change on the reference to authentication library – The reference is changed from Azure Active Directory Authentication Library ([ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)) to Microsoft Authentication Library ([MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet))</span></span>

  <span data-ttu-id="dda88-115">As seguintes alterações devem ser feitas para garantir que a MSAL funciona corretamente na sua aplicação ou na amostra .NET:</span><span class="sxs-lookup"><span data-stu-id="dda88-115">Following changes should be made to ensure MSAL runs correctly on your application or .NET sample:</span></span>

  * <span data-ttu-id="dda88-116">Adicione `https://login.microsoftonline.com/common/oauth2/nativeclient` como RedirectUrl para aplicações móveis e desktop</span><span class="sxs-lookup"><span data-stu-id="dda88-116">Add `https://login.microsoftonline.com/common/oauth2/nativeclient` as RedirectUrl for Mobile and desktop applications</span></span>
  * <span data-ttu-id="dda88-117">Adicione **domínio** na secção de instrução do utilizador no seu ficheiro de configuração de aplicação.</span><span class="sxs-lookup"><span data-stu-id="dda88-117">Add **Domain** into UserAuthentication section in your application configuration file.</span></span> 

    <span data-ttu-id="dda88-118">Domínio é o domínio Azure Ative Directory ou iD do inquilino onde a aplicação AD Azure foi criada</span><span class="sxs-lookup"><span data-stu-id="dda88-118">Domain is the Azure Active Directory domain or tenant ID where the Azure AD application was created</span></span>

* <span data-ttu-id="dda88-119">[Códigos de erro](error-codes.md) - Novo código de erro adicionado</span><span class="sxs-lookup"><span data-stu-id="dda88-119">[Error codes](error-codes.md) – New error code added</span></span> 
  * <span data-ttu-id="dda88-120">408: Pedido de tempo limite</span><span class="sxs-lookup"><span data-stu-id="dda88-120">408: Request timeout</span></span>
  * <span data-ttu-id="dda88-121">504: Tempo limite de gateway</span><span class="sxs-lookup"><span data-stu-id="dda88-121">504: Gateway timeout</span></span> 

### <a name="manage-billing"></a><span data-ttu-id="dda88-122">Gerir faturação</span><span class="sxs-lookup"><span data-stu-id="dda88-122">Manage billing</span></span>

* <span data-ttu-id="dda88-123">[Artigos de linha de fatura](get-invoiceline-items.md) - novos atributos adicionados às seguintes APIs:</span><span class="sxs-lookup"><span data-stu-id="dda88-123">[Invoice line-items](get-invoiceline-items.md) - new attributes added to following APIs:</span></span>
  * `GET /invoices/{invoice-id}/lineitems?provider={provider}&invoicelineitemtype=billinglineitems`
  * `GET /invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems`

  <span data-ttu-id="dda88-124">Novos atributos:</span><span class="sxs-lookup"><span data-stu-id="dda88-124">New attributes:</span></span> 
  * <span data-ttu-id="dda88-125">produtosQualifiers</span><span class="sxs-lookup"><span data-stu-id="dda88-125">productQualifiers</span></span>
  * <span data-ttu-id="dda88-126">subscriçãoStartDate</span><span class="sxs-lookup"><span data-stu-id="dda88-126">subscriptionStartDate</span></span>
  * <span data-ttu-id="dda88-127">subscriçãoEndDate</span><span class="sxs-lookup"><span data-stu-id="dda88-127">subscriptionEndDate</span></span>
  * <span data-ttu-id="dda88-128">referenceId</span><span class="sxs-lookup"><span data-stu-id="dda88-128">referenceId</span></span>
  * <span data-ttu-id="dda88-129">creditReasonCode (apenas aplicável à NCE)</span><span class="sxs-lookup"><span data-stu-id="dda88-129">creditReasonCode  (Only applicable to NCE)</span></span>
  * <span data-ttu-id="dda88-130">promotionId</span><span class="sxs-lookup"><span data-stu-id="dda88-130">promotionId</span></span> 


* <span data-ttu-id="dda88-131">[Itens de linha de utilização avaliados diariamente](get-invoice-billed-consumption-lineitems.md) – novos atributos adicionados à seguinte API:</span><span class="sxs-lookup"><span data-stu-id="dda88-131">[Daily rated usage Line-items](get-invoice-billed-consumption-lineitems.md) – new attributes added to following API:</span></span> 
  * `GET /invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems`
  
  <span data-ttu-id="dda88-132">Novos atributos:</span><span class="sxs-lookup"><span data-stu-id="dda88-132">New attributes:</span></span> 
  * <span data-ttu-id="dda88-133">hasPartnerEarnedCredit (Apenas aplicável à NCE)</span><span class="sxs-lookup"><span data-stu-id="dda88-133">hasPartnerEarnedCredit (Only applicable to NCE)</span></span>
  * <span data-ttu-id="dda88-134">creditType (apenas aplicável ao NCE)</span><span class="sxs-lookup"><span data-stu-id="dda88-134">creditType (Only applicable to NCE)</span></span>
  * <span data-ttu-id="dda88-135">taxaOfCredit (Apenas aplicável ao NCE)</span><span class="sxs-lookup"><span data-stu-id="dda88-135">rateOfCredit (Only applicable to NCE)</span></span>


### <a name="manage-orders"></a><span data-ttu-id="dda88-136">Gerir encomendas</span><span class="sxs-lookup"><span data-stu-id="dda88-136">Manage orders</span></span>

* <span data-ttu-id="dda88-137">[Recursos de Subscrição](subscription-resources.md) – Novo imóvel adicionado.</span><span class="sxs-lookup"><span data-stu-id="dda88-137">[Subscription Resources](subscription-resources.md) – New property added.</span></span> 
  * <span data-ttu-id="dda88-138">CancelamentoAllowedUntilDate - (Apenas aplicável à NCE)</span><span class="sxs-lookup"><span data-stu-id="dda88-138">CancellationAllowedUntilDate  - (Only applicable to NCE)</span></span>

* <span data-ttu-id="dda88-139">Recursos de Transição (Apenas aplicáveis à NCE) – Novo imóvel adicionado</span><span class="sxs-lookup"><span data-stu-id="dda88-139">Transition Resources (Only applicable to NCE) – New property added</span></span> 
  * <span data-ttu-id="dda88-140">FromSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="dda88-140">FromSubscriptionId</span></span>

### <a name="manage-customer-accounts"></a><span data-ttu-id="dda88-141">Gerir contas de clientes</span><span class="sxs-lookup"><span data-stu-id="dda88-141">Manage customer accounts</span></span>

* <span data-ttu-id="dda88-142">[Validar um endereço](validate-an-address.md) – A resposta é alterada de um Boolean para um novo modelo para API:</span><span class="sxs-lookup"><span data-stu-id="dda88-142">[Validate an address](validate-an-address.md) – Response is changed from a Boolean to a new model for API:</span></span>
  * `POST /validations/address`
  
  <span data-ttu-id="dda88-143">Novo modelo de resposta:</span><span class="sxs-lookup"><span data-stu-id="dda88-143">New response model:</span></span> 
  * <span data-ttu-id="dda88-144">EndereçoValidationResponse</span><span class="sxs-lookup"><span data-stu-id="dda88-144">AddressValidationResponse</span></span>

* <span data-ttu-id="dda88-145">A API sincronizada de qualificação do cliente é depreciada.</span><span class="sxs-lookup"><span data-stu-id="dda88-145">Customer’s qualification synchronous API is deprecated.</span></span>  


## <a name="version-1170"></a><span data-ttu-id="dda88-146">Versão 1.17.0</span><span class="sxs-lookup"><span data-stu-id="dda88-146">Version 1.17.0</span></span>

<span data-ttu-id="dda88-147">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.17.0) v1.17.0 é agora disponibilidade geral.</span><span class="sxs-lookup"><span data-stu-id="dda88-147">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.17.0) v1.17.0 is now general availability.</span></span> <span data-ttu-id="dda88-148">Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="dda88-148">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="dda88-149">As seguintes alterações estão incluídas nesta versão:</span><span class="sxs-lookup"><span data-stu-id="dda88-149">The following changes are included in this version:</span></span>

* <span data-ttu-id="dda88-150">Auditoria Atualizada - Adicionou novos tipos de operação para saber quando o cliente aprovou e encerrou o DAP</span><span class="sxs-lookup"><span data-stu-id="dda88-150">Audit Updated - Added new operation types for knowing when the customer approved and terminated DAP</span></span>
  * [<span data-ttu-id="dda88-151">DapAdminRelationshipApproved</span><span class="sxs-lookup"><span data-stu-id="dda88-151">DapAdminRelationshipApproved</span></span>](auditing-resources.md)
  * [<span data-ttu-id="dda88-152">DapAdminRelationshipTerminated</span><span class="sxs-lookup"><span data-stu-id="dda88-152">DapAdminRelationshipTerminated</span></span>](auditing-resources.md)

* <span data-ttu-id="dda88-153">Auditoria Atualizada – Adicionou novos tipos de recursos e operação para apoiar o cenário de função de diretório de clientes</span><span class="sxs-lookup"><span data-stu-id="dda88-153">Audit Updated – Added new resource and operation types for supporting the customer directory role scenario</span></span>
  * <span data-ttu-id="dda88-154">Tipo de recurso "[CustomerDirectoryRole](auditing-resources.md)"</span><span class="sxs-lookup"><span data-stu-id="dda88-154">Resource type "[CustomerDirectoryRole](auditing-resources.md)"</span></span>
  * <span data-ttu-id="dda88-155">Tipos de operação "[AddUserMember](auditing-resources.md)" e "[RemoveUserMember](auditing-resources.md)"</span><span class="sxs-lookup"><span data-stu-id="dda88-155">Operation types "[AddUserMember](auditing-resources.md)" and "[RemoveUserMember](auditing-resources.md)"</span></span>

* <span data-ttu-id="dda88-156">Atualizações SDK para conta de clientes - Suporte para seguir API's</span><span class="sxs-lookup"><span data-stu-id="dda88-156">SDK Updates to Customers Account - Support for following API's</span></span>
  * <span data-ttu-id="dda88-157">GET /clientes/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus</span><span class="sxs-lookup"><span data-stu-id="dda88-157">GET /customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus</span></span>
  * <span data-ttu-id="dda88-158">GET /clientes/{cliente-inquilino-id}/qualificações</span><span class="sxs-lookup"><span data-stu-id="dda88-158">GET /customers/{customer-tenant-id}/qualifications</span></span> 
  * <span data-ttu-id="dda88-159">POST /clientes/{customer_id}/qualificações?código={validação Código}</span><span class="sxs-lookup"><span data-stu-id="dda88-159">POST /customers/{customer_id}/qualifications?code={validationCode}</span></span>

* <span data-ttu-id="dda88-160">**Na sequência de alterações introduzidas no âmbito do Novo Comércio, que atualmente estão disponíveis com base apenas no convite aos parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365.**</span><span class="sxs-lookup"><span data-stu-id="dda88-160">**Following changes introduced as part of New Commerce which are currently available based on invitation only to partners who are part of the M365/D365 new commerce experience technical preview.**</span></span> <span data-ttu-id="dda88-161">Os parceiros que não fazem parte da pré-visualização privada de novo comércio não devem notar impactos e devem ser retro compatíveis.</span><span class="sxs-lookup"><span data-stu-id="dda88-161">Partners who are not part of New commerce private preview should not notice impacts and should be backward compatible.</span></span>
  * <span data-ttu-id="dda88-162">Alterações no catálogo:</span><span class="sxs-lookup"><span data-stu-id="dda88-162">Catalog Changes:</span></span>
    * <span data-ttu-id="dda88-163">GET /products/{product-id}/skus/{sku-id}</span><span class="sxs-lookup"><span data-stu-id="dda88-163">GET /products/{product-id}/skus/{sku-id}</span></span>
  * <span data-ttu-id="dda88-164">Compra e Gestão:</span><span class="sxs-lookup"><span data-stu-id="dda88-164">Purchase and Manage:</span></span>
    * <span data-ttu-id="dda88-165">GET /clientes/{clienteId}/subscrições</span><span class="sxs-lookup"><span data-stu-id="dda88-165">GET /customers/{customerId}/subscriptions</span></span>
    * <span data-ttu-id="dda88-166">GET /clientes/{customerId}/subscrições/{subscriçãoD}</span><span class="sxs-lookup"><span data-stu-id="dda88-166">GET /customers/{customerId}/subscriptions/{subscriptionId}</span></span>
    * <span data-ttu-id="dda88-167">PATCH /clientes/{customerId}/subscrições/{subscriçãoD}</span><span class="sxs-lookup"><span data-stu-id="dda88-167">PATCH /customers/{customerId}/subscriptions/{subscriptionId}</span></span>
    * <span data-ttu-id="dda88-168">GET /clientes/{customerId}/subscrições/{subscriçãoD}/transitioneligibilities</span><span class="sxs-lookup"><span data-stu-id="dda88-168">GET /customers/{customerId}/subscriptions/{subscriptionId}/transitioneligibilities</span></span>
    * <span data-ttu-id="dda88-169">GET /clientes/{customerId}/subscrições/{subscriçãoId}/transições</span><span class="sxs-lookup"><span data-stu-id="dda88-169">GET /customers/{customerId}/subscriptions/{subscriptionId}/transitions</span></span>
    * <span data-ttu-id="dda88-170">POST /clientes/{customerId}/subscrições/{subscriçãoD}/transições</span><span class="sxs-lookup"><span data-stu-id="dda88-170">POST /customers/{customerId}/subscriptions/{subscriptionId}/transitions</span></span>


## <a name="version-1163"></a><span data-ttu-id="dda88-171">Versão 1.16.3</span><span class="sxs-lookup"><span data-stu-id="dda88-171">Version 1.16.3</span></span>

<span data-ttu-id="dda88-172">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.3) v1.16.3 é agora disponibilidade geral.</span><span class="sxs-lookup"><span data-stu-id="dda88-172">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.3) v1.16.3 is now general availability.</span></span> <span data-ttu-id="dda88-173">Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="dda88-173">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="dda88-174">As seguintes alterações estão incluídas nesta versão:</span><span class="sxs-lookup"><span data-stu-id="dda88-174">The following changes are included in this version:</span></span>

* <span data-ttu-id="dda88-175">SelfServePolicies - nova funcionalidade adicionada</span><span class="sxs-lookup"><span data-stu-id="dda88-175">SelfServePolicies - new functionality added</span></span>
  * [<span data-ttu-id="dda88-176">GetSelfServePolicies</span><span class="sxs-lookup"><span data-stu-id="dda88-176">GetSelfServePolicies</span></span>](get-a-self-serve-policy-by-id.md)
  * [<span data-ttu-id="dda88-177">GetListOfSelfServicePolicies</span><span class="sxs-lookup"><span data-stu-id="dda88-177">GetListOfSelfServicePolicies</span></span>](get-a-list-of-self-serve-policies.md)
  * [<span data-ttu-id="dda88-178">CreateSelfServePolicies</span><span class="sxs-lookup"><span data-stu-id="dda88-178">CreateSelfServePolicies</span></span>](create-a-self-serve-policy.md)
  * [<span data-ttu-id="dda88-179">UpdateSelfServePolicies</span><span class="sxs-lookup"><span data-stu-id="dda88-179">UpdateSelfServePolicies</span></span>](update-a-self-serve-policy.md)
  * [<span data-ttu-id="dda88-180">DeleteSelfServePolicies</span><span class="sxs-lookup"><span data-stu-id="dda88-180">DeleteSelfServePolicies</span></span>](delete-a-self-serve-policy.md)

* <span data-ttu-id="dda88-181">Perfil da empresa de clientes</span><span class="sxs-lookup"><span data-stu-id="dda88-181">Customers Company Profile</span></span>
  * <span data-ttu-id="dda88-182">[Número de Registo de Organização Adicionado](create-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="dda88-182">Added [OrganizationRegistrationNumber](create-a-customer.md)</span></span>

* <span data-ttu-id="dda88-183">CustomerBillingProfile.DefaultAddress</span><span class="sxs-lookup"><span data-stu-id="dda88-183">CustomerBillingProfile.DefaultAddress</span></span>
  * <span data-ttu-id="dda88-184">Nome médio adicionado</span><span class="sxs-lookup"><span data-stu-id="dda88-184">Added MiddleName</span></span>

## <a name="version-1162"></a><span data-ttu-id="dda88-185">Versão 1.16.2</span><span class="sxs-lookup"><span data-stu-id="dda88-185">Version 1.16.2</span></span>

<span data-ttu-id="dda88-186">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.2) v1.16.2 é agora disponibilidade geral.</span><span class="sxs-lookup"><span data-stu-id="dda88-186">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.2) v1.16.2 is now general availability.</span></span> <span data-ttu-id="dda88-187">Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="dda88-187">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="dda88-188">As seguintes alterações estão incluídas nesta versão:</span><span class="sxs-lookup"><span data-stu-id="dda88-188">The following changes are included in this version:</span></span>

* <span data-ttu-id="dda88-189">Atualizar tipos de operação suportados para Registo de Auditoria.</span><span class="sxs-lookup"><span data-stu-id="dda88-189">Update supported operation types for Audit Record.</span></span> <span data-ttu-id="dda88-190">Os recém-adicionados são:</span><span class="sxs-lookup"><span data-stu-id="dda88-190">The newly added ones are:</span></span>
  * <span data-ttu-id="dda88-191">CreateSelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="dda88-191">CreateSelfServePolicy</span></span>
  * <span data-ttu-id="dda88-192">UpdateSelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="dda88-192">UpdateSelfServePolicy</span></span>
  * <span data-ttu-id="dda88-193">DeleteSelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="dda88-193">DeleteSelfServePolicy</span></span>
  * <span data-ttu-id="dda88-194">RemoverPartnerRelationship</span><span class="sxs-lookup"><span data-stu-id="dda88-194">RemovePartnerRelationship</span></span>
  * <span data-ttu-id="dda88-195">ExcluirTipCustomer</span><span class="sxs-lookup"><span data-stu-id="dda88-195">DeleteTipCustomer</span></span>
  * <span data-ttu-id="dda88-196">CreateRelatedReferral</span><span class="sxs-lookup"><span data-stu-id="dda88-196">CreateRelatedReferral</span></span>
  * <span data-ttu-id="dda88-197">UpdateRelatedReferral</span><span class="sxs-lookup"><span data-stu-id="dda88-197">UpdateRelatedReferral</span></span>

* <span data-ttu-id="dda88-198">A criação de pedido de serviço está agora depreciada</span><span class="sxs-lookup"><span data-stu-id="dda88-198">Service request creation is now deprecated</span></span>
* <span data-ttu-id="dda88-199">Os tópicos de apoio são agora depreciados</span><span class="sxs-lookup"><span data-stu-id="dda88-199">Support topics are now deprecated</span></span>


## <a name="version-1161"></a><span data-ttu-id="dda88-200">Versão 1.16.1</span><span class="sxs-lookup"><span data-stu-id="dda88-200">Version 1.16.1</span></span>

<span data-ttu-id="dda88-201">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.1) v1.16.1 é agora disponibilidade geral.</span><span class="sxs-lookup"><span data-stu-id="dda88-201">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.1) v1.16.1 is now general availability.</span></span> <span data-ttu-id="dda88-202">Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="dda88-202">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="dda88-203">As seguintes alterações estão incluídas nesta versão:</span><span class="sxs-lookup"><span data-stu-id="dda88-203">The following changes are included in this version:</span></span>

<span data-ttu-id="dda88-204">Migramos o Atual Microsoft Partner Center SDK de .NET Framework para a plataforma .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="dda88-204">We have migrated the existing Microsoft Partner Center SDK from .NET Framework to .NET Standard 2.0 platform.</span></span> <span data-ttu-id="dda88-205">Isto tornará o SDK compatível com as aplicações existentes utilizando .NET Framework 4.6.1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="dda88-205">This will make the SDK compatible with existing applications using .NET Framework 4.6.1 and above.</span></span> <span data-ttu-id="dda88-206">O SDK irá suportar .NET Core 2.0 e superior.</span><span class="sxs-lookup"><span data-stu-id="dda88-206">The SDK will support .NET Core 2.0 and above.</span></span> <span data-ttu-id="dda88-207">Verifique [o suporte de implementação .NET](/dotnet/standard/net-standard) antes de o apresentar às aplicações existentes.</span><span class="sxs-lookup"><span data-stu-id="dda88-207">Check [.NET implementation support](/dotnet/standard/net-standard) before porting it to existing applications.</span></span>   


## <a name="version-1153"></a><span data-ttu-id="dda88-208">Versão 1.15.3</span><span class="sxs-lookup"><span data-stu-id="dda88-208">Version 1.15.3</span></span>
<span data-ttu-id="dda88-209">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.15.3) v1.15.3 é agora disponibilidade geral.</span><span class="sxs-lookup"><span data-stu-id="dda88-209">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.15.3) v1.15.3 is now general availability.</span></span> <span data-ttu-id="dda88-210">Estão também disponíveis APIs de REST e [amostras GitHub.](https://github.com/Microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="dda88-210">Updated REST APIs and [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="dda88-211">As seguintes alterações estão incluídas nesta versão:</span><span class="sxs-lookup"><span data-stu-id="dda88-211">The following changes are included in this version:</span></span>

* <span data-ttu-id="dda88-212">Acordo de Parceiro</span><span class="sxs-lookup"><span data-stu-id="dda88-212">Partner Agreement</span></span>
  * <span data-ttu-id="dda88-213">Adicionou a capacidade de os fornecedores indiretos verificarem o [estado do Microsoft Partner Agreement dos revendedores indiretos](verify-indirect-reseller-mpa-status.md).</span><span class="sxs-lookup"><span data-stu-id="dda88-213">Added the ability for indirect providers to [verify Microsoft Partner Agreement status of indirect resellers](verify-indirect-reseller-mpa-status.md).</span></span>
* <span data-ttu-id="dda88-214">Produtos</span><span class="sxs-lookup"><span data-stu-id="dda88-214">Products</span></span>
  * <span data-ttu-id="dda88-215">As duas interfaces seguintes foram incorretamente colocadas no espaço de nomes Microsoft.Store.PartnerCenter.Products.</span><span class="sxs-lookup"><span data-stu-id="dda88-215">The following two interfaces were incorrectly placed under the Microsoft.Store.PartnerCenter.Products namespace.</span></span> <span data-ttu-id="dda88-216">Agora, estão localizados sob o espaço de nomes Microsoft.Store.PartnerCenter.Customers.Products.Products.</span><span class="sxs-lookup"><span data-stu-id="dda88-216">Now, they are located under the Microsoft.Store.PartnerCenter.Customers.Products namespace.</span></span>
    * <span data-ttu-id="dda88-217">ICustomerProductByReservationScope</span><span class="sxs-lookup"><span data-stu-id="dda88-217">ICustomerProductByReservationScope</span></span>
    * <span data-ttu-id="dda88-218">ICustomerSkuByReservationScope</span><span class="sxs-lookup"><span data-stu-id="dda88-218">ICustomerSkuByReservationScope</span></span>
