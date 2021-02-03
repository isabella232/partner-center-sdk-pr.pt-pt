---
title: Obter uma coleção de faturas
description: Como recuperar uma coleção das faturas do parceiro.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: f56c3de8dd227f573921e5b969c2217c2f743a21
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769289"
---
# <a name="get-a-collection-of-invoices"></a><span data-ttu-id="db66a-103">Obter uma coleção de faturas</span><span class="sxs-lookup"><span data-stu-id="db66a-103">Get a collection of invoices</span></span>

<span data-ttu-id="db66a-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="db66a-104">**Applies To**</span></span>

- <span data-ttu-id="db66a-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="db66a-105">Partner Center</span></span>
- <span data-ttu-id="db66a-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="db66a-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="db66a-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="db66a-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="db66a-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="db66a-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="db66a-109">Como recuperar uma coleção das faturas do parceiro.</span><span class="sxs-lookup"><span data-stu-id="db66a-109">How to retrieve a collection of the partner's invoices.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="db66a-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="db66a-110">Prerequisites</span></span>

- <span data-ttu-id="db66a-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="db66a-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="db66a-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="db66a-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="db66a-113">C\#</span><span class="sxs-lookup"><span data-stu-id="db66a-113">C\#</span></span>

<span data-ttu-id="db66a-114">Para obter uma recolha de todas as faturas disponíveis, use a propriedade [**Faturas**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) para obter uma interface para as operações de faturação e, em seguida, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.getasync) para recuperar a coleção.</span><span class="sxs-lookup"><span data-stu-id="db66a-114">To get a collection of all available invoices, use the [**Invoices**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) property to get an interface to invoice operations, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.getasync) method to retrieve the collection.</span></span>

<span data-ttu-id="db66a-115">Para obter uma coleção de faturas em página, ligue primeiro para o método [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) e passe-o pelo tamanho da página para criar um objeto [**IQuery.**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery)</span><span class="sxs-lookup"><span data-stu-id="db66a-115">To get a paged collection of invoices, first call the [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) method and pass it the page size to create an [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object.</span></span> <span data-ttu-id="db66a-116">Em seguida, use a propriedade [**Faturas**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) para obter uma interface para operações de faturação, e em seguida, passar o objeto IQuery para o método [**Consulta**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.query) ou [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.queryasync) para enviar o pedido e obter a primeira página.</span><span class="sxs-lookup"><span data-stu-id="db66a-116">Next, use the [**Invoices**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) property to get an interface to invoice operations, and then pass the IQuery object to the [**Query**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.queryasync) method to send the request and get the first page.</span></span>

<span data-ttu-id="db66a-117">Em seguida, use a propriedade [**Enumeradores**](/dotnet/api/microsoft.store.partnercenter.ipartner.enumerators) para obter uma interface para a recolha de enumeradores de recolha de recursos suportados, e, em seguida, ligue [**para Faturas.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) para criar um enumerador para atravessar a recolha de faturas.</span><span class="sxs-lookup"><span data-stu-id="db66a-117">Next, use the [**Enumerators**](/dotnet/api/microsoft.store.partnercenter.ipartner.enumerators) property to get an interface to the collection of supported resource collection enumerators, and then call [**Invoices.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) to create an enumerator for traversing the collection of invoices.</span></span> <span data-ttu-id="db66a-118">Por fim, utilize o enumerador para recuperar e trabalhar com cada página de faturas, como mostra o seguinte exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="db66a-118">Finally, use the enumerator to retrieve and work with each page of invoices as shown in the following code example.</span></span> <span data-ttu-id="db66a-119">Cada chamada para o método [**Seguinte**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumerator-1.next) envia um pedido para a próxima página de faturas com base no tamanho da página.</span><span class="sxs-lookup"><span data-stu-id="db66a-119">Each call to the [**Next**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumerator-1.next) method sends a request for the next page of invoices based on the page size.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// int invoicePageSize;

// Is this an unpaged or paged request?
bool isUnpaged = (this.invoicePageSize <= 0);

// If the scenario is unpaged, get all the invoices, otherwise get the first page.
var invoicesPage = (isUnpaged)
                 ? partnerOperations.Invoices.Get()
                 : partnerOperations.Invoices.Query(QueryFactory.Instance.BuildIndexedQuery(this.invoicePageSize));

// Create an invoice enumerator for traversing the invoice pages.
var invoicesEnumerator = partnerOperations.Enumerators.Invoices.Create(invoicesPage);
int lineCounter = 1;

while (invoicesEnumerator.HasValue)
{
    // Print the current invoice results page.
    var invoices = invoicesEnumerator.Current.Items;

    foreach (var i in invoices)
    {
        Console.WriteLine(String.Format("{0,3}. {1}  {2}  {3,16:C2}",
            lineCounter++,
            i.Id,
            i.InvoiceDate.ToString("yyyy&#39;-&#39;MM&#39;-&#39;dd&#39;T&#39;HH&#39;:&#39;mm&#39;:&#39;ss&#39;Z&#39;"),
            i.TotalCharges));
    }

    Console.WriteLine();
    Console.Write("Press any key to retrieve the next invoices page");
    Console.ReadKey();

    // Get the next page of invoices.
    invoicesEnumerator.Next();
}
```

<span data-ttu-id="db66a-120">Para obter um exemplo ligeiramente diferente, consulte **sample**: [Console test app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="db66a-120">For a slightly different example, see **Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="db66a-121">**Projeto**: Partner Center SDK Samples **Class**: GetPagedInvoices.cs</span><span class="sxs-lookup"><span data-stu-id="db66a-121">**Project**: Partner Center SDK Samples **Class**: GetPagedInvoices.cs</span></span>

> [!NOTE] 
> <span data-ttu-id="db66a-122">A mesma API é utilizada para todas as compras comerciais modernas, bem como licenças de 145p e Office.</span><span class="sxs-lookup"><span data-stu-id="db66a-122">The same API is used for all modern commercial purchases as well as 145p and Office licenses.</span></span> <span data-ttu-id="db66a-123">O tamanho e a compensação são considerados apenas para faturas antigas.</span><span class="sxs-lookup"><span data-stu-id="db66a-123">Size and offset are only considered for legacy invoices.</span></span> <span data-ttu-id="db66a-124">Para todas as compras comerciais modernas, o pagesize & offset será ignorado.</span><span class="sxs-lookup"><span data-stu-id="db66a-124">For all modern commercial purchases, pagesize & offset will be ignored.</span></span>

## <a name="rest-request"></a><span data-ttu-id="db66a-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="db66a-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="db66a-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="db66a-126">Request syntax</span></span>

| <span data-ttu-id="db66a-127">Método</span><span class="sxs-lookup"><span data-stu-id="db66a-127">Method</span></span>  | <span data-ttu-id="db66a-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="db66a-128">Request URI</span></span>                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="db66a-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="db66a-129">**GET**</span></span> | <span data-ttu-id="db66a-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas?size={size}&offset={offset} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="db66a-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices?size={size}&offset={offset} HTTP/1.1</span></span>  |

### <a name="uri-parameters"></a><span data-ttu-id="db66a-131">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="db66a-131">URI parameters</span></span>

<span data-ttu-id="db66a-132">Utilize os seguintes parâmetros de consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="db66a-132">Use the following query parameters when creating the request.</span></span>

| <span data-ttu-id="db66a-133">Nome</span><span class="sxs-lookup"><span data-stu-id="db66a-133">Name</span></span>   | <span data-ttu-id="db66a-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="db66a-134">Type</span></span> | <span data-ttu-id="db66a-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="db66a-135">Required</span></span> | <span data-ttu-id="db66a-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="db66a-136">Description</span></span>                                                                            |
|--------|------|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="db66a-137">size</span><span class="sxs-lookup"><span data-stu-id="db66a-137">size</span></span>   | <span data-ttu-id="db66a-138">int</span><span class="sxs-lookup"><span data-stu-id="db66a-138">int</span></span>  | <span data-ttu-id="db66a-139">Não</span><span class="sxs-lookup"><span data-stu-id="db66a-139">No</span></span>       | <span data-ttu-id="db66a-140">O número de recursos de fatura para devolver na resposta.</span><span class="sxs-lookup"><span data-stu-id="db66a-140">The number of invoice resources to return in the response.</span></span> <span data-ttu-id="db66a-141">Este parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="db66a-141">This parameter is optional.</span></span> |
| <span data-ttu-id="db66a-142">offset</span><span class="sxs-lookup"><span data-stu-id="db66a-142">offset</span></span> | <span data-ttu-id="db66a-143">int</span><span class="sxs-lookup"><span data-stu-id="db66a-143">int</span></span>  | <span data-ttu-id="db66a-144">Não</span><span class="sxs-lookup"><span data-stu-id="db66a-144">No</span></span>       | <span data-ttu-id="db66a-145">O índice baseado em zero da primeira fatura a devolver.</span><span class="sxs-lookup"><span data-stu-id="db66a-145">The zero-based index of the first invoice to return.</span></span>                                   |

### <a name="request-headers"></a><span data-ttu-id="db66a-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="db66a-146">Request headers</span></span>

<span data-ttu-id="db66a-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="db66a-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="db66a-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="db66a-148">Request body</span></span>

<span data-ttu-id="db66a-149">Nenhum</span><span class="sxs-lookup"><span data-stu-id="db66a-149">None</span></span>

### <a name="request-example"></a><span data-ttu-id="db66a-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="db66a-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices?size=200&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="db66a-151">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="db66a-151">REST response</span></span>

<span data-ttu-id="db66a-152">Se for bem sucedido, o organismo de resposta contém a recolha de recursos da [Fatura.](invoice-resources.md#invoice)</span><span class="sxs-lookup"><span data-stu-id="db66a-152">If successful, the response body contains the collection of [Invoice](invoice-resources.md#invoice) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="db66a-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="db66a-153">Response success and error codes</span></span>

<span data-ttu-id="db66a-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="db66a-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="db66a-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="db66a-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="db66a-156">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="db66a-156">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="db66a-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="db66a-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 256
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
Date: Thu, 24 Mar 2016 05:21:01 GMT
{
    "totalCount": 2,
    "items": [
        {
            "id": "D02005YFHI",
            "invoiceDate": "2017-01-21T00:00:00Z",
            "totalCharges": 24606.35,
            "paidAmount": 1000,
            "currencyCode": "GBP",
            "currencySymbol": "£",
            "pdfDownloadLink": "/invoices/D02005YFHI/documents/statement",
            "taxReceipts": [
                {
                    "id": "123456",
                    "taxReceiptPdfDownloadLink": "/invoices/D02005YFHI/receipts/123456/documents/statement"
                }
            ],
            "invoiceDetails": [
                {
                    "invoiceLineItemType": "billing_line_items",
                    "billingProvider": "office",
                    "links": {
                        "self": {
                            "uri": "/invoices/Recurring-D02005YFHI/lineitems/Office/BillingLineItems",
                            "method": "GET",
                            "headers": []
                        }
                    },
                    "attributes": {
                        "objectType": "InvoiceDetail"
                    }
                }
            ],
            "documentType": "invoice",
            "invoiceType": "Recurring",
            "links": {
                "self": {
                    "uri": "/invoices/Recurring-D02005YFHI",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Invoice"
            }
        },
        {
            "id": "G000024130",
            "invoiceDate": "2018-02-08T01:22:47.603895Z",
            "totalCharges": 586366,
            "paidAmount": 0,
            "currencyCode": "CHF",
            "currencySymbol": "CHF",
            "pdfDownloadLink": "/invoices/G000024130/documents/statement",
            "taxReceipts": [
                {
                    "id": "234567",
                    "taxReceiptPdfDownloadLink": "/invoices/G000024130/receipts/234567/documents/statement"
                }
            ],
            "invoiceDetails": [
                {
                    "invoiceLineItemType": "billing_line_items",
                    "billingProvider": "one_time",
                    "links": {
                        "self": {
                            "uri": "/invoices/OneTime-G000024130/lineitems/OneTime/BillingLineItems",
                            "method": "GET",
                            "headers": []
                        }
                    },
                    "attributes": {
                        "objectType": "InvoiceDetail"
                    }
                }
            ],
            "amendments": [
                {
                    "id": "G000024131",
                    "invoiceDate": "2018-02-08T18:44:37.5381456Z",
                    "totalCharges": 107661.12,
                    "paidAmount": 0,
                    "currencyCode": "CHF",
                    "currencySymbol": "CHF",
                    "invoiceDetails": [
                        {
                            "invoiceLineItemType": "billing_line_items",
                            "billingProvider": "one_time",
                            "attributes": {
                                "objectType": "InvoiceDetail"
                            }
                        }
                    ],
                    "documentType": "adjustment_note",
                    "amendsOf": "G000024130",
                    "invoiceType": "OneTime",
                    "attributes": {
                        "objectType": "Invoice"
                    }
                }
            ],
            "documentType": "void_note",
            "invoiceType": "OneTime",
            "links": {
                "self": {
                    "uri": "/invoices/OneTime-G000024130",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Invoice"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices?size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices?size=2&offset=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
