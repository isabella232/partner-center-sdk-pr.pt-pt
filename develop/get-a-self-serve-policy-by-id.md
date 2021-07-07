---
title: Obtenha uma política de autosserviço por ID
description: Obtém a política de autosserviço especificada utilizando o seu ID.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 074d7ba65c7aab91687a67f50e871cee913fc2bb
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873841"
---
# <a name="get-a-self-serve-policy-by-id"></a><span data-ttu-id="503ed-103">Obtenha uma política de autosserviço por ID</span><span class="sxs-lookup"><span data-stu-id="503ed-103">Get a self-serve policy by ID</span></span>

<span data-ttu-id="503ed-104">Obtém a política de autosserviço especificada utilizando o seu ID.</span><span class="sxs-lookup"><span data-stu-id="503ed-104">Gets the specified self-serve policy using its ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="503ed-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="503ed-105">Prerequisites</span></span>

- <span data-ttu-id="503ed-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="503ed-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="503ed-107">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="503ed-107">This scenario supports authentication with App+User credentials.</span></span>
- <span data-ttu-id="503ed-108">Uma identificação de política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="503ed-108">A self-serve policy ID.</span></span>

## <a name="examples"></a><span data-ttu-id="503ed-109">Exemplos</span><span class="sxs-lookup"><span data-stu-id="503ed-109">Examples</span></span>


## <a name="span-idrest_requestspan-idrest_requestspan-idrest_requestrest-request"></a><span data-ttu-id="503ed-110"><span id="REST_Request"/><span id="rest_request"/><span id="REST_REQUEST"/>Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="503ed-110"><span id="REST_Request"/><span id="rest_request"/><span id="REST_REQUEST"/>REST Request</span></span>

<span data-ttu-id="503ed-111">**Solicitar sintaxe**</span><span class="sxs-lookup"><span data-stu-id="503ed-111">**Request syntax**</span></span>

| <span data-ttu-id="503ed-112">Método</span><span class="sxs-lookup"><span data-stu-id="503ed-112">Method</span></span>  | <span data-ttu-id="503ed-113">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="503ed-113">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="503ed-114">**Obter**</span><span class="sxs-lookup"><span data-stu-id="503ed-114">**GET**</span></span> | <span data-ttu-id="503ed-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="503ed-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span></span> |

<span data-ttu-id="503ed-116">**Parâmetro URI**</span><span class="sxs-lookup"><span data-stu-id="503ed-116">**URI parameter**</span></span>

<span data-ttu-id="503ed-117">Utilize os seguintes parâmetros de trajetória para obter o produto especificado.</span><span class="sxs-lookup"><span data-stu-id="503ed-117">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="503ed-118">Nome</span><span class="sxs-lookup"><span data-stu-id="503ed-118">Name</span></span>                       | <span data-ttu-id="503ed-119">Tipo</span><span class="sxs-lookup"><span data-stu-id="503ed-119">Type</span></span>         | <span data-ttu-id="503ed-120">Necessário</span><span class="sxs-lookup"><span data-stu-id="503ed-120">Required</span></span> | <span data-ttu-id="503ed-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="503ed-121">Description</span></span>                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="503ed-122">**SelfServePolicy-id**</span><span class="sxs-lookup"><span data-stu-id="503ed-122">**SelfServePolicy-id**</span></span>     | <span data-ttu-id="503ed-123">**string**</span><span class="sxs-lookup"><span data-stu-id="503ed-123">**string**</span></span>   | <span data-ttu-id="503ed-124">Yes</span><span class="sxs-lookup"><span data-stu-id="503ed-124">Yes</span></span>      | <span data-ttu-id="503ed-125">Uma corda que identifica a política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="503ed-125">A string that identifies the self-serve policy.</span></span>                 |

<span data-ttu-id="503ed-126">**Pedido de cabeçalhos**</span><span class="sxs-lookup"><span data-stu-id="503ed-126">**Request headers**</span></span>

- <span data-ttu-id="503ed-127">Para obter mais informações, consulte [Headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="503ed-127">For more information, see [Headers](headers.md).</span></span>

<span data-ttu-id="503ed-128">**Corpo de pedido**</span><span class="sxs-lookup"><span data-stu-id="503ed-128">**Request body**</span></span>

<span data-ttu-id="503ed-129">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="503ed-129">None.</span></span>

<span data-ttu-id="503ed-130">**Exemplo de pedido**</span><span class="sxs-lookup"><span data-stu-id="503ed-130">**Request example**</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/SelfServePolicy/634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer  <token>
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="503ed-131">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="503ed-131">REST response</span></span>

<span data-ttu-id="503ed-132">Se for bem sucedido, o corpo de resposta contém um recurso [SelfServePolicy.](self-serve-policy-resources.md#selfservepolicy)</span><span class="sxs-lookup"><span data-stu-id="503ed-132">If successful, the response body contains a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource.</span></span>

<span data-ttu-id="503ed-133">**Códigos de sucesso e erro de resposta**</span><span class="sxs-lookup"><span data-stu-id="503ed-133">**Response success and error codes**</span></span>

<span data-ttu-id="503ed-134">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="503ed-134">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="503ed-135">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="503ed-135">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="503ed-136">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="503ed-136">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="503ed-137">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="503ed-137">This method returns the following error codes:</span></span>

| <span data-ttu-id="503ed-138">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="503ed-138">HTTP Status Code</span></span>     | <span data-ttu-id="503ed-139">Código de erro</span><span class="sxs-lookup"><span data-stu-id="503ed-139">Error code</span></span>   | <span data-ttu-id="503ed-140">Description</span><span class="sxs-lookup"><span data-stu-id="503ed-140">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="503ed-141">404</span><span class="sxs-lookup"><span data-stu-id="503ed-141">404</span></span>                  | <span data-ttu-id="503ed-142">600039</span><span class="sxs-lookup"><span data-stu-id="503ed-142">600039</span></span>       | <span data-ttu-id="503ed-143">A política de autosserviço não encontrada.</span><span class="sxs-lookup"><span data-stu-id="503ed-143">Self-serve policy not found.</span></span>                                                     |

<span data-ttu-id="503ed-144">**Exemplo de resposta**</span><span class="sxs-lookup"><span data-stu-id="503ed-144">**Response example**</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1918
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
Date: Tue, 23 Jan 2018 23:13:01 GMT

{
    "id": "634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415",
    "selfServeEntity": {
        "selfServeEntityType": "customer",
        "tenantID": "0431a72c-7d8a-4393-b25e-ef63f5efb415"
    },
    "grantor": {
        "grantorType": "billToPartner",
        "tenantID": "634f6379-ad54-449b-9821-564f737158ab"
    },
    "permissions": [{
        "resource": "AzureReservedInstances",
        "action": "Purchase"
    }],
    "attributes": {
        "etag": "\"933523d1-3f63-4fc3-8789-5e21c02cdaed\"",
        "objectType": "SelfServePolicy"
    }
}
```