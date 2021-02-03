---
title: Obter todas as informações de análise de pesquisas
description: Como obter toda a informação de pesquisa analítica.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 967f8d0ed2d276e0f68a047204b64d83dc69da95
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768756"
---
# <a name="get-all-search-analytics-information"></a><span data-ttu-id="d00f9-103">Obter todas as informações de análise de pesquisas</span><span class="sxs-lookup"><span data-stu-id="d00f9-103">Get all search analytics information</span></span>

<span data-ttu-id="d00f9-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="d00f9-104">**Applies To**</span></span>

- <span data-ttu-id="d00f9-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="d00f9-105">Partner Center</span></span>
- <span data-ttu-id="d00f9-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="d00f9-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="d00f9-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="d00f9-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="d00f9-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d00f9-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d00f9-109">Como obter toda a informação de pesquisa analítica para os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="d00f9-109">How to get all the search analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d00f9-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d00f9-110">Prerequisites</span></span>

- <span data-ttu-id="d00f9-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d00f9-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d00f9-112">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="d00f9-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="d00f9-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d00f9-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d00f9-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d00f9-114">Request syntax</span></span>

| <span data-ttu-id="d00f9-115">Método</span><span class="sxs-lookup"><span data-stu-id="d00f9-115">Method</span></span>  | <span data-ttu-id="d00f9-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d00f9-116">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="d00f9-117">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d00f9-117">**GET**</span></span> | <span data-ttu-id="d00f9-118">[*\{ baseURL \}*](partner-center-rest-urls.md)/parceiro/v1/analytics/search HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d00f9-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/search HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="d00f9-119">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="d00f9-119">URI parameters</span></span>

|    <span data-ttu-id="d00f9-120">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d00f9-120">Parameter</span></span>     |  <span data-ttu-id="d00f9-121">Tipo</span><span class="sxs-lookup"><span data-stu-id="d00f9-121">Type</span></span>  |                                                                                                                   <span data-ttu-id="d00f9-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d00f9-122">Description</span></span>                                                                                                                    |
|------------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      <span data-ttu-id="d00f9-123">filter</span><span class="sxs-lookup"><span data-stu-id="d00f9-123">filter</span></span>      | <span data-ttu-id="d00f9-124">string</span><span class="sxs-lookup"><span data-stu-id="d00f9-124">string</span></span> |                                                                     <span data-ttu-id="d00f9-125">Devolve dados correspondentes à condição do filtro.</span><span class="sxs-lookup"><span data-stu-id="d00f9-125">Returns data matching the filter condition.</span></span> </br> <span data-ttu-id="d00f9-126">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="d00f9-126">**Example:**</span></span></br> `.../search?filter=field eq 'value'`                                                                     |
|     <span data-ttu-id="d00f9-127">groupby</span><span class="sxs-lookup"><span data-stu-id="d00f9-127">groupby</span></span>      | <span data-ttu-id="d00f9-128">string</span><span class="sxs-lookup"><span data-stu-id="d00f9-128">string</span></span> |                                         <span data-ttu-id="d00f9-129">Suporta termos e datas.</span><span class="sxs-lookup"><span data-stu-id="d00f9-129">Supports both terms and dates.</span></span> <span data-ttu-id="d00f9-130">Lógica de curto-circuito para limitar o número de baldes.</span><span class="sxs-lookup"><span data-stu-id="d00f9-130">Short circuit logic to limit the number of buckets.</span></span> </br> <span data-ttu-id="d00f9-131">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="d00f9-131">**Example:**</span></span></br> `.../search?groupby=termField1,dateField1,termField2`                                         |
| <span data-ttu-id="d00f9-132">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="d00f9-132">aggregationLevel</span></span> | <span data-ttu-id="d00f9-133">string</span><span class="sxs-lookup"><span data-stu-id="d00f9-133">string</span></span> | <span data-ttu-id="d00f9-134">O parâmetro *agregaçãoLevel* requer um *groupby*.</span><span class="sxs-lookup"><span data-stu-id="d00f9-134">The *aggregationLevel* parameter requires a *groupby*.</span></span> <span data-ttu-id="d00f9-135">O parâmetro *agregaçãoLevel* aplica-se a todos os campos de data presentes no *grupo*.</span><span class="sxs-lookup"><span data-stu-id="d00f9-135">The *aggregationLevel* parameter applies to all date fields present in the *groupby*.</span></span> </br> <span data-ttu-id="d00f9-136">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="d00f9-136">**Example:**</span></span></br>  `.../search?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
|       <span data-ttu-id="d00f9-137">top</span><span class="sxs-lookup"><span data-stu-id="d00f9-137">top</span></span>        | <span data-ttu-id="d00f9-138">string</span><span class="sxs-lookup"><span data-stu-id="d00f9-138">string</span></span> |                                                                     <span data-ttu-id="d00f9-139">O limite da página é 10.000.</span><span class="sxs-lookup"><span data-stu-id="d00f9-139">The page limit is 10000.</span></span> <span data-ttu-id="d00f9-140">Leva qualquer valor inferior a 10.000.</span><span class="sxs-lookup"><span data-stu-id="d00f9-140">Takes any value less than 10000.</span></span>  </br> <span data-ttu-id="d00f9-141">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="d00f9-141">**Example:**</span></span></br>  `.../search?top=100`                                                                     |
|       <span data-ttu-id="d00f9-142">saltar</span><span class="sxs-lookup"><span data-stu-id="d00f9-142">skip</span></span>       | <span data-ttu-id="d00f9-143">string</span><span class="sxs-lookup"><span data-stu-id="d00f9-143">string</span></span> |                                                                                  <span data-ttu-id="d00f9-144">Número de filas para saltar.</span><span class="sxs-lookup"><span data-stu-id="d00f9-144">Number of rows to skip.</span></span> </br> <span data-ttu-id="d00f9-145">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="d00f9-145">**Example:**</span></span></br> `.../search?top=100&skip=100`                                                                                   |

### <a name="request-headers"></a><span data-ttu-id="d00f9-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d00f9-146">Request headers</span></span>

<span data-ttu-id="d00f9-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d00f9-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d00f9-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d00f9-148">Request body</span></span>

<span data-ttu-id="d00f9-149">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d00f9-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d00f9-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d00f9-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/search HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="d00f9-151">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d00f9-151">REST response</span></span>

<span data-ttu-id="d00f9-152">Se for bem sucedido, o corpo de resposta contém uma coleção de recursos de [pesquisa.](partner-center-analytics-resources.md#search-resource)</span><span class="sxs-lookup"><span data-stu-id="d00f9-152">If successful, the response body contains a collection of [Search](partner-center-analytics-resources.md#search-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d00f9-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d00f9-153">Response success and error codes</span></span>

<span data-ttu-id="d00f9-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d00f9-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d00f9-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d00f9-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d00f9-156">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d00f9-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d00f9-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d00f9-157">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d00f9-158">Ver também</span><span class="sxs-lookup"><span data-stu-id="d00f9-158">See also</span></span>

- [<span data-ttu-id="d00f9-159">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="d00f9-159">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
