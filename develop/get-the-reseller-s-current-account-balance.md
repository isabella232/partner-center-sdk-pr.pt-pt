---
title: Obter o saldo da conta atual do parceiro
description: Recupera o saldo da conta corrente do parceiro. Um resumo do saldo e os encargos totais de uma fatura para encargos recorrentes e pontuais.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 110da433faa6ff4d3d068c6d68a6f497f4a2721a
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769044"
---
# <a name="get-the-partners-current-account-balance"></a><span data-ttu-id="b6f05-104">Obter o saldo da conta atual do parceiro</span><span class="sxs-lookup"><span data-stu-id="b6f05-104">Get the partner's current account balance</span></span>

<span data-ttu-id="b6f05-105">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="b6f05-105">**Applies To**</span></span>

- <span data-ttu-id="b6f05-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="b6f05-106">Partner Center</span></span>
- <span data-ttu-id="b6f05-107">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="b6f05-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="b6f05-108">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="b6f05-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="b6f05-109">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b6f05-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b6f05-110">Recupera o saldo da conta corrente do parceiro.</span><span class="sxs-lookup"><span data-stu-id="b6f05-110">Retrieves the partner's current account balance.</span></span> <span data-ttu-id="b6f05-111">Um resumo do saldo e os encargos totais de uma fatura para encargos recorrentes e pontuais.</span><span class="sxs-lookup"><span data-stu-id="b6f05-111">A summary of the balance and total charges of an invoice for both recurring and one-time charges.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6f05-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b6f05-112">Prerequisites</span></span>

- <span data-ttu-id="b6f05-113">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b6f05-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b6f05-114">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="b6f05-114">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="b6f05-115">C\#</span><span class="sxs-lookup"><span data-stu-id="b6f05-115">C\#</span></span>

<span data-ttu-id="b6f05-116">Para recuperar o saldo da sua conta, utilize a sua coleção **IAggregatePartner.Faturas** e, em seguida, ligue para a propriedade **Sumário.**</span><span class="sxs-lookup"><span data-stu-id="b6f05-116">To retrieve your account balance, use your **IAggregatePartner.Invoices** collection, and then call the **Summary** property.</span></span> <span data-ttu-id="b6f05-117">Em seguida, ligue para a função **Obter** e, finalmente, ligue para a propriedade **BalanceAmount.**</span><span class="sxs-lookup"><span data-stu-id="b6f05-117">Then call the **Get** function, and finally call the **BalanceAmount** property.</span></span>

``` csharp
// IAggregatePartner scopedPartnerOperations;

var invoiceSummary = scopedPartnerOperations.Invoices.Summary.Get();

Console.Out.WriteLine("Current Account Balance:  {0:C}", invoiceSummary.BalanceAmount);
```

<span data-ttu-id="b6f05-118">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b6f05-118">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b6f05-119">**Projeto**: PartnerSDK.FeatureSample **Class**: GetInvoiceSummary.cs</span><span class="sxs-lookup"><span data-stu-id="b6f05-119">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceSummary.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b6f05-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b6f05-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b6f05-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6f05-121">Request syntax</span></span>

| <span data-ttu-id="b6f05-122">Método</span><span class="sxs-lookup"><span data-stu-id="b6f05-122">Method</span></span>  | <span data-ttu-id="b6f05-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b6f05-123">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="b6f05-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b6f05-124">**GET**</span></span> | <span data-ttu-id="b6f05-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/resumo HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b6f05-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summary HTTP/1.1</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="b6f05-126">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b6f05-126">Request headers</span></span>

<span data-ttu-id="b6f05-127">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b6f05-127">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b6f05-128">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b6f05-128">Request body</span></span>

<span data-ttu-id="b6f05-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b6f05-129">None</span></span>

### <a name="request-example"></a><span data-ttu-id="b6f05-130">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b6f05-130">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/summary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="b6f05-131">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b6f05-131">REST response</span></span>

<span data-ttu-id="b6f05-132">Se for bem sucedido, este método devolve um recurso [FaturaSummary](invoice-resources.md#invoicesummary) na resposta.</span><span class="sxs-lookup"><span data-stu-id="b6f05-132">If successful, this method returns an [InvoiceSummary](invoice-resources.md#invoicesummary) resource in the response.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b6f05-133">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b6f05-133">Response success and error codes</span></span>

<span data-ttu-id="b6f05-134">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b6f05-134">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b6f05-135">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b6f05-135">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b6f05-136">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b6f05-136">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b6f05-137">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b6f05-137">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 256
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
Date: Thu, 24 Mar 2016 05:21:01 GMT

{
    "balanceAmount": 751094.39,
    "currencyCode": "USD",
    "currencySymbol": "$",
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
                "currencyCode": "USD",
                "currencySymbol": "$",
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
                "currencyCode": "USD",
                "currencySymbol": "$",
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
```
