---
title: Obtenha uma lista de SKUs para um produto (por cliente)
description: Obtém uma coleção de SKUs para o produto especificado pelo cliente.
ms.assetid: ''
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b76526d97ba9027897fc88954ba45186d58aefb8
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874164"
---
# <a name="get-a-list-of-skus-for-a-product-by-customer"></a><span data-ttu-id="f07be-103">Obtenha uma lista de SKUs para um produto (por cliente)</span><span class="sxs-lookup"><span data-stu-id="f07be-103">Get a list of SKUs for a product (by customer)</span></span>

<span data-ttu-id="f07be-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="f07be-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="f07be-105">Obtém uma coleção de SKUs para um determinado produto que está disponível para um cliente existente.</span><span class="sxs-lookup"><span data-stu-id="f07be-105">Gets a collection of SKUs for a particular product that is available to an existing customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f07be-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f07be-106">Prerequisites</span></span>

- <span data-ttu-id="f07be-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f07be-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f07be-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="f07be-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="f07be-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f07be-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f07be-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f07be-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f07be-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="f07be-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f07be-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="f07be-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f07be-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="f07be-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f07be-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f07be-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f07be-115">Um ID do produto **(id do produto).**</span><span class="sxs-lookup"><span data-stu-id="f07be-115">A product ID (**product-id**).</span></span>

## <a name="rest-request"></a><span data-ttu-id="f07be-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f07be-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f07be-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f07be-117">Request syntax</span></span>

| <span data-ttu-id="f07be-118">Método</span><span class="sxs-lookup"><span data-stu-id="f07be-118">Method</span></span> | <span data-ttu-id="f07be-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f07be-119">Request URI</span></span>                                                                                                        |
|--------|--------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f07be-120">POST</span><span class="sxs-lookup"><span data-stu-id="f07be-120">POST</span></span>   | <span data-ttu-id="f07be-121">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/produtos/{product-id}/skus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f07be-121">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products/{product-id}/skus HTTP/1.1</span></span> |

### <a name="request-uri-parameter"></a><span data-ttu-id="f07be-122">Solicitação uri parâmetro</span><span class="sxs-lookup"><span data-stu-id="f07be-122">Request URI parameter</span></span>

| <span data-ttu-id="f07be-123">Nome</span><span class="sxs-lookup"><span data-stu-id="f07be-123">Name</span></span>               | <span data-ttu-id="f07be-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="f07be-124">Type</span></span> | <span data-ttu-id="f07be-125">Necessário</span><span class="sxs-lookup"><span data-stu-id="f07be-125">Required</span></span> | <span data-ttu-id="f07be-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f07be-126">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="f07be-127">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="f07be-127">customer-tenant-id</span></span> | <span data-ttu-id="f07be-128">GUID</span><span class="sxs-lookup"><span data-stu-id="f07be-128">GUID</span></span> | <span data-ttu-id="f07be-129">Yes</span><span class="sxs-lookup"><span data-stu-id="f07be-129">Yes</span></span> | <span data-ttu-id="f07be-130">O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="f07be-130">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="f07be-131">id produto</span><span class="sxs-lookup"><span data-stu-id="f07be-131">product-id</span></span> | <span data-ttu-id="f07be-132">string</span><span class="sxs-lookup"><span data-stu-id="f07be-132">string</span></span> | <span data-ttu-id="f07be-133">Yes</span><span class="sxs-lookup"><span data-stu-id="f07be-133">Yes</span></span> | <span data-ttu-id="f07be-134">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="f07be-134">A string that identifies the product.</span></span> |

### <a name="request-header"></a><span data-ttu-id="f07be-135">Cabeçalho do pedido</span><span class="sxs-lookup"><span data-stu-id="f07be-135">Request header</span></span>

<span data-ttu-id="f07be-136">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f07be-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f07be-137">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f07be-137">Request body</span></span>

<span data-ttu-id="f07be-138">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f07be-138">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f07be-139">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f07be-139">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products/DZH318Z0BPS6 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="f07be-140">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f07be-140">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f07be-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f07be-141">Response success and error codes</span></span>

<span data-ttu-id="f07be-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f07be-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f07be-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f07be-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f07be-144">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f07be-144">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="f07be-145">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="f07be-145">This method returns the following error codes:</span></span>

| <span data-ttu-id="f07be-146">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="f07be-146">HTTP Status Code</span></span> | <span data-ttu-id="f07be-147">Código de erro</span><span class="sxs-lookup"><span data-stu-id="f07be-147">Error code</span></span> | <span data-ttu-id="f07be-148">Description</span><span class="sxs-lookup"><span data-stu-id="f07be-148">Description</span></span> |
|------------------|------------|-------------|
| <span data-ttu-id="f07be-149">404</span><span class="sxs-lookup"><span data-stu-id="f07be-149">404</span></span> | <span data-ttu-id="f07be-150">400013</span><span class="sxs-lookup"><span data-stu-id="f07be-150">400013</span></span> | <span data-ttu-id="f07be-151">O produto-mãe não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="f07be-151">The parent product was not found.</span></span> |

### <a name="response-example"></a><span data-ttu-id="f07be-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f07be-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1909
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cad955c2-8efc-47fe-b112-548ff002ba18
MS-RequestId: ae7288e2-2673-4ad4-8c12-7aad818d5949

{
    "id": "DZH318Z0BPS6",
    "title": "Microsoft Azure plan",
    "description": "Gain access to Azure Services.",
    "productType": {
        "id": "Azure",
        "displayName": "Azure",
        "subType": {
            "id": "Azure",
            "displayName": "Azure"
        }
    },
    "isMicrosoftProduct": true,
    "publisherName": "Microsoft Corporation",
    "links": {
        "skus": {
            "uri": "/products/DZH318Z0BPS6/skus?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BPS6?country=US",
            "method": "GET",
            "headers": []
        }
    },
    "localizedAttributes": [
        {
            "key": "OfferType",
            "value": "OfferType"
        },
        {
            "key": "Standard",
            "value": "Standard"
        },
        {
            "key": "DevTest",
            "value": "Dev/Test"
        }
    ]
}
```
