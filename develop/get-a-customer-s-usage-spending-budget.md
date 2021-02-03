---
title: Obtenha o orçamento de gastos de uso de um cliente
description: Pode utilizar um orçamento de gastos (o objeto SpendBudget) para atualizar um resumo de utilização do cliente (o recurso CustomerUsageSummary).
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8be9ceaab6b7546de8eacba1e52e8766719e5125
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769344"
---
# <a name="get-a-customers-usage-spending-budget"></a><span data-ttu-id="2953d-103">Obtenha o orçamento de gastos de uso de um cliente</span><span class="sxs-lookup"><span data-stu-id="2953d-103">Get a customer's usage spending budget</span></span>

<span data-ttu-id="2953d-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="2953d-104">**Applies to:**</span></span>

- <span data-ttu-id="2953d-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="2953d-105">Partner Center</span></span>
- <span data-ttu-id="2953d-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="2953d-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="2953d-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2953d-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2953d-108">Pode atualizar o orçamento de gastos (o objeto **SpendBudget)** no resumo de utilização do [cliente (o recurso **CustomerUsageSummary)**](customer-usage-resources.md#customerusagesummary).</span><span class="sxs-lookup"><span data-stu-id="2953d-108">You can update the spending budget (the **SpendingBudget** object) in the [customer usage summary (the **CustomerUsageSummary** resource)](customer-usage-resources.md#customerusagesummary).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2953d-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2953d-109">Prerequisites</span></span>

- <span data-ttu-id="2953d-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2953d-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2953d-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="2953d-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="2953d-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2953d-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="2953d-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="2953d-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="2953d-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="2953d-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="2953d-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="2953d-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="2953d-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="2953d-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="2953d-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2953d-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="2953d-118">C\#</span><span class="sxs-lookup"><span data-stu-id="2953d-118">C\#</span></span>

<span data-ttu-id="2953d-119">Para atualizar o orçamento de gastos de utilização de um cliente:</span><span class="sxs-lookup"><span data-stu-id="2953d-119">To update a customer's usage spending budget:</span></span>

1. <span data-ttu-id="2953d-120">Crie um novo objeto [**Spendbudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) com o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="2953d-120">Create a new [**SpendingBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) object with the updated amount.</span></span>

2. <span data-ttu-id="2953d-121">Utilize a coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) para ligar para o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="2953d-121">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) collection to call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer's identifier.</span></span>

3. <span data-ttu-id="2953d-122">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) para obter o orçamento de utilização do cliente.</span><span class="sxs-lookup"><span data-stu-id="2953d-122">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to get the customer's usage budget.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="2953d-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2953d-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2953d-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2953d-124">Request syntax</span></span>

| <span data-ttu-id="2953d-125">Método</span><span class="sxs-lookup"><span data-stu-id="2953d-125">Method</span></span>    | <span data-ttu-id="2953d-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2953d-126">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2953d-127">**Obter**</span><span class="sxs-lookup"><span data-stu-id="2953d-127">**GET**</span></span> | <span data-ttu-id="2953d-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/usagebudget HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2953d-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagebudget  HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="2953d-129">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="2953d-129">URI parameter</span></span>

<span data-ttu-id="2953d-130">Utilize o seguinte parâmetro de consulta para atualizar o perfil de faturação.</span><span class="sxs-lookup"><span data-stu-id="2953d-130">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="2953d-131">Nome</span><span class="sxs-lookup"><span data-stu-id="2953d-131">Name</span></span>                   | <span data-ttu-id="2953d-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="2953d-132">Type</span></span>     | <span data-ttu-id="2953d-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="2953d-133">Required</span></span> | <span data-ttu-id="2953d-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="2953d-134">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2953d-135">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="2953d-135">**customer-tenant-id**</span></span> | <span data-ttu-id="2953d-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="2953d-136">**guid**</span></span> | <span data-ttu-id="2953d-137">Y</span><span class="sxs-lookup"><span data-stu-id="2953d-137">Y</span></span>        | <span data-ttu-id="2953d-138">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="2953d-138">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2953d-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2953d-139">Request headers</span></span>

<span data-ttu-id="2953d-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2953d-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2953d-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="2953d-141">Request body</span></span>

<span data-ttu-id="2953d-142">O recurso completo.</span><span class="sxs-lookup"><span data-stu-id="2953d-142">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="2953d-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="2953d-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/usagebudget HTTP/1.1
Authorization: Bearer <token>
Accept: application/json, text/plain, */*
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
Content-Type: application/json;charset=utf-8
X-Locale: "en-US"
```

## <a name="rest-response"></a><span data-ttu-id="2953d-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2953d-144">REST response</span></span>

<span data-ttu-id="2953d-145">Se for bem sucedido, este método devolve o orçamento de gastos de um utilizador com o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="2953d-145">If successful, this method returns a user's spending budget with the updated amount.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2953d-146">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2953d-146">Response success and error codes</span></span>

<span data-ttu-id="2953d-147">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2953d-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2953d-148">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2953d-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2953d-149">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2953d-149">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2953d-150">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="2953d-150">Response example</span></span>

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
