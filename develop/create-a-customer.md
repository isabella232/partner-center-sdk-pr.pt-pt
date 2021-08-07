---
title: Criar um cliente
description: Saiba como um parceiro Fornecedor de Soluções em Nuvem (CSP) pode usar APIs do Partner Center para criar um novo cliente. O artigo descreve os pré-requisitos e o que mais acontece.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 49df47441276c7e79074e1bf7f8d50cd72054b42acd93938de088046b68b6d98
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991774"
---
# <a name="create-a-customer-using-partner-center-apis"></a>Criar um cliente usando APIs do Partner Center

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud for US Government

Este artigo explica como criar um novo cliente.

> [!IMPORTANT]
> Se é um fornecedor indireto e pretende criar um cliente para um revendedor indireto, consulte [criar um cliente para um revendedor indireto.](create-a-customer-for-an-indirect-reseller.md)

Como parceiro de fornecedor de soluções em nuvem (CSP), quando criar um cliente pode fazer encomendas em nome do cliente. Quando cria um cliente, também cria:

- Um objeto de inquilino Azure Ative Directory (AD) para o cliente.

- Uma relação entre o revendedor e o cliente, usada para privilégios administrativos delegados.

- Um nome de utilizador e senha para iniciar sinscrônico para o cliente.

Uma vez criado o cliente, certifique-se de guardar os detalhes de ID e AD do cliente para utilização futura com o Partner Center SDK (por exemplo, gestão de conta).

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

> [!IMPORTANT]
> Para criar um inquilino do cliente deve fornecer um endereço físico válido durante o processo de criação. Um endereço pode ser validado seguindo os passos descritos no cenário [de validação de um endereço.](validate-an-address.md) Se criar um cliente usando um endereço inválido no ambiente da caixa de areia, não poderá eliminar esse cliente.

## <a name="c"></a>C\#

Para adicionar um cliente:

1. Instantaneamente um novo objeto [**cliente.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) Certifique-se de preencher o [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) e [**o CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).

2. Adicione o novo cliente à sua coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) chamando [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) ou [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync).

### <a name="c-example"></a>Exemplo \# C

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

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: CreateCustomer.cs

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Para criar um novo cliente:

1. Crie uma nova instância do **CustomerBillingProfile** e dos objetos **CustomerCompanyProfile.** Certifique-se de povoar os campos necessários.

2. Crie o cliente chamando o **IAggregatePartner.getCustomers().criar** função.

### <a name="java-example"></a>Exemplo de Java

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

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Para criar um cliente, execute o comando [**New-PartnerCustomer.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md)

```powershell
New-PartnerCustomer -BillingAddressLine1 '1 Microsoft Way' -BillingAddressCity 'Redmond' -BillingAddressCountry 'US' -BillingAddressPostalCode '98052' -BillingAddressState 'WA' -ContactEmail 'jdoe@customer.com' -ContactFirstName 'Jane' -ContactLastName 'Doe' -Culture 'en-US' -Domain 'newcustomer.onmicrosoft.com' -Language 'en' -Name 'New Customer'
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                       |
|----------|-------------------------------------------------------------------|
| **PUBLICAR** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

- Esta API é idempotente (não produzirá um resultado diferente se lhe chamar várias vezes).

- É necessária uma identificação de pedido e uma identificação de correlação.

- Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades necessárias no corpo de pedido.

| Nome                              | Tipo   | Description                                 |
|-----------------------------------|--------|---------------------------------------------|
| [BillingProfile](#billing-profile) | objeto | A informação do perfil de faturação do cliente. |
| [EmpresaProfile](#company-profile) | objeto | Informação do perfil da empresa do cliente. |

#### <a name="billing-profile"></a>Perfil de faturação

Esta tabela descreve os campos mínimos exigidos do recurso [CustomerBillingProfile](customer-resources.md#customerbillingprofile) necessário para criar um novo cliente.

| Nome             | Tipo                                     | Description                                                                                                                                                                                                     |
|------------------|------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| e-mail            | string                                   | O endereço de e-mail do cliente.                                                                                                                                                                                   |
| cultura          | string                                   | A sua cultura preferida para a comunicação e a moeda, como "en-US". Consulte [o Partner Center com línguas e locais apoiados](partner-center-supported-languages-and-locales.md) para as culturas apoiadas. |
| language         | string                                   | A linguagem padrão. Dois códigos linguísticos de caracteres (por exemplo `en` `fr` ou) são suportados.                                                                                                                                |
| nome da empresa \_    | string                                   | O nome de empresa/organização registado.                                                                                                                                                                       |
| endereço padrão \_ | [Endereço](utility-resources.md#address) | O endereço registado da empresa/organização do cliente. Consulte o recurso [Address](utility-resources.md#address) para obter informações sobre eventuais limitações de comprimento.                                             |

#### <a name="company-profile"></a>Perfil da empresa

Esta tabela descreve os campos mínimos exigidos do recurso [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) necessário para criar um novo cliente.

| Nome   | Tipo   | Description                                                  |
|--------|--------|--------------------------------------------------------------|
| domínio | string | O nome de domínio do cliente, como contoso.onmicrosoft.com. |
|organizaçãoRegistrationNumber|String|Número de registo da organização do cliente (também referido como número INN em determinados países). Apenas necessário para a empresa/organização do cliente localizada nos seguintes países: Arménia(AM), Azerbaijão(AZ), Bielorrússia(BY), Hungria (HU), Cazaquistão(KZ), Quirguistão(KG), Moldávia (MD), Rússia(RU), Tajiquistão(TJ), Uzhbequistão(UZ), Ucrânia(UA), Brasil(BR), Índia, África do Sul, Polónia, Emirados Árabes Unidos, Arábia Saudita, Turquia, Tailândia, Vietname, Myanmar, Iraque, Sudão do Sul e Venezuela. Para a empresa/organização do cliente localizada noutros países, este é um campo opcional.|

### <a name="request-example"></a>Exemplo de pedido

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

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, esta API devolve um recurso [ao Cliente](customer-resources.md#customer) para o novo cliente. Guarde os detalhes do ID e AD do cliente para utilização futura com o Partner Center SDK. Você vai precisar deles para uso com gestão de conta, por exemplo.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

As respostas vêm com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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
