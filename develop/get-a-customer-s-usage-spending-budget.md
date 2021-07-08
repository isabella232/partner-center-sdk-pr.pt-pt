---
title: Obtenha o orçamento de gastos de uso de um cliente
description: Pode utilizar um orçamento de gastos (o objeto SpendBudget) para atualizar um resumo de utilização do cliente (o recurso CustomerUsageSummary).
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b55f59fff7e5d7865811ecab3e901848126d31f7
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874878"
---
# <a name="get-a-customers-usage-spending-budget"></a><span data-ttu-id="eb453-103">Obtenha o orçamento de gastos de uso de um cliente</span><span class="sxs-lookup"><span data-stu-id="eb453-103">Get a customer's usage spending budget</span></span>

<span data-ttu-id="eb453-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="eb453-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="eb453-105">Pode atualizar o orçamento de gastos (o objeto **SpendBudget)** no resumo de utilização do [cliente (o recurso **CustomerUsageSummary)**](customer-usage-resources.md#customerusagesummary).</span><span class="sxs-lookup"><span data-stu-id="eb453-105">You can update the spending budget (the **SpendingBudget** object) in the [customer usage summary (the **CustomerUsageSummary** resource)](customer-usage-resources.md#customerusagesummary).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb453-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="eb453-106">Prerequisites</span></span>

- <span data-ttu-id="eb453-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eb453-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="eb453-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="eb453-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="eb453-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb453-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="eb453-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="eb453-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="eb453-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="eb453-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="eb453-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="eb453-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="eb453-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="eb453-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="eb453-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb453-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="eb453-115">C\#</span><span class="sxs-lookup"><span data-stu-id="eb453-115">C\#</span></span>

<span data-ttu-id="eb453-116">Para atualizar o orçamento de gastos de utilização de um cliente:</span><span class="sxs-lookup"><span data-stu-id="eb453-116">To update a customer's usage spending budget:</span></span>

1. <span data-ttu-id="eb453-117">Crie um novo objeto [**Spendbudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) com o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="eb453-117">Create a new [**SpendingBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) object with the updated amount.</span></span>

2. <span data-ttu-id="eb453-118">Utilize a coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) para ligar para o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="eb453-118">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) collection to call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer's identifier.</span></span>

3. <span data-ttu-id="eb453-119">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) para obter o orçamento de utilização do cliente.</span><span class="sxs-lookup"><span data-stu-id="eb453-119">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to get the customer's usage budget.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

// Create a new spending budget with the udpated amount.
var newUsageBudget = new SpendingBudget()
{
    Amount = 100
};

// Update the customer's usage budget.
var usageBudget = partnerOperations.Customers.ById(selectedCustomerId).UsageBudget.Get();
```

## <a name="rest-request"></a><span data-ttu-id="eb453-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="eb453-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="eb453-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb453-121">Request syntax</span></span>

| <span data-ttu-id="eb453-122">Método</span><span class="sxs-lookup"><span data-stu-id="eb453-122">Method</span></span>    | <span data-ttu-id="eb453-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="eb453-123">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb453-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="eb453-124">**GET**</span></span> | <span data-ttu-id="eb453-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/usagebudget HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="eb453-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagebudget  HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="eb453-126">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="eb453-126">URI parameter</span></span>

<span data-ttu-id="eb453-127">Utilize o seguinte parâmetro de consulta para atualizar o perfil de faturação.</span><span class="sxs-lookup"><span data-stu-id="eb453-127">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="eb453-128">Nome</span><span class="sxs-lookup"><span data-stu-id="eb453-128">Name</span></span>                   | <span data-ttu-id="eb453-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="eb453-129">Type</span></span>     | <span data-ttu-id="eb453-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="eb453-130">Required</span></span> | <span data-ttu-id="eb453-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb453-131">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb453-132">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="eb453-132">**customer-tenant-id**</span></span> | <span data-ttu-id="eb453-133">**guid**</span><span class="sxs-lookup"><span data-stu-id="eb453-133">**guid**</span></span> | <span data-ttu-id="eb453-134">Y</span><span class="sxs-lookup"><span data-stu-id="eb453-134">Y</span></span>        | <span data-ttu-id="eb453-135">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="eb453-135">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="eb453-136">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="eb453-136">Request headers</span></span>

<span data-ttu-id="eb453-137">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="eb453-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="eb453-138">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="eb453-138">Request body</span></span>

<span data-ttu-id="eb453-139">O recurso completo.</span><span class="sxs-lookup"><span data-stu-id="eb453-139">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="eb453-140">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="eb453-140">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/usagebudget HTTP/1.1
Authorization: Bearer <token>
Accept: application/json, text/plain, */*
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
Content-Type: application/json;charset=utf-8
X-Locale: "en-US"
```

## <a name="rest-response"></a><span data-ttu-id="eb453-141">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="eb453-141">REST response</span></span>

<span data-ttu-id="eb453-142">Se for bem sucedido, este método devolve o orçamento de gastos de um utilizador com o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="eb453-142">If successful, this method returns a user's spending budget with the updated amount.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="eb453-143">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="eb453-143">Response success and error codes</span></span>

<span data-ttu-id="eb453-144">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="eb453-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="eb453-145">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="eb453-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="eb453-146">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="eb453-146">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="eb453-147">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="eb453-147">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 12014
Content-Type: application/json
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
MS-RequestId: be82a8ba-4a53-49f7-8313-b033c058687e
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    {
        "amount": 100,
        "usageSpendingBudget": 100,
        "attributes":{
            "objectType":"SpendingBudget"
        }
    },
    "links":{
        "self":{
            "uri":"/v1/customers/<customer-tenant-id>/usagebudget",
            "method":"GET",
            "headers":[]
        }
    }
}
```
