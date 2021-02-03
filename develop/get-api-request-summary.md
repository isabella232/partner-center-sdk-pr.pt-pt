---
title: Obtenha o estado de adoção do MFA
description: Obtenha uma lista do estado de adoção de autenticação multi-factor para cada parceiro utilizando a API do Partner REST.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
author: amitravat
ms.author: amrava
ms.openlocfilehash: f82d163b704323c81e2948b78eb9b9d1a14ddc52
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769020"
---
# <a name="get-mfa-adoption-status"></a><span data-ttu-id="de3e6-103">Obtenha o estado de adoção do MFA</span><span class="sxs-lookup"><span data-stu-id="de3e6-103">Get MFA adoption status</span></span>

<span data-ttu-id="de3e6-104">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="de3e6-104">Applies to:</span></span>

- <span data-ttu-id="de3e6-105">API do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="de3e6-105">Partner Center API</span></span>

<span data-ttu-id="de3e6-106">Este artigo explica como obter o estatuto de autenticação multi-factor (MFA) para cada parceiro dentro de um inquilino.</span><span class="sxs-lookup"><span data-stu-id="de3e6-106">This article explains how to get the multi-factor authentication (MFA) adoption status for each partner within a tenant.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="de3e6-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="de3e6-107">Prerequisites</span></span>

- <span data-ttu-id="de3e6-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="de3e6-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="de3e6-109">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="de3e6-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="de3e6-110">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="de3e6-110">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="de3e6-111">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="de3e6-111">Request syntax</span></span>

| <span data-ttu-id="de3e6-112">Método</span><span class="sxs-lookup"><span data-stu-id="de3e6-112">Method</span></span>  | <span data-ttu-id="de3e6-113">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="de3e6-113">Request URI</span></span>                                                               |
|---------|---------------------------------------------------------------------------|
| <span data-ttu-id="de3e6-114">**Obter**</span><span class="sxs-lookup"><span data-stu-id="de3e6-114">**GET**</span></span> | <span data-ttu-id="de3e6-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/applicationmfaadoptionstatus></span><span class="sxs-lookup"><span data-stu-id="de3e6-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/applicationmfaadoptionstatus></span></span> |

### <a name="request-headers"></a><span data-ttu-id="de3e6-116">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="de3e6-116">Request headers</span></span>

- <span data-ttu-id="de3e6-117">Consulte [os cabeçalhos REST do Partner Center](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="de3e6-117">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="de3e6-118">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="de3e6-118">Request body</span></span>

<span data-ttu-id="de3e6-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="de3e6-119">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="de3e6-120">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="de3e6-120">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/applicationmfaadoptionstatus HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Type: application/json
```

## <a name="rest-response"></a><span data-ttu-id="de3e6-121">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="de3e6-121">REST response</span></span>

<span data-ttu-id="de3e6-122">Se for bem sucedido, este método devolve uma coleção de pedidos de [API resumidos pelos](mfa-resources.md#api-request-summarized-by-application) recursos da Aplicação no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="de3e6-122">If successful, this method returns a collection of [API request summarized by Application](mfa-resources.md#api-request-summarized-by-application) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="de3e6-123">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="de3e6-123">Response success and error codes</span></span>

<span data-ttu-id="de3e6-124">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="de3e6-124">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="de3e6-125">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="de3e6-125">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="de3e6-126">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="de3e6-126">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="de3e6-127">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="de3e6-127">Response example</span></span>

``` http
HTTP/1.1 200 OK
Content-Length: 313
Content-Type: application/json
MS-CorrelationId: 4cb80cbe-566b-4d8b-8b8f-af1454b73089
MS-RequestId: 566330a7-1e4b-4848-9c23-f135c70fd810
Date: Thu, 21 May 2020 22:29:17 GMT
[
    {
        "loginDate": "2020-05-20",
        "mfaCompliantRequestCount": 7,
        "totalRequestCount": 7,
        "applicationId": "14f38d7d-c4fc-448a-b2df-0fc60e75465a",
        "applicationName": ""
    },
    {
        "loginDate": "2020-05-19",
        "mfaCompliantRequestCount": 7,
        "totalRequestCount": 14,
        "applicationId": "60a00bf2-0644-4279-83b3-87ddf96f2509",
        "applicationName": ""
    }
]
```
