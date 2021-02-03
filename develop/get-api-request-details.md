---
title: Obtenha uma lista de todos os pedidos de utilizadores parceiros
description: Obtenha uma lista de todos os pedidos de utilizador parceiro usando a API Partner REST.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
author: cychua
ms.author: cychua
ms.openlocfilehash: 43b1e3d4a6220ac8adba8eed0389395113072288
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768750"
---
# <a name="get-app-and-user-api-requests"></a><span data-ttu-id="be30e-103">Obtenha pedidos de App e API do utilizador</span><span class="sxs-lookup"><span data-stu-id="be30e-103">Get App and User API requests</span></span>

<span data-ttu-id="be30e-104">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="be30e-104">Applies to:</span></span>

- <span data-ttu-id="be30e-105">API do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="be30e-105">Partner Center API</span></span>

<span data-ttu-id="be30e-106">Este artigo explica como obter uma lista de todos os pedidos de utilizador de um cliente parceiro dentro de um inquilino usando APIs REST.</span><span class="sxs-lookup"><span data-stu-id="be30e-106">This article explains how to obtain a list of all partner user requests within a tenant using REST APIs.</span></span>

 > [!NOTE]
 > <span data-ttu-id="be30e-107">Esta API apenas devolve os mais recentes pedidos de API feitos pela app + credencial do utilizador com limite máximo de 10K.</span><span class="sxs-lookup"><span data-stu-id="be30e-107">This API only returns the most recent API requests made by APP + User credential with maximum 10K limit.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be30e-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="be30e-108">Prerequisites</span></span>

- <span data-ttu-id="be30e-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="be30e-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="be30e-110">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="be30e-110">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="be30e-111">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="be30e-111">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="be30e-112">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="be30e-112">Request syntax</span></span>

| <span data-ttu-id="be30e-113">Método</span><span class="sxs-lookup"><span data-stu-id="be30e-113">Method</span></span>  | <span data-ttu-id="be30e-114">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="be30e-114">Request URI</span></span>                                                        |
|---------|--------------------------------------------------------------------|
| <span data-ttu-id="be30e-115">**Obter**</span><span class="sxs-lookup"><span data-stu-id="be30e-115">**GET**</span></span> | <span data-ttu-id="be30e-116">[*{baseURL}*](partner-center-rest-urls.md)/v1/partnerRequests</span><span class="sxs-lookup"><span data-stu-id="be30e-116">[*{baseURL}*](partner-center-rest-urls.md)/v1/partnerRequests</span></span> |

### <a name="request-headers"></a><span data-ttu-id="be30e-117">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="be30e-117">Request headers</span></span>

- <span data-ttu-id="be30e-118">Consulte [os cabeçalhos REST do Partner Center](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="be30e-118">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="be30e-119">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="be30e-119">Request body</span></span>

<span data-ttu-id="be30e-120">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="be30e-120">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="be30e-121">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="be30e-121">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/partnerRequests HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Type: application/json
```

## <a name="rest-response"></a><span data-ttu-id="be30e-122">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="be30e-122">REST response</span></span>

<span data-ttu-id="be30e-123">Se for bem sucedido, este método devolve uma coleção de pedidos de [API detalha recursos](mfa-resources.md#api-request-details) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="be30e-123">If successful, this method returns a collection of [API request details](mfa-resources.md#api-request-details) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="be30e-124">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="be30e-124">Response success and error codes</span></span>

<span data-ttu-id="be30e-125">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="be30e-125">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="be30e-126">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="be30e-126">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="be30e-127">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="be30e-127">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="be30e-128">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="be30e-128">Response example</span></span>

``` http
HTTP/1.1 200 OK
Content-Length: 2960
Content-Type: application/json
MS-CorrelationId: 4cb80cbe-566b-4d8b-8b8f-af1454b73089
MS-RequestId: 566330a7-1e4b-4848-9c23-f135c70fd810
Date: Thu, 21 May 2020 22:29:17 GMT
{
    "totalCount": 2,
    "items": [
        {
            "requestId": "6c583d8d-46cd-420c-ae3d-35b6dfdcdb21",
            "correlationId": "",
            "operationName": "Get /v{version}/nonMfaCompliantPartnerPrincipals",
            "requestDateTime": "2020-05-21T21:02:10.31",
            "sourceIpAddress": "13.88.20.150",
            "objectId": "c69854fe-5fb4-4527-a28f-f24f1acaffd6",
            "tenantId": "6e6aef4a-4ca9-40a8-b5bf-b53a1923c540",
            "upn": "admin@yourdomain.onmicrosoft.com",
            "applicationId": "60a00bf2-0644-4279-83b3-87ddf96f2509",
            "mfaCompliant": true
        },
        {
            "requestId": "09f8e434-a9ce-43ea-a9ac-270fbb22371a",
            "correlationId": "",
            "operationName": "Get /v{version}/customers/{customer_id}/subscriptions?order_id={order_id_value}&mpn_id={mpn_id_value}",
            "requestDateTime": "2020-05-21T22:18:35.73",
            "sourceIpAddress": "13.88.20.150",
            "objectId": "adc77aa5-7968-4c57-9f48-361018265c1a",
            "tenantId": "6e6aef4a-4ca9-40a8-b5bf-b53a1923c540",
            "upn": "portalnonmfa@yourdomain.onmicrosoft.com",
            "applicationId": "60a00bf2-0644-4279-83b3-87ddf96f2509",
            "mfaCompliant": false
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
