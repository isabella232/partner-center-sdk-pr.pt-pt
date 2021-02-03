---
title: Obtenha um resumo de utilização para todas as subscrições de um cliente
description: Pode utilizar o recurso CustomerUsageSummary para obter o uso de um serviço ou recurso Azure específico durante o período de faturação atual.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0c918434367a3514e6a6ad6034b4897c33f51025
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769128"
---
# <a name="get-a-usage-summary-for-all-of-a-customers-subscriptions"></a><span data-ttu-id="709f6-103">Obtenha um resumo de utilização para todas as subscrições de um cliente</span><span class="sxs-lookup"><span data-stu-id="709f6-103">Get a usage summary for all of a customer's subscriptions</span></span>

<span data-ttu-id="709f6-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="709f6-104">**Applies to:**</span></span>

- <span data-ttu-id="709f6-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="709f6-105">Partner Center</span></span>
- <span data-ttu-id="709f6-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="709f6-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="709f6-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="709f6-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="709f6-108">Pode utilizar o recurso **CustomerUsageSummary** para obter o uso de um serviço ou recurso Azure específico durante o período de faturação atual.</span><span class="sxs-lookup"><span data-stu-id="709f6-108">You can use the **CustomerUsageSummary** resource to get a customer's usage of a specific Azure service or resource during the current billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="709f6-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="709f6-109">Prerequisites</span></span>

- <span data-ttu-id="709f6-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="709f6-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="709f6-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="709f6-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="709f6-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="709f6-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="709f6-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="709f6-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="709f6-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="709f6-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="709f6-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="709f6-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="709f6-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="709f6-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="709f6-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="709f6-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="709f6-118">C\#</span><span class="sxs-lookup"><span data-stu-id="709f6-118">C\#</span></span>

<span data-ttu-id="709f6-119">Para obter um resumo de utilização para todas as subscrições de um cliente:</span><span class="sxs-lookup"><span data-stu-id="709f6-119">To get a usage summary for all of a customer's subscriptions:</span></span>

1. <span data-ttu-id="709f6-120">Utilize a sua coleção **IAggregatePartner.Customers** para ligar para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="709f6-120">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="709f6-121">Ligue para a propriedade **UsageSummary,** seguida dos métodos **Get()** ou **GetAsync():**</span><span class="sxs-lookup"><span data-stu-id="709f6-121">Call the **UsageSummary** property, followed by the **Get()** or **GetAsync()** methods:</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;

    var usageSummary = partnerOperations.Customers.ById(selectedCustomerId).UsageSummary.Get();
    ```

<span data-ttu-id="709f6-122">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="709f6-122">For an example, see the following:</span></span>

- <span data-ttu-id="709f6-123">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="709f6-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="709f6-124">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="709f6-124">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="709f6-125">Classe: **GetCustomerUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="709f6-125">Class: **GetCustomerUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="709f6-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="709f6-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="709f6-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="709f6-127">Request syntax</span></span>

| <span data-ttu-id="709f6-128">Método</span><span class="sxs-lookup"><span data-stu-id="709f6-128">Method</span></span>  | <span data-ttu-id="709f6-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="709f6-129">Request URI</span></span>                                                                                         |
|---------|-----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="709f6-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="709f6-130">**GET**</span></span> | <span data-ttu-id="709f6-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/usagesummary HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="709f6-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagesummary HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="709f6-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="709f6-132">URI parameter</span></span>

<span data-ttu-id="709f6-133">Esta tabela lista o parâmetro de consulta necessário para obter as informações de utilização classificadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="709f6-133">This table lists the required query parameter to get the customer's rated usage information.</span></span>

| <span data-ttu-id="709f6-134">Nome</span><span class="sxs-lookup"><span data-stu-id="709f6-134">Name</span></span>                   | <span data-ttu-id="709f6-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="709f6-135">Type</span></span>     | <span data-ttu-id="709f6-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="709f6-136">Required</span></span> | <span data-ttu-id="709f6-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="709f6-137">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="709f6-138">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="709f6-138">**customer-tenant-id**</span></span> | <span data-ttu-id="709f6-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="709f6-139">**guid**</span></span> | <span data-ttu-id="709f6-140">Y</span><span class="sxs-lookup"><span data-stu-id="709f6-140">Y</span></span>        | <span data-ttu-id="709f6-141">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="709f6-141">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="709f6-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="709f6-142">Request headers</span></span>

<span data-ttu-id="709f6-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="709f6-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="709f6-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="709f6-144">Request body</span></span>

<span data-ttu-id="709f6-145">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="709f6-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="709f6-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="709f6-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="709f6-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="709f6-147">REST response</span></span>

<span data-ttu-id="709f6-148">Se for bem sucedido, este método devolve um recurso **CustomerUsageSummary** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="709f6-148">If successful, this method returns a **CustomerUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="709f6-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="709f6-149">Response success and error codes</span></span>

<span data-ttu-id="709f6-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="709f6-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="709f6-151">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="709f6-151">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="709f6-152">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="709f6-152">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscription"></a><span data-ttu-id="709f6-153">Exemplo de resposta para a subscrição do Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="709f6-153">Response example for Microsoft Azure (MS-AZR-0145P) subscription</span></span>

<span data-ttu-id="709f6-154">Neste exemplo, o cliente comprou uma oferta **de 145P Azure PayG.**</span><span class="sxs-lookup"><span data-stu-id="709f6-154">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="709f6-155">*Para clientes com subscrições Microsoft Azure (MS-AZR-0145P), não haverá alteração na resposta da API.*</span><span class="sxs-lookup"><span data-stu-id="709f6-155">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "budget":{
        "ammount":300.000000,
        "attributes":{
            "objectType":"SpendingBudget"
        }
    },
    "id":"65726577-C208-40FD-9735-8C85AC9CAC68",
    "name":"600 test",
    "billingStartDate":"2016-02-06T00:00:00-08:00",
    "billingEndDate":"2016-03-05T00:00:00-08:00",
    "totalCost":0.0,
    "currencyLocale":"en-US",
    "lastModifiedDate":"2016-02-26T09:42:54.5130558+00:00",
    "links":{
        "self":{
            "uri":"/customers/{customer-tenant-id}/usagesummary",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"CustomerUsageSummary"
    }
}
```

### <a name="response-example-for-azure-plan"></a><span data-ttu-id="709f6-156">Exemplo de resposta para plano Azure</span><span class="sxs-lookup"><span data-stu-id="709f6-156">Response example for Azure plan</span></span>

<span data-ttu-id="709f6-157">Neste exemplo, o cliente comprou um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="709f6-157">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="709f6-158">*Para clientes com planos Azure, existem as seguintes alterações à resposta da API:*</span><span class="sxs-lookup"><span data-stu-id="709f6-158">*For customers with Azure plans, there are the following changes to the API response:*</span></span>

- <span data-ttu-id="709f6-159">**currencyLocale** é substituída por **moedaSCo**</span><span class="sxs-lookup"><span data-stu-id="709f6-159">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="709f6-160">**usdTotalCost** é um novo campo</span><span class="sxs-lookup"><span data-stu-id="709f6-160">**usdTotalCost** is a new field</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "budget": {
        "amount": 97,
        "attributes": {
            "objectType": "SpendingBudget"
        }
    },
    "resourceId": "44908a11-641b-4c53-b7fc-0f2bfca8a581",
    "resourceName": "Modern Azure Customer UK",
    "billingStartDate": "2019-09-01T00:00:00+00:00",
    "billingEndDate": "2019-10-01T00:00:00+00:00",
    "totalCost": 28.82860766744404945074,
    "currencyCode": "GBP",
    "usdTotalCost": 35.23000000000000362337,
    "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
    "attributes": {
        "objectType": "CustomerUsageSummary"
    }
}
```
