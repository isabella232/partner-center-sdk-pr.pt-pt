---
title: Alterar a quantidade de uma subscrição
description: Saiba como utilizar as APIs do Partner Center para alterar a quantidade de licenças para uma subscrição de clientes. Também pode fazê-lo no painel partner Center.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 85048dbbdc605f46c12c00484961fbb3068c4f16
ms.sourcegitcommit: 3ee00d9fe9da6b9df0fb7027ae506e2abe722770
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129417241"
---
# <a name="change-the-quantity-of-licenses-in-a-customer-subscription"></a>Alterar a quantidade de licenças numa subscrição de cliente

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Partner Center para Microsoft Cloud Germany | Centro de Parceiros para Microsoft Cloud for US Government

Atualiza uma [subscrição](subscription-resources.md) para aumentar ou diminuir a quantidade de licenças.

No painel partner center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md) Em seguida, selecione a subscrição em questão que deseja renomear. Para terminar, altere o valor no campo **Quantidade** e, em seguida, selecione **Enviar.**

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no painel do Centro [de Parceiros.](https://partner.microsoft.com/dashboard) Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta**. Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de assinatura.

## <a name="c"></a>C\#

Para alterar a quantidade da subscrição de um cliente, primeiro [obtenha a subscrição,](get-a-subscription-by-id.md)em seguida, altere a propriedade [**quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.quantity) da subscrição. Assim que a alteração for feita, utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().** Em seguida, ligue para a propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) seguida do método [**ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) Em seguida, termine chamando o método **Patch().**

``` csharp
// IAggregatePartner partnerOperations;
// var customerId;
// var subscriptionId;

//retrieving the subscription, for the purpose of the sample
ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.Get();
Subscription selectedSubscription = customerSubscriptions.Items.FirstOrDefault(sub => sub.Status == SubscriptionStatus.Active);

//update selected subscription,
selectedSubscription.Quantity++;

var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método    | URI do pedido                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscription-id} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Esta tabela lista o parâmetro de consulta necessário para alterar a quantidade da subscrição.

| Nome                    | Tipo     | Necessário | Descrição                               |
|-------------------------|----------|----------|-------------------------------------------|
| **cliente-inquilino-id**  | **guid** | Y        | Um GUID correspondente ao cliente.     |
| **id de subscrição** | **guid** | Y        | Um GUID correspondente à subscrição. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

É necessário um recurso **de subscrição** completo no organismo de pedido. Certifique-se de que a propriedade **Quantidade** foi atualizada.

### <a name="request-example"></a>Exemplo de pedido

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
    "FriendlyName": "nickname",
    "Quantity": 2,
    "UnitType": "none",
    "ParentSubscriptionId": null,
    "CreationDate": "2015-11-25T06:41:12Z",
    "EffectiveStartDate": "2015-11-24T08:00:00Z",
    "CommitmentEndDate": "2016-12-12T08:00:00Z",
    "Status": "active",
    "AutoRenewEnabled": false,
    "BillingType": "none",
    "PartnerId": null,
    "ContractType": "subscription",
    "OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```

### <a name="request-example-for-new-commerce-subscription-to-reduce-quantity"></a>Pedido de exemplo para nova subscrição de comércio para reduzir quantidade

> [!Note] 
> As novas alterações de Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.

A quantidade de licença só pode ser reduzida no prazo de 72 horas após a compra ou renovação de uma subscrição. As licenças adicionadas a meio do semestre também só podem ser reduzidas dentro de 72 horas, apenas através do apoio ao cliente.

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscription-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "id": "a4c1340d-6911-4758-bba3-0c4c6007d161",
    "offerId": "CFQ7TTC0LH18:0001:CFQ7TTC0K971",
    "offerName": "Microsoft 365 Business Basic",
    "friendlyName": "Microsoft 365 Business Basic",
    "productType": {
        "id": "OnlineServicesNCE",
        "displayName": "OnlineServicesNCE"
    },
    "quantity": 1, // original value = 10
    "unitType": "Licenses",
    "hasPurchasableAddons": false,
    "creationDate": "2021-01-14T16:57:15.0966728Z",
    "effectiveStartDate": "2021-01-14T16:57:14.498252Z",
    "commitmentEndDate": "2022-01-13T00:00:00Z",
    "status": "active", 
    "autoRenewEnabled": true, 
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1Y",
    "renewalTermDuration": "",
    "refundOptions": [
        {
            "type": "Full",
            "expiresAt": "2021-01-15T00:00:00Z"
        }
    ],
    "isMicrosoftProduct": true,
    "partnerId": "",
    "attentionNeeded": false,
    "actionTaken": false,
    "contractType": "subscription",
    "links": {
        "product": {
            "uri": "/products/CFQ7TTC0LH18?country=US",
            "method": "GET",
            "headers": []
        },
        "sku": {
            "uri": "/products/CFQ7TTC0LH18/skus/0001?country=US",
            "method": "GET",
            "headers": []
        },
        "availability": {
            "uri": "/products/CFQ7TTC0LH18/skus/0001/availabilities/CFQ7TTC0K971?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/d8202a51-69f9-4228-b900-d0e081af17d7/subscriptions/a4c1340d-6911-4758-bba3-0c4c6007d161",
            "method": "GET",
            "headers": []
        }
    },
    "publisherName": "Microsoft Corporation",
    "orderId": "34b37d7340cc",
    "attributes": {
        "objectType": "Subscription"
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um código de estado **HTTP 200** e atualiza as propriedades [dos recursos de subscrição](subscription-resources.md)  no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta devolve um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler o código de estado, o tipo de erro e os parâmetros adicionais. Para obter a lista completa, consulte [Códigos de Erro](error-codes.md).

Quando a operação de correção demorar mais do que o tempo esperado, o Partner Center envia um código de estado **HTTP 202** e um cabeçalho de localização que aponta para onde recuperar a subscrição. Pode consultar periodicamente a subscrição para monitorizar o estado e as alterações de quantidade.

### <a name="response-examples"></a>Exemplos de resposta

#### <a name="response-example-1"></a>Exemplo de resposta #1

Pedido de sucesso com um código de estado **HTTP 200:**

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-Contract-Version: v1
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
    "FriendlyName": "nickname",
    "Quantity": 2,
    "UnitType": "none",
    "ParentSubscriptionId": null,
    "CreationDate": "2015-11-25T06:41:12Z",
    "EffectiveStartDate": "2015-11-24T08:00:00Z",
    "CommitmentEndDate": "2016-12-12T08:00:00Z",
    "Status": "active",
    "AutoRenewEnabled": false,
    "BillingType": "none",
    "PartnerId": null,
    "ContractType": "subscription",
    "Links": {
        "Offer": {
            "Uri": "/v1/offers/0CCA44D6-68E9-4762-94EE-31ECE98783B9",
            "Method": "GET",
            "Headers": []
        },
        "Entitlement": {
            "Uri": "/entitlements?key=<key>",
            "Method": "GET",
            "Headers": []
        },
        "Self": {
            "Uri": "/subscriptions?key=<key>",
            "Method": "GET",
            "Headers": []
        }
    },
    "OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```

#### <a name="response-example-2"></a>Exemplo de resposta #2

Pedido de sucesso com um código de estado **HTTP 202:**

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 01880c1b-1966-40f0-d470-501a66d9948b
MS-CorrelationId: 2c5827c1-d5f9-4835-cc6d-f1918b782c79
Content-Type: application/json
Content-Length: 1432
Connection: Keep-Alive
Location: /customers/<customer-tenant-id>/subscriptions/<subscriptionID>
```

#### <a name="response-example-for-new-commerce-license-reduction"></a>Exemplo de resposta para nova redução de licenças de comércio

> [!Note] 
> As novas alterações de Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.

Experimente a resposta da API ao tentar reduzir as quantidades de licença para novas subscrições de comércio fora da janela de cancelamento de 72 horas.

```http
{
    "code": 800090,
    "description": "Subscription quantity cannot be decreased.",
    "data": [],
    "source": "PartnerFD"
}
```

