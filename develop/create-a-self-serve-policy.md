---
title: Criar uma política de autosserviço
description: Como criar uma nova política de autosserviço.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 14f46e22fbd294c765b745204cf62474250cbfbd
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973694"
---
# <a name="create-a-selfservepolicy"></a><span data-ttu-id="a1023-103">Criar uma AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="a1023-103">Create a SelfServePolicy</span></span>

<span data-ttu-id="a1023-104">Este artigo explica como criar uma nova política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="a1023-104">This article explains how to create a new self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a1023-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a1023-105">Prerequisites</span></span>

- <span data-ttu-id="a1023-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a1023-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a1023-107">Este cenário suporta a autenticação com credenciais de Aplicação+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="a1023-107">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="a1023-108">C\#</span><span class="sxs-lookup"><span data-stu-id="a1023-108">C\#</span></span>

<span data-ttu-id="a1023-109">Criar uma política de autosserviço:</span><span class="sxs-lookup"><span data-stu-id="a1023-109">Create a self-serve policy:</span></span>

1. <span data-ttu-id="a1023-110">Ligue para o método [**IAggregatePartner.SelfServePolicies.Create**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.create) ou [**IAggregatePartner.SelfServePolicies.CreateAsync**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.createasync) com a informação de política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="a1023-110">Call the [**IAggregatePartner.SelfServePolicies.Create**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.create) or [**IAggregatePartner.SelfServePolicies.CreateAsync**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.createasync) method with the self-serve policy info.</span></span>

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

<span data-ttu-id="a1023-111">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a1023-111">For an example, see the following:</span></span>

- <span data-ttu-id="a1023-112">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="a1023-112">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="a1023-113">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="a1023-113">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="a1023-114">Classe: **CreateSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="a1023-114">Class: **CreateSelfServePolicies.cs**</span></span>


## <a name="rest-request"></a><span data-ttu-id="a1023-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="a1023-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a1023-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1023-116">Request syntax</span></span>

| <span data-ttu-id="a1023-117">Método</span><span class="sxs-lookup"><span data-stu-id="a1023-117">Method</span></span>   | <span data-ttu-id="a1023-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="a1023-118">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="a1023-119">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="a1023-119">**POST**</span></span> | <span data-ttu-id="a1023-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a1023-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a1023-121">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="a1023-121">Request headers</span></span>

- <span data-ttu-id="a1023-122">É necessária uma identificação de pedido e uma identificação de correlação.</span><span class="sxs-lookup"><span data-stu-id="a1023-122">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="a1023-123">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a1023-123">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a1023-124">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="a1023-124">Request body</span></span>

<span data-ttu-id="a1023-125">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="a1023-125">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="a1023-126">Nome</span><span class="sxs-lookup"><span data-stu-id="a1023-126">Name</span></span>                              | <span data-ttu-id="a1023-127">Tipo</span><span class="sxs-lookup"><span data-stu-id="a1023-127">Type</span></span>   | <span data-ttu-id="a1023-128">Description</span><span class="sxs-lookup"><span data-stu-id="a1023-128">Description</span></span>                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="a1023-129">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="a1023-129">SelfServePolicy</span></span>](self-serve-policy-resources.md#selfservepolicy)| <span data-ttu-id="a1023-130">objeto</span><span class="sxs-lookup"><span data-stu-id="a1023-130">object</span></span> | <span data-ttu-id="a1023-131">A informação política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="a1023-131">The self-serve policy information.</span></span> |

#### <a name="selfservepolicy"></a><span data-ttu-id="a1023-132">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="a1023-132">SelfServePolicy</span></span>

<span data-ttu-id="a1023-133">Esta tabela descreve os campos mínimos exigidos do recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) necessário para criar uma nova política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="a1023-133">This table describes the minimum required fields from the [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource needed to create a new self-serve policy.</span></span>

| <span data-ttu-id="a1023-134">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a1023-134">Property</span></span>              | <span data-ttu-id="a1023-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="a1023-135">Type</span></span>             | <span data-ttu-id="a1023-136">Description</span><span class="sxs-lookup"><span data-stu-id="a1023-136">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a1023-137">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="a1023-137">SelfServeEntity</span></span>       | <span data-ttu-id="a1023-138">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="a1023-138">SelfServeEntity</span></span>  | <span data-ttu-id="a1023-139">A entidade self-serve a quem está a ser concedido acesso.</span><span class="sxs-lookup"><span data-stu-id="a1023-139">The self-serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="a1023-140">Grantor</span><span class="sxs-lookup"><span data-stu-id="a1023-140">Grantor</span></span>               | <span data-ttu-id="a1023-141">Grantor</span><span class="sxs-lookup"><span data-stu-id="a1023-141">Grantor</span></span>          | <span data-ttu-id="a1023-142">O concededor que está a conceder acesso.</span><span class="sxs-lookup"><span data-stu-id="a1023-142">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="a1023-143">Permissões</span><span class="sxs-lookup"><span data-stu-id="a1023-143">Permissions</span></span>           | <span data-ttu-id="a1023-144">Matriz de Permissão</span><span class="sxs-lookup"><span data-stu-id="a1023-144">Array of Permission</span></span>| <span data-ttu-id="a1023-145">Um conjunto de recursos [de permissão.](self-serve-policy-resources.md#permission)</span><span class="sxs-lookup"><span data-stu-id="a1023-145">An Array of [Permission](self-serve-policy-resources.md#permission) resources.</span></span>                                                                     |


### <a name="request-example"></a><span data-ttu-id="a1023-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a1023-146">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="a1023-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="a1023-147">REST response</span></span>

<span data-ttu-id="a1023-148">Se for bem sucedido, esta API devolve um recurso [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) para a nova política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="a1023-148">If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the new self-serve policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a1023-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="a1023-149">Response success and error codes</span></span>

<span data-ttu-id="a1023-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="a1023-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a1023-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="a1023-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a1023-152">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="a1023-152">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

<span data-ttu-id="a1023-153">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="a1023-153">This method returns the following error codes:</span></span>

| <span data-ttu-id="a1023-154">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="a1023-154">HTTP Status Code</span></span>     | <span data-ttu-id="a1023-155">Código de erro</span><span class="sxs-lookup"><span data-stu-id="a1023-155">Error code</span></span>   | <span data-ttu-id="a1023-156">Description</span><span class="sxs-lookup"><span data-stu-id="a1023-156">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="a1023-157">409</span><span class="sxs-lookup"><span data-stu-id="a1023-157">409</span></span>                  | <span data-ttu-id="a1023-158">600041</span><span class="sxs-lookup"><span data-stu-id="a1023-158">600041</span></span>       | <span data-ttu-id="a1023-159">A política de autosserviço já existe.</span><span class="sxs-lookup"><span data-stu-id="a1023-159">Self-serve policy already exists.</span></span>                                                     |


### <a name="response-example"></a><span data-ttu-id="a1023-160">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a1023-160">Response example</span></span>

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
