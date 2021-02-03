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
# <a name="create-a-customer-for-an-indirect-reseller-using-partner-center-apis"></a>Crie um cliente para um revendedor indireto usando APIs do Partner Center

**Aplica-se a:**

- Partner Center

Um fornecedor indireto pode criar um cliente para um revendedor indireto.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- O identificador do inquilino do revendedor indireto.

- O revendedor indireto deve ter uma parceria com o fornecedor indireto.

## <a name="c"></a>C\#

Para adicionar um novo cliente para um revendedor indireto:

1. Instantaneamente um novo objeto [**de Cliente**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) e, em seguida, instantaneamente e povoar o [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) e [**o CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile). Certifique-se de atribuir o ID do revendedor indireto à propriedade [**AssociatedPartnerID.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid)

2. Utilize a propriedade [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para obter uma interface para as operações de recolha de clientes.

3. Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) ou [**Criar Aync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) para criar o cliente.

### <a name="c-example"></a>Exemplo \# C

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

**Amostra**: [App de teste de consola](console-test-app.md). **Projeto**: Partner Center SDK Samples **Class**: CreateCustomerforIndirectReseller.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                       |
|----------|-------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades necessárias no corpo de pedido.

| Nome                                          | Tipo   | Necessário | Descrição                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [BillingProfile](#billing-profile)             | objeto | Sim      | A informação do perfil de faturação do cliente.                                                                                                                                                                                                                                                                                                           |
| [EmpresaProfile](#company-profile)             | objeto | Sim      | Informação do perfil da empresa do cliente.                                                               
| [PartnerId Associado](customer-resources.md#customer) | string | Sim      | O iD do revendedor indireto. O revendedor indireto, tal como indicado pelo ID aqui fornecido, deve ter uma parceria com o fornecedor indireto ou o pedido falhará. Note também que se o valor AssociatedPartnerId não for fornecido, o cliente é criado como cliente direto do fornecedor indireto e não como revendedor indireto. |
|Domínio| String| Sim|O nome de domínio do cliente, como contoso.onmicrosoft.com.|
|organizaçãoRegistrationNumber|    string|Sim|     Número de registo da organização do cliente (também referido como número INN em determinados países). Apenas necessário para a empresa/organização do cliente localizada nos seguintes países. Arménia(AM), Azerbaijão(AZ), Bielorrússia (BY), Hungria (HU), Cazaquistão (KZ), Quirguistão(KG), Moldávia (MD), Rússia(RU), Tajiquistão(TJ), Uzhbequistão(UZ), Ucrânia (UA). Para a empresa/organização do cliente localizada noutros países, tal não deve ser especificado.|



#### <a name="billing-profile"></a>Perfil de faturação

Esta tabela descreve os campos mínimos exigidos do recurso [CustomerBillingProfile](customer-resources.md#customerbillingprofile) necessário para criar um novo cliente.

| Nome             | Tipo                                     | Necessário | Descrição                                                                                                                                                                                                     |
|------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| e-mail            | string                                   | Sim      | O endereço de e-mail do cliente.                                                                                                                                                                                   |
| cultura          | string                                   | Sim      | A sua cultura preferida para a comunicação e a moeda, como "en-US". Consulte [o Partner Center com línguas e locais apoiados](partner-center-supported-languages-and-locales.md) para as culturas apoiadas. |
| language         | string                                   | Sim      | A linguagem padrão. Dois códigos linguísticos de caracteres (por exemplo `en` `fr` ou) são suportados.                                                                                                                                |
| nome da empresa \_    | string                                   | Sim      | O nome de empresa/organização registado.                                                                                                                                                                       |
| endereço padrão \_ | [Endereço](utility-resources.md#address) | Sim      | O endereço registado da empresa/organização do cliente. Consulte o recurso [Address](utility-resources.md#address) para obter informações sobre eventuais limitações de comprimento.                                             |

#### <a name="company-profile"></a>Perfil da empresa

Esta tabela descreve os campos mínimos exigidos do recurso [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) necessário para criar um novo cliente.

| Nome   | Tipo   | Necessário | Descrição                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| domínio | string | Sim     | O nome de domínio do cliente, como contoso.onmicrosoft.com. |
| organizaçãoRegistrationNumber | string | Depende da condição | Número de registo da organização do cliente (também referido como número INN em determinados países). <br/><br/>A conclusão deste campo só é necessária se a empresa/organização de um cliente estiver localizada nos seguintes países: <br/><br/>- Arménia (AM) <br/>- Azerbaijão (AZ)<br/>- Bielorrússia (BY)<br/>- Hungria (HU)<br/>- Cazaquistão (KZ)<br/>- Quirguistão (KG)<br/>- Moldávia (MD)<br/>- Rússia (RU)<br/>- Tajiquistão (TJ)<br/>- Uzbequistão (UZ)<br/>- Ucrânia (UA)<br/><br/>Este campo não é necessário se a empresa/organização do cliente estiver localizada noutros países para além dos mostrados aqui.  |

### <a name="request-example"></a>Exemplo de pedido

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

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedida, a resposta contém um recurso [do Cliente](customer-resources.md#customer) para o novo cliente.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

As respostas vêm com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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