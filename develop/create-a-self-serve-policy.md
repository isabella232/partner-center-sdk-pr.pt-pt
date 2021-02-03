---
title: Criar uma política de autosserviço
description: Como criar uma nova política de autosserviço.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fd1579b2775ead57a440db0d6afb3bf22164c319
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2020
ms.locfileid: "97770216"
---
# <a name="create-a-selfservepolicy"></a><span data-ttu-id="6fa1d-103">Criar uma AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="6fa1d-103">Create a SelfServePolicy</span></span>

<span data-ttu-id="6fa1d-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="6fa1d-104">**Applies to:**</span></span>

- <span data-ttu-id="6fa1d-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="6fa1d-105">Partner Center</span></span>

<span data-ttu-id="6fa1d-106">Este tópico explica como criar uma nova política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-106">This topic explains how to create a new self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6fa1d-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6fa1d-107">Prerequisites</span></span>

- <span data-ttu-id="6fa1d-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6fa1d-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6fa1d-109">Este cenário suporta a autenticação com credenciais de Aplicação+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-109">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="6fa1d-110">C\#</span><span class="sxs-lookup"><span data-stu-id="6fa1d-110">C\#</span></span>

<span data-ttu-id="6fa1d-111">Criar uma política de autosserviço:</span><span class="sxs-lookup"><span data-stu-id="6fa1d-111">Create a self-serve policy:</span></span>

1. <span data-ttu-id="6fa1d-112">Ligue para o método [**IAggregatePartner.SelfServePolicies.Create**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.create) ou [**IAggregatePartner.SelfServePolicies.CreateAsync**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.createasync) com a informação de política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-112">Call the [**IAggregatePartner.SelfServePolicies.Create**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.create) or [**IAggregatePartner.SelfServePolicies.CreateAsync**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.createasync) method with the self-serve policy info.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
string customerIdAsEntity;

var selfServePolicy = new SelfServePolicy
{
    SelfServeEntity = new SelfServeEntity
    {
        SelfServeEntityType = "customer",
        TenantID = customerIdAsEntity,
    },
    Grantor = new Grantor
    {
        GrantorType = "billToPartner",
        TenantID = partnerIdAsGrantor,
    },
    Permissions = new Permission[]
    {
        new Permission
        {
        Action = "Purchase",
        Resource = "AzureReservedInstances",
        },
    },
};

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// creates the self-serve policy
SelfServePolicy createdSelfServePolicy = scopedPartnerOperations.selfServePolicies.Create(selfServePolicy);
```

<span data-ttu-id="6fa1d-113">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6fa1d-113">For an example, see the following:</span></span>

- <span data-ttu-id="6fa1d-114">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="6fa1d-114">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="6fa1d-115">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="6fa1d-115">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="6fa1d-116">Classe: **CreateSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="6fa1d-116">Class: **CreateSelfServePolicies.cs**</span></span>


## <a name="rest-request"></a><span data-ttu-id="6fa1d-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6fa1d-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6fa1d-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fa1d-118">Request syntax</span></span>

| <span data-ttu-id="6fa1d-119">Método</span><span class="sxs-lookup"><span data-stu-id="6fa1d-119">Method</span></span>   | <span data-ttu-id="6fa1d-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6fa1d-120">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="6fa1d-121">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="6fa1d-121">**POST**</span></span> | <span data-ttu-id="6fa1d-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6fa1d-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6fa1d-123">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6fa1d-123">Request headers</span></span>

- <span data-ttu-id="6fa1d-124">É necessária uma identificação de pedido e uma identificação de correlação.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-124">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="6fa1d-125">Consulte [os cabeçalhos REST do Partner Center](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-125">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="6fa1d-126">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6fa1d-126">Request body</span></span>

<span data-ttu-id="6fa1d-127">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-127">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="6fa1d-128">Nome</span><span class="sxs-lookup"><span data-stu-id="6fa1d-128">Name</span></span>                              | <span data-ttu-id="6fa1d-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="6fa1d-129">Type</span></span>   | <span data-ttu-id="6fa1d-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fa1d-130">Description</span></span>                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="6fa1d-131">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="6fa1d-131">SelfServePolicy</span></span>](self-serve-policy-resources.md#selfservepolicy)| <span data-ttu-id="6fa1d-132">objeto</span><span class="sxs-lookup"><span data-stu-id="6fa1d-132">object</span></span> | <span data-ttu-id="6fa1d-133">A informação política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-133">The self-serve policy information.</span></span> |

#### <a name="selfservepolicy"></a><span data-ttu-id="6fa1d-134">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="6fa1d-134">SelfServePolicy</span></span>

<span data-ttu-id="6fa1d-135">Esta tabela descreve os campos mínimos exigidos do recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) necessário para criar uma nova política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-135">This table describes the minimum required fields from the [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource needed to create a new self-serve policy.</span></span>

| <span data-ttu-id="6fa1d-136">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6fa1d-136">Property</span></span>              | <span data-ttu-id="6fa1d-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="6fa1d-137">Type</span></span>             | <span data-ttu-id="6fa1d-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fa1d-138">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6fa1d-139">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="6fa1d-139">SelfServeEntity</span></span>       | <span data-ttu-id="6fa1d-140">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="6fa1d-140">SelfServeEntity</span></span>  | <span data-ttu-id="6fa1d-141">A entidade self-serve a quem está a ser concedido acesso.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-141">The self-serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="6fa1d-142">Grantor</span><span class="sxs-lookup"><span data-stu-id="6fa1d-142">Grantor</span></span>               | <span data-ttu-id="6fa1d-143">Grantor</span><span class="sxs-lookup"><span data-stu-id="6fa1d-143">Grantor</span></span>          | <span data-ttu-id="6fa1d-144">O concededor que está a conceder acesso.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-144">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="6fa1d-145">Permissões</span><span class="sxs-lookup"><span data-stu-id="6fa1d-145">Permissions</span></span>           | <span data-ttu-id="6fa1d-146">Matriz de Permissão</span><span class="sxs-lookup"><span data-stu-id="6fa1d-146">Array of Permission</span></span>| <span data-ttu-id="6fa1d-147">Um conjunto de recursos [de permissão.](self-serve-policy-resources.md#permission)</span><span class="sxs-lookup"><span data-stu-id="6fa1d-147">An Array of [Permission](self-serve-policy-resources.md#permission) resources.</span></span>                                                                     |


### <a name="request-example"></a><span data-ttu-id="6fa1d-148">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6fa1d-148">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/SelfServePolicy HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 789
Expect: 100-continue
Connection: Keep-Alive

{
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
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="6fa1d-149">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6fa1d-149">REST response</span></span>

<span data-ttu-id="6fa1d-150">Se for bem sucedido, esta API devolve um recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) para a nova política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-150">If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the new self-serve policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6fa1d-151">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6fa1d-151">Response success and error codes</span></span>

<span data-ttu-id="6fa1d-152">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6fa1d-153">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6fa1d-154">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6fa1d-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

<span data-ttu-id="6fa1d-155">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="6fa1d-155">This method returns the following error codes:</span></span>

| <span data-ttu-id="6fa1d-156">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="6fa1d-156">HTTP Status Code</span></span>     | <span data-ttu-id="6fa1d-157">Código de erro</span><span class="sxs-lookup"><span data-stu-id="6fa1d-157">Error code</span></span>   | <span data-ttu-id="6fa1d-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fa1d-158">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="6fa1d-159">409</span><span class="sxs-lookup"><span data-stu-id="6fa1d-159">409</span></span>                  | <span data-ttu-id="6fa1d-160">600041</span><span class="sxs-lookup"><span data-stu-id="6fa1d-160">600041</span></span>       | <span data-ttu-id="6fa1d-161">A política de autosserviço já existe.</span><span class="sxs-lookup"><span data-stu-id="6fa1d-161">Self-serve policy already exists.</span></span>                                                     |


### <a name="response-example"></a><span data-ttu-id="6fa1d-162">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6fa1d-162">Response example</span></span>

```http
HTTP/1.1 201 Created
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
        "etag": "\"933523d1-3f63-4fc3-8789-5e21c02cdaed\"",
        "objectType": "SelfServePolicy"
    }
}
```
