---
title: Obter resumos de faturas
description: Pode utilizar um recurso de resumos de fatura para cada tipo de moeda para mostrar o saldo e os encargos totais de taxas recorrentes e pontuais.
ms.date: 09/24/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 82cd669117db72e1819d941f48f8ea69b2eddaec
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768714"
---
# <a name="get-invoice-summaries"></a><span data-ttu-id="c6889-103">Obter resumos de faturas</span><span class="sxs-lookup"><span data-stu-id="c6889-103">Get invoice summaries</span></span>

<span data-ttu-id="c6889-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="c6889-104">**Applies to:**</span></span>

- <span data-ttu-id="c6889-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="c6889-105">Partner Center</span></span>
- <span data-ttu-id="c6889-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="c6889-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="c6889-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="c6889-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="c6889-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c6889-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c6889-109">Pode utilizar as **FaturaSummaries** para recuperar um resumo da fatura que mostra o saldo e os encargos totais de encargos recorrentes e pontuais.</span><span class="sxs-lookup"><span data-stu-id="c6889-109">You can use the **InvoiceSummaries** to retrieve an invoice summary which shows the balance and total charges of both recurring and one-time charges.</span></span> <span data-ttu-id="c6889-110">O recurso **FaturaSummaries** contém um resumo da fatura para cada tipo de moeda.</span><span class="sxs-lookup"><span data-stu-id="c6889-110">The **InvoiceSummaries** resource contains an invoice summary for each currency type.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c6889-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c6889-111">Prerequisites</span></span>

- <span data-ttu-id="c6889-112">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c6889-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c6889-113">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="c6889-113">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="c6889-114">Um identificador de fatura válido.</span><span class="sxs-lookup"><span data-stu-id="c6889-114">A valid invoice identifier.</span></span>

## <a name="c"></a><span data-ttu-id="c6889-115">C\#</span><span class="sxs-lookup"><span data-stu-id="c6889-115">C\#</span></span>

<span data-ttu-id="c6889-116">Para recuperar uma coleção [**FaturaSummaries**](invoice-resources.md#invoicesummaries) que contenha um [**FaturaSummary**](invoice-resources.md#invoicesummary) para cada tipo de moeda:</span><span class="sxs-lookup"><span data-stu-id="c6889-116">To retrieve an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) collection that contains an [**InvoiceSummary**](invoice-resources.md#invoicesummary) for each currency type:</span></span>

1. <span data-ttu-id="c6889-117">Utilize a sua coleção **IAggregatePartner.Faturas** para ligar para a propriedade **Resumos.**</span><span class="sxs-lookup"><span data-stu-id="c6889-117">Use your **IAggregatePartner.Invoices** collection to call the **Summaries** property.</span></span>

2. <span data-ttu-id="c6889-118">Ligue para o método **Get().**</span><span class="sxs-lookup"><span data-stu-id="c6889-118">Call the **Get()** method.</span></span>
3. <span data-ttu-id="c6889-119">Para obter o saldo de um [**dado individual faturaSummary,**](invoice-resources.md#invoicesummary)aceda ao **imóvel BalanceAmount** para aquele membro da coleção.</span><span class="sxs-lookup"><span data-stu-id="c6889-119">To get the balance of an individual [**InvoiceSummary**](invoice-resources.md#invoicesummary), access the **BalanceAmount** property for that member of the collection.</span></span>

``` csharp
// IAggregatePartner scopedPartnerOperations;

// Get the invoice summaries collection.
var invoiceSummaries = scopedPartnerOperations.Invoices.Summaries.Get();

// Display the balance on the first invoice summary in the collection.
Console.Out.WriteLine("Current Account Balance:  {0:C}", invoiceSummaries[0].BalanceAmount);
```

<span data-ttu-id="c6889-120">Para obter mais informações, consulte o seguinte código de exemplo:</span><span class="sxs-lookup"><span data-stu-id="c6889-120">For more information, see the following example code:</span></span>

- <span data-ttu-id="c6889-121">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="c6889-121">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="c6889-122">Projeto: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="c6889-122">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="c6889-123">Classe: **GetInvoiceSummaries.cs**</span><span class="sxs-lookup"><span data-stu-id="c6889-123">Class: **GetInvoiceSummaries.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="c6889-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c6889-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c6889-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6889-125">Request syntax</span></span>

| <span data-ttu-id="c6889-126">Método</span><span class="sxs-lookup"><span data-stu-id="c6889-126">Method</span></span>  | <span data-ttu-id="c6889-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c6889-127">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="c6889-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="c6889-128">**GET**</span></span> | <span data-ttu-id="c6889-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/resumos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c6889-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summaries HTTP/1.1</span></span>     |

#### <a name="uri-parameter"></a><span data-ttu-id="c6889-130">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="c6889-130">URI parameter</span></span>

<span data-ttu-id="c6889-131">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c6889-131">None.</span></span>

### <a name="request-headers"></a><span data-ttu-id="c6889-132">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c6889-132">Request headers</span></span>

<span data-ttu-id="c6889-133">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c6889-133">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c6889-134">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="c6889-134">Request body</span></span>

<span data-ttu-id="c6889-135">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c6889-135">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c6889-136">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c6889-136">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/summaries HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="c6889-137">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c6889-137">REST response</span></span>

<span data-ttu-id="c6889-138">Se for bem sucedido, este método devolve um recurso [**FaturaSummaries**](invoice-resources.md#invoicesummaries) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="c6889-138">If successful, this method returns an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c6889-139">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c6889-139">Response success and error codes</span></span>

<span data-ttu-id="c6889-140">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c6889-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c6889-141">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c6889-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c6889-142">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c6889-142">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c6889-143">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="c6889-143">Response example</span></span>

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
