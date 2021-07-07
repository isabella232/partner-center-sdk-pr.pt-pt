---
title: Obter a qualificação de um cliente
description: Saiba como utilizar a validação sincronizada para obter a qualificação de um cliente através da API do Partner Center. Os parceiros podem usá-lo para validar clientes da Educação.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: d215ddb105efe3acd1182c4ff4bb25b045b121f0
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446348"
---
# <a name="get-a-customers-qualification-via-synchronous-validation"></a><span data-ttu-id="372b3-104">Obtenha a qualificação de um cliente através de validação sincronizada</span><span class="sxs-lookup"><span data-stu-id="372b3-104">Get a customer's qualification via synchronous validation</span></span>

<span data-ttu-id="372b3-105">Saiba como obter a qualificação de um cliente sincronizadamente através de APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="372b3-105">Learn how to get a customer's qualification synchronously via Partner Center APIs.</span></span> <span data-ttu-id="372b3-106">Para aprender a fazê-lo assíncronos, consulte [obter a qualificação de um cliente através de validação assíncronosa.](get-customer-qualification-asynchronous.md)</span><span class="sxs-lookup"><span data-stu-id="372b3-106">To learn how to do this asynchronously, see [Get a customer's qualification via asynchronous validation](get-customer-qualification-asynchronous.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="372b3-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="372b3-107">Prerequisites</span></span>

- <span data-ttu-id="372b3-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="372b3-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="372b3-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="372b3-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="372b3-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="372b3-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="372b3-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="372b3-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="372b3-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="372b3-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="372b3-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="372b3-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="372b3-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="372b3-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="372b3-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="372b3-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="372b3-116">C\#</span><span class="sxs-lookup"><span data-stu-id="372b3-116">C\#</span></span>

<span data-ttu-id="372b3-117">Para obter a qualificação de um cliente, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="372b3-117">To get a customer's qualification, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="372b3-118">Em seguida, use a propriedade [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) para recuperar uma interface [**ICustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification)</span><span class="sxs-lookup"><span data-stu-id="372b3-118">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="372b3-119">Por fim, ligue para [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) para recuperar a qualificação do cliente.</span><span class="sxs-lookup"><span data-stu-id="372b3-119">Finally, call [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) to retrieve the customer's qualification.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var customerQualification = partnerOperations.Customers.ById(customerId).Qualification.Get();
```

## <a name="rest-request"></a><span data-ttu-id="372b3-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="372b3-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="372b3-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="372b3-121">Request syntax</span></span>

| <span data-ttu-id="372b3-122">Método</span><span class="sxs-lookup"><span data-stu-id="372b3-122">Method</span></span>  | <span data-ttu-id="372b3-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="372b3-123">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="372b3-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="372b3-124">**GET**</span></span> | <span data-ttu-id="372b3-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/qualificação HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="372b3-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualification HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="372b3-126">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="372b3-126">URI parameter</span></span>

<span data-ttu-id="372b3-127">Esta tabela lista o parâmetro de consulta necessário para obter toda a qualificação.</span><span class="sxs-lookup"><span data-stu-id="372b3-127">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="372b3-128">Nome</span><span class="sxs-lookup"><span data-stu-id="372b3-128">Name</span></span>               | <span data-ttu-id="372b3-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="372b3-129">Type</span></span>   | <span data-ttu-id="372b3-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="372b3-130">Required</span></span> | <span data-ttu-id="372b3-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="372b3-131">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="372b3-132">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="372b3-132">**customer-tenant-id**</span></span> | <span data-ttu-id="372b3-133">string</span><span class="sxs-lookup"><span data-stu-id="372b3-133">string</span></span> | <span data-ttu-id="372b3-134">Yes</span><span class="sxs-lookup"><span data-stu-id="372b3-134">Yes</span></span>      | <span data-ttu-id="372b3-135">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="372b3-135">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="372b3-136">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="372b3-136">Request headers</span></span>

<span data-ttu-id="372b3-137">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="372b3-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="372b3-138">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="372b3-138">Request body</span></span>

<span data-ttu-id="372b3-139">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="372b3-139">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="372b3-140">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="372b3-140">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="372b3-141">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="372b3-141">REST response</span></span>

<span data-ttu-id="372b3-142">Se for bem sucedido, este método devolve um valor de qualificação no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="372b3-142">If successful, this method returns a qualification value in the response body.</span></span>  <span data-ttu-id="372b3-143">Abaixo está um exemplo da chamada **GET** a um cliente com a **qualificação de educação.**</span><span class="sxs-lookup"><span data-stu-id="372b3-143">Below is an example of the **GET** call on a customer with the **education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="372b3-144">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="372b3-144">Response success and error codes</span></span>

<span data-ttu-id="372b3-145">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="372b3-145">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="372b3-146">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="372b3-146">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="372b3-147">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="372b3-147">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="372b3-148">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="372b3-148">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

    "education"

```

## <a name="related-articles"></a><span data-ttu-id="372b3-149">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="372b3-149">Related articles</span></span>

- [<span data-ttu-id="372b3-150">Atualizar a qualificação de um cliente</span><span class="sxs-lookup"><span data-stu-id="372b3-150">Update a customer's qualification</span></span>](./update-customer-qualification-synchronous.md)