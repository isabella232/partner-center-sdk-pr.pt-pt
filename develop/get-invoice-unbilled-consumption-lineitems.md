---
title: Obter faturas sem fatura de produtos de linha de consumo comercial
description: Você pode obter uma coleção de detalhes de item de linha de consumo comercial não faturado para uma fatura especificada usando as APIs do Partner Center.
ms.date: 01/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1b7dba3333aaec8df73f0e8147b0bbbc78b9b184
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446151"
---
# <a name="get-invoice-unbilled-commercial-consumption-line-items"></a><span data-ttu-id="757c4-103">Obter faturas sem fatura de produtos de linha de consumo comercial</span><span class="sxs-lookup"><span data-stu-id="757c4-103">Get invoice unbilled commercial consumption line items</span></span>

<span data-ttu-id="757c4-104">Como obter uma coleção de detalhes de linha de consumo comercial não bico.</span><span class="sxs-lookup"><span data-stu-id="757c4-104">How to get a collection of unbilled commercial consumption line item details.</span></span>

<span data-ttu-id="757c4-105">Pode utilizar os seguintes métodos para obter uma recolha de detalhes de linha de consumo comercial não bico (também conhecidos como itens de linha de uso aberto) programáticamente.</span><span class="sxs-lookup"><span data-stu-id="757c4-105">You can use the following methods to get a collection of details unbilled commercial consumption line items (also known as open usage line items) programmatically.</span></span>

>[!NOTE]
><span data-ttu-id="757c4-106">O uso diário normalmente demora 24 horas a aparecer no Partner Center ou a ser acedido através da API.</span><span class="sxs-lookup"><span data-stu-id="757c4-106">Daily-rated usage normally takes 24 hours to appear in Partner Center or to be accessed through the API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="757c4-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="757c4-107">Prerequisites</span></span>

- <span data-ttu-id="757c4-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="757c4-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="757c4-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="757c4-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="757c4-110">Um identificador de fatura.</span><span class="sxs-lookup"><span data-stu-id="757c4-110">An invoice identifier.</span></span> <span data-ttu-id="757c4-111">Isto identifica a fatura para a recuperação dos itens de linha.</span><span class="sxs-lookup"><span data-stu-id="757c4-111">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="757c4-112">C\#</span><span class="sxs-lookup"><span data-stu-id="757c4-112">C\#</span></span>

<span data-ttu-id="757c4-113">Para obter os itens de linha para a fatura especificada:</span><span class="sxs-lookup"><span data-stu-id="757c4-113">To get the line items for the specified invoice:</span></span>

1. <span data-ttu-id="757c4-114">Ligue para o método [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) para obter uma interface para as operações de faturação para a fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="757c4-114">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="757c4-115">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar o objeto da fatura.</span><span class="sxs-lookup"><span data-stu-id="757c4-115">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span>

<span data-ttu-id="757c4-116">O objeto da **fatura** contém todas as informações para a fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="757c4-116">The **invoice object** contains all of the information for the specified invoice.</span></span> <span data-ttu-id="757c4-117">O **Fornecedor** identifica a origem das informações de pormenor não bicos (por exemplo, **OneTime**).</span><span class="sxs-lookup"><span data-stu-id="757c4-117">The **Provider** identifies the source of the unbilled detail information (for example, **OneTime**).</span></span> <span data-ttu-id="757c4-118">A **FaturaLineItemType** especifica o tipo (por exemplo, **UsageLineItem**).</span><span class="sxs-lookup"><span data-stu-id="757c4-118">The **InvoiceLineItemType** specifies the type (for example, **UsageLineItem**).</span></span>

<span data-ttu-id="757c4-119">O seguinte código exemplo utiliza um circuito **de apreensão para** processar a coleção **FaturaLineItems.**</span><span class="sxs-lookup"><span data-stu-id="757c4-119">The following example code uses a **foreach** loop to process the **InvoiceLineItems** collection.</span></span> <span data-ttu-id="757c4-120">Uma coleção separada de itens de linha é recuperada para cada **FaturaLineItemType**.</span><span class="sxs-lookup"><span data-stu-id="757c4-120">A separate collection of line items is retrieved for each **InvoiceLineItemType**.</span></span>

<span data-ttu-id="757c4-121">Para obter uma coleção de itens de linha que correspondam a uma instância **FaturaDetail:**</span><span class="sxs-lookup"><span data-stu-id="757c4-121">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="757c4-122">Passe o **BillingProvider** e **o InvoiceLineItemType** para o método [**Por.**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by)</span><span class="sxs-lookup"><span data-stu-id="757c4-122">Pass the instance's **BillingProvider** and **InvoiceLineItemType** to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="757c4-123">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar os itens de linha associados.</span><span class="sxs-lookup"><span data-stu-id="757c4-123">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the associated line items.</span></span>
3. <span data-ttu-id="757c4-124">Crie um enumerador para atravessar a coleção como mostrado no exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="757c4-124">Create an enumerator to traverse the collection as shown in the following example.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string curencyCode;
// string period;
// int pageMaxSizeReconLineItems = 2000;

// all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

var seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById("unbilled").By("onetime", "usagelineitems", curencyCode, period, pageMaxSizeReconLineItems).Get();

var fetchNext = true;

ConsoleKeyInfo keyInfo;

var itemNumber = 1;
while (fetchNext)
{
    Console.Out.WriteLine("\tLine items count: " + seekBasedResourceCollection.Items.Count());

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
            seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById("unbilled").By("onetime", "usagelineitems", curencyCode, period, pageMaxSizeReconLineItems).Seek(seekBasedResourceCollection.ContinuationToken, SeekOperation.Next);
        }
    }
}
```

<span data-ttu-id="757c4-125">Para um exemplo semelhante, consulte:</span><span class="sxs-lookup"><span data-stu-id="757c4-125">For a similar example, see:</span></span>

- <span data-ttu-id="757c4-126">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="757c4-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="757c4-127">Project: **Amostras SDK do Centro Parceiro**</span><span class="sxs-lookup"><span data-stu-id="757c4-127">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="757c4-128">Classe: **GetUnBilledConsumptionReconLineItemsPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="757c4-128">Class: **GetUnBilledConsumptionReconLineItemsPaging.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="757c4-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="757c4-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="757c4-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="757c4-130">Request syntax</span></span>

<span data-ttu-id="757c4-131">Pode utilizar as seguintes sintaxes para o seu pedido DE REST, dependendo da sua caixa de utilização.</span><span class="sxs-lookup"><span data-stu-id="757c4-131">You can use the following syntaxes for your REST request, depending on your use case.</span></span> <span data-ttu-id="757c4-132">Para mais informações, consulte as descrições de cada sintaxe.</span><span class="sxs-lookup"><span data-stu-id="757c4-132">For more information, see the descriptions for each syntax.</span></span>

| <span data-ttu-id="757c4-133">Método</span><span class="sxs-lookup"><span data-stu-id="757c4-133">Method</span></span>  | <span data-ttu-id="757c4-134">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="757c4-134">Request URI</span></span>                                                                                                                                                                                              | <span data-ttu-id="757c4-135">Descrição do caso de utilização de sintaxe</span><span class="sxs-lookup"><span data-stu-id="757c4-135">Description of syntax use case</span></span>                                                                                                     |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="757c4-136">**Obter**</span><span class="sxs-lookup"><span data-stu-id="757c4-136">**GET**</span></span> | <span data-ttu-id="757c4-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="757c4-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period} HTTP/1.1</span></span>                       | <span data-ttu-id="757c4-138">Utilize esta sintaxe para devolver uma lista completa de todos os itens de linha para a fatura dada.</span><span class="sxs-lookup"><span data-stu-id="757c4-138">Use this syntax to return a full list of every line item for the given invoice.</span></span>                                                    |
| <span data-ttu-id="757c4-139">**Obter**</span><span class="sxs-lookup"><span data-stu-id="757c4-139">**GET**</span></span> | <span data-ttu-id="757c4-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="757c4-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span></span>           | <span data-ttu-id="757c4-141">Utilize esta sintaxe para faturas grandes.</span><span class="sxs-lookup"><span data-stu-id="757c4-141">Use this syntax for large invoices.</span></span> <span data-ttu-id="757c4-142">Utilize esta sintaxe com um tamanho especificado e uma compensação baseada em 0 para devolver uma lista de itens de linha paged.</span><span class="sxs-lookup"><span data-stu-id="757c4-142">Use this syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> |
| <span data-ttu-id="757c4-143">**Obter**</span><span class="sxs-lookup"><span data-stu-id="757c4-143">**GET**</span></span> | <span data-ttu-id="757c4-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span><span class="sxs-lookup"><span data-stu-id="757c4-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span></span> | <span data-ttu-id="757c4-145">Utilize esta sintaxe para obter a próxima página de itens da linha de reconciliação utilizando `seekOperation = "Next"` .</span><span class="sxs-lookup"><span data-stu-id="757c4-145">Use this syntax to get the next page of reconciliation line items using `seekOperation = "Next"`.</span></span>                                  |

#### <a name="uri-parameters"></a><span data-ttu-id="757c4-146">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="757c4-146">URI parameters</span></span>

<span data-ttu-id="757c4-147">Utilize os seguintes parâmetros URI e consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="757c4-147">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="757c4-148">Nome</span><span class="sxs-lookup"><span data-stu-id="757c4-148">Name</span></span>                   | <span data-ttu-id="757c4-149">Tipo</span><span class="sxs-lookup"><span data-stu-id="757c4-149">Type</span></span>   | <span data-ttu-id="757c4-150">Necessário</span><span class="sxs-lookup"><span data-stu-id="757c4-150">Required</span></span> | <span data-ttu-id="757c4-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="757c4-151">Description</span></span>                                                                                                                                                                                                                                |
|------------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="757c4-152">provedor</span><span class="sxs-lookup"><span data-stu-id="757c4-152">provider</span></span>               | <span data-ttu-id="757c4-153">string</span><span class="sxs-lookup"><span data-stu-id="757c4-153">string</span></span> | <span data-ttu-id="757c4-154">Yes</span><span class="sxs-lookup"><span data-stu-id="757c4-154">Yes</span></span>      | <span data-ttu-id="757c4-155">O fornecedor: "**OneTime**".</span><span class="sxs-lookup"><span data-stu-id="757c4-155">The provider: "**OneTime**".</span></span>                                                                                                                                                                                                               |
| <span data-ttu-id="757c4-156">tipo de artigo de linha de fatura</span><span class="sxs-lookup"><span data-stu-id="757c4-156">invoice-line-item-type</span></span> | <span data-ttu-id="757c4-157">string</span><span class="sxs-lookup"><span data-stu-id="757c4-157">string</span></span> | <span data-ttu-id="757c4-158">Yes</span><span class="sxs-lookup"><span data-stu-id="757c4-158">Yes</span></span>      | <span data-ttu-id="757c4-159">O tipo de detalhe de fatura: "**UsageLineItems**", "**UsageLineItems**".</span><span class="sxs-lookup"><span data-stu-id="757c4-159">The type of invoice detail: "**UsageLineItems**", "**UsageLineItems**".</span></span>                                                                                                                                                                    |
| <span data-ttu-id="757c4-160">currencyCode</span><span class="sxs-lookup"><span data-stu-id="757c4-160">currencyCode</span></span>           | <span data-ttu-id="757c4-161">string</span><span class="sxs-lookup"><span data-stu-id="757c4-161">string</span></span> | <span data-ttu-id="757c4-162">Yes</span><span class="sxs-lookup"><span data-stu-id="757c4-162">Yes</span></span>      | <span data-ttu-id="757c4-163">O código cambial para os itens de linha não bico.</span><span class="sxs-lookup"><span data-stu-id="757c4-163">The currency code for the unbilled line items.</span></span>                                                                                                                                                                                             |
| <span data-ttu-id="757c4-164">period</span><span class="sxs-lookup"><span data-stu-id="757c4-164">period</span></span>                 | <span data-ttu-id="757c4-165">string</span><span class="sxs-lookup"><span data-stu-id="757c4-165">string</span></span> | <span data-ttu-id="757c4-166">Yes</span><span class="sxs-lookup"><span data-stu-id="757c4-166">Yes</span></span>      | <span data-ttu-id="757c4-167">O período de reconhecimento não bico (por exemplo: **atual,** **anterior).**</span><span class="sxs-lookup"><span data-stu-id="757c4-167">The period for unbilled recon (for example: **current**, **previous**).</span></span> <span data-ttu-id="757c4-168">Suponha que precisa de consultar os seus dados de utilização não faturados do ciclo de faturação (01/01/2020 – 01/31/2020) em janeiro, escolha o período como **"Corrente",** caso contrário **"Anterior".**</span><span class="sxs-lookup"><span data-stu-id="757c4-168">Suppose you need to query your unbilled usage data of the billing cycle (01/01/2020 – 01/31/2020) in January, choose period as **"Current,"** else **"Previous."**</span></span> |
| <span data-ttu-id="757c4-169">size</span><span class="sxs-lookup"><span data-stu-id="757c4-169">size</span></span>                   | <span data-ttu-id="757c4-170">número</span><span class="sxs-lookup"><span data-stu-id="757c4-170">number</span></span> | <span data-ttu-id="757c4-171">No</span><span class="sxs-lookup"><span data-stu-id="757c4-171">No</span></span>       | <span data-ttu-id="757c4-172">O número máximo de itens para devolver.</span><span class="sxs-lookup"><span data-stu-id="757c4-172">The maximum number of items to return.</span></span> <span data-ttu-id="757c4-173">O tamanho padrão é 2000.</span><span class="sxs-lookup"><span data-stu-id="757c4-173">The default size is 2000.</span></span>                                                                                                                                                                           |
| <span data-ttu-id="757c4-174">procurarOperação</span><span class="sxs-lookup"><span data-stu-id="757c4-174">seekOperation</span></span>          | <span data-ttu-id="757c4-175">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="757c4-175">string</span></span> | <span data-ttu-id="757c4-176">No</span><span class="sxs-lookup"><span data-stu-id="757c4-176">No</span></span>       | <span data-ttu-id="757c4-177">Prepare `seekOperation=Next` para obter a próxima página de itens da linha de reconciliação.</span><span class="sxs-lookup"><span data-stu-id="757c4-177">Set `seekOperation=Next` to get the next page of reconciliation line items.</span></span>                                                                                                                                                                |

### <a name="request-headers"></a><span data-ttu-id="757c4-178">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="757c4-178">Request headers</span></span>

<span data-ttu-id="757c4-179">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="757c4-179">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="757c4-180">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="757c4-180">Request body</span></span>

<span data-ttu-id="757c4-181">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="757c4-181">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="757c4-182">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="757c4-182">REST response</span></span>

<span data-ttu-id="757c4-183">Se for bem sucedida, a resposta contém a recolha de detalhes do item da linha.</span><span class="sxs-lookup"><span data-stu-id="757c4-183">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="757c4-184">*Para o item da linha **ChargeType,** o valor **Compra** é mapeado para **Novo** e o valor **Reembolso** está mapeado para **Cancelar**.*</span><span class="sxs-lookup"><span data-stu-id="757c4-184">*For the line item **ChargeType**, the value **Purchase** is mapped to **New** and the value **Refund** is mapped to **Cancel**.*</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="757c4-185">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="757c4-185">Response success and error codes</span></span>

<span data-ttu-id="757c4-186">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="757c4-186">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="757c4-187">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="757c4-187">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="757c4-188">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="757c4-188">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

## <a name="request-response-examples"></a><span data-ttu-id="757c4-189">Exemplos de resposta a pedidos</span><span class="sxs-lookup"><span data-stu-id="757c4-189">Request-response examples</span></span>

### <a name="request-response-example-1"></a><span data-ttu-id="757c4-190">Exemplo de resposta a pedido 1</span><span class="sxs-lookup"><span data-stu-id="757c4-190">Request-response example 1</span></span>

<span data-ttu-id="757c4-191">Os seguintes detalhes aplicam-se a este exemplo:</span><span class="sxs-lookup"><span data-stu-id="757c4-191">The following details apply to this example:</span></span>

- <span data-ttu-id="757c4-192">**Fornecedor**: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="757c4-192">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="757c4-193">**FaturaLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="757c4-193">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="757c4-194">**Período**: **Anterior**</span><span class="sxs-lookup"><span data-stu-id="757c4-194">**Period**: **Previous**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="757c4-195">Pedido exemplo 1</span><span class="sxs-lookup"><span data-stu-id="757c4-195">Request example 1</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1//invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

### <a name="response-example-1"></a><span data-ttu-id="757c4-196">Exemplo de resposta 1</span><span class="sxs-lookup"><span data-stu-id="757c4-196">Response example 1</span></span>

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
            "partnerId": "00083575-bbd0-54de-b2ad-0f5b0e927d71",
            "partnerName": "MTBC",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "VM-Series Next-Generation Firewall (Bundle 2 PAYG)",
            "productName": "VM-Series Next Generation Firewall",
            "publisherName": "Test Alto Networks, Inc.",
            "publisherId": "",
            "subscriptionId": "12345678-04d9-421c-baf8-e3b8dd62ddba",
            "subscriptionDescription": "Pay-As-You-Go",
            "chargeStartDate": "2019-01-01T00:00:00Z",
            "chargeEndDate": "2019-02-01T00:00:00Z",
            "usageDate": "2019-01-01T00:00:00Z",
            "meterType": "1 Compute Hour - 4core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "4core",
            "meterSubCategory": "VM-Series Next Generation Firewall",
            "meterName": "VM-Series Next Generation Firewall - VM-Series Next-Generation Firewall (Bundle 2 PAYG) - 4 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "ECH-PAN-RG",
            "resourceUri": "/subscriptions/12345678-04d9-421c-baf8-e3b8dd62ddba/resourceGroups/ECH-PAN-RG/providers/Microsoft.Compute/virtualMachines/echpanfw",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_D3_v2\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "",
            "unitPrice": 1.2799888920023,
            "quantity": 24.0,
            "unitType": "",
            "billingPreTaxTotal": 30.7197334080551,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 30.7197334080551,
            "pricingCurrency": "USD",
            "entitlementId": "1234547f-b249-4edd-9319-637862d8c0b4",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0,
            "rateOfPartnerEarnedCredit": 0,
            "rateOfCredit": 0,
            "creditType": "Credit Not Applied",
            "invoiceLineItemType": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
         },
         {
            "partnerId": "00083575-bbd0-54de-b2ad-0f5b0e927d71",
            "partnerName": "MTBC",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "VM-Series Next-Generation Firewall (Bundle 2 PAYG)",
            "productName": "VM-Series Next Generation Firewall",
            "publisherName": "Test Alto Networks, Inc.",
            "publisherId": "",
            "subscriptionId": "12345678-04d9-421c-baf8-e3b8dd62ddba",
            "subscriptionDescription": "Pay-As-You-Go",
            "chargeStartDate": "2019-01-01T00:00:00Z",
            "chargeEndDate": "2019-02-01T00:00:00Z",
            "usageDate": "2019-01-02T00:00:00Z",
            "meterType": "1 Compute Hour - 4core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "4core",
            "meterSubCategory": "VM-Series Next Generation Firewall",
            "meterName": "VM-Series Next Generation Firewall - VM-Series Next-Generation Firewall (Bundle 2 PAYG) - 4 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "ECH-PAN-RG",
            "resourceUri": "/subscriptions/12345678-04d9-421c-baf8-e3b8dd62ddba/resourceGroups/ECH-PAN-RG/providers/Microsoft.Compute/virtualMachines/echpanfw",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_D3_v2\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "",
            "unitPrice": 1.2799888920023,
            "quantity": 24.0,
            "unitType": "",
            "billingPreTaxTotal": 30.7197334080551,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 30.7197334080551,
            "pricingCurrency": "USD",
            "entitlementId": "31cdf47f-b249-4edd-9319-637862d12345",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0,
            "rateOfPartnerEarnedCredit": 0,
            "rateOfCredit": 1,
            "creditType": "Azure Credit Applied",
            "invoiceLineItemTypce": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000&seekOperation=Next",
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

### <a name="request-response-example-2"></a><span data-ttu-id="757c4-197">Exemplo de resposta a pedido 2</span><span class="sxs-lookup"><span data-stu-id="757c4-197">Request-response example 2</span></span>

<span data-ttu-id="757c4-198">Os seguintes detalhes aplicam-se a este exemplo:</span><span class="sxs-lookup"><span data-stu-id="757c4-198">The following details apply to this example:</span></span>

- <span data-ttu-id="757c4-199">**Fornecedor**: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="757c4-199">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="757c4-200">**FaturaLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="757c4-200">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="757c4-201">**Período**: **Anterior**</span><span class="sxs-lookup"><span data-stu-id="757c4-201">**Period**: **Previous**</span></span>
- <span data-ttu-id="757c4-202">**SeekOperation**: **Seguinte**</span><span class="sxs-lookup"><span data-stu-id="757c4-202">**SeekOperation**: **Next**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="757c4-203">Pedido exemplo 2</span><span class="sxs-lookup"><span data-stu-id="757c4-203">Request example 2</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/unbilled/lineitems?provider=onetime&invoiceLineItemType=usagelineitems&currencyCode=usd&period=previous&size=2000&seekoperation=next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-2"></a><span data-ttu-id="757c4-204">Exemplo de resposta 2</span><span class="sxs-lookup"><span data-stu-id="757c4-204">Response example 2</span></span>

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
            "partnerId": "00083575-bbd0-54de-b2ad-0f5b0e927d71",
            "partnerName": "MTBC",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "VM-Series Next-Generation Firewall (Bundle 2 PAYG)",
            "productName": "VM-Series Next Generation Firewall",
            "publisherName": "Test Alto Networks, Inc.",
            "publisherId": "",
            "subscriptionId": "12345678-04d9-421c-baf8-e3b8dd62ddba",
            "subscriptionDescription": "Pay-As-You-Go",
            "chargeStartDate": "2019-01-01T00:00:00Z",
            "chargeEndDate": "2019-02-01T00:00:00Z",
            "usageDate": "2019-01-02T00:00:00Z",
            "meterType": "1 Compute Hour - 4core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "4core",
            "meterSubCategory": "VM-Series Next Generation Firewall",
            "meterName": "VM-Series Next Generation Firewall - VM-Series Next-Generation Firewall (Bundle 2 PAYG) - 4 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "ECH-PAN-RG",
            "resourceUri": "/subscriptions/12345678-04d9-421c-baf8-e3b8dd62ddba/resourceGroups/ECH-PAN-RG/providers/Microsoft.Compute/virtualMachines/echpanfw",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_D3_v2\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "",
            "unitPrice": 1.2799888920023,
            "quantity": 24.0,
            "unitType": "",
            "billingPreTaxTotal": 30.7197334080551,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 30.7197334080551,
            "pricingCurrency": "USD",
            "entitlementId": "31cdf47f-b249-4edd-9319-637862d8c0b4",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0,
            "rateOfPartnerEarnedCredit": 0.15,
            "rateOfCredit": 0.15,
            "creditType": "Partner Earned Credit Applied",
            "invoiceLineItemType": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
             "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
