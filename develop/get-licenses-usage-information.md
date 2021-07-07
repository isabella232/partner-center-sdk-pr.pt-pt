---
title: Obter informações de utilização de licenças
description: Como obter informações de utilização de licenças ao nível da carga de trabalho para Office e Dinâmica.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ea3658089ce7eb5c1ad7cc65c3db34f9b6353cdd
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445985"
---
# <a name="get-licenses-usage-information"></a><span data-ttu-id="08918-103">Obter informações de utilização de licenças</span><span class="sxs-lookup"><span data-stu-id="08918-103">Get licenses usage information</span></span>

<span data-ttu-id="08918-104">Como obter informações de utilização de licenças ao nível da carga de trabalho para Office e Dinâmica.</span><span class="sxs-lookup"><span data-stu-id="08918-104">How to get licenses usage information at the workload level for Office and Dynamics.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08918-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="08918-105">Prerequisites</span></span>

<span data-ttu-id="08918-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="08918-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="08918-107">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="08918-107">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="08918-108">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="08918-108">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="08918-109">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="08918-109">Request syntax</span></span>

| <span data-ttu-id="08918-110">Método</span><span class="sxs-lookup"><span data-stu-id="08918-110">Method</span></span>  | <span data-ttu-id="08918-111">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="08918-111">Request URI</span></span>                                                                                |
|---------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="08918-112">**Obter**</span><span class="sxs-lookup"><span data-stu-id="08918-112">**GET**</span></span> | <span data-ttu-id="08918-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/usage/license/ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="08918-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/usage/license/ HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="08918-114">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="08918-114">Request headers</span></span>

<span data-ttu-id="08918-115">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="08918-115">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="uri-parameters"></a><span data-ttu-id="08918-116">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="08918-116">URI parameters</span></span>

| <span data-ttu-id="08918-117">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="08918-117">Parameter</span></span>         | <span data-ttu-id="08918-118">Tipo</span><span class="sxs-lookup"><span data-stu-id="08918-118">Type</span></span>     | <span data-ttu-id="08918-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="08918-119">Description</span></span> | <span data-ttu-id="08918-120">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="08918-120">Required</span></span> |
|-------------------|----------|-------------|----------|
| <span data-ttu-id="08918-121">top</span><span class="sxs-lookup"><span data-stu-id="08918-121">top</span></span>               | <span data-ttu-id="08918-122">string</span><span class="sxs-lookup"><span data-stu-id="08918-122">string</span></span>   | <span data-ttu-id="08918-123">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="08918-123">The number of rows of data to return in the request.</span></span> <span data-ttu-id="08918-124">O valor máximo e o valor predefinido se não especificado for 10000.</span><span class="sxs-lookup"><span data-stu-id="08918-124">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="08918-125">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="08918-125">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> | <span data-ttu-id="08918-126">No</span><span class="sxs-lookup"><span data-stu-id="08918-126">No</span></span> |
| <span data-ttu-id="08918-127">saltar</span><span class="sxs-lookup"><span data-stu-id="08918-127">skip</span></span>              | <span data-ttu-id="08918-128">int</span><span class="sxs-lookup"><span data-stu-id="08918-128">int</span></span>      | <span data-ttu-id="08918-129">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="08918-129">The number of rows to skip in the query.</span></span> <span data-ttu-id="08918-130">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="08918-130">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="08918-131">Por exemplo, top=10000 e skip=0 recupera as primeiras 10000 linhas de dados, top=10000 e skip=10000 recupera as próximas 10000 linhas de dados, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="08918-131">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> | <span data-ttu-id="08918-132">No</span><span class="sxs-lookup"><span data-stu-id="08918-132">No</span></span> |
| <span data-ttu-id="08918-133">filter</span><span class="sxs-lookup"><span data-stu-id="08918-133">filter</span></span>            | <span data-ttu-id="08918-134">string</span><span class="sxs-lookup"><span data-stu-id="08918-134">string</span></span>   | <span data-ttu-id="08918-135">O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="08918-135">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="08918-136">Cada declaração contém um campo e valor que estão associados aos **`eq`** **`ne`** ou operadores, e as declarações podem ser combinadas usando **`and`** ou **`or`** .</span><span class="sxs-lookup"><span data-stu-id="08918-136">Each statement contains a field and value that are associated with the **`eq`** or **`ne`** operators, and statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="08918-137">Aqui estão alguns parâmetros *de filtragem* de exemplo:</span><span class="sxs-lookup"><span data-stu-id="08918-137">Here are some example *filter* parameters:</span></span><br/><br/><span data-ttu-id="08918-138">*filter=workloadCode eq 'SFB'*</span><span class="sxs-lookup"><span data-stu-id="08918-138">*filter=workloadCode eq 'SFB'*</span></span><br/><br/><span data-ttu-id="08918-139">*filter=workloadCode eq 'SFB'* ou *(canal eq 'Revendedor'*)</span><span class="sxs-lookup"><span data-stu-id="08918-139">*filter=workloadCode eq 'SFB'* or (*channel eq 'Reseller'*)</span></span><br/><br/><span data-ttu-id="08918-140">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="08918-140">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="08918-141">**código de carga de trabalho**</span><span class="sxs-lookup"><span data-stu-id="08918-141">**workloadCode**</span></span><br/><span data-ttu-id="08918-142">**carga de trabalhoName**</span><span class="sxs-lookup"><span data-stu-id="08918-142">**workloadName**</span></span><br/><span data-ttu-id="08918-143">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="08918-143">**serviceCode**</span></span><br/><span data-ttu-id="08918-144">**nome de serviço**</span><span class="sxs-lookup"><span data-stu-id="08918-144">**serviceName**</span></span><br/><span data-ttu-id="08918-145">**canal**</span><span class="sxs-lookup"><span data-stu-id="08918-145">**channel**</span></span><br/><span data-ttu-id="08918-146">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="08918-146">**customerTenantId**</span></span><br/><span data-ttu-id="08918-147">**nome do cliente**</span><span class="sxs-lookup"><span data-stu-id="08918-147">**customerName**</span></span><br/><span data-ttu-id="08918-148">**productId**</span><span class="sxs-lookup"><span data-stu-id="08918-148">**productId**</span></span><br/><span data-ttu-id="08918-149">**produtoName**</span><span class="sxs-lookup"><span data-stu-id="08918-149">**productName**</span></span> | <span data-ttu-id="08918-150">No</span><span class="sxs-lookup"><span data-stu-id="08918-150">No</span></span> |
| <span data-ttu-id="08918-151">groupby</span><span class="sxs-lookup"><span data-stu-id="08918-151">groupby</span></span>           | <span data-ttu-id="08918-152">string</span><span class="sxs-lookup"><span data-stu-id="08918-152">string</span></span>   | <span data-ttu-id="08918-153">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="08918-153">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="08918-154">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="08918-154">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="08918-155">**código de carga de trabalho**</span><span class="sxs-lookup"><span data-stu-id="08918-155">**workloadCode**</span></span><br/><span data-ttu-id="08918-156">**carga de trabalhoName**</span><span class="sxs-lookup"><span data-stu-id="08918-156">**workloadName**</span></span><br/><span data-ttu-id="08918-157">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="08918-157">**serviceCode**</span></span><br/><span data-ttu-id="08918-158">**nome de serviço**</span><span class="sxs-lookup"><span data-stu-id="08918-158">**serviceName**</span></span><br/><span data-ttu-id="08918-159">**channelcustomerTenantId**</span><span class="sxs-lookup"><span data-stu-id="08918-159">**channelcustomerTenantId**</span></span><br/><span data-ttu-id="08918-160">**nome do cliente**</span><span class="sxs-lookup"><span data-stu-id="08918-160">**customerName**</span></span><br/><span data-ttu-id="08918-161">**productId**</span><span class="sxs-lookup"><span data-stu-id="08918-161">**productId**</span></span><br/><span data-ttu-id="08918-162">**produtoName**</span><span class="sxs-lookup"><span data-stu-id="08918-162">**productName**</span></span><br/><br/><span data-ttu-id="08918-163">As linhas de dados devolvidas conterão os campos especificados no parâmetro *groupby* e os seguintes:</span><span class="sxs-lookup"><span data-stu-id="08918-163">The returned data rows will contain the fields specified in the *groupby* parameter and the following:</span></span><br/><br/><span data-ttu-id="08918-164">**licençasActivar**</span><span class="sxs-lookup"><span data-stu-id="08918-164">**licensesActive**</span></span><br/><span data-ttu-id="08918-165">**licençasQualizado**</span><span class="sxs-lookup"><span data-stu-id="08918-165">**licensesQualified**</span></span> | <span data-ttu-id="08918-166">No</span><span class="sxs-lookup"><span data-stu-id="08918-166">No</span></span> |
| <span data-ttu-id="08918-167">processadoDadade tempo</span><span class="sxs-lookup"><span data-stu-id="08918-167">processedDateTime</span></span> | <span data-ttu-id="08918-168">DateTime</span><span class="sxs-lookup"><span data-stu-id="08918-168">DateTime</span></span> | <span data-ttu-id="08918-169">Pode-se especificar a data a partir da qual os dados de utilização foram tratados.</span><span class="sxs-lookup"><span data-stu-id="08918-169">One can specify the date from which usage data was processed.</span></span> <span data-ttu-id="08918-170">Incumprimentos até à data mais recente quando os dados foram tratados</span><span class="sxs-lookup"><span data-stu-id="08918-170">Defaults to the latest date when the data was processed</span></span> | <span data-ttu-id="08918-171">No</span><span class="sxs-lookup"><span data-stu-id="08918-171">No</span></span> |

### <a name="request-example"></a><span data-ttu-id="08918-172">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="08918-172">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/usage/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="08918-173">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="08918-173">REST response</span></span>

<span data-ttu-id="08918-174">Se for bem sucedido, o organismo de resposta contém os seguintes campos que contêm dados sobre a utilização das licenças.</span><span class="sxs-lookup"><span data-stu-id="08918-174">If successful, the response body contains the following fields containing data about licenses usage.</span></span>

| <span data-ttu-id="08918-175">Campo</span><span class="sxs-lookup"><span data-stu-id="08918-175">Field</span></span>             | <span data-ttu-id="08918-176">Tipo</span><span class="sxs-lookup"><span data-stu-id="08918-176">Type</span></span>     | <span data-ttu-id="08918-177">Description</span><span class="sxs-lookup"><span data-stu-id="08918-177">Description</span></span>                                   |
|-------------------|----------|-----------------------------------------------|
| <span data-ttu-id="08918-178">código de carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="08918-178">workloadCode</span></span>      | <span data-ttu-id="08918-179">string</span><span class="sxs-lookup"><span data-stu-id="08918-179">string</span></span>   | <span data-ttu-id="08918-180">Código de carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="08918-180">Workload code</span></span>                                 |
| <span data-ttu-id="08918-181">carga de trabalhoName</span><span class="sxs-lookup"><span data-stu-id="08918-181">workloadName</span></span>      | <span data-ttu-id="08918-182">string</span><span class="sxs-lookup"><span data-stu-id="08918-182">string</span></span>   | <span data-ttu-id="08918-183">Nome da carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="08918-183">Workload name</span></span>                                 |
| <span data-ttu-id="08918-184">serviceCode</span><span class="sxs-lookup"><span data-stu-id="08918-184">serviceCode</span></span>       | <span data-ttu-id="08918-185">string</span><span class="sxs-lookup"><span data-stu-id="08918-185">string</span></span>   | <span data-ttu-id="08918-186">Código de serviço</span><span class="sxs-lookup"><span data-stu-id="08918-186">Service code</span></span>                                  |
| <span data-ttu-id="08918-187">nome de serviço</span><span class="sxs-lookup"><span data-stu-id="08918-187">serviceName</span></span>       | <span data-ttu-id="08918-188">string</span><span class="sxs-lookup"><span data-stu-id="08918-188">string</span></span>   | <span data-ttu-id="08918-189">Nome do serviço</span><span class="sxs-lookup"><span data-stu-id="08918-189">Service name</span></span>                                  |
| <span data-ttu-id="08918-190">canal</span><span class="sxs-lookup"><span data-stu-id="08918-190">channel</span></span>           | <span data-ttu-id="08918-191">string</span><span class="sxs-lookup"><span data-stu-id="08918-191">string</span></span>   | <span data-ttu-id="08918-192">Nome do canal, revendedor</span><span class="sxs-lookup"><span data-stu-id="08918-192">Channel name, reseller</span></span>                        |
| <span data-ttu-id="08918-193">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="08918-193">customerTenantId</span></span>  | <span data-ttu-id="08918-194">string</span><span class="sxs-lookup"><span data-stu-id="08918-194">string</span></span>   | <span data-ttu-id="08918-195">Identificador único para o cliente</span><span class="sxs-lookup"><span data-stu-id="08918-195">Unique identifier for the customer</span></span>            |
| <span data-ttu-id="08918-196">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="08918-196">customerName</span></span>      | <span data-ttu-id="08918-197">string</span><span class="sxs-lookup"><span data-stu-id="08918-197">string</span></span>   | <span data-ttu-id="08918-198">Nome do cliente</span><span class="sxs-lookup"><span data-stu-id="08918-198">Customer name</span></span>                                 |
| <span data-ttu-id="08918-199">productId</span><span class="sxs-lookup"><span data-stu-id="08918-199">productId</span></span>         | <span data-ttu-id="08918-200">string</span><span class="sxs-lookup"><span data-stu-id="08918-200">string</span></span>   | <span data-ttu-id="08918-201">Identificador único para o produto</span><span class="sxs-lookup"><span data-stu-id="08918-201">Unique identifier for the product</span></span>             |
| <span data-ttu-id="08918-202">produtoName</span><span class="sxs-lookup"><span data-stu-id="08918-202">productName</span></span>       | <span data-ttu-id="08918-203">string</span><span class="sxs-lookup"><span data-stu-id="08918-203">string</span></span>   | <span data-ttu-id="08918-204">Nome do produto</span><span class="sxs-lookup"><span data-stu-id="08918-204">Product name</span></span>                                  |
| <span data-ttu-id="08918-205">licençasActivar</span><span class="sxs-lookup"><span data-stu-id="08918-205">licensesActive</span></span>    | <span data-ttu-id="08918-206">long</span><span class="sxs-lookup"><span data-stu-id="08918-206">long</span></span>     | <span data-ttu-id="08918-207">Número de licenças ativas por carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="08918-207">Number of active licenses per workload</span></span>        |
| <span data-ttu-id="08918-208">licençasQualizado</span><span class="sxs-lookup"><span data-stu-id="08918-208">licensesQualified</span></span> | <span data-ttu-id="08918-209">long</span><span class="sxs-lookup"><span data-stu-id="08918-209">long</span></span>     | <span data-ttu-id="08918-210">Número de licenças qualificadas para a carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="08918-210">Number of qualified licenses for the workload</span></span> |
| <span data-ttu-id="08918-211">processadoDadade tempo</span><span class="sxs-lookup"><span data-stu-id="08918-211">processedDateTime</span></span> | <span data-ttu-id="08918-212">DateTime</span><span class="sxs-lookup"><span data-stu-id="08918-212">DateTime</span></span> | <span data-ttu-id="08918-213">Data em que os dados foram processados pela última vez</span><span class="sxs-lookup"><span data-stu-id="08918-213">Date when the data was last processed</span></span>         |

### <a name="response-success-and-error-codes"></a><span data-ttu-id="08918-214">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="08918-214">Response success and error codes</span></span>

<span data-ttu-id="08918-215">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="08918-215">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="08918-216">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="08918-216">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="08918-217">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="08918-217">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="08918-218">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="08918-218">Response example</span></span>

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
