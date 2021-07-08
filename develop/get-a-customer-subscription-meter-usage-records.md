---
title: Obter dados de utilização da subscrição por medidor
description: Pode utilizar a recolha de recursos MeterUsageRecord para obter registos de utilização de medidores de um cliente para serviços ou recursos específicos da Azure durante o período de faturação em curso.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0bd6143c80059bd140a4c4332ab4ec19c54d99f1
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874861"
---
# <a name="get-usage-data-for-subscription-by-meter"></a><span data-ttu-id="d913b-103">Obter dados de utilização da subscrição por medidor</span><span class="sxs-lookup"><span data-stu-id="d913b-103">Get usage data for subscription by meter</span></span>

<span data-ttu-id="d913b-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d913b-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d913b-105">Pode utilizar a recolha de recursos **MeterUsageRecord** para obter registos de utilização de medidores de um cliente para serviços ou recursos específicos da Azure durante o período de faturação em curso.</span><span class="sxs-lookup"><span data-stu-id="d913b-105">You can use the **MeterUsageRecord** resource collection to get meter usage records of a customer for specific Azure services or resources during the current billing period.</span></span> <span data-ttu-id="d913b-106">Esta recolha de recursos representa um total agregado para cada metro para o ciclo de faturação atual, em todo o seu plano Azure.</span><span class="sxs-lookup"><span data-stu-id="d913b-106">This resource collection represents an aggregated total for each meter for the current billing cycle, across your entire Azure plan.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d913b-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d913b-107">Prerequisites</span></span>

- <span data-ttu-id="d913b-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d913b-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d913b-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="d913b-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="d913b-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d913b-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d913b-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d913b-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d913b-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d913b-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d913b-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d913b-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d913b-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d913b-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d913b-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d913b-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d913b-116">Um ID de assinatura</span><span class="sxs-lookup"><span data-stu-id="d913b-116">A subscription ID</span></span>

<span data-ttu-id="d913b-117">*Esta nova rota é equivalente a `subscriptions/{subscription-id}/usagerecords/resources` , que continuará a funcionar apenas para Microsoft Azure (MS-AZR-0145P) assinaturas.*</span><span class="sxs-lookup"><span data-stu-id="d913b-117">*This new route is equivalent to `subscriptions/{subscription-id}/usagerecords/resources`, which will continue to function only for Microsoft Azure (MS-AZR-0145P) subscriptions.*</span></span> <span data-ttu-id="d913b-118">Esta nova rota apoiará as assinaturas Microsoft Azure (MS-AZR-0145P) e os planos Azure.</span><span class="sxs-lookup"><span data-stu-id="d913b-118">This new route will support both Microsoft Azure (MS-AZR-0145P) subscriptions and Azure plans.</span></span> <span data-ttu-id="d913b-119">Para obter esta informação para o seu plano Azure, você precisa mudar para esta nova rota.</span><span class="sxs-lookup"><span data-stu-id="d913b-119">In order to get this information for your Azure plan, you need to switch to this new route.</span></span> <span data-ttu-id="d913b-120">Além das propriedades mencionadas nas secções seguintes, a resposta é a mesma da rota antiga.</span><span class="sxs-lookup"><span data-stu-id="d913b-120">Other than the properties mentioned in the following sections, the response is the same as the old route.</span></span>

## <a name="c"></a><span data-ttu-id="d913b-121">C\#</span><span class="sxs-lookup"><span data-stu-id="d913b-121">C\#</span></span>

<span data-ttu-id="d913b-122">Para obter registos de utilização de medidores de um cliente para um serviço ou recurso Azure específico durante o período de faturação em curso:</span><span class="sxs-lookup"><span data-stu-id="d913b-122">To get meter usage records of a customer for a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="d913b-123">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="d913b-123">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="d913b-124">Ligue para a propriedade Subscrições, e **UsageRecords,** em seguida, a propriedade **Meters.**</span><span class="sxs-lookup"><span data-stu-id="d913b-124">Call the Subscriptions property, and **UsageRecords**, then the **Meters** property.</span></span> <span data-ttu-id="d913b-125">Termine chamando os métodos Get() ou GetAsync().</span><span class="sxs-lookup"><span data-stu-id="d913b-125">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Meters.Get();
    ```

<span data-ttu-id="d913b-126">Por exemplo, consulte a seguinte amostra:</span><span class="sxs-lookup"><span data-stu-id="d913b-126">For an example, see the following sample:</span></span>

- <span data-ttu-id="d913b-127">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="d913b-127">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="d913b-128">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="d913b-128">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="d913b-129">Classe: **GetSubscriptionUsageRecordsByMeter.cs**</span><span class="sxs-lookup"><span data-stu-id="d913b-129">Class: **GetSubscriptionUsageRecordsByMeter.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="d913b-130">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d913b-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d913b-131">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d913b-131">Request syntax</span></span>

| <span data-ttu-id="d913b-132">Método</span><span class="sxs-lookup"><span data-stu-id="d913b-132">Method</span></span>  | <span data-ttu-id="d913b-133">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d913b-133">Request URI</span></span>                                                                                                                             |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d913b-134">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d913b-134">**GET**</span></span> | <span data-ttu-id="d913b-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/meterusagerecords HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d913b-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="d913b-136">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="d913b-136">URI parameters</span></span>

<span data-ttu-id="d913b-137">Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização classificadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="d913b-137">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="d913b-138">Nome</span><span class="sxs-lookup"><span data-stu-id="d913b-138">Name</span></span>                   | <span data-ttu-id="d913b-139">Tipo</span><span class="sxs-lookup"><span data-stu-id="d913b-139">Type</span></span>     | <span data-ttu-id="d913b-140">Necessário</span><span class="sxs-lookup"><span data-stu-id="d913b-140">Required</span></span> | <span data-ttu-id="d913b-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="d913b-141">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="d913b-142">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="d913b-142">**customer-tenant-id**</span></span> | <span data-ttu-id="d913b-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="d913b-143">**guid**</span></span> | <span data-ttu-id="d913b-144">Y</span><span class="sxs-lookup"><span data-stu-id="d913b-144">Y</span></span>        | <span data-ttu-id="d913b-145">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="d913b-145">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="d913b-146">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="d913b-146">**subscription-id**</span></span>    | <span data-ttu-id="d913b-147">**guid**</span><span class="sxs-lookup"><span data-stu-id="d913b-147">**guid**</span></span> | <span data-ttu-id="d913b-148">Y</span><span class="sxs-lookup"><span data-stu-id="d913b-148">Y</span></span>        | <span data-ttu-id="d913b-149">Um GUID correspondente ao identificador de um recurso de [subscrição](subscription-resources.md#subscription)do Partner Center, que representa uma subscrição Microsoft Azure (MS-AZR-0145P) ou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="d913b-149">A GUID corresponding to the identifier of a Partner Center [subscription resource](subscription-resources.md#subscription), which represents a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span> <span data-ttu-id="d913b-150">*Para os recursos de subscrição do plano Azure, forneça o **id de plano** como **id de subscrição** nesta rota.*</span><span class="sxs-lookup"><span data-stu-id="d913b-150">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d913b-151">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d913b-151">Request headers</span></span>

<span data-ttu-id="d913b-152">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d913b-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d913b-153">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d913b-153">Request body</span></span>

<span data-ttu-id="d913b-154">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d913b-154">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d913b-155">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d913b-155">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="d913b-156">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d913b-156">REST response</span></span>

<span data-ttu-id="d913b-157">Se for bem sucedido, este método devolve um recurso **PagedResourceCollection \<MeterUsageRecord>** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="d913b-157">If successful, this method returns a **PagedResourceCollection\<MeterUsageRecord>** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d913b-158">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d913b-158">Response success and error codes</span></span>

<span data-ttu-id="d913b-159">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d913b-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d913b-160">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d913b-160">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="d913b-161">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d913b-161">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="d913b-162">Exemplo de resposta para subscrições Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="d913b-162">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="d913b-163">Neste exemplo, o cliente comprou **145P Azure PayG**.</span><span class="sxs-lookup"><span data-stu-id="d913b-163">In this example, the customer purchased **145P Azure PayG**.</span></span>

<span data-ttu-id="d913b-164">*Para clientes com uma subscrição de Microsoft Azure (MS-AZR-0145P), não haverá alteração na resposta da API.*</span><span class="sxs-lookup"><span data-stu-id="d913b-164">*For customers with a Microsoft Azure (MS-AZR-0145P) subscription, there will be no change to API response.*</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 1,
    "items": [
        {
            "status": "active",
            "offerId": "MS-AZR-0145P",
            "resourceId": "11111111-F347-41B6-B02C-187B1B778A43",
            "id": "11111111-F347-41B6-B02C-187B1B778A43",
            "resourceName": "Microsoft Azure",
            "name": "Microsoft Azure",
            "totalCost": 22.861172,
            "currencyLocale": "fr-FR",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/{customer-tenant-id}/subscriptions/usagerecords/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="d913b-165">Exemplo de resposta do REST para o plano Azure</span><span class="sxs-lookup"><span data-stu-id="d913b-165">REST response example for Azure plan</span></span>

<span data-ttu-id="d913b-166">Neste exemplo, o cliente comprou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="d913b-166">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="d913b-167">*Para clientes com planos Azure, existem as seguintes alterações na resposta da API:*</span><span class="sxs-lookup"><span data-stu-id="d913b-167">*For customers with Azure plans, there are the following changes in the API response:*</span></span>

- <span data-ttu-id="d913b-168">**currencyLocale** é substituída por **moedaSCo**</span><span class="sxs-lookup"><span data-stu-id="d913b-168">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="d913b-169">**usdTotalCost** é um novo campo</span><span class="sxs-lookup"><span data-stu-id="d913b-169">**usdTotalCost** is a new field</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Fri, 26 Feb 2016 20:31:45 GMT

{
    "totalCount": 4,
    "items": [
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNVX-005J-Data Transfer In (GB)",
            "meterName": "Data Transfer In",
            "category": "Bandwidth",
            "subcategory": "Bandwidth",
            "quantityUsed": 0.01129,
            "unit": "1 GB",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNVX-005J-Data Transfer Out (GB)",
            "meterName": "Data Transfer Out",
            "category": "Bandwidth",
            "subcategory": "Bandwidth",
            "quantityUsed": 0.000224,
            "unit": "1 GB",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNZ5-006G-10K Batch Write Operations",
            "meterName": "Batch Write Operations",
            "category": "Storage",
            "subcategory": "Tables",
            "quantityUsed": 0.2462,
            "unit": "10K",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNZ5-006G-Data Stored (GB/Month)",
            "meterName": "LRS Data Stored",
            "category": "Storage",
            "subcategory": "Tables",
            "quantityUsed": 0.002632,
            "unit": "1 GB/Month",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/meterusagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
