---
title: Obter itens de linha da fatura
description: Pode obter uma recolha de dados de linha de fatura (item de linha de faturação fechada) para uma fatura especificada utilizando as APIs do Partner Center.
ms.date: 01/27/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 085397f3dc36468e411cec71e0dc9ae2cc364673
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769673"
---
# <a name="get-invoice-line-items"></a><span data-ttu-id="abb6b-103">Obter itens de linha da fatura</span><span class="sxs-lookup"><span data-stu-id="abb6b-103">Get invoice line items</span></span>

<span data-ttu-id="abb6b-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="abb6b-104">**Applies to:**</span></span>

- <span data-ttu-id="abb6b-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="abb6b-105">Partner Center</span></span>
- <span data-ttu-id="abb6b-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="abb6b-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="abb6b-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="abb6b-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="abb6b-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="abb6b-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="abb6b-109">Pode utilizar os seguintes métodos para obter detalhes de recolha de itens de linha de fatura (também conhecidos como itens de linha de faturação fechados) para uma fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="abb6b-109">You can use the following methods to get a collection details for of invoice line items (also known as closed billing line items) for a specified invoice.</span></span>

<span data-ttu-id="abb6b-110">*Com exceção das correções de erros, esta API já não está a ser atualizada.*</span><span class="sxs-lookup"><span data-stu-id="abb6b-110">*Except for bug fixes, this API is no longer being updated.*</span></span> <span data-ttu-id="abb6b-111">Deve atualizar as suas aplicações para ligar para a única **API** em vez de **marketplace**.</span><span class="sxs-lookup"><span data-stu-id="abb6b-111">You should update your applications to call the **onetime** API instead of **marketplace**.</span></span> <span data-ttu-id="abb6b-112">A **única API** fornece funcionalidade adicional e continuará a ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="abb6b-112">The **onetime** API provides additional functionality, and will continue to be updated.</span></span>

<span data-ttu-id="abb6b-113">Você deve usar **uma vez** para consultar todos os itens de linha de consumo comercial em vez de **mercado**.</span><span class="sxs-lookup"><span data-stu-id="abb6b-113">You should use **onetime** to query all commercial consumption line items instead of **marketplace**.</span></span> <span data-ttu-id="abb6b-114">Ou pode seguir os links na chamada de links de estimativa.</span><span class="sxs-lookup"><span data-stu-id="abb6b-114">Or, you can follow the links in the estimate links call.</span></span>

<span data-ttu-id="abb6b-115">Esta API também suporta os tipos **de** **fornecedores** de subscrições e **escritórios** para subscrições e ofertas do Microsoft Azure (MS-AZR-0145P), o que torna a funcionalidade API para trás compatível.</span><span class="sxs-lookup"><span data-stu-id="abb6b-115">This API also supports the **provider** types of **azure** and **office** for Microsoft Azure (MS-AZR-0145P) subscriptions and Office offers, which makes the API feature backward compatible.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="abb6b-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="abb6b-116">Prerequisites</span></span>

- <span data-ttu-id="abb6b-117">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="abb6b-117">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="abb6b-118">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="abb6b-118">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="abb6b-119">Um identificador de fatura.</span><span class="sxs-lookup"><span data-stu-id="abb6b-119">An invoice identifier.</span></span> <span data-ttu-id="abb6b-120">Isto identifica a fatura para a recuperação dos itens de linha.</span><span class="sxs-lookup"><span data-stu-id="abb6b-120">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="abb6b-121">C\#</span><span class="sxs-lookup"><span data-stu-id="abb6b-121">C\#</span></span>

<span data-ttu-id="abb6b-122">Para obter os itens de linha para a fatura especificada:</span><span class="sxs-lookup"><span data-stu-id="abb6b-122">To get the line items for the specified invoice:</span></span>

1. <span data-ttu-id="abb6b-123">Ligue para o método [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) para obter uma interface para as operações de faturação para a fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="abb6b-123">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="abb6b-124">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) para recuperar o objeto da fatura.</span><span class="sxs-lookup"><span data-stu-id="abb6b-124">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span> <span data-ttu-id="abb6b-125">O objeto da fatura contém todas as informações para a fatura especificada.</span><span class="sxs-lookup"><span data-stu-id="abb6b-125">The invoice object contains all of the information for the specified invoice.</span></span>
3. <span data-ttu-id="abb6b-126">Utilize a propriedade [**faturadetails**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoice.invoicedetails) do objeto de fatura para ter acesso a uma coleção de objetos [**FaturaDetail,**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail) cada um dos quais contém um [**BillingProvider**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.billingprovider) e um [**InvoiceLineItemType**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.invoicelineitemtype).</span><span class="sxs-lookup"><span data-stu-id="abb6b-126">Use the invoice object's [**InvoiceDetails**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoice.invoicedetails) property to get access to a collection of [**InvoiceDetail**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail) objects, each of which contains a [**BillingProvider**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.billingprovider) and an [**InvoiceLineItemType**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.invoicelineitemtype).</span></span> <span data-ttu-id="abb6b-127">O **BillingProvider** identifica a origem das informações detalhadas da fatura (como **Office**, **Azure**, **OneTime**) e o **InvoiceLineItemType** especifica o tipo (por exemplo, **BillingLineItem).**</span><span class="sxs-lookup"><span data-stu-id="abb6b-127">The **BillingProvider** identifies the source of the invoice detail information (such as **Office**, **Azure**, **OneTime**), and the **InvoiceLineItemType** specifies the type (for example, **BillingLineItem**).</span></span>

<span data-ttu-id="abb6b-128">O seguinte código exemplo utiliza um circuito **de apreensão para** processar a coleção **FaturaDetails.**</span><span class="sxs-lookup"><span data-stu-id="abb6b-128">The following example code uses a **foreach** loop to process the **InvoiceDetails** collection.</span></span> <span data-ttu-id="abb6b-129">Uma coleção separada de itens de linha é recuperada para cada instância **FaturaDetail.**</span><span class="sxs-lookup"><span data-stu-id="abb6b-129">A separate collection of line items is retrieved for each **InvoiceDetail** instance.</span></span>

<span data-ttu-id="abb6b-130">Para obter uma coleção de itens de linha que correspondam a uma instância **FaturaDetail:**</span><span class="sxs-lookup"><span data-stu-id="abb6b-130">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="abb6b-131">Passe o **BillingProvider** e **o InvoiceLineItemType** para o método [**Por.**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by)</span><span class="sxs-lookup"><span data-stu-id="abb6b-131">Pass the instance's **BillingProvider** and **InvoiceLineItemType** to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="abb6b-132">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.getasync) para recuperar os itens de linha associados.</span><span class="sxs-lookup"><span data-stu-id="abb6b-132">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.getasync) method to retrieve the associated line items.</span></span>
3. <span data-ttu-id="abb6b-133">Crie um enumerador para atravessar a coleção como mostrado no exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="abb6b-133">Create an enumerator to traverse the collection as shown in the following example.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// int invoicePageSize;
// string invoiceId;

// Retrieve the invoice.
var invoiceOperations = partnerOperations.Invoices.ById(invoiceId);
var invoice = invoiceOperations.Get();

foreach (var invoiceDetail in invoice.InvoiceDetails)
{
    Console.WriteLine(string.Format("Getting invoice line item for product {0} and line item type {1}",
        invoiceDetail.BillingProvider,
        invoiceDetail.InvoiceLineItemType));

    // Is this an unpaged or paged request?
    bool isUnPaged = (this.invoicePageSize <= 0);

    // If the scenario is unpaged, get all the invoice line items, otherwise get the first page.
    var invoiceLineItemsCollection =
        (isUnPaged)
        ? invoiceOperations.By(invoiceDetail.BillingProvider, invoiceDetail.InvoiceLineItemType).Get()
        : invoiceOperations.By(invoiceDetail.BillingProvider, invoiceDetail.InvoiceLineItemType).Get(this.invoicePageSize, 0);

    // Create an enumerator for traversing the line items collection.
    var invoiceLineItemEnumerator =
        partnerOperations.Enumerators.InvoiceLineItems.Create(invoiceLineItemsCollection);

    while (invoiceLineItemEnumerator.HasValue)
    {
        // invoiceLineItemEnumerator.Current contains a collection
        // of line items.
        Console.WriteLine(String.Format("invoiceLineItemEnumerator.Current has {0} line items.",
            invoiceLineItemEnumerator.Current.TotalCount));
        //
        // Insert code here to work with the line items.
        //
        Console.WriteLine();
        Console.Write("Press any key to retrieve the next invoice line items page");
        Console.ReadKey();

        // Get the next list of invoice line items.
        invoiceLineItemEnumerator.Next();
    }
}
```

<span data-ttu-id="abb6b-134">Para um exemplo semelhante, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="abb6b-134">For a similar example, see the following:</span></span>

- <span data-ttu-id="abb6b-135">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="abb6b-135">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="abb6b-136">Projeto: **Partner Center SDK Samples**</span><span class="sxs-lookup"><span data-stu-id="abb6b-136">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="abb6b-137">Classe: **GetInvoiceLineItems.cs**</span><span class="sxs-lookup"><span data-stu-id="abb6b-137">Class: **GetInvoiceLineItems.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="abb6b-138">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="abb6b-138">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="abb6b-139">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="abb6b-139">Request syntax</span></span>

<span data-ttu-id="abb6b-140">Faça o seu pedido utilizando a sintaxe adequada para o fornecedor de faturação no seu cenário.</span><span class="sxs-lookup"><span data-stu-id="abb6b-140">Make your request using the appropriate syntax for the billing provider in your scenario.</span></span>

#### <a name="office"></a><span data-ttu-id="abb6b-141">Office</span><span class="sxs-lookup"><span data-stu-id="abb6b-141">Office</span></span>

<span data-ttu-id="abb6b-142">A seguinte sintaxe aplica-se quando o fornecedor de faturação é **o Office**.</span><span class="sxs-lookup"><span data-stu-id="abb6b-142">The following syntax applies when the billing provider is **Office**.</span></span>

| <span data-ttu-id="abb6b-143">Método</span><span class="sxs-lookup"><span data-stu-id="abb6b-143">Method</span></span>  | <span data-ttu-id="abb6b-144">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="abb6b-144">Request URI</span></span>                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abb6b-145">**Obter**</span><span class="sxs-lookup"><span data-stu-id="abb6b-145">**GET**</span></span> | <span data-ttu-id="abb6b-146">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=office&invoicelineitemtype=billinglineitems&size={size}&offset={offset} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="abb6b-146">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=office&invoicelineitemtype=billinglineitems&size={size}&offset={offset} HTTP/1.1</span></span>                               |

#### <a name="microsoft-azure-ms-azr-0145p-subscription"></a><span data-ttu-id="abb6b-147">Subscrição do Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="abb6b-147">Microsoft Azure (MS-AZR-0145P) subscription</span></span>

<span data-ttu-id="abb6b-148">Aplicam-se as seguintes sintaxes quando o fornecedor de faturação tem uma subscrição microsoft Azure (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="abb6b-148">The following syntaxes apply when the billing provider has a Microsoft Azure (MS-AZR-0145P) subscription.</span></span>

| <span data-ttu-id="abb6b-149">Método</span><span class="sxs-lookup"><span data-stu-id="abb6b-149">Method</span></span>  | <span data-ttu-id="abb6b-150">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="abb6b-150">Request URI</span></span>                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abb6b-151">**Obter**</span><span class="sxs-lookup"><span data-stu-id="abb6b-151">**GET**</span></span> | <span data-ttu-id="abb6b-152">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=azure&faturalineitemtype=billinglineitems&size={size}&offset={offset} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="abb6b-152">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=azure&invoicelineitemtype=billinglineitems&size={size}&offset={offset} HTTP/1.1</span></span>  |
| <span data-ttu-id="abb6b-153">**Obter**</span><span class="sxs-lookup"><span data-stu-id="abb6b-153">**GET**</span></span> | <span data-ttu-id="abb6b-154">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=azure&invoicelineitemtype=usagelineitems&size={size}&offset={offset} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="abb6b-154">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=azure&invoicelineitemtype=usagelineitems&size={size}&offset={offset} HTTP/1.1</span></span>  |

##### <a name="onetime"></a><span data-ttu-id="abb6b-155">OneTime</span><span class="sxs-lookup"><span data-stu-id="abb6b-155">OneTime</span></span>

<span data-ttu-id="abb6b-156">Aplicam-se as seguintes sintaxes quando o fornecedor de faturação é **o OneTime**.</span><span class="sxs-lookup"><span data-stu-id="abb6b-156">The following syntaxes apply when the billing provider is **OneTime**.</span></span> <span data-ttu-id="abb6b-157">Isto inclui taxas para reservas Azure, software, planos Azure e produtos de mercado comercial.</span><span class="sxs-lookup"><span data-stu-id="abb6b-157">This includes charges for Azure reservations, software, Azure plans, and commercial marketplace products.</span></span>

| <span data-ttu-id="abb6b-158">Método</span><span class="sxs-lookup"><span data-stu-id="abb6b-158">Method</span></span>  | <span data-ttu-id="abb6b-159">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="abb6b-159">Request URI</span></span>                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="abb6b-160">**Obter**</span><span class="sxs-lookup"><span data-stu-id="abb6b-160">**GET**</span></span> | <span data-ttu-id="abb6b-161">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="abb6b-161">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&size={size} HTTP/1.1</span></span>  |
| <span data-ttu-id="abb6b-162">**Obter**</span><span class="sxs-lookup"><span data-stu-id="abb6b-162">**GET**</span></span> | <span data-ttu-id="abb6b-163">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems/onetime/billinglineitems&size={size}?seekOperation=Next</span><span class="sxs-lookup"><span data-stu-id="abb6b-163">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems/onetime/billinglineitems&size={size}?seekOperation=Next</span></span>                           |

#### <a name="previous-syntaxes"></a><span data-ttu-id="abb6b-164">Sintaxes anteriores</span><span class="sxs-lookup"><span data-stu-id="abb6b-164">Previous syntaxes</span></span>

<span data-ttu-id="abb6b-165">Se estiver a utilizar as seguintes sintaxes, certifique-se de que utiliza a sintaxe adequada para o seu caso de utilização.</span><span class="sxs-lookup"><span data-stu-id="abb6b-165">If you are using the following syntaxes, be sure to use the appropriate syntax for your use case.</span></span>

<span data-ttu-id="abb6b-166">*Com exceção das correções de erros, esta API já não está a ser atualizada.*</span><span class="sxs-lookup"><span data-stu-id="abb6b-166">*Except for bug fixes, this API is no longer being updated.*</span></span> <span data-ttu-id="abb6b-167">Deve atualizar as suas aplicações para ligar para a única **API** em vez de **marketplace**.</span><span class="sxs-lookup"><span data-stu-id="abb6b-167">You should update your applications to call the **onetime** API instead of **marketplace**.</span></span> <span data-ttu-id="abb6b-168">A **única API** fornece funcionalidade adicional e continuará a ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="abb6b-168">The **onetime** API provides additional functionality, and will continue to be updated.</span></span>

<span data-ttu-id="abb6b-169">Você deve usar **uma vez** para consultar todos os itens de linha de consumo comercial em vez de **mercado**.</span><span class="sxs-lookup"><span data-stu-id="abb6b-169">You should use **onetime** to query all commercial consumption line items instead of **marketplace**.</span></span> <span data-ttu-id="abb6b-170">Ou pode seguir os links na chamada de links de estimativa.</span><span class="sxs-lookup"><span data-stu-id="abb6b-170">Or, you can follow the links in the estimate links call.</span></span>

| <span data-ttu-id="abb6b-171">Método</span><span class="sxs-lookup"><span data-stu-id="abb6b-171">Method</span></span> | <span data-ttu-id="abb6b-172">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="abb6b-172">Request URI</span></span> | <span data-ttu-id="abb6b-173">Descrição do caso de utilização de sintaxe</span><span class="sxs-lookup"><span data-stu-id="abb6b-173">Description of syntax use case</span></span> |
| ------ | ----------- | -------------------------------- |
| <span data-ttu-id="abb6b-174">GET</span><span class="sxs-lookup"><span data-stu-id="abb6b-174">GET</span></span> | <span data-ttu-id="abb6b-175">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems/{billing-provider}/{fatura-line-item-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="abb6b-175">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems/{billing-provider}/{invoice-line-item-type} HTTP/1.1</span></span>                              | <span data-ttu-id="abb6b-176">Pode utilizar esta sintaxe para devolver uma lista completa de todos os itens de linha para a fatura dada.</span><span class="sxs-lookup"><span data-stu-id="abb6b-176">You can use this syntax to return a full list of every line item for the given invoice.</span></span> |
| <span data-ttu-id="abb6b-177">GET</span><span class="sxs-lookup"><span data-stu-id="abb6b-177">GET</span></span> | <span data-ttu-id="abb6b-178">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems/{billing-provider}/{fatura-line-item-type}?size={size}&offset={offset} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="abb6b-178">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems/{billing-provider}/{invoice-line-item-type}?size={size}&offset={offset} HTTP/1.1</span></span>  | <span data-ttu-id="abb6b-179">Para faturas grandes, pode utilizar esta sintaxe com um tamanho especificado e uma compensação baseada em 0 para devolver uma lista de itens de linha paged.</span><span class="sxs-lookup"><span data-stu-id="abb6b-179">For large invoices, you can use this syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> |
| <span data-ttu-id="abb6b-180">GET</span><span class="sxs-lookup"><span data-stu-id="abb6b-180">GET</span></span> | <span data-ttu-id="abb6b-181">[*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/lineitems/OneTime/{fatura-line-item-type}?seekOperation=Next</span><span class="sxs-lookup"><span data-stu-id="abb6b-181">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems/OneTime/{invoice-line-item-type}?seekOperation=Next</span></span>                               | <span data-ttu-id="abb6b-182">Pode utilizar esta sintaxe para uma fatura com um valor de fornecedor de faturação do **OneTime** e definir **procurar a Cooperação** para a **Próxima** para obter a próxima página de itens da linha de fatura.</span><span class="sxs-lookup"><span data-stu-id="abb6b-182">You can use this syntax for an invoice with a billing-provider value of **OneTime** and set **seekOperation** to **Next** to get the next page of invoice line items.</span></span> |

##### <a name="uri-parameters"></a><span data-ttu-id="abb6b-183">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="abb6b-183">URI parameters</span></span>

<span data-ttu-id="abb6b-184">Utilize os seguintes parâmetros URI e consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="abb6b-184">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="abb6b-185">Nome</span><span class="sxs-lookup"><span data-stu-id="abb6b-185">Name</span></span>                   | <span data-ttu-id="abb6b-186">Tipo</span><span class="sxs-lookup"><span data-stu-id="abb6b-186">Type</span></span>   | <span data-ttu-id="abb6b-187">Necessário</span><span class="sxs-lookup"><span data-stu-id="abb6b-187">Required</span></span> | <span data-ttu-id="abb6b-188">Descrição</span><span class="sxs-lookup"><span data-stu-id="abb6b-188">Description</span></span>                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| <span data-ttu-id="abb6b-189">fatura id</span><span class="sxs-lookup"><span data-stu-id="abb6b-189">invoice-id</span></span>             | <span data-ttu-id="abb6b-190">string</span><span class="sxs-lookup"><span data-stu-id="abb6b-190">string</span></span> | <span data-ttu-id="abb6b-191">Sim</span><span class="sxs-lookup"><span data-stu-id="abb6b-191">Yes</span></span>      | <span data-ttu-id="abb6b-192">Uma corda que identifica a fatura.</span><span class="sxs-lookup"><span data-stu-id="abb6b-192">A string that identifies the invoice.</span></span>                             |
| <span data-ttu-id="abb6b-193">prestador de faturação</span><span class="sxs-lookup"><span data-stu-id="abb6b-193">billing-provider</span></span>       | <span data-ttu-id="abb6b-194">string</span><span class="sxs-lookup"><span data-stu-id="abb6b-194">string</span></span> | <span data-ttu-id="abb6b-195">Sim</span><span class="sxs-lookup"><span data-stu-id="abb6b-195">Yes</span></span>      | <span data-ttu-id="abb6b-196">O fornecedor de faturação: "Office", "Azure", "OneTime".</span><span class="sxs-lookup"><span data-stu-id="abb6b-196">The billing provider: "Office", "Azure", "OneTime".</span></span>               |
| <span data-ttu-id="abb6b-197">tipo de artigo de linha de fatura</span><span class="sxs-lookup"><span data-stu-id="abb6b-197">invoice-line-item-type</span></span> | <span data-ttu-id="abb6b-198">string</span><span class="sxs-lookup"><span data-stu-id="abb6b-198">string</span></span> | <span data-ttu-id="abb6b-199">Sim</span><span class="sxs-lookup"><span data-stu-id="abb6b-199">Yes</span></span>      | <span data-ttu-id="abb6b-200">O tipo de detalhe de fatura: "BillingLineItems", "UsageLineItems".</span><span class="sxs-lookup"><span data-stu-id="abb6b-200">The type of invoice detail: "BillingLineItems", "UsageLineItems".</span></span> |
| <span data-ttu-id="abb6b-201">size</span><span class="sxs-lookup"><span data-stu-id="abb6b-201">size</span></span>                   | <span data-ttu-id="abb6b-202">número</span><span class="sxs-lookup"><span data-stu-id="abb6b-202">number</span></span> | <span data-ttu-id="abb6b-203">Não</span><span class="sxs-lookup"><span data-stu-id="abb6b-203">No</span></span>       | <span data-ttu-id="abb6b-204">O número máximo de itens para devolver.</span><span class="sxs-lookup"><span data-stu-id="abb6b-204">The maximum number of items to return.</span></span> <span data-ttu-id="abb6b-205">Tamanho máximo padrão = 2000</span><span class="sxs-lookup"><span data-stu-id="abb6b-205">Default max size = 2000</span></span>    |
| <span data-ttu-id="abb6b-206">offset</span><span class="sxs-lookup"><span data-stu-id="abb6b-206">offset</span></span>                 | <span data-ttu-id="abb6b-207">número</span><span class="sxs-lookup"><span data-stu-id="abb6b-207">number</span></span> | <span data-ttu-id="abb6b-208">Não</span><span class="sxs-lookup"><span data-stu-id="abb6b-208">No</span></span>       | <span data-ttu-id="abb6b-209">O índice baseado em zero do primeiro item da primeira linha a devolver.</span><span class="sxs-lookup"><span data-stu-id="abb6b-209">The zero-based index of the first line item to return.</span></span>            |
| <span data-ttu-id="abb6b-210">procurarOperação</span><span class="sxs-lookup"><span data-stu-id="abb6b-210">seekOperation</span></span>          | <span data-ttu-id="abb6b-211">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="abb6b-211">string</span></span> | <span data-ttu-id="abb6b-212">No</span><span class="sxs-lookup"><span data-stu-id="abb6b-212">No</span></span>       | <span data-ttu-id="abb6b-213">Se **o fornecedor de faturação** for igual ao **OneTime,** desaperte a **procura De cooperação** igual a **Next** para obter a próxima página de itens da linha de fatura.</span><span class="sxs-lookup"><span data-stu-id="abb6b-213">If **billing-provider** equals **OneTime**, set **seekOperation** equal to **Next** to get the next page of invoice line items.</span></span> |
| <span data-ttu-id="abb6b-214">hasPartnerEarnedCredit</span><span class="sxs-lookup"><span data-stu-id="abb6b-214">hasPartnerEarnedCredit</span></span> | <span data-ttu-id="abb6b-215">bool</span><span class="sxs-lookup"><span data-stu-id="abb6b-215">bool</span></span> | <span data-ttu-id="abb6b-216">Não</span><span class="sxs-lookup"><span data-stu-id="abb6b-216">No</span></span> | <span data-ttu-id="abb6b-217">O valor indicando se devolver os itens de linha com o parceiro ganhou crédito aplicado.</span><span class="sxs-lookup"><span data-stu-id="abb6b-217">The value indicating if to return the line items with partner earned credit applied.</span></span> <span data-ttu-id="abb6b-218">Nota: este parâmetro só será aplicado quando o tipo de fornecedor de faturação for OneTime e o BillLineItemType for UsageLineItems.</span><span class="sxs-lookup"><span data-stu-id="abb6b-218">Note: this parameter will be only applied when billing provider type is OneTime and InvoiceLineItemType is UsageLineItems.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="abb6b-219">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="abb6b-219">Request headers</span></span>

<span data-ttu-id="abb6b-220">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="abb6b-220">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="abb6b-221">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="abb6b-221">Request body</span></span>

<span data-ttu-id="abb6b-222">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="abb6b-222">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="abb6b-223">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="abb6b-223">REST response</span></span>

<span data-ttu-id="abb6b-224">Se for bem sucedida, a resposta contém a recolha de detalhes do item da linha.</span><span class="sxs-lookup"><span data-stu-id="abb6b-224">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="abb6b-225">*Para o item de linha **ChargeType,** o valor **Compra** está mapeado para **New**. O valor **Reembolso** está mapeado para **cancelar.***</span><span class="sxs-lookup"><span data-stu-id="abb6b-225">*For the line item **ChargeType**, the value **Purchase** is mapped to **New**. The value **Refund** is mapped to **Cancel**.*</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="abb6b-226">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="abb6b-226">Response success and error codes</span></span>

<span data-ttu-id="abb6b-227">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="abb6b-227">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="abb6b-228">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="abb6b-228">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="abb6b-229">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="abb6b-229">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="rest-request-response-examples"></a><span data-ttu-id="abb6b-230">Rest exemplos de resposta a pedidos</span><span class="sxs-lookup"><span data-stu-id="abb6b-230">REST request-response examples</span></span>

### <a name="request-response-example-1"></a><span data-ttu-id="abb6b-231">Exemplo de resposta a pedido 1</span><span class="sxs-lookup"><span data-stu-id="abb6b-231">Request-response example 1</span></span>

<span data-ttu-id="abb6b-232">Neste exemplo, os detalhes são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="abb6b-232">In this example, the details are as follows:</span></span>

- <span data-ttu-id="abb6b-233">**BillingProvider**: **Escritório**</span><span class="sxs-lookup"><span data-stu-id="abb6b-233">**BillingProvider**: **Office**</span></span>
- <span data-ttu-id="abb6b-234">**FaturaLineItemType**: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="abb6b-234">**InvoiceLineItemType**: **BillingLineItems**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="abb6b-235">Pedido exemplo 1</span><span class="sxs-lookup"><span data-stu-id="abb6b-235">Request example 1</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/1234000000/lineitems?provider=Office&nvoicelineitemtype=BillingLineItems&size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-1"></a><span data-ttu-id="abb6b-236">Exemplo de resposta 1</span><span class="sxs-lookup"><span data-stu-id="abb6b-236">Response example 1</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 2,
    "items": [{
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "74221236-D09C-4870-AC1D-33E155E9AEBE",
            "customerName": "TSTAGIN1CUST190",
            "mpnId": 4391507,
            "tier2MpnId": -1,
            "orderId": "567735045559164136",
            "subscriptionId": "4KIKawEAAAAAAAEA",
            "syndicationPartnerSubscriptionNumber": "1F58ACD7-FE51-4705-9567-D009C9ADA150",
            "offerId": "AAA5B3F0-0EE2-431B-A42F-3F18F3C6D540",
            "durableOfferId": "2F707C7C-2433-49A5-A437-9CA7CF40D3EB",
            "offerName": "EXCHANGE ONLINE (PLAN 2)",
            "domainName": "TStagin1Cust190.onmicrosoft.com",
            "billingCycleType": "MONTHLY",
            "subscriptionName": "EXCHANGE ONLINE (PLAN 2)",
            "subscriptionDescription": "EXCHANGE ONLINE (PLAN 2)",
            "subscriptionStartDate": "2017-05-12T00:00:00",
            "subscriptionEndDate": "2018-06-10T00:00:00",
            "chargeStartDate": "2017-05-12T00:00:00",
            "chargeEndDate": "2017-06-09T00:00:00",
            "chargeType": "New",
            "unitPrice": 0.0,
            "quantity": 3,
            "amount": 0.0,
            "totalOtherDiscount": 0.0,
            "subtotal": 0.0,
            "tax": 0.0,
            "totalForCustomer": 0.0,
            "currency": "USD",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "office",
            "attributes": {
                "objectType": "LicenseBasedLineItem"
            }
        }, {
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "74221236-D09C-4870-AC1D-33E155E9AEBE",
            "customerName": "TSTAGIN1CUST190",
            "mpnId": 4391507,
            "tier2MpnId": -1,
            "orderId": "567735045564795186",
            "subscriptionId": "Ik4YawEAAAAAAAEA",
            "syndicationPartnerSubscriptionNumber": "D8A8F773-9D3E-4244-8797-3182075F09FA",
            "offerId": "618B53FE-9B99-428B-9745-F706AEAF3979",
            "durableOfferId": "69C67983-CF78-4102-83F6-3E5FD246864F",
            "offerName": "SHAREPOINT ONLINE (PLAN 2)",
            "domainName": "TStagin1Cust190.onmicrosoft.com",
            "billingCycleType": "MONTHLY",
            "subscriptionName": "SHAREPOINT ONLINE (PLAN 2)",
            "subscriptionDescription": "SHAREPOINT ONLINE (PLAN 2)",
            "subscriptionStartDate": "2017-05-13T00:00:00",
            "subscriptionEndDate": "2018-06-10T00:00:00",
            "chargeStartDate": "2017-05-13T00:00:00",
            "chargeEndDate": "2017-06-09T00:00:00",
            "chargeType": "New",
            "unitPrice": 0.0,
            "quantity": 1,
            "amount": 0.0,
            "totalOtherDiscount": 0.0,
            "subtotal": 0.0,
            "tax": 0.0,
            "totalForCustomer": 0.0,
            "currency": "USD",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "office",
            "attributes": {
                "objectType": "LicenseBasedLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/1234000000/lineitems?provider=Office&nvoicelineitemtype=BillingLineItems&size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/1234000000/lineitems?provider=Office&nvoicelineitemtype=BillingLineItems&size=2&offset=",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-2"></a><span data-ttu-id="abb6b-237">Exemplo de resposta a pedido 2</span><span class="sxs-lookup"><span data-stu-id="abb6b-237">Request-response example 2</span></span>

<span data-ttu-id="abb6b-238">No exemplo seguinte, os detalhes são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="abb6b-238">In the following example, the details are as follows:</span></span>

- <span data-ttu-id="abb6b-239">**BillingProvider**: **Azure**</span><span class="sxs-lookup"><span data-stu-id="abb6b-239">**BillingProvider**: **Azure**</span></span>
- <span data-ttu-id="abb6b-240">**FaturaLineItemType**: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="abb6b-240">**InvoiceLineItemType**: **BillingLineItems**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="abb6b-241">Pedido exemplo 2</span><span class="sxs-lookup"><span data-stu-id="abb6b-241">Request example 2</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=BillingLineItems&size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-2"></a><span data-ttu-id="abb6b-242">Exemplo de resposta 2</span><span class="sxs-lookup"><span data-stu-id="abb6b-242">Response example 2</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 2,
    "items": [
        {
            "detailLineItemId": 1,
            "sku": "7UD-00001",
            "includedQuantity": 0,
            "overageQuantity": 745,
            "listPrice": 0.085,
            "currency": "USD",
            "pretaxCharges": 63.33,
            "taxAmount": 6.34,
            "postTaxTotal": 69.67,
            "pretaxEffectiveRate": 0.08500671,
            "postTaxEffectiveRate": 0.09351677,
            "chargeType": "Assess usage fee for current cycle",
            "invoiceLineItemType": "billing_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E000000",
            "partnerName": "TEST_TEST_Big foot consulting",
            "partnerBillableAccountId": "1010578050",
            "customerId": "65726577-c208-40fd-9735-8c85ac000000",
            "domainName": "600test.onmicrosoft.com",
            "customerCompanyName": "601 tests",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "87f4b92f-a490-485e-ad34-5b70cb000000",
            "subscriptionName": "Microsoft Azure",
            "subscriptionDescription": "Microsoft Azure",
            "billingCycleType": "Monthly",
            "orderId": "568297985427000000",
            "serviceName": "Azure App Service",
            "serviceType": "Standard Plan",
            "resourceGuid": "505db374-df8a-44df-9d8c-13c14b61dee1",
            "resourceName": "S1",
            "region": "",
            "consumedQuantity": 745,
            "chargeStartDate": "2019-08-02T00:00:00",
            "chargeEndDate": "2019-09-01T00:00:00",
            "unit": "1 Hour",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "UsageBasedLineItem"
            }
        },
        {
            "detailLineItemId": 1,
            "sku": "7UD-00001",
            "includedQuantity": 0,
            "overageQuantity": 0.000882,
            "listPrice": 0.0383,
            "currency": "USD",
            "pretaxCharges": 0,
            "taxAmount": 0,
            "postTaxTotal": 0,
            "pretaxEffectiveRate": 0,
            "postTaxEffectiveRate": 0,
            "chargeType": "Assess usage fee for current cycle",
            "invoiceLineItemType": "billing_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E87E26A",
            "partnerName": "TEST_TEST_Big foot consulting",
            "partnerBillableAccountId": "1010578050",
            "customerId": "65726577-c208-40fd-9735-8c85ac9cac68",
            "domainName": "600test.onmicrosoft.com",
            "customerCompanyName": "601 tests",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "87f4b92f-a490-485e-ad34-5b70cb000000",
            "subscriptionName": "Microsoft Azure",
            "subscriptionDescription": "Microsoft Azure",
            "billingCycleType": "Monthly",
            "orderId": "568297985427000000",
            "serviceName": "Storage",
            "serviceType": "Standard Page Blob",
            "resourceGuid": "d23a5753-ff85-4ddf-af28-8cc5cf2d3882",
            "resourceName": "LRS Data Stored",
            "region": "",
            "consumedQuantity": 0.000882,
            "chargeStartDate": "2019-08-02T00:00:00",
            "chargeEndDate": "2019-09-01T00:00:00",
            "unit": "1 GB/Month",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "UsageBasedLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=BillingLineItems&size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=BillingLineItems&size=2&offset=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-3"></a><span data-ttu-id="abb6b-243">Exemplo de resposta a pedido 3</span><span class="sxs-lookup"><span data-stu-id="abb6b-243">Request-response example 3</span></span>

<span data-ttu-id="abb6b-244">No exemplo seguinte, os detalhes são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="abb6b-244">In the following example, the details are as follows:</span></span>

- <span data-ttu-id="abb6b-245">**BillingProvider**: **Azure**</span><span class="sxs-lookup"><span data-stu-id="abb6b-245">**BillingProvider**: **Azure**</span></span>
- <span data-ttu-id="abb6b-246">**FaturaLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="abb6b-246">**InvoiceLineItemType**: **UsageLineItems**</span></span>

#### <a name="request-example-3"></a><span data-ttu-id="abb6b-247">Pedido exemplo 3</span><span class="sxs-lookup"><span data-stu-id="abb6b-247">Request example 3</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=UsageLineItems&size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-3"></a><span data-ttu-id="abb6b-248">Exemplo de resposta 3</span><span class="sxs-lookup"><span data-stu-id="abb6b-248">Response example 3</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 2,
    "items": [
        {
            "customerBillableAccount": "1439508127",
            "usageDate": "2019-08-05T00:00:00",
            "invoiceLineItemType": "usage_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E000000",
            "partnerName": "TEST_TEST_BIG FOOT CONSULTING",
            "partnerBillableAccountId": "1010578050",
            "customerId": "9E9B71BA-3442-458B-B519-E1CCF72FBB54",
            "domainName": "test600.onmicrosoft.com",
            "customerCompanyName": "600 TEST",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "F9BA6DA0-6DAC-4F88-B623-313C9B9C117A",
            "subscriptionName": "MICROSOFT AZURE",
            "subscriptionDescription": "MICROSOFT AZURE",
            "billingCycleType": "MONTHLY",
            "orderId": "568297985577171353",
            "serviceName": "STORAGE",
            "serviceType": "STANDARD PAGE BLOB",
            "resourceGuid": "9CC63CF8-6593-410A-B0E7-26A4EF71E8B3",
            "resourceName": "DISK DELETE OPERATIONS",
            "region": "",
            "consumedQuantity": 2.9616,
            "chargeStartDate": "2019-08-05T00:00:00",
            "chargeEndDate": "2019-09-04T00:00:00",
            "unit": "10K",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "DailyUsageLineItem"
            }
        },
        {
            "customerBillableAccount": "1307536861",
            "usageDate": "2019-08-10T00:00:00",
            "invoiceLineItemType": "usage_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E000000",
            "partnerName": "TEST_TEST_BIG FOOT CONSULTING",
            "partnerBillableAccountId": "1010578050",
            "customerId": "EB53B7BD-267E-440E-B3C0-8F0B40000000",
            "domainName": "brandontest.onmicrosoft.com",
            "customerCompanyName": "BRANDON'S TEST",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "62D22561-AB15-41E5-AD59-99025C000000",
            "subscriptionName": "MICROSOFT AZURE",
            "subscriptionDescription": "MICROSOFT AZURE",
            "billingCycleType": "MONTHLY",
            "orderId": "568297985605838583",
            "serviceName": "VIRTUAL MACHINES",
            "serviceType": "D/DS SERIES WINDOWS",
            "resourceGuid": "62C64B6C-4033-4E20-AB33-9E81271AC12A",
            "resourceName": "D1/DS1",
            "region": "US WEST",
            "consumedQuantity": 24,
            "chargeStartDate": "2019-08-05T00:00:00",
            "chargeEndDate": "2019-09-04T00:00:00",
            "unit": "1 HOUR",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "DailyUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=UsageLineItems&size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=UsageLineItems&size=2&offset=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-4"></a><span data-ttu-id="abb6b-249">Exemplo de resposta a pedido 4</span><span class="sxs-lookup"><span data-stu-id="abb6b-249">Request-response example 4</span></span>

<span data-ttu-id="abb6b-250">No exemplo seguinte, os detalhes são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="abb6b-250">In the following example, the details are as follows:</span></span>

- <span data-ttu-id="abb6b-251">**BillingProvider**: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="abb6b-251">**BillingProvider**: **OneTime**</span></span>
- <span data-ttu-id="abb6b-252">**FaturaLineItemType**: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="abb6b-252">**InvoiceLineItemType**: **BillingLineItems**</span></span>

#### <a name="request-example-4"></a><span data-ttu-id="abb6b-253">Pedido exemplo 4</span><span class="sxs-lookup"><span data-stu-id="abb6b-253">Request example 4</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/G000024135/lineitems/OneTime/BillingLineItems?size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-4"></a><span data-ttu-id="abb6b-254">Exemplo de resposta 4</span><span class="sxs-lookup"><span data-stu-id="abb6b-254">Response example 4</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

 {
    "continuationToken": "d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7",
    "totalCount": 2,
    "items": [
        {
            "partnerId": "6480d686-cfb4-424d-a945-6b9b9f000000",
            "customerId": "org:9060d13d-c5ed-482e-b059-a15a38000000",
            "customerName": "recipientCustomerName",
            "customerDomainName": "recipientCustomerDomain",
            "invoiceNumber": "1234000000",
            "quoteId": "abcd12345678",
            "mpnId": "4870137",
            "resellerMpnId": 0,
            "orderId": "QDOx5ZN3YR9uYhm4M1MGQJ_0nievUOrx1",
            "orderDate": "2018-02-08T22:31:42.9397946Z",
            "productId": "productid",
            "skuId": "skuid",
            "availabilityId": "availabilityid",
            "productName": "TEST PRODUCT",
            "skuName": "TEST SKU TITLE",
            "chargeType": "New",
            "unitPrice": 431.8,
            "effectiveUnitPrice": 496.07,
            "unitType": "Seats",
            "quantity": 1,
            "subtotal": 431.8,
            "taxTotal": 38.87,
            "totalForCustomer": 470.67,
            "currency": "USD",
            "providerName": "Test Networks Inc",
            "providerId": "12343810",
            "subscriptionDescription": "",
            "subscriptionId": "281e26fe-9ce7-415b-911c-f39232000000",
            "subscriptionStartDate": "2019-01-03T19:53:55.1292512+00:00",
            "subscriptionEndDate": "2019-02-02T19:53:55.1292512+00:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "1234278124b8",
            "priceAdjustmentDescription": "[\"100.0% Tier 1 Discount\"]",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-09-30T23:59:59Z",
            "billableQuantity": 0.0159369774,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "billingFrequency": "Monthly",
            "reservationOrderId": "883d475b-0000-2222-0000-8818752f1234",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        },
        {
            "partnerId": "6480d686-cfb4-424d-a945-6b9b9f4badc2",
            "customerId": "org:9060d13d-c5ed-482e-b059-a15a38cbb28e",
            "customerName": "recipientCustomerName",
            "customerDomainName": "recipientCustomerDomain",
            "invoiceNumber": "1234000000",
            "quoteId": "abcd12345678",
            "mpnId": "4870137",
            "resellerMpnId": 0,
            "orderId": "QDOx5ZN3YR9uYhm4M1MGQJ_0nievUOrx1",
            "orderDate": "2018-02-08T22:31:42.9397946Z",
            "productId": "productid",
            "skuId": "skuid",
            "availabilityId": "availabilityid",
            "productName": "TEST PRODUCT",
            "skuName": "TEST SKU TITLE",
            "chargeType": "New",
            "unitPrice": 26.35,
            "effectiveUnitPrice": 496.07,
            "unitType": "1 Hour",
            "quantity": 1,
            "subtotal": 26.35,
            "taxTotal": 2.37,
            "totalForCustomer": 28.72,
            "currency": "USD",
            "providerName": "Test Networks Inc",
            "providerId": "12343810",
            "subscriptionDescription": "",
            "subscriptionId": "281e26fe-9ce7-415b-911c-f39232ea904a",
            "subscriptionStartDate": "2019-01-03T19:53:55.1292512+00:00",
            "subscriptionEndDate": "2019-02-02T19:53:55.1292512+00:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "1234578124b8",
            "priceAdjustmentDescription": "[\"100.0% Tier 1 Discount\"]",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-09-30T23:59:59Z",
            "billableQuantity": 0.0130687981,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/G000024135/lineitems?provider=OneTime&nvoicelineitemtype=BillingLineItems&size=2",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/G000024135/lineitems?provider=OneTime&nvoicelineitemtype=BillingLineItems&size=2?seekOperation=Next",
            "method": "GET",
            "headers": [
                {
                    "key": "MS-ContinuationToken",
                    "value": "d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7"
                }
            ]
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-5"></a><span data-ttu-id="abb6b-255">Exemplo de resposta a pedido 5</span><span class="sxs-lookup"><span data-stu-id="abb6b-255">Request-response example 5</span></span>

<span data-ttu-id="abb6b-256">No exemplo seguinte, há paging usando um token de continuação.</span><span class="sxs-lookup"><span data-stu-id="abb6b-256">In the following example, there is paging using a continuation token.</span></span> <span data-ttu-id="abb6b-257">Os detalhes são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="abb6b-257">The details are as follows:</span></span>

- <span data-ttu-id="abb6b-258">**BillingProvider**: **OneTime**</span><span class="sxs-lookup"><span data-stu-id="abb6b-258">**BillingProvider**: **OneTime**</span></span>
- <span data-ttu-id="abb6b-259">**FaturaLineItemType**: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="abb6b-259">**InvoiceLineItemType**: **BillingLineItems**</span></span>
- <span data-ttu-id="abb6b-260">**SeekOperation**: **Seguinte**</span><span class="sxs-lookup"><span data-stu-id="abb6b-260">**SeekOperation**: **Next**</span></span>

#### <a name="request-example-5"></a><span data-ttu-id="abb6b-261">Pedido exemplo 5</span><span class="sxs-lookup"><span data-stu-id="abb6b-261">Request example 5</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/G000024135/lineitems/OneTime/BillingLineItems?seekOperation=Next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-5"></a><span data-ttu-id="abb6b-262">Exemplo de resposta 5</span><span class="sxs-lookup"><span data-stu-id="abb6b-262">Response example 5</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 1,
    "items": [
        {
            "partnerId": "6480d686-cfb4-424d-a945-6b9b9f000000",
            "customerId": "org:9060d13d-c5ed-482e-b059-a15a38000000",
            "customerName": "recipientCustomerName",
            "customerDomainName": "recipientCustomerDomain",
            "invoiceNumber": "1234000000",
            "quoteId": "abcd12345678",
            "mpnId": "4870137",
            "resellerMpnId": 0,
            "orderId": "NeqT31Kziwf8gkCXM9YQToWTqU-9Jbm81",
            "orderDate": "2018-02-08T22:31:47.1751688Z",
            "productId": "DZH318Z0BQ3P",
            "skuId": "001F",
            "availabilityId": "DZH318Z0DR0H",
            "productName": "Reserved VM Instance, Standard_D1, AP East, 3 years",
            "skuName": "D Series",
            "chargeType": "New",
            "unitPrice": 1447,
            "effectiveUnitPrice": 496.07,
            "unitType": "Seats",
            "quantity": 1,
            "subtotal": 1447,
            "taxTotal": 130.24,
            "totalForCustomer": 1577.24,
            "currency": "USD",
            "providerName": "Test Networks Inc",
            "providerId": "12343810",
            "subscriptionDescription": "",
            "subscriptionId": "281e26fe-9ce7-415b-911c-f39232000000",
            "subscriptionStartDate": "2019-01-03T19:53:55.1292512+00:00",
            "subscriptionEndDate": "2019-02-02T19:53:55.1292512+00:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "1234568124b8",
            "priceAdjustmentDescription": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-09-30T23:59:59Z",
            "billableQuantity": 0.0130687981,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "",
            "billingFrequency": "Monthly",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/G000024135/lineitems?provider=OneTime&nvoicelineitemtype=BillingLineItems&size=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
