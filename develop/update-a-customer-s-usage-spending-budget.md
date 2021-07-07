---
title: Atualizar o orçamento de gastos de utilização de um cliente
description: Atualizar o orçamento de gastos atribuído para a utilização de um cliente.
ms.date: 02/05/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 043bd442266d081105e5e8767b6d597e89fc9e8b
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529720"
---
# <a name="update-a-customers-usage-spending-budget"></a><span data-ttu-id="dff65-103">Atualizar o orçamento de gastos de utilização de um cliente</span><span class="sxs-lookup"><span data-stu-id="dff65-103">Update a customer's usage spending budget</span></span>

<span data-ttu-id="dff65-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="dff65-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="dff65-105">Atualizar o [orçamento de gastos](customer-usage-resources.md#customerusagesummary) atribuído para a utilização de um cliente.</span><span class="sxs-lookup"><span data-stu-id="dff65-105">Update the [spending budget](customer-usage-resources.md#customerusagesummary) allocated for a customer's usage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dff65-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dff65-106">Prerequisites</span></span>

- <span data-ttu-id="dff65-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="dff65-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="dff65-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="dff65-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="dff65-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="dff65-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="dff65-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="dff65-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="dff65-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="dff65-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="dff65-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="dff65-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="dff65-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="dff65-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="dff65-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="dff65-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="dff65-115">C\#</span><span class="sxs-lookup"><span data-stu-id="dff65-115">C\#</span></span>

<span data-ttu-id="dff65-116">Para atualizar o orçamento de gastos de utilização de um cliente, primeiro crie um novo objeto [**SpendBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) com o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="dff65-116">To update a customer's usage spending budget, first create a new [**SpendingBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) object with the updated amount.</span></span> <span data-ttu-id="dff65-117">Em seguida, utilize a recolha [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) e ligue para o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="dff65-117">Then use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer's ID.</span></span> <span data-ttu-id="dff65-118">Em seguida, aceda à propriedade [**UsageBudget**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.usagebudget) e passe o orçamento de utilização atualizado para o método [**Patch()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patch) ou [**PatchAsync().**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patchasync)</span><span class="sxs-lookup"><span data-stu-id="dff65-118">Then access the [**UsageBudget**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.usagebudget) property and pass the updated usage budget to the [**Patch()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patch) or [**PatchAsync()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patchasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

// Create a new spending budget with the udpated amount.
var newUsageBudget = new SpendingBudget()
{
    Amount = 100
};

// Update the customer's usage budget.
var usageBudget = partnerOperations.Customers.ById(selectedCustomerId).UsageBudget.Patch(newUsageBudget);
```

## <a name="rest-request"></a><span data-ttu-id="dff65-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="dff65-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="dff65-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="dff65-120">Request syntax</span></span>

| <span data-ttu-id="dff65-121">Método</span><span class="sxs-lookup"><span data-stu-id="dff65-121">Method</span></span>    | <span data-ttu-id="dff65-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="dff65-122">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="dff65-123">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="dff65-123">**PATCH**</span></span> | <span data-ttu-id="dff65-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/usagebudget HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="dff65-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagebudget  HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="dff65-125">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="dff65-125">URI parameter</span></span>

<span data-ttu-id="dff65-126">Utilize o seguinte parâmetro de consulta para atualizar o perfil de faturação.</span><span class="sxs-lookup"><span data-stu-id="dff65-126">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="dff65-127">Nome</span><span class="sxs-lookup"><span data-stu-id="dff65-127">Name</span></span>                   | <span data-ttu-id="dff65-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="dff65-128">Type</span></span>     | <span data-ttu-id="dff65-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="dff65-129">Required</span></span> | <span data-ttu-id="dff65-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="dff65-130">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="dff65-131">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="dff65-131">**customer-tenant-id**</span></span> | <span data-ttu-id="dff65-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="dff65-132">**guid**</span></span> | <span data-ttu-id="dff65-133">Y</span><span class="sxs-lookup"><span data-stu-id="dff65-133">Y</span></span>        | <span data-ttu-id="dff65-134">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="dff65-134">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="dff65-135">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="dff65-135">Request headers</span></span>

<span data-ttu-id="dff65-136">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="dff65-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="dff65-137">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="dff65-137">Request body</span></span>

<span data-ttu-id="dff65-138">O recurso completo.</span><span class="sxs-lookup"><span data-stu-id="dff65-138">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="dff65-139">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="dff65-139">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/usagebudget HTTP/1.1
Authorization: Bearer <token>
Accept: application/json, text/plain, */*
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
Content-Type: application/json;charset=utf-8
X-Locale: "en-US"

{
     "Amount": 100,
     "Attributes": {
          "ObjectType": "SpendingBudget"
     }
}
```

## <a name="rest-response"></a><span data-ttu-id="dff65-140">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="dff65-140">REST response</span></span>

<span data-ttu-id="dff65-141">Se for bem sucedido, este método devolve o orçamento de gastos de um utilizador com o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="dff65-141">If successful, this method returns a user's spending budget with the updated amount.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="dff65-142">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="dff65-142">Response success and error codes</span></span>

<span data-ttu-id="dff65-143">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="dff65-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="dff65-144">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="dff65-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="dff65-145">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="dff65-145">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="dff65-146">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="dff65-146">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 12014
Content-Type: application/json
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
MS-RequestId: be82a8ba-4a53-49f7-8313-b033c058687e
Date: Tue, 10 Nov 2015 19:09:59 GMT

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
            "method":"PATCH",
            "headers":[]
        }
    }
}
```
