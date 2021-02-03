---
title: Obter uma política de self-service por ID
description: Obtém a política de autosserviço especificada utilizando o seu ID.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ec01d0d9b7c3858cdacf1dbaad3b2b0bb7b6a1a4
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769086"
---
# <a name="get-a-self-serve-policy-by-id"></a><span data-ttu-id="c3098-103">Obter uma política de self-service por ID</span><span class="sxs-lookup"><span data-stu-id="c3098-103">Get a self serve policy by ID</span></span>

<span data-ttu-id="c3098-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="c3098-104">**Applies To**</span></span>

- <span data-ttu-id="c3098-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="c3098-105">Partner Center</span></span>

<span data-ttu-id="c3098-106">Obtém a política de autosserviço especificada utilizando o seu ID.</span><span class="sxs-lookup"><span data-stu-id="c3098-106">Gets the specified self serve policy using its ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3098-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c3098-107">Prerequisites</span></span>

- <span data-ttu-id="c3098-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c3098-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c3098-109">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="c3098-109">This scenario supports authentication with App+User credentials.</span></span>
- <span data-ttu-id="c3098-110">Uma identificação de autosserviço da política.</span><span class="sxs-lookup"><span data-stu-id="c3098-110">A self serve policy ID.</span></span>

## <a name="examples"></a><span data-ttu-id="c3098-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c3098-111">Examples</span></span>


## <a name="span-idrest_requestspan-idrest_requestspan-idrest_requestrest-request"></a><span data-ttu-id="c3098-112"><span id="REST_Request"/><span id="rest_request"/><span id="REST_REQUEST"/>Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c3098-112"><span id="REST_Request"/><span id="rest_request"/><span id="REST_REQUEST"/>REST Request</span></span>

<span data-ttu-id="c3098-113">**Solicitar sintaxe**</span><span class="sxs-lookup"><span data-stu-id="c3098-113">**Request syntax**</span></span>

| <span data-ttu-id="c3098-114">Método</span><span class="sxs-lookup"><span data-stu-id="c3098-114">Method</span></span>  | <span data-ttu-id="c3098-115">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c3098-115">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="c3098-116">**Obter**</span><span class="sxs-lookup"><span data-stu-id="c3098-116">**GET**</span></span> | <span data-ttu-id="c3098-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c3098-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span></span> |

<span data-ttu-id="c3098-118">**Parâmetro URI**</span><span class="sxs-lookup"><span data-stu-id="c3098-118">**URI parameter**</span></span>

<span data-ttu-id="c3098-119">Utilize os seguintes parâmetros de trajetória para obter o produto especificado.</span><span class="sxs-lookup"><span data-stu-id="c3098-119">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="c3098-120">Nome</span><span class="sxs-lookup"><span data-stu-id="c3098-120">Name</span></span>                       | <span data-ttu-id="c3098-121">Tipo</span><span class="sxs-lookup"><span data-stu-id="c3098-121">Type</span></span>         | <span data-ttu-id="c3098-122">Necessário</span><span class="sxs-lookup"><span data-stu-id="c3098-122">Required</span></span> | <span data-ttu-id="c3098-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3098-123">Description</span></span>                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="c3098-124">**SelfServePolicy-id**</span><span class="sxs-lookup"><span data-stu-id="c3098-124">**SelfServePolicy-id**</span></span>     | <span data-ttu-id="c3098-125">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="c3098-125">**string**</span></span>   | <span data-ttu-id="c3098-126">Sim</span><span class="sxs-lookup"><span data-stu-id="c3098-126">Yes</span></span>      | <span data-ttu-id="c3098-127">Uma corda que identifica a política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="c3098-127">A string that identifies the self serve policy.</span></span>                 |

<span data-ttu-id="c3098-128">**Cabeçalhos do pedido**</span><span class="sxs-lookup"><span data-stu-id="c3098-128">**Request headers**</span></span>

- <span data-ttu-id="c3098-129">Consulte [os Cabeçalhos](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c3098-129">See [Headers](headers.md) for more information.</span></span>

<span data-ttu-id="c3098-130">**Corpo de pedido**</span><span class="sxs-lookup"><span data-stu-id="c3098-130">**Request body**</span></span>

<span data-ttu-id="c3098-131">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c3098-131">None.</span></span>

<span data-ttu-id="c3098-132">**Exemplo de pedido**</span><span class="sxs-lookup"><span data-stu-id="c3098-132">**Request example**</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/SelfServePolicy/634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer  <token>
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="c3098-133">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c3098-133">REST response</span></span>

<span data-ttu-id="c3098-134">Se for bem sucedido, o corpo de resposta contém um recurso [SelfServePolicy.](self-serve-policy-resources.md#selfservepolicy)</span><span class="sxs-lookup"><span data-stu-id="c3098-134">If successful, the response body contains a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource.</span></span>

<span data-ttu-id="c3098-135">**Códigos de sucesso e erro de resposta**</span><span class="sxs-lookup"><span data-stu-id="c3098-135">**Response success and error codes**</span></span>

<span data-ttu-id="c3098-136">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c3098-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c3098-137">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c3098-137">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c3098-138">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c3098-138">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="c3098-139">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="c3098-139">This method returns the following error codes:</span></span>

| <span data-ttu-id="c3098-140">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="c3098-140">HTTP Status Code</span></span>     | <span data-ttu-id="c3098-141">Código de erro</span><span class="sxs-lookup"><span data-stu-id="c3098-141">Error code</span></span>   | <span data-ttu-id="c3098-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3098-142">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="c3098-143">404</span><span class="sxs-lookup"><span data-stu-id="c3098-143">404</span></span>                  | <span data-ttu-id="c3098-144">600039</span><span class="sxs-lookup"><span data-stu-id="c3098-144">600039</span></span>       | <span data-ttu-id="c3098-145">A política de autosserviço não encontrada.</span><span class="sxs-lookup"><span data-stu-id="c3098-145">Self serve policy not found.</span></span>                                                     |

<span data-ttu-id="c3098-146">**Exemplo de resposta**</span><span class="sxs-lookup"><span data-stu-id="c3098-146">**Response example**</span></span>

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