---
title: Obter informações de utilização de licenças
description: Como obter informações de utilização de licenças ao nível da carga de trabalho para Office and Dynamics.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a144fd078a36289e4a2c70880817b1f0ca627e8a
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769428"
---
# <a name="get-licenses-usage-information"></a><span data-ttu-id="c4387-103">Obter informações de utilização de licenças</span><span class="sxs-lookup"><span data-stu-id="c4387-103">Get licenses usage information</span></span>

<span data-ttu-id="c4387-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="c4387-104">**Applies To**</span></span>

- <span data-ttu-id="c4387-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="c4387-105">Partner Center</span></span>

<span data-ttu-id="c4387-106">Como obter informações de utilização de licenças ao nível da carga de trabalho para Office and Dynamics.</span><span class="sxs-lookup"><span data-stu-id="c4387-106">How to get licenses usage information at the workload level for Office and Dynamics.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c4387-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c4387-107">Prerequisites</span></span>

<span data-ttu-id="c4387-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c4387-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c4387-109">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="c4387-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="c4387-110">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c4387-110">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c4387-111">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4387-111">Request syntax</span></span>

| <span data-ttu-id="c4387-112">Método</span><span class="sxs-lookup"><span data-stu-id="c4387-112">Method</span></span>  | <span data-ttu-id="c4387-113">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c4387-113">Request URI</span></span>                                                                                |
|---------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="c4387-114">**Obter**</span><span class="sxs-lookup"><span data-stu-id="c4387-114">**GET**</span></span> | <span data-ttu-id="c4387-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/usage/license/ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c4387-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/usage/license/ HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c4387-116">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c4387-116">Request headers</span></span>

<span data-ttu-id="c4387-117">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c4387-117">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="uri-parameters"></a><span data-ttu-id="c4387-118">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="c4387-118">URI parameters</span></span>

| <span data-ttu-id="c4387-119">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="c4387-119">Parameter</span></span>         | <span data-ttu-id="c4387-120">Tipo</span><span class="sxs-lookup"><span data-stu-id="c4387-120">Type</span></span>     | <span data-ttu-id="c4387-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4387-121">Description</span></span> | <span data-ttu-id="c4387-122">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c4387-122">Required</span></span> |
|-------------------|----------|-------------|----------|
| <span data-ttu-id="c4387-123">top</span><span class="sxs-lookup"><span data-stu-id="c4387-123">top</span></span>               | <span data-ttu-id="c4387-124">string</span><span class="sxs-lookup"><span data-stu-id="c4387-124">string</span></span>   | <span data-ttu-id="c4387-125">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="c4387-125">The number of rows of data to return in the request.</span></span> <span data-ttu-id="c4387-126">O valor máximo e o valor predefinido se não especificado for 10000.</span><span class="sxs-lookup"><span data-stu-id="c4387-126">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="c4387-127">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="c4387-127">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> | <span data-ttu-id="c4387-128">Não</span><span class="sxs-lookup"><span data-stu-id="c4387-128">No</span></span> |
| <span data-ttu-id="c4387-129">saltar</span><span class="sxs-lookup"><span data-stu-id="c4387-129">skip</span></span>              | <span data-ttu-id="c4387-130">int</span><span class="sxs-lookup"><span data-stu-id="c4387-130">int</span></span>      | <span data-ttu-id="c4387-131">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="c4387-131">The number of rows to skip in the query.</span></span> <span data-ttu-id="c4387-132">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="c4387-132">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="c4387-133">Por exemplo, top=10000 e skip=0 recupera as primeiras 10000 linhas de dados, top=10000 e skip=10000 recupera as próximas 10000 linhas de dados, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c4387-133">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> | <span data-ttu-id="c4387-134">Não</span><span class="sxs-lookup"><span data-stu-id="c4387-134">No</span></span> |
| <span data-ttu-id="c4387-135">filter</span><span class="sxs-lookup"><span data-stu-id="c4387-135">filter</span></span>            | <span data-ttu-id="c4387-136">string</span><span class="sxs-lookup"><span data-stu-id="c4387-136">string</span></span>   | <span data-ttu-id="c4387-137">O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="c4387-137">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="c4387-138">Cada declaração contém um campo e valor que estão associados aos **`eq`** **`ne`** ou operadores, e as declarações podem ser combinadas usando **`and`** ou **`or`** .</span><span class="sxs-lookup"><span data-stu-id="c4387-138">Each statement contains a field and value that are associated with the **`eq`** or **`ne`** operators, and statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="c4387-139">Aqui estão alguns parâmetros *de filtragem* de exemplo:</span><span class="sxs-lookup"><span data-stu-id="c4387-139">Here are some example *filter* parameters:</span></span><br/><br/><span data-ttu-id="c4387-140">*filter=workloadCode eq 'SFB'*</span><span class="sxs-lookup"><span data-stu-id="c4387-140">*filter=workloadCode eq 'SFB'*</span></span><br/><br/><span data-ttu-id="c4387-141">*filter=workloadCode eq 'SFB'* ou *(canal eq 'Revendedor'*)</span><span class="sxs-lookup"><span data-stu-id="c4387-141">*filter=workloadCode eq 'SFB'* or (*channel eq 'Reseller'*)</span></span><br/><br/><span data-ttu-id="c4387-142">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="c4387-142">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="c4387-143">**código de carga de trabalho**</span><span class="sxs-lookup"><span data-stu-id="c4387-143">**workloadCode**</span></span><br/><span data-ttu-id="c4387-144">**carga de trabalhoName**</span><span class="sxs-lookup"><span data-stu-id="c4387-144">**workloadName**</span></span><br/><span data-ttu-id="c4387-145">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="c4387-145">**serviceCode**</span></span><br/><span data-ttu-id="c4387-146">**nome de serviço**</span><span class="sxs-lookup"><span data-stu-id="c4387-146">**serviceName**</span></span><br/><span data-ttu-id="c4387-147">**canal**</span><span class="sxs-lookup"><span data-stu-id="c4387-147">**channel**</span></span><br/><span data-ttu-id="c4387-148">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="c4387-148">**customerTenantId**</span></span><br/><span data-ttu-id="c4387-149">**nome do cliente**</span><span class="sxs-lookup"><span data-stu-id="c4387-149">**customerName**</span></span><br/><span data-ttu-id="c4387-150">**productId**</span><span class="sxs-lookup"><span data-stu-id="c4387-150">**productId**</span></span><br/><span data-ttu-id="c4387-151">**produtoName**</span><span class="sxs-lookup"><span data-stu-id="c4387-151">**productName**</span></span> | <span data-ttu-id="c4387-152">Não</span><span class="sxs-lookup"><span data-stu-id="c4387-152">No</span></span> |
| <span data-ttu-id="c4387-153">groupby</span><span class="sxs-lookup"><span data-stu-id="c4387-153">groupby</span></span>           | <span data-ttu-id="c4387-154">string</span><span class="sxs-lookup"><span data-stu-id="c4387-154">string</span></span>   | <span data-ttu-id="c4387-155">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="c4387-155">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="c4387-156">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="c4387-156">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="c4387-157">**código de carga de trabalho**</span><span class="sxs-lookup"><span data-stu-id="c4387-157">**workloadCode**</span></span><br/><span data-ttu-id="c4387-158">**carga de trabalhoName**</span><span class="sxs-lookup"><span data-stu-id="c4387-158">**workloadName**</span></span><br/><span data-ttu-id="c4387-159">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="c4387-159">**serviceCode**</span></span><br/><span data-ttu-id="c4387-160">**nome de serviço**</span><span class="sxs-lookup"><span data-stu-id="c4387-160">**serviceName**</span></span><br/><span data-ttu-id="c4387-161">**channelcustomerTenantId**</span><span class="sxs-lookup"><span data-stu-id="c4387-161">**channelcustomerTenantId**</span></span><br/><span data-ttu-id="c4387-162">**nome do cliente**</span><span class="sxs-lookup"><span data-stu-id="c4387-162">**customerName**</span></span><br/><span data-ttu-id="c4387-163">**productId**</span><span class="sxs-lookup"><span data-stu-id="c4387-163">**productId**</span></span><br/><span data-ttu-id="c4387-164">**produtoName**</span><span class="sxs-lookup"><span data-stu-id="c4387-164">**productName**</span></span><br/><br/><span data-ttu-id="c4387-165">As linhas de dados devolvidas conterão os campos especificados no parâmetro *groupby,* bem como os seguintes:</span><span class="sxs-lookup"><span data-stu-id="c4387-165">The returned data rows will contain the fields specified in the *groupby* parameter as well as the following:</span></span><br/><br/><span data-ttu-id="c4387-166">**licençasActivar**</span><span class="sxs-lookup"><span data-stu-id="c4387-166">**licensesActive**</span></span><br/><span data-ttu-id="c4387-167">**licençasQualizado**</span><span class="sxs-lookup"><span data-stu-id="c4387-167">**licensesQualified**</span></span> | <span data-ttu-id="c4387-168">Não</span><span class="sxs-lookup"><span data-stu-id="c4387-168">No</span></span> |
| <span data-ttu-id="c4387-169">processadoDadade tempo</span><span class="sxs-lookup"><span data-stu-id="c4387-169">processedDateTime</span></span> | <span data-ttu-id="c4387-170">DateTime</span><span class="sxs-lookup"><span data-stu-id="c4387-170">DateTime</span></span> | <span data-ttu-id="c4387-171">Pode-se especificar a data a partir da qual os dados de utilização foram tratados.</span><span class="sxs-lookup"><span data-stu-id="c4387-171">One can specify the date from which usage data was processed.</span></span> <span data-ttu-id="c4387-172">Incumprimentos até à data mais recente quando os dados foram tratados</span><span class="sxs-lookup"><span data-stu-id="c4387-172">Defaults to the latest date when the data was processed</span></span> | <span data-ttu-id="c4387-173">Não</span><span class="sxs-lookup"><span data-stu-id="c4387-173">No</span></span> |

### <a name="request-example"></a><span data-ttu-id="c4387-174">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c4387-174">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/usage/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="c4387-175">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c4387-175">REST response</span></span>

<span data-ttu-id="c4387-176">Se for bem sucedido, o organismo de resposta contém os seguintes campos que contêm dados sobre a utilização das licenças.</span><span class="sxs-lookup"><span data-stu-id="c4387-176">If successful, the response body contains the following fields containing data about licenses usage.</span></span>

| <span data-ttu-id="c4387-177">Campo</span><span class="sxs-lookup"><span data-stu-id="c4387-177">Field</span></span>             | <span data-ttu-id="c4387-178">Tipo</span><span class="sxs-lookup"><span data-stu-id="c4387-178">Type</span></span>     | <span data-ttu-id="c4387-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4387-179">Description</span></span>                                   |
|-------------------|----------|-----------------------------------------------|
| <span data-ttu-id="c4387-180">código de carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="c4387-180">workloadCode</span></span>      | <span data-ttu-id="c4387-181">string</span><span class="sxs-lookup"><span data-stu-id="c4387-181">string</span></span>   | <span data-ttu-id="c4387-182">Código de carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="c4387-182">Workload code</span></span>                                 |
| <span data-ttu-id="c4387-183">carga de trabalhoName</span><span class="sxs-lookup"><span data-stu-id="c4387-183">workloadName</span></span>      | <span data-ttu-id="c4387-184">string</span><span class="sxs-lookup"><span data-stu-id="c4387-184">string</span></span>   | <span data-ttu-id="c4387-185">Nome da carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="c4387-185">Workload name</span></span>                                 |
| <span data-ttu-id="c4387-186">serviceCode</span><span class="sxs-lookup"><span data-stu-id="c4387-186">serviceCode</span></span>       | <span data-ttu-id="c4387-187">string</span><span class="sxs-lookup"><span data-stu-id="c4387-187">string</span></span>   | <span data-ttu-id="c4387-188">Código de serviço</span><span class="sxs-lookup"><span data-stu-id="c4387-188">Service code</span></span>                                  |
| <span data-ttu-id="c4387-189">nome de serviço</span><span class="sxs-lookup"><span data-stu-id="c4387-189">serviceName</span></span>       | <span data-ttu-id="c4387-190">string</span><span class="sxs-lookup"><span data-stu-id="c4387-190">string</span></span>   | <span data-ttu-id="c4387-191">Nome do serviço</span><span class="sxs-lookup"><span data-stu-id="c4387-191">Service name</span></span>                                  |
| <span data-ttu-id="c4387-192">canal</span><span class="sxs-lookup"><span data-stu-id="c4387-192">channel</span></span>           | <span data-ttu-id="c4387-193">string</span><span class="sxs-lookup"><span data-stu-id="c4387-193">string</span></span>   | <span data-ttu-id="c4387-194">Nome do canal, revendedor</span><span class="sxs-lookup"><span data-stu-id="c4387-194">Channel name, reseller</span></span>                        |
| <span data-ttu-id="c4387-195">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="c4387-195">customerTenantId</span></span>  | <span data-ttu-id="c4387-196">string</span><span class="sxs-lookup"><span data-stu-id="c4387-196">string</span></span>   | <span data-ttu-id="c4387-197">Identificador único para o cliente</span><span class="sxs-lookup"><span data-stu-id="c4387-197">Unique identifier for the customer</span></span>            |
| <span data-ttu-id="c4387-198">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="c4387-198">customerName</span></span>      | <span data-ttu-id="c4387-199">string</span><span class="sxs-lookup"><span data-stu-id="c4387-199">string</span></span>   | <span data-ttu-id="c4387-200">Nome do cliente</span><span class="sxs-lookup"><span data-stu-id="c4387-200">Customer name</span></span>                                 |
| <span data-ttu-id="c4387-201">productId</span><span class="sxs-lookup"><span data-stu-id="c4387-201">productId</span></span>         | <span data-ttu-id="c4387-202">string</span><span class="sxs-lookup"><span data-stu-id="c4387-202">string</span></span>   | <span data-ttu-id="c4387-203">Identificador único para o produto</span><span class="sxs-lookup"><span data-stu-id="c4387-203">Unique identifier for the product</span></span>             |
| <span data-ttu-id="c4387-204">produtoName</span><span class="sxs-lookup"><span data-stu-id="c4387-204">productName</span></span>       | <span data-ttu-id="c4387-205">string</span><span class="sxs-lookup"><span data-stu-id="c4387-205">string</span></span>   | <span data-ttu-id="c4387-206">Nome do produto</span><span class="sxs-lookup"><span data-stu-id="c4387-206">Product name</span></span>                                  |
| <span data-ttu-id="c4387-207">licençasActivar</span><span class="sxs-lookup"><span data-stu-id="c4387-207">licensesActive</span></span>    | <span data-ttu-id="c4387-208">long</span><span class="sxs-lookup"><span data-stu-id="c4387-208">long</span></span>     | <span data-ttu-id="c4387-209">Número de licenças ativas por carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="c4387-209">Number of active licenses per workload</span></span>        |
| <span data-ttu-id="c4387-210">licençasQualizado</span><span class="sxs-lookup"><span data-stu-id="c4387-210">licensesQualified</span></span> | <span data-ttu-id="c4387-211">long</span><span class="sxs-lookup"><span data-stu-id="c4387-211">long</span></span>     | <span data-ttu-id="c4387-212">Número de licenças qualificadas para a carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="c4387-212">Number of qualified licenses for the workload</span></span> |
| <span data-ttu-id="c4387-213">processadoDadade tempo</span><span class="sxs-lookup"><span data-stu-id="c4387-213">processedDateTime</span></span> | <span data-ttu-id="c4387-214">DateTime</span><span class="sxs-lookup"><span data-stu-id="c4387-214">DateTime</span></span> | <span data-ttu-id="c4387-215">Data em que os dados foram processados pela última vez</span><span class="sxs-lookup"><span data-stu-id="c4387-215">Date when the data was last processed</span></span>         |

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c4387-216">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c4387-216">Response success and error codes</span></span>

<span data-ttu-id="c4387-217">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c4387-217">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c4387-218">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c4387-218">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c4387-219">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c4387-219">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c4387-220">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="c4387-220">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 487
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CV: f0trvmq8mEScHcFS.0
MS-ServerId: 4
Date: Wed, 24 Oct 2018 22:37:18 GMT

{
"Value": [
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "workloadCode": "SPO",
      "workloadName": "SharePoint",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "6FD2C87F-B296-42F0-B197-1E91E994B900",
      "productName": "OFFICE 365 ENTERPRISE E3",
      "licenseActive": 0,
      "licensesQualified": 1
    },
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "workloadCode": "EXO",
      "workloadName": "Exchange",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "45A2423B-E884-448D-A831-D9E139C52D2F",
      "productName": "EXCHANGE ONLINE PROTECTION",
      "licenseActive": 0,
      "licensesQualified": 1
    }
}
```
