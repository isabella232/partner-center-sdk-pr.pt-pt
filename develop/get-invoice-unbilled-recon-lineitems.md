---
title: Obtenha os itens de linha de reconciliação não faturados da fatura
description: Você pode obter uma coleção de detalhes de item de linha de reconciliação não faturados para o período especificado usando as APIs do Centro parceiro.
ms.date: 01/27/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 5ab7dde0d78e8ff15bb1a960b16c8c925b0478ce
ms.sourcegitcommit: c5acfb373aa012eb3b6c17182f7ca56883502c6b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391296"
---
# <a name="get-invoices-unbilled-reconciliation-line-items"></a><span data-ttu-id="cea22-103">Obtenha os itens de linha de reconciliação não faturados da fatura</span><span class="sxs-lookup"><span data-stu-id="cea22-103">Get invoice's unbilled reconciliation line items</span></span>

<span data-ttu-id="cea22-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cea22-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cea22-105">Pode utilizar os seguintes métodos para obter uma recolha de detalhes para itens de linha de fatura não faturados (também conhecidos como itens de linha de faturação aberta).</span><span class="sxs-lookup"><span data-stu-id="cea22-105">You can use the following methods get a collection of details for unbilled invoice line items (also known as open billing line items).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cea22-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="cea22-106">Prerequisites</span></span>

- <span data-ttu-id="cea22-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cea22-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cea22-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="cea22-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="cea22-109">Um identificador de fatura.</span><span class="sxs-lookup"><span data-stu-id="cea22-109">An invoice identifier.</span></span> <span data-ttu-id="cea22-110">Isto identifica a fatura para a recuperação dos itens de linha.</span><span class="sxs-lookup"><span data-stu-id="cea22-110">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="cea22-111">C\#</span><span class="sxs-lookup"><span data-stu-id="cea22-111">C\#</span></span>

<span data-ttu-id="cea22-112">Para obter os itens de linha para a fatura especificada, recupere o objeto da fatura:</span><span class="sxs-lookup"><span data-stu-id="cea22-112">To get the line items for the specified invoice, retrieve the invoice object:</span></span>

1. <span data-ttu-id="cea22-113">Ligue para o método [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) para obter uma interface para as operações de faturação para a fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="cea22-113">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="cea22-114">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar o objeto da fatura.</span><span class="sxs-lookup"><span data-stu-id="cea22-114">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span>

<span data-ttu-id="cea22-115">O objeto da fatura contém todas as informações para a fatura especificada:</span><span class="sxs-lookup"><span data-stu-id="cea22-115">The invoice object contains all of the information for the specified invoice:</span></span>

- <span data-ttu-id="cea22-116">**O fornecedor** identifica a origem das informações de pormenor não bicos (por exemplo, **OneTime**).</span><span class="sxs-lookup"><span data-stu-id="cea22-116">**Provider** identifies the source of the unbilled detail information (for example, **OneTime**).</span></span>

- <span data-ttu-id="cea22-117">**FaturaLineItemType** especifica o tipo (por exemplo, **BillingLineItem**).</span><span class="sxs-lookup"><span data-stu-id="cea22-117">**InvoiceLineItemType** specifies the type (for example, **BillingLineItem**).</span></span>

<span data-ttu-id="cea22-118">Para obter uma coleção de itens de linha que correspondam a uma instância **FaturaDetail:**</span><span class="sxs-lookup"><span data-stu-id="cea22-118">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="cea22-119">Passe o BillingProvider e o InvoiceLineItemType para o método [**Por.**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by)</span><span class="sxs-lookup"><span data-stu-id="cea22-119">Pass the instance's BillingProvider and InvoiceLineItemType to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="cea22-120">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar os itens de linha associados.</span><span class="sxs-lookup"><span data-stu-id="cea22-120">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the associated line items.</span></span>

3. <span data-ttu-id="cea22-121">Crie um enumerador para atravessar a coleção.</span><span class="sxs-lookup"><span data-stu-id="cea22-121">Create an enumerator to traverse the collection.</span></span> <span data-ttu-id="cea22-122">Por exemplo, consulte o seguinte código de amostra.</span><span class="sxs-lookup"><span data-stu-id="cea22-122">For an example, see the following sample code.</span></span>

<span data-ttu-id="cea22-123">O seguinte código de amostra utiliza um circuito **de apreensão para** processar a coleção **FaturaLineItems.**</span><span class="sxs-lookup"><span data-stu-id="cea22-123">The following sample code uses a **foreach** loop to process the **InvoiceLineItems** collection.</span></span> <span data-ttu-id="cea22-124">Uma coleção separada de itens de linha é recuperada para cada **FaturaLineItemType**.</span><span class="sxs-lookup"><span data-stu-id="cea22-124">A separate collection of line items is retrieved for each **InvoiceLineItemType**.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string currencyCode;
// string period;
// int pageMaxSizeReconLineItems = 2000;

// all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

var seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById("unbilled").By("onetime", "billinglineitems", currencyCode, period, pageMaxSizeReconLineItems).Get();

var fetchNext = true;

ConsoleKeyInfo keyInfo;

var itemNumber = 1;
while (fetchNext)
{
    Console.Out.WriteLine("\tLine line items count: " + seekBasedResourceCollection.Items.Count());

    seekBasedResourceCollection.Items.ToList().ForEach(item =>
    {
        // Instance of type OneTimeInvoiceLineItem
        if (item is OneTimeInvoiceLineItem)
        {
            Type t = typeof(OneTimeInvoiceLineItem);
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
            seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById("unbilled").By("onetime", "billinglineitems", currencyCode, period, pageMaxSizeReconLineItems).Seek(seekBasedResourceCollection.ContinuationToken, SeekOperation.Next);
        }
    }
}
```

<span data-ttu-id="cea22-125">Para um exemplo semelhante, consulte:</span><span class="sxs-lookup"><span data-stu-id="cea22-125">For a similar example, see:</span></span>

- <span data-ttu-id="cea22-126">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="cea22-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="cea22-127">Project: **Amostras SDK do Centro Parceiro**</span><span class="sxs-lookup"><span data-stu-id="cea22-127">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="cea22-128">Classe: **GetUnBilledReconLineItemsPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="cea22-128">Class: **GetUnBilledReconLineItemsPaging.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="cea22-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="cea22-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cea22-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="cea22-130">Request syntax</span></span>

<span data-ttu-id="cea22-131">Pode utilizar as seguintes sintaxes para o seu pedido DE REST, dependendo da sua caixa de utilização.</span><span class="sxs-lookup"><span data-stu-id="cea22-131">You can use the following syntaxes for your REST request, depending on your use case.</span></span> <span data-ttu-id="cea22-132">Para mais informações, consulte as descrições de cada sintaxe.</span><span class="sxs-lookup"><span data-stu-id="cea22-132">For more information, see the descriptions for each syntax.</span></span>

 | <span data-ttu-id="cea22-133">Método</span><span class="sxs-lookup"><span data-stu-id="cea22-133">Method</span></span>  | <span data-ttu-id="cea22-134">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="cea22-134">Request URI</span></span>            | <span data-ttu-id="cea22-135">Descrição do caso de utilização de sintaxe</span><span class="sxs-lookup"><span data-stu-id="cea22-135">Description of syntax use case</span></span>                                                                                |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cea22-136">**Obter**</span><span class="sxs-lookup"><span data-stu-id="cea22-136">**GET**</span></span> | <span data-ttu-id="cea22-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="cea22-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period} HTTP/1.1</span></span>                              | <span data-ttu-id="cea22-138">Utilize esta sintaxe para devolver uma lista completa de todos os itens de linha para a fatura dada.</span><span class="sxs-lookup"><span data-stu-id="cea22-138">Use this syntax to return a full list of every line item for the given invoice.</span></span> |
| <span data-ttu-id="cea22-139">**Obter**</span><span class="sxs-lookup"><span data-stu-id="cea22-139">**GET**</span></span> | <span data-ttu-id="cea22-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="cea22-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span></span>  | <span data-ttu-id="cea22-141">Para faturas grandes, utilize esta sintaxe com um tamanho especificado e uma compensação baseada em 0 para devolver uma lista de itens de linha paged.</span><span class="sxs-lookup"><span data-stu-id="cea22-141">For large invoices, use this syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> |
| <span data-ttu-id="cea22-142">**Obter**</span><span class="sxs-lookup"><span data-stu-id="cea22-142">**GET**</span></span> | <span data-ttu-id="cea22-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span><span class="sxs-lookup"><span data-stu-id="cea22-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span></span>                               | <span data-ttu-id="cea22-144">Utilize esta sintaxe para obter a próxima página de itens da linha de reconciliação utilizando `seekOperation = "Next"` .</span><span class="sxs-lookup"><span data-stu-id="cea22-144">Use this syntax to get the next page of reconciliation line items using `seekOperation = "Next"`.</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="cea22-145">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="cea22-145">URI parameters</span></span>

<span data-ttu-id="cea22-146">Utilize os seguintes parâmetros URI e consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="cea22-146">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="cea22-147">Nome</span><span class="sxs-lookup"><span data-stu-id="cea22-147">Name</span></span>                   | <span data-ttu-id="cea22-148">Tipo</span><span class="sxs-lookup"><span data-stu-id="cea22-148">Type</span></span>   | <span data-ttu-id="cea22-149">Necessário</span><span class="sxs-lookup"><span data-stu-id="cea22-149">Required</span></span> | <span data-ttu-id="cea22-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="cea22-150">Description</span></span>                                                                     |
|------------------------|--------|----------|---------------------------------------------------------------------------------|
| <span data-ttu-id="cea22-151">fatura id</span><span class="sxs-lookup"><span data-stu-id="cea22-151">invoice-id</span></span>             | <span data-ttu-id="cea22-152">string</span><span class="sxs-lookup"><span data-stu-id="cea22-152">string</span></span> | <span data-ttu-id="cea22-153">Yes</span><span class="sxs-lookup"><span data-stu-id="cea22-153">Yes</span></span>      | <span data-ttu-id="cea22-154">Uma corda que identifica a fatura.</span><span class="sxs-lookup"><span data-stu-id="cea22-154">A string that identifies the invoice.</span></span> <span data-ttu-id="cea22-155">Use 'sem bico' para obter estimativas não mediadas.</span><span class="sxs-lookup"><span data-stu-id="cea22-155">Use 'unbilled' to get unbilled estimates.</span></span> |
| <span data-ttu-id="cea22-156">provedor</span><span class="sxs-lookup"><span data-stu-id="cea22-156">provider</span></span>               | <span data-ttu-id="cea22-157">string</span><span class="sxs-lookup"><span data-stu-id="cea22-157">string</span></span> | <span data-ttu-id="cea22-158">Yes</span><span class="sxs-lookup"><span data-stu-id="cea22-158">Yes</span></span>      | <span data-ttu-id="cea22-159">O provedor: "OneTime".</span><span class="sxs-lookup"><span data-stu-id="cea22-159">The provider: "OneTime".</span></span>                                                |
| <span data-ttu-id="cea22-160">tipo de artigo de linha de fatura</span><span class="sxs-lookup"><span data-stu-id="cea22-160">invoice-line-item-type</span></span> | <span data-ttu-id="cea22-161">string</span><span class="sxs-lookup"><span data-stu-id="cea22-161">string</span></span> | <span data-ttu-id="cea22-162">Yes</span><span class="sxs-lookup"><span data-stu-id="cea22-162">Yes</span></span>      | <span data-ttu-id="cea22-163">O tipo de detalhe de fatura: "BillingLineItems".</span><span class="sxs-lookup"><span data-stu-id="cea22-163">The type of invoice detail: "BillingLineItems".</span></span>               |
| <span data-ttu-id="cea22-164">hasPartnerEarnedCredit</span><span class="sxs-lookup"><span data-stu-id="cea22-164">hasPartnerEarnedCredit</span></span> | <span data-ttu-id="cea22-165">bool</span><span class="sxs-lookup"><span data-stu-id="cea22-165">bool</span></span>   | <span data-ttu-id="cea22-166">No</span><span class="sxs-lookup"><span data-stu-id="cea22-166">No</span></span>       | <span data-ttu-id="cea22-167">O valor indicando se devolver os itens de linha com o parceiro ganhou crédito aplicado.</span><span class="sxs-lookup"><span data-stu-id="cea22-167">The value indicating if to return the line items with partner earned credit applied.</span></span> <span data-ttu-id="cea22-168">Nota: este parâmetro só será aplicado quando o tipo de fornecedor for OneTime e o InvoiceLineItemType for UsageLineItems.</span><span class="sxs-lookup"><span data-stu-id="cea22-168">Note: this parameter will be only applied when provider type is OneTime and InvoiceLineItemType is UsageLineItems.</span></span>
| <span data-ttu-id="cea22-169">currencyCode</span><span class="sxs-lookup"><span data-stu-id="cea22-169">currencyCode</span></span>           | <span data-ttu-id="cea22-170">string</span><span class="sxs-lookup"><span data-stu-id="cea22-170">string</span></span> | <span data-ttu-id="cea22-171">Yes</span><span class="sxs-lookup"><span data-stu-id="cea22-171">Yes</span></span>      | <span data-ttu-id="cea22-172">O código cambial para os itens de linha não bico.</span><span class="sxs-lookup"><span data-stu-id="cea22-172">The currency code for the unbilled line items.</span></span>                                  |
| <span data-ttu-id="cea22-173">period</span><span class="sxs-lookup"><span data-stu-id="cea22-173">period</span></span>                 | <span data-ttu-id="cea22-174">string</span><span class="sxs-lookup"><span data-stu-id="cea22-174">string</span></span> | <span data-ttu-id="cea22-175">Yes</span><span class="sxs-lookup"><span data-stu-id="cea22-175">Yes</span></span>      | <span data-ttu-id="cea22-176">O período para reconhecimento não-marcado.</span><span class="sxs-lookup"><span data-stu-id="cea22-176">The period for unbilled recon.</span></span> <span data-ttu-id="cea22-177">exemplo: corrente, anterior.</span><span class="sxs-lookup"><span data-stu-id="cea22-177">example: current, previous.</span></span>                      |
| <span data-ttu-id="cea22-178">size</span><span class="sxs-lookup"><span data-stu-id="cea22-178">size</span></span>                   | <span data-ttu-id="cea22-179">número</span><span class="sxs-lookup"><span data-stu-id="cea22-179">number</span></span> | <span data-ttu-id="cea22-180">No</span><span class="sxs-lookup"><span data-stu-id="cea22-180">No</span></span>       | <span data-ttu-id="cea22-181">O número máximo de itens para devolver.</span><span class="sxs-lookup"><span data-stu-id="cea22-181">The maximum number of items to return.</span></span> <span data-ttu-id="cea22-182">O tamanho padrão é 2000</span><span class="sxs-lookup"><span data-stu-id="cea22-182">Default size is 2000</span></span>                     |
| <span data-ttu-id="cea22-183">procurarOperação</span><span class="sxs-lookup"><span data-stu-id="cea22-183">seekOperation</span></span>          | <span data-ttu-id="cea22-184">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="cea22-184">string</span></span> | <span data-ttu-id="cea22-185">No</span><span class="sxs-lookup"><span data-stu-id="cea22-185">No</span></span>       | <span data-ttu-id="cea22-186">Desaperte a procuraOperação=Próxima para obter a próxima página de itens de linha de reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="cea22-186">Set seekOperation=Next to get the next page of recon line items.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="cea22-187">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="cea22-187">Request headers</span></span>

<span data-ttu-id="cea22-188">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cea22-188">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cea22-189">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="cea22-189">Request body</span></span>

<span data-ttu-id="cea22-190">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cea22-190">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="cea22-191">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="cea22-191">REST response</span></span>

<span data-ttu-id="cea22-192">Se for bem sucedida, a resposta contém a recolha de detalhes do item da linha.</span><span class="sxs-lookup"><span data-stu-id="cea22-192">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="cea22-193">*Para o item da linha **ChargeType,** o valor **Compra** é mapeado para **Novo** e o valor **Reembolso** está mapeado para **Cancelar**.*</span><span class="sxs-lookup"><span data-stu-id="cea22-193">*For the line item **ChargeType**, the value **Purchase** is mapped to **New** and the value **Refund** is mapped to **Cancel**.*</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cea22-194">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="cea22-194">Response success and error codes</span></span>

<span data-ttu-id="cea22-195">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="cea22-195">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cea22-196">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="cea22-196">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cea22-197">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="cea22-197">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="request-response-examples"></a><span data-ttu-id="cea22-198">Exemplos de resposta a pedidos</span><span class="sxs-lookup"><span data-stu-id="cea22-198">Request-response examples</span></span>

#### <a name="request-response-example-1"></a><span data-ttu-id="cea22-199">Exemplo de resposta a pedido 1</span><span class="sxs-lookup"><span data-stu-id="cea22-199">Request-response example 1</span></span>

<span data-ttu-id="cea22-200">Os seguintes detalhes aplicam-se a este exemplo:</span><span class="sxs-lookup"><span data-stu-id="cea22-200">The following details apply to this example:</span></span>

- <span data-ttu-id="cea22-201">Fornecedor: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="cea22-201">Provider: **OneTime**</span></span>
- <span data-ttu-id="cea22-202">FaturaLineItemType: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="cea22-202">InvoiceLineItemType: **BillingLineItems**</span></span>
- <span data-ttu-id="cea22-203">Período: **Anterior**</span><span class="sxs-lookup"><span data-stu-id="cea22-203">Period: **Previous**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="cea22-204">Pedido exemplo 1</span><span class="sxs-lookup"><span data-stu-id="cea22-204">Request example 1</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1//invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-1"></a><span data-ttu-id="cea22-205">Exemplo de resposta 1</span><span class="sxs-lookup"><span data-stu-id="cea22-205">Response example 1</span></span>

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
   "totalCount": 3,
    "items": [
        {
            "partnerId": "934f3416-bc2f-47f3-b492-77e517d4e572",
            "customerId": "c139c4bf-2e8b-4ab5-8bed-d9f50dcca7a2",
            "customerName": "Test_Test_Office R2 Reduce Seats Validation",
            "customerDomainName": "testcustomerr2t2reduce.onmicrosoft.com",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "5357564",
            "resellerMpnId": "4649221",
            "orderId": "94e858b6d855",
            "orderDate": "2021-05-20T18:30:06.6045692Z",
            "productId": "CFQ7TTC0LH0R",
            "skuId": "0002",
            "availabilityId": "CFQ7TTC0K5RQ",
            "productName": "Microsoft 365 Phone System - Virtual User",
            "skuName": "Microsoft 365 Phone System - Virtual User",
            "productQualifiers": [
                "AddOn",
                "Trial"
            ],
            "chargeType": "new",
            "unitPrice": "0",
            "effectiveUnitPrice": "0",
            "unitType": "",
            "quantity": "25",
            "subtotal": "0",
            "taxTotal": "0",
            "totalForCustomer": "0",
            "currency": "USD",
            "publisherName": "Microsoft Corporation",
            "publisherId": "",
            "subscriptionDescription": "",
            "subscriptionId": "86646af9-e80a-4aa0-da80-3fd2b792c2cc",
            "subscriptionStartDate": "2021-05-20T00:00:00Z",
            "subscriptionEndDate": "2021-06-19T00:00:00Z",
            "chargeStartDate": "2021-05-20T00:00:00Z",
            "chargeEndDate": "2021-06-19T00:00:00Z",
            "termAndBillingCycle": "One-Month commitment for trial",
            "alternateId": "94e858b6d855",
            "referenceId": "0cf1202a-5b7d-4219-966e-93c637113708",
            "priceAdjustmentDescription": "",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": "1",
            "pcToBCExchangeRateDate": "2021-05-01T00:00:00",
            "billableQuantity": "25",
            "meterDescription": "",
            "billingFrequency": "",
            "reservationOrderId": "99f246cf-ed96-41b4-b0cd-0aa43eb1fe91",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "promotionId": "",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
            
        },
        {
            "partnerId": "934f3416-bc2f-47f3-b492-77e517d4e572",
            "customerId": "835a59a7-3172-47b5-bdef-d9cc65f4d0e4",
            "customerName": "TEST_TEST Test Promotions 01",
            "customerDomainName": "kyletestpromos01.onmicrosoft.com",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "5357564",
            "resellerMpnId": "0",
            "orderId": "5f9d52bb1408",
            "orderDate": "2021-05-20T18:48:30.6168285Z",
            "productId": "CFQ7TTC0HL8W",
            "skuId": "0001",
            "availabilityId": "CFQ7TTC0K59S",
            "productName": "Power BI Premium Per User",
            "skuName": "Power BI Premium Per User",
            "productQualifiers": [],
            "chargeType": "new",
            "unitPrice": "16",
            "effectiveUnitPrice": "14.4",
            "unitType": "",
            "quantity": "50",
            "subtotal": "720",
            "taxTotal": "0",
            "totalForCustomer": "0",
            "currency": "USD",
            "publisherName": "Microsoft Corporation",
            "publisherId": "",
            "subscriptionDescription": "",
            "subscriptionId": "9d7d1f3d-c8de-461c-db6d-91debd5129f0",
            "subscriptionStartDate": "2021-05-20T00:00:00Z",
            "subscriptionEndDate": "2022-05-19T00:00:00Z",
            "chargeStartDate": "2021-05-20T00:00:00Z",
            "chargeEndDate": "2021-06-19T00:00:00Z",
            "termAndBillingCycle": "One-Year commitment for monthly/yearly billing",
            "alternateId": "5f9d52bb1408",
            "referenceId": "28b535e0-68f4-40b5-84f7-8ed9241eb149",
            "priceAdjustmentDescription": "[\"Price for given billing period\",\"You are getting a discount due to a pre-determined override.\",\"You are getting a discount for being a partner.\",\"You are getting a price guarantee for your price.\",\"Price for given term\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": "1",
            "pcToBCExchangeRateDate": "2021-05-01T00:00:00",
            "billableQuantity": "50",
            "meterDescription": "",
            "billingFrequency": "Monthly",
            "reservationOrderId": "8fdebb4a-7110-496e-9570-623e4c992797",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "promotionId": "78bcf906-b945-4210-8818-cfb93caf12a1",
            "attributes/objectType": "OneTimeInvoiceLineItem",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        },
        {
            "partnerId": "934f3416-bc2f-47f3-b492-77e517d4e572",
            "customerId": "c139c4bf-2e8b-4ab5-8bed-d9f50dcca7a2",
            "customerName": "Test_Test_Office R2 Reduce Seats Validation",
            "customerDomainName": "testcustomerr2t2reduce.onmicrosoft.com",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "1234567",
            "resellerMpnId": 0,
            "orderId": "HJVtMZMkgQ2miuCiNv0RSr51zQDans0m1",
            "orderDate": "2019-02-04T17:59:52.9460102Z",
            "productId": "DZH318Z0BXWC",
            "skuId": "0002",
            "availabilityId": "DZH318Z0BP8B",
            "productName": "Test WAF-as-a-Service",
            "skuName": "Test WaaS - Medium Plan",
            "chargeType": "New",
            "unitPrice": 820,
            "effectiveUnitPrice": 820,
            "unitType": "",
            "quantity": 1,
            "subtotal": 820,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "publisherName": "Test Networks, Inc.",
            "publisherId": "21223810",
            "subscriptionDescription": "",
            "subscriptionId": "12345678-9cf0-4a1f-9514-7fcc7fe9d1fe",
            "subscriptionStartDate": "2019-02-01T00:00:00Z",
            "subscriptionEndDate": "2020-01-31T00:00:00Z",
            "chargeStartDate": "2019-02-04T09:22:40.1767993-08:00",
            "chargeEndDate": "2019-03-03T09:22:40.1767993-08:00",
            "termAndBillingCycle": "1 Year Subscription",
            "alternateId": "123456ad566",
            "priceAdjustmentDescription": "[\"15.0% Partner earned credit for services managed\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "billableQuantity": 3.1618,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "883d475b-0000-1234-0000-8818752f1234",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ]
}
    ],
    "links": {
        "self": {
            "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000&seekOperation=Next",
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

### <a name="request-response-example-2"></a><span data-ttu-id="cea22-206">Exemplo de resposta a pedido 2</span><span class="sxs-lookup"><span data-stu-id="cea22-206">Request-response example 2</span></span>

<span data-ttu-id="cea22-207">Os seguintes detalhes aplicam-se a este exemplo:</span><span class="sxs-lookup"><span data-stu-id="cea22-207">The following details apply to this example:</span></span>

- <span data-ttu-id="cea22-208">Fornecedor: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="cea22-208">Provider: **OneTime**</span></span>
- <span data-ttu-id="cea22-209">FaturaLineItemType: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="cea22-209">InvoiceLineItemType: **BillingLineItems**</span></span>
- <span data-ttu-id="cea22-210">Período: **Anterior**</span><span class="sxs-lookup"><span data-stu-id="cea22-210">Period: **Previous**</span></span>
- <span data-ttu-id="cea22-211">SeekOperation: **Next**</span><span class="sxs-lookup"><span data-stu-id="cea22-211">SeekOperation: **Next**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="cea22-212">Pedido exemplo 2</span><span class="sxs-lookup"><span data-stu-id="cea22-212">Request example 2</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/unbilled/lineitems?provider=onetime&invoiceLineItemType=billinglineitems&currencyCode=usd&period=previous&size=2000&seekoperation=next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-2"></a><span data-ttu-id="cea22-213">Exemplo de resposta 2</span><span class="sxs-lookup"><span data-stu-id="cea22-213">Response example 2</span></span>

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
   "totalCount": 3,
    "items": [
        {
            "partnerId": "934f3416-bc2f-47f3-b492-77e517d4e572",
            "customerId": "c139c4bf-2e8b-4ab5-8bed-d9f50dcca7a2",
            "customerName": "Test_Test_Office R2 Reduce Seats Validation",
            "customerDomainName": "testcustomerr2t2reduce.onmicrosoft.com",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "5357564",
            "resellerMpnId": "4649221",
            "orderId": "94e858b6d855",
            "orderDate": "2021-05-20T18:30:06.6045692Z",
            "productId": "CFQ7TTC0LH0R",
            "skuId": "0002",
            "availabilityId": "CFQ7TTC0K5RQ",
            "productName": "Microsoft 365 Phone System - Virtual User",
            "skuName": "Microsoft 365 Phone System - Virtual User",
            "productQualifiers": [
                "AddOn",
                "Trial"
            ],
            "chargeType": "new",
            "unitPrice": "0",
            "effectiveUnitPrice": "0",
            "unitType": "",
            "quantity": "25",
            "subtotal": "0",
            "taxTotal": "0",
            "totalForCustomer": "0",
            "currency": "USD",
            "publisherName": "Microsoft Corporation",
            "publisherId": "",
            "subscriptionDescription": "",
            "subscriptionId": "86646af9-e80a-4aa0-da80-3fd2b792c2cc",
            "subscriptionStartDate": "2021-05-20T00:00:00Z",
            "subscriptionEndDate": "2021-06-19T00:00:00Z",
            "chargeStartDate": "2021-05-20T00:00:00Z",
            "chargeEndDate": "2021-06-19T00:00:00Z",
            "termAndBillingCycle": "One-Month commitment for trial",
            "alternateId": "94e858b6d855",
            "referenceId": "0cf1202a-5b7d-4219-966e-93c637113708",
            "priceAdjustmentDescription": "",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": "1",
            "pcToBCExchangeRateDate": "2021-05-01T00:00:00",
            "billableQuantity": "25",
            "meterDescription": "",
            "billingFrequency": "",
            "reservationOrderId": "99f246cf-ed96-41b4-b0cd-0aa43eb1fe91",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "promotionId": "",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
            
        },
        {
            "partnerId": "934f3416-bc2f-47f3-b492-77e517d4e572",
            "customerId": "835a59a7-3172-47b5-bdef-d9cc65f4d0e4",
            "customerName": "TEST_TEST Test Promotions 01",
            "customerDomainName": "kyletestpromos01.onmicrosoft.com",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "5357564",
            "resellerMpnId": "0",
            "orderId": "5f9d52bb1408",
            "orderDate": "2021-05-20T18:48:30.6168285Z",
            "productId": "CFQ7TTC0HL8W",
            "skuId": "0001",
            "availabilityId": "CFQ7TTC0K59S",
            "productName": "Power BI Premium Per User",
            "skuName": "Power BI Premium Per User",
            "productQualifiers": [],
            "chargeType": "new",
            "unitPrice": "16",
            "effectiveUnitPrice": "14.4",
            "unitType": "",
            "quantity": "50",
            "subtotal": "720",
            "taxTotal": "0",
            "totalForCustomer": "0",
            "currency": "USD",
            "publisherName": "Microsoft Corporation",
            "publisherId": "",
            "subscriptionDescription": "",
            "subscriptionId": "9d7d1f3d-c8de-461c-db6d-91debd5129f0",
            "subscriptionStartDate": "2021-05-20T00:00:00Z",
            "subscriptionEndDate": "2022-05-19T00:00:00Z",
            "chargeStartDate": "2021-05-20T00:00:00Z",
            "chargeEndDate": "2021-06-19T00:00:00Z",
            "termAndBillingCycle": "One-Year commitment for monthly/yearly billing",
            "alternateId": "5f9d52bb1408",
            "referenceId": "28b535e0-68f4-40b5-84f7-8ed9241eb149",
            "priceAdjustmentDescription": "[\"Price for given billing period\",\"You are getting a discount due to a pre-determined override.\",\"You are getting a discount for being a partner.\",\"You are getting a price guarantee for your price.\",\"Price for given term\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": "1",
            "pcToBCExchangeRateDate": "2021-05-01T00:00:00",
            "billableQuantity": "50",
            "meterDescription": "",
            "billingFrequency": "Monthly",
            "reservationOrderId": "8fdebb4a-7110-496e-9570-623e4c992797",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "promotionId": "78bcf906-b945-4210-8818-cfb93caf12a1",
            "attributes/objectType": "OneTimeInvoiceLineItem",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        },
        {
            "partnerId": "934f3416-bc2f-47f3-b492-77e517d4e572",
            "customerId": "c139c4bf-2e8b-4ab5-8bed-d9f50dcca7a2",
            "customerName": "Test_Test_Office R2 Reduce Seats Validation",
            "customerDomainName": "testcustomerr2t2reduce.onmicrosoft.com",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "1234567",
            "resellerMpnId": 0,
            "orderId": "HJVtMZMkgQ2miuCiNv0RSr51zQDans0m1",
            "orderDate": "2019-02-04T17:59:52.9460102Z",
            "productId": "DZH318Z0BXWC",
            "skuId": "0002",
            "availabilityId": "DZH318Z0BP8B",
            "productName": "Test WAF-as-a-Service",
            "skuName": "Test WaaS - Medium Plan",
            "chargeType": "New",
            "unitPrice": 820,
            "effectiveUnitPrice": 820,
            "unitType": "",
            "quantity": 1,
            "subtotal": 820,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "publisherName": "Test Networks, Inc.",
            "publisherId": "21223810",
            "subscriptionDescription": "",
            "subscriptionId": "12345678-9cf0-4a1f-9514-7fcc7fe9d1fe",
            "subscriptionStartDate": "2019-02-01T00:00:00Z",
            "subscriptionEndDate": "2020-01-31T00:00:00Z",
            "chargeStartDate": "2019-02-04T09:22:40.1767993-08:00",
            "chargeEndDate": "2019-03-03T09:22:40.1767993-08:00",
            "termAndBillingCycle": "1 Year Subscription",
            "alternateId": "123456ad566",
            "priceAdjustmentDescription": "[\"15.0% Partner earned credit for services managed\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "billableQuantity": 3.1618,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "883d475b-0000-1234-0000-8818752f1234",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ]
}
    ],
    "links": {
        "self": {
             "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

#### <a name="request-example-3"></a><span data-ttu-id="cea22-214">Pedido exemplo 3</span><span class="sxs-lookup"><span data-stu-id="cea22-214">Request example 3</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/unbilled/lineitems?provider=OneTime&invoiceLineItemType=UsageLineItems&currencyCode=usd&period=previous&size=2000&seekoperation=next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-3"></a><span data-ttu-id="cea22-215">Exemplo de resposta 3</span><span class="sxs-lookup"><span data-stu-id="cea22-215">Response example 3</span></span>

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
    "totalCount": 3,
    "items": [
        {
            "partnerId": "934f3416-bc2f-47f3-b492-77e517d4e572",
            "customerId": "c139c4bf-2e8b-4ab5-8bed-d9f50dcca7a2",
            "customerName": "Test_Test_Office R2 Reduce Seats Validation",
            "customerDomainName": "testcustomerr2t2reduce.onmicrosoft.com",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "5357564",
            "resellerMpnId": "4649221",
            "orderId": "94e858b6d855",
            "orderDate": "2021-05-20T18:30:06.6045692Z",
            "productId": "CFQ7TTC0LH0R",
            "skuId": "0002",
            "availabilityId": "CFQ7TTC0K5RQ",
            "productName": "Microsoft 365 Phone System - Virtual User",
            "skuName": "Microsoft 365 Phone System - Virtual User",
            "productQualifiers": [
                "AddOn",
                "Trial"
            ],
            "chargeType": "new",
            "unitPrice": "0",
            "effectiveUnitPrice": "0",
            "unitType": "",
            "quantity": "25",
            "subtotal": "0",
            "taxTotal": "0",
            "totalForCustomer": "0",
            "currency": "USD",
            "publisherName": "Microsoft Corporation",
            "publisherId": "",
            "subscriptionDescription": "",
            "subscriptionId": "86646af9-e80a-4aa0-da80-3fd2b792c2cc",
            "subscriptionStartDate": "2021-05-20T00:00:00Z",
            "subscriptionEndDate": "2021-06-19T00:00:00Z",
            "chargeStartDate": "2021-05-20T00:00:00Z",
            "chargeEndDate": "2021-06-19T00:00:00Z",
            "termAndBillingCycle": "One-Month commitment for trial",
            "alternateId": "94e858b6d855",
            "referenceId": "0cf1202a-5b7d-4219-966e-93c637113708",
            "priceAdjustmentDescription": "",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": "1",
            "pcToBCExchangeRateDate": "2021-05-01T00:00:00",
            "billableQuantity": "25",
            "meterDescription": "",
            "billingFrequency": "",
            "reservationOrderId": "99f246cf-ed96-41b4-b0cd-0aa43eb1fe91",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "promotionId": "",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
            
        },
        {
            "partnerId": "934f3416-bc2f-47f3-b492-77e517d4e572",
            "customerId": "835a59a7-3172-47b5-bdef-d9cc65f4d0e4",
            "customerName": "TEST_TEST Test Promotions 01",
            "customerDomainName": "kyletestpromos01.onmicrosoft.com",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "5357564",
            "resellerMpnId": "0",
            "orderId": "5f9d52bb1408",
            "orderDate": "2021-05-20T18:48:30.6168285Z",
            "productId": "CFQ7TTC0HL8W",
            "skuId": "0001",
            "availabilityId": "CFQ7TTC0K59S",
            "productName": "Power BI Premium Per User",
            "skuName": "Power BI Premium Per User",
            "productQualifiers": [],
            "chargeType": "new",
            "unitPrice": "16",
            "effectiveUnitPrice": "14.4",
            "unitType": "",
            "quantity": "50",
            "subtotal": "720",
            "taxTotal": "0",
            "totalForCustomer": "0",
            "currency": "USD",
            "publisherName": "Microsoft Corporation",
            "publisherId": "",
            "subscriptionDescription": "",
            "subscriptionId": "9d7d1f3d-c8de-461c-db6d-91debd5129f0",
            "subscriptionStartDate": "2021-05-20T00:00:00Z",
            "subscriptionEndDate": "2022-05-19T00:00:00Z",
            "chargeStartDate": "2021-05-20T00:00:00Z",
            "chargeEndDate": "2021-06-19T00:00:00Z",
            "termAndBillingCycle": "One-Year commitment for monthly/yearly billing",
            "alternateId": "5f9d52bb1408",
            "referenceId": "28b535e0-68f4-40b5-84f7-8ed9241eb149",
            "priceAdjustmentDescription": "[\"Price for given billing period\",\"You are getting a discount due to a pre-determined override.\",\"You are getting a discount for being a partner.\",\"You are getting a price guarantee for your price.\",\"Price for given term\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": "1",
            "pcToBCExchangeRateDate": "2021-05-01T00:00:00",
            "billableQuantity": "50",
            "meterDescription": "",
            "billingFrequency": "Monthly",
            "reservationOrderId": "8fdebb4a-7110-496e-9570-623e4c992797",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "promotionId": "78bcf906-b945-4210-8818-cfb93caf12a1",
            "attributes/objectType": "OneTimeInvoiceLineItem",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        },
        {
            "partnerId": "934f3416-bc2f-47f3-b492-77e517d4e572",
            "customerId": "c139c4bf-2e8b-4ab5-8bed-d9f50dcca7a2",
            "customerName": "Test_Test_Office R2 Reduce Seats Validation",
            "customerDomainName": "testcustomerr2t2reduce.onmicrosoft.com",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "1234567",
            "resellerMpnId": 0,
            "orderId": "HJVtMZMkgQ2miuCiNv0RSr51zQDans0m1",
            "orderDate": "2019-02-04T17:59:52.9460102Z",
            "productId": "DZH318Z0BXWC",
            "skuId": "0002",
            "availabilityId": "DZH318Z0BP8B",
            "productName": "Test WAF-as-a-Service",
            "skuName": "Test WaaS - Medium Plan",
            "chargeType": "New",
            "unitPrice": 820,
            "effectiveUnitPrice": 820,
            "unitType": "",
            "quantity": 1,
            "subtotal": 820,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "publisherName": "Test Networks, Inc.",
            "publisherId": "21223810",
            "subscriptionDescription": "",
            "subscriptionId": "12345678-9cf0-4a1f-9514-7fcc7fe9d1fe",
            "subscriptionStartDate": "2019-02-01T00:00:00Z",
            "subscriptionEndDate": "2020-01-31T00:00:00Z",
            "chargeStartDate": "2019-02-04T09:22:40.1767993-08:00",
            "chargeEndDate": "2019-03-03T09:22:40.1767993-08:00",
            "termAndBillingCycle": "1 Year Subscription",
            "alternateId": "123456ad566",
            "priceAdjustmentDescription": "[\"15.0% Partner earned credit for services managed\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "billableQuantity": 3.1618,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "883d475b-0000-1234-0000-8818752f1234",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ]
}
    ],
    "links": {
        "self": {
             "uri": "/invoices/unbilled/lineitems?provider=all&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
