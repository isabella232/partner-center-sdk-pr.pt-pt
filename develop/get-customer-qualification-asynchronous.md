---
title: Obtenha as qualificações de um cliente
description: Saiba como usar a validação assíncrono para obter a qualificação de um cliente através da API do Partner Center. Os parceiros podem usá-lo para validar clientes da Educação.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 9f9b9aaddde0d66caf9c7ef32e8fba6d5e3aba36
ms.sourcegitcommit: 0c98496e972aebe10eba23822aa229125bfc035d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2020
ms.locfileid: "97770191"
---
# <a name="get-a-customers-qualifications-via-asynchronous-validation"></a><span data-ttu-id="46304-104">Obtenha as qualificações de um cliente através de validação assíncronea</span><span class="sxs-lookup"><span data-stu-id="46304-104">Get a customer's qualifications via asynchronous validation</span></span>

<span data-ttu-id="46304-105">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="46304-105">**Applies To**</span></span>

- <span data-ttu-id="46304-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="46304-106">Partner Center</span></span>

<span data-ttu-id="46304-107">Saiba como obter as qualificações de um cliente assíncroneamente através das APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="46304-107">Learn how to get a customer's qualifications asynchronously via Partner Center APIs.</span></span> <span data-ttu-id="46304-108">Para aprender a fazer isto de forma sincronizada, consulte [obter a qualificação de um cliente através de validação sincronizada.](get-customer-qualification-synchronous.md)</span><span class="sxs-lookup"><span data-stu-id="46304-108">To learn how to do this synchronously, see [Get a customer's qualification via synchronous validation](get-customer-qualification-synchronous.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46304-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="46304-109">Prerequisites</span></span>

- <span data-ttu-id="46304-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="46304-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="46304-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="46304-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="46304-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="46304-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="46304-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="46304-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="46304-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="46304-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="46304-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="46304-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="46304-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="46304-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="46304-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="46304-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="46304-118">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="46304-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="46304-119">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="46304-119">Request syntax</span></span>

| <span data-ttu-id="46304-120">Método</span><span class="sxs-lookup"><span data-stu-id="46304-120">Method</span></span>  | <span data-ttu-id="46304-121">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="46304-121">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="46304-122">**Obter**</span><span class="sxs-lookup"><span data-stu-id="46304-122">**GET**</span></span> | <span data-ttu-id="46304-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/qualificações HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="46304-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualifications HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="46304-124">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="46304-124">URI parameter</span></span>

<span data-ttu-id="46304-125">Esta tabela lista o parâmetro de consulta necessário para obter toda a qualificação.</span><span class="sxs-lookup"><span data-stu-id="46304-125">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="46304-126">Nome</span><span class="sxs-lookup"><span data-stu-id="46304-126">Name</span></span>               | <span data-ttu-id="46304-127">Tipo</span><span class="sxs-lookup"><span data-stu-id="46304-127">Type</span></span>   | <span data-ttu-id="46304-128">Necessário</span><span class="sxs-lookup"><span data-stu-id="46304-128">Required</span></span> | <span data-ttu-id="46304-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="46304-129">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="46304-130">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="46304-130">**customer-tenant-id**</span></span> | <span data-ttu-id="46304-131">string</span><span class="sxs-lookup"><span data-stu-id="46304-131">string</span></span> | <span data-ttu-id="46304-132">Sim</span><span class="sxs-lookup"><span data-stu-id="46304-132">Yes</span></span>      | <span data-ttu-id="46304-133">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="46304-133">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="46304-134">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="46304-134">Request headers</span></span>

<span data-ttu-id="46304-135">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="46304-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="46304-136">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="46304-136">Request body</span></span>

<span data-ttu-id="46304-137">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="46304-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="46304-138">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="46304-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="46304-139">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="46304-139">REST response</span></span>

<span data-ttu-id="46304-140">Se for bem sucedido, este método devolve uma coleção de qualificações no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="46304-140">If successful, this method returns a collection of qualifications in the response body.</span></span>  <span data-ttu-id="46304-141">Abaixo estão exemplos da chamada **GET** a um cliente com a qualificação **de Educação.**</span><span class="sxs-lookup"><span data-stu-id="46304-141">Below are examples of the **GET** call on a customer with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="46304-142">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="46304-142">Response success and error codes</span></span>

<span data-ttu-id="46304-143">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="46304-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="46304-144">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="46304-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="46304-145">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="46304-145">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-examples"></a><span data-ttu-id="46304-146">Exemplos de resposta</span><span class="sxs-lookup"><span data-stu-id="46304-146">Response examples</span></span>

<span data-ttu-id="46304-147">Esta secção mostra as respostas que pode receber quando a de um cliente `vettingStatus` é:</span><span class="sxs-lookup"><span data-stu-id="46304-147">This section shows responses you might receive when a customer's `vettingStatus` is:</span></span>

- <span data-ttu-id="46304-148">Aprovado</span><span class="sxs-lookup"><span data-stu-id="46304-148">Approved</span></span>
- <span data-ttu-id="46304-149">Em Revisão</span><span class="sxs-lookup"><span data-stu-id="46304-149">In Review</span></span>
- <span data-ttu-id="46304-150">Negado</span><span class="sxs-lookup"><span data-stu-id="46304-150">Denied</span></span>

<span data-ttu-id="46304-151">**Exemplo aprovado:**</span><span class="sxs-lookup"><span data-stu-id="46304-151">**Approved** example:</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "Approved",
    }
]

```

<span data-ttu-id="46304-152">No exemplo **de Revisão:**</span><span class="sxs-lookup"><span data-stu-id="46304-152">**In Review** example:</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "InReview",
        "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
    }
]

```

<span data-ttu-id="46304-153">**Exemplo negado:**</span><span class="sxs-lookup"><span data-stu-id="46304-153">**Denied** example:</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "Denied",
        "vettingReason": "Not an Education Customer", // example Vetting Reason
        "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
    }
]

```

## <a name="related-articles"></a><span data-ttu-id="46304-154">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="46304-154">Related articles</span></span>

- [<span data-ttu-id="46304-155">Atualizar as qualificações de um cliente</span><span class="sxs-lookup"><span data-stu-id="46304-155">Update a customer's qualifications</span></span>](update-a-customer-s-qualifications.md)