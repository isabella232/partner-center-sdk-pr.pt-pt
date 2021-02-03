---
title: Obter uma lista de produtos (por país)
description: Pode utilizar o recurso Produto para obter uma coleção de produtos por país de clientes.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ea239aa008a5b7c33740e9c4697c3795908415cd
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769446"
---
# <a name="get-a-list-of-products-by-country"></a><span data-ttu-id="fdd55-103">Obter uma lista de produtos (por país)</span><span class="sxs-lookup"><span data-stu-id="fdd55-103">Get a list of products (by country)</span></span>

<span data-ttu-id="fdd55-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="fdd55-104">**Applies to:**</span></span>

- <span data-ttu-id="fdd55-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="fdd55-105">Partner Center</span></span>
- <span data-ttu-id="fdd55-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="fdd55-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="fdd55-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="fdd55-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="fdd55-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fdd55-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fdd55-109">Você pode usar os seguintes métodos para obter uma coleção de produtos disponíveis em um determinado país.</span><span class="sxs-lookup"><span data-stu-id="fdd55-109">You can use the following methods to get a collection of products available in a particular country.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fdd55-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fdd55-110">Prerequisites</span></span>

- <span data-ttu-id="fdd55-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fdd55-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fdd55-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="fdd55-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="fdd55-113">Um país.</span><span class="sxs-lookup"><span data-stu-id="fdd55-113">A country.</span></span>

## <a name="c"></a><span data-ttu-id="fdd55-114">C\#</span><span class="sxs-lookup"><span data-stu-id="fdd55-114">C\#</span></span>

<span data-ttu-id="fdd55-115">Para obter uma lista de produtos:</span><span class="sxs-lookup"><span data-stu-id="fdd55-115">To get a list of products:</span></span>

1. <span data-ttu-id="fdd55-116">Utilize a sua coleção **IAggregatePartner.Products** para selecionar o país utilizando o método **ByCountry().**</span><span class="sxs-lookup"><span data-stu-id="fdd55-116">Use your **IAggregatePartner.Products** collection to select the country by using the **ByCountry()** method.</span></span>

2. <span data-ttu-id="fdd55-117">Selecione a vista do catálogo utilizando o método **ByTargetView().**</span><span class="sxs-lookup"><span data-stu-id="fdd55-117">Select the catalog view using the **ByTargetView()** method.</span></span>

3. <span data-ttu-id="fdd55-118">(Opcional) Selecione o âmbito de reserva utilizando o método **ByReservationScope().**</span><span class="sxs-lookup"><span data-stu-id="fdd55-118">(Optional) Select the reservation scope using the **ByReservationScope()** method.</span></span>

4. <span data-ttu-id="fdd55-119">(Opcional) Selecione o segmento alvo utilizando o método **ByTargetSegment().**</span><span class="sxs-lookup"><span data-stu-id="fdd55-119">(Optional) Select the target segment using the **ByTargetSegment()** method.</span></span>

5. <span data-ttu-id="fdd55-120">Ligue para o método **Get()** ou **GetAsync()** para devolver a coleção.</span><span class="sxs-lookup"><span data-stu-id="fdd55-120">Call the **Get()** or **GetAsync()** method to return the collection.</span></span>

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

## <a name="java"></a><span data-ttu-id="fdd55-121">Java</span><span class="sxs-lookup"><span data-stu-id="fdd55-121">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="fdd55-122">Para obter uma lista de produtos:</span><span class="sxs-lookup"><span data-stu-id="fdd55-122">To get a list of products:</span></span>

1. <span data-ttu-id="fdd55-123">Utilize a função **IAggregatePartner.getProducts** para selecionar o país utilizando a função **byCountry().**</span><span class="sxs-lookup"><span data-stu-id="fdd55-123">Use your **IAggregatePartner.getProducts** function to select the country by using the **byCountry()** function.</span></span>

2. <span data-ttu-id="fdd55-124">Selecione a vista do catálogo utilizando a função **byTargetView().**</span><span class="sxs-lookup"><span data-stu-id="fdd55-124">Select the catalog view using the **byTargetView()** function.</span></span>
3. <span data-ttu-id="fdd55-125">(Opcional) Selecione o segmento alvo utilizando a função **byTargetSegment().**</span><span class="sxs-lookup"><span data-stu-id="fdd55-125">(Optional) Select the target segment using the **byTargetSegment()** function.</span></span>

4. <span data-ttu-id="fdd55-126">Ligue para a função **get()** para devolver a coleção.</span><span class="sxs-lookup"><span data-stu-id="fdd55-126">Call the **get()** function to return the collection.</span></span>

```java
// IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").byTargetSegment("commercial").get();
```

## <a name="powershell"></a><span data-ttu-id="fdd55-127">PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdd55-127">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="fdd55-128">Para obter uma lista de produtos:</span><span class="sxs-lookup"><span data-stu-id="fdd55-128">To get a list of products:</span></span>

1. <span data-ttu-id="fdd55-129">Execute o comando [**Get-PartnerProduct.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md)</span><span class="sxs-lookup"><span data-stu-id="fdd55-129">Execute the [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) command.</span></span>

2. <span data-ttu-id="fdd55-130">Selecione o catálogo especificando o parâmetro **Catálogo.**</span><span class="sxs-lookup"><span data-stu-id="fdd55-130">Select the catalog by specifying the **Catalog** parameter.</span></span>
3. <span data-ttu-id="fdd55-131">(Opcional) Selecione o segmento alvo especificando o parâmetro **Segmento.**</span><span class="sxs-lookup"><span data-stu-id="fdd55-131">(Optional) Select the target segment by specifying the **Segment** parameter.</span></span>

```powershell
Get-PartnerProduct -Catalog 'Azure' -Segment 'commercial'
```

## <a name="rest-request"></a><span data-ttu-id="fdd55-132">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="fdd55-132">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fdd55-133">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdd55-133">Request syntax</span></span>

| <span data-ttu-id="fdd55-134">Método</span><span class="sxs-lookup"><span data-stu-id="fdd55-134">Method</span></span>  | <span data-ttu-id="fdd55-135">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="fdd55-135">Request URI</span></span>                                                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="fdd55-136">**Obter**</span><span class="sxs-lookup"><span data-stu-id="fdd55-136">**GET**</span></span> | <span data-ttu-id="fdd55-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fdd55-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="fdd55-138">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="fdd55-138">URI parameters</span></span>

<span data-ttu-id="fdd55-139">Utilize os seguintes parâmetros de percurso e consulta para obter uma lista de produtos.</span><span class="sxs-lookup"><span data-stu-id="fdd55-139">Use the following path and query parameters to get a list of products.</span></span>

| <span data-ttu-id="fdd55-140">Nome</span><span class="sxs-lookup"><span data-stu-id="fdd55-140">Name</span></span>                   | <span data-ttu-id="fdd55-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="fdd55-141">Type</span></span>     | <span data-ttu-id="fdd55-142">Necessário</span><span class="sxs-lookup"><span data-stu-id="fdd55-142">Required</span></span> | <span data-ttu-id="fdd55-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdd55-143">Description</span></span>                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| <span data-ttu-id="fdd55-144">país</span><span class="sxs-lookup"><span data-stu-id="fdd55-144">country</span></span>                | <span data-ttu-id="fdd55-145">string</span><span class="sxs-lookup"><span data-stu-id="fdd55-145">string</span></span>   | <span data-ttu-id="fdd55-146">Sim</span><span class="sxs-lookup"><span data-stu-id="fdd55-146">Yes</span></span>      | <span data-ttu-id="fdd55-147">O ID do país/região.</span><span class="sxs-lookup"><span data-stu-id="fdd55-147">The country/region ID.</span></span>                                                  |
| <span data-ttu-id="fdd55-148">targetView</span><span class="sxs-lookup"><span data-stu-id="fdd55-148">targetView</span></span>             | <span data-ttu-id="fdd55-149">string</span><span class="sxs-lookup"><span data-stu-id="fdd55-149">string</span></span>   | <span data-ttu-id="fdd55-150">Sim</span><span class="sxs-lookup"><span data-stu-id="fdd55-150">Yes</span></span>      | <span data-ttu-id="fdd55-151">Identifica a visão do catálogo.</span><span class="sxs-lookup"><span data-stu-id="fdd55-151">Identifies the target view of the catalog.</span></span> <span data-ttu-id="fdd55-152">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="fdd55-152">The supported values are:</span></span> <br/><br/><span data-ttu-id="fdd55-153">**Azure,** que inclui todos os itens Azure</span><span class="sxs-lookup"><span data-stu-id="fdd55-153">**Azure**, which includes all Azure items</span></span><br/><br/><span data-ttu-id="fdd55-154">**AzureReservations**, que inclui todos os itens de reserva Azure</span><span class="sxs-lookup"><span data-stu-id="fdd55-154">**AzureReservations**, which includes all Azure reservation items</span></span><br/><br/><span data-ttu-id="fdd55-155">**AzureReservationsVM,** que inclui todos os itens de reserva de máquina virtual (VM)</span><span class="sxs-lookup"><span data-stu-id="fdd55-155">**AzureReservationsVM**, which includes all virtual machine (VM) reservation items</span></span><br/><br/><span data-ttu-id="fdd55-156">**AzureReservationsSQL,** que inclui todos os itens de reserva SQL</span><span class="sxs-lookup"><span data-stu-id="fdd55-156">**AzureReservationsSQL**, which includes all SQL reservation items</span></span><br/><br/><span data-ttu-id="fdd55-157">**AzureReservationsCosmosDb,** que inclui todos os itens de reserva da base de dados cosmos</span><span class="sxs-lookup"><span data-stu-id="fdd55-157">**AzureReservationsCosmosDb**, which includes all Cosmos database reservation items</span></span><br/><br/><span data-ttu-id="fdd55-158">**MicrosoftAzure**, que inclui itens para subscrições microsoft Azure **(MS-AZR-0145P**) e planos Azure</span><span class="sxs-lookup"><span data-stu-id="fdd55-158">**MicrosoftAzure**, which includes items for Microsoft Azure subscriptions (**MS-AZR-0145P**) and Azure plans</span></span><br/><br/><span data-ttu-id="fdd55-159">**OnlineServices**, que inclui todos os itens de serviço on-line (incluindo produtos de mercado comercial)</span><span class="sxs-lookup"><span data-stu-id="fdd55-159">**OnlineServices**, which includes all online service items (including commercial marketplace products)</span></span><br/><br/><span data-ttu-id="fdd55-160">**Software**, que inclui todos os itens de software</span><span class="sxs-lookup"><span data-stu-id="fdd55-160">**Software**, which includes all software items</span></span><br/><br/><span data-ttu-id="fdd55-161">**SoftwareSUSELinux,** que inclui todos os itens SUSE Linux de software</span><span class="sxs-lookup"><span data-stu-id="fdd55-161">**SoftwareSUSELinux**, which includes all software SUSE Linux items</span></span><br/><br/><span data-ttu-id="fdd55-162">**SoftwarePerpetual,** que inclui todos os itens de software perpétuos</span><span class="sxs-lookup"><span data-stu-id="fdd55-162">**SoftwarePerpetual**, which includes all perpetual software items</span></span><br/><br/><span data-ttu-id="fdd55-163">**SoftwareSubscriptions**, que inclui todos os itens de subscrição de software</span><span class="sxs-lookup"><span data-stu-id="fdd55-163">**SoftwareSubscriptions**, which includes all software subscription items</span></span>    |
| <span data-ttu-id="fdd55-164">targetSegment</span><span class="sxs-lookup"><span data-stu-id="fdd55-164">targetSegment</span></span>          | <span data-ttu-id="fdd55-165">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="fdd55-165">string</span></span>   | <span data-ttu-id="fdd55-166">No</span><span class="sxs-lookup"><span data-stu-id="fdd55-166">No</span></span>       | <span data-ttu-id="fdd55-167">Identifica o segmento alvo.</span><span class="sxs-lookup"><span data-stu-id="fdd55-167">Identifies the target segment.</span></span> <span data-ttu-id="fdd55-168">A vista para diferentes públicos-alvo.</span><span class="sxs-lookup"><span data-stu-id="fdd55-168">The view for different target audiences.</span></span> <span data-ttu-id="fdd55-169">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="fdd55-169">The supported values are:</span></span> <br/><br/><span data-ttu-id="fdd55-170">**comercial**</span><span class="sxs-lookup"><span data-stu-id="fdd55-170">**commercial**</span></span><br/><span data-ttu-id="fdd55-171">**educação**</span><span class="sxs-lookup"><span data-stu-id="fdd55-171">**education**</span></span><br/><span data-ttu-id="fdd55-172">**governo**</span><span class="sxs-lookup"><span data-stu-id="fdd55-172">**government**</span></span><br/><span data-ttu-id="fdd55-173">**sem fins lucrativos**</span><span class="sxs-lookup"><span data-stu-id="fdd55-173">**nonprofit**</span></span>  |
| <span data-ttu-id="fdd55-174">reservationScope</span><span class="sxs-lookup"><span data-stu-id="fdd55-174">reservationScope</span></span> | <span data-ttu-id="fdd55-175">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="fdd55-175">string</span></span>   | <span data-ttu-id="fdd55-176">No</span><span class="sxs-lookup"><span data-stu-id="fdd55-176">No</span></span> | <span data-ttu-id="fdd55-177">Ao consultar uma lista de produtos para Reservas Azure, especifique `reservationScope=AzurePlan` para obter uma lista de produtos que são aplicáveis aos planos Azure.</span><span class="sxs-lookup"><span data-stu-id="fdd55-177">When querying for a list of products for Azure Reservations, specify `reservationScope=AzurePlan` to get a list of products that are applicable to Azure plans.</span></span> <span data-ttu-id="fdd55-178">Exclua este parâmetro para obter uma lista de produtos para reservas Azure, que são aplicáveis às subscrições do Microsoft Azure **(MS-AZR-0145P).**</span><span class="sxs-lookup"><span data-stu-id="fdd55-178">Exclude this parameter to get a list of products for Azure reservations, which are applicable to Microsoft Azure (**MS-AZR-0145P**) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="fdd55-179">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="fdd55-179">Request headers</span></span>

<span data-ttu-id="fdd55-180">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="fdd55-180">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fdd55-181">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="fdd55-181">Request body</span></span>

<span data-ttu-id="fdd55-182">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fdd55-182">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="fdd55-183">Solicitar exemplos</span><span class="sxs-lookup"><span data-stu-id="fdd55-183">Request examples</span></span>

#### <a name="products-by-country"></a><span data-ttu-id="fdd55-184">Produtos por país</span><span class="sxs-lookup"><span data-stu-id="fdd55-184">Products by country</span></span>

<span data-ttu-id="fdd55-185">Siga este exemplo para obter uma lista de produtos por país para subscrições microsoft Azure (MS-AZR-0145P) e planos Azure.</span><span class="sxs-lookup"><span data-stu-id="fdd55-185">Follow this example to get a list of products by country for Microsoft Azure (MS-AZR-0145P) subscriptions and Azure plans.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-azure-plan"></a><span data-ttu-id="fdd55-186">Reservas Azure VM (plano Azure)</span><span class="sxs-lookup"><span data-stu-id="fdd55-186">Azure VM reservations (Azure plan)</span></span>

<span data-ttu-id="fdd55-187">Siga este exemplo para obter uma lista de produtos por país para reservas Azure VM que são aplicáveis aos planos Azure.</span><span class="sxs-lookup"><span data-stu-id="fdd55-187">Follow this example to get a list of products by country for Azure VM reservations that are applicable to Azure plans.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureAzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="fdd55-188">Reservas Azure VM para subscrições microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="fdd55-188">Azure VM reservations for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="fdd55-189">Siga este exemplo para obter uma lista de produtos por país para reservas Azure VM que são aplicáveis às subscrições do Microsoft Azure (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="fdd55-189">Follow this example to get a list of products by country for Azure VM reservations that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="fdd55-190">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="fdd55-190">REST response</span></span>

<span data-ttu-id="fdd55-191">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [**do Produto.**](product-resources.md#product)</span><span class="sxs-lookup"><span data-stu-id="fdd55-191">If successful, the response body contains a collection of [**Product**](product-resources.md#product) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fdd55-192">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="fdd55-192">Response success and error codes</span></span>

<span data-ttu-id="fdd55-193">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="fdd55-193">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fdd55-194">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="fdd55-194">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fdd55-195">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="fdd55-195">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="fdd55-196">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="fdd55-196">This method returns the following error codes:</span></span>

| <span data-ttu-id="fdd55-197">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="fdd55-197">HTTP Status Code</span></span>     | <span data-ttu-id="fdd55-198">Código de erro</span><span class="sxs-lookup"><span data-stu-id="fdd55-198">Error code</span></span>   | <span data-ttu-id="fdd55-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdd55-199">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fdd55-200">403</span><span class="sxs-lookup"><span data-stu-id="fdd55-200">403</span></span>                  | <span data-ttu-id="fdd55-201">400030</span><span class="sxs-lookup"><span data-stu-id="fdd55-201">400030</span></span>       | <span data-ttu-id="fdd55-202">Não é permitido o acesso ao objetivo solicitado.</span><span class="sxs-lookup"><span data-stu-id="fdd55-202">Access to the requested targetSegment is not allowed.</span></span>                                                     |
| <span data-ttu-id="fdd55-203">403</span><span class="sxs-lookup"><span data-stu-id="fdd55-203">403</span></span>                  | <span data-ttu-id="fdd55-204">400036</span><span class="sxs-lookup"><span data-stu-id="fdd55-204">400036</span></span>       | <span data-ttu-id="fdd55-205">Não é permitido o acesso ao targetView solicitado.</span><span class="sxs-lookup"><span data-stu-id="fdd55-205">Access to the requested targetView is not allowed.</span></span>                                                        |

### <a name="response-example"></a><span data-ttu-id="fdd55-206">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="fdd55-206">Response example</span></span>

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
