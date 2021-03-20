---
title: Obtenha as qualificações de um cliente
description: Saiba como usar a validação assíncrono para obter a qualificação de um cliente através da API do Partner Center. Os parceiros podem usá-lo para validar clientes da Educação.
ms.date: 01/21/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 2c860d4a35104131197e06d4712f4ef41ba0008e
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711919"
---
# <a name="get-a-customers-qualification-asynchronously"></a><span data-ttu-id="c942b-104">Obtenha a qualificação de um cliente assíncronea</span><span class="sxs-lookup"><span data-stu-id="c942b-104">Get a customer's qualification asynchronously</span></span>

<span data-ttu-id="c942b-105">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="c942b-105">**Applies To**</span></span>

- <span data-ttu-id="c942b-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="c942b-106">Partner Center</span></span>

<span data-ttu-id="c942b-107">Como obter as qualificações de um cliente assíncroneamente.</span><span class="sxs-lookup"><span data-stu-id="c942b-107">How to get a customer's qualifications asynchronously.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c942b-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c942b-108">Prerequisites</span></span>

- <span data-ttu-id="c942b-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c942b-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c942b-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="c942b-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="c942b-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c942b-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c942b-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="c942b-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c942b-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="c942b-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c942b-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="c942b-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c942b-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="c942b-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c942b-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c942b-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="c942b-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c942b-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c942b-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c942b-118">Request syntax</span></span>

| <span data-ttu-id="c942b-119">Método</span><span class="sxs-lookup"><span data-stu-id="c942b-119">Method</span></span>  | <span data-ttu-id="c942b-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c942b-120">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c942b-121">**Obter**</span><span class="sxs-lookup"><span data-stu-id="c942b-121">**GET**</span></span> | <span data-ttu-id="c942b-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/qualificações HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c942b-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualifications HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="c942b-123">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="c942b-123">URI parameter</span></span>

<span data-ttu-id="c942b-124">Esta tabela lista o parâmetro de consulta necessário para obter toda a qualificação.</span><span class="sxs-lookup"><span data-stu-id="c942b-124">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="c942b-125">Nome</span><span class="sxs-lookup"><span data-stu-id="c942b-125">Name</span></span>               | <span data-ttu-id="c942b-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="c942b-126">Type</span></span>   | <span data-ttu-id="c942b-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="c942b-127">Required</span></span> | <span data-ttu-id="c942b-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="c942b-128">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="c942b-129">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="c942b-129">**customer-tenant-id**</span></span> | <span data-ttu-id="c942b-130">string</span><span class="sxs-lookup"><span data-stu-id="c942b-130">string</span></span> | <span data-ttu-id="c942b-131">Yes</span><span class="sxs-lookup"><span data-stu-id="c942b-131">Yes</span></span>      | <span data-ttu-id="c942b-132">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="c942b-132">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c942b-133">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c942b-133">Request headers</span></span>

<span data-ttu-id="c942b-134">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c942b-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c942b-135">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="c942b-135">Request body</span></span>

<span data-ttu-id="c942b-136">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c942b-136">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c942b-137">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c942b-137">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="c942b-138">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c942b-138">REST response</span></span>

<span data-ttu-id="c942b-139">Se for bem sucedido, este método devolve uma coleção de qualificações no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="c942b-139">If successful, this method returns a collection of qualifications in the response body.</span></span>  <span data-ttu-id="c942b-140">Abaixo estão exemplos da chamada **GET** a um cliente com a qualificação **de Educação.**</span><span class="sxs-lookup"><span data-stu-id="c942b-140">Below are examples of the **GET** call on a customer with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c942b-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c942b-141">Response success and error codes</span></span>

<span data-ttu-id="c942b-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c942b-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c942b-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c942b-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c942b-144">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c942b-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-examples"></a><span data-ttu-id="c942b-145">Exemplos de resposta</span><span class="sxs-lookup"><span data-stu-id="c942b-145">Response examples</span></span>

#### <a name="approved"></a><span data-ttu-id="c942b-146">Aprovado</span><span class="sxs-lookup"><span data-stu-id="c942b-146">Approved</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualifications": [
        {
            "qualification": "Education",
            "vettingStatus": "Approved",
        }
    ]
}

```

#### <a name="in-review"></a><span data-ttu-id="c942b-147">Em Revisão</span><span class="sxs-lookup"><span data-stu-id="c942b-147">In Review</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualifications": [
        {
            "qualification": "Education",
            "vettingStatus": "InReview",
            "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
        }
    ]
}

```

#### <a name="denied"></a><span data-ttu-id="c942b-148">Negado</span><span class="sxs-lookup"><span data-stu-id="c942b-148">Denied</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualifications": [
        {
            "qualification": "Education",
            "vettingStatus": "Denied",
            "vettingReason": "Not an Education Customer", // example Vetting Reason
            "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
        }
    ]
}

```

## <a name="related-articles"></a><span data-ttu-id="c942b-149">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="c942b-149">Related articles</span></span>

- [<span data-ttu-id="c942b-150">Atualizar as qualificações de um cliente</span><span class="sxs-lookup"><span data-stu-id="c942b-150">Update a customer's qualifications</span></span>](./update-customer-qualification-asynchronous.md)