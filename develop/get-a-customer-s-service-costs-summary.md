---
title: Obter resumo dos custos de serviços de um cliente
description: Obtém os custos de serviço de um cliente para o período de faturação especificado.
ms.date: 06/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 635e61342e13c3676120ec0df02f1e8bffda64ac
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769349"
---
# <a name="get-a-customers-service-costs-summary"></a><span data-ttu-id="20ecb-103">Obter resumo dos custos de serviços de um cliente</span><span class="sxs-lookup"><span data-stu-id="20ecb-103">Get a customer's service costs summary</span></span>

<span data-ttu-id="20ecb-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="20ecb-104">**Applies to:**</span></span>

- <span data-ttu-id="20ecb-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="20ecb-105">Partner Center</span></span>

<span data-ttu-id="20ecb-106">Obtém os custos de serviço de um cliente para o período de faturação especificado.</span><span class="sxs-lookup"><span data-stu-id="20ecb-106">Gets a customer's service costs for the specified billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="20ecb-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="20ecb-107">Prerequisites</span></span>

- <span data-ttu-id="20ecb-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="20ecb-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="20ecb-109">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="20ecb-109">This scenario supports authentication with App+User credentials.</span></span>

- <span data-ttu-id="20ecb-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="20ecb-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="20ecb-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="20ecb-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="20ecb-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="20ecb-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="20ecb-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="20ecb-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="20ecb-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="20ecb-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="20ecb-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="20ecb-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="20ecb-116">Um indicador do período de faturação **`mostrecent`** ().</span><span class="sxs-lookup"><span data-stu-id="20ecb-116">A billing period indicator (**`mostrecent`**).</span></span>

## <a name="c"></a><span data-ttu-id="20ecb-117">C\#</span><span class="sxs-lookup"><span data-stu-id="20ecb-117">C\#</span></span>

<span data-ttu-id="20ecb-118">Para recuperar um resumo dos custos de serviço para o cliente especificado:</span><span class="sxs-lookup"><span data-stu-id="20ecb-118">To retrieve a service costs summary for the specified customer:</span></span>

1. <span data-ttu-id="20ecb-119">Ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="20ecb-119">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="20ecb-120">Utilize a propriedade [**ServiceCosts**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) para obter uma interface para as operações de recolha de custos de atendimento ao cliente.</span><span class="sxs-lookup"><span data-stu-id="20ecb-120">Use the [**ServiceCosts**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) property to get an interface to customer service costs collection operations.</span></span>

3. <span data-ttu-id="20ecb-121">Ligue para o método [**ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) com um membro da enumeração [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) para devolver uma [**IServiceCostsCollection**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection).</span><span class="sxs-lookup"><span data-stu-id="20ecb-121">Call the [**ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) method with a member of the [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) enumeration to return an [**IServiceCostsCollection**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection).</span></span>

4. <span data-ttu-id="20ecb-122">Utilize o método [**IServiceCostsCollection.Summary.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.getasync) para obter o resumo dos custos de serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="20ecb-122">Use the [**IServiceCostsCollection.Summary.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.getasync) method to get the customer's service costs summary.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var serviceCostsSummary = partnerOperations.Customers.ById(selectedCustomerId).ServiceCosts.ByBillingPeriod(ServiceCostsBillingPeriod.MostRecent).Summary.Get();
```

## <a name="rest-request"></a><span data-ttu-id="20ecb-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="20ecb-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="20ecb-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="20ecb-124">Request syntax</span></span>

| <span data-ttu-id="20ecb-125">Método</span><span class="sxs-lookup"><span data-stu-id="20ecb-125">Method</span></span>  | <span data-ttu-id="20ecb-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="20ecb-126">Request URI</span></span>                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="20ecb-127">**Obter**</span><span class="sxs-lookup"><span data-stu-id="20ecb-127">**GET**</span></span> | <span data-ttu-id="20ecb-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/servicecosts/{billing-period} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="20ecb-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/servicecosts/{billing-period} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="20ecb-129">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="20ecb-129">URI parameters</span></span>

<span data-ttu-id="20ecb-130">Utilize os seguintes parâmetros de trajeto para identificar o cliente e o período de faturação.</span><span class="sxs-lookup"><span data-stu-id="20ecb-130">Use the following path parameters to identify the customer and the billing period.</span></span>

| <span data-ttu-id="20ecb-131">Nome</span><span class="sxs-lookup"><span data-stu-id="20ecb-131">Name</span></span>           | <span data-ttu-id="20ecb-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="20ecb-132">Type</span></span>   | <span data-ttu-id="20ecb-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="20ecb-133">Required</span></span> | <span data-ttu-id="20ecb-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="20ecb-134">Description</span></span>                                                                                                                      |
|----------------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="20ecb-135">id cliente</span><span class="sxs-lookup"><span data-stu-id="20ecb-135">customer-id</span></span>    | <span data-ttu-id="20ecb-136">guid</span><span class="sxs-lookup"><span data-stu-id="20ecb-136">guid</span></span>   | <span data-ttu-id="20ecb-137">Sim</span><span class="sxs-lookup"><span data-stu-id="20ecb-137">Yes</span></span>      | <span data-ttu-id="20ecb-138">Um ID de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="20ecb-138">A GUID formatted customer ID that identifies the customer.</span></span>                                                                       |
| <span data-ttu-id="20ecb-139">período de faturação</span><span class="sxs-lookup"><span data-stu-id="20ecb-139">billing-period</span></span> | <span data-ttu-id="20ecb-140">string</span><span class="sxs-lookup"><span data-stu-id="20ecb-140">string</span></span> | <span data-ttu-id="20ecb-141">Sim</span><span class="sxs-lookup"><span data-stu-id="20ecb-141">Yes</span></span>      | <span data-ttu-id="20ecb-142">Um indicador que representa o período de faturação.</span><span class="sxs-lookup"><span data-stu-id="20ecb-142">An indicator that represents the billing period.</span></span> <span data-ttu-id="20ecb-143">O único valor suportado é o MostRecent.</span><span class="sxs-lookup"><span data-stu-id="20ecb-143">The only supported value is MostRecent.</span></span> <span data-ttu-id="20ecb-144">O caso da corda não importa.</span><span class="sxs-lookup"><span data-stu-id="20ecb-144">The case of the string does not matter.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="20ecb-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="20ecb-145">Request headers</span></span>

<span data-ttu-id="20ecb-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="20ecb-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="20ecb-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="20ecb-147">Request body</span></span>

<span data-ttu-id="20ecb-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="20ecb-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="20ecb-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="20ecb-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65726577-c208-40fd-9735-8c85ac9cac68/servicecosts/mostrecent HTTP/1.1
Authorization: Bearer <authorization token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="20ecb-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="20ecb-150">REST response</span></span>

<span data-ttu-id="20ecb-151">Se for bem sucedido, o organismo de resposta contém um recurso [ServiceCostsSummary](service-costs-resources.md) que fornece informações sobre os custos de serviço.</span><span class="sxs-lookup"><span data-stu-id="20ecb-151">If successful, the response body contains a [ServiceCostsSummary](service-costs-resources.md) resource that provides information about the service costs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="20ecb-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="20ecb-152">Response success and error codes</span></span>

<span data-ttu-id="20ecb-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="20ecb-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="20ecb-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="20ecb-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="20ecb-155">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="20ecb-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="20ecb-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="20ecb-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 766
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CV: gPPoyNX1X0asAAcw.0
MS-ServerId: 101112202
Date: Fri, 02 Dec 2016 18: 54: 38 GMT

{
    "billingStartDate": "2015-12-12T00:00:00Z",
    "billingEndDate": "2016-01-11T00:00:00Z",
    "pretaxTotal": 17.22,
    "tax": 0.0,
    "afterTaxTotal": 17.22,
    "currencySymbol": "$",
    "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
    "details":
     [
        {
            "invoiceType": "Recurring",
            "summary": {
                "billingStartDate": "2015-12-12T00:00:00Z",
                "billingEndDate": "2016-01-11T00:00:00Z",
                "pretaxTotal": 17.22,
                "tax": 0.0,
                "afterTaxTotal": 17.22,
                "currencyCode": "USD",
                "currencySymbol": "$",
                "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
                "links": {},
                "attributes": {
                    "objectType": "ServiceCostsSummary"
                }
            }
        },
        {
            "invoiceType": "OneTime",
            "summary": {
                "billingStartDate": "2019-04-01T00:00:00Z",
                "billingEndDate": "2019-04-30T23:59:59.9999999Z",
                "pretaxTotal": 2,
                "tax": 0.2,
                "afterTaxTotal": 2.2,
                "currencyCode": "USD",
                "currencySymbol": "$",
                "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
                "links": {},
                "attributes": {
                    "objectType": "ServiceCostsSummary"
                }
            }
        }
    ],
    "links": {
        "serviceCostLineItems": {
            "uri": "/customers/ae1d5b32-f9ff-4252-b2bf-40e21937a51a/servicecosts/MostRecent/lineitems",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/ae1d5b32-f9ff-4252-b2bf-40e21937a51a/servicecosts/MostRecent",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "ServiceCostsSummary"
    }
}
```
