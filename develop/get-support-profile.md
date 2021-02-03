---
title: Obter perfil de suporte
description: Obtém um objeto que representa o perfil de suporte de um utilizador.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b8b0fa533aaba74418985ea02cbb13bd722cede2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769806"
---
# <a name="get-support-profile"></a><span data-ttu-id="8a735-103">Obter perfil de suporte</span><span class="sxs-lookup"><span data-stu-id="8a735-103">Get support profile</span></span>

<span data-ttu-id="8a735-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="8a735-104">**Applies To**</span></span>

- <span data-ttu-id="8a735-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="8a735-105">Partner Center</span></span>
- <span data-ttu-id="8a735-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="8a735-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="8a735-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8a735-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8a735-108">Obtém um objeto que representa o perfil de suporte de um utilizador.</span><span class="sxs-lookup"><span data-stu-id="8a735-108">Gets an object representing a user's support profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a735-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8a735-109">Prerequisites</span></span>

- <span data-ttu-id="8a735-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8a735-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8a735-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="8a735-111">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="8a735-112">C\#</span><span class="sxs-lookup"><span data-stu-id="8a735-112">C\#</span></span>

<span data-ttu-id="8a735-113">Para obter o seu perfil de suporte, utilize a sua coleção **IAggregatePartner.Profiles.**</span><span class="sxs-lookup"><span data-stu-id="8a735-113">To get your support profile, use your **IAggregatePartner.Profiles** collection.</span></span> <span data-ttu-id="8a735-114">Ligue para a propriedade [**SupportProfile,**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) seguida dos métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.getasync)</span><span class="sxs-lookup"><span data-stu-id="8a735-114">Call the [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

SupportProfile supportProfile = partnerOperations.Profiles.SupportProfile.Get();
```

<span data-ttu-id="8a735-115">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="8a735-115">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="8a735-116">**Projeto**: PartnerCenterSDK.FeaturesSamples **Class**: GetSupportProfile.cs</span><span class="sxs-lookup"><span data-stu-id="8a735-116">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetSupportProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="8a735-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="8a735-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8a735-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a735-118">Request syntax</span></span>

| <span data-ttu-id="8a735-119">Método</span><span class="sxs-lookup"><span data-stu-id="8a735-119">Method</span></span>  | <span data-ttu-id="8a735-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="8a735-120">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="8a735-121">**Obter**</span><span class="sxs-lookup"><span data-stu-id="8a735-121">**GET**</span></span> | <span data-ttu-id="8a735-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/suporte HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8a735-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/support HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8a735-123">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="8a735-123">Request headers</span></span>

<span data-ttu-id="8a735-124">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8a735-124">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8a735-125">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="8a735-125">Request body</span></span>

<span data-ttu-id="8a735-126">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8a735-126">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="8a735-127">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="8a735-127">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/support HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07029132-385d-416f-a9a6-df5e9e4c78d3
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
```

## <a name="rest-response"></a><span data-ttu-id="8a735-128">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="8a735-128">REST response</span></span>

<span data-ttu-id="8a735-129">Se for bem sucedido, este método devolve um objeto **SupportProfile** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="8a735-129">If successful, this method returns a **SupportProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8a735-130">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="8a735-130">Response success and error codes</span></span>

<span data-ttu-id="8a735-131">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="8a735-131">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8a735-132">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8a735-132">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8a735-133">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="8a735-133">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8a735-134">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="8a735-134">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 502
Content-Type: application/json
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
MS-RequestId: 07029132-385d-416f-a9a6-df5e9e4c78d3
Date: Wed, 25 Nov 2015 07:16:17 GMT

{
    "email": "email@sample.com",
    "telephone": "4255555555",
    "website": "www.microsoft.com",
    "profileType": "support_profile",
    "links": {
        "self": {
            "uri": "/v1/profiles/support",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "PartnerSupportProfile"
    }
}
```
