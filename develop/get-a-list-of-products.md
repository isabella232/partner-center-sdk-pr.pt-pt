---
title: Obter uma lista de produtos (por país)
description: Pode utilizar o recurso Produto para obter uma coleção de produtos por país de clientes.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 1258727ecbe7c5cc332624577fa8a355e28e3717
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874215"
---
# <a name="get-a-list-of-products-by-country"></a><span data-ttu-id="14bbc-103">Obter uma lista de produtos (por país)</span><span class="sxs-lookup"><span data-stu-id="14bbc-103">Get a list of products (by country)</span></span>

<span data-ttu-id="14bbc-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="14bbc-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="14bbc-105">Você pode usar os seguintes métodos para obter uma coleção de produtos disponíveis em um determinado país.</span><span class="sxs-lookup"><span data-stu-id="14bbc-105">You can use the following methods to get a collection of products available in a particular country.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14bbc-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="14bbc-106">Prerequisites</span></span>

- <span data-ttu-id="14bbc-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="14bbc-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="14bbc-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="14bbc-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="14bbc-109">Um país.</span><span class="sxs-lookup"><span data-stu-id="14bbc-109">A country.</span></span>

## <a name="c"></a><span data-ttu-id="14bbc-110">C\#</span><span class="sxs-lookup"><span data-stu-id="14bbc-110">C\#</span></span>

<span data-ttu-id="14bbc-111">Para obter uma lista de produtos:</span><span class="sxs-lookup"><span data-stu-id="14bbc-111">To get a list of products:</span></span>

1. <span data-ttu-id="14bbc-112">Utilize a sua coleção **IAggregatePartner.Products** para selecionar o país utilizando o método **ByCountry().**</span><span class="sxs-lookup"><span data-stu-id="14bbc-112">Use your **IAggregatePartner.Products** collection to select the country by using the **ByCountry()** method.</span></span>

2. <span data-ttu-id="14bbc-113">Selecione a vista do catálogo utilizando o método **ByTargetView().**</span><span class="sxs-lookup"><span data-stu-id="14bbc-113">Select the catalog view using the **ByTargetView()** method.</span></span>

3. <span data-ttu-id="14bbc-114">(Opcional) Selecione o âmbito de reserva utilizando o método **ByReservationScope().**</span><span class="sxs-lookup"><span data-stu-id="14bbc-114">(Optional) Select the reservation scope using the **ByReservationScope()** method.</span></span>

4. <span data-ttu-id="14bbc-115">(Opcional) Selecione o segmento alvo utilizando o método **ByTargetSegment().**</span><span class="sxs-lookup"><span data-stu-id="14bbc-115">(Optional) Select the target segment using the **ByTargetSegment()** method.</span></span>

5. <span data-ttu-id="14bbc-116">Ligue para o método **Get()** ou **GetAsync()** para devolver a coleção.</span><span class="sxs-lookup"><span data-stu-id="14bbc-116">Call the **Get()** or **GetAsync()** method to return the collection.</span></span>

```csharp
IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").Get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").ByTargetSegment("commercial").Get();

// Get the products for Azure reservations which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").Get();

// Get the products for Azure reservations which are applicable to Azure plans only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").ByReservationScope("AzurePlan").Get();

```

## <a name="java"></a><span data-ttu-id="14bbc-117">Java</span><span class="sxs-lookup"><span data-stu-id="14bbc-117">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="14bbc-118">Para obter uma lista de produtos:</span><span class="sxs-lookup"><span data-stu-id="14bbc-118">To get a list of products:</span></span>

1. <span data-ttu-id="14bbc-119">Utilize a função **IAggregatePartner.getProducts** para selecionar o país utilizando a função **byCountry().**</span><span class="sxs-lookup"><span data-stu-id="14bbc-119">Use your **IAggregatePartner.getProducts** function to select the country by using the **byCountry()** function.</span></span>

2. <span data-ttu-id="14bbc-120">Selecione a vista do catálogo utilizando a função **byTargetView().**</span><span class="sxs-lookup"><span data-stu-id="14bbc-120">Select the catalog view using the **byTargetView()** function.</span></span>
3. <span data-ttu-id="14bbc-121">(Opcional) Selecione o segmento alvo utilizando a função **byTargetSegment().**</span><span class="sxs-lookup"><span data-stu-id="14bbc-121">(Optional) Select the target segment using the **byTargetSegment()** function.</span></span>

4. <span data-ttu-id="14bbc-122">Ligue para a função **get()** para devolver a coleção.</span><span class="sxs-lookup"><span data-stu-id="14bbc-122">Call the **get()** function to return the collection.</span></span>

```java
// IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").byTargetSegment("commercial").get();
```

## <a name="powershell"></a><span data-ttu-id="14bbc-123">PowerShell</span><span class="sxs-lookup"><span data-stu-id="14bbc-123">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="14bbc-124">Para obter uma lista de produtos:</span><span class="sxs-lookup"><span data-stu-id="14bbc-124">To get a list of products:</span></span>

1. <span data-ttu-id="14bbc-125">Execute o comando [**Get-PartnerProduct.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md)</span><span class="sxs-lookup"><span data-stu-id="14bbc-125">Execute the [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) command.</span></span>

2. <span data-ttu-id="14bbc-126">Selecione o catálogo especificando o parâmetro **Catálogo.**</span><span class="sxs-lookup"><span data-stu-id="14bbc-126">Select the catalog by specifying the **Catalog** parameter.</span></span>
3. <span data-ttu-id="14bbc-127">(Opcional) Selecione o segmento alvo especificando o parâmetro **Segmento.**</span><span class="sxs-lookup"><span data-stu-id="14bbc-127">(Optional) Select the target segment by specifying the **Segment** parameter.</span></span>

```powershell
Get-PartnerProduct -Catalog 'Azure' -Segment 'commercial'
```

## <a name="rest-request"></a><span data-ttu-id="14bbc-128">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="14bbc-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="14bbc-129">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="14bbc-129">Request syntax</span></span>

| <span data-ttu-id="14bbc-130">Método</span><span class="sxs-lookup"><span data-stu-id="14bbc-130">Method</span></span>  | <span data-ttu-id="14bbc-131">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="14bbc-131">Request URI</span></span>                                                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="14bbc-132">**Obter**</span><span class="sxs-lookup"><span data-stu-id="14bbc-132">**GET**</span></span> | <span data-ttu-id="14bbc-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="14bbc-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="14bbc-134">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="14bbc-134">URI parameters</span></span>

<span data-ttu-id="14bbc-135">Utilize os seguintes parâmetros de percurso e consulta para obter uma lista de produtos.</span><span class="sxs-lookup"><span data-stu-id="14bbc-135">Use the following path and query parameters to get a list of products.</span></span>

| <span data-ttu-id="14bbc-136">Nome</span><span class="sxs-lookup"><span data-stu-id="14bbc-136">Name</span></span>                   | <span data-ttu-id="14bbc-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="14bbc-137">Type</span></span>     | <span data-ttu-id="14bbc-138">Necessário</span><span class="sxs-lookup"><span data-stu-id="14bbc-138">Required</span></span> | <span data-ttu-id="14bbc-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="14bbc-139">Description</span></span>                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| <span data-ttu-id="14bbc-140">país</span><span class="sxs-lookup"><span data-stu-id="14bbc-140">country</span></span>                | <span data-ttu-id="14bbc-141">string</span><span class="sxs-lookup"><span data-stu-id="14bbc-141">string</span></span>   | <span data-ttu-id="14bbc-142">Yes</span><span class="sxs-lookup"><span data-stu-id="14bbc-142">Yes</span></span>      | <span data-ttu-id="14bbc-143">O ID do país/região.</span><span class="sxs-lookup"><span data-stu-id="14bbc-143">The country/region ID.</span></span>                                                  |
| <span data-ttu-id="14bbc-144">targetView</span><span class="sxs-lookup"><span data-stu-id="14bbc-144">targetView</span></span>             | <span data-ttu-id="14bbc-145">string</span><span class="sxs-lookup"><span data-stu-id="14bbc-145">string</span></span>   | <span data-ttu-id="14bbc-146">Yes</span><span class="sxs-lookup"><span data-stu-id="14bbc-146">Yes</span></span>      | <span data-ttu-id="14bbc-147">Identifica a visão do catálogo.</span><span class="sxs-lookup"><span data-stu-id="14bbc-147">Identifies the target view of the catalog.</span></span> <span data-ttu-id="14bbc-148">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="14bbc-148">The supported values are:</span></span> <br/><br/><span data-ttu-id="14bbc-149">**Azure,** que inclui todos os itens Azure</span><span class="sxs-lookup"><span data-stu-id="14bbc-149">**Azure**, which includes all Azure items</span></span><br/><br/><span data-ttu-id="14bbc-150">**AzureReservations**, que inclui todos os itens de reserva Azure</span><span class="sxs-lookup"><span data-stu-id="14bbc-150">**AzureReservations**, which includes all Azure reservation items</span></span><br/><br/><span data-ttu-id="14bbc-151">**AzureReservationsVM,** que inclui todos os itens de reserva de máquina virtual (VM)</span><span class="sxs-lookup"><span data-stu-id="14bbc-151">**AzureReservationsVM**, which includes all virtual machine (VM) reservation items</span></span><br/><br/><span data-ttu-id="14bbc-152">**AzureReservationsSQL,** que inclui todos os itens de reserva SQL</span><span class="sxs-lookup"><span data-stu-id="14bbc-152">**AzureReservationsSQL**, which includes all SQL reservation items</span></span><br/><br/><span data-ttu-id="14bbc-153">**AzureReservationsCosmosDb,** que inclui todos os itens de reserva da base de dados cosmos</span><span class="sxs-lookup"><span data-stu-id="14bbc-153">**AzureReservationsCosmosDb**, which includes all Cosmos database reservation items</span></span><br/><br/><span data-ttu-id="14bbc-154">**MicrosoftAzure**, que inclui itens para subscrições Microsoft Azure **(MS-AZR-0145P)** e planos Azure</span><span class="sxs-lookup"><span data-stu-id="14bbc-154">**MicrosoftAzure**, which includes items for Microsoft Azure subscriptions (**MS-AZR-0145P**) and Azure plans</span></span><br/><br/><span data-ttu-id="14bbc-155">**OnlineServices**, que inclui todos os itens de serviço on-line (incluindo produtos de mercado comercial)</span><span class="sxs-lookup"><span data-stu-id="14bbc-155">**OnlineServices**, which includes all online service items (including commercial marketplace products)</span></span><br/><br/><span data-ttu-id="14bbc-156">**Software**, que inclui todos os itens de software</span><span class="sxs-lookup"><span data-stu-id="14bbc-156">**Software**, which includes all software items</span></span><br/><br/><span data-ttu-id="14bbc-157">**SoftwareSUSELinux,** que inclui todos os itens SUSE Linux de software</span><span class="sxs-lookup"><span data-stu-id="14bbc-157">**SoftwareSUSELinux**, which includes all software SUSE Linux items</span></span><br/><br/><span data-ttu-id="14bbc-158">**SoftwarePerpetual,** que inclui todos os itens de software perpétuos</span><span class="sxs-lookup"><span data-stu-id="14bbc-158">**SoftwarePerpetual**, which includes all perpetual software items</span></span><br/><br/><span data-ttu-id="14bbc-159">**SoftwareSubscriptions**, que inclui todos os itens de subscrição de software</span><span class="sxs-lookup"><span data-stu-id="14bbc-159">**SoftwareSubscriptions**, which includes all software subscription items</span></span>    |
| <span data-ttu-id="14bbc-160">targetSegment</span><span class="sxs-lookup"><span data-stu-id="14bbc-160">targetSegment</span></span>          | <span data-ttu-id="14bbc-161">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="14bbc-161">string</span></span>   | <span data-ttu-id="14bbc-162">No</span><span class="sxs-lookup"><span data-stu-id="14bbc-162">No</span></span>       | <span data-ttu-id="14bbc-163">Identifica o segmento alvo.</span><span class="sxs-lookup"><span data-stu-id="14bbc-163">Identifies the target segment.</span></span> <span data-ttu-id="14bbc-164">A vista para diferentes públicos-alvo.</span><span class="sxs-lookup"><span data-stu-id="14bbc-164">The view for different target audiences.</span></span> <span data-ttu-id="14bbc-165">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="14bbc-165">The supported values are:</span></span> <br/><br/><span data-ttu-id="14bbc-166">**comercial**</span><span class="sxs-lookup"><span data-stu-id="14bbc-166">**commercial**</span></span><br/><span data-ttu-id="14bbc-167">**educação**</span><span class="sxs-lookup"><span data-stu-id="14bbc-167">**education**</span></span><br/><span data-ttu-id="14bbc-168">**governo**</span><span class="sxs-lookup"><span data-stu-id="14bbc-168">**government**</span></span><br/><span data-ttu-id="14bbc-169">**sem fins lucrativos**</span><span class="sxs-lookup"><span data-stu-id="14bbc-169">**nonprofit**</span></span>  |
| <span data-ttu-id="14bbc-170">reservationScope</span><span class="sxs-lookup"><span data-stu-id="14bbc-170">reservationScope</span></span> | <span data-ttu-id="14bbc-171">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="14bbc-171">string</span></span>   | <span data-ttu-id="14bbc-172">No</span><span class="sxs-lookup"><span data-stu-id="14bbc-172">No</span></span> | <span data-ttu-id="14bbc-173">Ao consultar uma lista de produtos para Reservas Azure, especifique `reservationScope=AzurePlan` para obter uma lista de produtos que são aplicáveis aos planos Azure.</span><span class="sxs-lookup"><span data-stu-id="14bbc-173">When querying for a list of products for Azure Reservations, specify `reservationScope=AzurePlan` to get a list of products that are applicable to Azure plans.</span></span> <span data-ttu-id="14bbc-174">Exclua este parâmetro para obter uma lista de produtos para reservas Azure, que são aplicáveis a Microsoft Azure **(MS-AZR-0145P)** subscrições.</span><span class="sxs-lookup"><span data-stu-id="14bbc-174">Exclude this parameter to get a list of products for Azure reservations, which are applicable to Microsoft Azure (**MS-AZR-0145P**) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="14bbc-175">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="14bbc-175">Request headers</span></span>

<span data-ttu-id="14bbc-176">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="14bbc-176">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="14bbc-177">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="14bbc-177">Request body</span></span>

<span data-ttu-id="14bbc-178">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="14bbc-178">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="14bbc-179">Solicitar exemplos</span><span class="sxs-lookup"><span data-stu-id="14bbc-179">Request examples</span></span>

#### <a name="products-by-country"></a><span data-ttu-id="14bbc-180">Produtos por país</span><span class="sxs-lookup"><span data-stu-id="14bbc-180">Products by country</span></span>

<span data-ttu-id="14bbc-181">Siga este exemplo para obter uma lista de produtos por país para assinaturas Microsoft Azure (MS-AZR-0145P) e planos Azure.</span><span class="sxs-lookup"><span data-stu-id="14bbc-181">Follow this example to get a list of products by country for Microsoft Azure (MS-AZR-0145P) subscriptions and Azure plans.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-azure-plan"></a><span data-ttu-id="14bbc-182">Reservas Azure VM (plano Azure)</span><span class="sxs-lookup"><span data-stu-id="14bbc-182">Azure VM reservations (Azure plan)</span></span>

<span data-ttu-id="14bbc-183">Siga este exemplo para obter uma lista de produtos por país para reservas Azure VM que são aplicáveis aos planos Azure.</span><span class="sxs-lookup"><span data-stu-id="14bbc-183">Follow this example to get a list of products by country for Azure VM reservations that are applicable to Azure plans.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureAzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="14bbc-184">Reservas Azure VM para subscrições Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="14bbc-184">Azure VM reservations for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="14bbc-185">Siga este exemplo para obter uma lista de produtos por país para reservas Azure VM que são aplicáveis às assinaturas Microsoft Azure (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="14bbc-185">Follow this example to get a list of products by country for Azure VM reservations that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="14bbc-186">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="14bbc-186">REST response</span></span>

<span data-ttu-id="14bbc-187">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [**do Produto.**](product-resources.md#product)</span><span class="sxs-lookup"><span data-stu-id="14bbc-187">If successful, the response body contains a collection of [**Product**](product-resources.md#product) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="14bbc-188">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="14bbc-188">Response success and error codes</span></span>

<span data-ttu-id="14bbc-189">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="14bbc-189">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="14bbc-190">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="14bbc-190">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="14bbc-191">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="14bbc-191">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="14bbc-192">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="14bbc-192">This method returns the following error codes:</span></span>

| <span data-ttu-id="14bbc-193">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="14bbc-193">HTTP Status Code</span></span>     | <span data-ttu-id="14bbc-194">Código de erro</span><span class="sxs-lookup"><span data-stu-id="14bbc-194">Error code</span></span>   | <span data-ttu-id="14bbc-195">Description</span><span class="sxs-lookup"><span data-stu-id="14bbc-195">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="14bbc-196">403</span><span class="sxs-lookup"><span data-stu-id="14bbc-196">403</span></span>                  | <span data-ttu-id="14bbc-197">400030</span><span class="sxs-lookup"><span data-stu-id="14bbc-197">400030</span></span>       | <span data-ttu-id="14bbc-198">Não é permitido o acesso ao objetivo solicitado.</span><span class="sxs-lookup"><span data-stu-id="14bbc-198">Access to the requested targetSegment is not allowed.</span></span>                                                     |
| <span data-ttu-id="14bbc-199">403</span><span class="sxs-lookup"><span data-stu-id="14bbc-199">403</span></span>                  | <span data-ttu-id="14bbc-200">400036</span><span class="sxs-lookup"><span data-stu-id="14bbc-200">400036</span></span>       | <span data-ttu-id="14bbc-201">Não é permitido o acesso ao targetView solicitado.</span><span class="sxs-lookup"><span data-stu-id="14bbc-201">Access to the requested targetView is not allowed.</span></span>                                                        |

### <a name="response-example"></a><span data-ttu-id="14bbc-202">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="14bbc-202">Response example</span></span>

```http
{
    "totalCount": 19,
    "items": [
        {
            "id": "DZH318Z0BQ3Q",
            "title": "Virtual Machines DSv2 Series",
            "description": "Dsv2-series instances are the latest generation of D-series instances that will carry more powerful CPUs which are on average about 35% faster than D-series instances, and carry the same memory and disk configurations as the D-series. Dsv2-series instances are based on the latest generation 2.4 GHz Intel Xeon® E5-2673 v3 (Haswell) processor, and with Intel Turbo Boost Technology 2.0 can go to 3.2 GHz.",
            "productType": {
                "id": "Azure",
                "displayName": "Azure",
                "subType": {
                "id": "VirtualMachines",
                "displayName": "VirtualMachines"
                }
            },
            "isMicrosoftProduct": true,
            "publisherName": "Microsoft",
            "links": {
                "skus": {
                    "uri": "/products/DZH318Z0BQ3Q/skus?country=US",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/DZH318Z0BQ3Q?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        ...
    ],
    "links": {
        "self": {
            "uri": "/products?country=US&targetView=Azure",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
