---
title: Converter uma subscrição de avaliação em paga
description: Saiba como usar as APIs do Partner Center para converter uma subscrição de teste para uma paga.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 59dcf6caf21d407b2fba4cc8438bc435fda9dc77
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770064"
---
# <a name="convert-a-trial-subscription-to-paid-using-partner-center-apis"></a><span data-ttu-id="71eb4-103">Converter uma subscrição experimental para pago usando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="71eb4-103">Convert a trial subscription to paid using Partner Center APIs</span></span>

<span data-ttu-id="71eb4-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="71eb4-104">**Applies to:**</span></span>

- <span data-ttu-id="71eb4-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="71eb4-105">Partner Center</span></span>

<span data-ttu-id="71eb4-106">Pode converter uma subscrição experimental a pagar.</span><span class="sxs-lookup"><span data-stu-id="71eb4-106">You can convert a trial subscription to paid.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="71eb4-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="71eb4-107">Prerequisites</span></span>

- <span data-ttu-id="71eb4-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="71eb4-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="71eb4-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="71eb4-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="71eb4-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="71eb4-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="71eb4-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="71eb4-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="71eb4-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="71eb4-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="71eb4-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="71eb4-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="71eb4-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="71eb4-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="71eb4-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="71eb4-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="71eb4-116">Um ID de assinatura para uma subscrição de teste ativo.</span><span class="sxs-lookup"><span data-stu-id="71eb4-116">A subscription ID for an active trial subscription.</span></span>

- <span data-ttu-id="71eb4-117">Uma oferta de conversão disponível.</span><span class="sxs-lookup"><span data-stu-id="71eb4-117">An available conversion offer.</span></span>

## <a name="convert-a-trial-subscription-to-paid-through-code"></a><span data-ttu-id="71eb4-118">Converter uma subscrição experimental para ser pago através do código</span><span class="sxs-lookup"><span data-stu-id="71eb4-118">Convert a trial subscription to paid through code</span></span>

<span data-ttu-id="71eb4-119">Para converter uma subscrição experimental para uma paga, você deve primeiro obter uma coleção das conversões de ensaio disponíveis.</span><span class="sxs-lookup"><span data-stu-id="71eb4-119">To convert a trial subscription to a paid one, you must first obtain a collection of the trial conversions available.</span></span> <span data-ttu-id="71eb4-120">Em seguida, deve escolher a oferta de conversão que pretende comprar.</span><span class="sxs-lookup"><span data-stu-id="71eb4-120">Then, you must choose the conversion offer that you want to purchase.</span></span>

<span data-ttu-id="71eb4-121">As ofertas de conversão especificarão uma quantidade que predefinirá ao mesmo número de licenças que a subscrição do ensaio.</span><span class="sxs-lookup"><span data-stu-id="71eb4-121">The conversion offers will specify a quantity that defaults to the same number of licenses as the trial subscription.</span></span> <span data-ttu-id="71eb4-122">Pode alterar esta quantidade definindo a propriedade [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion.quantity) para o número de licenças que pretende adquirir.</span><span class="sxs-lookup"><span data-stu-id="71eb4-122">You can change this quantity by setting the [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion.quantity) property to the number of licenses that you want to purchase.</span></span>

> [!NOTE]
> <span data-ttu-id="71eb4-123">Independentemente do número de licenças adquiridas, o ID de assinatura do ensaio é reutilizado para as licenças adquiridas.</span><span class="sxs-lookup"><span data-stu-id="71eb4-123">Regardless of the number of licenses purchased, the subscription ID of the trial is reused for the purchased licenses.</span></span> <span data-ttu-id="71eb4-124">Como resultado, o julgamento em vigor desaparece e é substituído pela compra.</span><span class="sxs-lookup"><span data-stu-id="71eb4-124">As a result, the trial in effect disappears and is replaced by the purchase.</span></span>

<span data-ttu-id="71eb4-125">Utilize os seguintes passos para converter uma subscrição experimental através de código:</span><span class="sxs-lookup"><span data-stu-id="71eb4-125">Use the following steps to convert a trial subscription through code:</span></span>

1. <span data-ttu-id="71eb4-126">Obtenha uma interface para as operações de subscrição disponíveis.</span><span class="sxs-lookup"><span data-stu-id="71eb4-126">Get an interface to the subscription operations available.</span></span> <span data-ttu-id="71eb4-127">Deve identificar o cliente e especificar o identificador de subscrição da subscrição do ensaio.</span><span class="sxs-lookup"><span data-stu-id="71eb4-127">You must identify the customer and specify the subscription identifier of the trial subscription.</span></span>

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2. <span data-ttu-id="71eb4-128">Obtenha uma coleção das ofertas de conversão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="71eb4-128">Get a collection of the available conversion offers.</span></span> <span data-ttu-id="71eb4-129">Para obter mais informações e detalhes sobre o pedido/resposta para este método, consulte [obter uma lista de ofertas de conversão experimental](get-a-list-of-trial-conversion-offers.md).</span><span class="sxs-lookup"><span data-stu-id="71eb4-129">For more information and details on the request/response for this method, see [Get a list of trial conversion offers](get-a-list-of-trial-conversion-offers.md).</span></span>

    ``` csharp
    var conversions = subscriptionOperations.Conversions.Get();
    ```

3. <span data-ttu-id="71eb4-130">Escolha uma oferta de conversão.</span><span class="sxs-lookup"><span data-stu-id="71eb4-130">Choose a conversion offer.</span></span> <span data-ttu-id="71eb4-131">O código seguinte escolhe a primeira oferta de conversão na coleção.</span><span class="sxs-lookup"><span data-stu-id="71eb4-131">The following code chooses the first conversion offer in the collection.</span></span>

    ``` csharp
    var selectedConversion = conversions.Items.ToList()[0];
    ```

4. <span data-ttu-id="71eb4-132">Opcionalmente, especifique o número de licenças para comprar.</span><span class="sxs-lookup"><span data-stu-id="71eb4-132">Optionally, specify the number of licenses to purchase.</span></span> <span data-ttu-id="71eb4-133">O padrão é o número de licenças na subscrição de ensaio.</span><span class="sxs-lookup"><span data-stu-id="71eb4-133">The default is the number of licenses in the trial subscription.</span></span>

    ``` csharp
    selectedConversion.Quantity = 10;
    ```

5. <span data-ttu-id="71eb4-134">Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) ou [**CriarAync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) para converter a subscrição experimental a ser paga.</span><span class="sxs-lookup"><span data-stu-id="71eb4-134">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) method to convert the trial subscription to paid.</span></span>

    ``` csharp
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
    ```

## <a name="c"></a><span data-ttu-id="71eb4-135">C\#</span><span class="sxs-lookup"><span data-stu-id="71eb4-135">C\#</span></span>

<span data-ttu-id="71eb4-136">Para converter uma subscrição experimental para uma paga:</span><span class="sxs-lookup"><span data-stu-id="71eb4-136">To convert a trial subscription to a paid one:</span></span>

1. <span data-ttu-id="71eb4-137">Utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="71eb4-137">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="71eb4-138">Obtenha uma interface para as operações de subscrição ligando para o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID de subscrição de teste.</span><span class="sxs-lookup"><span data-stu-id="71eb4-138">Get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the trial subscription ID.</span></span> <span data-ttu-id="71eb4-139">Guarde uma referência à interface de operações de subscrição numa variável local.</span><span class="sxs-lookup"><span data-stu-id="71eb4-139">Save a reference to the subscription operations interface in a local variable.</span></span>

3. <span data-ttu-id="71eb4-140">Utilize a propriedade [**Conversões**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) para obter uma interface para as operações disponíveis nas conversões e, em seguida, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) para recuperar uma coleção de ofertas de [**Conversão**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) disponíveis.</span><span class="sxs-lookup"><span data-stu-id="71eb4-140">Use the [**Conversions**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) property to obtain an interface to the available operations on conversions, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) method to retrieve a collection of available [**Conversion**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) offers.</span></span> <span data-ttu-id="71eb4-141">Tem de escolher um.</span><span class="sxs-lookup"><span data-stu-id="71eb4-141">You must choose one.</span></span> <span data-ttu-id="71eb4-142">O exemplo a seguir é o desresponsa da primeira conversão disponível.</span><span class="sxs-lookup"><span data-stu-id="71eb4-142">The following example defaults to the first conversion available.</span></span>

4. <span data-ttu-id="71eb4-143">Utilize a referência à interface de operações de subscrição que guardou numa variável local e na propriedade [**Conversões**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) para obter uma interface para as operações disponíveis nas conversões.</span><span class="sxs-lookup"><span data-stu-id="71eb4-143">Use the reference to the subscription operations interface that you saved in a local variable and the [**Conversions**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) property to obtain an interface to the available operations on conversions.</span></span>

5. <span data-ttu-id="71eb4-144">Passe o objeto de oferta de conversão selecionado para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) ou [**CriarAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) para tentar a conversão experimental.</span><span class="sxs-lookup"><span data-stu-id="71eb4-144">Pass the selected conversion offer object to the [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) method to attempt the trial conversion.</span></span>

### <a name="c-example"></a><span data-ttu-id="71eb4-145">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="71eb4-145">C\# example</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

// Get subscription operations for the trial subscription.
var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);

// Get the available conversions.
var conversions = subscriptionOperations.Conversions.Get();

// If there are no conversions available, we&#39;re done.
// Otherwise, convert the trial to the first available conversion offer.
if (conversions.TotalCount <= 0)
{
    System.Console.WriteLine("This subscription has no conversions");
}
else
{
    // Default to the first conversion.
    var selectedConversion = conversions.Items.ToList()[0];

    // Convert the trial and return the result.
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
}
```

## <a name="rest-request"></a><span data-ttu-id="71eb4-146">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="71eb4-146">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="71eb4-147">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="71eb4-147">Request syntax</span></span>

| <span data-ttu-id="71eb4-148">Método</span><span class="sxs-lookup"><span data-stu-id="71eb4-148">Method</span></span>   | <span data-ttu-id="71eb4-149">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="71eb4-149">Request URI</span></span>                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="71eb4-150">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="71eb4-150">**POST**</span></span> | <span data-ttu-id="71eb4-151">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/conversões HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="71eb4-151">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="71eb4-152">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="71eb4-152">URI parameter</span></span>

<span data-ttu-id="71eb4-153">Utilize os seguintes parâmetros de percurso para identificar a subscrição do cliente e do ensaio.</span><span class="sxs-lookup"><span data-stu-id="71eb4-153">Use the following path parameters to identify the customer and trial subscription.</span></span>

| <span data-ttu-id="71eb4-154">Nome</span><span class="sxs-lookup"><span data-stu-id="71eb4-154">Name</span></span>            | <span data-ttu-id="71eb4-155">Tipo</span><span class="sxs-lookup"><span data-stu-id="71eb4-155">Type</span></span>   | <span data-ttu-id="71eb4-156">Necessário</span><span class="sxs-lookup"><span data-stu-id="71eb4-156">Required</span></span> | <span data-ttu-id="71eb4-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="71eb4-157">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="71eb4-158">id cliente</span><span class="sxs-lookup"><span data-stu-id="71eb4-158">customer-id</span></span>     | <span data-ttu-id="71eb4-159">string</span><span class="sxs-lookup"><span data-stu-id="71eb4-159">string</span></span> | <span data-ttu-id="71eb4-160">Sim</span><span class="sxs-lookup"><span data-stu-id="71eb4-160">Yes</span></span>      | <span data-ttu-id="71eb4-161">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="71eb4-161">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="71eb4-162">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="71eb4-162">subscription-id</span></span> | <span data-ttu-id="71eb4-163">string</span><span class="sxs-lookup"><span data-stu-id="71eb4-163">string</span></span> | <span data-ttu-id="71eb4-164">Sim</span><span class="sxs-lookup"><span data-stu-id="71eb4-164">Yes</span></span>      | <span data-ttu-id="71eb4-165">Uma cadeia formatada GUID que identifica a subscrição do ensaio.</span><span class="sxs-lookup"><span data-stu-id="71eb4-165">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="71eb4-166">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="71eb4-166">Request headers</span></span>

<span data-ttu-id="71eb4-167">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="71eb4-167">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="71eb4-168">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="71eb4-168">Request body</span></span>

<span data-ttu-id="71eb4-169">Um recurso de [conversão](conversions-resources.md#conversion) povoado deve ser incluído no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="71eb4-169">A populated [Conversion](conversions-resources.md#conversion) resource must be included in the request body.</span></span>

### <a name="request-example"></a><span data-ttu-id="71eb4-170">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="71eb4-170">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638/conversions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bd0cde7f-ba87-4010-8a73-1190b641f2a4
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 234
Expect: 100-continue

{
    "OfferId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
    "TargetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "OrderId": "D51A052E-043C-4A2A-AA37-2BB938CEF6C1",
    "Quantity": 25,
    "BillingCycle": "monthly",
    "Attributes": {
        "ObjectType": "Conversion"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="71eb4-171">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="71eb4-171">REST response</span></span>

<span data-ttu-id="71eb4-172">Se for bem sucedido, o organismo de resposta contém um recurso [ConversionResult.](conversions-resources.md#conversionresult)</span><span class="sxs-lookup"><span data-stu-id="71eb4-172">If successful, the response body contains a [ConversionResult](conversions-resources.md#conversionresult) resource.</span></span>

#### <a name="response-success-and-error-codes"></a><span data-ttu-id="71eb4-173">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="71eb4-173">Response success and error codes</span></span>

<span data-ttu-id="71eb4-174">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="71eb4-174">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="71eb4-175">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="71eb4-175">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="71eb4-176">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="71eb4-176">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="71eb4-177">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="71eb4-177">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 211
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
MS-RequestId: bd0cde7f-ba87-4010-8a73-1190b641f2a4
MS-CV: kW4GzmhvHEqCq1ls.0
MS-ServerId: 030020643
Date: Thu, 15 Jun 2017 23:10:40 GMT

 {
    "subscriptionId": "488745B5-2086-4912-802C-6ABB9F7C3638",
    "offerId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
    "targetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "attributes": {
        "objectType": "ConversionResult"
    }
}
```
