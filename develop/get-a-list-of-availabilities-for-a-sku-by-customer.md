---
title: Obter uma lista de disponibilidade para um SKU (por cliente)
description: Você pode obter uma coleção de disponibilidades para um produto especificado e SKU pelo cliente usando os identificadores de cliente, produto e SKU.
ms.assetid: ''
ms.date: 10/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b237bbd17a6108bbcb4e23529cf476a6b8306f68
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874555"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-customer"></a><span data-ttu-id="d9b2c-103">Obter uma lista de disponibilidade para um SKU (por cliente)</span><span class="sxs-lookup"><span data-stu-id="d9b2c-103">Get a list of availabilities for a SKU (by customer)</span></span>

<span data-ttu-id="d9b2c-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d9b2c-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d9b2c-105">Pode utilizar os seguintes métodos para obter uma coleção de disponibilidades para um produto especificado e sKU disponível para um determinado cliente.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-105">You can use the following methods to get a collection of availabilities for a specified product and SKU available to a particular customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d9b2c-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d9b2c-106">Prerequisites</span></span>

- <span data-ttu-id="d9b2c-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d9b2c-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d9b2c-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="d9b2c-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d9b2c-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d9b2c-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d9b2c-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d9b2c-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d9b2c-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d9b2c-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d9b2c-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d9b2c-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d9b2c-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d9b2c-115">Um identificador de produto **(id produto).**</span><span class="sxs-lookup"><span data-stu-id="d9b2c-115">A product identifier (**product-id**).</span></span>

- <span data-ttu-id="d9b2c-116">Um identificador SKU **(sku-id).**</span><span class="sxs-lookup"><span data-stu-id="d9b2c-116">A SKU identifier (**sku-id**).</span></span>

## <a name="rest-request"></a><span data-ttu-id="d9b2c-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d9b2c-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d9b2c-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9b2c-118">Request syntax</span></span>

| <span data-ttu-id="d9b2c-119">Método</span><span class="sxs-lookup"><span data-stu-id="d9b2c-119">Method</span></span> | <span data-ttu-id="d9b2c-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d9b2c-120">Request URI</span></span>                                                                                                                 |
|--------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d9b2c-121">POST</span><span class="sxs-lookup"><span data-stu-id="d9b2c-121">POST</span></span>   | <span data-ttu-id="d9b2c-122">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/produtos/{product-id}/skus/{sku-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d9b2c-122">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products/{product-id}/skus/{sku-id} HTTP/1.1</span></span> |

### <a name="request-uri-parameters"></a><span data-ttu-id="d9b2c-123">Solicite parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="d9b2c-123">Request URI parameters</span></span>

| <span data-ttu-id="d9b2c-124">Nome</span><span class="sxs-lookup"><span data-stu-id="d9b2c-124">Name</span></span>               | <span data-ttu-id="d9b2c-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="d9b2c-125">Type</span></span> | <span data-ttu-id="d9b2c-126">Necessário</span><span class="sxs-lookup"><span data-stu-id="d9b2c-126">Required</span></span> | <span data-ttu-id="d9b2c-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9b2c-127">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="d9b2c-128">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="d9b2c-128">customer-tenant-id</span></span> | <span data-ttu-id="d9b2c-129">GUID</span><span class="sxs-lookup"><span data-stu-id="d9b2c-129">GUID</span></span> | <span data-ttu-id="d9b2c-130">Yes</span><span class="sxs-lookup"><span data-stu-id="d9b2c-130">Yes</span></span> | <span data-ttu-id="d9b2c-131">O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-131">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="d9b2c-132">id produto</span><span class="sxs-lookup"><span data-stu-id="d9b2c-132">product-id</span></span> | <span data-ttu-id="d9b2c-133">string</span><span class="sxs-lookup"><span data-stu-id="d9b2c-133">string</span></span> | <span data-ttu-id="d9b2c-134">Yes</span><span class="sxs-lookup"><span data-stu-id="d9b2c-134">Yes</span></span> | <span data-ttu-id="d9b2c-135">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-135">A string that identifies the product.</span></span> |
| <span data-ttu-id="d9b2c-136">sku-id</span><span class="sxs-lookup"><span data-stu-id="d9b2c-136">sku-id</span></span> | <span data-ttu-id="d9b2c-137">string</span><span class="sxs-lookup"><span data-stu-id="d9b2c-137">string</span></span> | <span data-ttu-id="d9b2c-138">Yes</span><span class="sxs-lookup"><span data-stu-id="d9b2c-138">Yes</span></span> | <span data-ttu-id="d9b2c-139">Uma corda que identifica o SKU.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-139">A string that identifies the SKU.</span></span> |

### <a name="request-header"></a><span data-ttu-id="d9b2c-140">Cabeçalho do pedido</span><span class="sxs-lookup"><span data-stu-id="d9b2c-140">Request header</span></span>

<span data-ttu-id="d9b2c-141">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d9b2c-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d9b2c-142">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d9b2c-142">Request body</span></span>

<span data-ttu-id="d9b2c-143">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d9b2c-144">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d9b2c-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products/DZH318Z0BPS6/skus/0001/availabilities HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="d9b2c-145">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d9b2c-145">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d9b2c-146">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d9b2c-146">Response success and error codes</span></span>

<span data-ttu-id="d9b2c-147">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d9b2c-148">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d9b2c-149">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d9b2c-149">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="d9b2c-150">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="d9b2c-150">This method returns the following error codes:</span></span>

| <span data-ttu-id="d9b2c-151">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="d9b2c-151">HTTP Status Code</span></span> | <span data-ttu-id="d9b2c-152">Código de erro</span><span class="sxs-lookup"><span data-stu-id="d9b2c-152">Error code</span></span> | <span data-ttu-id="d9b2c-153">Description</span><span class="sxs-lookup"><span data-stu-id="d9b2c-153">Description</span></span> |
|------------------|------------|-------------|
| <span data-ttu-id="d9b2c-154">404</span><span class="sxs-lookup"><span data-stu-id="d9b2c-154">404</span></span> | <span data-ttu-id="d9b2c-155">400013</span><span class="sxs-lookup"><span data-stu-id="d9b2c-155">400013</span></span> | <span data-ttu-id="d9b2c-156">O produto-mãe não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="d9b2c-156">The parent product was not found.</span></span> |

### <a name="response-example"></a><span data-ttu-id="d9b2c-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d9b2c-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1909
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cad955c2-8efc-47fe-b112-548ff002ba18
MS-RequestId: ae7288e2-2673-4ad4-8c12-7aad818d5949
{
    "id": "0001",
    "productId": "DZH318Z0BPS6",
    "title": "Microsoft Azure plan",
    "description": "Microsoft Azure plan (MS-AZR-0017G)",
    "minimumQuantity": 1,
    "maximumQuantity": 1,
    "isTrial": false,
    "supportedBillingCycles": [
        "one_time"
    ],
    "purchasePrerequisites": [
        "MicrosoftCustomerAgreement"
    ],
    "inventoryVariables": [],
    "provisioningVariables": [],
    "actions": [
        "Refund"
    ],
    "dynamicAttributes": {
        "isMicrosoftProduct": true,
        "pilotProgram": "modernazurepilot"
    },
    "links": {
        "availabilities": {
            "uri": "/products/DZH318Z0BPS6/skus/0001/availabilities?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BPS6/skus/0001?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
