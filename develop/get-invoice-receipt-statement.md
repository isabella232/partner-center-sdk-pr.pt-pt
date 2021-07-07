---
title: Obter declaração do recibo da fatura
description: Recupera uma declaração de recibo de fatura usando o ID da fatura e o ID do recibo.
ms.date: 02/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: dcac4c8f0b881409dcad3560eefb82d4bb5e877a
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446134"
---
# <a name="get-invoice-receipt-statement"></a><span data-ttu-id="cee8b-103">Obter declaração do recibo da fatura</span><span class="sxs-lookup"><span data-stu-id="cee8b-103">Get invoice receipt statement</span></span>

<span data-ttu-id="cee8b-104">Recupera uma declaração de recibo de fatura usando o ID da fatura e o ID do recibo.</span><span class="sxs-lookup"><span data-stu-id="cee8b-104">Retrieves an invoice receipt statement using invoice ID and the receipt ID.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cee8b-105">Esta funcionalidade aplica-se apenas às receitas fiscais de Taiwan.</span><span class="sxs-lookup"><span data-stu-id="cee8b-105">This feature is only applicable to Taiwan tax receipts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cee8b-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="cee8b-106">Prerequisites</span></span>

- <span data-ttu-id="cee8b-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cee8b-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cee8b-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="cee8b-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="cee8b-109">Um ID de fatura válido e um documento de recibo correspondente.</span><span class="sxs-lookup"><span data-stu-id="cee8b-109">A valid Invoice ID and a corresponding receipt ID.</span></span>

## <a name="c"></a><span data-ttu-id="cee8b-110">C\#</span><span class="sxs-lookup"><span data-stu-id="cee8b-110">C\#</span></span>

<span data-ttu-id="cee8b-111">Para obter uma declaração de recibo de fatura por ID, a começar pelo Partner Center SDK v1.12.0, utilize a sua coleção **IPartner.Faturas** e ligue para o método **ById()** utilizando o ID da fatura, depois ligue para a recolha **de Recibos** e ligue para o **ById()** e ligue para os **métodos de documentos()** e **declaração()** para aceder à declaração de recibo de fatura.</span><span class="sxs-lookup"><span data-stu-id="cee8b-111">To get an invoice receipt statement by ID, starting with Partner Center SDK v1.12.0, use your **IPartner.Invoices** collection and call the **ById()** method using the invoice ID, then call the **Receipts** collection and call **ById()** then call the **Documents()** and **Statement()** methods to access the invoice receipt statement.</span></span> <span data-ttu-id="cee8b-112">Por fim, ligue para os métodos **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="cee8b-112">Finally, call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Receipts.ById(selectedReceipt).Documents.Statement.Get();
```

<span data-ttu-id="cee8b-113">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cee8b-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cee8b-114">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceReceiptStatement.cs</span><span class="sxs-lookup"><span data-stu-id="cee8b-114">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceReceiptStatement.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="cee8b-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="cee8b-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cee8b-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="cee8b-116">Request syntax</span></span>

| <span data-ttu-id="cee8b-117">Método</span><span class="sxs-lookup"><span data-stu-id="cee8b-117">Method</span></span>  | <span data-ttu-id="cee8b-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="cee8b-118">Request URI</span></span>                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cee8b-119">**Obter**</span><span class="sxs-lookup"><span data-stu-id="cee8b-119">**GET**</span></span> | <span data-ttu-id="cee8b-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/recibos/{recibo-id}/documentos/declaração HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="cee8b-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/receipts/{receipt-id}/documents/statement HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="cee8b-121">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="cee8b-121">URI parameter</span></span>

<span data-ttu-id="cee8b-122">Utilize o seguinte parâmetro de consulta para obter a declaração de recibo de fatura.</span><span class="sxs-lookup"><span data-stu-id="cee8b-122">Use the following query parameter to get the invoice receipt statement.</span></span>

| <span data-ttu-id="cee8b-123">Nome</span><span class="sxs-lookup"><span data-stu-id="cee8b-123">Name</span></span>       | <span data-ttu-id="cee8b-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="cee8b-124">Type</span></span>   | <span data-ttu-id="cee8b-125">Necessário</span><span class="sxs-lookup"><span data-stu-id="cee8b-125">Required</span></span> | <span data-ttu-id="cee8b-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="cee8b-126">Description</span></span>                                                                                    |
|------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cee8b-127">fatura id</span><span class="sxs-lookup"><span data-stu-id="cee8b-127">invoice-id</span></span> | <span data-ttu-id="cee8b-128">string</span><span class="sxs-lookup"><span data-stu-id="cee8b-128">string</span></span> | <span data-ttu-id="cee8b-129">Yes</span><span class="sxs-lookup"><span data-stu-id="cee8b-129">Yes</span></span>      | <span data-ttu-id="cee8b-130">O valor é um id de fatura que permite ao revendedor filtrar os resultados de uma determinada fatura.</span><span class="sxs-lookup"><span data-stu-id="cee8b-130">The value is an invoice-id that allows the reseller to filter the results for a given invoice.</span></span> |
| <span data-ttu-id="cee8b-131">recibo id</span><span class="sxs-lookup"><span data-stu-id="cee8b-131">receipt-id</span></span> | <span data-ttu-id="cee8b-132">string</span><span class="sxs-lookup"><span data-stu-id="cee8b-132">string</span></span> | <span data-ttu-id="cee8b-133">Yes</span><span class="sxs-lookup"><span data-stu-id="cee8b-133">Yes</span></span>      | <span data-ttu-id="cee8b-134">O valor é um recibo-id que permite ao revendedor filtrar os recibos de uma determinada fatura.</span><span class="sxs-lookup"><span data-stu-id="cee8b-134">The value is a receipt-id that allows the reseller to filter the receipts for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cee8b-135">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="cee8b-135">Request headers</span></span>

<span data-ttu-id="cee8b-136">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cee8b-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cee8b-137">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="cee8b-137">Request body</span></span>

<span data-ttu-id="cee8b-138">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="cee8b-138">None</span></span>

### <a name="request-example"></a><span data-ttu-id="cee8b-139">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="cee8b-139">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/receipts/<receipt-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="cee8b-140">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="cee8b-140">REST response</span></span>

<span data-ttu-id="cee8b-141">Se for bem sucedido, este método devolve um fluxo pdf no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="cee8b-141">If successful, this method returns a pdf stream in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cee8b-142">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="cee8b-142">Response success and error codes</span></span>

<span data-ttu-id="cee8b-143">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="cee8b-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cee8b-144">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="cee8b-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cee8b-145">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="cee8b-145">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cee8b-146">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="cee8b-146">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 195556
Content-Type: application/pdf
MS-CorrelationId: a1d6ab41-5a30-4643-898b-b30d65d3a0a1
MS-RequestId: cc1ba6db-ab26-404a-9196-712b6395f518
Date: Tue, 05 Feb 2019 04:08:23 GMT

{
    _content    {System.Net.Http.ByteArrayContent}    System.Net.Http.HttpContent {System.Net.Http.ByteArrayContent}
    _content    {byte[195556]}    byte[]
    _headers    {Content-Type: application/pdf Content-Disposition: attachment; filename=E-Tax-8602768.pdf}
}
```
