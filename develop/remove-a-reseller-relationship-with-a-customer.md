---
title: Remover uma relação de revendedor com um cliente
description: Como remover uma relação de revendedor com um cliente com o qual já não tem transações.
ms.date: 01/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 45eca3564c3b9078e04d1f8155d08849a589d52f
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446603"
---
# <a name="remove-a-reseller-relationship-with-a-customer"></a>Remover uma relação de revendedor com um cliente

Remova uma relação de revendedor com um cliente com o quais já não tenha transações.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Todas as ordens de Azure Reserved VM Instance devem ser canceladas antes de uma relação de revendedor ser removida. Ligue para o suporte da Azure para cancelar quaisquer ordens de Azure Reserved VM Instance.

## <a name="c"></a>C\#

Para remover a relação de revendedor para um cliente, certifique-se primeiro de que quaisquer instâncias VM reservadas ativas para esse cliente são canceladas. Em seguida, certifique-se de que todas as subscrições ativas para esse cliente estão suspensas. Para tal, determine o ID do cliente para quem pretende eliminar a relação do revendedor. No seguinte exemplo de código, o utilizador é solicitado a fornecer o identificador do cliente.

Para determinar se quaisquer instâncias VM Reservadas Azure para o cliente devem ser canceladas, recupere a recolha de direitos ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) utilizando o identificador de clientes para especificar o cliente, e a propriedade Entitlements para recuperar uma interface para operações de cobrança de [**direitos.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) para recuperar a coleção de direitos. Filtrar a coleção para quaisquer direitos com um valor [**EntitlementType**](entitlement-resources.md#entitlementtype) de [**EntitlementType.VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) e, se houver, cancele-os chamando o apoio antes de prosseguir.

Em seguida, recupere uma coleção das subscrições do cliente ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) utilizando o identificador de clientes para especificar o cliente, e a propriedade [**de Subscrições**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) para recuperar uma interface para operações de recolha de subscrição. Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) para recuperar a recolha de subscrições do cliente. Traverse a coleção de subscrição e certifique-se de que nenhuma das subscrições tem um valor de propriedade [**subscrição.Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) do [**SubscriptionStatus.Ative**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus). Se uma subscrição ainda estiver ativa, consulte [suspender uma subscrição](suspend-a-subscription.md) para obter informações sobre como suspendê-la.

Depois de confirmar que todas as instâncias ativas do Azure Reserved VM para esse cliente são canceladas e todas as subscrições ativas estão suspensas, pode remover a relação de revendedor para o cliente. Em primeiro lugar, crie um novo objeto [Cliente/dotnet/api/microsoft.store.partnercenter.customer.customer.customer. [](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship) Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) utilizando o identificador de clientes para especificar o cliente e ligar para o método **Patch,** passando no novo objeto do cliente.

Para restabelecer a relação, repita o processo de [solicitar uma relação revendedor/parceiro-centro/desenvolver/solicitar-revendedor-relação).

``` csharp
// IAggregatePartner partnerOperations;

// Prompt the user the enter the customer ID.
var customerIdToDeleteRelationshipOf = this.Context.ConsoleHelper.ReadNonEmptyString("Please enter the ID of the customer you want to delete the relationship with", "The customer ID can't be empty");

// Determine if there are any active Azure Reserved VM Instances for this customer.
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Entitlements.Get();

If (entitlements.Items.Where(x => x.EntitlementType == EntitlementType.VirtualMachineReservedInstance).Any())
{
    this.Context.ConsoleHelper.Warning("Please cancel Azure Reserved Virtual Machine Instance orders through support and try again. Aborting the delete customer relationship operation");
               return;
}

// Verify that there are no active subscriptions.
ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Subscriptions.Get();
IList<Subscription> subscriptions = new List<Subscription>(customerSubscriptions.Items);

foreach (Subscription customerSubscription in subscriptions)
{
    if (customerSubscription.Status == SubscriptionStatus.Active)
    {
        this.Context.ConsoleHelper.Warning(String.Format("Subscription with ID :{0}  OfferName: {1} cannot be in active state, ", customerSubscription.Id, customerSubscription.OfferName));
        this.Context.ConsoleHelper.Warning("Please Suspend all the Subscriptions and try again. Aborting the delete customer relationship operation");
               return;
    }
}

// Delete the customer's relationship to the partner.
Customer customer = new Customer();
customer.RelationshipToPartner = CustomerPartnerRelationship.None;
customer = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Patch(customer);

if (customer.RelationshipToPartner == CustomerPartnerRelationship.None)
{
    this.Context.ConsoleHelper.Success("Customer Partner Relationship successfully deleted");
}
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: PartnerSDK.FeatureSample **Class**: DeletePartnerCustomerRelationship.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método     | URI do pedido                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| **PATCH**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/ HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Esta tabela lista os parâmetros de consulta necessários para remover uma relação de revendedor.

| Nome                   | Tipo     | Necessário | Descrição                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | O valor é um **design de cliente-inquilino-inquilino** formatado guid que identifica o cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

É necessário um recurso **do Cliente** no organismo de pedido. Certifique-se de que a propriedade **RelationshipToPartner** não foi definida para nenhuma.

### <a name="request-example"></a>Exemplo de pedido

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Authorization: Bearer <token>
Content-Length: 74
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
MS-RequestId: 9fef8b23-6e3e-45d2-8678-e9fe89c35af5
Date: Fri, 12 Jan 2018 00:31:55 GMT

{
    "relationshipToPartner":"none",
    "attributes":{
        "objectType":"Customer"
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método remove uma relação de revendedor para o cliente especificado.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
MS-RequestId: 7988dde4-b516-472c-b226-6d53fb18f04e
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
X-Locale: en-US
Content-Type: application/json
Content-Length: 242
Expect: 100-continue

{
    "Id":null,
    "CommerceId":null,
    "CompanyProfile":null,
    "BillingProfile":null,
    "RelationshipToPartner":"none",
    "AllowDelegatedAccess":null,
    "UserCredentials":null,
    "CustomDomains":null,
    "AssociatedPartnerId":null,
    "Attributes":{
        "ObjectType":"Customer"
    }
}
```
