---
title: Obter a qualificação de um cliente
description: Saiba como utilizar a validação sincronizada para obter a qualificação de um cliente através da API do Partner Center. Os parceiros podem usá-lo para validar clientes da Educação.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 82812091be9c13d64ac183c37461e3b63b2ec294
ms.sourcegitcommit: 0c98496e972aebe10eba23822aa229125bfc035d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770184"
---
# <a name="get-a-customers-qualification-via-synchronous-validation"></a><span data-ttu-id="46540-104">Obtenha a qualificação de um cliente através de validação sincronizada</span><span class="sxs-lookup"><span data-stu-id="46540-104">Get a customer's qualification via synchronous validation</span></span>

<span data-ttu-id="46540-105">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="46540-105">**Applies To**</span></span>

- <span data-ttu-id="46540-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="46540-106">Partner Center</span></span>

<span data-ttu-id="46540-107">Saiba como obter a qualificação de um cliente sincronizadamente através de APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="46540-107">Learn how to get a customer's qualification synchronously via Partner Center APIs.</span></span> <span data-ttu-id="46540-108">Para aprender a fazê-lo assíncronos, consulte [obter a qualificação de um cliente através de validação assíncronosa.](get-customer-qualification-asynchronous.md)</span><span class="sxs-lookup"><span data-stu-id="46540-108">To learn how to do this asynchronously, see [Get a customer's qualification via asynchronous validation](get-customer-qualification-asynchronous.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46540-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="46540-109">Prerequisites</span></span>

- <span data-ttu-id="46540-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="46540-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="46540-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="46540-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="46540-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="46540-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="46540-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="46540-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="46540-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="46540-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="46540-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="46540-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="46540-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="46540-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="46540-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="46540-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="46540-118">C\#</span><span class="sxs-lookup"><span data-stu-id="46540-118">C\#</span></span>

<span data-ttu-id="46540-119">Para obter a qualificação de um cliente, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="46540-119">To get a customer's qualification, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="46540-120">Em seguida, use a propriedade [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) para recuperar uma interface [**ICustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification)</span><span class="sxs-lookup"><span data-stu-id="46540-120">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="46540-121">Por fim, ligue para [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) para recuperar a qualificação do cliente.</span><span class="sxs-lookup"><span data-stu-id="46540-121">Finally, call [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) to retrieve the customer's qualification.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var customerQualification = partnerOperations.Customers.ById(customerId).Qualification.Get();
```

## <a name="rest-request"></a><span data-ttu-id="46540-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="46540-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="46540-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="46540-123">Request syntax</span></span>

| <span data-ttu-id="46540-124">Método</span><span class="sxs-lookup"><span data-stu-id="46540-124">Method</span></span>  | <span data-ttu-id="46540-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="46540-125">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="46540-126">**Obter**</span><span class="sxs-lookup"><span data-stu-id="46540-126">**GET**</span></span> | <span data-ttu-id="46540-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/qualificação HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="46540-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualification HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="46540-128">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="46540-128">URI parameter</span></span>

<span data-ttu-id="46540-129">Esta tabela lista o parâmetro de consulta necessário para obter toda a qualificação.</span><span class="sxs-lookup"><span data-stu-id="46540-129">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="46540-130">Nome</span><span class="sxs-lookup"><span data-stu-id="46540-130">Name</span></span>               | <span data-ttu-id="46540-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="46540-131">Type</span></span>   | <span data-ttu-id="46540-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="46540-132">Required</span></span> | <span data-ttu-id="46540-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="46540-133">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="46540-134">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="46540-134">**customer-tenant-id**</span></span> | <span data-ttu-id="46540-135">string</span><span class="sxs-lookup"><span data-stu-id="46540-135">string</span></span> | <span data-ttu-id="46540-136">Sim</span><span class="sxs-lookup"><span data-stu-id="46540-136">Yes</span></span>      | <span data-ttu-id="46540-137">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="46540-137">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="46540-138">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="46540-138">Request headers</span></span>

<span data-ttu-id="46540-139">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="46540-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="46540-140">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="46540-140">Request body</span></span>

<span data-ttu-id="46540-141">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="46540-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="46540-142">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="46540-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="46540-143">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="46540-143">REST response</span></span>

<span data-ttu-id="46540-144">Se for bem sucedido, este método devolve um valor de qualificação no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="46540-144">If successful, this method returns a qualification value in the response body.</span></span>  <span data-ttu-id="46540-145">Abaixo está um exemplo da chamada **GET** a um cliente com a **qualificação de educação.**</span><span class="sxs-lookup"><span data-stu-id="46540-145">Below is an example of the **GET** call on a customer with the **education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="46540-146">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="46540-146">Response success and error codes</span></span>

<span data-ttu-id="46540-147">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="46540-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="46540-148">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="46540-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="46540-149">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="46540-149">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="46540-150">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="46540-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

    "education"

```

## <a name="related-articles"></a><span data-ttu-id="46540-151">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="46540-151">Related articles</span></span>

- [<span data-ttu-id="46540-152">Atualizar a qualificação de um cliente</span><span class="sxs-lookup"><span data-stu-id="46540-152">Update a customer's qualification</span></span>](update-a-customer-s-qualification.md)
