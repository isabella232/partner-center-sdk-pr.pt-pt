---
title: Obter dados de utilização da subscrição por medidor
description: Pode utilizar a recolha de recursos MeterUsageRecord para obter registos de utilização de medidores de um cliente para serviços ou recursos específicos da Azure durante o período de faturação em curso.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df981eae8d2caee2dcb7f36696725ec011ead75b
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769146"
---
# <a name="get-usage-data-for-subscription-by-meter"></a><span data-ttu-id="7425f-103">Obter dados de utilização da subscrição por medidor</span><span class="sxs-lookup"><span data-stu-id="7425f-103">Get usage data for subscription by meter</span></span>

<span data-ttu-id="7425f-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="7425f-104">**Applies to:**</span></span>

- <span data-ttu-id="7425f-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="7425f-105">Partner Center</span></span>
- <span data-ttu-id="7425f-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="7425f-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="7425f-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7425f-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7425f-108">Pode utilizar a recolha de recursos **MeterUsageRecord** para obter registos de utilização de medidores de um cliente para serviços ou recursos específicos da Azure durante o período de faturação em curso.</span><span class="sxs-lookup"><span data-stu-id="7425f-108">You can use the **MeterUsageRecord** resource collection to get meter usage records of a customer for specific Azure services or resources during the current billing period.</span></span> <span data-ttu-id="7425f-109">Esta recolha de recursos representa um total agregado para cada metro para o ciclo de faturação atual, em todo o seu plano Azure.</span><span class="sxs-lookup"><span data-stu-id="7425f-109">This resource collection represents an aggregated total for each meter for the current billing cycle, across your entire Azure plan.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7425f-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7425f-110">Prerequisites</span></span>

- <span data-ttu-id="7425f-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7425f-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7425f-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="7425f-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="7425f-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7425f-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7425f-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="7425f-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7425f-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="7425f-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7425f-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="7425f-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7425f-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="7425f-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7425f-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7425f-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7425f-119">Um ID de assinatura</span><span class="sxs-lookup"><span data-stu-id="7425f-119">A subscription ID</span></span>

<span data-ttu-id="7425f-120">*Esta nova rota é equivalente a `subscriptions/{subscription-id}/usagerecords/resources` , que continuará a funcionar apenas para as subscrições do Microsoft Azure (MS-AZR-0145P).*</span><span class="sxs-lookup"><span data-stu-id="7425f-120">*This new route is equivalent to `subscriptions/{subscription-id}/usagerecords/resources`, which will continue to function only for Microsoft Azure (MS-AZR-0145P) subscriptions.*</span></span> <span data-ttu-id="7425f-121">Esta nova rota irá suportar tanto as subscrições do Microsoft Azure (MS-AZR-0145P) como os planos Azure.</span><span class="sxs-lookup"><span data-stu-id="7425f-121">This new route will support both Microsoft Azure (MS-AZR-0145P) subscriptions and Azure plans.</span></span> <span data-ttu-id="7425f-122">Para obter esta informação para o seu plano Azure, você precisa mudar para esta nova rota.</span><span class="sxs-lookup"><span data-stu-id="7425f-122">In order to get this information for your Azure plan, you need to switch to this new route.</span></span> <span data-ttu-id="7425f-123">Além das propriedades mencionadas nas secções seguintes, a resposta é a mesma da rota antiga.</span><span class="sxs-lookup"><span data-stu-id="7425f-123">Other than the properties mentioned in the following sections, the response is the same as the old route.</span></span>

## <a name="c"></a><span data-ttu-id="7425f-124">C\#</span><span class="sxs-lookup"><span data-stu-id="7425f-124">C\#</span></span>

<span data-ttu-id="7425f-125">Para obter registos de utilização de medidores de um cliente para um serviço ou recurso Azure específico durante o período de faturação em curso:</span><span class="sxs-lookup"><span data-stu-id="7425f-125">To get meter usage records of a customer for a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="7425f-126">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="7425f-126">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="7425f-127">Ligue para a propriedade Subscrições, e **UsageRecords,** em seguida, a propriedade **Meters.**</span><span class="sxs-lookup"><span data-stu-id="7425f-127">Call the Subscriptions property, and **UsageRecords**, then the **Meters** property.</span></span> <span data-ttu-id="7425f-128">Termine chamando os métodos Get() ou GetAsync().</span><span class="sxs-lookup"><span data-stu-id="7425f-128">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Meters.Get();
    ```

<span data-ttu-id="7425f-129">Por exemplo, consulte a seguinte amostra:</span><span class="sxs-lookup"><span data-stu-id="7425f-129">For an example, see the following sample:</span></span>

- <span data-ttu-id="7425f-130">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="7425f-130">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="7425f-131">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="7425f-131">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="7425f-132">Classe: **GetSubscriptionUsageRecordsByMeter.cs**</span><span class="sxs-lookup"><span data-stu-id="7425f-132">Class: **GetSubscriptionUsageRecordsByMeter.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="7425f-133">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="7425f-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7425f-134">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="7425f-134">Request syntax</span></span>

| <span data-ttu-id="7425f-135">Método</span><span class="sxs-lookup"><span data-stu-id="7425f-135">Method</span></span>  | <span data-ttu-id="7425f-136">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="7425f-136">Request URI</span></span>                                                                                                                             |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7425f-137">**Obter**</span><span class="sxs-lookup"><span data-stu-id="7425f-137">**GET**</span></span> | <span data-ttu-id="7425f-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/meterusagerecords HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7425f-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="7425f-139">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="7425f-139">URI parameters</span></span>

<span data-ttu-id="7425f-140">Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização classificadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="7425f-140">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="7425f-141">Nome</span><span class="sxs-lookup"><span data-stu-id="7425f-141">Name</span></span>                   | <span data-ttu-id="7425f-142">Tipo</span><span class="sxs-lookup"><span data-stu-id="7425f-142">Type</span></span>     | <span data-ttu-id="7425f-143">Necessário</span><span class="sxs-lookup"><span data-stu-id="7425f-143">Required</span></span> | <span data-ttu-id="7425f-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="7425f-144">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="7425f-145">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="7425f-145">**customer-tenant-id**</span></span> | <span data-ttu-id="7425f-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="7425f-146">**guid**</span></span> | <span data-ttu-id="7425f-147">Y</span><span class="sxs-lookup"><span data-stu-id="7425f-147">Y</span></span>        | <span data-ttu-id="7425f-148">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="7425f-148">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="7425f-149">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="7425f-149">**subscription-id**</span></span>    | <span data-ttu-id="7425f-150">**guid**</span><span class="sxs-lookup"><span data-stu-id="7425f-150">**guid**</span></span> | <span data-ttu-id="7425f-151">Y</span><span class="sxs-lookup"><span data-stu-id="7425f-151">Y</span></span>        | <span data-ttu-id="7425f-152">Um GUID correspondente ao identificador de um recurso de [subscrição](subscription-resources.md#subscription)partner Center, que representa uma subscrição do Microsoft Azure (MS-AZR-0145P) ou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="7425f-152">A GUID corresponding to the identifier of a Partner Center [subscription resource](subscription-resources.md#subscription), which represents a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span> <span data-ttu-id="7425f-153">*Para os recursos de subscrição do plano Azure, forneça o **id de plano** como **id de subscrição** nesta rota.*</span><span class="sxs-lookup"><span data-stu-id="7425f-153">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="7425f-154">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="7425f-154">Request headers</span></span>

<span data-ttu-id="7425f-155">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7425f-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7425f-156">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="7425f-156">Request body</span></span>

<span data-ttu-id="7425f-157">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7425f-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7425f-158">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="7425f-158">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="7425f-159">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="7425f-159">REST response</span></span>

<span data-ttu-id="7425f-160">Se for bem sucedido, este método devolve um recurso **PagedResourceCollection \<MeterUsageRecord>** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="7425f-160">If successful, this method returns a **PagedResourceCollection\<MeterUsageRecord>** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7425f-161">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="7425f-161">Response success and error codes</span></span>

<span data-ttu-id="7425f-162">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="7425f-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7425f-163">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="7425f-163">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="7425f-164">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="7425f-164">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="7425f-165">Exemplo de resposta para subscrições microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="7425f-165">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="7425f-166">Neste exemplo, o cliente comprou **145P Azure PayG**.</span><span class="sxs-lookup"><span data-stu-id="7425f-166">In this example, the customer purchased **145P Azure PayG**.</span></span>

<span data-ttu-id="7425f-167">*Para clientes com uma subscrição Microsoft Azure (MS-AZR-0145P), não haverá alteração na resposta da API.*</span><span class="sxs-lookup"><span data-stu-id="7425f-167">*For customers with a Microsoft Azure (MS-AZR-0145P) subscription, there will be no change to API response.*</span></span>

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

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="7425f-168">Exemplo de resposta do REST para o plano Azure</span><span class="sxs-lookup"><span data-stu-id="7425f-168">REST response example for Azure plan</span></span>

<span data-ttu-id="7425f-169">Neste exemplo, o cliente comprou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="7425f-169">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="7425f-170">*Para clientes com planos Azure, existem as seguintes alterações na resposta da API:*</span><span class="sxs-lookup"><span data-stu-id="7425f-170">*For customers with Azure plans, there are the following changes in the API response:*</span></span>

- <span data-ttu-id="7425f-171">**currencyLocale** é substituída por **moedaSCo**</span><span class="sxs-lookup"><span data-stu-id="7425f-171">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="7425f-172">**usdTotalCost** é um novo campo</span><span class="sxs-lookup"><span data-stu-id="7425f-172">**usdTotalCost** is a new field</span></span>

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
