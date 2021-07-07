---
title: Obter todas as informações de análise de utilização do Azure
description: Como obter toda a informação de análise de uso do Azure.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 7fe987c7dc50d55b26cd72d5aead52963eb1cfbe
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760220"
---
# <a name="get-all-azure-usage-analytics-information"></a><span data-ttu-id="2a083-103">Obter todas as informações de análise de utilização do Azure</span><span class="sxs-lookup"><span data-stu-id="2a083-103">Get all Azure usage analytics information</span></span>

<span data-ttu-id="2a083-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2a083-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2a083-105">Como obter todas as informações de análise de uso da Azure para os seus clientes.</span><span class="sxs-lookup"><span data-stu-id="2a083-105">How to get all the Azure usage analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2a083-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2a083-106">Prerequisites</span></span>

- <span data-ttu-id="2a083-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2a083-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2a083-108">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="2a083-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="2a083-109">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2a083-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2a083-110">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a083-110">Request syntax</span></span>

| <span data-ttu-id="2a083-111">Método</span><span class="sxs-lookup"><span data-stu-id="2a083-111">Method</span></span>  | <span data-ttu-id="2a083-112">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2a083-112">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="2a083-113">**Obter**</span><span class="sxs-lookup"><span data-stu-id="2a083-113">**GET**</span></span> | <span data-ttu-id="2a083-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/usage/azure HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2a083-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/usage/azure HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="2a083-115">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="2a083-115">URI parameters</span></span>

|<span data-ttu-id="2a083-116">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="2a083-116">Parameter</span></span>        |<span data-ttu-id="2a083-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="2a083-117">Type</span></span>                        |<span data-ttu-id="2a083-118">Description</span><span class="sxs-lookup"><span data-stu-id="2a083-118">Description</span></span>               |
|:----------------|:---------------------------|:-------------------------|
|<span data-ttu-id="2a083-119">top</span><span class="sxs-lookup"><span data-stu-id="2a083-119">top</span></span>              | <span data-ttu-id="2a083-120">string</span><span class="sxs-lookup"><span data-stu-id="2a083-120">string</span></span>                     | <span data-ttu-id="2a083-121">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="2a083-121">The number of rows of data to return in the request.</span></span> <span data-ttu-id="2a083-122">O valor máximo e o valor predefinido se não especificado for 10000.</span><span class="sxs-lookup"><span data-stu-id="2a083-122">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="2a083-123">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="2a083-123">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span>                        |
|<span data-ttu-id="2a083-124">saltar</span><span class="sxs-lookup"><span data-stu-id="2a083-124">skip</span></span>             | <span data-ttu-id="2a083-125">int</span><span class="sxs-lookup"><span data-stu-id="2a083-125">int</span></span>                        | <span data-ttu-id="2a083-126">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="2a083-126">The number of rows to skip in the query.</span></span> <span data-ttu-id="2a083-127">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="2a083-127">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="2a083-128">Por exemplo, `top=10000 and skip=0` recupera as primeiras 10000 linhas de `top=10000 and skip=10000` dados, recupera as próximas 10000 linhas de dados, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="2a083-128">For example, `top=10000 and skip=0` retrieves the first 10000 rows of data, `top=10000 and skip=10000` retrieves the next 10000 rows of data, and so on.</span></span>                       |
|<span data-ttu-id="2a083-129">filter</span><span class="sxs-lookup"><span data-stu-id="2a083-129">filter</span></span>           | <span data-ttu-id="2a083-130">string</span><span class="sxs-lookup"><span data-stu-id="2a083-130">string</span></span>                     | <span data-ttu-id="2a083-131">O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="2a083-131">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="2a083-132">Cada declaração contém um campo e valor que estão associados aos `eq` `ne` ou operadores, e as declarações podem ser combinadas usando `and` ou `or` .</span><span class="sxs-lookup"><span data-stu-id="2a083-132">Each statement contains a field and value that are associated with the `eq` or `ne` operators, and statements can be combined using `and` or `or`.</span></span> <span data-ttu-id="2a083-133">Pode especificar as seguintes cordas:</span><span class="sxs-lookup"><span data-stu-id="2a083-133">You can specify the following strings:</span></span><br/><br/>                                                       `customerTenantId`<br/> `customerName`<br/> `subscriptionId`<br/> `subscriptionName`<br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/><span data-ttu-id="2a083-134">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="2a083-134">**Example:**</span></span><br/> `.../usage/azure?filter=meterCategory eq 'Data Management'`<br/><br/> <span data-ttu-id="2a083-135">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="2a083-135">**Example:**</span></span><br/>`.../usage/azure?filter=meterCategory eq 'Data Management' or (usageDate le cast('2018-01-01', Edm.DateTimeOffset) and usageDate le cast('2018-04-01', Edm.DateTimeOffset))`                        |
|<span data-ttu-id="2a083-136">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="2a083-136">aggregationLevel</span></span> | <span data-ttu-id="2a083-137">string</span><span class="sxs-lookup"><span data-stu-id="2a083-137">string</span></span>                    | <span data-ttu-id="2a083-138">Especifica o intervalo de tempo para a recuperação de dados agregados.</span><span class="sxs-lookup"><span data-stu-id="2a083-138">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="2a083-139">Pode ser uma das seguintes cordas: `day` `week` , ou `month` .</span><span class="sxs-lookup"><span data-stu-id="2a083-139">Can be one of the following strings: `day`, `week`, or `month`.</span></span> <span data-ttu-id="2a083-140">Se não for especificado, o padrão é `day` .</span><span class="sxs-lookup"><span data-stu-id="2a083-140">If unspecified, the default is `day`.</span></span><br/><br/>                                              <span data-ttu-id="2a083-141">O `aggregationLevel` parâmetro não é suportado sem um `groupby` .</span><span class="sxs-lookup"><span data-stu-id="2a083-141">The `aggregationLevel` parameter isn't supported without a `groupby`.</span></span> <span data-ttu-id="2a083-142">O `aggregationLevel` parâmetro aplica-se a todos os campos de data presentes no `groupby` .</span><span class="sxs-lookup"><span data-stu-id="2a083-142">The `aggregationLevel` parameter applies to all date fields present in the `groupby`.</span></span>                                                      |
|<span data-ttu-id="2a083-143">orderby</span><span class="sxs-lookup"><span data-stu-id="2a083-143">orderby</span></span>          |<span data-ttu-id="2a083-144">string</span><span class="sxs-lookup"><span data-stu-id="2a083-144">string</span></span>                     | <span data-ttu-id="2a083-145">Uma declaração que encomenda os valores de dados de resultados para cada instalação.</span><span class="sxs-lookup"><span data-stu-id="2a083-145">A statement that orders the result data values for each install.</span></span> <span data-ttu-id="2a083-146">A sintaxe é `...&orderby=field [order],field [order],...`.</span><span class="sxs-lookup"><span data-stu-id="2a083-146">The syntax is `...&orderby=field [order],field [order],...`.</span></span> <span data-ttu-id="2a083-147">O `field` parâmetro pode ser uma das seguintes cordas:</span><span class="sxs-lookup"><span data-stu-id="2a083-147">The `field` parameter can be one of the following strings:</span></span><br/><br/>                    `customerTenantId`<br/>`customerName`<br/>`subscriptionId`<br/>`subscriptionName`<br/>`usageDate`<br/>`resourceLocation`<br/>`meterCategory`<br/>`meterSubcategory`<br/>`meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/> <span data-ttu-id="2a083-148">O parâmetro *de encomenda* é opcional e pode ser `asc` ou `desc` especificar a ordem ascendente ou descendente para cada campo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2a083-148">The *order* parameter is optional and can be `asc` or `desc` to specify ascending or descending order for each field, respectively.</span></span> <span data-ttu-id="2a083-149">A predefinição é `asc`.</span><span class="sxs-lookup"><span data-stu-id="2a083-149">The default is `asc`.</span></span><br/><br/><span data-ttu-id="2a083-150">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="2a083-150">**Example:**</span></span><br/> `...&orderby=meterCategory,meterUnit`                                                                                           |
|<span data-ttu-id="2a083-151">groupby</span><span class="sxs-lookup"><span data-stu-id="2a083-151">groupby</span></span>          |<span data-ttu-id="2a083-152">string</span><span class="sxs-lookup"><span data-stu-id="2a083-152">string</span></span>                    | <span data-ttu-id="2a083-153">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="2a083-153">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="2a083-154">Pode especificar os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="2a083-154">You can specify the following fields:</span></span><br/><br/>                                                                                                                     `customerTenantId`<br/>`customerName`<br/> `subscriptionId` <br/> `subscriptionName` <br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit` <br/> `reservationOrderId` <br/> `reservationId` <br/> `consumptionMeterId` <br/> `serviceType` <br/><br/><span data-ttu-id="2a083-155">As linhas de dados devolvidas conterão os campos especificados no `groupby`  parâmetro e na *quantidade*.</span><span class="sxs-lookup"><span data-stu-id="2a083-155">The returned data rows will contain the fields specified in the `groupby`  parameter and the *Quantity*.</span></span><br/><br/><span data-ttu-id="2a083-156">O `groupby` parâmetro pode ser usado com o `aggregationLevel` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2a083-156">The `groupby` parameter can be used with the `aggregationLevel` parameter.</span></span><br/><br/><span data-ttu-id="2a083-157">**Exemplo:**</span><span class="sxs-lookup"><span data-stu-id="2a083-157">**Example:**</span></span><br/>`...&groupby=meterCategory,meterUnit` |

### <a name="request-headers"></a><span data-ttu-id="2a083-158">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2a083-158">Request headers</span></span>

<span data-ttu-id="2a083-159">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2a083-159">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2a083-160">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="2a083-160">Request body</span></span>

<span data-ttu-id="2a083-161">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2a083-161">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="2a083-162">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="2a083-162">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/usage/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="2a083-163">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2a083-163">REST response</span></span>

<span data-ttu-id="2a083-164">Se for bem sucedido, o corpo de resposta contém uma coleção de recursos de [uso Azure.](partner-center-analytics-resources.md#csp-program-azure-usage-analytics)</span><span class="sxs-lookup"><span data-stu-id="2a083-164">If successful, the response body contains a collection of [Azure usage](partner-center-analytics-resources.md#csp-program-azure-usage-analytics) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2a083-165">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2a083-165">Response success and error codes</span></span>

<span data-ttu-id="2a083-166">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2a083-166">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2a083-167">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2a083-167">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2a083-168">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2a083-168">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2a083-169">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="2a083-169">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2a083-170">Ver também</span><span class="sxs-lookup"><span data-stu-id="2a083-170">See also</span></span>

- [<span data-ttu-id="2a083-171">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="2a083-171">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
