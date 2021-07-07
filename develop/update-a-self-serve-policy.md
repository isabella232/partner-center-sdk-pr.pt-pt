---
title: Atualizar uma política de autosserviço
description: Como atualizar uma política de autosserviço.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d94382e73fd2a79751fe5f8f8414df2befde584f
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445260"
---
# <a name="update-a-selfservepolicy"></a><span data-ttu-id="9b8ab-103">Atualizar uma AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="9b8ab-103">Update a SelfServePolicy</span></span>

<span data-ttu-id="9b8ab-104">Este artigo explica como atualizar uma política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-104">This article explains how to update a self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b8ab-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9b8ab-105">Prerequisites</span></span>

- <span data-ttu-id="9b8ab-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9b8ab-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9b8ab-107">Este cenário suporta a autenticação com credenciais de Aplicação+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-107">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="9b8ab-108">C\#</span><span class="sxs-lookup"><span data-stu-id="9b8ab-108">C\#</span></span>

<span data-ttu-id="9b8ab-109">Para eliminar uma política de autosserviço:</span><span class="sxs-lookup"><span data-stu-id="9b8ab-109">To delete a self-serve policy:</span></span>

1. <span data-ttu-id="9b8ab-110">Ligue para o método [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) com o identificador de entidade para recuperar uma interface para operações nas políticas.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-110">Call the [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

2. <span data-ttu-id="9b8ab-111">Ligue para o método [**Put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) ou [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) para atualizar a política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-111">Call the [**Put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) or [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) method to update the self-serve policy.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
SelfServePolicy policy;

// All the operations executed on this partner operation instance will share the same correlation identifier but will differ in request identifier
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// updates the self-serve policies
partnerOperations.SelfServePolicies.ById(policy.id).Put(policy);
```

## <a name="rest-request"></a><span data-ttu-id="9b8ab-112">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="9b8ab-112">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9b8ab-113">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b8ab-113">Request syntax</span></span>

| <span data-ttu-id="9b8ab-114">Método</span><span class="sxs-lookup"><span data-stu-id="9b8ab-114">Method</span></span>   | <span data-ttu-id="9b8ab-115">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="9b8ab-115">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="9b8ab-116">**PUT**</span><span class="sxs-lookup"><span data-stu-id="9b8ab-116">**PUT**</span></span> | <span data-ttu-id="9b8ab-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9b8ab-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9b8ab-118">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="9b8ab-118">Request headers</span></span>

- <span data-ttu-id="9b8ab-119">É necessário um identificador de pedido e um identificador de correlação.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-119">A request identifier and correlation identifier are required.</span></span>
- <span data-ttu-id="9b8ab-120">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9b8ab-120">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9b8ab-121">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="9b8ab-121">Request body</span></span>

<span data-ttu-id="9b8ab-122">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-122">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="9b8ab-123">Nome</span><span class="sxs-lookup"><span data-stu-id="9b8ab-123">Name</span></span>                              | <span data-ttu-id="9b8ab-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="9b8ab-124">Type</span></span>   | <span data-ttu-id="9b8ab-125">Description</span><span class="sxs-lookup"><span data-stu-id="9b8ab-125">Description</span></span>                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="9b8ab-126">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="9b8ab-126">SelfServePolicy</span></span>](self-serve-policy-resources.md#selfservepolicy)| <span data-ttu-id="9b8ab-127">objeto</span><span class="sxs-lookup"><span data-stu-id="9b8ab-127">object</span></span> | <span data-ttu-id="9b8ab-128">A informação política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-128">The self-serve policy information.</span></span> |

#### <a name="selfservepolicy"></a><span data-ttu-id="9b8ab-129">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="9b8ab-129">SelfServePolicy</span></span>

<span data-ttu-id="9b8ab-130">Esta tabela descreve os campos mínimos exigidos do recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) necessário para criar uma nova política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-130">This table describes the minimum required fields from the [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource needed to create a new self-serve policy.</span></span>

| <span data-ttu-id="9b8ab-131">Propriedade</span><span class="sxs-lookup"><span data-stu-id="9b8ab-131">Property</span></span>              | <span data-ttu-id="9b8ab-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="9b8ab-132">Type</span></span>             | <span data-ttu-id="9b8ab-133">Description</span><span class="sxs-lookup"><span data-stu-id="9b8ab-133">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9b8ab-134">ID</span><span class="sxs-lookup"><span data-stu-id="9b8ab-134">id</span></span>                    | <span data-ttu-id="9b8ab-135">string</span><span class="sxs-lookup"><span data-stu-id="9b8ab-135">string</span></span>           | <span data-ttu-id="9b8ab-136">Um identificador de política de autosserviço que é fornecido após a criação bem sucedida da política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-136">A self-serve policy identifier that is supplied upon successful creation of the self-serve policy.</span></span>     |
| <span data-ttu-id="9b8ab-137">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="9b8ab-137">SelfServeEntity</span></span>       | <span data-ttu-id="9b8ab-138">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="9b8ab-138">SelfServeEntity</span></span>  | <span data-ttu-id="9b8ab-139">A entidade self-serve a quem está a ser concedido acesso.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-139">The self-serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="9b8ab-140">Grantor</span><span class="sxs-lookup"><span data-stu-id="9b8ab-140">Grantor</span></span>               | <span data-ttu-id="9b8ab-141">Grantor</span><span class="sxs-lookup"><span data-stu-id="9b8ab-141">Grantor</span></span>          | <span data-ttu-id="9b8ab-142">O concededor que está a conceder acesso.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-142">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="9b8ab-143">Permissões</span><span class="sxs-lookup"><span data-stu-id="9b8ab-143">Permissions</span></span>           | <span data-ttu-id="9b8ab-144">Matriz de Permissão</span><span class="sxs-lookup"><span data-stu-id="9b8ab-144">Array of Permission</span></span>| <span data-ttu-id="9b8ab-145">Um conjunto de recursos [de permissão.](self-serve-policy-resources.md#permission)</span><span class="sxs-lookup"><span data-stu-id="9b8ab-145">An Array of [Permission](self-serve-policy-resources.md#permission) resources.</span></span>                                                      |
| <span data-ttu-id="9b8ab-146">Etag</span><span class="sxs-lookup"><span data-stu-id="9b8ab-146">Etag</span></span>                  | <span data-ttu-id="9b8ab-147">string</span><span class="sxs-lookup"><span data-stu-id="9b8ab-147">string</span></span>           | <span data-ttu-id="9b8ab-148">O Etag.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-148">The Etag.</span></span>                                                                                               |


### <a name="request-example"></a><span data-ttu-id="9b8ab-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="9b8ab-149">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/SelfServePolicy HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive

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

## <a name="rest-response"></a><span data-ttu-id="9b8ab-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="9b8ab-150">REST response</span></span>

<span data-ttu-id="9b8ab-151">Se for bem sucedido, esta API devolve um recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) para a política de autosserviço atualizada.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-151">If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the updated self-serve policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9b8ab-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="9b8ab-152">Response success and error codes</span></span>

<span data-ttu-id="9b8ab-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9b8ab-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="9b8ab-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9b8ab-155">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="9b8ab-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

<span data-ttu-id="9b8ab-156">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="9b8ab-156">This method returns the following error codes:</span></span>

| <span data-ttu-id="9b8ab-157">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="9b8ab-157">HTTP Status Code</span></span>     | <span data-ttu-id="9b8ab-158">Código de erro</span><span class="sxs-lookup"><span data-stu-id="9b8ab-158">Error code</span></span>   | <span data-ttu-id="9b8ab-159">Description</span><span class="sxs-lookup"><span data-stu-id="9b8ab-159">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="9b8ab-160">404</span><span class="sxs-lookup"><span data-stu-id="9b8ab-160">404</span></span>                  | <span data-ttu-id="9b8ab-161">600039</span><span class="sxs-lookup"><span data-stu-id="9b8ab-161">600039</span></span>       | <span data-ttu-id="9b8ab-162">A política de autosserviço não foi encontrada</span><span class="sxs-lookup"><span data-stu-id="9b8ab-162">Self-serve policy was not found</span></span>                                            |
| <span data-ttu-id="9b8ab-163">404</span><span class="sxs-lookup"><span data-stu-id="9b8ab-163">404</span></span>                  | <span data-ttu-id="9b8ab-164">600040</span><span class="sxs-lookup"><span data-stu-id="9b8ab-164">600040</span></span>       | <span data-ttu-id="9b8ab-165">O identificador de política de autosserviço está incorreto</span><span class="sxs-lookup"><span data-stu-id="9b8ab-165">Self-serve policy identifier is incorrect</span></span>                                  |


### <a name="response-example"></a><span data-ttu-id="9b8ab-166">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="9b8ab-166">Response example</span></span>

```http
HTTP/1.1 200 Ok
Content-Length: 834
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

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
        "etag": "\"1ec98034-a249-46f4-b9dd-9cd464fb5e47\"",
        "objectType": "SelfServePolicy"
    }
}
```
