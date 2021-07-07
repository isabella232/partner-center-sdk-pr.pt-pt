---
title: Obter todas as informações de análise de pesquisas
description: Como obter toda a informação de pesquisa analítica.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e789a013b01fb63a38c72f4fe94864ecf21f7e4b
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760169"
---
# <a name="get-all-search-analytics-information"></a><span data-ttu-id="c0837-103">Obter todas as informações de análise de pesquisas</span><span class="sxs-lookup"><span data-stu-id="c0837-103">Get all search analytics information</span></span>

<span data-ttu-id="c0837-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c0837-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c0837-105">Como obter toda a informação de pesquisa analítica para os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="c0837-105">How to get all the search analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0837-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c0837-106">Prerequisites</span></span>

- <span data-ttu-id="c0837-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c0837-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c0837-108">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="c0837-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="c0837-109">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c0837-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c0837-110">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0837-110">Request syntax</span></span>

| <span data-ttu-id="c0837-111">Método</span><span class="sxs-lookup"><span data-stu-id="c0837-111">Method</span></span>  | <span data-ttu-id="c0837-112">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c0837-112">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="c0837-113">**Obter**</span><span class="sxs-lookup"><span data-stu-id="c0837-113">**GET**</span></span> | <span data-ttu-id="c0837-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/parceiro/v1/analytics/search HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c0837-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/search HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="c0837-115">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="c0837-115">URI parameters</span></span>

|    <span data-ttu-id="c0837-116">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="c0837-116">Parameter</span></span>     |  <span data-ttu-id="c0837-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="c0837-117">Type</span></span>  |                                                                                                                   <span data-ttu-id="c0837-118">Description</span><span class="sxs-lookup"><span data-stu-id="c0837-118">Description</span></span>                                                                                                                    |
|------------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      <span data-ttu-id="c0837-119">filter</span><span class="sxs-lookup"><span data-stu-id="c0837-119">filter</span></span>      | <span data-ttu-id="c0837-120">string</span><span class="sxs-lookup"><span data-stu-id="c0837-120">string</span></span> |                                                                     <span data-ttu-id="c0837-121">Devolve dados correspondentes à condição do filtro.</span><span class="sxs-lookup"><span data-stu-id="c0837-121">Returns data matching the filter condition.</span></span> </br> <span data-ttu-id="c0837-122">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="c0837-122">**Example:**</span></span></br> `.../search?filter=field eq 'value'`                                                                     |
|     <span data-ttu-id="c0837-123">groupby</span><span class="sxs-lookup"><span data-stu-id="c0837-123">groupby</span></span>      | <span data-ttu-id="c0837-124">string</span><span class="sxs-lookup"><span data-stu-id="c0837-124">string</span></span> |                                         <span data-ttu-id="c0837-125">Suporta termos e datas.</span><span class="sxs-lookup"><span data-stu-id="c0837-125">Supports both terms and dates.</span></span> <span data-ttu-id="c0837-126">Lógica de curto-circuito para limitar o número de baldes.</span><span class="sxs-lookup"><span data-stu-id="c0837-126">Short circuit logic to limit the number of buckets.</span></span> </br> <span data-ttu-id="c0837-127">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="c0837-127">**Example:**</span></span></br> `.../search?groupby=termField1,dateField1,termField2`                                         |
| <span data-ttu-id="c0837-128">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="c0837-128">aggregationLevel</span></span> | <span data-ttu-id="c0837-129">string</span><span class="sxs-lookup"><span data-stu-id="c0837-129">string</span></span> | <span data-ttu-id="c0837-130">O parâmetro *agregaçãoLevel* requer um *groupby*.</span><span class="sxs-lookup"><span data-stu-id="c0837-130">The *aggregationLevel* parameter requires a *groupby*.</span></span> <span data-ttu-id="c0837-131">O parâmetro *agregaçãoLevel* aplica-se a todos os campos de data presentes no *grupo*.</span><span class="sxs-lookup"><span data-stu-id="c0837-131">The *aggregationLevel* parameter applies to all date fields present in the *groupby*.</span></span> </br> <span data-ttu-id="c0837-132">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="c0837-132">**Example:**</span></span></br>  `.../search?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
|       <span data-ttu-id="c0837-133">top</span><span class="sxs-lookup"><span data-stu-id="c0837-133">top</span></span>        | <span data-ttu-id="c0837-134">string</span><span class="sxs-lookup"><span data-stu-id="c0837-134">string</span></span> |                                                                     <span data-ttu-id="c0837-135">O limite da página é 10.000.</span><span class="sxs-lookup"><span data-stu-id="c0837-135">The page limit is 10000.</span></span> <span data-ttu-id="c0837-136">Leva qualquer valor inferior a 10.000.</span><span class="sxs-lookup"><span data-stu-id="c0837-136">Takes any value less than 10000.</span></span>  </br> <span data-ttu-id="c0837-137">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="c0837-137">**Example:**</span></span></br>  `.../search?top=100`                                                                     |
|       <span data-ttu-id="c0837-138">saltar</span><span class="sxs-lookup"><span data-stu-id="c0837-138">skip</span></span>       | <span data-ttu-id="c0837-139">string</span><span class="sxs-lookup"><span data-stu-id="c0837-139">string</span></span> |                                                                                  <span data-ttu-id="c0837-140">Número de filas para saltar.</span><span class="sxs-lookup"><span data-stu-id="c0837-140">Number of rows to skip.</span></span> </br> <span data-ttu-id="c0837-141">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="c0837-141">**Example:**</span></span></br> `.../search?top=100&skip=100`                                                                                   |

### <a name="request-headers"></a><span data-ttu-id="c0837-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c0837-142">Request headers</span></span>

<span data-ttu-id="c0837-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c0837-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c0837-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="c0837-144">Request body</span></span>

<span data-ttu-id="c0837-145">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c0837-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c0837-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c0837-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/search HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="c0837-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c0837-147">REST response</span></span>

<span data-ttu-id="c0837-148">Se for bem sucedido, o corpo de resposta contém uma coleção de recursos de [pesquisa.](partner-center-analytics-resources.md#search-resource)</span><span class="sxs-lookup"><span data-stu-id="c0837-148">If successful, the response body contains a collection of [Search](partner-center-analytics-resources.md#search-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c0837-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c0837-149">Response success and error codes</span></span>

<span data-ttu-id="c0837-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c0837-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c0837-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c0837-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c0837-152">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c0837-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c0837-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="c0837-153">Response example</span></span>

```http
{
  "companyName": "my company",
  "contactButtonClicked": false,
  "keywordCountry": null,
  "detailsViewed": true,
  "keywordIndustryFocus": null,
  "mpnId": 2604568,
  "partnerMarket": "CN",
  "keywordProduct": null,
  "referralSubmitted": false,
  "searchDate": "2018-05-30",
  "keywordSearchText": " my company"
}
```

## <a name="see-also"></a><span data-ttu-id="c0837-154">Ver também</span><span class="sxs-lookup"><span data-stu-id="c0837-154">See also</span></span>

- [<span data-ttu-id="c0837-155">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="c0837-155">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
