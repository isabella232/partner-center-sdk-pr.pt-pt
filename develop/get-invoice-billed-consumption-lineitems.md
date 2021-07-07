---
title: Obter fatura faturada itens de linha de consumo comercial
description: Pode obter uma recolha de dados de linha de consumo comercial (item de linha de uso avaliado diariamente) para uma fatura especificada usando as APIs do Partner Center.
ms.date: 01/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 285b6fbda774c9396dee8947550ed774d52bf901
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446229"
---
# <a name="get-invoice-billed-commercial-consumption-line-items"></a><span data-ttu-id="4d7a9-103">Obter fatura faturada itens de linha de consumo comercial</span><span class="sxs-lookup"><span data-stu-id="4d7a9-103">Get invoice billed commercial consumption line items</span></span>

<span data-ttu-id="4d7a9-104">Pode utilizar os seguintes métodos para obter uma recolha de detalhes para artigos de linha de fatura de consumo comercial (também conhecidos como itens de linha de utilização com classificação diária fechada) para uma fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-104">You can use the following methods to get a collection of details for commercial consumption invoice line items (also known as closed daily rated usage line items) for a specified invoice.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="4d7a9-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4d7a9-105">Prerequisites</span></span>

- <span data-ttu-id="4d7a9-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4d7a9-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4d7a9-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="4d7a9-108">Um identificador de fatura.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-108">An invoice identifier.</span></span> <span data-ttu-id="4d7a9-109">Isto identifica a fatura para a recuperação dos itens de linha.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-109">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="4d7a9-110">C\#</span><span class="sxs-lookup"><span data-stu-id="4d7a9-110">C\#</span></span>

<span data-ttu-id="4d7a9-111">Para obter os itens de linha comercial para a fatura especificada, tem de recuperar o objeto da fatura:</span><span class="sxs-lookup"><span data-stu-id="4d7a9-111">To get the commercial line items for the specified invoice, you must retrieve the invoice object:</span></span>

1. <span data-ttu-id="4d7a9-112">Ligue para o método [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) para obter uma interface para as operações de faturação para a fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-112">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="4d7a9-113">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar o objeto da fatura.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-113">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span> <span data-ttu-id="4d7a9-114">O objeto da fatura contém todas as informações para a fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-114">The invoice object contains all of the information for the specified invoice.</span></span>

<span data-ttu-id="4d7a9-115">O **Fornecedor** identifica a origem das informações de pormenor faturadas (por exemplo, **uma vez).**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-115">The **Provider** identifies the source of the billed detail information (for example, **onetime**).</span></span> <span data-ttu-id="4d7a9-116">A **FaturaLineItemType** especifica o tipo (por exemplo, **UsageLineItem**).</span><span class="sxs-lookup"><span data-stu-id="4d7a9-116">The **InvoiceLineItemType** specifies the type (for example, **UsageLineItem**).</span></span>

<span data-ttu-id="4d7a9-117">O seguinte código exemplo utiliza um circuito **de apreensão para** processar a recolha de itens de linha.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-117">The following example code uses a **foreach** loop to process the line items collection.</span></span> <span data-ttu-id="4d7a9-118">Uma coleção separada de itens de linha é recuperada para cada **FaturaLineItemType**.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-118">A separate collection of line items is retrieved for each **InvoiceLineItemType**.</span></span>

<span data-ttu-id="4d7a9-119">Para obter uma coleção de itens de linha que correspondam a uma instância **FaturaDetail:**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-119">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="4d7a9-120">Passe o **BillingProvider** e **o InvoiceLineItemType** para o método [**Por.**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by)</span><span class="sxs-lookup"><span data-stu-id="4d7a9-120">Pass the instance's **BillingProvider** and **InvoiceLineItemType** to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="4d7a9-121">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar os itens de linha associados.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-121">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the associated line items.</span></span>
3. <span data-ttu-id="4d7a9-122">Crie um enumerador para atravessar a coleção como mostrado no exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-122">Create an enumerator to traverse the collection as shown in the following example.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string invoiceId;
// string curencyCode;
// string period;
// int pageMaxSizeReconLineItems = 2000;

// all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

var seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById(invoiceId).By("onetime", "usagelineitems", curencyCode, period, pageMaxSizeReconLineItems).Get();

var fetchNext = true;

ConsoleKeyInfo keyInfo;

var itemNumber = 1;
while (fetchNext)
{
    Console.Out.WriteLine("\tLine line items count: " + seekBasedResourceCollection.Items.Count());

    seekBasedResourceCollection.Items.ToList().ForEach(item =>
    {
        // Instance of type DailyRatedUsageLineItem
        if (item is DailyRatedUsageLineItem)
        {
            Type t = typeof(DailyRatedUsageLineItem);
            PropertyInfo[] properties = t.GetProperties();

            foreach (PropertyInfo property in properties)
            {
                // Insert code here to work with the line item properties
            }
        }
        itemNumber++;
    });

    Console.Out.WriteLine("\tPress any key to fetch next data. Press the Escape (Esc) key to quit: \n");
    keyInfo = Console.ReadKey();

    if (keyInfo.Key == ConsoleKey.Escape)
    {
        break;
    }

    fetchNext = !string.IsNullOrWhiteSpace(seekBasedResourceCollection.ContinuationToken);

    if (fetchNext)
    {
        if (seekBasedResourceCollection.Links.Next.Headers != null && seekBasedResourceCollection.Links.Next.Headers.Any())
        {
            seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById(invoiceId).By("onetime", "usagelineitems", curencyCode, period, pageMaxSizeReconLineItems).Seek(seekBasedResourceCollection.ContinuationToken, SeekOperation.Next);
        }
    }
}
```

<span data-ttu-id="4d7a9-123">Para um exemplo semelhante, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4d7a9-123">For a similar example, see the following:</span></span>

- <span data-ttu-id="4d7a9-124">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="4d7a9-124">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="4d7a9-125">Project: **Amostras SDK do Centro Parceiro**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-125">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="4d7a9-126">Classe: **GetBilledConsumptionReconLineItemsPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-126">Class: **GetBilledConsumptionReconLineItemsPaging.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="4d7a9-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="4d7a9-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4d7a9-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d7a9-128">Request syntax</span></span>

<span data-ttu-id="4d7a9-129">Utilize a primeira sintaxe para devolver uma lista completa de todos os itens de linha para a fatura dada.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-129">Use the first syntax to return a full list of every line item for the given invoice.</span></span> <span data-ttu-id="4d7a9-130">Para faturas grandes, utilize a segunda sintaxe com um tamanho especificado e uma compensação baseada em 0 para devolver uma lista de itens de linha paged.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-130">For large invoices, use the second syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> <span data-ttu-id="4d7a9-131">Utilize a terceira sintaxe para obter a próxima página de itens de linha de reconhecimento utilizando `seekOperation = "Next"` .</span><span class="sxs-lookup"><span data-stu-id="4d7a9-131">Use the third syntax to get the next page of recon line items using `seekOperation = "Next"`.</span></span>

| <span data-ttu-id="4d7a9-132">Método</span><span class="sxs-lookup"><span data-stu-id="4d7a9-132">Method</span></span>  | <span data-ttu-id="4d7a9-133">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="4d7a9-133">Request URI</span></span>                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4d7a9-134">**Obter**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-134">**GET**</span></span> | <span data-ttu-id="4d7a9-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4d7a9-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode} HTTP/1.1</span></span>                              |
| <span data-ttu-id="4d7a9-136">**Obter**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-136">**GET**</span></span> | <span data-ttu-id="4d7a9-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4d7a9-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size} HTTP/1.1</span></span>  |
| <span data-ttu-id="4d7a9-138">**Obter**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-138">**GET**</span></span> | <span data-ttu-id="4d7a9-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size}&seekOperation=Next</span><span class="sxs-lookup"><span data-stu-id="4d7a9-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size}&seekOperation=Next</span></span>                               |

#### <a name="uri-parameters"></a><span data-ttu-id="4d7a9-140">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="4d7a9-140">URI parameters</span></span>

<span data-ttu-id="4d7a9-141">Utilize os seguintes parâmetros URI e consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-141">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="4d7a9-142">Nome</span><span class="sxs-lookup"><span data-stu-id="4d7a9-142">Name</span></span>                   | <span data-ttu-id="4d7a9-143">Tipo</span><span class="sxs-lookup"><span data-stu-id="4d7a9-143">Type</span></span>   | <span data-ttu-id="4d7a9-144">Necessário</span><span class="sxs-lookup"><span data-stu-id="4d7a9-144">Required</span></span> | <span data-ttu-id="4d7a9-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d7a9-145">Description</span></span>                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| <span data-ttu-id="4d7a9-146">fatura id</span><span class="sxs-lookup"><span data-stu-id="4d7a9-146">invoice-id</span></span>             | <span data-ttu-id="4d7a9-147">string</span><span class="sxs-lookup"><span data-stu-id="4d7a9-147">string</span></span> | <span data-ttu-id="4d7a9-148">Yes</span><span class="sxs-lookup"><span data-stu-id="4d7a9-148">Yes</span></span>      | <span data-ttu-id="4d7a9-149">Uma corda que identifica a fatura.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-149">A string that identifies the invoice.</span></span>                             |
| <span data-ttu-id="4d7a9-150">provedor</span><span class="sxs-lookup"><span data-stu-id="4d7a9-150">provider</span></span>               | <span data-ttu-id="4d7a9-151">string</span><span class="sxs-lookup"><span data-stu-id="4d7a9-151">string</span></span> | <span data-ttu-id="4d7a9-152">Yes</span><span class="sxs-lookup"><span data-stu-id="4d7a9-152">Yes</span></span>      | <span data-ttu-id="4d7a9-153">O provedor: "OneTime".</span><span class="sxs-lookup"><span data-stu-id="4d7a9-153">The provider: "OneTime".</span></span>                                  |
| <span data-ttu-id="4d7a9-154">tipo de artigo de linha de fatura</span><span class="sxs-lookup"><span data-stu-id="4d7a9-154">invoice-line-item-type</span></span> | <span data-ttu-id="4d7a9-155">string</span><span class="sxs-lookup"><span data-stu-id="4d7a9-155">string</span></span> | <span data-ttu-id="4d7a9-156">Yes</span><span class="sxs-lookup"><span data-stu-id="4d7a9-156">Yes</span></span>      | <span data-ttu-id="4d7a9-157">O tipo de detalhe de fatura: "UsageLineItems".</span><span class="sxs-lookup"><span data-stu-id="4d7a9-157">The type of invoice detail: "UsageLineItems".</span></span> |
| <span data-ttu-id="4d7a9-158">currencyCode</span><span class="sxs-lookup"><span data-stu-id="4d7a9-158">currencyCode</span></span>           | <span data-ttu-id="4d7a9-159">string</span><span class="sxs-lookup"><span data-stu-id="4d7a9-159">string</span></span> | <span data-ttu-id="4d7a9-160">Yes</span><span class="sxs-lookup"><span data-stu-id="4d7a9-160">Yes</span></span>      | <span data-ttu-id="4d7a9-161">O código cambial para os itens da linha faturada.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-161">The currency code for the billed line items.</span></span>                    |
| <span data-ttu-id="4d7a9-162">period</span><span class="sxs-lookup"><span data-stu-id="4d7a9-162">period</span></span>                 | <span data-ttu-id="4d7a9-163">string</span><span class="sxs-lookup"><span data-stu-id="4d7a9-163">string</span></span> | <span data-ttu-id="4d7a9-164">Yes</span><span class="sxs-lookup"><span data-stu-id="4d7a9-164">Yes</span></span>      | <span data-ttu-id="4d7a9-165">O período para o reconhecimento cobrado.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-165">The period for billed recon.</span></span> <span data-ttu-id="4d7a9-166">exemplo: corrente, anterior.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-166">example: current, previous.</span></span>        |
| <span data-ttu-id="4d7a9-167">size</span><span class="sxs-lookup"><span data-stu-id="4d7a9-167">size</span></span>                   | <span data-ttu-id="4d7a9-168">número</span><span class="sxs-lookup"><span data-stu-id="4d7a9-168">number</span></span> | <span data-ttu-id="4d7a9-169">No</span><span class="sxs-lookup"><span data-stu-id="4d7a9-169">No</span></span>       | <span data-ttu-id="4d7a9-170">O número máximo de itens para devolver.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-170">The maximum number of items to return.</span></span> <span data-ttu-id="4d7a9-171">O tamanho padrão é 2000</span><span class="sxs-lookup"><span data-stu-id="4d7a9-171">Default size is 2000</span></span>       |
| <span data-ttu-id="4d7a9-172">procurarOperação</span><span class="sxs-lookup"><span data-stu-id="4d7a9-172">seekOperation</span></span>          | <span data-ttu-id="4d7a9-173">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="4d7a9-173">string</span></span> | <span data-ttu-id="4d7a9-174">No</span><span class="sxs-lookup"><span data-stu-id="4d7a9-174">No</span></span>       | <span data-ttu-id="4d7a9-175">Desaperte a procuraOperação=Próxima para obter a próxima página de itens de linha de reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-175">Set seekOperation=Next to get the next page of recon line items.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4d7a9-176">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="4d7a9-176">Request headers</span></span>

<span data-ttu-id="4d7a9-177">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4d7a9-177">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4d7a9-178">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="4d7a9-178">Request body</span></span>

<span data-ttu-id="4d7a9-179">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-179">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="4d7a9-180">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="4d7a9-180">REST response</span></span>

<span data-ttu-id="4d7a9-181">Se for bem sucedida, a resposta contém a recolha de detalhes do item da linha.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-181">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="4d7a9-182">Para o item de linha **ChargeType,** o valor **Compra** está mapeado para **New**.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-182">For the line item **ChargeType**, the value **Purchase** is mapped to **New**.</span></span> <span data-ttu-id="4d7a9-183">O valor **Reembolso** está mapeado para **cancelar.**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-183">The value **Refund** is mapped to **Cancel**.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4d7a9-184">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="4d7a9-184">Response success and error codes</span></span>

<span data-ttu-id="4d7a9-185">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-185">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4d7a9-186">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4d7a9-186">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4d7a9-187">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4d7a9-187">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

## <a name="rest-examples"></a><span data-ttu-id="4d7a9-188">Exemplos DE REPOUSO</span><span class="sxs-lookup"><span data-stu-id="4d7a9-188">REST examples</span></span>

### <a name="request-response-example-1"></a><span data-ttu-id="4d7a9-189">Exemplo de resposta a pedido 1</span><span class="sxs-lookup"><span data-stu-id="4d7a9-189">Request-response example 1</span></span>

<span data-ttu-id="4d7a9-190">Os detalhes para este exemplo pedido e resposta REST são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="4d7a9-190">The details for this example REST request and response are as follows:</span></span>

- <span data-ttu-id="4d7a9-191">**Fornecedor**: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-191">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="4d7a9-192">**FaturaLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-192">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="4d7a9-193">**Período**: **Anterior**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-193">**Period**: **Previous**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="4d7a9-194">Pedido exemplo 1</span><span class="sxs-lookup"><span data-stu-id="4d7a9-194">Request example 1</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/T000001234/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-1"></a><span data-ttu-id="4d7a9-195">Exemplo de resposta 1</span><span class="sxs-lookup"><span data-stu-id="4d7a9-195">Response example 1</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Wed, 20 Feb 2019 19:59:27 GMT

{
    "totalCount": 2,
    "items": [
        {
            "partnerId": "2b8940db-5089-539c-e757-520ed1d1bc88",
            "partnerName": "",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "T000001234",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "Test Test on Windows 2012 R2 (WebHost)",
            "productName": "Test Test on Windows",
            "publisherName": "Test",
            "publisherId": "28503520",
            "subscriptionId": "12345678-9d62-4a85-8fd0-91a87c261bc4",
            "subscriptionDescription": "Subscription 10",
            "chargeStartDate": "2018-11-01T00:00:00Z",
            "chargeEndDate": "2018-12-01T00:00:00Z",
            "usageDate": "2018-11-13T00:00:00Z",
            "meterType": "1 Compute Hour - 1core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "1core",
            "meterSubCategory": "Test Test on Windows",
            "meterName": "Test Test on Windows - Test Test on Windows 2012 R2 (WebHost) - 1 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS2",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "TestWINRG",
            "resourceUri": "/subscriptions/12345678-9d62-4a85-8fd0-91a87c261bc4/resourceGroups/TestWINRG/providers/Microsoft.Compute/virtualMachines/testWinTest",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_B1s\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "new",
            "unitPrice": 0.0209496384791679,
            "quantity": 23.200004,
            "unitType": "1 Hour",
            "billingPreTaxTotal": 0.486031696515249,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 0.486031696515249,
            "pricingCurrency": "USD",
            "creditType": "Credit Not Applied",
            "invoiceLineItemType": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        },
        {
            "partnerId": "2b8940db-5089-539c-e757-520ed1d1bc88",
            "partnerName": "",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "T000001234",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "Test Test on Ubuntu 16.04 (WebHost)",
            "productName": "Test Test on Linux",
            "publisherName": "Test",
            "publisherId": "28503520",
            "subscriptionId": "12345678-9d62-4a85-8fd0-91a87c261bc4",
            "subscriptionDescription": "Subscription 10",
            "chargeStartDate": "2018-11-01T00:00:00Z",
            "chargeEndDate": "2018-12-01T00:00:00Z",
            "usageDate": "2018-11-13T00:00:00Z",
            "meterType": "1 Compute Hour - 1core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "1core",
            "meterSubCategory": "Test Test on Linux",
            "meterName": "Test Test on Linux - Test Test on Ubuntu 16.04 (WebHost) - 1 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "TESTRG",
            "resourceUri": "/subscriptions/12345678-9d62-4a85-8fd0-91a87c261bc4/resourceGroups/TestRG/providers/Microsoft.Compute/virtualMachines/testUbuntuTest",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_B1s\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "new",
            "unitPrice": 0.0209951014286867,
            "quantity": 23.350007,
            "unitType": "1 Hour",
            "billingPreTaxTotal": 0.490235765325545,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 0.490235765325545,
            "pricingCurrency": "USD",
            "entitlementId": "66bada28-271e-4b7a-aaf5-c0ead6312345",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0.1999968000511991808131,
            "rateOfPartnerEarnedCredit": 0,
            "rateOfCredit": 1,
            "creditType": "Azure Credit Applied",
            "invoiceLineItemType": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/T000001234/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/T000001234/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000&seekOperation=Next",
            "method": "GET",
            "headers": [
                {
                    "key": "MS-ContinuationToken",
                    "value": "AQAAAA=="
                }
            ]
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-2"></a><span data-ttu-id="4d7a9-196">Exemplo de resposta a pedido 2</span><span class="sxs-lookup"><span data-stu-id="4d7a9-196">Request-response example 2</span></span>

<span data-ttu-id="4d7a9-197">Os detalhes para este exemplo pedido e resposta REST são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="4d7a9-197">The details for this example REST request and response are as follows:</span></span>

- <span data-ttu-id="4d7a9-198">**Fornecedor**: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-198">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="4d7a9-199">**FaturaLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-199">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="4d7a9-200">**Período**: **Anterior**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-200">**Period**: **Previous**</span></span>
- <span data-ttu-id="4d7a9-201">**SeekOperation**: **Seguinte**</span><span class="sxs-lookup"><span data-stu-id="4d7a9-201">**SeekOperation**: **Next**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="4d7a9-202">Pedido exemplo 2</span><span class="sxs-lookup"><span data-stu-id="4d7a9-202">Request example 2</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/T000001234/lineitems?provider=onetime&invoiceLineItemType=usagelineitems&currencyCode=usd&period=previous&size=2000&seekoperation=next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="response-example-2"></a><span data-ttu-id="4d7a9-203">Exemplo de resposta 2</span><span class="sxs-lookup"><span data-stu-id="4d7a9-203">Response example 2</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Wed, 20 Feb 2019 19:59:27 GMT

{
    "totalCount": 1,
    "items": [
          {
            "partnerId": "2b8940db-5089-539c-e757-520ed1d1bc88",
            "partnerName": "",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "T000001234",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "Test Test on Windows 2012 R2 (WebHost)",
            "productName": "Test Test on Windows",
            "publisherName": "Test",
            "publisherId": "28503520",
            "subscriptionId": "12345678-9d62-4a85-8fd0-91a87c261bc4",
            "subscriptionDescription": "Subscription 10",
            "chargeStartDate": "2018-11-01T00:00:00Z",
            "chargeEndDate": "2018-12-01T00:00:00Z",
            "usageDate": "2018-11-13T00:00:00Z",
            "meterType": "1 Compute Hour - 1core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "1core",
            "meterSubCategory": "Test Test on Windows",
            "meterName": "Test Test on Windows - Test Test on Windows 2012 R2 (WebHost) - 1 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS2",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "TestWINRG",
            "resourceUri": "/subscriptions/12345678-9d62-4a85-8fd0-91a87c261bc4/resourceGroups/TestWINRG/providers/Microsoft.Compute/virtualMachines/testWinTest",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_B1s\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "new",
            "unitPrice": 0.0209496384791679,
            "quantity": 23.200004,
            "unitType": "1 Hour",
            "billingPreTaxTotal": 0.486031696515249,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 0.486031696515249,
            "pricingCurrency": "USD",
            "entitlementId": "66bada28-271e-4b7a-aaf5-c0ead6312345",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0.1835431430074643112595,
            "rateOfPartnerEarnedCredit": 0.15,
            "rateOfCredit": 0.15,
            "creditType": "Partner Earned Credit Applied",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
             "uri": "/invoices/T000001234/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
