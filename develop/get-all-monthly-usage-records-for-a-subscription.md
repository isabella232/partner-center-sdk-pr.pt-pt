---
title: Obter todos os registos de utilização mensal de uma subscrição
description: Pode utilizar a coleção de recursos AzureResourceMonthlyUsageRecord para obter uma lista de serviços dentro da subscrição de um cliente e as suas informações de utilização cotadas associadas.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: ee4bd413eec7d5a2dddbe3803df8839589ab7504
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760288"
---
# <a name="get-all-monthly-usage-records-for-a-subscription"></a><span data-ttu-id="d234e-103">Obter todos os registos de utilização mensal de uma subscrição</span><span class="sxs-lookup"><span data-stu-id="d234e-103">Get all monthly usage records for a subscription</span></span>

<span data-ttu-id="d234e-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d234e-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d234e-105">Pode utilizar a coleção de recursos [**AzureResourceMonthlyUsageRecord**](/dotnet/api/microsoft.store.partnercenter.models.usage.azureresourcemonthlyusagerecord) para obter uma lista de serviços dentro da subscrição de um cliente e as suas informações de utilização cotadas associadas.</span><span class="sxs-lookup"><span data-stu-id="d234e-105">You can use the [**AzureResourceMonthlyUsageRecord**](/dotnet/api/microsoft.store.partnercenter.models.usage.azureresourcemonthlyusagerecord) resource collection to get a list of services within a customer's subscription and their associated rated usage information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d234e-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d234e-106">Prerequisites</span></span>

- <span data-ttu-id="d234e-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d234e-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d234e-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="d234e-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="d234e-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d234e-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d234e-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d234e-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d234e-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d234e-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d234e-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d234e-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d234e-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d234e-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d234e-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d234e-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d234e-115">Um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="d234e-115">A subscription identifier.</span></span>

<span data-ttu-id="d234e-116">*Esta API suporta apenas Microsoft Azure subscrições (MS-AZR-0145P). Se estiver a utilizar um plano Azure, consulte [obter dados de utilização para subscrição por contador.](get-a-customer-subscription-meter-usage-records.md)*</span><span class="sxs-lookup"><span data-stu-id="d234e-116">*This API only supports Microsoft Azure (MS-AZR-0145P) subscriptions. If you are using an Azure plan, see [Get usage data for subscription by meter](get-a-customer-subscription-meter-usage-records.md) instead.*</span></span>

## <a name="c"></a><span data-ttu-id="d234e-117">C\#</span><span class="sxs-lookup"><span data-stu-id="d234e-117">C\#</span></span>

<span data-ttu-id="d234e-118">Para obter as informações de utilização de recursos de uma subscrição:</span><span class="sxs-lookup"><span data-stu-id="d234e-118">To get a subscription's resource usage information:</span></span>

1. <span data-ttu-id="d234e-119">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="d234e-119">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="d234e-120">Ligue para a propriedade **Subscrições,** e **UsageRecords,** em seguida, a propriedade **Recursos.**</span><span class="sxs-lookup"><span data-stu-id="d234e-120">Call the **Subscriptions** property, and **UsageRecords**, then the **Resources** property.</span></span>
3. <span data-ttu-id="d234e-121">Ligue para os **métodos Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="d234e-121">Call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// var selectedSubscriptionID as string;

var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Resources.Get();
```

<span data-ttu-id="d234e-122">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d234e-122">For an example, see the following:</span></span>

- <span data-ttu-id="d234e-123">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="d234e-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="d234e-124">Project: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="d234e-124">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="d234e-125">Classe: **SubscriptionResourceUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="d234e-125">Class: **SubscriptionResourceUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="d234e-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d234e-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d234e-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d234e-127">Request syntax</span></span>

| <span data-ttu-id="d234e-128">Método</span><span class="sxs-lookup"><span data-stu-id="d234e-128">Method</span></span>  | <span data-ttu-id="d234e-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d234e-129">Request URI</span></span>                                                                                                                                       |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d234e-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d234e-130">**GET**</span></span> | <span data-ttu-id="d234e-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-subscription}/usagerecords/resources HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d234e-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/usagerecords/resources HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="d234e-132">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="d234e-132">URI parameters</span></span>

<span data-ttu-id="d234e-133">Esta tabela lista os parâmetros de consulta necessários para obter as informações de utilização nominal.</span><span class="sxs-lookup"><span data-stu-id="d234e-133">This table lists the required query parameters to get the rated usage information.</span></span>

| <span data-ttu-id="d234e-134">Nome</span><span class="sxs-lookup"><span data-stu-id="d234e-134">Name</span></span>                    | <span data-ttu-id="d234e-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="d234e-135">Type</span></span>     | <span data-ttu-id="d234e-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="d234e-136">Required</span></span> | <span data-ttu-id="d234e-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="d234e-137">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="d234e-138">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="d234e-138">**customer-tenant-id**</span></span>  | <span data-ttu-id="d234e-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="d234e-139">**guid**</span></span> | <span data-ttu-id="d234e-140">Y</span><span class="sxs-lookup"><span data-stu-id="d234e-140">Y</span></span>        | <span data-ttu-id="d234e-141">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="d234e-141">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="d234e-142">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="d234e-142">**subscription-id**</span></span> | <span data-ttu-id="d234e-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="d234e-143">**guid**</span></span> | <span data-ttu-id="d234e-144">Y</span><span class="sxs-lookup"><span data-stu-id="d234e-144">Y</span></span>        | <span data-ttu-id="d234e-145">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="d234e-145">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d234e-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d234e-146">Request headers</span></span>

<span data-ttu-id="d234e-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d234e-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d234e-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d234e-148">Request body</span></span>

<span data-ttu-id="d234e-149">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d234e-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d234e-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d234e-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/usagerecords/resources HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 65b26053-37d0-4303-9fd1-46ad8012bcb6
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="d234e-151">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d234e-151">REST response</span></span>

<span data-ttu-id="d234e-152">Se for bem sucedido, este método devolve uma coleção de recursos **AzureResourceMonthlyUsageRecord** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="d234e-152">If successful, this method returns a collection of **AzureResourceMonthlyUsageRecord** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d234e-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d234e-153">Response success and error codes</span></span>

<span data-ttu-id="d234e-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d234e-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d234e-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d234e-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d234e-156">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d234e-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d234e-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d234e-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 12014
Content-Type: application/json
MS-CorrelationId: 648a26a4-a63e-459f-844b-4f29d7913353
MS-RequestId: be82a8ba-4a53-49f7-8313-b033c058687e
Date: Tue, 10 Nov 2015 19:09:59 GMT

{
    "totalCount":20,
    "items":[{
        "category":"Storage",
        "subcategory":"LOCALLY REDUNDANT",
        "quantityUsed":0.151287527825352,
        "unit":"GB",
        "id":"2a2419c0-cefe-46b2-8004-8eb002ad606c",
        "name":"Azure Resource 1",
        "totalCost":0.195779159290613,
        "currencyLocale":"en-US",
        "attributes":{
            "objectType":"AzureResourceMonthlyUsageRecord"
        }
    },
    {
        "category":"Remote App",
        "subcategory":"Remote App",
        "quantityUsed":0.932546524299563,
        "unit":"GB",
        "id":"7e4099c8-2b3d-41a6-a1bd-d5cf315989b2",
        "name":"Azure Resource 2",
        "totalCost":0.920983775016379,
        "currencyLocale":"en-US",
        "attributes":{
            "objectType":"AzureResourceMonthlyUsageRecord"
        }
    }],
    "links":{
        "self":{
            "uri":"/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription>%20/usagerecords",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"Collection"
    }
}
```
