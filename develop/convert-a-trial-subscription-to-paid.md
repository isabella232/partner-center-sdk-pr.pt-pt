---
title: Converter uma subscrição de avaliação em paga
description: Saiba como usar as APIs do Partner Center para converter uma subscrição de teste para uma paga.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7cee9b9afddb12137bb66b57250a9487bd4902f5
ms.sourcegitcommit: f112efee7344d739bdbf385adba0c554ea2a63e3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439332"
---
# <a name="convert-a-trial-subscription-to-paid-using-partner-center-apis"></a>Converter uma subscrição experimental para pago usando APIs do Partner Center

> [!NOTE]
> Estes passos não são aplicáveis aos Novos Produtos de Comércio. Consulte para a Transição uma nova documentação **de subscrição de comércio** para converter ensaios de New Commerce para subscrições pagas

Pode converter uma subscrição experimental a pagar.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+Utilizador.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no painel do Centro [de Parceiros.](https://partner.microsoft.com/dashboard) Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta**. Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de assinatura para uma subscrição de teste ativo.

- Uma oferta de conversão disponível.

## <a name="convert-a-trial-subscription-to-a-paid-subscription-through-code"></a>Converter uma subscrição experimental para uma subscrição paga através de código

Para converter uma subscrição experimental para uma paga, você deve primeiro obter uma coleção das conversões experimentais disponíveis. Em seguida, deve escolher a oferta de conversão que pretende comprar.

As ofertas de conversão especificarão uma quantidade que predefinirá ao mesmo número de licenças que a subscrição do ensaio. Pode alterar esta quantidade definindo a propriedade [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion.quantity) para o número de licenças que pretende adquirir.

> [!NOTE]
> Independentemente do número de licenças adquiridas, o ID de subscrição do ensaio é reutilizado para as licenças adquiridas. Como resultado, o julgamento em vigor desaparece e é substituído pela compra.

Utilize os seguintes passos para converter uma subscrição experimental através de código:

1. Obtenha uma interface para as operações de subscrição disponíveis. Deve identificar o cliente e especificar o identificador de subscrição da subscrição do ensaio.

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2. Obtenha uma coleção das ofertas de conversão disponíveis. Para obter mais informações e detalhes sobre o pedido/resposta para este método, consulte [obter uma lista de ofertas de conversão experimental](get-a-list-of-trial-conversion-offers.md).

    ``` csharp
    var conversions = subscriptionOperations.Conversions.Get();
    ```

3. Escolha uma oferta de conversão. O código seguinte escolhe a primeira oferta de conversão na coleção.

    ``` csharp
    var selectedConversion = conversions.Items.ToList()[0];
    ```

4. Opcionalmente, especifique o número de licenças para comprar. O padrão é o número de licenças na subscrição de teste.

    ``` csharp
    selectedConversion.Quantity = 10;
    ```

5. Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) ou [**CriarAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) para converter a subscrição experimental a pagar.

    ``` csharp
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
    ```

## <a name="c"></a>C\#

Para converter uma subscrição experimental para uma paga:

1. Utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.

2. Obtenha uma interface para as operações de subscrição ligando para o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID de subscrição de teste. Guarde uma referência à interface de operações de subscrição numa variável local.

3. Utilize a propriedade [**Conversões**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) para obter uma interface para as operações disponíveis nas conversões e, em seguida, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) para recuperar uma coleção de ofertas de [**Conversão**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) disponíveis. Tem de escolher um. O exemplo a seguir é o de incumprimento da primeira conversão disponível.

4. Utilize a referência à interface de operações de subscrição que guardou numa variável local e na propriedade [**Conversões**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) para obter uma interface para as operações disponíveis nas conversões.

5. Passe o objeto de oferta de conversão selecionado para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) ou [**CriarAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) para tentar a conversão experimental.

### <a name="c-example"></a>Exemplo \# C

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

// Get subscription operations for the trial subscription.
var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);

// Get the available conversions.
var conversions = subscriptionOperations.Conversions.Get();

// If there are no conversions available, we&#39;re done.
// Otherwise, convert the trial to the first available conversion offer.
if (conversions.TotalCount <= 0)
{
    System.Console.WriteLine("This subscription has no conversions");
}
else
{
    // Default to the first conversion.
    var selectedConversion = conversions.Items.ToList()[0];

    // Convert the trial and return the result.
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
}
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| **PUBLICAR** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/conversões HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de percurso para identificar a subscrição do cliente e do ensaio.

| Nome            | Tipo   | Necessário | Descrição                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| id cliente     | string | Yes      | Uma cadeia formatada GUID que identifica o cliente.           |
| id de subscrição | string | Yes      | Uma cadeia formatada GUID que identifica a subscrição do ensaio. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Um recurso de [conversão](conversions-resources.md#conversion) povoado deve ser incluído no organismo de pedido.

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638/conversions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bd0cde7f-ba87-4010-8a73-1190b641f2a4
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 234
Expect: 100-continue

{
    "OfferId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
    "TargetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "OrderId": "D51A052E-043C-4A2A-AA37-2BB938CEF6C1",
    "Quantity": 25,
    "BillingCycle": "monthly",
    "Attributes": {
        "ObjectType": "Conversion"
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém um recurso [ConversionResult.](conversions-resources.md#conversionresult)

#### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

#### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 211
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
MS-RequestId: bd0cde7f-ba87-4010-8a73-1190b641f2a4
MS-CV: kW4GzmhvHEqCq1ls.0
MS-ServerId: 030020643
Date: Thu, 15 Jun 2017 23:10:40 GMT

 {
    "subscriptionId": "488745B5-2086-4912-802C-6ABB9F7C3638",
    "offerId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
    "targetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "attributes": {
        "objectType": "ConversionResult"
    }
}
```
