---
title: Obter declaração da fatura
description: Recupera uma declaração de fatura utilizando o ID da fatura.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: f0324916eb2efd9244530a53b1d7bb4abc0c8e6e
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549132"
---
# <a name="get-invoice-statement"></a><span data-ttu-id="fcfff-103">Obter declaração da fatura</span><span class="sxs-lookup"><span data-stu-id="fcfff-103">Get invoice statement</span></span>

<span data-ttu-id="fcfff-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fcfff-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fcfff-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fcfff-105">Prerequisites</span></span>

- <span data-ttu-id="fcfff-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fcfff-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fcfff-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="fcfff-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="fcfff-108">Um ID de fatura válido.</span><span class="sxs-lookup"><span data-stu-id="fcfff-108">A valid Invoice ID.</span></span>

## <a name="c"></a><span data-ttu-id="fcfff-109">C\#</span><span class="sxs-lookup"><span data-stu-id="fcfff-109">C\#</span></span>

<span data-ttu-id="fcfff-110">Para obter uma declaração de fatura por ID, use a sua recolha **IPartner.Faturas** e ligue para o método **ById()** usando o ID da fatura, em seguida, ligue para os métodos **documentos()** e **Statement()** para aceder à declaração de fatura.</span><span class="sxs-lookup"><span data-stu-id="fcfff-110">To get an invoice statement by ID, use your **IPartner.Invoices** collection and call the **ById()** method using the invoice ID, then call the **Documents()** and **Statement()** methods to access the invoice statement.</span></span> <span data-ttu-id="fcfff-111">Por fim, ligue para os métodos **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="fcfff-111">Finally, call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Documents.Statement.Get();
```

<span data-ttu-id="fcfff-112">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="fcfff-112">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="fcfff-113">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceStatement.cs</span><span class="sxs-lookup"><span data-stu-id="fcfff-113">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceStatement.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="fcfff-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="fcfff-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fcfff-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcfff-115">Request syntax</span></span>

| <span data-ttu-id="fcfff-116">Método</span><span class="sxs-lookup"><span data-stu-id="fcfff-116">Method</span></span>  | <span data-ttu-id="fcfff-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="fcfff-117">Request URI</span></span>                                                                                       |
|---------|---------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fcfff-118">**Obter**</span><span class="sxs-lookup"><span data-stu-id="fcfff-118">**GET**</span></span> | <span data-ttu-id="fcfff-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/documentos/declaração HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fcfff-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/documents/statement HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="fcfff-120">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="fcfff-120">URI parameter</span></span>

<span data-ttu-id="fcfff-121">Utilize o seguinte parâmetro de consulta para obter a declaração de fatura.</span><span class="sxs-lookup"><span data-stu-id="fcfff-121">Use the following query parameter to get the invoice statement.</span></span>

| <span data-ttu-id="fcfff-122">Nome</span><span class="sxs-lookup"><span data-stu-id="fcfff-122">Name</span></span>       | <span data-ttu-id="fcfff-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="fcfff-123">Type</span></span>       | <span data-ttu-id="fcfff-124">Necessário</span><span class="sxs-lookup"><span data-stu-id="fcfff-124">Required</span></span> | <span data-ttu-id="fcfff-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="fcfff-125">Description</span></span>                                                                                        |
|------------|------------|----------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fcfff-126">fatura id</span><span class="sxs-lookup"><span data-stu-id="fcfff-126">invoice-id</span></span> | <span data-ttu-id="fcfff-127">string</span><span class="sxs-lookup"><span data-stu-id="fcfff-127">string</span></span>     | <span data-ttu-id="fcfff-128">Yes</span><span class="sxs-lookup"><span data-stu-id="fcfff-128">Yes</span></span>      | <span data-ttu-id="fcfff-129">O valor é um id de fatura que permite ao revendedor filtrar os resultados de uma determinada fatura.</span><span class="sxs-lookup"><span data-stu-id="fcfff-129">The value is an invoice-id that allows the reseller to filter the results for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fcfff-130">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="fcfff-130">Request headers</span></span>

<span data-ttu-id="fcfff-131">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="fcfff-131">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fcfff-132">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="fcfff-132">Request body</span></span>

<span data-ttu-id="fcfff-133">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="fcfff-133">None</span></span>

### <a name="request-example"></a><span data-ttu-id="fcfff-134">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="fcfff-134">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="fcfff-135">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="fcfff-135">REST response</span></span>

<span data-ttu-id="fcfff-136">Se for bem sucedido, este método devolve um recurso [de Declaração de Fatura no](invoice-resources.md#invoicestatement) organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="fcfff-136">If successful, this method returns an [InvoiceStatement](invoice-resources.md#invoicestatement) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fcfff-137">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="fcfff-137">Response success and error codes</span></span>

<span data-ttu-id="fcfff-138">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="fcfff-138">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fcfff-139">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="fcfff-139">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fcfff-140">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="fcfff-140">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fcfff-141">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="fcfff-141">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 219753
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
Date: Thu, 24 Mar 2016 05:21:01 GMT

{
    _content    {System.Net.Http.ByteArrayContent}    System.Net.Http.HttpContent {System.Net.Http.ByteArrayContent}
    _content    {byte[219753]}    byte[]
    _headers    {Content-Type: application/pdf Content-Disposition: attachment; filename=Invoice_G000024132.pdf}
}
```
