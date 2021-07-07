---
title: Criar um cliente
description: Saiba como um parceiro Fornecedor de Soluções em Nuvem (CSP) pode usar APIs do Partner Center para criar um novo cliente. O artigo descreve os pré-requisitos e o que mais acontece.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 6232ca77d057f2f5168b73d81ec551669d540246
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973728"
---
# <a name="create-a-customer-using-partner-center-apis"></a><span data-ttu-id="c02fc-104">Criar um cliente usando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="c02fc-104">Create a customer using Partner Center APIs</span></span>

<span data-ttu-id="c02fc-105">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c02fc-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c02fc-106">Este artigo explica como criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-106">This article explains how to create a new customer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c02fc-107">Se é um fornecedor indireto e pretende criar um cliente para um revendedor indireto, consulte [criar um cliente para um revendedor indireto.](create-a-customer-for-an-indirect-reseller.md)</span><span class="sxs-lookup"><span data-stu-id="c02fc-107">If you are an indirect provider and you want to create a customer for an indirect reseller, please see [Create a customer for an indirect reseller](create-a-customer-for-an-indirect-reseller.md).</span></span>

<span data-ttu-id="c02fc-108">Como parceiro de fornecedor de soluções em nuvem (CSP), quando criar um cliente pode fazer encomendas em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-108">As a cloud solution provider (CSP) partner, when you create a customer you can place orders on behalf of the customer.</span></span> <span data-ttu-id="c02fc-109">Quando cria um cliente, também cria:</span><span class="sxs-lookup"><span data-stu-id="c02fc-109">When you create a customer, you also create:</span></span>

- <span data-ttu-id="c02fc-110">Um objeto de inquilino Azure Ative Directory (AD) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-110">An Azure Active Directory (AD) tenant object for the customer.</span></span>

- <span data-ttu-id="c02fc-111">Uma relação entre o revendedor e o cliente, usada para privilégios administrativos delegados.</span><span class="sxs-lookup"><span data-stu-id="c02fc-111">A relationship between the reseller and customer, used for delegated admin privileges.</span></span>

- <span data-ttu-id="c02fc-112">Um nome de utilizador e senha para iniciar sinscrônico para o cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-112">A user name and password to sign in as an admin for the customer.</span></span>

<span data-ttu-id="c02fc-113">Uma vez criado o cliente, certifique-se de guardar os detalhes de ID e AD do cliente para utilização futura com o Partner Center SDK (por exemplo, gestão de conta).</span><span class="sxs-lookup"><span data-stu-id="c02fc-113">Once the customer is created, be sure to save the customer ID and Azure AD details for future use with the Partner Center SDK (for example, account management).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c02fc-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c02fc-114">Prerequisites</span></span>

- <span data-ttu-id="c02fc-115">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c02fc-115">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c02fc-116">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="c02fc-116">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c02fc-117">Para criar um inquilino do cliente deve fornecer um endereço físico válido durante o processo de criação.</span><span class="sxs-lookup"><span data-stu-id="c02fc-117">To create a customer tenant you must provide a valid physical address during the creation process.</span></span> <span data-ttu-id="c02fc-118">Um endereço pode ser validado seguindo os passos descritos no cenário [de validação de um endereço.](validate-an-address.md)</span><span class="sxs-lookup"><span data-stu-id="c02fc-118">An address can be validated by following the steps outlined in the [Validate an address](validate-an-address.md) scenario.</span></span> <span data-ttu-id="c02fc-119">Se criar um cliente usando um endereço inválido no ambiente da caixa de areia, não poderá eliminar esse cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-119">If you create a customer using an invalid address in the sandbox environment, you will not be able to delete that customer tenant.</span></span>

## <a name="c"></a><span data-ttu-id="c02fc-120">C\#</span><span class="sxs-lookup"><span data-stu-id="c02fc-120">C\#</span></span>

<span data-ttu-id="c02fc-121">Para adicionar um cliente:</span><span class="sxs-lookup"><span data-stu-id="c02fc-121">To add a customer:</span></span>

1. <span data-ttu-id="c02fc-122">Instantaneamente um novo objeto [**cliente.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer)</span><span class="sxs-lookup"><span data-stu-id="c02fc-122">Instantiate a new [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object.</span></span> <span data-ttu-id="c02fc-123">Certifique-se de preencher o [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) e [**o CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span><span class="sxs-lookup"><span data-stu-id="c02fc-123">Be sure to fill in the [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) and [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span></span>

2. <span data-ttu-id="c02fc-124">Adicione o novo cliente à sua coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) chamando [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) ou [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync).</span><span class="sxs-lookup"><span data-stu-id="c02fc-124">Add the new customer to your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection by calling [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync).</span></span>

### <a name="c-example"></a><span data-ttu-id="c02fc-125">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="c02fc-125">C\# example</span></span>

```csharp
// IAggregatePartner partnerOperations;

var partnerOperations = this.Context.UserPartnerOperations;

var customerToCreate = new Customer()
{
    CompanyProfile = new CustomerCompanyProfile()
    {
        Domain = string.Format(CultureInfo.InvariantCulture,
            "SampleApplication{0}.{1}",
            new Random().Next(),
            this.Context.Configuration.Scenario.CustomerDomainSuffix),
        //// OrganizationRegistrationNumber = "123456" // Please add if in specific country that requires
    },
    BillingProfile = new CustomerBillingProfile()
    {
        Culture = "EN-US",
        Email = "someone@example.com",
        Language = "En",
        CompanyName = "Some Company" + new Random().Next(),
        DefaultAddress = new Address()
        {
            FirstName = "Tania",
            MiddleName = "MiddleName",
            LastName = "Carr",
            AddressLine1 = "One Microsoft Way",
            City = "Redmond",
            State = "WA",
            Country = "US",
            PostalCode = "98052",
            PhoneNumber = ""
        }
    }
};

var newCustomer = partnerOperations.Customers.Create(customerToCreate);
```

<span data-ttu-id="c02fc-126">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="c02fc-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="c02fc-127">**Project**: Partner Center SDK Samples **Class**: CreateCustomer.cs</span><span class="sxs-lookup"><span data-stu-id="c02fc-127">**Project**: Partner Center SDK Samples **Class**: CreateCustomer.cs</span></span>

## <a name="java"></a><span data-ttu-id="c02fc-128">Java</span><span class="sxs-lookup"><span data-stu-id="c02fc-128">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="c02fc-129">Para criar um novo cliente:</span><span class="sxs-lookup"><span data-stu-id="c02fc-129">To create a new customer:</span></span>

1. <span data-ttu-id="c02fc-130">Crie uma nova instância do **CustomerBillingProfile** e dos objetos **CustomerCompanyProfile.**</span><span class="sxs-lookup"><span data-stu-id="c02fc-130">Create a new instance of the **CustomerBillingProfile** and the **CustomerCompanyProfile** objects.</span></span> <span data-ttu-id="c02fc-131">Certifique-se de povoar os campos necessários.</span><span class="sxs-lookup"><span data-stu-id="c02fc-131">Be sure to populate the required fields.</span></span>

2. <span data-ttu-id="c02fc-132">Crie o cliente chamando o **IAggregatePartner.getCustomers().criar** função.</span><span class="sxs-lookup"><span data-stu-id="c02fc-132">Create the customer by calling the **IAggregatePartner.getCustomers().create** function.</span></span>

### <a name="java-example"></a><span data-ttu-id="c02fc-133">Exemplo de Java</span><span class="sxs-lookup"><span data-stu-id="c02fc-133">Java example</span></span>

```java
// IAggregatePartner partnerOperations;

Address address = new Address();

address.setFirstName( "Gena" );
address.setLastName( "Soto" );
address.setAddressLine1( "One Microsoft Way" );
address.setCity( "Redmond" );
address.setState( "WA" );
address.setCountry( "US" );
address.setPostalCode( "98052" );
address.setPhoneNumber( "4255550101" );

CustomerBillingProfile billingProfile = new CustomerBillingProfile();

billingProfile.setCulture( "en-US" );
billingProfile.setEmail( "gena@wingtiptoys.com" );
billingProfile.setLanguage( "en" );
billingProfile.setCompanyName( "Wingtip Toys" + new Random().nextInt() );
billingProfile.setDefaultAddress( address );

CustomerCompanyProfile companyProfile = new CustomerCompanyProfile();

companyProfile.setDomain( "WingtipToys" + Math.abs( new Random().nextInt() ) + ".onmicrosoft.com" );

Customer customerToCreate = new Customer();

customerToCreate.setBillingProfile( billingProfile );
customerToCreate.setCompanyProfile( companyProfile );

Customer newCustomer = partnerOperations.getCustomers().create( customerToCreate );
```

## <a name="powershell"></a><span data-ttu-id="c02fc-134">PowerShell</span><span class="sxs-lookup"><span data-stu-id="c02fc-134">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="c02fc-135">Para criar um cliente, execute o comando [**New-PartnerCustomer.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md)</span><span class="sxs-lookup"><span data-stu-id="c02fc-135">To create a customer, execute the [**New-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md) command.</span></span>

```powershell
New-PartnerCustomer -BillingAddressLine1 '1 Microsoft Way' -BillingAddressCity 'Redmond' -BillingAddressCountry 'US' -BillingAddressPostalCode '98052' -BillingAddressState 'WA' -ContactEmail 'jdoe@customer.com' -ContactFirstName 'Jane' -ContactLastName 'Doe' -Culture 'en-US' -Domain 'newcustomer.onmicrosoft.com' -Language 'en' -Name 'New Customer'
```

## <a name="rest-request"></a><span data-ttu-id="c02fc-136">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c02fc-136">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c02fc-137">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c02fc-137">Request syntax</span></span>

| <span data-ttu-id="c02fc-138">Método</span><span class="sxs-lookup"><span data-stu-id="c02fc-138">Method</span></span>   | <span data-ttu-id="c02fc-139">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c02fc-139">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="c02fc-140">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="c02fc-140">**POST**</span></span> | <span data-ttu-id="c02fc-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c02fc-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c02fc-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c02fc-142">Request headers</span></span>

- <span data-ttu-id="c02fc-143">Esta API é idempotente (não produzirá um resultado diferente se lhe chamar várias vezes).</span><span class="sxs-lookup"><span data-stu-id="c02fc-143">This API is idempotent (it will not yield a different result if you call it multiple times).</span></span>

- <span data-ttu-id="c02fc-144">É necessária uma identificação de pedido e uma identificação de correlação.</span><span class="sxs-lookup"><span data-stu-id="c02fc-144">A request ID and correlation ID are required.</span></span>

- <span data-ttu-id="c02fc-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c02fc-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c02fc-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="c02fc-146">Request body</span></span>

<span data-ttu-id="c02fc-147">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="c02fc-147">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="c02fc-148">Nome</span><span class="sxs-lookup"><span data-stu-id="c02fc-148">Name</span></span>                              | <span data-ttu-id="c02fc-149">Tipo</span><span class="sxs-lookup"><span data-stu-id="c02fc-149">Type</span></span>   | <span data-ttu-id="c02fc-150">Description</span><span class="sxs-lookup"><span data-stu-id="c02fc-150">Description</span></span>                                 |
|-----------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="c02fc-151">BillingProfile</span><span class="sxs-lookup"><span data-stu-id="c02fc-151">BillingProfile</span></span>](#billing-profile) | <span data-ttu-id="c02fc-152">objeto</span><span class="sxs-lookup"><span data-stu-id="c02fc-152">object</span></span> | <span data-ttu-id="c02fc-153">A informação do perfil de faturação do cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-153">The customer's billing profile information.</span></span> |
| [<span data-ttu-id="c02fc-154">EmpresaProfile</span><span class="sxs-lookup"><span data-stu-id="c02fc-154">CompanyProfile</span></span>](#company-profile) | <span data-ttu-id="c02fc-155">objeto</span><span class="sxs-lookup"><span data-stu-id="c02fc-155">object</span></span> | <span data-ttu-id="c02fc-156">Informação do perfil da empresa do cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-156">The customer's company profile information.</span></span> |

#### <a name="billing-profile"></a><span data-ttu-id="c02fc-157">Perfil de faturação</span><span class="sxs-lookup"><span data-stu-id="c02fc-157">Billing profile</span></span>

<span data-ttu-id="c02fc-158">Esta tabela descreve os campos mínimos exigidos do recurso [CustomerBillingProfile](customer-resources.md#customerbillingprofile) necessário para criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-158">This table describes the minimum required fields from the [CustomerBillingProfile](customer-resources.md#customerbillingprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="c02fc-159">Nome</span><span class="sxs-lookup"><span data-stu-id="c02fc-159">Name</span></span>             | <span data-ttu-id="c02fc-160">Tipo</span><span class="sxs-lookup"><span data-stu-id="c02fc-160">Type</span></span>                                     | <span data-ttu-id="c02fc-161">Description</span><span class="sxs-lookup"><span data-stu-id="c02fc-161">Description</span></span>                                                                                                                                                                                                     |
|------------------|------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c02fc-162">e-mail</span><span class="sxs-lookup"><span data-stu-id="c02fc-162">email</span></span>            | <span data-ttu-id="c02fc-163">string</span><span class="sxs-lookup"><span data-stu-id="c02fc-163">string</span></span>                                   | <span data-ttu-id="c02fc-164">O endereço de e-mail do cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-164">The customer's email address.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="c02fc-165">cultura</span><span class="sxs-lookup"><span data-stu-id="c02fc-165">culture</span></span>          | <span data-ttu-id="c02fc-166">string</span><span class="sxs-lookup"><span data-stu-id="c02fc-166">string</span></span>                                   | <span data-ttu-id="c02fc-167">A sua cultura preferida para a comunicação e a moeda, como "en-US".</span><span class="sxs-lookup"><span data-stu-id="c02fc-167">Their preferred culture for communication and currency, such as "en-US".</span></span> <span data-ttu-id="c02fc-168">Consulte [o Partner Center com línguas e locais apoiados](partner-center-supported-languages-and-locales.md) para as culturas apoiadas.</span><span class="sxs-lookup"><span data-stu-id="c02fc-168">See [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md) for the supported cultures.</span></span> |
| <span data-ttu-id="c02fc-169">language</span><span class="sxs-lookup"><span data-stu-id="c02fc-169">language</span></span>         | <span data-ttu-id="c02fc-170">string</span><span class="sxs-lookup"><span data-stu-id="c02fc-170">string</span></span>                                   | <span data-ttu-id="c02fc-171">A linguagem padrão.</span><span class="sxs-lookup"><span data-stu-id="c02fc-171">The default language.</span></span> <span data-ttu-id="c02fc-172">Dois códigos linguísticos de caracteres (por exemplo `en` `fr` ou) são suportados.</span><span class="sxs-lookup"><span data-stu-id="c02fc-172">Two character language codes (for example `en` or `fr`) are supported.</span></span>                                                                                                                                |
| <span data-ttu-id="c02fc-173">nome da empresa \_</span><span class="sxs-lookup"><span data-stu-id="c02fc-173">company\_name</span></span>    | <span data-ttu-id="c02fc-174">string</span><span class="sxs-lookup"><span data-stu-id="c02fc-174">string</span></span>                                   | <span data-ttu-id="c02fc-175">O nome de empresa/organização registado.</span><span class="sxs-lookup"><span data-stu-id="c02fc-175">The registered company/organization name.</span></span>                                                                                                                                                                       |
| <span data-ttu-id="c02fc-176">endereço padrão \_</span><span class="sxs-lookup"><span data-stu-id="c02fc-176">default\_address</span></span> | [<span data-ttu-id="c02fc-177">Endereço</span><span class="sxs-lookup"><span data-stu-id="c02fc-177">Address</span></span>](utility-resources.md#address) | <span data-ttu-id="c02fc-178">O endereço registado da empresa/organização do cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-178">The registered address of the customer's company/organization.</span></span> <span data-ttu-id="c02fc-179">Consulte o recurso [Address](utility-resources.md#address) para obter informações sobre eventuais limitações de comprimento.</span><span class="sxs-lookup"><span data-stu-id="c02fc-179">See the [Address](utility-resources.md#address) resource for information on any length limitations.</span></span>                                             |

#### <a name="company-profile"></a><span data-ttu-id="c02fc-180">Perfil da empresa</span><span class="sxs-lookup"><span data-stu-id="c02fc-180">Company profile</span></span>

<span data-ttu-id="c02fc-181">Esta tabela descreve os campos mínimos exigidos do recurso [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) necessário para criar um novo cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-181">This table describes the minimum required fields from the [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="c02fc-182">Nome</span><span class="sxs-lookup"><span data-stu-id="c02fc-182">Name</span></span>   | <span data-ttu-id="c02fc-183">Tipo</span><span class="sxs-lookup"><span data-stu-id="c02fc-183">Type</span></span>   | <span data-ttu-id="c02fc-184">Description</span><span class="sxs-lookup"><span data-stu-id="c02fc-184">Description</span></span>                                                  |
|--------|--------|--------------------------------------------------------------|
| <span data-ttu-id="c02fc-185">domínio</span><span class="sxs-lookup"><span data-stu-id="c02fc-185">domain</span></span> | <span data-ttu-id="c02fc-186">string</span><span class="sxs-lookup"><span data-stu-id="c02fc-186">string</span></span> | <span data-ttu-id="c02fc-187">O nome de domínio do cliente, como contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="c02fc-187">The customer's domain name, such as contoso.onmicrosoft.com.</span></span> |
|<span data-ttu-id="c02fc-188">organizaçãoRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="c02fc-188">organizationRegistrationNumber</span></span>|<span data-ttu-id="c02fc-189">String</span><span class="sxs-lookup"><span data-stu-id="c02fc-189">String</span></span>|<span data-ttu-id="c02fc-190">Número de registo da organização do cliente (também referido como número INN em determinados países).</span><span class="sxs-lookup"><span data-stu-id="c02fc-190">The customer’s organization registration number (also referred to as INN number in certain countries).</span></span> <span data-ttu-id="c02fc-191">Apenas necessário para a empresa/organização do cliente localizada nos seguintes países: Arménia(AM), Azerbaijão(AZ), Bielorrússia(BY), Hungria (HU), Cazaquistão(KZ), Quirguistão(KG), Moldávia (MD), Rússia(RU), Tajiquistão(TJ), Uzhbequistão(UZ), Ucrânia(UA), Brasil(BR), Índia, África do Sul, Polónia, Emirados Árabes Unidos, Arábia Saudita, Turquia, Tailândia, Vietname, Myanmar, Iraque, Sudão do Sul e Venezuela.</span><span class="sxs-lookup"><span data-stu-id="c02fc-191">Only required for customer’s company/organization located in the following countries: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA), Brazil(BR), India, South Africa, Poland, United Arab Emirates, Saudi Arabia, Turkey, Thailand, Vietnam, Myanmar, Iraq, South Sudan, and Venezuela.</span></span> <span data-ttu-id="c02fc-192">Para a empresa/organização do cliente localizada noutros países, este é um campo opcional.</span><span class="sxs-lookup"><span data-stu-id="c02fc-192">For customer’s company/organization located in other countries, this is an optional field.</span></span>|

### <a name="request-example"></a><span data-ttu-id="c02fc-193">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c02fc-193">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 789
Expect: 100-continue
Connection: Keep-Alive

{
    "CompanyProfile": {
        "Domain": "xyz.ccsctp.net",
    },
    "BillingProfile": {
        "Culture": "EN-US",
        "Email": "test@outlook.com",
        "Language": "en",
        "CompanyName": "test company",
        "DefaultAddress": {
            "FirstName": "Test",
            "LastName": "Test",
            "AddressLine1": "One Microsoft Way",
            "City": "Redmond",
            "State": "WA",
            "PostalCode": "98052",
            "Country": "US",
        }
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="c02fc-194">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c02fc-194">REST response</span></span>

<span data-ttu-id="c02fc-195">Se for bem sucedido, esta API devolve um recurso [ao Cliente](customer-resources.md#customer) para o novo cliente.</span><span class="sxs-lookup"><span data-stu-id="c02fc-195">If successful, this API returns a [Customer](customer-resources.md#customer) resource for the new customer.</span></span> <span data-ttu-id="c02fc-196">Guarde os detalhes do ID e AD do cliente para utilização futura com o Partner Center SDK.</span><span class="sxs-lookup"><span data-stu-id="c02fc-196">Save the customer ID and Azure AD details for future use with the Partner Center SDK.</span></span> <span data-ttu-id="c02fc-197">Você vai precisar deles para uso com gestão de conta, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="c02fc-197">You will need them for use with account management, for example.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c02fc-198">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c02fc-198">Response success and error codes</span></span>

<span data-ttu-id="c02fc-199">As respostas vêm com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c02fc-199">Responses come with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c02fc-200">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c02fc-200">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c02fc-201">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c02fc-201">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c02fc-202">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="c02fc-202">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 834
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CV: ObwhuhD2tUKJoM+Z.0
MS-ServerId: 202010223
Date: Tue, 14 Feb 2017 20:06:02 GMT

{
    "id": "dfd8cc0a-c592-468c-8461-869a38d24738",
    "commerceId": "0a4ce58a-6f96-4273-8035-d9c7d31b9ba4",
    "companyProfile": {
        "tenantId": "dfd8cc0a-c592-468c-8461-869a38d24738",
        "domain": "xyz.ccsctp.net",
        "attributes": {
            "objectType": "CustomerCompanyProfile"
        }
    },
    "billingProfile": {
        "id": "d17c0275-da92-5c33-9032-782ef1d0b69b",
        "email": "test@outlook.com",
        "culture": "en-US",
        "language": "en",
        "companyName": "test company",
        "defaultAddress": {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "One Microsoft Way",
            "postalCode": "98052",
            "firstName": "Test",
            "lastName": "Test",
            "phoneNumber": ""
        },
        "attributes": {
            "etag": "5920358838484612121",
            "objectType": "CustomerBillingProfile"
        }
    },
    "relationshipToPartner": "none",
    "userCredentials": {
        "userName": "admin",
        "password": "=;;n.=s9Z"
    },
    "attributes": {
        "objectType": "Customer"
    }
}
```
