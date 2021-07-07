---
title: Obter todas as informações de análise de referências
description: Como obter todas as referências informações de análise.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: Kim-Davis
ms.author: kimnich
ms.openlocfilehash: 7deda4098ceb9eb4e1ee75056c53c754618bf3e2
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760611"
---
# <a name="get-all-referrals-analytics-information"></a><span data-ttu-id="a0f4a-103">Obter todas as informações de análise de referências</span><span class="sxs-lookup"><span data-stu-id="a0f4a-103">Get all referrals analytics information</span></span>

<span data-ttu-id="a0f4a-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="a0f4a-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="a0f4a-105">Como obter todas as informações de análise de referências para os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-105">How to get all the referrals analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0f4a-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a0f4a-106">Prerequisites</span></span>

- <span data-ttu-id="a0f4a-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a0f4a-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a0f4a-108">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="a0f4a-109">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="a0f4a-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a0f4a-110">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0f4a-110">Request syntax</span></span>

| <span data-ttu-id="a0f4a-111">Método</span><span class="sxs-lookup"><span data-stu-id="a0f4a-111">Method</span></span>  | <span data-ttu-id="a0f4a-112">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="a0f4a-112">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="a0f4a-113">**Obter**</span><span class="sxs-lookup"><span data-stu-id="a0f4a-113">**GET**</span></span> | <span data-ttu-id="a0f4a-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/referrals HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a0f4a-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/referrals HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="a0f4a-115">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="a0f4a-115">URI parameters</span></span>

| <span data-ttu-id="a0f4a-116">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a0f4a-116">Parameter</span></span> | <span data-ttu-id="a0f4a-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="a0f4a-117">Type</span></span> | <span data-ttu-id="a0f4a-118">Description</span><span class="sxs-lookup"><span data-stu-id="a0f4a-118">Description</span></span> |
|-----------|------|-------------|
| <span data-ttu-id="a0f4a-119">filter</span><span class="sxs-lookup"><span data-stu-id="a0f4a-119">filter</span></span> | <span data-ttu-id="a0f4a-120">string</span><span class="sxs-lookup"><span data-stu-id="a0f4a-120">string</span></span> | <span data-ttu-id="a0f4a-121">Devolve dados correspondentes à condição do filtro.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-121">Returns data matching the filter condition.</span></span></br> <span data-ttu-id="a0f4a-122">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="a0f4a-122">**Example:**</span></span></br>  `.../referrals?filter=field eq 'value'` |
| <span data-ttu-id="a0f4a-123">groupby</span><span class="sxs-lookup"><span data-stu-id="a0f4a-123">groupby</span></span> | <span data-ttu-id="a0f4a-124">string</span><span class="sxs-lookup"><span data-stu-id="a0f4a-124">string</span></span> | <span data-ttu-id="a0f4a-125">Suporta termos e datas.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-125">Supports both terms and dates.</span></span> <span data-ttu-id="a0f4a-126">Lógica de curto-circuito para limitar o número de baldes.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-126">Short circuit logic to limit the number of buckets.</span></span></br> <span data-ttu-id="a0f4a-127">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="a0f4a-127">**Example:**</span></span></br>  `.../referrals?groupby=termField1,dateField1,termField2` |
| <span data-ttu-id="a0f4a-128">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="a0f4a-128">aggregationLevel</span></span> | <span data-ttu-id="a0f4a-129">string</span><span class="sxs-lookup"><span data-stu-id="a0f4a-129">string</span></span> | <span data-ttu-id="a0f4a-130">O parâmetro *agregaçãoLevel* requer um *groupby*.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-130">The *aggregationLevel* parameter requires a *groupby*.</span></span> <span data-ttu-id="a0f4a-131">O parâmetro *agregaçãoLevel* aplica-se a todos os campos de data presentes no *grupo*.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-131">The *aggregationLevel* parameter applies to all date fields present in the *groupby*.</span></span></br> <span data-ttu-id="a0f4a-132">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="a0f4a-132">**Example:**</span></span></br> `.../referrals?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
| <span data-ttu-id="a0f4a-133">top</span><span class="sxs-lookup"><span data-stu-id="a0f4a-133">top</span></span> | <span data-ttu-id="a0f4a-134">string</span><span class="sxs-lookup"><span data-stu-id="a0f4a-134">string</span></span> | <span data-ttu-id="a0f4a-135">O limite da página é 10.000.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-135">The page limit is 10000.</span></span> <span data-ttu-id="a0f4a-136">Leva qualquer valor inferior a 10.000.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-136">Takes any value less than 10000.</span></span></br> <span data-ttu-id="a0f4a-137">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="a0f4a-137">**Example:**</span></span></br> `.../referrals?top=100`</br> |
| <span data-ttu-id="a0f4a-138">saltar</span><span class="sxs-lookup"><span data-stu-id="a0f4a-138">skip</span></span> | <span data-ttu-id="a0f4a-139">string</span><span class="sxs-lookup"><span data-stu-id="a0f4a-139">string</span></span> | <span data-ttu-id="a0f4a-140">Número de filas para saltar.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-140">Number of rows to skip.</span></span></br> <span data-ttu-id="a0f4a-141">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="a0f4a-141">**Example:**</span></span></br>  `.../referrals?top=100&skip=100` |

### <a name="request-headers"></a><span data-ttu-id="a0f4a-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="a0f4a-142">Request headers</span></span>

<span data-ttu-id="a0f4a-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a0f4a-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a0f4a-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="a0f4a-144">Request body</span></span>

<span data-ttu-id="a0f4a-145">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="a0f4a-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a0f4a-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/referrals HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="a0f4a-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="a0f4a-147">REST response</span></span>

<span data-ttu-id="a0f4a-148">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [referências.](partner-center-analytics-resources.md#referrals-resource)</span><span class="sxs-lookup"><span data-stu-id="a0f4a-148">If successful, the response body contains a collection of [Referrals](partner-center-analytics-resources.md#referrals-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a0f4a-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="a0f4a-149">Response success and error codes</span></span>

<span data-ttu-id="a0f4a-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a0f4a-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="a0f4a-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a0f4a-152">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="a0f4a-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a0f4a-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a0f4a-153">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a0f4a-154">Ver também</span><span class="sxs-lookup"><span data-stu-id="a0f4a-154">See also</span></span>

- [<span data-ttu-id="a0f4a-155">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="a0f4a-155">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
