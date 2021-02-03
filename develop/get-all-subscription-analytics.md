---
title: Obter todas as informações de análise de subscrições
description: Como obter todas as informações de análise de subscrição.
ms.date: 08/02/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: f32fb99ad52939ae8e9de26276588d3022f18fbc
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768755"
---
# <a name="get-all-subscription-analytics-information"></a><span data-ttu-id="cffeb-103">Obter todas as informações de análise de subscrições</span><span class="sxs-lookup"><span data-stu-id="cffeb-103">Get all subscription analytics information</span></span>

<span data-ttu-id="cffeb-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="cffeb-104">**Applies to:**</span></span>

- <span data-ttu-id="cffeb-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="cffeb-105">Partner Center</span></span>
- <span data-ttu-id="cffeb-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="cffeb-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="cffeb-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="cffeb-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="cffeb-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cffeb-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cffeb-109">Este artigo descreve como obter todas as informações de análise de subscrição para os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="cffeb-109">This article describes how to get all the subscription analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cffeb-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="cffeb-110">Prerequisites</span></span>

- <span data-ttu-id="cffeb-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cffeb-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cffeb-112">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="cffeb-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="cffeb-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="cffeb-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cffeb-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="cffeb-114">Request syntax</span></span>

| <span data-ttu-id="cffeb-115">Método</span><span class="sxs-lookup"><span data-stu-id="cffeb-115">Method</span></span> | <span data-ttu-id="cffeb-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="cffeb-116">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="cffeb-117">**Obter**</span><span class="sxs-lookup"><span data-stu-id="cffeb-117">**GET**</span></span> | <span data-ttu-id="cffeb-118">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscrições HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="cffeb-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="cffeb-119">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="cffeb-119">URI parameters</span></span>

<span data-ttu-id="cffeb-120">O quadro que se segue enumera os parâmetros opcionais e as suas descrições:</span><span class="sxs-lookup"><span data-stu-id="cffeb-120">The following table lists optional parameters and their descriptions:</span></span>

| <span data-ttu-id="cffeb-121">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="cffeb-121">Parameter</span></span> | <span data-ttu-id="cffeb-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="cffeb-122">Type</span></span> |  <span data-ttu-id="cffeb-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="cffeb-123">Description</span></span> |
|-----------|------|--------------|
| <span data-ttu-id="cffeb-124">top</span><span class="sxs-lookup"><span data-stu-id="cffeb-124">top</span></span> | <span data-ttu-id="cffeb-125">int</span><span class="sxs-lookup"><span data-stu-id="cffeb-125">int</span></span> | <span data-ttu-id="cffeb-126">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="cffeb-126">The number of rows of data to return in the request.</span></span> <span data-ttu-id="cffeb-127">Se o valor não for especificado, o valor máximo e o valor predefinido são `10000` .</span><span class="sxs-lookup"><span data-stu-id="cffeb-127">If the value isn't specified, the maximum value and the default value are `10000`.</span></span> <span data-ttu-id="cffeb-128">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="cffeb-128">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |
| <span data-ttu-id="cffeb-129">saltar</span><span class="sxs-lookup"><span data-stu-id="cffeb-129">skip</span></span> | <span data-ttu-id="cffeb-130">int</span><span class="sxs-lookup"><span data-stu-id="cffeb-130">int</span></span> | <span data-ttu-id="cffeb-131">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="cffeb-131">The number of rows to skip in the query.</span></span> <span data-ttu-id="cffeb-132">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="cffeb-132">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="cffeb-133">Por exemplo, `top=10000` e `skip=0` recupera as primeiras 10000 linhas de dados, `top=10000` e recupera as `skip=10000` próximas 10000 linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="cffeb-133">For example, `top=10000` and `skip=0` retrieves the first 10000 rows of data, `top=10000` and `skip=10000` retrieves the next 10000 rows of data.</span></span> |
| <span data-ttu-id="cffeb-134">filter</span><span class="sxs-lookup"><span data-stu-id="cffeb-134">filter</span></span> | <span data-ttu-id="cffeb-135">string</span><span class="sxs-lookup"><span data-stu-id="cffeb-135">string</span></span> | <span data-ttu-id="cffeb-136">Uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="cffeb-136">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="cffeb-137">Cada declaração de filtro contém um nome de campo do corpo de resposta e um valor que está associado ao **`eq`** , ou para certos **`ne`** campos, o **`contains`** operador.</span><span class="sxs-lookup"><span data-stu-id="cffeb-137">Each filter statement contains a field name from the response body and a value that are associated with the **`eq`**, **`ne`**, or for certain fields, the **`contains`** operator.</span></span> <span data-ttu-id="cffeb-138">As declarações podem ser combinadas utilizando **`and`** ou **`or`** .</span><span class="sxs-lookup"><span data-stu-id="cffeb-138">Statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="cffeb-139">Os valores das cordas devem ser rodeados por citações únicas no parâmetro do **filtro.**</span><span class="sxs-lookup"><span data-stu-id="cffeb-139">String values must be surrounded by single quotes in the **filter** parameter.</span></span> <span data-ttu-id="cffeb-140">Consulte a secção seguinte para obter uma lista de campos que podem ser filtrados e os operadores que são apoiados nesses campos.</span><span class="sxs-lookup"><span data-stu-id="cffeb-140">See the following section for a list of fields that can be filtered and the operators that are supported with those fields.</span></span> |
| <span data-ttu-id="cffeb-141">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="cffeb-141">aggregationLevel</span></span> | <span data-ttu-id="cffeb-142">string</span><span class="sxs-lookup"><span data-stu-id="cffeb-142">string</span></span> | <span data-ttu-id="cffeb-143">Especifica o intervalo de tempo para a recuperação de dados agregados.</span><span class="sxs-lookup"><span data-stu-id="cffeb-143">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="cffeb-144">Pode ser uma das seguintes cordas: **dia,** **semana,** **ou mês.**</span><span class="sxs-lookup"><span data-stu-id="cffeb-144">Can be one of the following strings: **day**, **week**, or **month**.</span></span> <span data-ttu-id="cffeb-145">Se o valor não for especificado, o padrão é **dataRange**.</span><span class="sxs-lookup"><span data-stu-id="cffeb-145">If the value isn't specified, the default is **dateRange**.</span></span> <span data-ttu-id="cffeb-146">Este parâmetro só se aplica quando um campo de data é passado como parte do parâmetro **groupBy.**</span><span class="sxs-lookup"><span data-stu-id="cffeb-146">This parameter applies only when a date field is passed as part of the **groupBy** parameter.</span></span> |
| <span data-ttu-id="cffeb-147">grupoBy</span><span class="sxs-lookup"><span data-stu-id="cffeb-147">groupBy</span></span> | <span data-ttu-id="cffeb-148">string</span><span class="sxs-lookup"><span data-stu-id="cffeb-148">string</span></span> | <span data-ttu-id="cffeb-149">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="cffeb-149">A statement that applies data aggregation only to the specified fields.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cffeb-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="cffeb-150">Request headers</span></span>

<span data-ttu-id="cffeb-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cffeb-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cffeb-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="cffeb-152">Request body</span></span>

<span data-ttu-id="cffeb-153">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cffeb-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="cffeb-154">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="cffeb-154">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="cffeb-155">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="cffeb-155">REST response</span></span>

<span data-ttu-id="cffeb-156">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [**Subscrição.**](partner-center-analytics-resources.md#subscription-resource)</span><span class="sxs-lookup"><span data-stu-id="cffeb-156">If successful, the response body contains a collection of [**Subscription**](partner-center-analytics-resources.md#subscription-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cffeb-157">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="cffeb-157">Response success and error codes</span></span>

<span data-ttu-id="cffeb-158">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="cffeb-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cffeb-159">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="cffeb-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cffeb-160">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="cffeb-160">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cffeb-161">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="cffeb-161">Response example</span></span>

```http
{
    "customerTenantId": "76906668-27FC-4F5B-A35C-75A9823E13AF",
    "customerName": "TESTORG65656565",
    "customerMarket": "US",
    "id": "4BF546B2-8998-4838-BEE2-5F1BBE65A04F",
    "status": "ACTIVE",
    "productName": "OFFICE 365 BUSINESS PREMIUM",
    "subscriptionType": "Office",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "FULL OFFICE SUITE",
    "partnerName": "Partner Name",
    "providerName": "Provider Name",
    "creationDate": "2016-02-04T19:29:38.037",
   "effectiveStartDate": "2016-02-04T00:00:00",
    "commitmentEndDate": "2019-02-10T00:00:00",
    "currentStateEndDate": "2019-02-10T00:00:00",
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": "2018-02-10T02:39:57.729",
    "licenseCount": 2,
    "churnRisk": "High",
    "billingCycleName": "MONTHLY"

}
```

## <a name="see-also"></a><span data-ttu-id="cffeb-162">Ver também</span><span class="sxs-lookup"><span data-stu-id="cffeb-162">See also</span></span>

- [<span data-ttu-id="cffeb-163">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="cffeb-163">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
