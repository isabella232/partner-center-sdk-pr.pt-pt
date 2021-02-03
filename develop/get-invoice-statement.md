---
title: Obter declaração da fatura
description: Recupera uma declaração de fatura utilizando o ID da fatura.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 42e5201919eea5644da463dfe2584c8d55002083
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769014"
---
# <a name="get-invoice-statement"></a><span data-ttu-id="5b3eb-103">Obter declaração da fatura</span><span class="sxs-lookup"><span data-stu-id="5b3eb-103">Get invoice statement</span></span>

<span data-ttu-id="5b3eb-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="5b3eb-104">**Applies To**</span></span>

- <span data-ttu-id="5b3eb-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="5b3eb-105">Partner Center</span></span>
- <span data-ttu-id="5b3eb-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="5b3eb-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="5b3eb-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="5b3eb-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="5b3eb-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5b3eb-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5b3eb-109">Recupera uma declaração de fatura utilizando o ID da fatura.</span><span class="sxs-lookup"><span data-stu-id="5b3eb-109">Retrieves an invoice statement using the invoice ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5b3eb-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5b3eb-110">Prerequisites</span></span>

- <span data-ttu-id="5b3eb-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5b3eb-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5b3eb-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="5b3eb-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="5b3eb-113">Um ID de fatura válido.</span><span class="sxs-lookup"><span data-stu-id="5b3eb-113">A valid Invoice ID.</span></span>

## <a name="c"></a><span data-ttu-id="5b3eb-114">C\#</span><span class="sxs-lookup"><span data-stu-id="5b3eb-114">C\#</span></span>

<span data-ttu-id="5b3eb-115">Para obter uma declaração de fatura por ID, use a sua recolha **IPartner.Faturas** e ligue para o método **ById()** usando o ID da fatura, em seguida, ligue para os métodos **documentos()** e **Statement()** para aceder à declaração de fatura.</span><span class="sxs-lookup"><span data-stu-id="5b3eb-115">To get an invoice statement by ID, use your **IPartner.Invoices** collection and call the **ById()** method using the invoice ID, then call the **Documents()** and **Statement()** methods to access the invoice statement.</span></span> <span data-ttu-id="5b3eb-116">Por fim, ligue para os métodos **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="5b3eb-116">Finally, call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Documents.Statement.Get();
```

<span data-ttu-id="5b3eb-117">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="5b3eb-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="5b3eb-118">**Projeto**: PartnerSDK.FeatureSample **Class**: GetInvoiceStatement.cs</span><span class="sxs-lookup"><span data-stu-id="5b3eb-118">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceStatement.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="5b3eb-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5b3eb-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5b3eb-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b3eb-120">Request syntax</span></span>

| <span data-ttu-id="5b3eb-121">Método</span><span class="sxs-lookup"><span data-stu-id="5b3eb-121">Method</span></span>  | <span data-ttu-id="5b3eb-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5b3eb-122">Request URI</span></span>                                                                                       |
|---------|---------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5b3eb-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="5b3eb-123">**GET**</span></span> | <span data-ttu-id="5b3eb-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/documentos/declaração HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5b3eb-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/documents/statement HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="5b3eb-125">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="5b3eb-125">URI parameter</span></span>

<span data-ttu-id="5b3eb-126">Utilize o seguinte parâmetro de consulta para obter a declaração de fatura.</span><span class="sxs-lookup"><span data-stu-id="5b3eb-126">Use the following query parameter to get the invoice statement.</span></span>

| <span data-ttu-id="5b3eb-127">Nome</span><span class="sxs-lookup"><span data-stu-id="5b3eb-127">Name</span></span>       | <span data-ttu-id="5b3eb-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="5b3eb-128">Type</span></span>       | <span data-ttu-id="5b3eb-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="5b3eb-129">Required</span></span> | <span data-ttu-id="5b3eb-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b3eb-130">Description</span></span>                                                                                        |
|------------|------------|----------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5b3eb-131">fatura id</span><span class="sxs-lookup"><span data-stu-id="5b3eb-131">invoice-id</span></span> | <span data-ttu-id="5b3eb-132">string</span><span class="sxs-lookup"><span data-stu-id="5b3eb-132">string</span></span>     | <span data-ttu-id="5b3eb-133">Sim</span><span class="sxs-lookup"><span data-stu-id="5b3eb-133">Yes</span></span>      | <span data-ttu-id="5b3eb-134">O valor é um id de fatura que permite ao revendedor filtrar os resultados de uma determinada fatura.</span><span class="sxs-lookup"><span data-stu-id="5b3eb-134">The value is an invoice-id that allows the reseller to filter the results for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5b3eb-135">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="5b3eb-135">Request headers</span></span>

<span data-ttu-id="5b3eb-136">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5b3eb-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5b3eb-137">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5b3eb-137">Request body</span></span>

<span data-ttu-id="5b3eb-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5b3eb-138">None</span></span>

### <a name="request-example"></a><span data-ttu-id="5b3eb-139">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5b3eb-139">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="5b3eb-140">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5b3eb-140">REST response</span></span>

<span data-ttu-id="5b3eb-141">Se for bem sucedido, este método devolve um recurso [de Declaração de Fatura no](invoice-resources.md#invoicestatement) organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="5b3eb-141">If successful, this method returns an [InvoiceStatement](invoice-resources.md#invoicestatement) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5b3eb-142">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5b3eb-142">Response success and error codes</span></span>

<span data-ttu-id="5b3eb-143">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5b3eb-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5b3eb-144">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5b3eb-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5b3eb-145">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="5b3eb-145">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5b3eb-146">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5b3eb-146">Response example</span></span>

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
