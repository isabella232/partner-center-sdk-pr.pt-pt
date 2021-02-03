---
title: Obtenha os itens de linha de reconciliação não faturados da fatura
description: Você pode obter uma coleção de detalhes de item de linha de reconciliação não faturados para o período especificado usando as APIs do Centro parceiro.
ms.date: 01/27/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: ff69798ddfd91fca817ec0d047bf407f326066c2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769853"
---
# <a name="get-invoices-unbilled-reconciliation-line-items"></a><span data-ttu-id="2bfae-103">Obtenha os itens de linha de reconciliação não faturados da fatura</span><span class="sxs-lookup"><span data-stu-id="2bfae-103">Get invoice's unbilled reconciliation line items</span></span>

<span data-ttu-id="2bfae-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="2bfae-104">**Applies to:**</span></span>

- <span data-ttu-id="2bfae-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="2bfae-105">Partner Center</span></span>
- <span data-ttu-id="2bfae-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="2bfae-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="2bfae-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="2bfae-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="2bfae-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2bfae-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2bfae-109">Pode utilizar os seguintes métodos para obter uma recolha de detalhes para itens de linha de fatura não faturados (também conhecidos como itens de linha de faturação aberta).</span><span class="sxs-lookup"><span data-stu-id="2bfae-109">You can use the following methods get a collection of details for unbilled invoice line items (also known as open billing line items).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2bfae-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2bfae-110">Prerequisites</span></span>

- <span data-ttu-id="2bfae-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2bfae-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2bfae-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="2bfae-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="2bfae-113">Um identificador de fatura.</span><span class="sxs-lookup"><span data-stu-id="2bfae-113">An invoice identifier.</span></span> <span data-ttu-id="2bfae-114">Isto identifica a fatura para a recuperação dos itens de linha.</span><span class="sxs-lookup"><span data-stu-id="2bfae-114">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="2bfae-115">C\#</span><span class="sxs-lookup"><span data-stu-id="2bfae-115">C\#</span></span>

<span data-ttu-id="2bfae-116">Para obter os itens de linha para a fatura especificada, recupere o objeto da fatura:</span><span class="sxs-lookup"><span data-stu-id="2bfae-116">To get the line items for the specified invoice, retrieve the invoice object:</span></span>

1. <span data-ttu-id="2bfae-117">Ligue para o método [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) para obter uma interface para as operações de faturação para a fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="2bfae-117">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="2bfae-118">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar o objeto da fatura.</span><span class="sxs-lookup"><span data-stu-id="2bfae-118">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span>

<span data-ttu-id="2bfae-119">O objeto da fatura contém todas as informações para a fatura especificada:</span><span class="sxs-lookup"><span data-stu-id="2bfae-119">The invoice object contains all of the information for the specified invoice:</span></span>

- <span data-ttu-id="2bfae-120">**O fornecedor** identifica a origem das informações de pormenor não bicos (por exemplo, **OneTime**).</span><span class="sxs-lookup"><span data-stu-id="2bfae-120">**Provider** identifies the source of the unbilled detail information (for example, **OneTime**).</span></span>

- <span data-ttu-id="2bfae-121">**FaturaLineItemType** especifica o tipo (por exemplo, **BillingLineItem**).</span><span class="sxs-lookup"><span data-stu-id="2bfae-121">**InvoiceLineItemType** specifies the type (for example, **BillingLineItem**).</span></span>

<span data-ttu-id="2bfae-122">Para obter uma coleção de itens de linha que correspondam a uma instância **FaturaDetail:**</span><span class="sxs-lookup"><span data-stu-id="2bfae-122">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="2bfae-123">Passe o BillingProvider e o InvoiceLineItemType para o método [**Por.**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by)</span><span class="sxs-lookup"><span data-stu-id="2bfae-123">Pass the instance's BillingProvider and InvoiceLineItemType to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="2bfae-124">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar os itens de linha associados.</span><span class="sxs-lookup"><span data-stu-id="2bfae-124">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the associated line items.</span></span>

3. <span data-ttu-id="2bfae-125">Crie um enumerador para atravessar a coleção.</span><span class="sxs-lookup"><span data-stu-id="2bfae-125">Create an enumerator to traverse the collection.</span></span> <span data-ttu-id="2bfae-126">Por exemplo, consulte o seguinte código de amostra.</span><span class="sxs-lookup"><span data-stu-id="2bfae-126">For an example, see the following sample code.</span></span>

<span data-ttu-id="2bfae-127">O seguinte código de amostra utiliza um circuito **de apreensão para** processar a coleção **FaturaLineItems.**</span><span class="sxs-lookup"><span data-stu-id="2bfae-127">The following sample code uses a **foreach** loop to process the **InvoiceLineItems** collection.</span></span> <span data-ttu-id="2bfae-128">Uma coleção separada de itens de linha é recuperada para cada **FaturaLineItemType**.</span><span class="sxs-lookup"><span data-stu-id="2bfae-128">A separate collection of line items is retrieved for each **InvoiceLineItemType**.</span></span>

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

<span data-ttu-id="2bfae-129">Para um exemplo semelhante, consulte:</span><span class="sxs-lookup"><span data-stu-id="2bfae-129">For a similar example, see:</span></span>

- <span data-ttu-id="2bfae-130">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="2bfae-130">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="2bfae-131">Projeto: **Partner Center SDK Samples**</span><span class="sxs-lookup"><span data-stu-id="2bfae-131">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="2bfae-132">Classe: **GetUnBilledReconLineItemsPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="2bfae-132">Class: **GetUnBilledReconLineItemsPaging.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="2bfae-133">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2bfae-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2bfae-134">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bfae-134">Request syntax</span></span>

<span data-ttu-id="2bfae-135">Pode utilizar as seguintes sintaxes para o seu pedido DE REST, dependendo da sua caixa de utilização.</span><span class="sxs-lookup"><span data-stu-id="2bfae-135">You can use the following syntaxes for your REST request, depending on your use case.</span></span> <span data-ttu-id="2bfae-136">Para mais informações, consulte as descrições de cada sintaxe.</span><span class="sxs-lookup"><span data-stu-id="2bfae-136">For more information, see the descriptions for each syntax.</span></span>

 | <span data-ttu-id="2bfae-137">Método</span><span class="sxs-lookup"><span data-stu-id="2bfae-137">Method</span></span>  | <span data-ttu-id="2bfae-138">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2bfae-138">Request URI</span></span>            | <span data-ttu-id="2bfae-139">Descrição do caso de utilização de sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bfae-139">Description of syntax use case</span></span>                                                                                |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2bfae-140">**Obter**</span><span class="sxs-lookup"><span data-stu-id="2bfae-140">**GET**</span></span> | <span data-ttu-id="2bfae-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2bfae-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period} HTTP/1.1</span></span>                              | <span data-ttu-id="2bfae-142">Utilize esta sintaxe para devolver uma lista completa de todos os itens de linha para a fatura dada.</span><span class="sxs-lookup"><span data-stu-id="2bfae-142">Use this syntax to return a full list of every line item for the given invoice.</span></span> |
| <span data-ttu-id="2bfae-143">**Obter**</span><span class="sxs-lookup"><span data-stu-id="2bfae-143">**GET**</span></span> | <span data-ttu-id="2bfae-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2bfae-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span></span>  | <span data-ttu-id="2bfae-145">Para faturas grandes, utilize esta sintaxe com um tamanho especificado e uma compensação baseada em 0 para devolver uma lista de itens de linha paged.</span><span class="sxs-lookup"><span data-stu-id="2bfae-145">For large invoices, use this syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> |
| <span data-ttu-id="2bfae-146">**Obter**</span><span class="sxs-lookup"><span data-stu-id="2bfae-146">**GET**</span></span> | <span data-ttu-id="2bfae-147">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span><span class="sxs-lookup"><span data-stu-id="2bfae-147">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span></span>                               | <span data-ttu-id="2bfae-148">Utilize esta sintaxe para obter a próxima página de itens da linha de reconciliação utilizando `seekOperation = "Next"` .</span><span class="sxs-lookup"><span data-stu-id="2bfae-148">Use this syntax to get the next page of reconciliation line items using `seekOperation = "Next"`.</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="2bfae-149">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="2bfae-149">URI parameters</span></span>

<span data-ttu-id="2bfae-150">Utilize os seguintes parâmetros URI e consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="2bfae-150">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="2bfae-151">Nome</span><span class="sxs-lookup"><span data-stu-id="2bfae-151">Name</span></span>                   | <span data-ttu-id="2bfae-152">Tipo</span><span class="sxs-lookup"><span data-stu-id="2bfae-152">Type</span></span>   | <span data-ttu-id="2bfae-153">Necessário</span><span class="sxs-lookup"><span data-stu-id="2bfae-153">Required</span></span> | <span data-ttu-id="2bfae-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bfae-154">Description</span></span>                                                                     |
|------------------------|--------|----------|---------------------------------------------------------------------------------|
| <span data-ttu-id="2bfae-155">fatura id</span><span class="sxs-lookup"><span data-stu-id="2bfae-155">invoice-id</span></span>             | <span data-ttu-id="2bfae-156">string</span><span class="sxs-lookup"><span data-stu-id="2bfae-156">string</span></span> | <span data-ttu-id="2bfae-157">Sim</span><span class="sxs-lookup"><span data-stu-id="2bfae-157">Yes</span></span>      | <span data-ttu-id="2bfae-158">Uma corda que identifica a fatura.</span><span class="sxs-lookup"><span data-stu-id="2bfae-158">A string that identifies the invoice.</span></span> <span data-ttu-id="2bfae-159">Use 'sem bico' para obter estimativas não mediadas.</span><span class="sxs-lookup"><span data-stu-id="2bfae-159">Use 'unbilled' to get unbilled estimates.</span></span> |
| <span data-ttu-id="2bfae-160">provedor</span><span class="sxs-lookup"><span data-stu-id="2bfae-160">provider</span></span>               | <span data-ttu-id="2bfae-161">string</span><span class="sxs-lookup"><span data-stu-id="2bfae-161">string</span></span> | <span data-ttu-id="2bfae-162">Sim</span><span class="sxs-lookup"><span data-stu-id="2bfae-162">Yes</span></span>      | <span data-ttu-id="2bfae-163">O provedor: "OneTime".</span><span class="sxs-lookup"><span data-stu-id="2bfae-163">The provider: "OneTime".</span></span>                                                |
| <span data-ttu-id="2bfae-164">tipo de artigo de linha de fatura</span><span class="sxs-lookup"><span data-stu-id="2bfae-164">invoice-line-item-type</span></span> | <span data-ttu-id="2bfae-165">string</span><span class="sxs-lookup"><span data-stu-id="2bfae-165">string</span></span> | <span data-ttu-id="2bfae-166">Sim</span><span class="sxs-lookup"><span data-stu-id="2bfae-166">Yes</span></span>      | <span data-ttu-id="2bfae-167">O tipo de detalhe de fatura: "BillingLineItems".</span><span class="sxs-lookup"><span data-stu-id="2bfae-167">The type of invoice detail: "BillingLineItems".</span></span>               |
| <span data-ttu-id="2bfae-168">hasPartnerEarnedCredit</span><span class="sxs-lookup"><span data-stu-id="2bfae-168">hasPartnerEarnedCredit</span></span> | <span data-ttu-id="2bfae-169">bool</span><span class="sxs-lookup"><span data-stu-id="2bfae-169">bool</span></span>   | <span data-ttu-id="2bfae-170">Não</span><span class="sxs-lookup"><span data-stu-id="2bfae-170">No</span></span>       | <span data-ttu-id="2bfae-171">O valor indicando se devolver os itens de linha com o parceiro ganhou crédito aplicado.</span><span class="sxs-lookup"><span data-stu-id="2bfae-171">The value indicating if to return the line items with partner earned credit applied.</span></span> <span data-ttu-id="2bfae-172">Nota: este parâmetro só será aplicado quando o tipo de fornecedor for OneTime e o InvoiceLineItemType for UsageLineItems.</span><span class="sxs-lookup"><span data-stu-id="2bfae-172">Note: this parameter will be only applied when provider type is OneTime and InvoiceLineItemType is UsageLineItems.</span></span>
| <span data-ttu-id="2bfae-173">currencyCode</span><span class="sxs-lookup"><span data-stu-id="2bfae-173">currencyCode</span></span>           | <span data-ttu-id="2bfae-174">string</span><span class="sxs-lookup"><span data-stu-id="2bfae-174">string</span></span> | <span data-ttu-id="2bfae-175">Sim</span><span class="sxs-lookup"><span data-stu-id="2bfae-175">Yes</span></span>      | <span data-ttu-id="2bfae-176">O código cambial para os itens de linha não bico.</span><span class="sxs-lookup"><span data-stu-id="2bfae-176">The currency code for the unbilled line items.</span></span>                                  |
| <span data-ttu-id="2bfae-177">period</span><span class="sxs-lookup"><span data-stu-id="2bfae-177">period</span></span>                 | <span data-ttu-id="2bfae-178">string</span><span class="sxs-lookup"><span data-stu-id="2bfae-178">string</span></span> | <span data-ttu-id="2bfae-179">Sim</span><span class="sxs-lookup"><span data-stu-id="2bfae-179">Yes</span></span>      | <span data-ttu-id="2bfae-180">O período para reconhecimento não-marcado.</span><span class="sxs-lookup"><span data-stu-id="2bfae-180">The period for unbilled recon.</span></span> <span data-ttu-id="2bfae-181">exemplo: corrente, anterior.</span><span class="sxs-lookup"><span data-stu-id="2bfae-181">example: current, previous.</span></span>                      |
| <span data-ttu-id="2bfae-182">size</span><span class="sxs-lookup"><span data-stu-id="2bfae-182">size</span></span>                   | <span data-ttu-id="2bfae-183">número</span><span class="sxs-lookup"><span data-stu-id="2bfae-183">number</span></span> | <span data-ttu-id="2bfae-184">Não</span><span class="sxs-lookup"><span data-stu-id="2bfae-184">No</span></span>       | <span data-ttu-id="2bfae-185">O número máximo de itens para devolver.</span><span class="sxs-lookup"><span data-stu-id="2bfae-185">The maximum number of items to return.</span></span> <span data-ttu-id="2bfae-186">O tamanho padrão é 2000</span><span class="sxs-lookup"><span data-stu-id="2bfae-186">Default size is 2000</span></span>                     |
| <span data-ttu-id="2bfae-187">procurarOperação</span><span class="sxs-lookup"><span data-stu-id="2bfae-187">seekOperation</span></span>          | <span data-ttu-id="2bfae-188">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="2bfae-188">string</span></span> | <span data-ttu-id="2bfae-189">No</span><span class="sxs-lookup"><span data-stu-id="2bfae-189">No</span></span>       | <span data-ttu-id="2bfae-190">Desaperte a procuraOperação=Próxima para obter a próxima página de itens de linha de reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="2bfae-190">Set seekOperation=Next to get the next page of recon line items.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="2bfae-191">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2bfae-191">Request headers</span></span>

<span data-ttu-id="2bfae-192">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2bfae-192">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2bfae-193">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="2bfae-193">Request body</span></span>

<span data-ttu-id="2bfae-194">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2bfae-194">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="2bfae-195">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2bfae-195">REST response</span></span>

<span data-ttu-id="2bfae-196">Se for bem sucedida, a resposta contém a recolha de detalhes do item da linha.</span><span class="sxs-lookup"><span data-stu-id="2bfae-196">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="2bfae-197">*Para o item da linha **ChargeType,** o valor **Compra** é mapeado para **Novo** e o valor **Reembolso** está mapeado para **Cancelar**.*</span><span class="sxs-lookup"><span data-stu-id="2bfae-197">*For the line item **ChargeType**, the value **Purchase** is mapped to **New** and the value **Refund** is mapped to **Cancel**.*</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2bfae-198">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2bfae-198">Response success and error codes</span></span>

<span data-ttu-id="2bfae-199">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2bfae-199">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2bfae-200">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2bfae-200">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2bfae-201">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2bfae-201">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="request-response-examples"></a><span data-ttu-id="2bfae-202">Exemplos de resposta a pedidos</span><span class="sxs-lookup"><span data-stu-id="2bfae-202">Request-response examples</span></span>

#### <a name="request-response-example-1"></a><span data-ttu-id="2bfae-203">Exemplo de resposta a pedido 1</span><span class="sxs-lookup"><span data-stu-id="2bfae-203">Request-response example 1</span></span>

<span data-ttu-id="2bfae-204">Os seguintes detalhes aplicam-se a este exemplo:</span><span class="sxs-lookup"><span data-stu-id="2bfae-204">The following details apply to this example:</span></span>

- <span data-ttu-id="2bfae-205">Fornecedor: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="2bfae-205">Provider: **OneTime**</span></span>
- <span data-ttu-id="2bfae-206">FaturaLineItemType: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="2bfae-206">InvoiceLineItemType: **BillingLineItems**</span></span>
- <span data-ttu-id="2bfae-207">Período: **Anterior**</span><span class="sxs-lookup"><span data-stu-id="2bfae-207">Period: **Previous**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="2bfae-208">Pedido exemplo 1</span><span class="sxs-lookup"><span data-stu-id="2bfae-208">Request example 1</span></span>

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

#### <a name="response-example-1"></a><span data-ttu-id="2bfae-209">Exemplo de resposta 1</span><span class="sxs-lookup"><span data-stu-id="2bfae-209">Response example 1</span></span>

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
            "partnerId": "0c924e8d-4852-4692-a4d7-7dd0dc09ad80",
            "customerId": "org:d7f565f5-5367-492f-a465-9e2057c5e3c3",
            "customerName": "TEST_TEST_GTM1",
            "customerDomainName": "TESTTESTGTM1.ccsctp.net",
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
            "chargeStartDate": "2019-02-04T09:22:40.1767993-08:00",
            "chargeEndDate": "2019-03-03T09:22:40.1767993-08:00",
            "termAndBillingCycle": "1 Month Subscription",
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
        },
        {
            "partnerId": "0c924e8d-4852-4692-a4d7-7dd0dc09ad80",
            "customerId": "org:d7f565f5-5367-492f-a465-9e2057c5e3c3",
            "customerName": "TEST_TEST_GTM1",
            "customerDomainName": "TESTTESTGTM1.ccsctp.net",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "1234567",
            "resellerMpnId": 0,
            "orderId": "Oi2kwDPEOyGEFUkESk3QR4XSxcpvwp1x1",
            "orderDate": "2019-02-04T17:59:53.1628078Z",
            "productId": "DZH318Z0BXWC",
            "skuId": "0005",
            "availabilityId": "DZH318Z0BH9R",
            "productName": "Test WAF-as-a-Service",
            "skuName": "Test WaaS - Large Plan",
            "chargeType": "New",
            "unitPrice": 2598,
            "effectiveUnitPrice": 2598,
            "unitType": "",
            "quantity": 1,
            "subtotal": 2598,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "publisherName": "Test Networks, Inc.",
            "publisherId": "21223810",
            "subscriptionDescription": "",
            "subscriptionId": "12345678-28db-48c2-8c30-04d7c9455746",
            "chargeStartDate": "2019-02-04T09:22:34.6455294-08:00",
            "chargeEndDate": "2019-03-03T09:22:34.6455294-08:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "123456ad566",
            "priceAdjustmentDescription": "[\"15.0% Partner earned credit for services managed\",\"100.0% Tier 1 Discount\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "billableQuantity": 0.737083,
            "meterDescription": "",
            "reservationOrderId": "883d475b-0000-2222-0000-8818752f1234",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
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

### <a name="request-response-example-2"></a><span data-ttu-id="2bfae-210">Exemplo de resposta a pedido 2</span><span class="sxs-lookup"><span data-stu-id="2bfae-210">Request-response example 2</span></span>

<span data-ttu-id="2bfae-211">Os seguintes detalhes aplicam-se a este exemplo:</span><span class="sxs-lookup"><span data-stu-id="2bfae-211">The following details apply to this example:</span></span>

- <span data-ttu-id="2bfae-212">Fornecedor: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="2bfae-212">Provider: **OneTime**</span></span>
- <span data-ttu-id="2bfae-213">FaturaLineItemType: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="2bfae-213">InvoiceLineItemType: **BillingLineItems**</span></span>
- <span data-ttu-id="2bfae-214">Período: **Anterior**</span><span class="sxs-lookup"><span data-stu-id="2bfae-214">Period: **Previous**</span></span>
- <span data-ttu-id="2bfae-215">SeekOperation: **Next**</span><span class="sxs-lookup"><span data-stu-id="2bfae-215">SeekOperation: **Next**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="2bfae-216">Pedido exemplo 2</span><span class="sxs-lookup"><span data-stu-id="2bfae-216">Request example 2</span></span>

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

#### <a name="response-example-2"></a><span data-ttu-id="2bfae-217">Exemplo de resposta 2</span><span class="sxs-lookup"><span data-stu-id="2bfae-217">Response example 2</span></span>

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
            "partnerId": "0c924e8d-4852-4692-a4d7-7dd0dc09ad80",
            "customerId": "org:d7f565f5-5367-492f-a465-9e2057c5e3c3",
            "customerName": "TEST_TEST_GTM1",
            "customerDomainName": "TESTTESTGTM1.ccsctp.net",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "1234567",
            "resellerMpnId": 0,
            "orderId": "Oi2kwDPEOyGEFUkESk3QR4XSxcpvwp1x1",
            "orderDate": "2019-02-04T17:59:53.1628078Z",
            "productId": "DZH318Z0BXWC",
            "skuId": "0005",
            "availabilityId": "DZH318Z0BH9R",
            "productName": "Test WAF-as-a-Service",
            "skuName": "Test WaaS - Large Plan",
            "chargeType": "New",
            "unitPrice": 2598,
            "effectiveUnitPrice": 2598,
            "unitType": "",
            "quantity": 1,
            "subtotal": 2598,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "publisherName": "Test Networks, Inc.",
            "publisherId": "21223810",
            "subscriptionDescription": "",
            "subscriptionId": "12345678-28db-48c2-8c30-04d7c9455746",
            "chargeStartDate": "2019-02-04T09:22:34.6455294-08:00",
            "chargeEndDate": "2019-03-03T09:22:34.6455294-08:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "123456ad566",
            "priceAdjustmentDescription": "[\"15.0% Partner earned credit for services managed\",\"100.0% Tier 1 Discount\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "billableQuantity": 0.737083,
            "meterDescription": "",
            "reservationOrderId": ""
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
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

#### <a name="request-example-3"></a><span data-ttu-id="2bfae-218">Pedido exemplo 3</span><span class="sxs-lookup"><span data-stu-id="2bfae-218">Request example 3</span></span>

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

#### <a name="response-example-3"></a><span data-ttu-id="2bfae-219">Exemplo de resposta 3</span><span class="sxs-lookup"><span data-stu-id="2bfae-219">Response example 3</span></span>

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
            "partnerId": "0c924e8d-4852-4692-a4d7-7dd0dc09ad80",
            "PartnerName": "testPartner",
            "customerId": "org:d7f565f5-5367-492f-a465-9e2057c5e3c3",
            "customerName": "TEST_TEST_GTM1",
            "customerDomainName": "TESTTESTGTM1.ccsctp.net",
            "invoiceNumber": "T11ETHHDDD",
            "productId": "DZH318Z0BXWC",
            "skuId": "0005",
            "availabilityId": "DZH318Z0BH9R",
            "productName": "Test WAF-as-a-Service",
            "publisherId": "21223810",
            "subscriptionId": "12345678-28db-48c2-8c30-04d7c9455746",
            "subscriptionDescription": "sub description",
            "chargeStartDate": "2019-02-04T09:22:34.6455294-08:00",
            "chargeEndDate": "2019-03-03T09:22:34.6455294-08:00",
            "UsageDate": "2019-02-07T09:22:34.6455294-08:00",
            "MeterType": "type",
            "MeterCategory": "category",
            "MeterId": "21312312312-fdsfsd",
            "MeterSubCategory": "subcategory",
            "MeterName": "meter name",
            "MeterRegion": "meter region",
            "UnitOfMeasure": "11",
            "skuName": "Test WaaS - Large Plan",
            "publisherName": "Test Networks, Inc.",
            "chargeType": "New",
            "unitPrice": 2598,
            "effectiveUnitPrice": 2598,
            "unitType": "",
            "quantity": 1,
            "subtotal": 2598,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "123456ad566",
            "discountDetails": "",
            "providerSource": "All",
            "RateOfPartnerEarnedCredit": 0.15,
            "IsPartnerEarnedCreditApplied": true,
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
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
