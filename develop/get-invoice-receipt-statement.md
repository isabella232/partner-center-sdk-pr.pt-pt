---
title: Obter declaração do recibo da fatura
description: Recupera uma declaração de recibo de fatura usando o ID da fatura e o ID do recibo.
ms.date: 02/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 96cef11d6778de2d9bf28e466d88a39f9415727d
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768713"
---
# <a name="get-invoice-receipt-statement"></a><span data-ttu-id="d3116-103">Obter declaração do recibo da fatura</span><span class="sxs-lookup"><span data-stu-id="d3116-103">Get invoice receipt statement</span></span>

<span data-ttu-id="d3116-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="d3116-104">**Applies To**</span></span>

- <span data-ttu-id="d3116-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="d3116-105">Partner Center</span></span>

<span data-ttu-id="d3116-106">Recupera uma declaração de recibo de fatura usando o ID da fatura e o ID do recibo.</span><span class="sxs-lookup"><span data-stu-id="d3116-106">Retrieves an invoice receipt statement using invoice ID and the receipt ID.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3116-107">Esta funcionalidade aplica-se apenas às receitas fiscais de Taiwan.</span><span class="sxs-lookup"><span data-stu-id="d3116-107">This feature is only applicable to Taiwan tax receipts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3116-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d3116-108">Prerequisites</span></span>

- <span data-ttu-id="d3116-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d3116-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d3116-110">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="d3116-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="d3116-111">Um ID de fatura válido e um documento de recibo correspondente.</span><span class="sxs-lookup"><span data-stu-id="d3116-111">A valid Invoice ID and a corresponding receipt ID.</span></span>

## <a name="c"></a><span data-ttu-id="d3116-112">C\#</span><span class="sxs-lookup"><span data-stu-id="d3116-112">C\#</span></span>

<span data-ttu-id="d3116-113">Para obter uma declaração de recibo de fatura por ID, a começar pelo Partner Center SDK v1.12.0, utilize a sua coleção **IPartner.Faturas** e ligue para o método **ById()** utilizando o ID da fatura, depois ligue para a recolha **de Recibos** e ligue para o **ById()** e ligue para os **métodos de documentos()** e **declaração()** para aceder à declaração de recibo de fatura.</span><span class="sxs-lookup"><span data-stu-id="d3116-113">To get an invoice receipt statement by ID, starting with Partner Center SDK v1.12.0, use your **IPartner.Invoices** collection and call the **ById()** method using the invoice ID, then call the **Receipts** collection and call **ById()** then call the **Documents()** and **Statement()** methods to access the invoice receipt statement.</span></span> <span data-ttu-id="d3116-114">Por fim, ligue para os métodos **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="d3116-114">Finally, call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Receipts.ById(selectedReceipt).Documents.Statement.Get();
```

<span data-ttu-id="d3116-115">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d3116-115">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d3116-116">**Projeto**: PartnerSDK.FeatureSample **Class**: GetInvoiceReceiptStatement.cs</span><span class="sxs-lookup"><span data-stu-id="d3116-116">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceReceiptStatement.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="d3116-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d3116-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d3116-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3116-118">Request syntax</span></span>

| <span data-ttu-id="d3116-119">Método</span><span class="sxs-lookup"><span data-stu-id="d3116-119">Method</span></span>  | <span data-ttu-id="d3116-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d3116-120">Request URI</span></span>                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d3116-121">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d3116-121">**GET**</span></span> | <span data-ttu-id="d3116-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/recibos/{recibo-id}/documentos/declaração HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d3116-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/receipts/{receipt-id}/documents/statement HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="d3116-123">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="d3116-123">URI parameter</span></span>

<span data-ttu-id="d3116-124">Utilize o seguinte parâmetro de consulta para obter a declaração de recibo de fatura.</span><span class="sxs-lookup"><span data-stu-id="d3116-124">Use the following query parameter to get the invoice receipt statement.</span></span>

| <span data-ttu-id="d3116-125">Nome</span><span class="sxs-lookup"><span data-stu-id="d3116-125">Name</span></span>       | <span data-ttu-id="d3116-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="d3116-126">Type</span></span>   | <span data-ttu-id="d3116-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="d3116-127">Required</span></span> | <span data-ttu-id="d3116-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3116-128">Description</span></span>                                                                                    |
|------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d3116-129">fatura id</span><span class="sxs-lookup"><span data-stu-id="d3116-129">invoice-id</span></span> | <span data-ttu-id="d3116-130">string</span><span class="sxs-lookup"><span data-stu-id="d3116-130">string</span></span> | <span data-ttu-id="d3116-131">Sim</span><span class="sxs-lookup"><span data-stu-id="d3116-131">Yes</span></span>      | <span data-ttu-id="d3116-132">O valor é um id de fatura que permite ao revendedor filtrar os resultados de uma determinada fatura.</span><span class="sxs-lookup"><span data-stu-id="d3116-132">The value is an invoice-id that allows the reseller to filter the results for a given invoice.</span></span> |
| <span data-ttu-id="d3116-133">recibo id</span><span class="sxs-lookup"><span data-stu-id="d3116-133">receipt-id</span></span> | <span data-ttu-id="d3116-134">string</span><span class="sxs-lookup"><span data-stu-id="d3116-134">string</span></span> | <span data-ttu-id="d3116-135">Sim</span><span class="sxs-lookup"><span data-stu-id="d3116-135">Yes</span></span>      | <span data-ttu-id="d3116-136">O valor é um recibo-id que permite ao revendedor filtrar os recibos de uma determinada fatura.</span><span class="sxs-lookup"><span data-stu-id="d3116-136">The value is a receipt-id that allows the reseller to filter the receipts for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d3116-137">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d3116-137">Request headers</span></span>

<span data-ttu-id="d3116-138">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d3116-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d3116-139">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d3116-139">Request body</span></span>

<span data-ttu-id="d3116-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d3116-140">None</span></span>

### <a name="request-example"></a><span data-ttu-id="d3116-141">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d3116-141">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/receipts/<receipt-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="d3116-142">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d3116-142">REST response</span></span>

<span data-ttu-id="d3116-143">Se for bem sucedido, este método devolve um fluxo pdf no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="d3116-143">If successful, this method returns a pdf stream in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d3116-144">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d3116-144">Response success and error codes</span></span>

<span data-ttu-id="d3116-145">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d3116-145">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d3116-146">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d3116-146">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d3116-147">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d3116-147">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d3116-148">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d3116-148">Response example</span></span>

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
