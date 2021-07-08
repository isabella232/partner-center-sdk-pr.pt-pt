---
title: Obtenha fatura por ID
description: Recupera uma determinada fatura utilizando o ID da fatura.
ms.date: 06/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: c888786a6b6ca941629bb7aac95227021c37a7fc
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549166"
---
# <a name="get-invoice-by-id"></a><span data-ttu-id="2ab8b-103">Obtenha fatura por ID</span><span class="sxs-lookup"><span data-stu-id="2ab8b-103">Get invoice by ID</span></span>

<span data-ttu-id="2ab8b-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2ab8b-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2ab8b-105">Recupera uma determinada fatura utilizando o ID da fatura.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-105">Retrieves a given invoice using the invoice ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ab8b-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2ab8b-106">Prerequisites</span></span>

- <span data-ttu-id="2ab8b-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2ab8b-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2ab8b-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="2ab8b-109">Um ID de fatura válido.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-109">A valid Invoice ID.</span></span>

## <a name="c"></a><span data-ttu-id="2ab8b-110">C\#</span><span class="sxs-lookup"><span data-stu-id="2ab8b-110">C\#</span></span>

<span data-ttu-id="2ab8b-111">Para obter uma fatura por ID:</span><span class="sxs-lookup"><span data-stu-id="2ab8b-111">To get an invoice by ID:</span></span>

1. <span data-ttu-id="2ab8b-112">Utilize a sua recolha **IPartner.Faturas** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="2ab8b-112">Use your **IPartner.Invoices** collection and call the **ById()** method.</span></span>

2. <span data-ttu-id="2ab8b-113">Ligue para os **métodos Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="2ab8b-113">Call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoice = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Get();
```

<span data-ttu-id="2ab8b-114">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="2ab8b-114">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="2ab8b-115">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoice.cs</span><span class="sxs-lookup"><span data-stu-id="2ab8b-115">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoice.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="2ab8b-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2ab8b-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2ab8b-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ab8b-117">Request syntax</span></span>

| <span data-ttu-id="2ab8b-118">Método</span><span class="sxs-lookup"><span data-stu-id="2ab8b-118">Method</span></span>  | <span data-ttu-id="2ab8b-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2ab8b-119">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="2ab8b-120">**Obter**</span><span class="sxs-lookup"><span data-stu-id="2ab8b-120">**GET**</span></span> | <span data-ttu-id="2ab8b-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2ab8b-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="2ab8b-122">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="2ab8b-122">URI parameter</span></span>

<span data-ttu-id="2ab8b-123">Utilize o seguinte parâmetro de consulta para obter a fatura.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-123">Use the following query parameter to get the invoice.</span></span>

| <span data-ttu-id="2ab8b-124">Nome</span><span class="sxs-lookup"><span data-stu-id="2ab8b-124">Name</span></span>           | <span data-ttu-id="2ab8b-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="2ab8b-125">Type</span></span>       | <span data-ttu-id="2ab8b-126">Necessário</span><span class="sxs-lookup"><span data-stu-id="2ab8b-126">Required</span></span> | <span data-ttu-id="2ab8b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ab8b-127">Description</span></span>                                                                                        |
|----------------|------------|----------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ab8b-128">**fatura id**</span><span class="sxs-lookup"><span data-stu-id="2ab8b-128">**invoice-id**</span></span> | <span data-ttu-id="2ab8b-129">**string**</span><span class="sxs-lookup"><span data-stu-id="2ab8b-129">**string**</span></span> | <span data-ttu-id="2ab8b-130">Yes</span><span class="sxs-lookup"><span data-stu-id="2ab8b-130">Yes</span></span>      | <span data-ttu-id="2ab8b-131">O valor é um **id de fatura** que permite ao revendedor filtrar os resultados de uma determinada fatura.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-131">The value is an **invoice-id** that allows the reseller to filter the results for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2ab8b-132">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2ab8b-132">Request headers</span></span>

<span data-ttu-id="2ab8b-133">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2ab8b-133">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2ab8b-134">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="2ab8b-134">Request body</span></span>

<span data-ttu-id="2ab8b-135">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="2ab8b-135">None</span></span>

### <a name="request-example"></a><span data-ttu-id="2ab8b-136">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="2ab8b-136">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="2ab8b-137">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2ab8b-137">REST response</span></span>

<span data-ttu-id="2ab8b-138">Se for bem sucedido, este método devolve um recurso [de Fatura](invoice-resources.md#invoice) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-138">If successful, this method returns an [Invoice](invoice-resources.md#invoice) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2ab8b-139">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2ab8b-139">Response success and error codes</span></span>

<span data-ttu-id="2ab8b-140">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2ab8b-141">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2ab8b-142">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2ab8b-142">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2ab8b-143">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="2ab8b-143">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 676
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
Date: Thu, 24 Mar 2016 05:22:14 GMT

{
    "id": "G000024135",
    "invoiceDate": "2018-02-08T22:40:37.5897767Z",
    "billingPeriodStartDate": "2018-02-01T22:40:37.5897767Z",
    "billingPeriodEndDate": "2018-02-28T22:40:37.5897767Z",
    "totalCharges": 2076.63,
    "paidAmount": 0,
    "currencyCode": "USD",
    "currencySymbol": "$",
    "pdfDownloadLink": "/invoices/G000024135/documents/statement",
    "taxReceipts": [
        {
            "id": "123456",
            "taxReceiptPdfDownloadLink": "/invoices/G000024135/receipts/123456/documents/statement"
        }
    ],
    "invoiceDetails": [
        {
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "links": {
                "self": {
                    "uri": "/invoices/OneTime-G000024135/lineitems/OneTime/BillingLineItems",
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
    "invoiceType": "OneTime",
    "links": {
        "self": {
            "uri": "/invoices/OneTime-G000024135",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Invoice"
    }
}
```
