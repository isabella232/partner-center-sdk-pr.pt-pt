---
title: Atribuir licenças a um utilizador
description: Saiba como atribuir licenças a um utilizador do cliente através de APIs do Partner Center, como a utilização de APIs C \# ou REST.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6eb0b953b9157e48074415bb3207e2946cfb2ab4
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2020
ms.locfileid: "97770009"
---
# <a name="assign-licenses-to-a-user-via-partner-center-apis"></a>Atribuir licenças a um utilizador através de APIs do Partner Center

**Aplica-se a:**

- Partner Center

Como atribuir licenças a um utilizador cliente.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um identificador de utilizador de clientes. Esta identificação identifica o utilizador a quem atribuir a licença.

- Um identificador SKU de produto que identifica o produto para a licença.

## <a name="assigning-licenses-through-code"></a>Atribuição de licenças através de código

Ao atribuir licenças a um utilizador, deve escolher entre a recolha do cliente de SKUs subscritos. Em seguida, depois de ter identificado os produtos que pretende atribuir, tem de obter o produto SKU ID para cada produto para então fazer as atribuições. Cada [**instância SubscritaSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) contém uma propriedade [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) a partir da qual pode referenciar o objeto [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) e obter o [**ID**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id).

Um pedido de atribuição de licença deve conter licenças de um único grupo de licenças. Por exemplo, não é possível atribuir licenças do [**Grupo1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) e **do Grupo2** no mesmo pedido. Uma tentativa de atribuir licenças a mais de um grupo num único pedido falhará com um erro apropriado. Para saber quais as licenças disponíveis por grupo de licenças, consulte [obter uma lista de licenças disponíveis por grupo de licenças.](get-a-list-of-available-licenses-by-license-group.md)

Aqui estão os passos para atribuir licenças através do código:

1. Instantied um objeto [**de assinatura de licença.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) Utilize este objeto para especificar o produto SKU e os planos de serviço para atribuir.

    ``` csharp
    LicenseAssignment license = new LicenseAssignment();
    ```

2. Povoar as propriedades do objeto como mostrado abaixo. Este código pressupõe que já tem o produto SKU ID, e que todos os planos de serviço disponíveis serão atribuídos (ou seja, nenhum será excluído).

    ```csharp
    license.SkuId = selectedProductSkuId;
    license.ExcludedPlans = null;
    ```

3. Se não tiver o produto SKU ID, precisa de recuperar a recolha de SKUs subscritos e obter o produto SKU ID de um deles. Aqui está um exemplo se conhecer o nome SKU do produto.

    ```csharp
    var customerSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
    var sku = customerSubscribedSkus.Items.Where(n => n.ProductSku.Name == "Office 365 Enterprise E3").First();
    license.SkuId = sku.ProductSku.Id;
    license.ExcludedPlans = null;
    ```

4. Em seguida, instantânea uma nova lista de [**tipo Licençaasignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment), e adicionar o objeto de licença. Pode atribuir mais do que uma licença adicionando cada uma individualmente à lista. As licenças incluídas nesta lista devem ser do mesmo grupo de licenças.

    ```csharp
    List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
    licenseList.Add(license);
    ```

5. Crie uma instância [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) e atribua a lista de atribuições de licenças à propriedade [**LicensesToAssign.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign)

    ```csharp
    LicenseUpdate updateLicense = new LicenseUpdate();
    updateLicense.LicensesToAssign = licenseList;
    ```

6. Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) ou [**CriarAync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) e passe o objeto de atualização da licença como mostrado abaixo para atribuir as licenças.

    ```csharp
    var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
    ```

## <a name="c"></a>C\#

Para atribuir uma licença a um utilizador do cliente, primeiro instantaneamente um objeto [**de assinatura de Licença**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) e povoar as propriedades [**Skuid**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) e [**ExcluiedPlans.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans) Utilize este objeto para especificar o produto SKU para atribuir e os planos de serviço para excluir. Em seguida, instantânea uma nova lista de **tipo Licençaassignment**, e adicionar o objeto de licença à lista. Em seguida, crie uma instância [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) e atribua a lista de atribuições de licenças para a propriedade [**LicensesToAssign.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign)

Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente, e o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID do utilizador para identificar o utilizador. Em seguida, obtenha uma interface para as operações de atualização da licença de utilizador do cliente a partir da propriedade [**LicenseUpdates.**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates)

Por fim, ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) ou [**CriarAync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) e passe o objeto de atualização de licença para atribuir a licença.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerUserId;
// string selectedCustomerId;
// string selectedProductSkuId;

// Instantiate and populate a LicenseAssignment object.
LicenseAssignment license = new LicenseAssignment();
license.SkuId = selectedProductSkuId;
license.ExcludedPlans = null;

// Instantiate a list of licenses to assign and add the license to it.
List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
licenseList.Add(license);

// Instantiate a LicenseUpdate object and add the list of licenses to assign.
LicenseUpdate updateLicense = new LicenseUpdate();
updateLicense.LicensesToAssign = licenseList;

// Update the user licenses.
var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
```

**Amostra**: [App de teste de consola](console-test-app.md). **Projeto**: Partner Center SDK Samples **Class**: CustomerUserAssignLicenses.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                    |
|----------|----------------------------------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/users/{user-id}/licenseupdates HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros de percurso para identificar o cliente e o utilizador.

| Nome        | Tipo   | Necessário | Descrição                                       |
|-------------|--------|----------|---------------------------------------------------|
| id cliente | string | Sim      | Um ID formatado GUID que identifica o cliente. |
| user-id     | string | Sim      | Um ID formatado GUID que identifica o utilizador.     |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Inclua um recurso [LicenseUpdate](license-resources.md#licenseupdate) no órgão de pedido que especifica as licenças a atribuir.

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/554526aa-cf5e-46fa-95df-98dbc55d8a1e/licenseupdates HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 183
Expect: 100-continue

{
    "LicensesToAssign": [{
            "ExcludedPlans": null,
            "SkuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "LicensesToRemove": null,
    "LicenseWarnings": null,
    "Attributes": {
        "ObjectType": "LicenseUpdate"
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, é devolvido um código de estado de resposta HTTP 201 e o organismo de resposta contém um recurso [LicenseUpdate](license-resources.md#licenseupdate) com as informações da licença.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example-success"></a>Exemplo de resposta (sucesso)

```http
HTTP/1.1 201 Created
Content-Length: 139
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CV: 5AnzcZQrvUqCq3kd.0
MS-ServerId: 030020525
Date: Thu, 20 Apr 2017 21:50:39 GMT

{
    "licensesToAssign": [{
            "skuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "licenseWarnings": [],
    "attributes": {
        "objectType": "LicenseUpdate"
    }
}
```

### <a name="response-example-license-isnt-available"></a>Exemplo de resposta (a licença não está disponível)

```http
HTTP/1.1 400 Bad Request
Content-Length: 341
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: f4f3b748-8b22-4d07-a5a1-dceb32824192
MS-CV: 5npA0K22CUmWPOzB.0
MS-ServerId: 102030524
Date: Thu, 20 Apr 2017 22:12:36 GMT

{
    "code": 60012,
    "description": "We&#39;re sorry, it looks like you've run out of licenses. Buy more licenses, and then try again.",
    "data": ["LicenseQuotaExceededException : Subscription with Account 0c39d6d5-c70d-4c55-bc02-f620844f3fd1 and SKU f8a1db68-be16-40ed-86d5-cb42ce701560 does not have any available licenses left."],
    "source": "PartnerFD"
}
```
