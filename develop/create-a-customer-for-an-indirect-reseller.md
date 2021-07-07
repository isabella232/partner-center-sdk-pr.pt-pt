---
title: Criar um cliente para um revendedor indireto
description: Saiba como um fornecedor indireto pode usar APIs do Partner Center para criar um cliente para um revendedor indireto.
ms.date: 04/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 9a6218aeb61f3775c89d34b4d57a17741e3a1e93
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973745"
---
# <a name="create-a-customer-for-an-indirect-reseller-using-partner-center-apis"></a><span data-ttu-id="ac647-103">Crie um cliente para um revendedor indireto usando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="ac647-103">Create a customer for an indirect reseller using Partner Center APIs</span></span>

<span data-ttu-id="ac647-104">Um fornecedor indireto pode criar um cliente para um revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="ac647-104">An indirect provider can create a customer for an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ac647-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ac647-105">Prerequisites</span></span>

- <span data-ttu-id="ac647-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ac647-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ac647-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="ac647-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="ac647-108">O identificador do inquilino do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="ac647-108">The tenant identifier of the indirect reseller.</span></span>

- <span data-ttu-id="ac647-109">O revendedor indireto deve ter uma parceria com o fornecedor indireto.</span><span class="sxs-lookup"><span data-stu-id="ac647-109">The indirect reseller must have a partnership with the indirect provider.</span></span>

## <a name="c"></a><span data-ttu-id="ac647-110">C\#</span><span class="sxs-lookup"><span data-stu-id="ac647-110">C\#</span></span>

<span data-ttu-id="ac647-111">Para adicionar um novo cliente para um revendedor indireto:</span><span class="sxs-lookup"><span data-stu-id="ac647-111">To add a new customer for an indirect reseller:</span></span>

1. <span data-ttu-id="ac647-112">Instantaneamente um novo objeto [**de Cliente**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) e, em seguida, instantaneamente e povoar o [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) e [**o CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span><span class="sxs-lookup"><span data-stu-id="ac647-112">Instantiate a new [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object and then instantiate and populate the [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) and [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span></span> <span data-ttu-id="ac647-113">Certifique-se de atribuir o ID do revendedor indireto à propriedade [**AssociatedPartnerID.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid)</span><span class="sxs-lookup"><span data-stu-id="ac647-113">Be sure to assign the indirect reseller ID to the [**AssociatedPartnerID**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid) property.</span></span>

2. <span data-ttu-id="ac647-114">Utilize a propriedade [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para obter uma interface para as operações de recolha de clientes.</span><span class="sxs-lookup"><span data-stu-id="ac647-114">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) property to get an interface to customer collection operations.</span></span>

3. <span data-ttu-id="ac647-115">Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) ou [**Criar Aync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) para criar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ac647-115">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) method to create the customer.</span></span>

### <a name="c-example"></a><span data-ttu-id="ac647-116">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="ac647-116">C\# example</span></span>

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

<span data-ttu-id="ac647-117">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="ac647-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="ac647-118">**Project**: Partner Center SDK Samples **Class**: CreateCustomerforIndirectReseller.cs</span><span class="sxs-lookup"><span data-stu-id="ac647-118">**Project**: Partner Center SDK Samples **Class**: CreateCustomerforIndirectReseller.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="ac647-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="ac647-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ac647-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac647-120">Request syntax</span></span>

| <span data-ttu-id="ac647-121">Método</span><span class="sxs-lookup"><span data-stu-id="ac647-121">Method</span></span>   | <span data-ttu-id="ac647-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="ac647-122">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="ac647-123">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="ac647-123">**POST**</span></span> | <span data-ttu-id="ac647-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ac647-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ac647-125">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="ac647-125">Request headers</span></span>

<span data-ttu-id="ac647-126">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ac647-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ac647-127">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="ac647-127">Request body</span></span>

<span data-ttu-id="ac647-128">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="ac647-128">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="ac647-129">Nome</span><span class="sxs-lookup"><span data-stu-id="ac647-129">Name</span></span>                                          | <span data-ttu-id="ac647-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="ac647-130">Type</span></span>   | <span data-ttu-id="ac647-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="ac647-131">Required</span></span> | <span data-ttu-id="ac647-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac647-132">Description</span></span>                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<span data-ttu-id="ac647-133">BillingProfile</span><span class="sxs-lookup"><span data-stu-id="ac647-133">BillingProfile</span></span>](#billing-profile)             | <span data-ttu-id="ac647-134">objeto</span><span class="sxs-lookup"><span data-stu-id="ac647-134">object</span></span> | <span data-ttu-id="ac647-135">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-135">Yes</span></span>      | <span data-ttu-id="ac647-136">A informação do perfil de faturação do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac647-136">The customer's billing profile information.</span></span>                                                                                                                                                                                                                                                                                                           |
| [<span data-ttu-id="ac647-137">EmpresaProfile</span><span class="sxs-lookup"><span data-stu-id="ac647-137">CompanyProfile</span></span>](#company-profile)             | <span data-ttu-id="ac647-138">objeto</span><span class="sxs-lookup"><span data-stu-id="ac647-138">object</span></span> | <span data-ttu-id="ac647-139">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-139">Yes</span></span>      | <span data-ttu-id="ac647-140">Informação do perfil da empresa do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac647-140">The customer's company profile information.</span></span>                                                               
| [<span data-ttu-id="ac647-141">PartnerId Associado</span><span class="sxs-lookup"><span data-stu-id="ac647-141">AssociatedPartnerId</span></span>](customer-resources.md#customer) | <span data-ttu-id="ac647-142">string</span><span class="sxs-lookup"><span data-stu-id="ac647-142">string</span></span> | <span data-ttu-id="ac647-143">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-143">Yes</span></span>      | <span data-ttu-id="ac647-144">O iD do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="ac647-144">The indirect reseller ID.</span></span> <span data-ttu-id="ac647-145">O revendedor indireto, tal como indicado pelo ID aqui fornecido, deve ter uma parceria com o fornecedor indireto ou o pedido falhará.</span><span class="sxs-lookup"><span data-stu-id="ac647-145">The indirect reseller as indicated by the ID supplied here must have a partnership with the indirect provider or the request will fail.</span></span> <span data-ttu-id="ac647-146">Note também que se o valor AssociatedPartnerId não for fornecido, o cliente é criado como cliente direto do fornecedor indireto e não como revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="ac647-146">Also note that if the AssociatedPartnerId value isn't supplied, the customer is created as a direct customer of the indirect provider rather than the indirect reseller.</span></span> |
|<span data-ttu-id="ac647-147">Domínio</span><span class="sxs-lookup"><span data-stu-id="ac647-147">Domain</span></span>| <span data-ttu-id="ac647-148">String</span><span class="sxs-lookup"><span data-stu-id="ac647-148">String</span></span>| <span data-ttu-id="ac647-149">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-149">Yes</span></span>|<span data-ttu-id="ac647-150">O nome de domínio do cliente, como contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="ac647-150">The customer's domain name, such as contoso.onmicrosoft.com.</span></span>|
|<span data-ttu-id="ac647-151">organizaçãoRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="ac647-151">organizationRegistrationNumber</span></span>|    <span data-ttu-id="ac647-152">string</span><span class="sxs-lookup"><span data-stu-id="ac647-152">string</span></span>|<span data-ttu-id="ac647-153">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-153">Yes</span></span>|     <span data-ttu-id="ac647-154">Número de registo da organização do cliente (também referido como número INN em determinados países).</span><span class="sxs-lookup"><span data-stu-id="ac647-154">The customer’s organization registration number (also referred to as INN number in certain countries).</span></span> <span data-ttu-id="ac647-155">Apenas necessário para a empresa/organização do cliente localizada nos seguintes países: Arménia(AM), Azerbaijão(AZ), Bielorrússia(BY), Hungria (HU), Cazaquistão(KZ), Quirguistão(KG), Moldávia (MD), Rússia(RU), Tajiquistão(TJ), Uz, Ucrânia(UA), Índia, Brasil, África do Sul, Polónia, Emirados Árabes Unidos, Arábia Saudita, Arábia Saudita,</span><span class="sxs-lookup"><span data-stu-id="ac647-155">Only required for customer’s company/organization located in the following countries: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA), India, Brazil, South Africa, Poland, United Arab Emirates, Saudi Arabia, Turkey, Thailand, Vietnam, Myanmar, Iraq, South Sudan, and Venezuela.</span></span> <span data-ttu-id="ac647-156">Para a empresa/organização do cliente localizada noutros países este é um campo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac647-156">For customer’s company/organization located in other countries this is an optional field.</span></span>|



#### <a name="billing-profile"></a><span data-ttu-id="ac647-157">Perfil de faturação</span><span class="sxs-lookup"><span data-stu-id="ac647-157">Billing profile</span></span>

<span data-ttu-id="ac647-158">Esta tabela descreve os campos mínimos exigidos do recurso [CustomerBillingProfile](customer-resources.md#customerbillingprofile) necessário para criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="ac647-158">This table describes the minimum required fields from the [CustomerBillingProfile](customer-resources.md#customerbillingprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="ac647-159">Nome</span><span class="sxs-lookup"><span data-stu-id="ac647-159">Name</span></span>             | <span data-ttu-id="ac647-160">Tipo</span><span class="sxs-lookup"><span data-stu-id="ac647-160">Type</span></span>                                     | <span data-ttu-id="ac647-161">Necessário</span><span class="sxs-lookup"><span data-stu-id="ac647-161">Required</span></span> | <span data-ttu-id="ac647-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac647-162">Description</span></span>                                                                                                                                                                                                     |
|------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ac647-163">e-mail</span><span class="sxs-lookup"><span data-stu-id="ac647-163">email</span></span>            | <span data-ttu-id="ac647-164">string</span><span class="sxs-lookup"><span data-stu-id="ac647-164">string</span></span>                                   | <span data-ttu-id="ac647-165">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-165">Yes</span></span>      | <span data-ttu-id="ac647-166">O endereço de e-mail do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac647-166">The customer's email address.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="ac647-167">cultura</span><span class="sxs-lookup"><span data-stu-id="ac647-167">culture</span></span>          | <span data-ttu-id="ac647-168">string</span><span class="sxs-lookup"><span data-stu-id="ac647-168">string</span></span>                                   | <span data-ttu-id="ac647-169">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-169">Yes</span></span>      | <span data-ttu-id="ac647-170">A sua cultura preferida para a comunicação e a moeda, como "en-US".</span><span class="sxs-lookup"><span data-stu-id="ac647-170">Their preferred culture for communication and currency, such as "en-US".</span></span> <span data-ttu-id="ac647-171">Consulte [o Partner Center com línguas e locais apoiados](partner-center-supported-languages-and-locales.md) para as culturas apoiadas.</span><span class="sxs-lookup"><span data-stu-id="ac647-171">See [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md) for the supported cultures.</span></span> |
| <span data-ttu-id="ac647-172">language</span><span class="sxs-lookup"><span data-stu-id="ac647-172">language</span></span>         | <span data-ttu-id="ac647-173">string</span><span class="sxs-lookup"><span data-stu-id="ac647-173">string</span></span>                                   | <span data-ttu-id="ac647-174">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-174">Yes</span></span>      | <span data-ttu-id="ac647-175">A linguagem padrão.</span><span class="sxs-lookup"><span data-stu-id="ac647-175">The default language.</span></span> <span data-ttu-id="ac647-176">Dois códigos linguísticos de caracteres (por exemplo `en` `fr` ou) são suportados.</span><span class="sxs-lookup"><span data-stu-id="ac647-176">Two character language codes (for example `en` or `fr`) are supported.</span></span>                                                                                                                                |
| <span data-ttu-id="ac647-177">nome da empresa \_</span><span class="sxs-lookup"><span data-stu-id="ac647-177">company\_name</span></span>    | <span data-ttu-id="ac647-178">string</span><span class="sxs-lookup"><span data-stu-id="ac647-178">string</span></span>                                   | <span data-ttu-id="ac647-179">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-179">Yes</span></span>      | <span data-ttu-id="ac647-180">O nome de empresa/organização registado.</span><span class="sxs-lookup"><span data-stu-id="ac647-180">The registered company/organization name.</span></span>                                                                                                                                                                       |
| <span data-ttu-id="ac647-181">endereço padrão \_</span><span class="sxs-lookup"><span data-stu-id="ac647-181">default\_address</span></span> | [<span data-ttu-id="ac647-182">Endereço</span><span class="sxs-lookup"><span data-stu-id="ac647-182">Address</span></span>](utility-resources.md#address) | <span data-ttu-id="ac647-183">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-183">Yes</span></span>      | <span data-ttu-id="ac647-184">O endereço registado da empresa/organização do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac647-184">The registered address of the customer's company/organization.</span></span> <span data-ttu-id="ac647-185">Consulte o recurso [Address](utility-resources.md#address) para obter informações sobre eventuais limitações de comprimento.</span><span class="sxs-lookup"><span data-stu-id="ac647-185">See the [Address](utility-resources.md#address) resource for information on any length limitations.</span></span>                                             |

#### <a name="company-profile"></a><span data-ttu-id="ac647-186">Perfil da empresa</span><span class="sxs-lookup"><span data-stu-id="ac647-186">Company profile</span></span>

<span data-ttu-id="ac647-187">Esta tabela descreve os campos mínimos exigidos do recurso [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) necessário para criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="ac647-187">This table describes the minimum required fields from the [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="ac647-188">Nome</span><span class="sxs-lookup"><span data-stu-id="ac647-188">Name</span></span>   | <span data-ttu-id="ac647-189">Tipo</span><span class="sxs-lookup"><span data-stu-id="ac647-189">Type</span></span>   | <span data-ttu-id="ac647-190">Necessário</span><span class="sxs-lookup"><span data-stu-id="ac647-190">Required</span></span> | <span data-ttu-id="ac647-191">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac647-191">Description</span></span>                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| <span data-ttu-id="ac647-192">domínio</span><span class="sxs-lookup"><span data-stu-id="ac647-192">domain</span></span> | <span data-ttu-id="ac647-193">string</span><span class="sxs-lookup"><span data-stu-id="ac647-193">string</span></span> | <span data-ttu-id="ac647-194">Yes</span><span class="sxs-lookup"><span data-stu-id="ac647-194">Yes</span></span>     | <span data-ttu-id="ac647-195">O nome de domínio do cliente, como contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="ac647-195">The customer's domain name, such as contoso.onmicrosoft.com.</span></span> |
| <span data-ttu-id="ac647-196">organizaçãoRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="ac647-196">organizationRegistrationNumber</span></span> | <span data-ttu-id="ac647-197">string</span><span class="sxs-lookup"><span data-stu-id="ac647-197">string</span></span> | <span data-ttu-id="ac647-198">Depende da condição</span><span class="sxs-lookup"><span data-stu-id="ac647-198">Depends on condition</span></span> | <span data-ttu-id="ac647-199">Número de registo da organização do cliente (também referido como número INN em determinados países).</span><span class="sxs-lookup"><span data-stu-id="ac647-199">The customer’s organization registration number (also referred to as the INN number in certain countries).</span></span> <br/><br/><span data-ttu-id="ac647-200">A conclusão deste campo só é necessária se a empresa/organização de um cliente estiver localizada nos seguintes países:</span><span class="sxs-lookup"><span data-stu-id="ac647-200">Completing this field is required only if a customer’s company/organization is located in the following countries:</span></span> <br/><br/><span data-ttu-id="ac647-201">- Arménia (AM)</span><span class="sxs-lookup"><span data-stu-id="ac647-201">- Armenia (AM)</span></span> <br/><span data-ttu-id="ac647-202">- Azerbaijão (AZ)</span><span class="sxs-lookup"><span data-stu-id="ac647-202">- Azerbaijan (AZ)</span></span><br/><span data-ttu-id="ac647-203">- Bielorrússia (BY)</span><span class="sxs-lookup"><span data-stu-id="ac647-203">- Belarus (BY)</span></span><br/><span data-ttu-id="ac647-204">- Hungria (HU)</span><span class="sxs-lookup"><span data-stu-id="ac647-204">- Hungary (HU)</span></span><br/><span data-ttu-id="ac647-205">- Cazaquistão (KZ)</span><span class="sxs-lookup"><span data-stu-id="ac647-205">- Kazakhstan (KZ)</span></span><br/><span data-ttu-id="ac647-206">- Quirguistão (KG)</span><span class="sxs-lookup"><span data-stu-id="ac647-206">- Kyrgyzstan (KG)</span></span><br/><span data-ttu-id="ac647-207">- Moldávia (MD)</span><span class="sxs-lookup"><span data-stu-id="ac647-207">- Moldova (MD)</span></span><br/><span data-ttu-id="ac647-208">- Rússia (RU)</span><span class="sxs-lookup"><span data-stu-id="ac647-208">- Russia (RU)</span></span><br/><span data-ttu-id="ac647-209">- Tajiquistão (TJ)</span><span class="sxs-lookup"><span data-stu-id="ac647-209">- Tajikistan (TJ)</span></span><br/><span data-ttu-id="ac647-210">- Uzbequistão (UZ)</span><span class="sxs-lookup"><span data-stu-id="ac647-210">- Uzbekistan (UZ)</span></span><br/><span data-ttu-id="ac647-211">- Ucrânia (UA)</span><span class="sxs-lookup"><span data-stu-id="ac647-211">- Ukraine (UA)</span></span><br/><span data-ttu-id="ac647-212">- Índia</span><span class="sxs-lookup"><span data-stu-id="ac647-212">- India</span></span> <br/><span data-ttu-id="ac647-213">- Brasil</span><span class="sxs-lookup"><span data-stu-id="ac647-213">- Brazil</span></span> <br/><span data-ttu-id="ac647-214">- África do Sul</span><span class="sxs-lookup"><span data-stu-id="ac647-214">- South Africa</span></span> <br/><span data-ttu-id="ac647-215">- Polónia</span><span class="sxs-lookup"><span data-stu-id="ac647-215">- Poland</span></span> <br/><span data-ttu-id="ac647-216">- Emirados Árabes Unidos</span><span class="sxs-lookup"><span data-stu-id="ac647-216">- United Arab Emirates</span></span> <br/><span data-ttu-id="ac647-217">- Arábia Saudita</span><span class="sxs-lookup"><span data-stu-id="ac647-217">- Saudi Arabia</span></span> <br/><span data-ttu-id="ac647-218">- Turquia</span><span class="sxs-lookup"><span data-stu-id="ac647-218">- Turkey</span></span> <br/><span data-ttu-id="ac647-219">- Tailândia</span><span class="sxs-lookup"><span data-stu-id="ac647-219">- Thailand</span></span> <br/><span data-ttu-id="ac647-220">- Vietname</span><span class="sxs-lookup"><span data-stu-id="ac647-220">- Vietnam</span></span> <br/><span data-ttu-id="ac647-221">- Myanmar</span><span class="sxs-lookup"><span data-stu-id="ac647-221">- Myanmar</span></span> <br/><span data-ttu-id="ac647-222">- Iraque</span><span class="sxs-lookup"><span data-stu-id="ac647-222">- Iraq</span></span> <br/><span data-ttu-id="ac647-223">- Sudão do Sul</span><span class="sxs-lookup"><span data-stu-id="ac647-223">- South Sudan</span></span> <br/><span data-ttu-id="ac647-224">- Venezuela</span><span class="sxs-lookup"><span data-stu-id="ac647-224">- Venezuela</span></span><br/> <br/><span data-ttu-id="ac647-225">Para a empresa/organização do cliente localizada noutros países, este é um campo opcional.</span><span class="sxs-lookup"><span data-stu-id="ac647-225">For customer’s company/organization located in other countries, this is an optional field.</span></span>  |

### <a name="request-example"></a><span data-ttu-id="ac647-226">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="ac647-226">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="ac647-227">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="ac647-227">REST response</span></span>

<span data-ttu-id="ac647-228">Se for bem sucedida, a resposta contém um recurso [do Cliente](customer-resources.md#customer) para o novo cliente.</span><span class="sxs-lookup"><span data-stu-id="ac647-228">If successful, the response contains a [Customer](customer-resources.md#customer) resource for the new customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ac647-229">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="ac647-229">Response success and error codes</span></span>

<span data-ttu-id="ac647-230">As respostas vêm com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="ac647-230">Responses come with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ac647-231">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="ac647-231">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ac647-232">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="ac647-232">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ac647-233">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="ac647-233">Response example</span></span>

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