---
title: Excluir uma política de autosserviço
description: Como apagar uma política de autosserviço.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 063cf98d4c78e82622e486427baeb1a5721715e5
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973099"
---
# <a name="delete-a-selfservepolicy"></a><span data-ttu-id="1dc33-103">Excluir uma AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="1dc33-103">Delete a SelfServePolicy</span></span>

<span data-ttu-id="1dc33-104">Este artigo explica como atualizar uma política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="1dc33-104">This article explains how to update a self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1dc33-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1dc33-105">Prerequisites</span></span>

- <span data-ttu-id="1dc33-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1dc33-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1dc33-107">Este cenário suporta a autenticação com credenciais de Aplicação+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="1dc33-107">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="1dc33-108">C\#</span><span class="sxs-lookup"><span data-stu-id="1dc33-108">C\#</span></span>

<span data-ttu-id="1dc33-109">Para eliminar uma política de autosserviço:</span><span class="sxs-lookup"><span data-stu-id="1dc33-109">To delete a self-serve policy:</span></span>

1. <span data-ttu-id="1dc33-110">Ligue para o método [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) com o identificador de entidade para recuperar uma interface para operações nas políticas.</span><span class="sxs-lookup"><span data-stu-id="1dc33-110">Call the [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

2. <span data-ttu-id="1dc33-111">Ligue para o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.delete) ou [**EliminarAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.deleteasync) para eliminar a política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="1dc33-111">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.deleteasync) method to delete the self-serve policy.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
string policyId;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// deletes the self-serve policies
partnerOperations.SelfServePolicies.ById(policyId).Delete();
```

<span data-ttu-id="1dc33-112">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1dc33-112">For an example, see the following:</span></span>

- <span data-ttu-id="1dc33-113">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="1dc33-113">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="1dc33-114">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="1dc33-114">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="1dc33-115">Classe: **DeleteSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="1dc33-115">Class: **DeleteSelfServePolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="1dc33-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="1dc33-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1dc33-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="1dc33-117">Request syntax</span></span>

| <span data-ttu-id="1dc33-118">Método</span><span class="sxs-lookup"><span data-stu-id="1dc33-118">Method</span></span>  | <span data-ttu-id="1dc33-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="1dc33-119">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="1dc33-120">**EXCLUIR**</span><span class="sxs-lookup"><span data-stu-id="1dc33-120">**DELETE**</span></span> | <span data-ttu-id="1dc33-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1dc33-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span></span> |

<span data-ttu-id="1dc33-122">**Parâmetro URI**</span><span class="sxs-lookup"><span data-stu-id="1dc33-122">**URI parameter**</span></span>

<span data-ttu-id="1dc33-123">Utilize os seguintes parâmetros de trajetória para obter o produto especificado.</span><span class="sxs-lookup"><span data-stu-id="1dc33-123">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="1dc33-124">Nome</span><span class="sxs-lookup"><span data-stu-id="1dc33-124">Name</span></span>                       | <span data-ttu-id="1dc33-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="1dc33-125">Type</span></span>         | <span data-ttu-id="1dc33-126">Necessário</span><span class="sxs-lookup"><span data-stu-id="1dc33-126">Required</span></span> | <span data-ttu-id="1dc33-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dc33-127">Description</span></span>                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="1dc33-128">**SelfServePolicy-id**</span><span class="sxs-lookup"><span data-stu-id="1dc33-128">**SelfServePolicy-id**</span></span>     | <span data-ttu-id="1dc33-129">**string**</span><span class="sxs-lookup"><span data-stu-id="1dc33-129">**string**</span></span>   | <span data-ttu-id="1dc33-130">Yes</span><span class="sxs-lookup"><span data-stu-id="1dc33-130">Yes</span></span>      | <span data-ttu-id="1dc33-131">Uma corda que identifica a política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="1dc33-131">A string that identifies the self-serve policy.</span></span>                 |

### <a name="request-headers"></a><span data-ttu-id="1dc33-132">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="1dc33-132">Request headers</span></span>

- <span data-ttu-id="1dc33-133">É necessária uma identificação de pedido e uma identificação de correlação.</span><span class="sxs-lookup"><span data-stu-id="1dc33-133">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="1dc33-134">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1dc33-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1dc33-135">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="1dc33-135">Request body</span></span>

<span data-ttu-id="1dc33-136">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1dc33-136">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="1dc33-137">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="1dc33-137">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="1dc33-138">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="1dc33-138">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1dc33-139">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="1dc33-139">Response success and error codes</span></span>

<span data-ttu-id="1dc33-140">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="1dc33-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1dc33-141">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="1dc33-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1dc33-142">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="1dc33-142">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1dc33-143">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="1dc33-143">Response example</span></span>

```http
HTTP/1.1 204 deleted
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

```
