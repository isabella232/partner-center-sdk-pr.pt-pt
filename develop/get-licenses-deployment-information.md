---
title: Obter informações de implementação de licenças
description: Como obter informações de implementação para licenças Office e Dinâmica.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9eb0dc655affb2216b11635e58e00ed6464d6792
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445668"
---
# <a name="get-licenses-deployment-information"></a><span data-ttu-id="37694-103">Obter informações de implementação de licenças</span><span class="sxs-lookup"><span data-stu-id="37694-103">Get licenses deployment information</span></span>

<span data-ttu-id="37694-104">Como obter informações de implementação para licenças Office e Dinâmica.</span><span class="sxs-lookup"><span data-stu-id="37694-104">How to get deployment information for Office and Dynamics licenses.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="37694-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="37694-105">Prerequisites</span></span>

<span data-ttu-id="37694-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="37694-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="37694-107">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="37694-107">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="37694-108">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="37694-108">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="37694-109">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="37694-109">Request syntax</span></span>

| <span data-ttu-id="37694-110">Método</span><span class="sxs-lookup"><span data-stu-id="37694-110">Method</span></span>  | <span data-ttu-id="37694-111">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="37694-111">Request URI</span></span>                                                                                     |
|---------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="37694-112">**Obter**</span><span class="sxs-lookup"><span data-stu-id="37694-112">**GET**</span></span> | <span data-ttu-id="37694-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/deployment/license/ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="37694-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/deployment/license/ HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="37694-114">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="37694-114">Request headers</span></span>

<span data-ttu-id="37694-115">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="37694-115">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="uri-parameters"></a><span data-ttu-id="37694-116">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="37694-116">URI parameters</span></span>

| <span data-ttu-id="37694-117">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="37694-117">Parameter</span></span>         | <span data-ttu-id="37694-118">Tipo</span><span class="sxs-lookup"><span data-stu-id="37694-118">Type</span></span>     | <span data-ttu-id="37694-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="37694-119">Description</span></span> | <span data-ttu-id="37694-120">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="37694-120">Required</span></span> |
|-------------------|----------|-------------|----------|
| <span data-ttu-id="37694-121">top</span><span class="sxs-lookup"><span data-stu-id="37694-121">top</span></span>               | <span data-ttu-id="37694-122">string</span><span class="sxs-lookup"><span data-stu-id="37694-122">string</span></span>   | <span data-ttu-id="37694-123">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="37694-123">The number of rows of data to return in the request.</span></span> <span data-ttu-id="37694-124">O valor máximo e o valor predefinido se não especificado for 10000.</span><span class="sxs-lookup"><span data-stu-id="37694-124">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="37694-125">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="37694-125">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> | <span data-ttu-id="37694-126">No</span><span class="sxs-lookup"><span data-stu-id="37694-126">No</span></span> |
| <span data-ttu-id="37694-127">saltar</span><span class="sxs-lookup"><span data-stu-id="37694-127">skip</span></span>              | <span data-ttu-id="37694-128">int</span><span class="sxs-lookup"><span data-stu-id="37694-128">int</span></span>      | <span data-ttu-id="37694-129">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="37694-129">The number of rows to skip in the query.</span></span> <span data-ttu-id="37694-130">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="37694-130">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="37694-131">Por exemplo, top=10000 e skip=0 recupera as primeiras 10000 linhas de dados, top=10000 e skip=10000 recupera as próximas 10000 linhas de dados, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="37694-131">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> | <span data-ttu-id="37694-132">No</span><span class="sxs-lookup"><span data-stu-id="37694-132">No</span></span> |
| <span data-ttu-id="37694-133">filter</span><span class="sxs-lookup"><span data-stu-id="37694-133">filter</span></span>            | <span data-ttu-id="37694-134">string</span><span class="sxs-lookup"><span data-stu-id="37694-134">string</span></span>   | <span data-ttu-id="37694-135">O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="37694-135">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="37694-136">Cada declaração contém um campo e valor que estão associados aos `eq` `ne` ou operadores, e as declarações podem ser combinadas usando `and` ou `or` .</span><span class="sxs-lookup"><span data-stu-id="37694-136">Each statement contains a field and value that are associated with the `eq` or `ne` operators, and statements can be combined using `and` or `or`.</span></span> <span data-ttu-id="37694-137">Aqui estão alguns parâmetros *de filtragem* de exemplo:</span><span class="sxs-lookup"><span data-stu-id="37694-137">Here are some example *filter* parameters:</span></span><br/><br/> <span data-ttu-id="37694-138">*filter=serviceCode eq 'O365'*</span><span class="sxs-lookup"><span data-stu-id="37694-138">*filter=serviceCode eq 'O365'*</span></span><br/> <span data-ttu-id="37694-139">*filter=serviceCode eq 'O365'* ou *(canal eq 'Revendedor'*)</span><span class="sxs-lookup"><span data-stu-id="37694-139">*filter=serviceCode eq 'O365'* or (*channel eq 'Reseller'*)</span></span><br/><br/> <span data-ttu-id="37694-140">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="37694-140">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="37694-141">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="37694-141">**serviceCode**</span></span><br/><span data-ttu-id="37694-142">**nome de serviço**</span><span class="sxs-lookup"><span data-stu-id="37694-142">**serviceName**</span></span><br/><span data-ttu-id="37694-143">**canal**</span><span class="sxs-lookup"><span data-stu-id="37694-143">**channel**</span></span><br/><span data-ttu-id="37694-144">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="37694-144">**customerTenantId**</span></span><br/><span data-ttu-id="37694-145">**nome do cliente**</span><span class="sxs-lookup"><span data-stu-id="37694-145">**customerName**</span></span><br/><span data-ttu-id="37694-146">**productId**</span><span class="sxs-lookup"><span data-stu-id="37694-146">**productId**</span></span><br/><span data-ttu-id="37694-147">**produtoName**</span><span class="sxs-lookup"><span data-stu-id="37694-147">**productName**</span></span>  | <span data-ttu-id="37694-148">No</span><span class="sxs-lookup"><span data-stu-id="37694-148">No</span></span> |
| <span data-ttu-id="37694-149">groupby</span><span class="sxs-lookup"><span data-stu-id="37694-149">groupby</span></span>           | <span data-ttu-id="37694-150">string</span><span class="sxs-lookup"><span data-stu-id="37694-150">string</span></span>   | <span data-ttu-id="37694-151">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="37694-151">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="37694-152">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="37694-152">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="37694-153">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="37694-153">**serviceCode**</span></span><br/><span data-ttu-id="37694-154">**nome de serviço**</span><span class="sxs-lookup"><span data-stu-id="37694-154">**serviceName**</span></span><br/><span data-ttu-id="37694-155">**canal**</span><span class="sxs-lookup"><span data-stu-id="37694-155">**channel**</span></span><br/><span data-ttu-id="37694-156">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="37694-156">**customerTenantId**</span></span><br/><span data-ttu-id="37694-157">**nome do cliente**</span><span class="sxs-lookup"><span data-stu-id="37694-157">**customerName**</span></span><br/><span data-ttu-id="37694-158">**productId**</span><span class="sxs-lookup"><span data-stu-id="37694-158">**productId**</span></span><br/><span data-ttu-id="37694-159">**produtoName**</span><span class="sxs-lookup"><span data-stu-id="37694-159">**productName**</span></span><br/><br/> <span data-ttu-id="37694-160">As linhas de dados devolvidas conterão os campos especificados no parâmetro *groupby* e os seguintes:</span><span class="sxs-lookup"><span data-stu-id="37694-160">The returned data rows will contain the fields specified in the *groupby* parameter and the following:</span></span><br/><br/><span data-ttu-id="37694-161">**licençasDeployed**</span><span class="sxs-lookup"><span data-stu-id="37694-161">**licensesDeployed**</span></span><br/><span data-ttu-id="37694-162">**licençasSold**</span><span class="sxs-lookup"><span data-stu-id="37694-162">**licensesSold**</span></span>  | <span data-ttu-id="37694-163">No</span><span class="sxs-lookup"><span data-stu-id="37694-163">No</span></span> |
| <span data-ttu-id="37694-164">processadoDadade tempo</span><span class="sxs-lookup"><span data-stu-id="37694-164">processedDateTime</span></span> | <span data-ttu-id="37694-165">DateTime</span><span class="sxs-lookup"><span data-stu-id="37694-165">DateTime</span></span> | <span data-ttu-id="37694-166">Pode-se especificar a data a partir da qual os dados de utilização foram tratados.</span><span class="sxs-lookup"><span data-stu-id="37694-166">One can specify the date from which usage data was processed.</span></span> <span data-ttu-id="37694-167">Incumprimentos até à data mais recente quando os dados foram tratados</span><span class="sxs-lookup"><span data-stu-id="37694-167">Defaults to the latest date when the data was processed</span></span> | <span data-ttu-id="37694-168">No</span><span class="sxs-lookup"><span data-stu-id="37694-168">No</span></span> |

### <a name="request-example"></a><span data-ttu-id="37694-169">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="37694-169">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/deployment/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="37694-170">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="37694-170">REST response</span></span>

<span data-ttu-id="37694-171">Se for bem sucedido, o organismo de resposta contém os seguintes campos contendo dados sobre as licenças implementadas.</span><span class="sxs-lookup"><span data-stu-id="37694-171">If successful, the response body contains the following fields containing data about the licenses deployed.</span></span>

| <span data-ttu-id="37694-172">Campo</span><span class="sxs-lookup"><span data-stu-id="37694-172">Field</span></span>             | <span data-ttu-id="37694-173">Tipo</span><span class="sxs-lookup"><span data-stu-id="37694-173">Type</span></span>     | <span data-ttu-id="37694-174">Description</span><span class="sxs-lookup"><span data-stu-id="37694-174">Description</span></span>                           |
|-------------------|----------|---------------------------------------|
| <span data-ttu-id="37694-175">serviceCode</span><span class="sxs-lookup"><span data-stu-id="37694-175">serviceCode</span></span>       | <span data-ttu-id="37694-176">string</span><span class="sxs-lookup"><span data-stu-id="37694-176">string</span></span>   | <span data-ttu-id="37694-177">Código de serviço</span><span class="sxs-lookup"><span data-stu-id="37694-177">Service code</span></span>                          |
| <span data-ttu-id="37694-178">nome de serviço</span><span class="sxs-lookup"><span data-stu-id="37694-178">serviceName</span></span>       | <span data-ttu-id="37694-179">string</span><span class="sxs-lookup"><span data-stu-id="37694-179">string</span></span>   | <span data-ttu-id="37694-180">Nome do serviço</span><span class="sxs-lookup"><span data-stu-id="37694-180">Service name</span></span>                          |
| <span data-ttu-id="37694-181">canal</span><span class="sxs-lookup"><span data-stu-id="37694-181">channel</span></span>           | <span data-ttu-id="37694-182">string</span><span class="sxs-lookup"><span data-stu-id="37694-182">string</span></span>   | <span data-ttu-id="37694-183">Nome do canal, revendedor</span><span class="sxs-lookup"><span data-stu-id="37694-183">Channel name, reseller</span></span>                |
| <span data-ttu-id="37694-184">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="37694-184">customerTenantId</span></span>  | <span data-ttu-id="37694-185">string</span><span class="sxs-lookup"><span data-stu-id="37694-185">string</span></span>   | <span data-ttu-id="37694-186">Identificador único para o cliente</span><span class="sxs-lookup"><span data-stu-id="37694-186">Unique identifier for the customer</span></span>    |
| <span data-ttu-id="37694-187">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="37694-187">customerName</span></span>      | <span data-ttu-id="37694-188">string</span><span class="sxs-lookup"><span data-stu-id="37694-188">string</span></span>   | <span data-ttu-id="37694-189">Nome do cliente</span><span class="sxs-lookup"><span data-stu-id="37694-189">Customer name</span></span>                         |
| <span data-ttu-id="37694-190">productId</span><span class="sxs-lookup"><span data-stu-id="37694-190">productId</span></span>         | <span data-ttu-id="37694-191">string</span><span class="sxs-lookup"><span data-stu-id="37694-191">string</span></span>   | <span data-ttu-id="37694-192">Identificador único para o produto</span><span class="sxs-lookup"><span data-stu-id="37694-192">Unique identifier for the product</span></span>     |
| <span data-ttu-id="37694-193">produtoName</span><span class="sxs-lookup"><span data-stu-id="37694-193">productName</span></span>       | <span data-ttu-id="37694-194">string</span><span class="sxs-lookup"><span data-stu-id="37694-194">string</span></span>   | <span data-ttu-id="37694-195">Nome do produto</span><span class="sxs-lookup"><span data-stu-id="37694-195">Product name</span></span>                          |
| <span data-ttu-id="37694-196">licençasDeployed</span><span class="sxs-lookup"><span data-stu-id="37694-196">licensesDeployed</span></span>  | <span data-ttu-id="37694-197">long</span><span class="sxs-lookup"><span data-stu-id="37694-197">long</span></span>     | <span data-ttu-id="37694-198">Número de licenças implantadas</span><span class="sxs-lookup"><span data-stu-id="37694-198">Number of licenses deployed</span></span>           |
| <span data-ttu-id="37694-199">licençasSold</span><span class="sxs-lookup"><span data-stu-id="37694-199">licensesSold</span></span>      | <span data-ttu-id="37694-200">long</span><span class="sxs-lookup"><span data-stu-id="37694-200">long</span></span>     | <span data-ttu-id="37694-201">Número de licenças vendidas</span><span class="sxs-lookup"><span data-stu-id="37694-201">Number of licenses sold</span></span>               |
| <span data-ttu-id="37694-202">processadoDadade tempo</span><span class="sxs-lookup"><span data-stu-id="37694-202">processedDateTime</span></span> | <span data-ttu-id="37694-203">DateTime</span><span class="sxs-lookup"><span data-stu-id="37694-203">DateTime</span></span> | <span data-ttu-id="37694-204">Data em que os dados foram processados pela última vez</span><span class="sxs-lookup"><span data-stu-id="37694-204">Date when the data was last processed</span></span> |

### <a name="response-success-and-error-codes"></a><span data-ttu-id="37694-205">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="37694-205">Response success and error codes</span></span>

<span data-ttu-id="37694-206">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="37694-206">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="37694-207">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="37694-207">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="37694-208">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="37694-208">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="37694-209">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="37694-209">Response example</span></span>

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
