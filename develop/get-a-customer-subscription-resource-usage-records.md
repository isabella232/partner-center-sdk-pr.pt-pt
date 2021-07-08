---
title: Obter dados de utilização da subscrição por recurso
description: Pode utilizar o recurso ResourceUsageRecord para obter os registos de utilização de recursos de um cliente para serviços ou recursos específicos da Azure durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 50edb9de1d09363b242c080a76c683732f05a5de
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874844"
---
# <a name="get-usage-data-for-subscription-by-resource"></a><span data-ttu-id="d4ca1-103">Obter dados de utilização da subscrição por recurso</span><span class="sxs-lookup"><span data-stu-id="d4ca1-103">Get usage data for subscription by resource</span></span>

<span data-ttu-id="d4ca1-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d4ca1-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d4ca1-105">Este artigo descreve como obter o recurso **ResourceUsageRecord.**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-105">This article describes how to get the **ResourceUsageRecord** resource.</span></span> <span data-ttu-id="d4ca1-106">Este recurso representa um total agregado para o mês para os recursos individuais aprovisionados no seu plano Azure.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-106">This resource represents an aggregated total for the month for individual resources provisioned in your Azure plan.</span></span> <span data-ttu-id="d4ca1-107">Pode utilizar este recurso para obter os registos de utilização de recursos de um cliente para serviços ou recursos específicos da Azure durante o período de faturação atual.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-107">You can use this resource to get a customer's resource usage records for specific Azure services or resources during the current billing period.</span></span> <span data-ttu-id="d4ca1-108">Esta API devolve dados que não estavam disponíveis anteriormente através das APIs de gastos da Azure.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-108">This API returns data that was not available previously through Azure spending APIs.</span></span>

<span data-ttu-id="d4ca1-109">*Esta rota não suporta Microsoft Azure subscrições (MS-AZR-0145P).*</span><span class="sxs-lookup"><span data-stu-id="d4ca1-109">*This route does not support Microsoft Azure (MS-AZR-0145P) subscriptions.*</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4ca1-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d4ca1-110">Prerequisites</span></span>

- <span data-ttu-id="d4ca1-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d4ca1-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d4ca1-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="d4ca1-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d4ca1-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d4ca1-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d4ca1-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d4ca1-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d4ca1-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d4ca1-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d4ca1-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d4ca1-119">Um identificador de assinatura</span><span class="sxs-lookup"><span data-stu-id="d4ca1-119">A subscription identifier</span></span>

## <a name="c"></a><span data-ttu-id="d4ca1-120">C\#</span><span class="sxs-lookup"><span data-stu-id="d4ca1-120">C\#</span></span>

<span data-ttu-id="d4ca1-121">Para obter registos de utilização de recursos de um cliente para um serviço ou recurso Azure específico durante o período de faturação atual:</span><span class="sxs-lookup"><span data-stu-id="d4ca1-121">To get resource usage records of a customer for a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="d4ca1-122">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="d4ca1-123">Ligue para a propriedade de Subscrições e **UsageRecords,** e depois para a propriedade **Recursos.**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-123">Call the Subscriptions property and **UsageRecords**, and then the **Resources** property.</span></span> <span data-ttu-id="d4ca1-124">Termine chamando os métodos Get() ou GetAsync().</span><span class="sxs-lookup"><span data-stu-id="d4ca1-124">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Resources.Get();
    ```

<span data-ttu-id="d4ca1-125">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d4ca1-125">For an example, see the following:</span></span>

- <span data-ttu-id="d4ca1-126">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="d4ca1-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="d4ca1-127">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-127">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="d4ca1-128">Classe: **GetSubscriptionUsageRecordsByResource.cs**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-128">Class: **GetSubscriptionUsageRecordsByResource.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="d4ca1-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d4ca1-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d4ca1-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4ca1-130">Request syntax</span></span>

| <span data-ttu-id="d4ca1-131">Método</span><span class="sxs-lookup"><span data-stu-id="d4ca1-131">Method</span></span>  | <span data-ttu-id="d4ca1-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d4ca1-132">Request URI</span></span>                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d4ca1-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-133">**GET**</span></span> | <span data-ttu-id="d4ca1-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/resourceusagerecords HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d4ca1-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/resourceusagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="d4ca1-135">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="d4ca1-135">URI parameters</span></span>

<span data-ttu-id="d4ca1-136">Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização classificadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-136">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="d4ca1-137">Nome</span><span class="sxs-lookup"><span data-stu-id="d4ca1-137">Name</span></span>                   | <span data-ttu-id="d4ca1-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="d4ca1-138">Type</span></span>     | <span data-ttu-id="d4ca1-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="d4ca1-139">Required</span></span> | <span data-ttu-id="d4ca1-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4ca1-140">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="d4ca1-141">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-141">**customer-tenant-id**</span></span> | <span data-ttu-id="d4ca1-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-142">**guid**</span></span> | <span data-ttu-id="d4ca1-143">Y</span><span class="sxs-lookup"><span data-stu-id="d4ca1-143">Y</span></span>        | <span data-ttu-id="d4ca1-144">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-144">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="d4ca1-145">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-145">**subscription-id**</span></span>    | <span data-ttu-id="d4ca1-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="d4ca1-146">**guid**</span></span> | <span data-ttu-id="d4ca1-147">Y</span><span class="sxs-lookup"><span data-stu-id="d4ca1-147">Y</span></span>        | <span data-ttu-id="d4ca1-148">Um GUID correspondente ao identificador de um recurso de [subscrição](subscription-resources.md#subscription)do Partner Center, que representa uma subscrição Microsoft Azure (MS-AZR-0145P) ou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-148">A GUID corresponding to the identifier of a Partner Center [subscription resource](subscription-resources.md#subscription), which represents a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span> <span data-ttu-id="d4ca1-149">*Para os recursos de subscrição do plano Azure, forneça o **id de plano** como **id de subscrição** nesta rota.*</span><span class="sxs-lookup"><span data-stu-id="d4ca1-149">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d4ca1-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d4ca1-150">Request headers</span></span>

<span data-ttu-id="d4ca1-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d4ca1-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d4ca1-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d4ca1-152">Request body</span></span>

<span data-ttu-id="d4ca1-153">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d4ca1-154">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d4ca1-154">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/resourceusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="d4ca1-155">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d4ca1-155">REST response</span></span>

<span data-ttu-id="d4ca1-156">Se for bem sucedido, este método devolve um recurso **PagedResourceCollection \<ResourceUsageRecord>** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-156">If successful, this method returns a **PagedResourceCollection\<ResourceUsageRecord>** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d4ca1-157">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d4ca1-157">Response success and error codes</span></span>

<span data-ttu-id="d4ca1-158">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d4ca1-159">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d4ca1-159">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="d4ca1-160">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d4ca1-160">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d4ca1-161">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d4ca1-161">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 3,
    "items": [
        {
            "subscriptionId": "{subscription-id}",
            "resourceUri": "/subscriptions/{subscription-id}/resourceGroups/TESTRG1/providers/Microsoft.Compute/disks/testVM1_OsDisk_1_531d3c99534b4649ae025d485370143e",
            "resourceType": "Microsoft.Compute",
            "entitlementId": "{entitlemen-id}",
            "entitlementName": "Partner Subscription",
            "resourceGroupName": "TESTRG1",
            "name": "testVM1_OsDisk_1_531d3c99534b4649ae025d485370143e",
            "resourceName": "testVM1_OsDisk_1_531d3c99534b4649ae025d485370143e",
            "totalCost": 2.0211938955034572,
            "currencyCode": "GBP",
            "usdTotalCost": 2.4700000000000001,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "ResourceUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "resourceUri": "/subscriptions/{subscription-id}/resourceGroups/TESTRG1/providers/Microsoft.Compute/virtualMachines/testVM1",
            "resourceType": "Microsoft.Compute",
            "entitlementId": "{entitlement-id}",
            "entitlementName": "Partner Subscription",
            "resourceGroupName": "TESTRG1",
            "name": "testVM1",
            "resourceName": "testVM1",
            "totalCost": 80.3322286322163563,
            "currencyCode": "GBP",
            "usdTotalCost": 98.1699999999999985,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "ResourceUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "resourceUri": "/subscriptions/{subscription-id}/resourceGroups/testrg1/providers/Microsoft.Storage/storageAccounts/testrg1diag153",
            "resourceType": "Microsoft.Storage",
            "entitlementId": "{entitlemen-id}",
            "entitlementName": "Partner Subscription",
            "resourceGroupName": "testrg1",
            "name": "testrg1diag153",
            "resourceName": "testrg1diag153",
            "totalCost": 0.0081829712368561032,
            "currencyCode": "GBP",
            "usdTotalCost": 0.0099999999999999997,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "ResourceUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/resourceusagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
