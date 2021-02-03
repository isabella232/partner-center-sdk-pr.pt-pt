---
title: Obtenha fatura por ID
description: Recupera uma determinada fatura utilizando o ID da fatura.
ms.date: 06/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 17880265d06e8e5eaacc5470d83c49defd10ad51
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768719"
---
# <a name="get-invoice-by-id"></a><span data-ttu-id="8d98b-103">Obtenha fatura por ID</span><span class="sxs-lookup"><span data-stu-id="8d98b-103">Get invoice by ID</span></span>

<span data-ttu-id="8d98b-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="8d98b-104">**Applies to:**</span></span>

- <span data-ttu-id="8d98b-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="8d98b-105">Partner Center</span></span>
- <span data-ttu-id="8d98b-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="8d98b-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="8d98b-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="8d98b-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="8d98b-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8d98b-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8d98b-109">Recupera uma determinada fatura utilizando o ID da fatura.</span><span class="sxs-lookup"><span data-stu-id="8d98b-109">Retrieves a given invoice using the invoice ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d98b-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8d98b-110">Prerequisites</span></span>

- <span data-ttu-id="8d98b-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8d98b-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8d98b-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="8d98b-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="8d98b-113">Um ID de fatura válido.</span><span class="sxs-lookup"><span data-stu-id="8d98b-113">A valid Invoice ID.</span></span>

## <a name="c"></a><span data-ttu-id="8d98b-114">C\#</span><span class="sxs-lookup"><span data-stu-id="8d98b-114">C\#</span></span>

<span data-ttu-id="8d98b-115">Para obter uma fatura por ID:</span><span class="sxs-lookup"><span data-stu-id="8d98b-115">To get an invoice by ID:</span></span>

1. <span data-ttu-id="8d98b-116">Utilize a sua recolha **IPartner.Faturas** e ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="8d98b-116">Use your **IPartner.Invoices** collection and call the **ById()** method.</span></span>

2. <span data-ttu-id="8d98b-117">Ligue para os **métodos Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="8d98b-117">Call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoice = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Get();
```

<span data-ttu-id="8d98b-118">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="8d98b-118">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="8d98b-119">**Projeto**: PartnerSDK.FeatureSample **Class**: GetInvoice.cs</span><span class="sxs-lookup"><span data-stu-id="8d98b-119">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoice.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="8d98b-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="8d98b-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8d98b-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d98b-121">Request syntax</span></span>

| <span data-ttu-id="8d98b-122">Método</span><span class="sxs-lookup"><span data-stu-id="8d98b-122">Method</span></span>  | <span data-ttu-id="8d98b-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="8d98b-123">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="8d98b-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="8d98b-124">**GET**</span></span> | <span data-ttu-id="8d98b-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8d98b-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="8d98b-126">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="8d98b-126">URI parameter</span></span>

<span data-ttu-id="8d98b-127">Utilize o seguinte parâmetro de consulta para obter a fatura.</span><span class="sxs-lookup"><span data-stu-id="8d98b-127">Use the following query parameter to get the invoice.</span></span>

| <span data-ttu-id="8d98b-128">Nome</span><span class="sxs-lookup"><span data-stu-id="8d98b-128">Name</span></span>           | <span data-ttu-id="8d98b-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="8d98b-129">Type</span></span>       | <span data-ttu-id="8d98b-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="8d98b-130">Required</span></span> | <span data-ttu-id="8d98b-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d98b-131">Description</span></span>                                                                                        |
|----------------|------------|----------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8d98b-132">**fatura id**</span><span class="sxs-lookup"><span data-stu-id="8d98b-132">**invoice-id**</span></span> | <span data-ttu-id="8d98b-133">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="8d98b-133">**string**</span></span> | <span data-ttu-id="8d98b-134">Sim</span><span class="sxs-lookup"><span data-stu-id="8d98b-134">Yes</span></span>      | <span data-ttu-id="8d98b-135">O valor é um **id de fatura** que permite ao revendedor filtrar os resultados de uma determinada fatura.</span><span class="sxs-lookup"><span data-stu-id="8d98b-135">The value is an **invoice-id** that allows the reseller to filter the results for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8d98b-136">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="8d98b-136">Request headers</span></span>

<span data-ttu-id="8d98b-137">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8d98b-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8d98b-138">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="8d98b-138">Request body</span></span>

<span data-ttu-id="8d98b-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8d98b-139">None</span></span>

### <a name="request-example"></a><span data-ttu-id="8d98b-140">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="8d98b-140">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="8d98b-141">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="8d98b-141">REST response</span></span>

<span data-ttu-id="8d98b-142">Se for bem sucedido, este método devolve um recurso [de Fatura](invoice-resources.md#invoice) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="8d98b-142">If successful, this method returns an [Invoice](invoice-resources.md#invoice) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8d98b-143">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="8d98b-143">Response success and error codes</span></span>

<span data-ttu-id="8d98b-144">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="8d98b-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8d98b-145">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8d98b-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8d98b-146">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="8d98b-146">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8d98b-147">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="8d98b-147">Response example</span></span>

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
