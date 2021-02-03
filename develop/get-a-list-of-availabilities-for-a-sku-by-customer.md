---
title: Obter uma lista de disponibilidade para um SKU (por cliente)
description: Você pode obter uma coleção de disponibilidades para um produto especificado e SKU pelo cliente usando os identificadores de cliente, produto e SKU.
ms.assetid: ''
ms.date: 10/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 5f4067916fea911963182954eed77f4e230e79d6
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769127"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-customer"></a><span data-ttu-id="5dd06-103">Obter uma lista de disponibilidade para um SKU (por cliente)</span><span class="sxs-lookup"><span data-stu-id="5dd06-103">Get a list of availabilities for a SKU (by customer)</span></span>

<span data-ttu-id="5dd06-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="5dd06-104">**Applies to:**</span></span>

- <span data-ttu-id="5dd06-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="5dd06-105">Partner Center</span></span>
- <span data-ttu-id="5dd06-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="5dd06-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="5dd06-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="5dd06-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="5dd06-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5dd06-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5dd06-109">Pode utilizar os seguintes métodos para obter uma coleção de disponibilidades para um produto especificado e sKU disponível para um determinado cliente.</span><span class="sxs-lookup"><span data-stu-id="5dd06-109">You can use the following methods to get a collection of availabilities for a specified product and SKU available to a particular customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5dd06-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5dd06-110">Prerequisites</span></span>

- <span data-ttu-id="5dd06-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5dd06-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5dd06-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="5dd06-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="5dd06-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5dd06-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5dd06-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5dd06-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5dd06-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="5dd06-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5dd06-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="5dd06-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5dd06-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="5dd06-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5dd06-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5dd06-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="5dd06-119">Um identificador de produto **(id produto).**</span><span class="sxs-lookup"><span data-stu-id="5dd06-119">A product identifier (**product-id**).</span></span>

- <span data-ttu-id="5dd06-120">Um identificador SKU **(sku-id).**</span><span class="sxs-lookup"><span data-stu-id="5dd06-120">A SKU identifier (**sku-id**).</span></span>

## <a name="rest-request"></a><span data-ttu-id="5dd06-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5dd06-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5dd06-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5dd06-122">Request syntax</span></span>

| <span data-ttu-id="5dd06-123">Método</span><span class="sxs-lookup"><span data-stu-id="5dd06-123">Method</span></span> | <span data-ttu-id="5dd06-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5dd06-124">Request URI</span></span>                                                                                                                 |
|--------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5dd06-125">POST</span><span class="sxs-lookup"><span data-stu-id="5dd06-125">POST</span></span>   | <span data-ttu-id="5dd06-126">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/produtos/{product-id}/skus/{sku-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5dd06-126">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products/{product-id}/skus/{sku-id} HTTP/1.1</span></span> |

### <a name="request-uri-parameters"></a><span data-ttu-id="5dd06-127">Solicite parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="5dd06-127">Request URI parameters</span></span>

| <span data-ttu-id="5dd06-128">Nome</span><span class="sxs-lookup"><span data-stu-id="5dd06-128">Name</span></span>               | <span data-ttu-id="5dd06-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="5dd06-129">Type</span></span> | <span data-ttu-id="5dd06-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="5dd06-130">Required</span></span> | <span data-ttu-id="5dd06-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="5dd06-131">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="5dd06-132">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="5dd06-132">customer-tenant-id</span></span> | <span data-ttu-id="5dd06-133">GUID</span><span class="sxs-lookup"><span data-stu-id="5dd06-133">GUID</span></span> | <span data-ttu-id="5dd06-134">Sim</span><span class="sxs-lookup"><span data-stu-id="5dd06-134">Yes</span></span> | <span data-ttu-id="5dd06-135">O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="5dd06-135">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="5dd06-136">id produto</span><span class="sxs-lookup"><span data-stu-id="5dd06-136">product-id</span></span> | <span data-ttu-id="5dd06-137">string</span><span class="sxs-lookup"><span data-stu-id="5dd06-137">string</span></span> | <span data-ttu-id="5dd06-138">Sim</span><span class="sxs-lookup"><span data-stu-id="5dd06-138">Yes</span></span> | <span data-ttu-id="5dd06-139">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="5dd06-139">A string that identifies the product.</span></span> |
| <span data-ttu-id="5dd06-140">sku-id</span><span class="sxs-lookup"><span data-stu-id="5dd06-140">sku-id</span></span> | <span data-ttu-id="5dd06-141">string</span><span class="sxs-lookup"><span data-stu-id="5dd06-141">string</span></span> | <span data-ttu-id="5dd06-142">Sim</span><span class="sxs-lookup"><span data-stu-id="5dd06-142">Yes</span></span> | <span data-ttu-id="5dd06-143">Uma corda que identifica o SKU.</span><span class="sxs-lookup"><span data-stu-id="5dd06-143">A string that identifies the SKU.</span></span> |

### <a name="request-header"></a><span data-ttu-id="5dd06-144">Cabeçalho do pedido</span><span class="sxs-lookup"><span data-stu-id="5dd06-144">Request header</span></span>

<span data-ttu-id="5dd06-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5dd06-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5dd06-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5dd06-146">Request body</span></span>

<span data-ttu-id="5dd06-147">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5dd06-147">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5dd06-148">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5dd06-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products/DZH318Z0BPS6/skus/0001/availabilities HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="5dd06-149">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5dd06-149">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5dd06-150">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5dd06-150">Response success and error codes</span></span>

<span data-ttu-id="5dd06-151">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5dd06-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5dd06-152">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5dd06-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5dd06-153">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="5dd06-153">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="5dd06-154">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="5dd06-154">This method returns the following error codes:</span></span>

| <span data-ttu-id="5dd06-155">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="5dd06-155">HTTP Status Code</span></span> | <span data-ttu-id="5dd06-156">Código de erro</span><span class="sxs-lookup"><span data-stu-id="5dd06-156">Error code</span></span> | <span data-ttu-id="5dd06-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="5dd06-157">Description</span></span> |
|------------------|------------|-------------|
| <span data-ttu-id="5dd06-158">404</span><span class="sxs-lookup"><span data-stu-id="5dd06-158">404</span></span> | <span data-ttu-id="5dd06-159">400013</span><span class="sxs-lookup"><span data-stu-id="5dd06-159">400013</span></span> | <span data-ttu-id="5dd06-160">O produto-mãe não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="5dd06-160">The parent product was not found.</span></span> |

### <a name="response-example"></a><span data-ttu-id="5dd06-161">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5dd06-161">Response example</span></span>

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
