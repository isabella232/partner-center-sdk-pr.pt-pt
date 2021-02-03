---
title: Obter todas as informações de análise de referências
description: Como obter todas as referências informações de análise.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: Kim-Davis
ms.author: kimnich
ms.openlocfilehash: b470c59cecf8b214e6d90a244e928e5d15ebd3e0
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769080"
---
# <a name="get-all-referrals-analytics-information"></a><span data-ttu-id="bd285-103">Obter todas as informações de análise de referências</span><span class="sxs-lookup"><span data-stu-id="bd285-103">Get all referrals analytics information</span></span>

<span data-ttu-id="bd285-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="bd285-104">**Applies To**</span></span>

- <span data-ttu-id="bd285-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="bd285-105">Partner Center</span></span>
- <span data-ttu-id="bd285-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="bd285-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="bd285-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="bd285-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="bd285-108">Como obter todas as informações de análise de referências para os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="bd285-108">How to get all the referrals analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd285-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bd285-109">Prerequisites</span></span>

- <span data-ttu-id="bd285-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bd285-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bd285-111">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="bd285-111">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="bd285-112">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="bd285-112">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bd285-113">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd285-113">Request syntax</span></span>

| <span data-ttu-id="bd285-114">Método</span><span class="sxs-lookup"><span data-stu-id="bd285-114">Method</span></span>  | <span data-ttu-id="bd285-115">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="bd285-115">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="bd285-116">**Obter**</span><span class="sxs-lookup"><span data-stu-id="bd285-116">**GET**</span></span> | <span data-ttu-id="bd285-117">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/referrals HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="bd285-117">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/referrals HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="bd285-118">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="bd285-118">URI parameters</span></span>

| <span data-ttu-id="bd285-119">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="bd285-119">Parameter</span></span> | <span data-ttu-id="bd285-120">Tipo</span><span class="sxs-lookup"><span data-stu-id="bd285-120">Type</span></span> | <span data-ttu-id="bd285-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd285-121">Description</span></span> |
|-----------|------|-------------|
| <span data-ttu-id="bd285-122">filter</span><span class="sxs-lookup"><span data-stu-id="bd285-122">filter</span></span> | <span data-ttu-id="bd285-123">string</span><span class="sxs-lookup"><span data-stu-id="bd285-123">string</span></span> | <span data-ttu-id="bd285-124">Devolve dados correspondentes à condição do filtro.</span><span class="sxs-lookup"><span data-stu-id="bd285-124">Returns data matching the filter condition.</span></span></br> <span data-ttu-id="bd285-125">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="bd285-125">**Example:**</span></span></br>  `.../referrals?filter=field eq 'value'` |
| <span data-ttu-id="bd285-126">groupby</span><span class="sxs-lookup"><span data-stu-id="bd285-126">groupby</span></span> | <span data-ttu-id="bd285-127">string</span><span class="sxs-lookup"><span data-stu-id="bd285-127">string</span></span> | <span data-ttu-id="bd285-128">Suporta termos e datas.</span><span class="sxs-lookup"><span data-stu-id="bd285-128">Supports both terms and dates.</span></span> <span data-ttu-id="bd285-129">Lógica de curto-circuito para limitar o número de baldes.</span><span class="sxs-lookup"><span data-stu-id="bd285-129">Short circuit logic to limit the number of buckets.</span></span></br> <span data-ttu-id="bd285-130">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="bd285-130">**Example:**</span></span></br>  `.../referrals?groupby=termField1,dateField1,termField2` |
| <span data-ttu-id="bd285-131">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="bd285-131">aggregationLevel</span></span> | <span data-ttu-id="bd285-132">string</span><span class="sxs-lookup"><span data-stu-id="bd285-132">string</span></span> | <span data-ttu-id="bd285-133">O parâmetro *agregaçãoLevel* requer um *groupby*.</span><span class="sxs-lookup"><span data-stu-id="bd285-133">The *aggregationLevel* parameter requires a *groupby*.</span></span> <span data-ttu-id="bd285-134">O parâmetro *agregaçãoLevel* aplica-se a todos os campos de data presentes no *grupo*.</span><span class="sxs-lookup"><span data-stu-id="bd285-134">The *aggregationLevel* parameter applies to all date fields present in the *groupby*.</span></span></br> <span data-ttu-id="bd285-135">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="bd285-135">**Example:**</span></span></br> `.../referrals?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
| <span data-ttu-id="bd285-136">top</span><span class="sxs-lookup"><span data-stu-id="bd285-136">top</span></span> | <span data-ttu-id="bd285-137">string</span><span class="sxs-lookup"><span data-stu-id="bd285-137">string</span></span> | <span data-ttu-id="bd285-138">O limite da página é 10.000.</span><span class="sxs-lookup"><span data-stu-id="bd285-138">The page limit is 10000.</span></span> <span data-ttu-id="bd285-139">Leva qualquer valor inferior a 10.000.</span><span class="sxs-lookup"><span data-stu-id="bd285-139">Takes any value less than 10000.</span></span></br> <span data-ttu-id="bd285-140">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="bd285-140">**Example:**</span></span></br> `.../referrals?top=100`</br> |
| <span data-ttu-id="bd285-141">saltar</span><span class="sxs-lookup"><span data-stu-id="bd285-141">skip</span></span> | <span data-ttu-id="bd285-142">string</span><span class="sxs-lookup"><span data-stu-id="bd285-142">string</span></span> | <span data-ttu-id="bd285-143">Número de filas para saltar.</span><span class="sxs-lookup"><span data-stu-id="bd285-143">Number of rows to skip.</span></span></br> <span data-ttu-id="bd285-144">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="bd285-144">**Example:**</span></span></br>  `.../referrals?top=100&skip=100` |

### <a name="request-headers"></a><span data-ttu-id="bd285-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="bd285-145">Request headers</span></span>

<span data-ttu-id="bd285-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="bd285-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bd285-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="bd285-147">Request body</span></span>

<span data-ttu-id="bd285-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bd285-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="bd285-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="bd285-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/referrals HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="bd285-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="bd285-150">REST response</span></span>

<span data-ttu-id="bd285-151">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [referências.](partner-center-analytics-resources.md#referrals-resource)</span><span class="sxs-lookup"><span data-stu-id="bd285-151">If successful, the response body contains a collection of [Referrals](partner-center-analytics-resources.md#referrals-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bd285-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="bd285-152">Response success and error codes</span></span>

<span data-ttu-id="bd285-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="bd285-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bd285-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="bd285-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bd285-155">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="bd285-155">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="bd285-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="bd285-156">Response example</span></span>

```http
{
  "id": "112310",
  "status": "Accepted",
  "customerMarket": "US",
  "customerName": "Best Customer Ever",
  "customerOrgSize": "10to50employees",
  "acceptedDate": "2018-02-07T23:43:19",
  "acknowledgedDate": "2018-02-07T23:40:50",
  "archivedDate": null,
  "declinedDate": null,
  "expiredDate": null,
  "lostDate": null,
  "missedDate": null,
  "createdDate": "2018-02-04T23:08:59",
  "skippedDate": null,
  "wonDate": null,
  "partnerMarket": "US"
}
```

## <a name="see-also"></a><span data-ttu-id="bd285-157">Ver também</span><span class="sxs-lookup"><span data-stu-id="bd285-157">See also</span></span>

- [<span data-ttu-id="bd285-158">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="bd285-158">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
