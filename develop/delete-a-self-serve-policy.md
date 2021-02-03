---
title: Excluir uma política de autosserviço
description: Como apagar uma política de autosserviço.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3450145d6daf2ffca5e2886245e592406cb0886d
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2020
ms.locfileid: "97770224"
---
# <a name="delete-a-selfservepolicy"></a><span data-ttu-id="69655-103">Excluir uma AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="69655-103">Delete a SelfServePolicy</span></span>

<span data-ttu-id="69655-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="69655-104">**Applies to:**</span></span>

- <span data-ttu-id="69655-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="69655-105">Partner Center</span></span>

<span data-ttu-id="69655-106">Este tópico explica como atualizar uma política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="69655-106">This topic explains how to update a self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="69655-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="69655-107">Prerequisites</span></span>

- <span data-ttu-id="69655-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="69655-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="69655-109">Este cenário suporta a autenticação com credenciais de Aplicação+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="69655-109">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="69655-110">C\#</span><span class="sxs-lookup"><span data-stu-id="69655-110">C\#</span></span>

<span data-ttu-id="69655-111">Para eliminar uma política de autosserviço:</span><span class="sxs-lookup"><span data-stu-id="69655-111">To delete a self-serve policy:</span></span>

1. <span data-ttu-id="69655-112">Ligue para o método [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) com o identificador de entidade para recuperar uma interface para operações nas políticas.</span><span class="sxs-lookup"><span data-stu-id="69655-112">Call the [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

2. <span data-ttu-id="69655-113">Ligue para o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.delete) ou [**EliminarAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.deleteasync) para eliminar a política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="69655-113">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.deleteasync) method to delete the self-serve policy.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
string policyId;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// deletes the self-serve policies
partnerOperations.SelfServePolicies.ById(policyId).Delete();
```

<span data-ttu-id="69655-114">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="69655-114">For an example, see the following:</span></span>

- <span data-ttu-id="69655-115">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="69655-115">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="69655-116">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="69655-116">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="69655-117">Classe: **DeleteSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="69655-117">Class: **DeleteSelfServePolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="69655-118">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="69655-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="69655-119">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="69655-119">Request syntax</span></span>

| <span data-ttu-id="69655-120">Método</span><span class="sxs-lookup"><span data-stu-id="69655-120">Method</span></span>  | <span data-ttu-id="69655-121">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="69655-121">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="69655-122">**EXCLUIR**</span><span class="sxs-lookup"><span data-stu-id="69655-122">**DELETE**</span></span> | <span data-ttu-id="69655-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="69655-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span></span> |

<span data-ttu-id="69655-124">**Parâmetro URI**</span><span class="sxs-lookup"><span data-stu-id="69655-124">**URI parameter**</span></span>

<span data-ttu-id="69655-125">Utilize os seguintes parâmetros de trajetória para obter o produto especificado.</span><span class="sxs-lookup"><span data-stu-id="69655-125">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="69655-126">Nome</span><span class="sxs-lookup"><span data-stu-id="69655-126">Name</span></span>                       | <span data-ttu-id="69655-127">Tipo</span><span class="sxs-lookup"><span data-stu-id="69655-127">Type</span></span>         | <span data-ttu-id="69655-128">Necessário</span><span class="sxs-lookup"><span data-stu-id="69655-128">Required</span></span> | <span data-ttu-id="69655-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="69655-129">Description</span></span>                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="69655-130">**SelfServePolicy-id**</span><span class="sxs-lookup"><span data-stu-id="69655-130">**SelfServePolicy-id**</span></span>     | <span data-ttu-id="69655-131">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="69655-131">**string**</span></span>   | <span data-ttu-id="69655-132">Sim</span><span class="sxs-lookup"><span data-stu-id="69655-132">Yes</span></span>      | <span data-ttu-id="69655-133">Uma corda que identifica a política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="69655-133">A string that identifies the self-serve policy.</span></span>                 |

### <a name="request-headers"></a><span data-ttu-id="69655-134">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="69655-134">Request headers</span></span>

- <span data-ttu-id="69655-135">É necessária uma identificação de pedido e uma identificação de correlação.</span><span class="sxs-lookup"><span data-stu-id="69655-135">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="69655-136">Consulte [os cabeçalhos REST do Partner Center](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="69655-136">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="69655-137">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="69655-137">Request body</span></span>

<span data-ttu-id="69655-138">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="69655-138">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="69655-139">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="69655-139">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/SelfServePolicy/634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 789
Connection: Keep-Alive

```

## <a name="rest-response"></a><span data-ttu-id="69655-140">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="69655-140">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="69655-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="69655-141">Response success and error codes</span></span>

<span data-ttu-id="69655-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="69655-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="69655-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="69655-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="69655-144">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="69655-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="69655-145">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="69655-145">Response example</span></span>

```http
HTTP/1.1 204 deleted
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

```
