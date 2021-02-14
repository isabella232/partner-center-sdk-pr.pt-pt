---
title: Obter itens de linha da fatura
description: Pode obter uma recolha de dados de linha de fatura (item de linha de faturação fechada) para uma fatura especificada utilizando as APIs do Partner Center.
ms.date: 01/27/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e797f549e1344268c8167259a231122e7c669a2e
ms.sourcegitcommit: 9f8ba784171ab4f980ed0c60ef6f2323849c4a98
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100499903"
---
# <a name="get-invoice-line-items"></a>Obter itens de linha da fatura

**Aplica-se a:**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Pode utilizar os seguintes métodos para obter detalhes de recolha de itens de linha de fatura (também conhecidos como itens de linha de faturação fechados) para uma fatura especificada.

*Com exceção das correções de erros, esta API já não está a ser atualizada.* Deve atualizar as suas aplicações para ligar para a única **API** em vez de **marketplace**. A **única API** fornece funcionalidade adicional e continuará a ser atualizada.

Você deve usar **uma vez** para consultar todos os itens de linha de consumo comercial em vez de **mercado**. Ou pode seguir os links na chamada de links de estimativa.

Esta API também suporta os tipos **de** **fornecedores** de subscrições e **escritórios** para subscrições e ofertas do Microsoft Azure (MS-AZR-0145P), o que torna a funcionalidade API para trás compatível.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um identificador de fatura. Isto identifica a fatura para a recuperação dos itens de linha.

## <a name="c"></a>C\#

Para obter os itens de linha para a fatura especificada:

1. Ligue para o método [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) para obter uma interface para as operações de faturação para a fatura especificada.

2. Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar o objeto da fatura. O objeto da fatura contém todas as informações para a fatura especificada.
3. Utilize a propriedade [**faturadetails**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoice.invoicedetails) do objeto de fatura para ter acesso a uma coleção de objetos [**FaturaDetail,**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail) cada um dos quais contém um [**BillingProvider**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.billingprovider) e um [**InvoiceLineItemType**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.invoicelineitemtype). O **BillingProvider** identifica a origem das informações detalhadas da fatura (como **Office**, **Azure**, **OneTime**) e o **InvoiceLineItemType** especifica o tipo (por exemplo, **BillingLineItem).**

O seguinte código exemplo utiliza um circuito **de apreensão para** processar a coleção **FaturaDetails.** Uma coleção separada de itens de linha é recuperada para cada instância **FaturaDetail.**

Para obter uma coleção de itens de linha que correspondam a uma instância **FaturaDetail:**

1. Passe o **BillingProvider** e **o InvoiceLineItemType** para o método [**Por.**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by)

2. Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.getasync) para recuperar os itens de linha associados.
3. Crie um enumerador para atravessar a coleção como mostrado no exemplo seguinte.

``` csharp
// IAggregatePartner partnerOperations;
// int invoicePageSize;
// string invoiceId;

// Retrieve the invoice.
var invoiceOperations = partnerOperations.Invoices.ById(invoiceId);
var invoice = invoiceOperations.Get();

foreach (var invoiceDetail in invoice.InvoiceDetails)
{
    Console.WriteLine(string.Format("Getting invoice line item for product {0} and line item type {1}",
        invoiceDetail.BillingProvider,
        invoiceDetail.InvoiceLineItemType));

    // Is this an unpaged or paged request?
    bool isUnPaged = (this.invoicePageSize <= 0);

    // If the scenario is unpaged, get all the invoice line items, otherwise get the first page.
    var invoiceLineItemsCollection =
        (isUnPaged)
        ? invoiceOperations.By(invoiceDetail.BillingProvider, invoiceDetail.InvoiceLineItemType).Get()
        : invoiceOperations.By(invoiceDetail.BillingProvider, invoiceDetail.InvoiceLineItemType).Get(this.invoicePageSize, 0);

    // Create an enumerator for traversing the line items collection.
    var invoiceLineItemEnumerator =
        partnerOperations.Enumerators.InvoiceLineItems.Create(invoiceLineItemsCollection);

    while (invoiceLineItemEnumerator.HasValue)
    {
        // invoiceLineItemEnumerator.Current contains a collection
        // of line items.
        Console.WriteLine(String.Format("invoiceLineItemEnumerator.Current has {0} line items.",
            invoiceLineItemEnumerator.Current.TotalCount));
        //
        // Insert code here to work with the line items.
        //
        Console.WriteLine();
        Console.Write("Press any key to retrieve the next invoice line items page");
        Console.ReadKey();

        // Get the next list of invoice line items.
        invoiceLineItemEnumerator.Next();
    }
}
```

Para um exemplo semelhante, consulte o seguinte:

- Amostra: [App de teste de consola](console-test-app.md)
- Projeto: **Partner Center SDK Samples**
- Classe: **GetInvoiceLineItems.cs**

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

Faça o seu pedido utilizando a sintaxe adequada para o fornecedor de faturação no seu cenário.

#### <a name="office"></a>Office

A seguinte sintaxe aplica-se quando o fornecedor de faturação é **o Office**.

| Método  | URI do pedido                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=office&invoicelineitemtype=billinglineitems&size={size}&offset={offset} HTTP/1.1                               |

#### <a name="microsoft-azure-ms-azr-0145p-subscription"></a>Subscrição do Microsoft Azure (MS-AZR-0145P)

Aplicam-se as seguintes sintaxes quando o fornecedor de faturação tem uma subscrição microsoft Azure (MS-AZR-0145P).

| Método  | URI do pedido                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=azure&faturalineitemtype=billinglineitems&size={size}&offset={offset} HTTP/1.1  |
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=azure&invoicelineitemtype=usagelineitems&size={size}&offset={offset} HTTP/1.1  |

##### <a name="onetime"></a>OneTime

Aplicam-se as seguintes sintaxes quando o fornecedor de faturação é **o OneTime**. Isto inclui taxas para reservas Azure, software, planos Azure e produtos de mercado comercial.

| Método  | URI do pedido                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&size={size} HTTP/1.1  |
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems/onetime/billinglineitems&size={size}?seekOperation=Next                           |

#### <a name="previous-syntaxes"></a>Sintaxes anteriores

Se estiver a utilizar as seguintes sintaxes, certifique-se de que utiliza a sintaxe adequada para o seu caso de utilização.

*Com exceção das correções de erros, esta API já não está a ser atualizada.* Deve atualizar as suas aplicações para ligar para a única **API** em vez de **marketplace**. A **única API** fornece funcionalidade adicional e continuará a ser atualizada.

Você deve usar **uma vez** para consultar todos os itens de linha de consumo comercial em vez de **mercado**. Ou pode seguir os links na chamada de links de estimativa.

| Método | URI do pedido | Descrição do caso de utilização de sintaxe |
| ------ | ----------- | -------------------------------- |
| GET | [*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems/{billing-provider}/{fatura-line-item-type} HTTP/1.1                              | Pode utilizar esta sintaxe para devolver uma lista completa de todos os itens de linha para a fatura dada. |
| GET | [*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems/{billing-provider}/{fatura-line-item-type}?size={size}&offset={offset} HTTP/1.1  | Para faturas grandes, pode utilizar esta sintaxe com um tamanho especificado e uma compensação baseada em 0 para devolver uma lista de itens de linha paged. |
| GET | [*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems/OneTime/{fatura-line-item-type}?seekOperation=Next                               | Pode utilizar esta sintaxe para uma fatura com um valor de fornecedor de faturação do **OneTime** e definir **procurar a Cooperação** para a **Próxima** para obter a próxima página de itens da linha de fatura. |

##### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros URI e consulta ao criar o pedido.

| Nome                   | Tipo   | Necessário | Descrição                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| fatura id             | string | Yes      | Uma corda que identifica a fatura.                             |
| prestador de faturação       | string | Yes      | O fornecedor de faturação: "Office", "Azure", "OneTime". No legado, temos modelos de dados separados para as transações do Office & Azure. No entanto, o moderno tem um único modelo de dados em todas as transações filtradas através do valor "OneTime".            |
| tipo de artigo de linha de fatura | string | Yes      | O tipo de detalhe de fatura: "BillingLineItems", "UsageLineItems". |
| size                   | número | No       | O número máximo de itens para devolver. Tamanho máximo padrão = 2000    |
| offset                 | número | No       | O índice baseado em zero do primeiro item da primeira linha a devolver.            |
| procurarOperação          | cadeia (de carateres) | No       | Se **o fornecedor de faturação** for igual ao **OneTime,** desaperte a **procura De cooperação** igual a **Next** para obter a próxima página de itens da linha de fatura. |
| hasPartnerEarnedCredit | bool | No | O valor indicando se devolver os itens de linha com o parceiro ganhou crédito aplicado. Nota: este parâmetro só será aplicado quando o tipo de fornecedor de faturação for OneTime e o BillLineItemType for UsageLineItems. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedida, a resposta contém a recolha de detalhes do item da linha.

*Para o item de linha **ChargeType,** o valor **Compra** está mapeado para **New**. O valor **Reembolso** está mapeado para **cancelar.***

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="rest-request-response-examples"></a>Rest exemplos de resposta a pedidos

### <a name="request-response-example-1"></a>Exemplo de resposta a pedido 1

Neste exemplo, os detalhes são os seguintes:

- **BillingProvider**: **Escritório**
- **FaturaLineItemType**: **BillingLineItems**

#### <a name="request-example-1"></a>Pedido exemplo 1

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/1234000000/lineitems?provider=Office&nvoicelineitemtype=BillingLineItems&size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-1"></a>Exemplo de resposta 1

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 2,
    "items": [{
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "74221236-D09C-4870-AC1D-33E155E9AEBE",
            "customerName": "TSTAGIN1CUST190",
            "mpnId": 4391507,
            "tier2MpnId": -1,
            "orderId": "567735045559164136",
            "subscriptionId": "4KIKawEAAAAAAAEA",
            "syndicationPartnerSubscriptionNumber": "1F58ACD7-FE51-4705-9567-D009C9ADA150",
            "offerId": "AAA5B3F0-0EE2-431B-A42F-3F18F3C6D540",
            "durableOfferId": "2F707C7C-2433-49A5-A437-9CA7CF40D3EB",
            "offerName": "EXCHANGE ONLINE (PLAN 2)",
            "domainName": "TStagin1Cust190.onmicrosoft.com",
            "billingCycleType": "MONTHLY",
            "subscriptionName": "EXCHANGE ONLINE (PLAN 2)",
            "subscriptionDescription": "EXCHANGE ONLINE (PLAN 2)",
            "subscriptionStartDate": "2017-05-12T00:00:00",
            "subscriptionEndDate": "2018-06-10T00:00:00",
            "chargeStartDate": "2017-05-12T00:00:00",
            "chargeEndDate": "2017-06-09T00:00:00",
            "chargeType": "New",
            "unitPrice": 0.0,
            "quantity": 3,
            "amount": 0.0,
            "totalOtherDiscount": 0.0,
            "subtotal": 0.0,
            "tax": 0.0,
            "totalForCustomer": 0.0,
            "currency": "USD",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "office",
            "attributes": {
                "objectType": "LicenseBasedLineItem"
            }
        }, {
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "74221236-D09C-4870-AC1D-33E155E9AEBE",
            "customerName": "TSTAGIN1CUST190",
            "mpnId": 4391507,
            "tier2MpnId": -1,
            "orderId": "567735045564795186",
            "subscriptionId": "Ik4YawEAAAAAAAEA",
            "syndicationPartnerSubscriptionNumber": "D8A8F773-9D3E-4244-8797-3182075F09FA",
            "offerId": "618B53FE-9B99-428B-9745-F706AEAF3979",
            "durableOfferId": "69C67983-CF78-4102-83F6-3E5FD246864F",
            "offerName": "SHAREPOINT ONLINE (PLAN 2)",
            "domainName": "TStagin1Cust190.onmicrosoft.com",
            "billingCycleType": "MONTHLY",
            "subscriptionName": "SHAREPOINT ONLINE (PLAN 2)",
            "subscriptionDescription": "SHAREPOINT ONLINE (PLAN 2)",
            "subscriptionStartDate": "2017-05-13T00:00:00",
            "subscriptionEndDate": "2018-06-10T00:00:00",
            "chargeStartDate": "2017-05-13T00:00:00",
            "chargeEndDate": "2017-06-09T00:00:00",
            "chargeType": "New",
            "unitPrice": 0.0,
            "quantity": 1,
            "amount": 0.0,
            "totalOtherDiscount": 0.0,
            "subtotal": 0.0,
            "tax": 0.0,
            "totalForCustomer": 0.0,
            "currency": "USD",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "office",
            "attributes": {
                "objectType": "LicenseBasedLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/1234000000/lineitems?provider=Office&nvoicelineitemtype=BillingLineItems&size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/1234000000/lineitems?provider=Office&nvoicelineitemtype=BillingLineItems&size=2&offset=",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-2"></a>Exemplo de resposta a pedido 2

No exemplo seguinte, os detalhes são os seguintes:

- **BillingProvider**: **Azure**
- **FaturaLineItemType**: **BillingLineItems**

#### <a name="request-example-2"></a>Pedido exemplo 2

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=BillingLineItems&size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-2"></a>Exemplo de resposta 2

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 2,
    "items": [
        {
            "detailLineItemId": 1,
            "sku": "7UD-00001",
            "includedQuantity": 0,
            "overageQuantity": 745,
            "listPrice": 0.085,
            "currency": "USD",
            "pretaxCharges": 63.33,
            "taxAmount": 6.34,
            "postTaxTotal": 69.67,
            "pretaxEffectiveRate": 0.08500671,
            "postTaxEffectiveRate": 0.09351677,
            "chargeType": "Assess usage fee for current cycle",
            "invoiceLineItemType": "billing_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E000000",
            "partnerName": "TEST_TEST_Big foot consulting",
            "partnerBillableAccountId": "1010578050",
            "customerId": "65726577-c208-40fd-9735-8c85ac000000",
            "domainName": "600test.onmicrosoft.com",
            "customerCompanyName": "601 tests",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "87f4b92f-a490-485e-ad34-5b70cb000000",
            "subscriptionName": "Microsoft Azure",
            "subscriptionDescription": "Microsoft Azure",
            "billingCycleType": "Monthly",
            "orderId": "568297985427000000",
            "serviceName": "Azure App Service",
            "serviceType": "Standard Plan",
            "resourceGuid": "505db374-df8a-44df-9d8c-13c14b61dee1",
            "resourceName": "S1",
            "region": "",
            "consumedQuantity": 745,
            "chargeStartDate": "2019-08-02T00:00:00",
            "chargeEndDate": "2019-09-01T00:00:00",
            "unit": "1 Hour",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "UsageBasedLineItem"
            }
        },
        {
            "detailLineItemId": 1,
            "sku": "7UD-00001",
            "includedQuantity": 0,
            "overageQuantity": 0.000882,
            "listPrice": 0.0383,
            "currency": "USD",
            "pretaxCharges": 0,
            "taxAmount": 0,
            "postTaxTotal": 0,
            "pretaxEffectiveRate": 0,
            "postTaxEffectiveRate": 0,
            "chargeType": "Assess usage fee for current cycle",
            "invoiceLineItemType": "billing_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E87E26A",
            "partnerName": "TEST_TEST_Big foot consulting",
            "partnerBillableAccountId": "1010578050",
            "customerId": "65726577-c208-40fd-9735-8c85ac9cac68",
            "domainName": "600test.onmicrosoft.com",
            "customerCompanyName": "601 tests",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "87f4b92f-a490-485e-ad34-5b70cb000000",
            "subscriptionName": "Microsoft Azure",
            "subscriptionDescription": "Microsoft Azure",
            "billingCycleType": "Monthly",
            "orderId": "568297985427000000",
            "serviceName": "Storage",
            "serviceType": "Standard Page Blob",
            "resourceGuid": "d23a5753-ff85-4ddf-af28-8cc5cf2d3882",
            "resourceName": "LRS Data Stored",
            "region": "",
            "consumedQuantity": 0.000882,
            "chargeStartDate": "2019-08-02T00:00:00",
            "chargeEndDate": "2019-09-01T00:00:00",
            "unit": "1 GB/Month",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "UsageBasedLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=BillingLineItems&size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=BillingLineItems&size=2&offset=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-3"></a>Exemplo de resposta a pedido 3

No exemplo seguinte, os detalhes são os seguintes:

- **BillingProvider**: **Azure**
- **FaturaLineItemType**: **UsageLineItems**

#### <a name="request-example-3"></a>Pedido exemplo 3

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=UsageLineItems&size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-3"></a>Exemplo de resposta 3

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 2,
    "items": [
        {
            "customerBillableAccount": "1439508127",
            "usageDate": "2019-08-05T00:00:00",
            "invoiceLineItemType": "usage_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E000000",
            "partnerName": "TEST_TEST_BIG FOOT CONSULTING",
            "partnerBillableAccountId": "1010578050",
            "customerId": "9E9B71BA-3442-458B-B519-E1CCF72FBB54",
            "domainName": "test600.onmicrosoft.com",
            "customerCompanyName": "600 TEST",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "F9BA6DA0-6DAC-4F88-B623-313C9B9C117A",
            "subscriptionName": "MICROSOFT AZURE",
            "subscriptionDescription": "MICROSOFT AZURE",
            "billingCycleType": "MONTHLY",
            "orderId": "568297985577171353",
            "serviceName": "STORAGE",
            "serviceType": "STANDARD PAGE BLOB",
            "resourceGuid": "9CC63CF8-6593-410A-B0E7-26A4EF71E8B3",
            "resourceName": "DISK DELETE OPERATIONS",
            "region": "",
            "consumedQuantity": 2.9616,
            "chargeStartDate": "2019-08-05T00:00:00",
            "chargeEndDate": "2019-09-04T00:00:00",
            "unit": "10K",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "DailyUsageLineItem"
            }
        },
        {
            "customerBillableAccount": "1307536861",
            "usageDate": "2019-08-10T00:00:00",
            "invoiceLineItemType": "usage_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E000000",
            "partnerName": "TEST_TEST_BIG FOOT CONSULTING",
            "partnerBillableAccountId": "1010578050",
            "customerId": "EB53B7BD-267E-440E-B3C0-8F0B40000000",
            "domainName": "brandontest.onmicrosoft.com",
            "customerCompanyName": "BRANDON'S TEST",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "62D22561-AB15-41E5-AD59-99025C000000",
            "subscriptionName": "MICROSOFT AZURE",
            "subscriptionDescription": "MICROSOFT AZURE",
            "billingCycleType": "MONTHLY",
            "orderId": "568297985605838583",
            "serviceName": "VIRTUAL MACHINES",
            "serviceType": "D/DS SERIES WINDOWS",
            "resourceGuid": "62C64B6C-4033-4E20-AB33-9E81271AC12A",
            "resourceName": "D1/DS1",
            "region": "US WEST",
            "consumedQuantity": 24,
            "chargeStartDate": "2019-08-05T00:00:00",
            "chargeEndDate": "2019-09-04T00:00:00",
            "unit": "1 HOUR",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "DailyUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=UsageLineItems&size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=UsageLineItems&size=2&offset=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-4"></a>Exemplo de resposta a pedido 4

No exemplo seguinte, os detalhes são os seguintes:

- **BillingProvider**: **OneTime**
- **FaturaLineItemType**: **BillingLineItems**

#### <a name="request-example-4"></a>Pedido exemplo 4

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/G000024135/lineitems/OneTime/BillingLineItems?size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-4"></a>Exemplo de resposta 4

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

 {
    "continuationToken": "d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7",
    "totalCount": 2,
    "items": [
        {
            "partnerId": "6480d686-cfb4-424d-a945-6b9b9f000000",
            "customerId": "org:9060d13d-c5ed-482e-b059-a15a38000000",
            "customerName": "recipientCustomerName",
            "customerDomainName": "recipientCustomerDomain",
            "invoiceNumber": "1234000000",
            "quoteId": "abcd12345678",
            "mpnId": "4870137",
            "resellerMpnId": 0,
            "orderId": "QDOx5ZN3YR9uYhm4M1MGQJ_0nievUOrx1",
            "orderDate": "2018-02-08T22:31:42.9397946Z",
            "productId": "productid",
            "skuId": "skuid",
            "availabilityId": "availabilityid",
            "productName": "TEST PRODUCT",
            "skuName": "TEST SKU TITLE",
            "chargeType": "New",
            "unitPrice": 431.8,
            "effectiveUnitPrice": 496.07,
            "unitType": "Seats",
            "quantity": 1,
            "subtotal": 431.8,
            "taxTotal": 38.87,
            "totalForCustomer": 470.67,
            "currency": "USD",
            "providerName": "Test Networks Inc",
            "providerId": "12343810",
            "subscriptionDescription": "",
            "subscriptionId": "281e26fe-9ce7-415b-911c-f39232000000",
            "subscriptionStartDate": "2019-01-03T19:53:55.1292512+00:00",
            "subscriptionEndDate": "2019-02-02T19:53:55.1292512+00:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "1234278124b8",
            "priceAdjustmentDescription": "[\"100.0% Tier 1 Discount\"]",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-09-30T23:59:59Z",
            "billableQuantity": 0.0159369774,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "billingFrequency": "Monthly",
            "reservationOrderId": "883d475b-0000-2222-0000-8818752f1234",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        },
        {
            "partnerId": "6480d686-cfb4-424d-a945-6b9b9f4badc2",
            "customerId": "org:9060d13d-c5ed-482e-b059-a15a38cbb28e",
            "customerName": "recipientCustomerName",
            "customerDomainName": "recipientCustomerDomain",
            "invoiceNumber": "1234000000",
            "quoteId": "abcd12345678",
            "mpnId": "4870137",
            "resellerMpnId": 0,
            "orderId": "QDOx5ZN3YR9uYhm4M1MGQJ_0nievUOrx1",
            "orderDate": "2018-02-08T22:31:42.9397946Z",
            "productId": "productid",
            "skuId": "skuid",
            "availabilityId": "availabilityid",
            "productName": "TEST PRODUCT",
            "skuName": "TEST SKU TITLE",
            "chargeType": "New",
            "unitPrice": 26.35,
            "effectiveUnitPrice": 496.07,
            "unitType": "1 Hour",
            "quantity": 1,
            "subtotal": 26.35,
            "taxTotal": 2.37,
            "totalForCustomer": 28.72,
            "currency": "USD",
            "providerName": "Test Networks Inc",
            "providerId": "12343810",
            "subscriptionDescription": "",
            "subscriptionId": "281e26fe-9ce7-415b-911c-f39232ea904a",
            "subscriptionStartDate": "2019-01-03T19:53:55.1292512+00:00",
            "subscriptionEndDate": "2019-02-02T19:53:55.1292512+00:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "1234578124b8",
            "priceAdjustmentDescription": "[\"100.0% Tier 1 Discount\"]",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-09-30T23:59:59Z",
            "billableQuantity": 0.0130687981,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/G000024135/lineitems?provider=OneTime&nvoicelineitemtype=BillingLineItems&size=2",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/G000024135/lineitems?provider=OneTime&nvoicelineitemtype=BillingLineItems&size=2?seekOperation=Next",
            "method": "GET",
            "headers": [
                {
                    "key": "MS-ContinuationToken",
                    "value": "d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7"
                }
            ]
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-5"></a>Exemplo de resposta a pedido 5

No exemplo seguinte, há paging usando um token de continuação. Os detalhes são os seguintes:

- **BillingProvider**: **OneTime**
- **FaturaLineItemType**: **BillingLineItems**
- **SeekOperation**: **Seguinte**

#### <a name="request-example-5"></a>Pedido exemplo 5

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/G000024135/lineitems/OneTime/BillingLineItems?seekOperation=Next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-5"></a>Exemplo de resposta 5

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 1,
    "items": [
        {
            "partnerId": "6480d686-cfb4-424d-a945-6b9b9f000000",
            "customerId": "org:9060d13d-c5ed-482e-b059-a15a38000000",
            "customerName": "recipientCustomerName",
            "customerDomainName": "recipientCustomerDomain",
            "invoiceNumber": "1234000000",
            "quoteId": "abcd12345678",
            "mpnId": "4870137",
            "resellerMpnId": 0,
            "orderId": "NeqT31Kziwf8gkCXM9YQToWTqU-9Jbm81",
            "orderDate": "2018-02-08T22:31:47.1751688Z",
            "productId": "DZH318Z0BQ3P",
            "skuId": "001F",
            "availabilityId": "DZH318Z0DR0H",
            "productName": "Reserved VM Instance, Standard_D1, AP East, 3 years",
            "skuName": "D Series",
            "chargeType": "New",
            "unitPrice": 1447,
            "effectiveUnitPrice": 496.07,
            "unitType": "Seats",
            "quantity": 1,
            "subtotal": 1447,
            "taxTotal": 130.24,
            "totalForCustomer": 1577.24,
            "currency": "USD",
            "providerName": "Test Networks Inc",
            "providerId": "12343810",
            "subscriptionDescription": "",
            "subscriptionId": "281e26fe-9ce7-415b-911c-f39232000000",
            "subscriptionStartDate": "2019-01-03T19:53:55.1292512+00:00",
            "subscriptionEndDate": "2019-02-02T19:53:55.1292512+00:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "1234568124b8",
            "priceAdjustmentDescription": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-09-30T23:59:59Z",
            "billableQuantity": 0.0130687981,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "",
            "billingFrequency": "Monthly",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/G000024135/lineitems?provider=OneTime&nvoicelineitemtype=BillingLineItems&size=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
