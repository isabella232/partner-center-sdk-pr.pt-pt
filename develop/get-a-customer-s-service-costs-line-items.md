---
title: Obter itens de linha dos custos de serviços de um cliente
description: Obtém itens de linha de custo de serviço do cliente para o período de faturação especificado.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1bc2914d7c8d41c6d806131444fdc241aa1feb90
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874946"
---
# <a name="get-a-customers-service-costs-line-items"></a><span data-ttu-id="9e759-103">Obter itens de linha dos custos de serviços de um cliente</span><span class="sxs-lookup"><span data-stu-id="9e759-103">Get a customer's service costs line items</span></span>

<span data-ttu-id="9e759-104">Obtém itens de linha de custo de serviço do cliente para o período de faturação especificado.</span><span class="sxs-lookup"><span data-stu-id="9e759-104">Gets a customer's service cost line items for the specified billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e759-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9e759-105">Prerequisites</span></span>

- <span data-ttu-id="9e759-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9e759-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9e759-107">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="9e759-107">This scenario supports authentication with App+User credentials.</span></span>

- <span data-ttu-id="9e759-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9e759-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="9e759-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="9e759-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="9e759-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="9e759-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="9e759-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="9e759-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="9e759-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="9e759-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="9e759-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9e759-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="9e759-114">Um indicador do período de faturação **`mostrecent`** ().</span><span class="sxs-lookup"><span data-stu-id="9e759-114">A billing period indicator (**`mostrecent`**).</span></span>

## <a name="c"></a><span data-ttu-id="9e759-115">C\#</span><span class="sxs-lookup"><span data-stu-id="9e759-115">C\#</span></span>

<span data-ttu-id="9e759-116">Para recuperar um resumo dos custos de serviço para o cliente especificado:</span><span class="sxs-lookup"><span data-stu-id="9e759-116">To retrieve a service costs summary for the specified customer:</span></span>

1. <span data-ttu-id="9e759-117">Ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="9e759-117">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="9e759-118">Utilize a propriedade [**ServiceCosts**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) para obter uma interface para as operações de recolha de custos de atendimento ao cliente.</span><span class="sxs-lookup"><span data-stu-id="9e759-118">Use the [**ServiceCosts**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) property to get an interface to customer service costs collection operations.</span></span>

3. <span data-ttu-id="9e759-119">Ligue para o método [**ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) com um membro da enumeração [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) para devolver uma [**IServiceCostsCollection**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection).</span><span class="sxs-lookup"><span data-stu-id="9e759-119">Call the [**ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) method with a member of the [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) enumeration to return an [**IServiceCostsCollection**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection).</span></span>

4. <span data-ttu-id="9e759-120">Utilize o método [**IServiceCostsCollection.LineItems.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.getasync) para obter os itens de linha de custos de serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="9e759-120">Use the [**IServiceCostsCollection.LineItems.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.getasync) method to get the customer's service costs line items.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var serviceCostsSummary = partnerOperations.Customers.ById(selectedCustomerId).ServiceCosts.ByBillingPeriod(ServiceCostsBillingPeriod.MostRecent).LineItems.Get();
```

## <a name="rest-request"></a><span data-ttu-id="9e759-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="9e759-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9e759-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e759-122">Request syntax</span></span>

| <span data-ttu-id="9e759-123">Método</span><span class="sxs-lookup"><span data-stu-id="9e759-123">Method</span></span>  | <span data-ttu-id="9e759-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="9e759-124">Request URI</span></span>                                                                                                             |
|---------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9e759-125">**Obter**</span><span class="sxs-lookup"><span data-stu-id="9e759-125">**GET**</span></span> | <span data-ttu-id="9e759-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/servicecosts/{billing-period}/lineitems HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9e759-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/servicecosts/{billing-period}/lineitems HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="9e759-127">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="9e759-127">URI parameters</span></span>

<span data-ttu-id="9e759-128">Utilize os seguintes parâmetros de trajeto para identificar o cliente e o período de faturação.</span><span class="sxs-lookup"><span data-stu-id="9e759-128">Use the following path parameters to identify the customer and the billing period.</span></span>

| <span data-ttu-id="9e759-129">Nome</span><span class="sxs-lookup"><span data-stu-id="9e759-129">Name</span></span>           | <span data-ttu-id="9e759-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="9e759-130">Type</span></span>   | <span data-ttu-id="9e759-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="9e759-131">Required</span></span> | <span data-ttu-id="9e759-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e759-132">Description</span></span>                                                                                                                      |
|----------------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9e759-133">id cliente</span><span class="sxs-lookup"><span data-stu-id="9e759-133">customer-id</span></span>    | <span data-ttu-id="9e759-134">guid</span><span class="sxs-lookup"><span data-stu-id="9e759-134">guid</span></span>   | <span data-ttu-id="9e759-135">Yes</span><span class="sxs-lookup"><span data-stu-id="9e759-135">Yes</span></span>      | <span data-ttu-id="9e759-136">Um ID de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="9e759-136">A GUID formatted customer ID that identifies the customer.</span></span>                                                                       |
| <span data-ttu-id="9e759-137">período de faturação</span><span class="sxs-lookup"><span data-stu-id="9e759-137">billing-period</span></span> | <span data-ttu-id="9e759-138">string</span><span class="sxs-lookup"><span data-stu-id="9e759-138">string</span></span> | <span data-ttu-id="9e759-139">Yes</span><span class="sxs-lookup"><span data-stu-id="9e759-139">Yes</span></span>      | <span data-ttu-id="9e759-140">Um indicador que representa o período de faturação.</span><span class="sxs-lookup"><span data-stu-id="9e759-140">An indicator that represents the billing period.</span></span> <span data-ttu-id="9e759-141">O único valor suportado é o MostRecent.</span><span class="sxs-lookup"><span data-stu-id="9e759-141">The only supported value is MostRecent.</span></span> <span data-ttu-id="9e759-142">O caso da corda não importa.</span><span class="sxs-lookup"><span data-stu-id="9e759-142">The case of the string does not matter.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9e759-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="9e759-143">Request headers</span></span>

<span data-ttu-id="9e759-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9e759-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9e759-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="9e759-145">Request body</span></span>

<span data-ttu-id="9e759-146">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9e759-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9e759-147">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="9e759-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65726577-c208-40fd-9735-8c85ac9cac68/servicecosts/mostrecent/lineitems HTTP/1.1
Authorization: Bearer <authorization token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="9e759-148">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="9e759-148">REST response</span></span>

<span data-ttu-id="9e759-149">Se for bem sucedido, o organismo de resposta contém um recurso [ServiceCostLineItem](service-costs-resources.md) que fornece informações sobre os custos de serviço.</span><span class="sxs-lookup"><span data-stu-id="9e759-149">If successful, the response body contains a [ServiceCostLineItem](service-costs-resources.md) resource that provides information about the service costs.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e759-150">As seguintes propriedades *aplicam-se apenas aos* itens da linha de custos de serviço em que o produto é uma *compra única*: **produtoId**, **produtoName,** **skuId,** **skuName,** **availabilityId,** **publisherId,** **publisherName,** **termAndBillingCycle,** **discountDetails**.</span><span class="sxs-lookup"><span data-stu-id="9e759-150">The following properties *only apply to* service cost line items where the product is a *one-time purchase*: **productId**, **productName**, **skuId**, **skuName**, **availabilityId**, **publisherId**, **publisherName**, **termAndBillingCycle**, **discountDetails**.</span></span> <span data-ttu-id="9e759-151">Estas propriedades *não se aplicam a* itens de linha de serviço onde o produto é uma compra *recorrente.*</span><span class="sxs-lookup"><span data-stu-id="9e759-151">These properties *don't apply to* service line items where the product is a *recurring purchase*.</span></span> <span data-ttu-id="9e759-152">Por exemplo, estas propriedades *não se aplicam* a Office 365 e Azure baseados em subscrições.</span><span class="sxs-lookup"><span data-stu-id="9e759-152">For example, these properties *don't apply* to subscription-based Office 365 and Azure.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9e759-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="9e759-153">Response success and error codes</span></span>

<span data-ttu-id="9e759-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="9e759-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9e759-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="9e759-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9e759-156">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="9e759-156">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9e759-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="9e759-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2148
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CV: gPPoyNX1X0asAAcw.0
MS-ServerId: 101112202
Date: Fri, 02 Dec 2016 18: 54: 38 GMT

{
    "attributes": {
        "objectType": "Collection"
    },
    "items":
    [{
            "afterTaxTotal": 0.0,
            "chargeType": "PURCHASE FEE",
            "currencyCode": "USD",
            "currencySymbol": "$",
            "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
            "customerName": "AABB CCDD",
            "endDate": "2016-01-11T00:00:00",
            "offerId": "11E3C9A9-24A2-4CFD-9F60-A9797D68E296",
            "offerName": "Project for Office 365 (Government Pricing)",
            "orderId": "4FEB262A-FAF3-4710-B216-D563421B006F",
            "pretaxTotal": 0.0,
            "quantity": 1.0,
            "resellerMPNId": "-1",
            "startDate": "2015-12-15T00:00:00",
            "subscriptionFriendlyName": "Project Pro for Office 365 (Government Pricing)",
            "subscriptionId": "71B5BCDD-51C8-4BF2-B704-D3432EE33064",
            "tax": 0.0,
            "unitPrice": 0.0,
            "invoiceNumber": "T000003163",
            "invoiceType": "OneTime",
            "productId": "DZH318Z0BJR6",
            "skuId": "0001",
            "availabilityId": "DZH318Z0BMFK",
            "productName": "Azure Managed Experience",
            "skuName": "Azure Managed Experience - Optimize",
            "publisherName": "Microsoft",
            "publisherId": "01323244",
            "termAndBillingCycle": "",
            "discountDetails": "N/A"
        }, {
            "afterTaxTotal": 17.219999999999999,
            "chargeType": "CYCLE FEE",
            "currencyCode": "USD",
            "currencySymbol": "$",
            "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
            "customerName": "AABB CCDD",
            "endDate": "2016-02-11T00:00:00",
            "offerId": "11E3C9A9-24A2-4CFD-9F60-A9797D68E296",
            "offerName": "Project for Office 365 (Government Pricing)",
            "orderId": "4FEB262A-FAF3-4710-B216-D563421B006F",
            "pretaxTotal": 17.219999999999999,
            "quantity": 1.0,
            "resellerMPNId": "-1",
            "startDate": "2016-01-12T00:00:00",
            "subscriptionFriendlyName": "Project Pro for Office 365 (Government Pricing)",
            "subscriptionId": "71B5BCDD-51C8-4BF2-B704-D3432EE33064",
            "tax": 0.0,
            "unitPrice": 17.219999999999999,
            "invoiceNumber": "D000003163",
            "invoiceType": "Recurring",
            "productId": "DZH318Z0BJR7",
            "skuId": "0001",
            "availabilityId": "DZH318Z0BTTTT",
            "productName": "NGINX Plus",
            "skuName": "NGINX Plus (Ubuntu 14.04)",
            "publisherName": "Nginx, Inc.",
            "publisherId": "212336222",
            "termAndBillingCycle": "30 Days Trial",
            "discountDetails": "20%"
        }
    ],
    "links": {
        "self": {
            "headers": [],
            "method": "GET",
            "uri": "/customers/ae1d5b32-f9ff-4252-b2bf-40e21937a51a/servicecosts/MostRecent/lineitems"
        }
    },
    "totalCount": 2
}
```
