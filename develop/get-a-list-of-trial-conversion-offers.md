---
title: Obter uma lista de ofertas de conversão de avaliação
description: Como recuperar uma lista de ofertas de conversão experimental.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 981910560faf7b7957b28e643c09a003826b9cff
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873926"
---
# <a name="get-a-list-of-trial-conversion-offers"></a><span data-ttu-id="8740b-103">Obter uma lista de ofertas de conversão de avaliação</span><span class="sxs-lookup"><span data-stu-id="8740b-103">Get a list of trial conversion offers</span></span>

<span data-ttu-id="8740b-104">Como recuperar uma lista de ofertas de conversão experimental.</span><span class="sxs-lookup"><span data-stu-id="8740b-104">How to retrieve a list of trial conversion offers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8740b-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8740b-105">Prerequisites</span></span>

- <span data-ttu-id="8740b-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8740b-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8740b-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="8740b-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="8740b-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8740b-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8740b-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="8740b-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8740b-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="8740b-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8740b-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="8740b-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8740b-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="8740b-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8740b-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8740b-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="8740b-114">Um ID de assinatura para uma subscrição de teste ativo.</span><span class="sxs-lookup"><span data-stu-id="8740b-114">A subscription ID for an active trial subscription.</span></span>

## <a name="c"></a><span data-ttu-id="8740b-115">C\#</span><span class="sxs-lookup"><span data-stu-id="8740b-115">C\#</span></span>

<span data-ttu-id="8740b-116">Para obter uma lista de conversões experimentais disponíveis, comece por utilizar o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="8740b-116">To get a list of trial conversions available, start by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="8740b-117">Em seguida, obtenha uma interface para as operações de subscrição ligando para o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID de subscrição de teste.</span><span class="sxs-lookup"><span data-stu-id="8740b-117">Then, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the trial subscription ID.</span></span> <span data-ttu-id="8740b-118">Em seguida, utilize a propriedade [**Conversões**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) para obter uma interface para as operações disponíveis nas conversões e, em seguida, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) para recuperar uma coleção de ofertas de [**Conversão**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8740b-118">Next, use the [**Conversions**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) property to obtain an interface to the available operations on conversions, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) method to retrieve a collection of available [**Conversion**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) offers.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

// Get the available conversions.
var conversions =
    partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId).Conversions.Get();
```

## <a name="rest-request"></a><span data-ttu-id="8740b-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="8740b-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8740b-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="8740b-120">Request syntax</span></span>

| <span data-ttu-id="8740b-121">Método</span><span class="sxs-lookup"><span data-stu-id="8740b-121">Method</span></span>  | <span data-ttu-id="8740b-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="8740b-122">Request URI</span></span>                                                                                                                 |
|---------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8740b-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="8740b-123">**GET**</span></span> | <span data-ttu-id="8740b-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/conversões HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8740b-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="8740b-125">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="8740b-125">URI parameter</span></span>

<span data-ttu-id="8740b-126">Utilize os seguintes parâmetros de percurso para identificar a subscrição do cliente e do ensaio.</span><span class="sxs-lookup"><span data-stu-id="8740b-126">Use the following path parameters to identify the customer and trial subscription.</span></span>

| <span data-ttu-id="8740b-127">Nome</span><span class="sxs-lookup"><span data-stu-id="8740b-127">Name</span></span>            | <span data-ttu-id="8740b-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="8740b-128">Type</span></span>   | <span data-ttu-id="8740b-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="8740b-129">Required</span></span> | <span data-ttu-id="8740b-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="8740b-130">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="8740b-131">id cliente</span><span class="sxs-lookup"><span data-stu-id="8740b-131">customer-id</span></span>     | <span data-ttu-id="8740b-132">string</span><span class="sxs-lookup"><span data-stu-id="8740b-132">string</span></span> | <span data-ttu-id="8740b-133">Yes</span><span class="sxs-lookup"><span data-stu-id="8740b-133">Yes</span></span>      | <span data-ttu-id="8740b-134">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="8740b-134">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="8740b-135">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="8740b-135">subscription-id</span></span> | <span data-ttu-id="8740b-136">string</span><span class="sxs-lookup"><span data-stu-id="8740b-136">string</span></span> | <span data-ttu-id="8740b-137">Yes</span><span class="sxs-lookup"><span data-stu-id="8740b-137">Yes</span></span>      | <span data-ttu-id="8740b-138">Uma cadeia formatada GUID que identifica a subscrição do ensaio.</span><span class="sxs-lookup"><span data-stu-id="8740b-138">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8740b-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="8740b-139">Request headers</span></span>

<span data-ttu-id="8740b-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8740b-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8740b-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="8740b-141">Request body</span></span>

<span data-ttu-id="8740b-142">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8740b-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="8740b-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="8740b-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638/conversions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e17f5bc6-24bf-4cbe-b632-d7fc6cec3058
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="8740b-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="8740b-144">REST response</span></span>

<span data-ttu-id="8740b-145">Se for bem sucedido, o corpo de resposta contém uma coleção de recursos de [conversão.](conversions-resources.md#conversionresult)</span><span class="sxs-lookup"><span data-stu-id="8740b-145">If successful, the response body contains a collection of [Conversion](conversions-resources.md#conversionresult) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8740b-146">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="8740b-146">Response success and error codes</span></span>

<span data-ttu-id="8740b-147">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="8740b-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8740b-148">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8740b-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8740b-149">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="8740b-149">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8740b-150">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="8740b-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 305
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
MS-RequestId: e17f5bc6-24bf-4cbe-b632-d7fc6cec3058
MS-CV: feJByqU1X0ObaTQr.0
MS-ServerId: 030011719
Date: Thu, 15 Jun 2017 23:10:01 GMT

 {
    "totalCount": 1,
    "items": [{
            "offerId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
            "targetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
            "orderId": "D51A052E-043C-4A2A-AA37-2BB938CEF6C1",
            "quantity": 25,
            "billingCycle": "monthly",
            "attributes": {
                "objectType": "Conversion"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
