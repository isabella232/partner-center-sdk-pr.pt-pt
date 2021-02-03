---
title: Obter dados de utilização da subscrição por recurso
description: Pode utilizar o recurso ResourceUsageRecord para obter os registos de utilização de recursos de um cliente para serviços ou recursos específicos da Azure durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e815430730dd7182380e9efd1fea80f9e84d2ce7
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769140"
---
# <a name="get-usage-data-for-subscription-by-resource"></a><span data-ttu-id="0bb44-103">Obter dados de utilização da subscrição por recurso</span><span class="sxs-lookup"><span data-stu-id="0bb44-103">Get usage data for subscription by resource</span></span>

<span data-ttu-id="0bb44-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="0bb44-104">**Applies to:**</span></span>

- <span data-ttu-id="0bb44-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="0bb44-105">Partner Center</span></span>
- <span data-ttu-id="0bb44-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="0bb44-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="0bb44-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0bb44-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0bb44-108">Este artigo descreve como obter o recurso **ResourceUsageRecord.**</span><span class="sxs-lookup"><span data-stu-id="0bb44-108">This article describes how to get the **ResourceUsageRecord** resource.</span></span> <span data-ttu-id="0bb44-109">Este recurso representa um total agregado para o mês para os recursos individuais aprovisionados no seu plano Azure.</span><span class="sxs-lookup"><span data-stu-id="0bb44-109">This resource represents an aggregated total for the month for individual resources provisioned in your Azure plan.</span></span> <span data-ttu-id="0bb44-110">Pode utilizar este recurso para obter os registos de utilização de recursos de um cliente para serviços ou recursos específicos da Azure durante o período de faturação atual.</span><span class="sxs-lookup"><span data-stu-id="0bb44-110">You can use this resource to get a customer's resource usage records for specific Azure services or resources during the current billing period.</span></span> <span data-ttu-id="0bb44-111">Esta API devolve dados que não estavam disponíveis anteriormente através das APIs de gastos da Azure.</span><span class="sxs-lookup"><span data-stu-id="0bb44-111">This API returns data that was not available previously through Azure spending APIs.</span></span>

<span data-ttu-id="0bb44-112">*Esta rota não suporta subscrições do Microsoft Azure (MS-AZR-0145P).*</span><span class="sxs-lookup"><span data-stu-id="0bb44-112">*This route does not support Microsoft Azure (MS-AZR-0145P) subscriptions.*</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0bb44-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0bb44-113">Prerequisites</span></span>

- <span data-ttu-id="0bb44-114">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0bb44-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0bb44-115">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="0bb44-115">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="0bb44-116">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0bb44-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="0bb44-117">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="0bb44-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="0bb44-118">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="0bb44-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="0bb44-119">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="0bb44-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="0bb44-120">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="0bb44-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="0bb44-121">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0bb44-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="0bb44-122">Um identificador de assinatura</span><span class="sxs-lookup"><span data-stu-id="0bb44-122">A subscription identifier</span></span>

## <a name="c"></a><span data-ttu-id="0bb44-123">C\#</span><span class="sxs-lookup"><span data-stu-id="0bb44-123">C\#</span></span>

<span data-ttu-id="0bb44-124">Para obter registos de utilização de recursos de um cliente para um serviço ou recurso Azure específico durante o período de faturação atual:</span><span class="sxs-lookup"><span data-stu-id="0bb44-124">To get resource usage records of a customer for a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="0bb44-125">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="0bb44-125">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="0bb44-126">Ligue para a propriedade Subscrições, bem como **UsageRecords,** em seguida, a propriedade **Recursos.**</span><span class="sxs-lookup"><span data-stu-id="0bb44-126">Call the Subscriptions property, as well as **UsageRecords**, then the **Resources** property.</span></span> <span data-ttu-id="0bb44-127">Termine chamando os métodos Get() ou GetAsync().</span><span class="sxs-lookup"><span data-stu-id="0bb44-127">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Resources.Get();
    ```

<span data-ttu-id="0bb44-128">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0bb44-128">For an example, see the following:</span></span>

- <span data-ttu-id="0bb44-129">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="0bb44-129">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="0bb44-130">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="0bb44-130">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="0bb44-131">Classe: **GetSubscriptionUsageRecordsByResource.cs**</span><span class="sxs-lookup"><span data-stu-id="0bb44-131">Class: **GetSubscriptionUsageRecordsByResource.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="0bb44-132">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="0bb44-132">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0bb44-133">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bb44-133">Request syntax</span></span>

| <span data-ttu-id="0bb44-134">Método</span><span class="sxs-lookup"><span data-stu-id="0bb44-134">Method</span></span>  | <span data-ttu-id="0bb44-135">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="0bb44-135">Request URI</span></span>                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0bb44-136">**Obter**</span><span class="sxs-lookup"><span data-stu-id="0bb44-136">**GET**</span></span> | <span data-ttu-id="0bb44-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/resourceusagerecords HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0bb44-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/resourceusagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="0bb44-138">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="0bb44-138">URI parameters</span></span>

<span data-ttu-id="0bb44-139">Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização classificadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="0bb44-139">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="0bb44-140">Nome</span><span class="sxs-lookup"><span data-stu-id="0bb44-140">Name</span></span>                   | <span data-ttu-id="0bb44-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="0bb44-141">Type</span></span>     | <span data-ttu-id="0bb44-142">Necessário</span><span class="sxs-lookup"><span data-stu-id="0bb44-142">Required</span></span> | <span data-ttu-id="0bb44-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bb44-143">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="0bb44-144">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="0bb44-144">**customer-tenant-id**</span></span> | <span data-ttu-id="0bb44-145">**guid**</span><span class="sxs-lookup"><span data-stu-id="0bb44-145">**guid**</span></span> | <span data-ttu-id="0bb44-146">Y</span><span class="sxs-lookup"><span data-stu-id="0bb44-146">Y</span></span>        | <span data-ttu-id="0bb44-147">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="0bb44-147">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="0bb44-148">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="0bb44-148">**subscription-id**</span></span>    | <span data-ttu-id="0bb44-149">**guid**</span><span class="sxs-lookup"><span data-stu-id="0bb44-149">**guid**</span></span> | <span data-ttu-id="0bb44-150">Y</span><span class="sxs-lookup"><span data-stu-id="0bb44-150">Y</span></span>        | <span data-ttu-id="0bb44-151">Um GUID correspondente ao identificador de um recurso de [subscrição](subscription-resources.md#subscription)partner Center, que representa uma subscrição do Microsoft Azure (MS-AZR-0145P) ou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="0bb44-151">A GUID corresponding to the identifier of a Partner Center [subscription resource](subscription-resources.md#subscription), which represents a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span> <span data-ttu-id="0bb44-152">*Para os recursos de subscrição do plano Azure, forneça o **id de plano** como **id de subscrição** nesta rota.*</span><span class="sxs-lookup"><span data-stu-id="0bb44-152">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="0bb44-153">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="0bb44-153">Request headers</span></span>

<span data-ttu-id="0bb44-154">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="0bb44-154">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0bb44-155">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="0bb44-155">Request body</span></span>

<span data-ttu-id="0bb44-156">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0bb44-156">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0bb44-157">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="0bb44-157">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/resourceusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="0bb44-158">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="0bb44-158">REST response</span></span>

<span data-ttu-id="0bb44-159">Se for bem sucedido, este método devolve um recurso **PagedResourceCollection \<ResourceUsageRecord>** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="0bb44-159">If successful, this method returns a **PagedResourceCollection\<ResourceUsageRecord>** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0bb44-160">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="0bb44-160">Response success and error codes</span></span>

<span data-ttu-id="0bb44-161">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="0bb44-161">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0bb44-162">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="0bb44-162">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="0bb44-163">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="0bb44-163">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0bb44-164">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="0bb44-164">Response example</span></span>

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
