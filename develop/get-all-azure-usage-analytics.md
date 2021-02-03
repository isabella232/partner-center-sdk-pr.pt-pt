---
title: Obter todas as informações de análise de utilização do Azure
description: Como obter toda a informação de análise de uso do Azure.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: c281dcdeb93771a69a388ad64e1127b24156c809
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769440"
---
# <a name="get-all-azure-usage-analytics-information"></a><span data-ttu-id="947cd-103">Obter todas as informações de análise de utilização do Azure</span><span class="sxs-lookup"><span data-stu-id="947cd-103">Get all Azure usage analytics information</span></span>

<span data-ttu-id="947cd-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="947cd-104">**Applies To**</span></span>

- <span data-ttu-id="947cd-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="947cd-105">Partner Center</span></span>
- <span data-ttu-id="947cd-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="947cd-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="947cd-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="947cd-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="947cd-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="947cd-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="947cd-109">Como obter todas as informações de análise de uso da Azure para os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="947cd-109">How to get all the Azure usage analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="947cd-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="947cd-110">Prerequisites</span></span>

- <span data-ttu-id="947cd-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="947cd-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="947cd-112">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="947cd-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="947cd-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="947cd-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="947cd-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="947cd-114">Request syntax</span></span>

| <span data-ttu-id="947cd-115">Método</span><span class="sxs-lookup"><span data-stu-id="947cd-115">Method</span></span>  | <span data-ttu-id="947cd-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="947cd-116">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="947cd-117">**Obter**</span><span class="sxs-lookup"><span data-stu-id="947cd-117">**GET**</span></span> | <span data-ttu-id="947cd-118">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/usage/azure HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="947cd-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/usage/azure HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="947cd-119">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="947cd-119">URI parameters</span></span>

|<span data-ttu-id="947cd-120">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="947cd-120">Parameter</span></span>        |<span data-ttu-id="947cd-121">Tipo</span><span class="sxs-lookup"><span data-stu-id="947cd-121">Type</span></span>                        |<span data-ttu-id="947cd-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="947cd-122">Description</span></span>               |
|:----------------|:---------------------------|:-------------------------|
|<span data-ttu-id="947cd-123">top</span><span class="sxs-lookup"><span data-stu-id="947cd-123">top</span></span>              | <span data-ttu-id="947cd-124">string</span><span class="sxs-lookup"><span data-stu-id="947cd-124">string</span></span>                     | <span data-ttu-id="947cd-125">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="947cd-125">The number of rows of data to return in the request.</span></span> <span data-ttu-id="947cd-126">O valor máximo e o valor predefinido se não especificado for 10000.</span><span class="sxs-lookup"><span data-stu-id="947cd-126">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="947cd-127">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="947cd-127">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span>                        |
|<span data-ttu-id="947cd-128">saltar</span><span class="sxs-lookup"><span data-stu-id="947cd-128">skip</span></span>             | <span data-ttu-id="947cd-129">int</span><span class="sxs-lookup"><span data-stu-id="947cd-129">int</span></span>                        | <span data-ttu-id="947cd-130">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="947cd-130">The number of rows to skip in the query.</span></span> <span data-ttu-id="947cd-131">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="947cd-131">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="947cd-132">Por exemplo, `top=10000 and skip=0` recupera as primeiras 10000 linhas de `top=10000 and skip=10000` dados, recupera as próximas 10000 linhas de dados, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="947cd-132">For example, `top=10000 and skip=0` retrieves the first 10000 rows of data, `top=10000 and skip=10000` retrieves the next 10000 rows of data, and so on.</span></span>                       |
|<span data-ttu-id="947cd-133">filter</span><span class="sxs-lookup"><span data-stu-id="947cd-133">filter</span></span>           | <span data-ttu-id="947cd-134">string</span><span class="sxs-lookup"><span data-stu-id="947cd-134">string</span></span>                     | <span data-ttu-id="947cd-135">O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="947cd-135">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="947cd-136">Cada declaração contém um campo e valor que estão associados aos `eq` `ne` ou operadores, e as declarações podem ser combinadas usando `and` ou `or` .</span><span class="sxs-lookup"><span data-stu-id="947cd-136">Each statement contains a field and value that are associated with the `eq` or `ne` operators, and statements can be combined using `and` or `or`.</span></span> <span data-ttu-id="947cd-137">Pode especificar as seguintes cordas:</span><span class="sxs-lookup"><span data-stu-id="947cd-137">You can specify the following strings:</span></span><br/><br/>                                                       `customerTenantId`<br/> `customerName`<br/> `subscriptionId`<br/> `subscriptionName`<br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/><span data-ttu-id="947cd-138">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="947cd-138">**Example:**</span></span><br/> `.../usage/azure?filter=meterCategory eq 'Data Management'`<br/><br/> <span data-ttu-id="947cd-139">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="947cd-139">**Example:**</span></span><br/>`.../usage/azure?filter=meterCategory eq 'Data Management' or (usageDate le cast('2018-01-01', Edm.DateTimeOffset) and usageDate le cast('2018-04-01', Edm.DateTimeOffset))`                        |
|<span data-ttu-id="947cd-140">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="947cd-140">aggregationLevel</span></span> | <span data-ttu-id="947cd-141">string</span><span class="sxs-lookup"><span data-stu-id="947cd-141">string</span></span>                    | <span data-ttu-id="947cd-142">Especifica o intervalo de tempo para a recuperação de dados agregados.</span><span class="sxs-lookup"><span data-stu-id="947cd-142">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="947cd-143">Pode ser uma das seguintes cordas: `day` `week` , ou `month` .</span><span class="sxs-lookup"><span data-stu-id="947cd-143">Can be one of the following strings: `day`, `week`, or `month`.</span></span> <span data-ttu-id="947cd-144">Se não for especificado, o padrão é `day` .</span><span class="sxs-lookup"><span data-stu-id="947cd-144">If unspecified, the default is `day`.</span></span><br/><br/>                                              <span data-ttu-id="947cd-145">O `aggregationLevel` parâmetro não é suportado sem um `groupby` .</span><span class="sxs-lookup"><span data-stu-id="947cd-145">The `aggregationLevel` parameter isn't supported without a `groupby`.</span></span> <span data-ttu-id="947cd-146">O `aggregationLevel` parâmetro aplica-se a todos os campos de data presentes no `groupby` .</span><span class="sxs-lookup"><span data-stu-id="947cd-146">The `aggregationLevel` parameter applies to all date fields present in the `groupby`.</span></span>                                                      |
|<span data-ttu-id="947cd-147">orderby</span><span class="sxs-lookup"><span data-stu-id="947cd-147">orderby</span></span>          |<span data-ttu-id="947cd-148">string</span><span class="sxs-lookup"><span data-stu-id="947cd-148">string</span></span>                     | <span data-ttu-id="947cd-149">Uma declaração que encomenda os valores de dados de resultados para cada instalação.</span><span class="sxs-lookup"><span data-stu-id="947cd-149">A statement that orders the result data values for each install.</span></span> <span data-ttu-id="947cd-150">A sintaxe é `...&orderby=field [order],field [order],...`.</span><span class="sxs-lookup"><span data-stu-id="947cd-150">The syntax is `...&orderby=field [order],field [order],...`.</span></span> <span data-ttu-id="947cd-151">O `field` parâmetro pode ser uma das seguintes cordas:</span><span class="sxs-lookup"><span data-stu-id="947cd-151">The `field` parameter can be one of the following strings:</span></span><br/><br/>                    `customerTenantId`<br/>`customerName`<br/>`subscriptionId`<br/>`subscriptionName`<br/>`usageDate`<br/>`resourceLocation`<br/>`meterCategory`<br/>`meterSubcategory`<br/>`meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/> <span data-ttu-id="947cd-152">O parâmetro *de encomenda* é opcional e pode ser `asc` ou `desc` especificar a ordem ascendente ou descendente para cada campo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="947cd-152">The *order* parameter is optional and can be `asc` or `desc` to specify ascending or descending order for each field, respectively.</span></span> <span data-ttu-id="947cd-153">A predefinição é `asc`.</span><span class="sxs-lookup"><span data-stu-id="947cd-153">The default is `asc`.</span></span><br/><br/><span data-ttu-id="947cd-154">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="947cd-154">**Example:**</span></span><br/> `...&orderby=meterCategory,meterUnit`                                                                                           |
|<span data-ttu-id="947cd-155">groupby</span><span class="sxs-lookup"><span data-stu-id="947cd-155">groupby</span></span>          |<span data-ttu-id="947cd-156">string</span><span class="sxs-lookup"><span data-stu-id="947cd-156">string</span></span>                    | <span data-ttu-id="947cd-157">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="947cd-157">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="947cd-158">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="947cd-158">You can specify the following fields:</span></span><br/><br/>                                                                                                                     `customerTenantId`<br/>`customerName`<br/> `subscriptionId` <br/> `subscriptionName` <br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit` <br/> `reservationOrderId` <br/> `reservationId` <br/> `consumptionMeterId` <br/> `serviceType` <br/><br/><span data-ttu-id="947cd-159">As linhas de dados devolvidas conterão os campos especificados no `groupby`  parâmetro, bem como a *Quantidade*.</span><span class="sxs-lookup"><span data-stu-id="947cd-159">The returned data rows will contain the fields specified in the `groupby`  parameter as well as the *Quantity*.</span></span><br/><br/><span data-ttu-id="947cd-160">O `groupby` parâmetro pode ser usado com o `aggregationLevel` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="947cd-160">The `groupby` parameter can be used with the `aggregationLevel` parameter.</span></span><br/><br/><span data-ttu-id="947cd-161">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="947cd-161">**Example:**</span></span><br/>`...&groupby=meterCategory,meterUnit` |

### <a name="request-headers"></a><span data-ttu-id="947cd-162">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="947cd-162">Request headers</span></span>

<span data-ttu-id="947cd-163">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="947cd-163">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="947cd-164">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="947cd-164">Request body</span></span>

<span data-ttu-id="947cd-165">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="947cd-165">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="947cd-166">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="947cd-166">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/usage/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="947cd-167">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="947cd-167">REST response</span></span>

<span data-ttu-id="947cd-168">Se for bem sucedido, o corpo de resposta contém uma coleção de recursos de [uso Azure.](partner-center-analytics-resources.md#csp-program-azure-usage-analytics)</span><span class="sxs-lookup"><span data-stu-id="947cd-168">If successful, the response body contains a collection of [Azure usage](partner-center-analytics-resources.md#csp-program-azure-usage-analytics) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="947cd-169">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="947cd-169">Response success and error codes</span></span>

<span data-ttu-id="947cd-170">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="947cd-170">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="947cd-171">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="947cd-171">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="947cd-172">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="947cd-172">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="947cd-173">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="947cd-173">Response example</span></span>

```http
{
  "customerTenantId": "39A1DFAC-4969-4F31-AF94-D76588189CFE",
  "customerName": "A",
  "subscriptionId": "EC649980-D623-49F5-B7C1-80CC772B83A8",
  "subscriptionName": "AZURE PURCHSE SAMPLE APP",
  "usageDate": "2018-05-27T00:00:00",
  "resourceLocation": "useast",
  "meterCategory": "Data Management",
  "meterSubcategory": "None",
  "meterUnit": "10,000s",
  "reservationOrderId": "",
  "reservationId": "",
  "consumptionMeterId": "",
  "serviceType": "",
  "quantity": 20
}
```

## <a name="see-also"></a><span data-ttu-id="947cd-174">Ver também</span><span class="sxs-lookup"><span data-stu-id="947cd-174">See also</span></span>

- [<span data-ttu-id="947cd-175">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="947cd-175">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
