---
title: Obtenha uma lista de políticas de autosserviço
description: Como obter uma coleção de recursos que representam as políticas de autosserviço de um cliente.
ms.date: 07/06/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ff3116b8757e28e03615930ebd19bc75f34e2efe
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2020
ms.locfileid: "97770240"
---
# <a name="get-a-list-of-self-serve-policies"></a><span data-ttu-id="310f7-103">Obtenha uma lista de políticas de autosserviço</span><span class="sxs-lookup"><span data-stu-id="310f7-103">Get a list of self-serve policies</span></span>

<span data-ttu-id="310f7-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="310f7-104">**Applies to:**</span></span>

- <span data-ttu-id="310f7-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="310f7-105">Partner Center</span></span>

<span data-ttu-id="310f7-106">Este artigo descreve como obter uma coleção de recursos que representa políticas de autosserviço para uma entidade.</span><span class="sxs-lookup"><span data-stu-id="310f7-106">This article describes how to get a collection of resources that represents self-serve policies for an entity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="310f7-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="310f7-107">Prerequisites</span></span>

- <span data-ttu-id="310f7-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="310f7-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="310f7-109">Este cenário suporta a autenticação com credenciais de Aplicação+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="310f7-109">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="310f7-110">C\#</span><span class="sxs-lookup"><span data-stu-id="310f7-110">C\#</span></span>

<span data-ttu-id="310f7-111">Para obter uma lista de todas as políticas de autosserviço:</span><span class="sxs-lookup"><span data-stu-id="310f7-111">To get a list of all self-serve policies:</span></span>

1. <span data-ttu-id="310f7-112">Ligue para o método [**IAggregatePartner.SelfServePolicies**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection) com o identificador de entidade para recuperar uma interface para operações nas políticas.</span><span class="sxs-lookup"><span data-stu-id="310f7-112">Call the [**IAggregatePartner.SelfServePolicies**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// gets the self-serve policies
var SelfServePolicies = scopedPartnerOperations.SelfServePolicies.Get(customerIdAsEntity);
```

<span data-ttu-id="310f7-113">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="310f7-113">For an example, see the following:</span></span>

- <span data-ttu-id="310f7-114">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="310f7-114">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="310f7-115">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="310f7-115">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="310f7-116">Classe: **GetSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="310f7-116">Class: **GetSelfServePolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="310f7-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="310f7-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="310f7-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="310f7-118">Request syntax</span></span>

| <span data-ttu-id="310f7-119">Método</span><span class="sxs-lookup"><span data-stu-id="310f7-119">Method</span></span>  | <span data-ttu-id="310f7-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="310f7-120">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="310f7-121">**Obter**</span><span class="sxs-lookup"><span data-stu-id="310f7-121">**GET**</span></span> | <span data-ttu-id="310f7-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy?entity_id={{entity_id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="310f7-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy?entity_id={entity_id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="310f7-123">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="310f7-123">URI parameter</span></span>

<span data-ttu-id="310f7-124">Use o seguinte parâmetro de consulta para obter uma lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="310f7-124">Use the following query parameter to get a list of customers.</span></span>

| <span data-ttu-id="310f7-125">Nome</span><span class="sxs-lookup"><span data-stu-id="310f7-125">Name</span></span>          | <span data-ttu-id="310f7-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="310f7-126">Type</span></span>       | <span data-ttu-id="310f7-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="310f7-127">Required</span></span> | <span data-ttu-id="310f7-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="310f7-128">Description</span></span>                                        |
|---------------|------------|----------|----------------------------------------------------|
| <span data-ttu-id="310f7-129">**entity_id**</span><span class="sxs-lookup"><span data-stu-id="310f7-129">**entity_id**</span></span> | <span data-ttu-id="310f7-130">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="310f7-130">**string**</span></span> | <span data-ttu-id="310f7-131">Y</span><span class="sxs-lookup"><span data-stu-id="310f7-131">Y</span></span>        | <span data-ttu-id="310f7-132">O identificador de entidade que solicita acesso.</span><span class="sxs-lookup"><span data-stu-id="310f7-132">The entity identifier requesting access for.</span></span> <span data-ttu-id="310f7-133">Esta será a identificação do inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="310f7-133">This will be the customer's tenant ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="310f7-134">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="310f7-134">Request headers</span></span>

<span data-ttu-id="310f7-135">Para obter mais informações, consulte [Headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="310f7-135">For more information, see [Headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="310f7-136">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="310f7-136">Request body</span></span>

<span data-ttu-id="310f7-137">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="310f7-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="310f7-138">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="310f7-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/SelfServePolicy?entity_id=0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="310f7-139">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="310f7-139">REST response</span></span>

<span data-ttu-id="310f7-140">Se for bem sucedido, este método devolve uma coleção de recursos [da SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="310f7-140">If successful, this method returns a collection of [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="310f7-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="310f7-141">Response success and error codes</span></span>

<span data-ttu-id="310f7-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="310f7-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="310f7-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="310f7-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="310f7-144">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="310f7-144">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="310f7-145">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="310f7-145">Response example</span></span>

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
