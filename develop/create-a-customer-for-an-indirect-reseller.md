---
title: Criar um cliente para um revendedor indireto
description: Saiba como um fornecedor indireto pode usar APIs do Partner Center para criar um cliente para um revendedor indireto.
ms.date: 11/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: e2386f1963a5bb3ea4269bcbf4327c75987f3b91
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770176"
---
# <a name="create-a-customer-for-an-indirect-reseller-using-partner-center-apis"></a><span data-ttu-id="919c2-103">Crie um cliente para um revendedor indireto usando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="919c2-103">Create a customer for an indirect reseller using Partner Center APIs</span></span>

<span data-ttu-id="919c2-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="919c2-104">**Applies to:**</span></span>

- <span data-ttu-id="919c2-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="919c2-105">Partner Center</span></span>

<span data-ttu-id="919c2-106">Um fornecedor indireto pode criar um cliente para um revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="919c2-106">An indirect provider can create a customer for an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="919c2-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="919c2-107">Prerequisites</span></span>

- <span data-ttu-id="919c2-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="919c2-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="919c2-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="919c2-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="919c2-110">O identificador do inquilino do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="919c2-110">The tenant identifier of the indirect reseller.</span></span>

- <span data-ttu-id="919c2-111">O revendedor indireto deve ter uma parceria com o fornecedor indireto.</span><span class="sxs-lookup"><span data-stu-id="919c2-111">The indirect reseller must have a partnership with the indirect provider.</span></span>

## <a name="c"></a><span data-ttu-id="919c2-112">C\#</span><span class="sxs-lookup"><span data-stu-id="919c2-112">C\#</span></span>

<span data-ttu-id="919c2-113">Para adicionar um novo cliente para um revendedor indireto:</span><span class="sxs-lookup"><span data-stu-id="919c2-113">To add a new customer for an indirect reseller:</span></span>

1. <span data-ttu-id="919c2-114">Instantaneamente um novo objeto [**de Cliente**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) e, em seguida, instantaneamente e povoar o [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) e [**o CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span><span class="sxs-lookup"><span data-stu-id="919c2-114">Instantiate a new [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object and then instantiate and populate the [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) and [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span></span> <span data-ttu-id="919c2-115">Certifique-se de atribuir o ID do revendedor indireto à propriedade [**AssociatedPartnerID.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid)</span><span class="sxs-lookup"><span data-stu-id="919c2-115">Be sure to assign the indirect reseller ID to the [**AssociatedPartnerID**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid) property.</span></span>

2. <span data-ttu-id="919c2-116">Utilize a propriedade [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para obter uma interface para as operações de recolha de clientes.</span><span class="sxs-lookup"><span data-stu-id="919c2-116">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) property to get an interface to customer collection operations.</span></span>

3. <span data-ttu-id="919c2-117">Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) ou [**Criar Aync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) para criar o cliente.</span><span class="sxs-lookup"><span data-stu-id="919c2-117">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) method to create the customer.</span></span>

### <a name="c-example"></a><span data-ttu-id="919c2-118">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="919c2-118">C\# example</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var indirectResellerId;
var customerToCreate = new Customer()
{
    CompanyProfile = new CustomerCompanyProfile()
    {
        Domain = string.Format(CultureInfo.InvariantCulture,
            "WingtipToys{0}.{1}",
            new Random().Next(),
            this.Context.Configuration.Scenario.CustomerDomainSuffix)
    },
    BillingProfile = new CustomerBillingProfile()
    {
        Culture = "EN-US",
        Email = "Gena@wingtiptoys.com",
        Language = "En",
        CompanyName = "Wingtip Toys" + new Random().Next(),
        DefaultAddress = new Address()
        {
            FirstName = "Gena",
            LastName = "Soto",
            AddressLine1 = "One Microsoft Way",
            City = "Redmond",
            State = "WA",
            Country = "US",
            PostalCode = "98052",
            PhoneNumber = "4255550101"
        }
    },
    AssociatedPartnerId = indirectResellerId
};

var newCustomer = partnerOperations.Customers.Create(customerToCreate);
```

<span data-ttu-id="919c2-119">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="919c2-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="919c2-120">**Projeto**: Partner Center SDK Samples **Class**: CreateCustomerforIndirectReseller.cs</span><span class="sxs-lookup"><span data-stu-id="919c2-120">**Project**: Partner Center SDK Samples **Class**: CreateCustomerforIndirectReseller.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="919c2-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="919c2-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="919c2-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="919c2-122">Request syntax</span></span>

| <span data-ttu-id="919c2-123">Método</span><span class="sxs-lookup"><span data-stu-id="919c2-123">Method</span></span>   | <span data-ttu-id="919c2-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="919c2-124">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="919c2-125">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="919c2-125">**POST**</span></span> | <span data-ttu-id="919c2-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="919c2-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="919c2-127">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="919c2-127">Request headers</span></span>

<span data-ttu-id="919c2-128">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="919c2-128">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="919c2-129">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="919c2-129">Request body</span></span>

<span data-ttu-id="919c2-130">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="919c2-130">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="919c2-131">Nome</span><span class="sxs-lookup"><span data-stu-id="919c2-131">Name</span></span>                                          | <span data-ttu-id="919c2-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="919c2-132">Type</span></span>   | <span data-ttu-id="919c2-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="919c2-133">Required</span></span> | <span data-ttu-id="919c2-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="919c2-134">Description</span></span>                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<span data-ttu-id="919c2-135">BillingProfile</span><span class="sxs-lookup"><span data-stu-id="919c2-135">BillingProfile</span></span>](#billing-profile)             | <span data-ttu-id="919c2-136">objeto</span><span class="sxs-lookup"><span data-stu-id="919c2-136">object</span></span> | <span data-ttu-id="919c2-137">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-137">Yes</span></span>      | <span data-ttu-id="919c2-138">A informação do perfil de faturação do cliente.</span><span class="sxs-lookup"><span data-stu-id="919c2-138">The customer's billing profile information.</span></span>                                                                                                                                                                                                                                                                                                           |
| [<span data-ttu-id="919c2-139">EmpresaProfile</span><span class="sxs-lookup"><span data-stu-id="919c2-139">CompanyProfile</span></span>](#company-profile)             | <span data-ttu-id="919c2-140">objeto</span><span class="sxs-lookup"><span data-stu-id="919c2-140">object</span></span> | <span data-ttu-id="919c2-141">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-141">Yes</span></span>      | <span data-ttu-id="919c2-142">Informação do perfil da empresa do cliente.</span><span class="sxs-lookup"><span data-stu-id="919c2-142">The customer's company profile information.</span></span>                                                               
| [<span data-ttu-id="919c2-143">PartnerId Associado</span><span class="sxs-lookup"><span data-stu-id="919c2-143">AssociatedPartnerId</span></span>](customer-resources.md#customer) | <span data-ttu-id="919c2-144">string</span><span class="sxs-lookup"><span data-stu-id="919c2-144">string</span></span> | <span data-ttu-id="919c2-145">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-145">Yes</span></span>      | <span data-ttu-id="919c2-146">O iD do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="919c2-146">The indirect reseller ID.</span></span> <span data-ttu-id="919c2-147">O revendedor indireto, tal como indicado pelo ID aqui fornecido, deve ter uma parceria com o fornecedor indireto ou o pedido falhará.</span><span class="sxs-lookup"><span data-stu-id="919c2-147">The indirect reseller as indicated by the ID supplied here must have a partnership with the indirect provider or the request will fail.</span></span> <span data-ttu-id="919c2-148">Note também que se o valor AssociatedPartnerId não for fornecido, o cliente é criado como cliente direto do fornecedor indireto e não como revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="919c2-148">Also note that if the AssociatedPartnerId value isn't supplied, the customer is created as a direct customer of the indirect provider rather than the indirect reseller.</span></span> |
|<span data-ttu-id="919c2-149">Domínio</span><span class="sxs-lookup"><span data-stu-id="919c2-149">Domain</span></span>| <span data-ttu-id="919c2-150">String</span><span class="sxs-lookup"><span data-stu-id="919c2-150">String</span></span>| <span data-ttu-id="919c2-151">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-151">Yes</span></span>|<span data-ttu-id="919c2-152">O nome de domínio do cliente, como contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="919c2-152">The customer's domain name, such as contoso.onmicrosoft.com.</span></span>|
|<span data-ttu-id="919c2-153">organizaçãoRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="919c2-153">organizationRegistrationNumber</span></span>|    <span data-ttu-id="919c2-154">string</span><span class="sxs-lookup"><span data-stu-id="919c2-154">string</span></span>|<span data-ttu-id="919c2-155">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-155">Yes</span></span>|     <span data-ttu-id="919c2-156">Número de registo da organização do cliente (também referido como número INN em determinados países).</span><span class="sxs-lookup"><span data-stu-id="919c2-156">The customer’s organization registration number (also referred to as INN number in certain countries).</span></span> <span data-ttu-id="919c2-157">Apenas necessário para a empresa/organização do cliente localizada nos seguintes países.</span><span class="sxs-lookup"><span data-stu-id="919c2-157">Only required for customer’s company/organization located in the following countries.</span></span> <span data-ttu-id="919c2-158">Arménia(AM), Azerbaijão(AZ), Bielorrússia (BY), Hungria (HU), Cazaquistão (KZ), Quirguistão(KG), Moldávia (MD), Rússia(RU), Tajiquistão(TJ), Uzhbequistão(UZ), Ucrânia (UA).</span><span class="sxs-lookup"><span data-stu-id="919c2-158">Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA).</span></span> <span data-ttu-id="919c2-159">Para a empresa/organização do cliente localizada noutros países, tal não deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="919c2-159">For customer’s company/organization located in other countries this should not be specified.</span></span>|



#### <a name="billing-profile"></a><span data-ttu-id="919c2-160">Perfil de faturação</span><span class="sxs-lookup"><span data-stu-id="919c2-160">Billing profile</span></span>

<span data-ttu-id="919c2-161">Esta tabela descreve os campos mínimos exigidos do recurso [CustomerBillingProfile](customer-resources.md#customerbillingprofile) necessário para criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="919c2-161">This table describes the minimum required fields from the [CustomerBillingProfile](customer-resources.md#customerbillingprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="919c2-162">Nome</span><span class="sxs-lookup"><span data-stu-id="919c2-162">Name</span></span>             | <span data-ttu-id="919c2-163">Tipo</span><span class="sxs-lookup"><span data-stu-id="919c2-163">Type</span></span>                                     | <span data-ttu-id="919c2-164">Necessário</span><span class="sxs-lookup"><span data-stu-id="919c2-164">Required</span></span> | <span data-ttu-id="919c2-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="919c2-165">Description</span></span>                                                                                                                                                                                                     |
|------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="919c2-166">e-mail</span><span class="sxs-lookup"><span data-stu-id="919c2-166">email</span></span>            | <span data-ttu-id="919c2-167">string</span><span class="sxs-lookup"><span data-stu-id="919c2-167">string</span></span>                                   | <span data-ttu-id="919c2-168">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-168">Yes</span></span>      | <span data-ttu-id="919c2-169">O endereço de e-mail do cliente.</span><span class="sxs-lookup"><span data-stu-id="919c2-169">The customer's email address.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="919c2-170">cultura</span><span class="sxs-lookup"><span data-stu-id="919c2-170">culture</span></span>          | <span data-ttu-id="919c2-171">string</span><span class="sxs-lookup"><span data-stu-id="919c2-171">string</span></span>                                   | <span data-ttu-id="919c2-172">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-172">Yes</span></span>      | <span data-ttu-id="919c2-173">A sua cultura preferida para a comunicação e a moeda, como "en-US".</span><span class="sxs-lookup"><span data-stu-id="919c2-173">Their preferred culture for communication and currency, such as "en-US".</span></span> <span data-ttu-id="919c2-174">Consulte [o Partner Center com línguas e locais apoiados](partner-center-supported-languages-and-locales.md) para as culturas apoiadas.</span><span class="sxs-lookup"><span data-stu-id="919c2-174">See [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md) for the supported cultures.</span></span> |
| <span data-ttu-id="919c2-175">language</span><span class="sxs-lookup"><span data-stu-id="919c2-175">language</span></span>         | <span data-ttu-id="919c2-176">string</span><span class="sxs-lookup"><span data-stu-id="919c2-176">string</span></span>                                   | <span data-ttu-id="919c2-177">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-177">Yes</span></span>      | <span data-ttu-id="919c2-178">A linguagem padrão.</span><span class="sxs-lookup"><span data-stu-id="919c2-178">The default language.</span></span> <span data-ttu-id="919c2-179">Dois códigos linguísticos de caracteres (por exemplo `en` `fr` ou) são suportados.</span><span class="sxs-lookup"><span data-stu-id="919c2-179">Two character language codes (for example `en` or `fr`) are supported.</span></span>                                                                                                                                |
| <span data-ttu-id="919c2-180">nome da empresa \_</span><span class="sxs-lookup"><span data-stu-id="919c2-180">company\_name</span></span>    | <span data-ttu-id="919c2-181">string</span><span class="sxs-lookup"><span data-stu-id="919c2-181">string</span></span>                                   | <span data-ttu-id="919c2-182">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-182">Yes</span></span>      | <span data-ttu-id="919c2-183">O nome de empresa/organização registado.</span><span class="sxs-lookup"><span data-stu-id="919c2-183">The registered company/organization name.</span></span>                                                                                                                                                                       |
| <span data-ttu-id="919c2-184">endereço padrão \_</span><span class="sxs-lookup"><span data-stu-id="919c2-184">default\_address</span></span> | [<span data-ttu-id="919c2-185">Endereço</span><span class="sxs-lookup"><span data-stu-id="919c2-185">Address</span></span>](utility-resources.md#address) | <span data-ttu-id="919c2-186">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-186">Yes</span></span>      | <span data-ttu-id="919c2-187">O endereço registado da empresa/organização do cliente.</span><span class="sxs-lookup"><span data-stu-id="919c2-187">The registered address of the customer's company/organization.</span></span> <span data-ttu-id="919c2-188">Consulte o recurso [Address](utility-resources.md#address) para obter informações sobre eventuais limitações de comprimento.</span><span class="sxs-lookup"><span data-stu-id="919c2-188">See the [Address](utility-resources.md#address) resource for information on any length limitations.</span></span>                                             |

#### <a name="company-profile"></a><span data-ttu-id="919c2-189">Perfil da empresa</span><span class="sxs-lookup"><span data-stu-id="919c2-189">Company profile</span></span>

<span data-ttu-id="919c2-190">Esta tabela descreve os campos mínimos exigidos do recurso [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) necessário para criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="919c2-190">This table describes the minimum required fields from the [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="919c2-191">Nome</span><span class="sxs-lookup"><span data-stu-id="919c2-191">Name</span></span>   | <span data-ttu-id="919c2-192">Tipo</span><span class="sxs-lookup"><span data-stu-id="919c2-192">Type</span></span>   | <span data-ttu-id="919c2-193">Necessário</span><span class="sxs-lookup"><span data-stu-id="919c2-193">Required</span></span> | <span data-ttu-id="919c2-194">Descrição</span><span class="sxs-lookup"><span data-stu-id="919c2-194">Description</span></span>                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| <span data-ttu-id="919c2-195">domínio</span><span class="sxs-lookup"><span data-stu-id="919c2-195">domain</span></span> | <span data-ttu-id="919c2-196">string</span><span class="sxs-lookup"><span data-stu-id="919c2-196">string</span></span> | <span data-ttu-id="919c2-197">Sim</span><span class="sxs-lookup"><span data-stu-id="919c2-197">Yes</span></span>     | <span data-ttu-id="919c2-198">O nome de domínio do cliente, como contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="919c2-198">The customer's domain name, such as contoso.onmicrosoft.com.</span></span> |
| <span data-ttu-id="919c2-199">organizaçãoRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="919c2-199">organizationRegistrationNumber</span></span> | <span data-ttu-id="919c2-200">string</span><span class="sxs-lookup"><span data-stu-id="919c2-200">string</span></span> | <span data-ttu-id="919c2-201">Depende da condição</span><span class="sxs-lookup"><span data-stu-id="919c2-201">Depends on condition</span></span> | <span data-ttu-id="919c2-202">Número de registo da organização do cliente (também referido como número INN em determinados países).</span><span class="sxs-lookup"><span data-stu-id="919c2-202">The customer’s organization registration number (also referred to as the INN number in certain countries).</span></span> <br/><br/><span data-ttu-id="919c2-203">A conclusão deste campo só é necessária se a empresa/organização de um cliente estiver localizada nos seguintes países:</span><span class="sxs-lookup"><span data-stu-id="919c2-203">Completing this field is required only if a customer’s company/organization is located in the following countries:</span></span> <br/><br/><span data-ttu-id="919c2-204">- Arménia (AM)</span><span class="sxs-lookup"><span data-stu-id="919c2-204">- Armenia (AM)</span></span> <br/><span data-ttu-id="919c2-205">- Azerbaijão (AZ)</span><span class="sxs-lookup"><span data-stu-id="919c2-205">- Azerbaijan (AZ)</span></span><br/><span data-ttu-id="919c2-206">- Bielorrússia (BY)</span><span class="sxs-lookup"><span data-stu-id="919c2-206">- Belarus (BY)</span></span><br/><span data-ttu-id="919c2-207">- Hungria (HU)</span><span class="sxs-lookup"><span data-stu-id="919c2-207">- Hungary (HU)</span></span><br/><span data-ttu-id="919c2-208">- Cazaquistão (KZ)</span><span class="sxs-lookup"><span data-stu-id="919c2-208">- Kazakhstan (KZ)</span></span><br/><span data-ttu-id="919c2-209">- Quirguistão (KG)</span><span class="sxs-lookup"><span data-stu-id="919c2-209">- Kyrgyzstan (KG)</span></span><br/><span data-ttu-id="919c2-210">- Moldávia (MD)</span><span class="sxs-lookup"><span data-stu-id="919c2-210">- Moldova (MD)</span></span><br/><span data-ttu-id="919c2-211">- Rússia (RU)</span><span class="sxs-lookup"><span data-stu-id="919c2-211">- Russia (RU)</span></span><br/><span data-ttu-id="919c2-212">- Tajiquistão (TJ)</span><span class="sxs-lookup"><span data-stu-id="919c2-212">- Tajikistan (TJ)</span></span><br/><span data-ttu-id="919c2-213">- Uzbequistão (UZ)</span><span class="sxs-lookup"><span data-stu-id="919c2-213">- Uzbekistan (UZ)</span></span><br/><span data-ttu-id="919c2-214">- Ucrânia (UA)</span><span class="sxs-lookup"><span data-stu-id="919c2-214">- Ukraine (UA)</span></span><br/><br/><span data-ttu-id="919c2-215">Este campo não é necessário se a empresa/organização do cliente estiver localizada noutros países para além dos mostrados aqui.</span><span class="sxs-lookup"><span data-stu-id="919c2-215">This field is not required if the customer’s company/organization is located in other countries beyond those shown here.</span></span>  |

### <a name="request-example"></a><span data-ttu-id="919c2-216">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="919c2-216">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: d628adbe-b7ee-412e-ac55-58f22b4ba2f4
MS-CorrelationId: 0dd197a8-992c-44ca-aeae-21cd83494dce
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 823
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": null,
    "CommerceId": null,
    "CompanyProfile": {
        "TenantId": null,
        "Domain": "WingtipToys678152504.onmicrosoft.com",
        "CompanyName": null,
        "Attributes": {
            "ObjectType": "CustomerCompanyProfile"
        }
    },
    "BillingProfile": {
        "Id": null,
        "FirstName": null,
        "LastName": null,
        "Email": "Gena@wingtiptoys.com",
        "Culture": "EN-US",
        "Language": "En",
        "CompanyName": "Wingtip Toys678152504",
        "DefaultAddress": {
            "Country": "US",
            "Region": null,
            "City": "Redmond",
            "State": "WA",
            "AddressLine1": "One Microsoft Way",
            "AddressLine2": null,
            "PostalCode": "98052",
            "FirstName": "Gena",
            "LastName": "Soto",
            "PhoneNumber": "4255550101"
        },
        "Attributes": {
            "ObjectType": "CustomerBillingProfile"
        }
    },
    "RelationshipToPartner": "none",
    "AllowDelegatedAccess": null,
    "UserCredentials": null,
    "CustomDomains": null,
    "AssociatedPartnerId": "484e548c-f5f3-4528-93a9-c16c6373cb59",
    "Attributes": {
        "ObjectType": "Customer"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="919c2-217">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="919c2-217">REST response</span></span>

<span data-ttu-id="919c2-218">Se for bem sucedida, a resposta contém um recurso [do Cliente](customer-resources.md#customer) para o novo cliente.</span><span class="sxs-lookup"><span data-stu-id="919c2-218">If successful, the response contains a [Customer](customer-resources.md#customer) resource for the new customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="919c2-219">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="919c2-219">Response success and error codes</span></span>

<span data-ttu-id="919c2-220">As respostas vêm com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="919c2-220">Responses come with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="919c2-221">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="919c2-221">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="919c2-222">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="919c2-222">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="919c2-223">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="919c2-223">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 1085
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0dd197a8-992c-44ca-aeae-21cd83494dce
MS-RequestId: d628adbe-b7ee-412e-ac55-58f22b4ba2f4
MS-CV: Yy/YaA0gYEmfQyR/.0
MS-ServerId: 030020525
Date: Tue, 06 Jun 2017 23:11:40 GMT

{
    "id": "626099fe-17af-4756-9fd0-6a73b7127859",
    "commerceId": "626099fe-17af-4756-9fd0-6a73b7127859",
    "companyProfile": {
        "tenantId": "626099fe-17af-4756-9fd0-6a73b7127859",
        "domain": "WingtipToys678152504.onmicrosoft.com",
        "companyName": "Wingtip Toys678152504",
        "links": {
            "self": {
                "uri": "/customers/626099fe-17af-4756-9fd0-6a73b7127859/profiles/company",
                "method": "GET",
                "headers": []
            }
        },
        "attributes": {
            "objectType": "CustomerCompanyProfile"
        }
    },
    "billingProfile": {
        "id": "7079246e-7b62-56ef-7cbd-a819514b54b5",
        "email": "Gena@wingtiptoys.com",
        "culture": "en-US",
        "language": "En",
        "companyName": "Wingtip Toys678152504",
        "defaultAddress": {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "One Microsoft Way",
            "postalCode": "98052",
            "firstName": "Gena",
            "lastName": "Soto",
            "phoneNumber": "4255550101"
        },
        "attributes": {
            "etag": "-8799889149591823008",
            "objectType": "CustomerBillingProfile"
        }
    },
    "relationshipToPartner": "reseller",
    "allowDelegatedAccess": true,
    "userCredentials": {
        "userName": "admin",
        "password": "0Krha*Io"
    },
    "associatedPartnerId": "484e548c-f5f3-4528-93a9-c16c6373cb59",
    "attributes": {
        "objectType": "Customer"
    }
}
```