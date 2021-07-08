---
title: Obter resumos de faturas
description: Pode utilizar um recurso de resumos de fatura para cada tipo de moeda para mostrar o saldo e os encargos totais de taxas recorrentes e pontuais.
ms.date: 09/24/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: fb6ff839c56c7b0b77a9904abf05d95ca0500b00
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549115"
---
# <a name="get-invoice-summaries"></a><span data-ttu-id="9e9b1-103">Obter resumos de faturas</span><span class="sxs-lookup"><span data-stu-id="9e9b1-103">Get invoice summaries</span></span>

<span data-ttu-id="9e9b1-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9e9b1-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9e9b1-105">Pode utilizar as **FaturaSummaries** para recuperar um resumo da fatura que mostre o saldo e os encargos totais de encargos recorrentes e pontuais.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-105">You can use the **InvoiceSummaries** to retrieve an invoice summary that shows the balance and total charges of both recurring and one-time charges.</span></span> <span data-ttu-id="9e9b1-106">O recurso **FaturaSummaries** contém um resumo da fatura para cada tipo de moeda.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-106">The **InvoiceSummaries** resource contains an invoice summary for each currency type.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e9b1-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9e9b1-107">Prerequisites</span></span>

- <span data-ttu-id="9e9b1-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9e9b1-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9e9b1-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="9e9b1-110">Um identificador de fatura válido.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-110">A valid invoice identifier.</span></span>

## <a name="c"></a><span data-ttu-id="9e9b1-111">C\#</span><span class="sxs-lookup"><span data-stu-id="9e9b1-111">C\#</span></span>

<span data-ttu-id="9e9b1-112">Para recuperar uma coleção [**FaturaSummaries**](invoice-resources.md#invoicesummaries) que contenha um [**FaturaSummary**](invoice-resources.md#invoicesummary) para cada tipo de moeda:</span><span class="sxs-lookup"><span data-stu-id="9e9b1-112">To retrieve an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) collection that contains an [**InvoiceSummary**](invoice-resources.md#invoicesummary) for each currency type:</span></span>

1. <span data-ttu-id="9e9b1-113">Utilize a sua coleção **IAggregatePartner.Faturas** para ligar para a propriedade **Resumos.**</span><span class="sxs-lookup"><span data-stu-id="9e9b1-113">Use your **IAggregatePartner.Invoices** collection to call the **Summaries** property.</span></span>

2. <span data-ttu-id="9e9b1-114">Ligue para o método **Get().**</span><span class="sxs-lookup"><span data-stu-id="9e9b1-114">Call the **Get()** method.</span></span>
3. <span data-ttu-id="9e9b1-115">Para obter o saldo de um [**dado individual faturaSummary,**](invoice-resources.md#invoicesummary)aceda ao **imóvel BalanceAmount** para aquele membro da coleção.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-115">To get the balance of an individual [**InvoiceSummary**](invoice-resources.md#invoicesummary), access the **BalanceAmount** property for that member of the collection.</span></span>

``` csharp
// IAggregatePartner scopedPartnerOperations;

// Get the invoice summaries collection.
var invoiceSummaries = scopedPartnerOperations.Invoices.Summaries.Get();

// Display the balance on the first invoice summary in the collection.
Console.Out.WriteLine("Current Account Balance:  {0:C}", invoiceSummaries[0].BalanceAmount);
```

<span data-ttu-id="9e9b1-116">Para obter mais informações, consulte o seguinte código de exemplo:</span><span class="sxs-lookup"><span data-stu-id="9e9b1-116">For more information, see the following example code:</span></span>

- <span data-ttu-id="9e9b1-117">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="9e9b1-117">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="9e9b1-118">Project: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="9e9b1-118">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="9e9b1-119">Classe: **GetInvoiceSummaries.cs**</span><span class="sxs-lookup"><span data-stu-id="9e9b1-119">Class: **GetInvoiceSummaries.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="9e9b1-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="9e9b1-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9e9b1-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e9b1-121">Request syntax</span></span>

| <span data-ttu-id="9e9b1-122">Método</span><span class="sxs-lookup"><span data-stu-id="9e9b1-122">Method</span></span>  | <span data-ttu-id="9e9b1-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="9e9b1-123">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="9e9b1-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="9e9b1-124">**GET**</span></span> | <span data-ttu-id="9e9b1-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/resumos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9e9b1-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summaries HTTP/1.1</span></span>     |

#### <a name="uri-parameter"></a><span data-ttu-id="9e9b1-126">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="9e9b1-126">URI parameter</span></span>

<span data-ttu-id="9e9b1-127">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-127">None.</span></span>

### <a name="request-headers"></a><span data-ttu-id="9e9b1-128">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="9e9b1-128">Request headers</span></span>

<span data-ttu-id="9e9b1-129">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9e9b1-129">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9e9b1-130">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="9e9b1-130">Request body</span></span>

<span data-ttu-id="9e9b1-131">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-131">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9e9b1-132">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="9e9b1-132">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/summaries HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="9e9b1-133">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="9e9b1-133">REST response</span></span>

<span data-ttu-id="9e9b1-134">Se for bem sucedido, este método devolve um recurso [**FaturaSummaries**](invoice-resources.md#invoicesummaries) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-134">If successful, this method returns an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9e9b1-135">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="9e9b1-135">Response success and error codes</span></span>

<span data-ttu-id="9e9b1-136">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9e9b1-137">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="9e9b1-137">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9e9b1-138">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="9e9b1-138">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9e9b1-139">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="9e9b1-139">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 256
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
Date: Thu, 24 Mar 2016 05:21:01 GMT

{
    "totalCount": 3,
    "items": [
        {
            "balanceAmount": 751094.39,
            "currencyCode": "GBP",
            "currencySymbol": "£",
            "accountingDate": "2018-03-16T00:00:00",
            "firstInvoiceCreationDate": "2017-01-21T00:00:00Z",
            "lastPaymentDate": "2017-01-01T12:00:00Z",
            "lastPaymentAmount": 1000,
            "latestInvoiceDate": "2018-03-16T00:00:00",
            "details": [
                {
                    "invoiceType": "Recurring",
                    "summary": {
                        "balanceAmount": 202955.87,
                        "currencyCode": "GBP",
                        "currencySymbol": "£",
                        "accountingDate": "2017-02-27T00:00:00Z",
                        "firstInvoiceCreationDate": "2017-01-21T00:00:00Z",
                        "lastPaymentDate": "2017-01-01T12:00:00Z",
                        "lastPaymentAmount": 1000,
                        "latestInvoiceDate": "0001-01-01T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                },
                {
                    "invoiceType": "OneTime",
                    "summary": {
                        "balanceAmount": 548138.52,
                        "currencyCode": "GBP",
                        "currencySymbol": "£",
                        "accountingDate": "2018-03-16T00:00:00",
                        "firstInvoiceCreationDate": "2018-03-16T00:00:00",
                        "lastPaymentDate": "0001-01-01T00:00:00",
                        "lastPaymentAmount": 0,
                        "latestInvoiceDate": "2018-03-16T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                }
            ],
            "links": {
                "self": {
                    "uri": "/invoices/summary",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceSummary"
            }
        },
        {
            "balanceAmount": 1230.33,
            "currencyCode": "CHF",
            "currencySymbol": "CHF",
            "accountingDate": "2018-03-16T00:00:00",
            "firstInvoiceCreationDate": "2018-03-16T00:00:00",
            "lastPaymentDate": "0001-01-01T00:00:00",
            "lastPaymentAmount": 0,
            "latestInvoiceDate": "2018-03-16T00:00:00",
            "details": [
                {
                    "invoiceType": "OneTime",
                    "summary": {
                        "balanceAmount": 1230.33,
                        "currencyCode": "CHF",
                        "currencySymbol": "CHF",
                        "accountingDate": "2018-03-16T00:00:00",
                        "firstInvoiceCreationDate": "2018-03-16T00:00:00",
                        "lastPaymentDate": "0001-01-01T00:00:00",
                        "lastPaymentAmount": 0,
                        "latestInvoiceDate": "2018-03-16T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                }
            ],
            "links": {
                "self": {
                    "uri": "/invoices/summary",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceSummary"
            }
        },
        {
            "balanceAmount": 1001.12,
            "currencyCode": "EUR",
            "currencySymbol": "€",
            "accountingDate": "2018-03-16T00:00:00",
            "firstInvoiceCreationDate": "2018-03-16T00:00:00",
            "lastPaymentDate": "0001-01-01T00:00:00",
            "lastPaymentAmount": 0,
            "latestInvoiceDate": "2018-03-16T00:00:00",
            "details": [
                {
                    "invoiceType": "OneTime",
                    "summary": {
                        "balanceAmount": 1001.12,
                        "currencyCode": "EUR",
                        "currencySymbol": "€",
                        "accountingDate": "2018-03-16T00:00:00",
                        "firstInvoiceCreationDate": "2018-03-16T00:00:00",
                        "lastPaymentDate": "0001-01-01T00:00:00",
                        "lastPaymentAmount": 0,
                        "latestInvoiceDate": "2018-03-16T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                }
            ],
            "links": {
                "self": {
                    "uri": "/invoices/summary",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceSummary"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/summaries",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
