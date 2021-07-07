---
title: Criar Revendedor Indireto na Caixa de Areia
description: Fornece informações aos fornecedores indiretos da Sandbox sobre a ativação de testes de ponta a ponta utilizando APIs.
ms.date: 5/24/2021
ms.author: vijvala
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 93e26792b66e447a0047bd550f4302c7fca4e87b
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973439"
---
# <a name="create-indirect-reseller-in-sandbox"></a><span data-ttu-id="34294-103">Criar Revendedor Indireto na Caixa de Areia</span><span class="sxs-lookup"><span data-stu-id="34294-103">Create Indirect Reseller in Sandbox</span></span>

<span data-ttu-id="34294-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="34294-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="34294-105">Este documento mostra como criar fornecedores indiretos sandbox e permitir testes de ponta a ponta utilizando APIs.</span><span class="sxs-lookup"><span data-stu-id="34294-105">This document shows how to create Sandbox Indirect Providers and enable end-to-end testing using APIs.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="34294-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="34294-106">Prerequisites</span></span>

- <span data-ttu-id="34294-107">Credenciais descritas na [Autenticação do Centro de Parceiros.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="34294-107">Credentials as described in [Partner Center Authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="34294-108">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="34294-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="csp-indirect-provider"></a><span data-ttu-id="34294-109">CSP Indirect Provider</span><span class="sxs-lookup"><span data-stu-id="34294-109">CSP Indirect Provider</span></span>

| <span data-ttu-id="34294-110">Capacidades de produção</span><span class="sxs-lookup"><span data-stu-id="34294-110">Production capabilities</span></span>             | <span data-ttu-id="34294-111">Capacidades de caixa de areia</span><span class="sxs-lookup"><span data-stu-id="34294-111">Sandbox capabilities</span></span>                            |
|-------------------------------------|-------------------------------------------------|
| <span data-ttu-id="34294-112">Vende através do revendedor indireto ao cliente final</span><span class="sxs-lookup"><span data-stu-id="34294-112">Sells through the indirect reseller to the end customer</span></span> | <span data-ttu-id="34294-113">Suportado</span><span class="sxs-lookup"><span data-stu-id="34294-113">Supported</span></span> |
| <span data-ttu-id="34294-114">Detém todas as vendas, faturação, provisionamento e gestão/suporte</span><span class="sxs-lookup"><span data-stu-id="34294-114">Owns all sales, billing, provisioning, and management/support</span></span> | <span data-ttu-id="34294-115">Suportado</span><span class="sxs-lookup"><span data-stu-id="34294-115">Supported</span></span> |
| <span data-ttu-id="34294-116">Solicite uma parceria com os revendedores</span><span class="sxs-lookup"><span data-stu-id="34294-116">Request a partnership with the resellers</span></span> | <span data-ttu-id="34294-117">Suportado</span><span class="sxs-lookup"><span data-stu-id="34294-117">Supported</span></span> |
| <span data-ttu-id="34294-118">Ver clientes por Revendedor</span><span class="sxs-lookup"><span data-stu-id="34294-118">View customers by Reseller</span></span> | <span data-ttu-id="34294-119">Suportado</span><span class="sxs-lookup"><span data-stu-id="34294-119">Supported</span></span> |
| <span data-ttu-id="34294-120">Adicionar novos clientes por revendedores</span><span class="sxs-lookup"><span data-stu-id="34294-120">Add new customers by resellers</span></span> | <span data-ttu-id="34294-121">Suportado</span><span class="sxs-lookup"><span data-stu-id="34294-121">Supported</span></span> |
| <span data-ttu-id="34294-122">Convidar clientes</span><span class="sxs-lookup"><span data-stu-id="34294-122">Invite customers</span></span> | <span data-ttu-id="34294-123">Pedido de relacionamento com o cliente não suportado na Sandbox</span><span class="sxs-lookup"><span data-stu-id="34294-123">Customer relationship request not supported in Sandbox</span></span> |
| <span data-ttu-id="34294-124">Sandbox Indireta Fornecedor pode selecionar Sandbox IR (MPN ID) como o POR enquanto coloca a transação</span><span class="sxs-lookup"><span data-stu-id="34294-124">Sandbox Indirect Provider can select Sandbox IR (MPN ID) as the POR while placing the transaction</span></span> | <span data-ttu-id="34294-125">Suportado</span><span class="sxs-lookup"><span data-stu-id="34294-125">Supported</span></span> |
| <span data-ttu-id="34294-126">Não apoiado na produção</span><span class="sxs-lookup"><span data-stu-id="34294-126">Not supported in production</span></span> | <span data-ttu-id="34294-127">Sandbox Fornecedor Indireto pode criar Revendedor Indireto Sandbox</span><span class="sxs-lookup"><span data-stu-id="34294-127">Sandbox Indirect Provider can create Sandbox Indirect Reseller</span></span> |
| <span data-ttu-id="34294-128">Sandbox MPN ID deve ser introduzido, o produto MPN ID não funcionará</span><span class="sxs-lookup"><span data-stu-id="34294-128">Sandbox MPN ID should be entered, the product MPN ID will not work</span></span> | <span data-ttu-id="34294-129">Não apoiado na produção</span><span class="sxs-lookup"><span data-stu-id="34294-129">Not supported in production</span></span> |
| <span data-ttu-id="34294-130">Não apoiado na produção</span><span class="sxs-lookup"><span data-stu-id="34294-130">Not supported in production</span></span> | <span data-ttu-id="34294-131">Sandbox Fornecedor Indireto pode eliminar Revendedor Indireto Sandbox</span><span class="sxs-lookup"><span data-stu-id="34294-131">Sandbox Indirect Provider can delete Sandbox Indirect Reseller</span></span> |

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller"></a><span data-ttu-id="34294-132">Sandbox Fornecedor Indireto – Criar Revendedor Indireto Sandbox</span><span class="sxs-lookup"><span data-stu-id="34294-132">Sandbox Indirect Provider – Create Sandbox Indirect Reseller</span></span>

<span data-ttu-id="34294-133">Esta funcionalidade só está disponível na Sandbox e dá aos Fornecedores Indiretos sandbox a capacidade de criar revendedores indiretos sandbox.</span><span class="sxs-lookup"><span data-stu-id="34294-133">This feature is only available in the Sandbox and gives Sandbox Indirect Providers an ability to create Sandbox Indirect Resellers.</span></span>

1. <span data-ttu-id="34294-134">Limite de cinco revendedores indiretos sandbox permitidos por Sandbox Fornecedor Indireto</span><span class="sxs-lookup"><span data-stu-id="34294-134">Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider</span></span>
2. <span data-ttu-id="34294-135">Sandbox Indirect Providers pode criar clientes com `associatedPartnerId` revendedor indireto Sandbox</span><span class="sxs-lookup"><span data-stu-id="34294-135">Sandbox Indirect Providers can create customers with `associatedPartnerId` of Sandbox Indirect Reseller</span></span>
3. <span data-ttu-id="34294-136">Introduza o [ID MPN](/partner-center/mpn-create-a-partner-center-account) de uma região específica enquanto cria um Revendedor Indireto Sandbox.</span><span class="sxs-lookup"><span data-stu-id="34294-136">Enter the [MPN](/partner-center/mpn-create-a-partner-center-account) ID of a specific region while creating a Sandbox Indirect Reseller.</span></span> <span data-ttu-id="34294-137">Vários Revendedores Indiretos sandbox podem ser criados com o mesmo ID MPN da Sandbox.</span><span class="sxs-lookup"><span data-stu-id="34294-137">Multiple Sandbox Indirect Resellers can be created with the same Sandbox MPN ID.</span></span>
4. <span data-ttu-id="34294-138">Apenas 75 clientes são permitidos por Sandbox Indireto Fornecedor</span><span class="sxs-lookup"><span data-stu-id="34294-138">Only 75 customers are allowed per Sandbox Indirect Provider</span></span>

## <a name="sandbox-indirect-resellers--view-customers"></a><span data-ttu-id="34294-139">Sandbox Revendedores Indiretos – Ver clientes</span><span class="sxs-lookup"><span data-stu-id="34294-139">Sandbox Indirect Resellers – View customers</span></span>

1. <span data-ttu-id="34294-140">Os Revendedores Indiretos sandbox podem ver a lista de clientes de sandbox por fornecedores indiretos da Sandbox.</span><span class="sxs-lookup"><span data-stu-id="34294-140">Sandbox Indirect Resellers can view the list of sandbox customers by Sandbox Indirect providers.</span></span>
2. <span data-ttu-id="34294-141">Os Revendedores Indiretos sandbox podem gerir a conta do cliente utilizando permissões de administrador delegadas.</span><span class="sxs-lookup"><span data-stu-id="34294-141">Sandbox Indirect Resellers can manage the customer account by using delegated administrator permissions.</span></span>

## <a name="create-sandbox-indirect-reseller-through-api"></a><span data-ttu-id="34294-142">Criar Sandbox Reseller Indireto através da API</span><span class="sxs-lookup"><span data-stu-id="34294-142">Create Sandbox Indirect Reseller through API</span></span>

### <a name="rest-request"></a><span data-ttu-id="34294-143">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="34294-143">REST request</span></span>

#### <a name="request-syntax"></a><span data-ttu-id="34294-144">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="34294-144">Request syntax</span></span>

| <span data-ttu-id="34294-145">**Método**</span><span class="sxs-lookup"><span data-stu-id="34294-145">**Method**</span></span> | <span data-ttu-id="34294-146">**URI do pedido**</span><span class="sxs-lookup"><span data-stu-id="34294-146">**Request URI**</span></span>                                                        |
|------------|------------------------------------------------------------------------|
| <span data-ttu-id="34294-147">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="34294-147">**POST**</span></span>   | <span data-ttu-id="34294-148">[*{baseURL}*](partner-center-rest-urls.md)/v1//sandboxIndirectReseller</span><span class="sxs-lookup"><span data-stu-id="34294-148">[*{baseURL}*](partner-center-rest-urls.md)/v1//sandboxIndirectReseller</span></span> |

#### <a name="request-headers"></a><span data-ttu-id="34294-149">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="34294-149">Request headers</span></span>

- <span data-ttu-id="34294-150">Esta API é idempotente (não produzirá um resultado diferente se lhe chamar várias vezes).</span><span class="sxs-lookup"><span data-stu-id="34294-150">This API is idempotent (it will not yield a different result if you call it multiple times).</span></span>
- <span data-ttu-id="34294-151">É necessária uma identificação de pedido e uma identificação de correlação.</span><span class="sxs-lookup"><span data-stu-id="34294-151">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="34294-152">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="34294-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

#### <a name="request-body"></a><span data-ttu-id="34294-153">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="34294-153">Request body</span></span>

<span data-ttu-id="34294-154">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="34294-154">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="34294-155">Propriedade</span><span class="sxs-lookup"><span data-stu-id="34294-155">Property</span></span>             | <span data-ttu-id="34294-156">Tipo</span><span class="sxs-lookup"><span data-stu-id="34294-156">Type</span></span>           | <span data-ttu-id="34294-157">Description</span><span class="sxs-lookup"><span data-stu-id="34294-157">Description</span></span>                                      |
|----------------------|----------------|--------------------------------------------------|
| <span data-ttu-id="34294-158">mpnId</span><span class="sxs-lookup"><span data-stu-id="34294-158">mpnId</span></span>                | <span data-ttu-id="34294-159">string</span><span class="sxs-lookup"><span data-stu-id="34294-159">string</span></span>         | <span data-ttu-id="34294-160">O ID do MPN para o IR em região específica</span><span class="sxs-lookup"><span data-stu-id="34294-160">The MPN ID for the IR in specific region</span></span>         |
| <span data-ttu-id="34294-161">inquilino</span><span class="sxs-lookup"><span data-stu-id="34294-161">tenant</span></span>               | <span data-ttu-id="34294-162">Cadeia de &lt; dicionário, corda&gt;</span><span class="sxs-lookup"><span data-stu-id="34294-162">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="34294-163">Recolha de informação básica que define uma conta a ser criada</span><span class="sxs-lookup"><span data-stu-id="34294-163">Collection of basic information that defines an account to be created</span></span> |
| <span data-ttu-id="34294-164">legalBusinessProfile</span><span class="sxs-lookup"><span data-stu-id="34294-164">legalBusinessProfile</span></span> | <span data-ttu-id="34294-165">Cadeia de &lt; dicionário, corda&gt;</span><span class="sxs-lookup"><span data-stu-id="34294-165">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="34294-166">Recolha de informação que represente a entidade empresarial legal, como contacto, morada e nome</span><span class="sxs-lookup"><span data-stu-id="34294-166">Collection of information that represents the legal business entity such as contact, address, and name</span></span> |
| <span data-ttu-id="34294-167">organizaçãoProfileLanguage</span><span class="sxs-lookup"><span data-stu-id="34294-167">organizationProfileLanguage</span></span> | <span data-ttu-id="34294-168">Cadeia de &lt; dicionário, corda&gt;</span><span class="sxs-lookup"><span data-stu-id="34294-168">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="34294-169">O identificador de linguagem da organização</span><span class="sxs-lookup"><span data-stu-id="34294-169">The organization language identifier</span></span> |

<span data-ttu-id="34294-170">Esta tabela descreve os imóveis exigidos no atributo do **inquilino.**</span><span class="sxs-lookup"><span data-stu-id="34294-170">This table describes the required properties in the **tenant** attribute.</span></span>

| <span data-ttu-id="34294-171">Propriedade</span><span class="sxs-lookup"><span data-stu-id="34294-171">Property</span></span>           | <span data-ttu-id="34294-172">Tipo</span><span class="sxs-lookup"><span data-stu-id="34294-172">Type</span></span>           | <span data-ttu-id="34294-173">Description</span><span class="sxs-lookup"><span data-stu-id="34294-173">Description</span></span>                         |
|--------------------|----------------|-------------------------------------|
| <span data-ttu-id="34294-174">domínioPrefixo</span><span class="sxs-lookup"><span data-stu-id="34294-174">domainPrefix</span></span>       | <span data-ttu-id="34294-175">Corda; único</span><span class="sxs-lookup"><span data-stu-id="34294-175">String; unique</span></span> | <span data-ttu-id="34294-176">Domínio para a conta do inquilino</span><span class="sxs-lookup"><span data-stu-id="34294-176">Domain for the tenant account</span></span>       |
| <span data-ttu-id="34294-177">name</span><span class="sxs-lookup"><span data-stu-id="34294-177">name</span></span>               | <span data-ttu-id="34294-178">string</span><span class="sxs-lookup"><span data-stu-id="34294-178">string</span></span>         | <span data-ttu-id="34294-179">Nome amigável do inquilino</span><span class="sxs-lookup"><span data-stu-id="34294-179">Friendly name of the tenant</span></span>         |
| <span data-ttu-id="34294-180">displayName</span><span class="sxs-lookup"><span data-stu-id="34294-180">displayName</span></span>        | <span data-ttu-id="34294-181">string</span><span class="sxs-lookup"><span data-stu-id="34294-181">string</span></span>         | <span data-ttu-id="34294-182">Mostrar o nome da conta</span><span class="sxs-lookup"><span data-stu-id="34294-182">Display name for the account</span></span>        |
| <span data-ttu-id="34294-183">adminUserName</span><span class="sxs-lookup"><span data-stu-id="34294-183">adminUserName</span></span>      | <span data-ttu-id="34294-184">string</span><span class="sxs-lookup"><span data-stu-id="34294-184">string</span></span>         | <span data-ttu-id="34294-185">Nome do utilizador para a conta de login</span><span class="sxs-lookup"><span data-stu-id="34294-185">User name for the account for login</span></span> |
| <span data-ttu-id="34294-186">nome adminfirst</span><span class="sxs-lookup"><span data-stu-id="34294-186">adminfirstname</span></span>     | <span data-ttu-id="34294-187">string</span><span class="sxs-lookup"><span data-stu-id="34294-187">string</span></span>         | <span data-ttu-id="34294-188">Primeiro nome para o utilizador administrador</span><span class="sxs-lookup"><span data-stu-id="34294-188">First Name for the admin user</span></span>       |
| <span data-ttu-id="34294-189">nome adminlastname</span><span class="sxs-lookup"><span data-stu-id="34294-189">adminlastname</span></span>      | <span data-ttu-id="34294-190">string</span><span class="sxs-lookup"><span data-stu-id="34294-190">string</span></span>         | <span data-ttu-id="34294-191">Apelido para o utilizador administrador</span><span class="sxs-lookup"><span data-stu-id="34294-191">Last Name for the admin user</span></span>        |
| <span data-ttu-id="34294-192">adminAlernateEmail</span><span class="sxs-lookup"><span data-stu-id="34294-192">adminAlernateEmail</span></span> | <span data-ttu-id="34294-193">string</span><span class="sxs-lookup"><span data-stu-id="34294-193">string</span></span>         | <span data-ttu-id="34294-194">e-mail para o utilizador administrador</span><span class="sxs-lookup"><span data-stu-id="34294-194">email for the admin user</span></span>            |
| <span data-ttu-id="34294-195">país</span><span class="sxs-lookup"><span data-stu-id="34294-195">country</span></span>            | <span data-ttu-id="34294-196">string</span><span class="sxs-lookup"><span data-stu-id="34294-196">string</span></span>         | <span data-ttu-id="34294-197">País da conta</span><span class="sxs-lookup"><span data-stu-id="34294-197">Country of the account</span></span>              |
| <span data-ttu-id="34294-198">cultura</span><span class="sxs-lookup"><span data-stu-id="34294-198">culture</span></span>            | <span data-ttu-id="34294-199">string</span><span class="sxs-lookup"><span data-stu-id="34294-199">string</span></span>         | <span data-ttu-id="34294-200">Preferência linguística por conta</span><span class="sxs-lookup"><span data-stu-id="34294-200">Language preference for account</span></span>     |

<span data-ttu-id="34294-201">Esta tabela descreve as propriedades necessárias no atributo **legal BusinessinessProfile.**</span><span class="sxs-lookup"><span data-stu-id="34294-201">This table describes the required properties in the **legalBusinessProfile** attribute.</span></span>

| <span data-ttu-id="34294-202">Propriedade</span><span class="sxs-lookup"><span data-stu-id="34294-202">Property</span></span>       | <span data-ttu-id="34294-203">Tipo</span><span class="sxs-lookup"><span data-stu-id="34294-203">Type</span></span>                             | <span data-ttu-id="34294-204">Description</span><span class="sxs-lookup"><span data-stu-id="34294-204">Description</span></span>                          |
|----------------|----------------------------------|--------------------------------------|
| <span data-ttu-id="34294-205">nome da empresa</span><span class="sxs-lookup"><span data-stu-id="34294-205">companyName</span></span>    | <span data-ttu-id="34294-206">string</span><span class="sxs-lookup"><span data-stu-id="34294-206">string</span></span>                           | <span data-ttu-id="34294-207">Nome da empresa para entidade jurídica</span><span class="sxs-lookup"><span data-stu-id="34294-207">Company name for legal entity</span></span>        |
| <span data-ttu-id="34294-208">address</span><span class="sxs-lookup"><span data-stu-id="34294-208">address</span></span>        | <span data-ttu-id="34294-209">Cadeia de &lt; dicionário, corda&gt;</span><span class="sxs-lookup"><span data-stu-id="34294-209">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="34294-210">Endereço da localização da entidade jurídica</span><span class="sxs-lookup"><span data-stu-id="34294-210">Address of the legal entity location</span></span> |
| <span data-ttu-id="34294-211">principalContact</span><span class="sxs-lookup"><span data-stu-id="34294-211">primaryContact</span></span> | <span data-ttu-id="34294-212">Cadeia de &lt; dicionário, corda&gt;</span><span class="sxs-lookup"><span data-stu-id="34294-212">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="34294-213">Detalhes de contato da empresa</span><span class="sxs-lookup"><span data-stu-id="34294-213">Contact details of the company</span></span>       |
| <span data-ttu-id="34294-214">cultura</span><span class="sxs-lookup"><span data-stu-id="34294-214">culture</span></span>        | <span data-ttu-id="34294-215">string</span><span class="sxs-lookup"><span data-stu-id="34294-215">string</span></span>                           | <span data-ttu-id="34294-216">Linguagem preferida pela empresa</span><span class="sxs-lookup"><span data-stu-id="34294-216">Language preferred by the company</span></span>    |

### <a name="request-example"></a><span data-ttu-id="34294-217">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="34294-217">Request Example</span></span>

```http
{
    "mpnId": "6363276",
    "tenant": {
        "domainPrefix": "TipIRIntTest705",
        "name": "TipIRIntTest705",
        "displayName": "TipIRIntTest705",
        "adminUserName": "admin",
        "adminFirstName": "TipIRIntTest705",
        "adminLastName": "TipIRIntTest705",
        "adminAlternateEmail": "TipIRIntTest705@test.com",
        "country": "US",
        "culture": "en-us"
    },
    "legalBusinessProfile": {
        "companyName": "TipIRIntTest705",
        "address": {
            "country": "FR",
            "city": "Issy-les-Moulineaux",
            "state": "",
            "addressLine1": "39-41 quai du Président Roosevelt",
            "addressLine2": "",
            "postalCode": "92130"
        },
        "primaryContact": {
            "firstName": "Sandbox",
            "lastName": "Scenario",
            "email": "Sandbox.Scenario@test.com",
            "phoneNumber": "1234567890"
        },
        "culture": "en-US"
    },
    "organizationProfileLanguage": "en"
}
```

### <a name="rest-response"></a><span data-ttu-id="34294-218">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="34294-218">REST response</span></span>

<span data-ttu-id="34294-219">Se for bem sucedido, este método devolve o recurso IV de Sandbox povoado no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="34294-219">If successful, this method returns the populated Sandbox IR resource in the response body.</span></span>

```http
{

    "accountId": "6f94b119-793c-44c7-862b-c327c9057eab",
    "mpnId": "6363276",
    "tenant": {
        "id": "6f94b119-793c-44c7-862b-c327c9057eab",
        "adminUserAccount": "admin@TipIRIntTest705.onmicrosoft.com",
        "password": "\*\*\*\*\*\*”
    },
    "agreementSignature": {
        "id": "30ac23e7-e200-42cf-a5bc-dd9148cdc632",
        "accountId": "6f94b119-793c-44c7-862b-c327c9057eab",
        "agreementId": "1e18c5b2-e42a-4b84-82c8-d0155aa94c6e",
        "agreementType": "ValueAddedReseller",
        "dateSigned": "2021-02-23T18:10:14.8461137Z",
        "signedByFirstName": "Test123@PLAMUATT2NetNewTip.onmicrosoft.com",
        "signedByUserPrincipalName": "Test123@PLAMUATT2NetNewTip.onmicrosoft.com",
        "signedByUserObjectId": "e6e0c29d-acda-4ef2-b370-d37a4e06fb98",
        "signedByUserTenantId": "0e195b37-4574-4539-bc42-0e539b9684c0",
        "attributes": {
            "objectType": "AgreementSignatureResponse"
        }
    },
    "partnerRelationship": {
        "id": "0e195b37-4574-4539-bc42-0e539b9684c0",
        "name": "PLAMUATT2NetNew",
        "relationshipType": "is\_indirect\_reseller\_of",
        "state": "Active",
        "mpnId": "6363276",
        "attributes": {
            "objectType": "PartnerRelationshipResponse"
        }
    }
}
```
