---
title: Obter informações de implementação de licenças
description: Como obter informações de implantação para licenças office e Dynamics.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ef0e5d73d34bc51e4cc58143db6c9fc49cb58fcb
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769434"
---
# <a name="get-licenses-deployment-information"></a><span data-ttu-id="4c1cd-103">Obter informações de implementação de licenças</span><span class="sxs-lookup"><span data-stu-id="4c1cd-103">Get licenses deployment information</span></span>

<span data-ttu-id="4c1cd-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-104">**Applies To**</span></span>

- <span data-ttu-id="4c1cd-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="4c1cd-105">Partner Center</span></span>

<span data-ttu-id="4c1cd-106">Como obter informações de implantação para licenças office e Dynamics.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-106">How to get deployment information for Office and Dynamics licenses.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4c1cd-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4c1cd-107">Prerequisites</span></span>

<span data-ttu-id="4c1cd-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4c1cd-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4c1cd-109">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="4c1cd-110">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="4c1cd-110">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4c1cd-111">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c1cd-111">Request syntax</span></span>

| <span data-ttu-id="4c1cd-112">Método</span><span class="sxs-lookup"><span data-stu-id="4c1cd-112">Method</span></span>  | <span data-ttu-id="4c1cd-113">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="4c1cd-113">Request URI</span></span>                                                                                     |
|---------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4c1cd-114">**Obter**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-114">**GET**</span></span> | <span data-ttu-id="4c1cd-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/deployment/license/ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4c1cd-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/deployment/license/ HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4c1cd-116">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="4c1cd-116">Request headers</span></span>

<span data-ttu-id="4c1cd-117">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4c1cd-117">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="uri-parameters"></a><span data-ttu-id="4c1cd-118">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="4c1cd-118">URI parameters</span></span>

| <span data-ttu-id="4c1cd-119">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4c1cd-119">Parameter</span></span>         | <span data-ttu-id="4c1cd-120">Tipo</span><span class="sxs-lookup"><span data-stu-id="4c1cd-120">Type</span></span>     | <span data-ttu-id="4c1cd-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c1cd-121">Description</span></span> | <span data-ttu-id="4c1cd-122">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="4c1cd-122">Required</span></span> |
|-------------------|----------|-------------|----------|
| <span data-ttu-id="4c1cd-123">top</span><span class="sxs-lookup"><span data-stu-id="4c1cd-123">top</span></span>               | <span data-ttu-id="4c1cd-124">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-124">string</span></span>   | <span data-ttu-id="4c1cd-125">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-125">The number of rows of data to return in the request.</span></span> <span data-ttu-id="4c1cd-126">O valor máximo e o valor predefinido se não especificado for 10000.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-126">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="4c1cd-127">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-127">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> | <span data-ttu-id="4c1cd-128">Não</span><span class="sxs-lookup"><span data-stu-id="4c1cd-128">No</span></span> |
| <span data-ttu-id="4c1cd-129">saltar</span><span class="sxs-lookup"><span data-stu-id="4c1cd-129">skip</span></span>              | <span data-ttu-id="4c1cd-130">int</span><span class="sxs-lookup"><span data-stu-id="4c1cd-130">int</span></span>      | <span data-ttu-id="4c1cd-131">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-131">The number of rows to skip in the query.</span></span> <span data-ttu-id="4c1cd-132">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-132">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="4c1cd-133">Por exemplo, top=10000 e skip=0 recupera as primeiras 10000 linhas de dados, top=10000 e skip=10000 recupera as próximas 10000 linhas de dados, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-133">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> | <span data-ttu-id="4c1cd-134">Não</span><span class="sxs-lookup"><span data-stu-id="4c1cd-134">No</span></span> |
| <span data-ttu-id="4c1cd-135">filter</span><span class="sxs-lookup"><span data-stu-id="4c1cd-135">filter</span></span>            | <span data-ttu-id="4c1cd-136">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-136">string</span></span>   | <span data-ttu-id="4c1cd-137">O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-137">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="4c1cd-138">Cada declaração contém um campo e valor que estão associados aos `eq` `ne` ou operadores, e as declarações podem ser combinadas usando `and` ou `or` .</span><span class="sxs-lookup"><span data-stu-id="4c1cd-138">Each statement contains a field and value that are associated with the `eq` or `ne` operators, and statements can be combined using `and` or `or`.</span></span> <span data-ttu-id="4c1cd-139">Aqui estão alguns parâmetros *de filtragem* de exemplo:</span><span class="sxs-lookup"><span data-stu-id="4c1cd-139">Here are some example *filter* parameters:</span></span><br/><br/> <span data-ttu-id="4c1cd-140">*filter=serviceCode eq 'O365'*</span><span class="sxs-lookup"><span data-stu-id="4c1cd-140">*filter=serviceCode eq 'O365'*</span></span><br/> <span data-ttu-id="4c1cd-141">*filter=serviceCode eq 'O365'* ou *(canal eq 'Revendedor'*)</span><span class="sxs-lookup"><span data-stu-id="4c1cd-141">*filter=serviceCode eq 'O365'* or (*channel eq 'Reseller'*)</span></span><br/><br/> <span data-ttu-id="4c1cd-142">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="4c1cd-142">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="4c1cd-143">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-143">**serviceCode**</span></span><br/><span data-ttu-id="4c1cd-144">**nome de serviço**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-144">**serviceName**</span></span><br/><span data-ttu-id="4c1cd-145">**canal**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-145">**channel**</span></span><br/><span data-ttu-id="4c1cd-146">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-146">**customerTenantId**</span></span><br/><span data-ttu-id="4c1cd-147">**nome do cliente**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-147">**customerName**</span></span><br/><span data-ttu-id="4c1cd-148">**productId**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-148">**productId**</span></span><br/><span data-ttu-id="4c1cd-149">**produtoName**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-149">**productName**</span></span>  | <span data-ttu-id="4c1cd-150">Não</span><span class="sxs-lookup"><span data-stu-id="4c1cd-150">No</span></span> |
| <span data-ttu-id="4c1cd-151">groupby</span><span class="sxs-lookup"><span data-stu-id="4c1cd-151">groupby</span></span>           | <span data-ttu-id="4c1cd-152">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-152">string</span></span>   | <span data-ttu-id="4c1cd-153">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-153">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="4c1cd-154">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="4c1cd-154">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="4c1cd-155">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-155">**serviceCode**</span></span><br/><span data-ttu-id="4c1cd-156">**nome de serviço**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-156">**serviceName**</span></span><br/><span data-ttu-id="4c1cd-157">**canal**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-157">**channel**</span></span><br/><span data-ttu-id="4c1cd-158">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-158">**customerTenantId**</span></span><br/><span data-ttu-id="4c1cd-159">**nome do cliente**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-159">**customerName**</span></span><br/><span data-ttu-id="4c1cd-160">**productId**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-160">**productId**</span></span><br/><span data-ttu-id="4c1cd-161">**produtoName**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-161">**productName**</span></span><br/><br/> <span data-ttu-id="4c1cd-162">As linhas de dados devolvidas conterão os campos especificados no parâmetro *groupby,* bem como os seguintes:</span><span class="sxs-lookup"><span data-stu-id="4c1cd-162">The returned data rows will contain the fields specified in the *groupby* parameter as well as the following:</span></span><br/><br/><span data-ttu-id="4c1cd-163">**licençasDeployed**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-163">**licensesDeployed**</span></span><br/><span data-ttu-id="4c1cd-164">**licençasSold**</span><span class="sxs-lookup"><span data-stu-id="4c1cd-164">**licensesSold**</span></span>  | <span data-ttu-id="4c1cd-165">Não</span><span class="sxs-lookup"><span data-stu-id="4c1cd-165">No</span></span> |
| <span data-ttu-id="4c1cd-166">processadoDadade tempo</span><span class="sxs-lookup"><span data-stu-id="4c1cd-166">processedDateTime</span></span> | <span data-ttu-id="4c1cd-167">DateTime</span><span class="sxs-lookup"><span data-stu-id="4c1cd-167">DateTime</span></span> | <span data-ttu-id="4c1cd-168">Pode-se especificar a data a partir da qual os dados de utilização foram tratados.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-168">One can specify the date from which usage data was processed.</span></span> <span data-ttu-id="4c1cd-169">Incumprimentos até à data mais recente quando os dados foram tratados</span><span class="sxs-lookup"><span data-stu-id="4c1cd-169">Defaults to the latest date when the data was processed</span></span> | <span data-ttu-id="4c1cd-170">Não</span><span class="sxs-lookup"><span data-stu-id="4c1cd-170">No</span></span> |

### <a name="request-example"></a><span data-ttu-id="4c1cd-171">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="4c1cd-171">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/deployment/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="4c1cd-172">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="4c1cd-172">REST response</span></span>

<span data-ttu-id="4c1cd-173">Se for bem sucedido, o organismo de resposta contém os seguintes campos contendo dados sobre as licenças implementadas.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-173">If successful, the response body contains the following fields containing data about the licenses deployed.</span></span>

| <span data-ttu-id="4c1cd-174">Campo</span><span class="sxs-lookup"><span data-stu-id="4c1cd-174">Field</span></span>             | <span data-ttu-id="4c1cd-175">Tipo</span><span class="sxs-lookup"><span data-stu-id="4c1cd-175">Type</span></span>     | <span data-ttu-id="4c1cd-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c1cd-176">Description</span></span>                           |
|-------------------|----------|---------------------------------------|
| <span data-ttu-id="4c1cd-177">serviceCode</span><span class="sxs-lookup"><span data-stu-id="4c1cd-177">serviceCode</span></span>       | <span data-ttu-id="4c1cd-178">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-178">string</span></span>   | <span data-ttu-id="4c1cd-179">Código de serviço</span><span class="sxs-lookup"><span data-stu-id="4c1cd-179">Service code</span></span>                          |
| <span data-ttu-id="4c1cd-180">nome de serviço</span><span class="sxs-lookup"><span data-stu-id="4c1cd-180">serviceName</span></span>       | <span data-ttu-id="4c1cd-181">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-181">string</span></span>   | <span data-ttu-id="4c1cd-182">Nome do serviço</span><span class="sxs-lookup"><span data-stu-id="4c1cd-182">Service name</span></span>                          |
| <span data-ttu-id="4c1cd-183">canal</span><span class="sxs-lookup"><span data-stu-id="4c1cd-183">channel</span></span>           | <span data-ttu-id="4c1cd-184">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-184">string</span></span>   | <span data-ttu-id="4c1cd-185">Nome do canal, revendedor</span><span class="sxs-lookup"><span data-stu-id="4c1cd-185">Channel name, reseller</span></span>                |
| <span data-ttu-id="4c1cd-186">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="4c1cd-186">customerTenantId</span></span>  | <span data-ttu-id="4c1cd-187">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-187">string</span></span>   | <span data-ttu-id="4c1cd-188">Identificador único para o cliente</span><span class="sxs-lookup"><span data-stu-id="4c1cd-188">Unique identifier for the customer</span></span>    |
| <span data-ttu-id="4c1cd-189">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="4c1cd-189">customerName</span></span>      | <span data-ttu-id="4c1cd-190">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-190">string</span></span>   | <span data-ttu-id="4c1cd-191">Nome do cliente</span><span class="sxs-lookup"><span data-stu-id="4c1cd-191">Customer name</span></span>                         |
| <span data-ttu-id="4c1cd-192">productId</span><span class="sxs-lookup"><span data-stu-id="4c1cd-192">productId</span></span>         | <span data-ttu-id="4c1cd-193">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-193">string</span></span>   | <span data-ttu-id="4c1cd-194">Identificador único para o produto</span><span class="sxs-lookup"><span data-stu-id="4c1cd-194">Unique identifier for the product</span></span>     |
| <span data-ttu-id="4c1cd-195">produtoName</span><span class="sxs-lookup"><span data-stu-id="4c1cd-195">productName</span></span>       | <span data-ttu-id="4c1cd-196">string</span><span class="sxs-lookup"><span data-stu-id="4c1cd-196">string</span></span>   | <span data-ttu-id="4c1cd-197">Nome do produto</span><span class="sxs-lookup"><span data-stu-id="4c1cd-197">Product name</span></span>                          |
| <span data-ttu-id="4c1cd-198">licençasDeployed</span><span class="sxs-lookup"><span data-stu-id="4c1cd-198">licensesDeployed</span></span>  | <span data-ttu-id="4c1cd-199">long</span><span class="sxs-lookup"><span data-stu-id="4c1cd-199">long</span></span>     | <span data-ttu-id="4c1cd-200">Número de licenças implantadas</span><span class="sxs-lookup"><span data-stu-id="4c1cd-200">Number of licenses deployed</span></span>           |
| <span data-ttu-id="4c1cd-201">licençasSold</span><span class="sxs-lookup"><span data-stu-id="4c1cd-201">licensesSold</span></span>      | <span data-ttu-id="4c1cd-202">long</span><span class="sxs-lookup"><span data-stu-id="4c1cd-202">long</span></span>     | <span data-ttu-id="4c1cd-203">Número de licenças vendidas</span><span class="sxs-lookup"><span data-stu-id="4c1cd-203">Number of licenses sold</span></span>               |
| <span data-ttu-id="4c1cd-204">processadoDadade tempo</span><span class="sxs-lookup"><span data-stu-id="4c1cd-204">processedDateTime</span></span> | <span data-ttu-id="4c1cd-205">DateTime</span><span class="sxs-lookup"><span data-stu-id="4c1cd-205">DateTime</span></span> | <span data-ttu-id="4c1cd-206">Data em que os dados foram processados pela última vez</span><span class="sxs-lookup"><span data-stu-id="4c1cd-206">Date when the data was last processed</span></span> |

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4c1cd-207">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="4c1cd-207">Response success and error codes</span></span>

<span data-ttu-id="4c1cd-208">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-208">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4c1cd-209">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4c1cd-209">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4c1cd-210">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4c1cd-210">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4c1cd-211">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="4c1cd-211">Response example</span></span>

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
      "serviceCode": "crm",
      "serviceName": "Microsoft Dynamics",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "54B84594-9C77-4499-8D65-5E0D5F410E78",
      "productName": "DYNAMICS AX TASK",
      "licensesDeployed": 0,
      "licensesSold": 9
    },
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "D3B4FE1F-9992-4930-8ACB-CA6EC609365E",
      "productName": "DOMESTIC AND INTERNATIONAL CALLING PLAN",
      "licensesDeployed": 0,
      "licensesSold": 5
    }
],
  "@nextLink": null,
  "TotalCount": 2
}
```
