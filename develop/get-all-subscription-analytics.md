---
title: Obter todas as informações de análise de subscrições
description: Como obter todas as informações de análise de subscrição.
ms.date: 08/02/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: e1f16c92569a02bc51c96a85ecb642fbeb76a9a7
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760254"
---
# <a name="get-all-subscription-analytics-information"></a><span data-ttu-id="08807-103">Obter todas as informações de análise de subscrições</span><span class="sxs-lookup"><span data-stu-id="08807-103">Get all subscription analytics information</span></span>

<span data-ttu-id="08807-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="08807-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="08807-105">Este artigo descreve como obter todas as informações de análise de subscrição para os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="08807-105">This article describes how to get all the subscription analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08807-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="08807-106">Prerequisites</span></span>

- <span data-ttu-id="08807-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="08807-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="08807-108">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="08807-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="08807-109">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="08807-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="08807-110">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="08807-110">Request syntax</span></span>

| <span data-ttu-id="08807-111">Método</span><span class="sxs-lookup"><span data-stu-id="08807-111">Method</span></span> | <span data-ttu-id="08807-112">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="08807-112">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="08807-113">**Obter**</span><span class="sxs-lookup"><span data-stu-id="08807-113">**GET**</span></span> | <span data-ttu-id="08807-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscrições HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="08807-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="08807-115">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="08807-115">URI parameters</span></span>

<span data-ttu-id="08807-116">O quadro que se segue enumera os parâmetros opcionais e as suas descrições:</span><span class="sxs-lookup"><span data-stu-id="08807-116">The following table lists optional parameters and their descriptions:</span></span>

| <span data-ttu-id="08807-117">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="08807-117">Parameter</span></span> | <span data-ttu-id="08807-118">Tipo</span><span class="sxs-lookup"><span data-stu-id="08807-118">Type</span></span> |  <span data-ttu-id="08807-119">Description</span><span class="sxs-lookup"><span data-stu-id="08807-119">Description</span></span> |
|-----------|------|--------------|
| <span data-ttu-id="08807-120">top</span><span class="sxs-lookup"><span data-stu-id="08807-120">top</span></span> | <span data-ttu-id="08807-121">int</span><span class="sxs-lookup"><span data-stu-id="08807-121">int</span></span> | <span data-ttu-id="08807-122">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="08807-122">The number of rows of data to return in the request.</span></span> <span data-ttu-id="08807-123">Se o valor não for especificado, o valor máximo e o valor predefinido são `10000` .</span><span class="sxs-lookup"><span data-stu-id="08807-123">If the value isn't specified, the maximum value and the default value are `10000`.</span></span> <span data-ttu-id="08807-124">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="08807-124">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |
| <span data-ttu-id="08807-125">saltar</span><span class="sxs-lookup"><span data-stu-id="08807-125">skip</span></span> | <span data-ttu-id="08807-126">int</span><span class="sxs-lookup"><span data-stu-id="08807-126">int</span></span> | <span data-ttu-id="08807-127">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="08807-127">The number of rows to skip in the query.</span></span> <span data-ttu-id="08807-128">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="08807-128">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="08807-129">Por exemplo, `top=10000` e `skip=0` recupera as primeiras 10000 linhas de dados, `top=10000` e recupera as `skip=10000` próximas 10000 linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="08807-129">For example, `top=10000` and `skip=0` retrieves the first 10000 rows of data, `top=10000` and `skip=10000` retrieves the next 10000 rows of data.</span></span> |
| <span data-ttu-id="08807-130">filter</span><span class="sxs-lookup"><span data-stu-id="08807-130">filter</span></span> | <span data-ttu-id="08807-131">string</span><span class="sxs-lookup"><span data-stu-id="08807-131">string</span></span> | <span data-ttu-id="08807-132">Uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="08807-132">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="08807-133">Cada declaração de filtro contém um nome de campo do corpo de resposta e um valor que está associado ao **`eq`** , ou para certos **`ne`** campos, o **`contains`** operador.</span><span class="sxs-lookup"><span data-stu-id="08807-133">Each filter statement contains a field name from the response body and a value that are associated with the **`eq`**, **`ne`**, or for certain fields, the **`contains`** operator.</span></span> <span data-ttu-id="08807-134">As declarações podem ser combinadas utilizando **`and`** ou **`or`** .</span><span class="sxs-lookup"><span data-stu-id="08807-134">Statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="08807-135">Os valores das cordas devem ser rodeados por citações únicas no parâmetro do **filtro.**</span><span class="sxs-lookup"><span data-stu-id="08807-135">String values must be surrounded by single quotes in the **filter** parameter.</span></span> <span data-ttu-id="08807-136">Consulte a secção seguinte para obter uma lista de campos que podem ser filtrados e os operadores que são apoiados nesses campos.</span><span class="sxs-lookup"><span data-stu-id="08807-136">See the following section for a list of fields that can be filtered and the operators that are supported with those fields.</span></span> |
| <span data-ttu-id="08807-137">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="08807-137">aggregationLevel</span></span> | <span data-ttu-id="08807-138">string</span><span class="sxs-lookup"><span data-stu-id="08807-138">string</span></span> | <span data-ttu-id="08807-139">Especifica o intervalo de tempo para a recuperação de dados agregados.</span><span class="sxs-lookup"><span data-stu-id="08807-139">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="08807-140">Pode ser uma das seguintes cordas: **dia,** **semana,** **ou mês.**</span><span class="sxs-lookup"><span data-stu-id="08807-140">Can be one of the following strings: **day**, **week**, or **month**.</span></span> <span data-ttu-id="08807-141">Se o valor não for especificado, o padrão é **dataRange**.</span><span class="sxs-lookup"><span data-stu-id="08807-141">If the value isn't specified, the default is **dateRange**.</span></span> <span data-ttu-id="08807-142">Este parâmetro só se aplica quando um campo de data é passado como parte do parâmetro **groupBy.**</span><span class="sxs-lookup"><span data-stu-id="08807-142">This parameter applies only when a date field is passed as part of the **groupBy** parameter.</span></span> |
| <span data-ttu-id="08807-143">grupoBy</span><span class="sxs-lookup"><span data-stu-id="08807-143">groupBy</span></span> | <span data-ttu-id="08807-144">string</span><span class="sxs-lookup"><span data-stu-id="08807-144">string</span></span> | <span data-ttu-id="08807-145">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="08807-145">A statement that applies data aggregation only to the specified fields.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="08807-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="08807-146">Request headers</span></span>

<span data-ttu-id="08807-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="08807-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="08807-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="08807-148">Request body</span></span>

<span data-ttu-id="08807-149">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="08807-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="08807-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="08807-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="08807-151">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="08807-151">REST response</span></span>

<span data-ttu-id="08807-152">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [**Subscrição.**](partner-center-analytics-resources.md#subscription-resource)</span><span class="sxs-lookup"><span data-stu-id="08807-152">If successful, the response body contains a collection of [**Subscription**](partner-center-analytics-resources.md#subscription-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="08807-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="08807-153">Response success and error codes</span></span>

<span data-ttu-id="08807-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="08807-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="08807-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="08807-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="08807-156">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="08807-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="08807-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="08807-157">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="08807-158">Ver também</span><span class="sxs-lookup"><span data-stu-id="08807-158">See also</span></span>

- [<span data-ttu-id="08807-159">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="08807-159">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
