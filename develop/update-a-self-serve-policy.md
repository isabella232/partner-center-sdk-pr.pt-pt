---
title: Atualizar uma política de autosserviço
description: Como atualizar uma política de autosserviço.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4d53ab8e5b8ef5b7be83360a3f43ec7791b2e3b4
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2020
ms.locfileid: "97770248"
---
# <a name="update-a-selfservepolicy"></a><span data-ttu-id="f35bf-103">Atualizar uma AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="f35bf-103">Update a SelfServePolicy</span></span>

<span data-ttu-id="f35bf-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="f35bf-104">**Applies to:**</span></span>

- <span data-ttu-id="f35bf-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="f35bf-105">Partner Center</span></span>

<span data-ttu-id="f35bf-106">Este tópico explica como atualizar uma política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="f35bf-106">This topic explains how to update a self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f35bf-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f35bf-107">Prerequisites</span></span>

- <span data-ttu-id="f35bf-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f35bf-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f35bf-109">Este cenário suporta a autenticação com credenciais de Aplicação+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="f35bf-109">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="f35bf-110">C\#</span><span class="sxs-lookup"><span data-stu-id="f35bf-110">C\#</span></span>

<span data-ttu-id="f35bf-111">Para eliminar uma política de autosserviço:</span><span class="sxs-lookup"><span data-stu-id="f35bf-111">To delete a self-serve policy:</span></span>

1. <span data-ttu-id="f35bf-112">Ligue para o método [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) com o identificador de entidade para recuperar uma interface para operações nas políticas.</span><span class="sxs-lookup"><span data-stu-id="f35bf-112">Call the [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

2. <span data-ttu-id="f35bf-113">Ligue para o método [**Put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) ou [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) para atualizar a política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="f35bf-113">Call the [**Put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) or [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) method to update the self-serve policy.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
SelfServePolicy policy;

// All the operations executed on this partner operation instance will share the same correlation identifier but will differ in request identifier
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// updates the self-serve policies
partnerOperations.SelfServePolicies.ById(policy.id).Put(policy);
```

## <a name="rest-request"></a><span data-ttu-id="f35bf-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f35bf-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f35bf-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f35bf-115">Request syntax</span></span>

| <span data-ttu-id="f35bf-116">Método</span><span class="sxs-lookup"><span data-stu-id="f35bf-116">Method</span></span>   | <span data-ttu-id="f35bf-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f35bf-117">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="f35bf-118">**PUT**</span><span class="sxs-lookup"><span data-stu-id="f35bf-118">**PUT**</span></span> | <span data-ttu-id="f35bf-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f35bf-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f35bf-120">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="f35bf-120">Request headers</span></span>

- <span data-ttu-id="f35bf-121">É necessário um identificador de pedido e um identificador de correlação.</span><span class="sxs-lookup"><span data-stu-id="f35bf-121">A request identifier and correlation identifier are required.</span></span>
- <span data-ttu-id="f35bf-122">Consulte [os cabeçalhos REST do Partner Center](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f35bf-122">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="f35bf-123">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f35bf-123">Request body</span></span>

<span data-ttu-id="f35bf-124">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="f35bf-124">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="f35bf-125">Nome</span><span class="sxs-lookup"><span data-stu-id="f35bf-125">Name</span></span>                              | <span data-ttu-id="f35bf-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="f35bf-126">Type</span></span>   | <span data-ttu-id="f35bf-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="f35bf-127">Description</span></span>                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="f35bf-128">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="f35bf-128">SelfServePolicy</span></span>](self-serve-policy-resources.md#selfservepolicy)| <span data-ttu-id="f35bf-129">objeto</span><span class="sxs-lookup"><span data-stu-id="f35bf-129">object</span></span> | <span data-ttu-id="f35bf-130">A informação política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="f35bf-130">The self-serve policy information.</span></span> |

#### <a name="selfservepolicy"></a><span data-ttu-id="f35bf-131">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="f35bf-131">SelfServePolicy</span></span>

<span data-ttu-id="f35bf-132">Esta tabela descreve os campos mínimos exigidos do recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) necessário para criar uma nova política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="f35bf-132">This table describes the minimum required fields from the [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource needed to create a new self-serve policy.</span></span>

| <span data-ttu-id="f35bf-133">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f35bf-133">Property</span></span>              | <span data-ttu-id="f35bf-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="f35bf-134">Type</span></span>             | <span data-ttu-id="f35bf-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="f35bf-135">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f35bf-136">ID</span><span class="sxs-lookup"><span data-stu-id="f35bf-136">id</span></span>                    | <span data-ttu-id="f35bf-137">string</span><span class="sxs-lookup"><span data-stu-id="f35bf-137">string</span></span>           | <span data-ttu-id="f35bf-138">Um identificador de política de autosserviço que é fornecido após a criação bem sucedida da política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="f35bf-138">A self-serve policy identifier that is supplied upon successful creation of the self-serve policy.</span></span>     |
| <span data-ttu-id="f35bf-139">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="f35bf-139">SelfServeEntity</span></span>       | <span data-ttu-id="f35bf-140">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="f35bf-140">SelfServeEntity</span></span>  | <span data-ttu-id="f35bf-141">A entidade self-serve a quem está a ser concedido acesso.</span><span class="sxs-lookup"><span data-stu-id="f35bf-141">The self-serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="f35bf-142">Grantor</span><span class="sxs-lookup"><span data-stu-id="f35bf-142">Grantor</span></span>               | <span data-ttu-id="f35bf-143">Grantor</span><span class="sxs-lookup"><span data-stu-id="f35bf-143">Grantor</span></span>          | <span data-ttu-id="f35bf-144">O concededor que está a conceder acesso.</span><span class="sxs-lookup"><span data-stu-id="f35bf-144">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="f35bf-145">Permissões</span><span class="sxs-lookup"><span data-stu-id="f35bf-145">Permissions</span></span>           | <span data-ttu-id="f35bf-146">Matriz de Permissão</span><span class="sxs-lookup"><span data-stu-id="f35bf-146">Array of Permission</span></span>| <span data-ttu-id="f35bf-147">Um conjunto de recursos [de permissão.](self-serve-policy-resources.md#permission)</span><span class="sxs-lookup"><span data-stu-id="f35bf-147">An Array of [Permission](self-serve-policy-resources.md#permission) resources.</span></span>                                                      |
| <span data-ttu-id="f35bf-148">Etag</span><span class="sxs-lookup"><span data-stu-id="f35bf-148">Etag</span></span>                  | <span data-ttu-id="f35bf-149">string</span><span class="sxs-lookup"><span data-stu-id="f35bf-149">string</span></span>           | <span data-ttu-id="f35bf-150">O Etag.</span><span class="sxs-lookup"><span data-stu-id="f35bf-150">The Etag.</span></span>                                                                                               |


### <a name="request-example"></a><span data-ttu-id="f35bf-151">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f35bf-151">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="f35bf-152">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f35bf-152">REST response</span></span>

<span data-ttu-id="f35bf-153">Se for bem sucedido, esta API devolve um recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) para a política de autosserviço atualizada.</span><span class="sxs-lookup"><span data-stu-id="f35bf-153">If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the updated self-serve policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f35bf-154">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f35bf-154">Response success and error codes</span></span>

<span data-ttu-id="f35bf-155">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f35bf-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f35bf-156">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f35bf-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f35bf-157">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f35bf-157">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

<span data-ttu-id="f35bf-158">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="f35bf-158">This method returns the following error codes:</span></span>

| <span data-ttu-id="f35bf-159">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="f35bf-159">HTTP Status Code</span></span>     | <span data-ttu-id="f35bf-160">Código de erro</span><span class="sxs-lookup"><span data-stu-id="f35bf-160">Error code</span></span>   | <span data-ttu-id="f35bf-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="f35bf-161">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="f35bf-162">404</span><span class="sxs-lookup"><span data-stu-id="f35bf-162">404</span></span>                  | <span data-ttu-id="f35bf-163">600039</span><span class="sxs-lookup"><span data-stu-id="f35bf-163">600039</span></span>       | <span data-ttu-id="f35bf-164">A política de autosserviço não foi encontrada</span><span class="sxs-lookup"><span data-stu-id="f35bf-164">Self-serve policy was not found</span></span>                                            |
| <span data-ttu-id="f35bf-165">404</span><span class="sxs-lookup"><span data-stu-id="f35bf-165">404</span></span>                  | <span data-ttu-id="f35bf-166">600040</span><span class="sxs-lookup"><span data-stu-id="f35bf-166">600040</span></span>       | <span data-ttu-id="f35bf-167">O identificador de política de autosserviço está incorreto</span><span class="sxs-lookup"><span data-stu-id="f35bf-167">Self-serve policy identifier is incorrect</span></span>                                  |


### <a name="response-example"></a><span data-ttu-id="f35bf-168">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f35bf-168">Response example</span></span>

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
