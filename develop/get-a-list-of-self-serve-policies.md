---
title: Obtenha uma lista de políticas de autosserviço
description: Como obter uma coleção de recursos que representam as políticas de autosserviço de um cliente.
ms.date: 07/06/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b18fde8a11d3ed3dd31e50fdba746dd6b0bf3f97
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025738"
---
# <a name="get-a-list-of-self-serve-policies"></a><span data-ttu-id="0f1fe-103">Obtenha uma lista de políticas de autosserviço</span><span class="sxs-lookup"><span data-stu-id="0f1fe-103">Get a list of self-serve policies</span></span>

<span data-ttu-id="0f1fe-104">Obtém uma coleção de recursos que representa políticas de autosserviço para uma entidade.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-104">Gets a collection of resources that represents self-serve policies for an entity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f1fe-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0f1fe-105">Prerequisites</span></span>

- <span data-ttu-id="0f1fe-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0f1fe-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0f1fe-107">Este cenário suporta a autenticação com credenciais de Aplicação+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-107">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="0f1fe-108">C\#</span><span class="sxs-lookup"><span data-stu-id="0f1fe-108">C\#</span></span>

<span data-ttu-id="0f1fe-109">Para obter uma lista de todas as políticas de autosserviço:</span><span class="sxs-lookup"><span data-stu-id="0f1fe-109">To get a list of all self-serve policies:</span></span>

1. <span data-ttu-id="0f1fe-110">Ligue para o método [**IAggregatePartner.SelfServePolicies**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection) com o identificador de entidade para recuperar uma interface para operações nas políticas.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-110">Call the [**IAggregatePartner.SelfServePolicies**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// gets the self-serve policies
var SelfServePolicies = scopedPartnerOperations.SelfServePolicies.Get(customerIdAsEntity);
```

<span data-ttu-id="0f1fe-111">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f1fe-111">For an example, see the following:</span></span>

- <span data-ttu-id="0f1fe-112">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="0f1fe-112">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="0f1fe-113">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="0f1fe-113">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="0f1fe-114">Classe: **GetSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="0f1fe-114">Class: **GetSelfServePolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="0f1fe-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="0f1fe-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0f1fe-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f1fe-116">Request syntax</span></span>

| <span data-ttu-id="0f1fe-117">Método</span><span class="sxs-lookup"><span data-stu-id="0f1fe-117">Method</span></span>  | <span data-ttu-id="0f1fe-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="0f1fe-118">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="0f1fe-119">**Obter**</span><span class="sxs-lookup"><span data-stu-id="0f1fe-119">**GET**</span></span> | <span data-ttu-id="0f1fe-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy?entity_id={{entity_id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0f1fe-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy?entity_id={entity_id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="0f1fe-121">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="0f1fe-121">URI parameter</span></span>

<span data-ttu-id="0f1fe-122">Use o seguinte parâmetro de consulta para obter uma lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-122">Use the following query parameter to get a list of customers.</span></span>

| <span data-ttu-id="0f1fe-123">Nome</span><span class="sxs-lookup"><span data-stu-id="0f1fe-123">Name</span></span>          | <span data-ttu-id="0f1fe-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="0f1fe-124">Type</span></span>       | <span data-ttu-id="0f1fe-125">Necessário</span><span class="sxs-lookup"><span data-stu-id="0f1fe-125">Required</span></span> | <span data-ttu-id="0f1fe-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f1fe-126">Description</span></span>                                        |
|---------------|------------|----------|----------------------------------------------------|
| <span data-ttu-id="0f1fe-127">**entity_id**</span><span class="sxs-lookup"><span data-stu-id="0f1fe-127">**entity_id**</span></span> | <span data-ttu-id="0f1fe-128">**string**</span><span class="sxs-lookup"><span data-stu-id="0f1fe-128">**string**</span></span> | <span data-ttu-id="0f1fe-129">Y</span><span class="sxs-lookup"><span data-stu-id="0f1fe-129">Y</span></span>        | <span data-ttu-id="0f1fe-130">O identificador de entidade que solicita acesso.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-130">The entity identifier requesting access for.</span></span> <span data-ttu-id="0f1fe-131">Esta será a identificação do inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-131">This will be the customer's tenant ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="0f1fe-132">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="0f1fe-132">Request headers</span></span>

<span data-ttu-id="0f1fe-133">Para obter mais informações, consulte [Headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="0f1fe-133">For more information, see [Headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0f1fe-134">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="0f1fe-134">Request body</span></span>

<span data-ttu-id="0f1fe-135">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-135">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0f1fe-136">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="0f1fe-136">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/SelfServePolicy?entity_id=0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="0f1fe-137">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="0f1fe-137">REST response</span></span>

<span data-ttu-id="0f1fe-138">Se for bem sucedido, este método devolve uma coleção de recursos [da SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-138">If successful, this method returns a collection of [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0f1fe-139">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="0f1fe-139">Response success and error codes</span></span>

<span data-ttu-id="0f1fe-140">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0f1fe-141">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0f1fe-142">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="0f1fe-142">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0f1fe-143">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="0f1fe-143">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 15650
Content-Type: application/json
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
Date: Fri, 20 Nov 2015 01:08:23 GMT

{
    "totalCount": 1,
    "items": [{
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
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
