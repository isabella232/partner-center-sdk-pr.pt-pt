---
title: Obter um URL de pedido de relação
description: Como recuperar um URL de pedido de relacionamento para enviar a um cliente.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 5f899734b774ff460e005e20df8658275b2ce9d5
ms.sourcegitcommit: d4e652e3b73c6137704d43d4a472cc5aa5549f11
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/09/2020
ms.locfileid: "97770272"
---
# <a name="retrieve-a-relationship-request-url"></a><span data-ttu-id="69b1c-103">Obter um URL de pedido de relação</span><span class="sxs-lookup"><span data-stu-id="69b1c-103">Retrieve a relationship request URL</span></span>

<span data-ttu-id="69b1c-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="69b1c-104">**Applies To**</span></span>

- <span data-ttu-id="69b1c-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="69b1c-105">Partner Center</span></span>
- <span data-ttu-id="69b1c-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="69b1c-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="69b1c-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="69b1c-107">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="69b1c-108">Como recuperar um URL de pedido de relacionamento para enviar a um cliente.</span><span class="sxs-lookup"><span data-stu-id="69b1c-108">How to retrieve a relationship request URL to send to a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="69b1c-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="69b1c-109">Prerequisites</span></span>

- <span data-ttu-id="69b1c-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="69b1c-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="69b1c-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="69b1c-111">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="69b1c-112">C\#</span><span class="sxs-lookup"><span data-stu-id="69b1c-112">C\#</span></span>

<span data-ttu-id="69b1c-113">Para recuperar um URL de pedido de relacionamento, utilize primeiro [**o IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para obter uma interface para as operações do cliente do parceiro.</span><span class="sxs-lookup"><span data-stu-id="69b1c-113">To retrieve a relationship request URL, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="69b1c-114">Em seguida, use a propriedade [**RelationshipRequest**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.relationshiprequest) para obter uma interface para operações de pedido de relacionamento com o cliente.</span><span class="sxs-lookup"><span data-stu-id="69b1c-114">Next, use the [**RelationshipRequest**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.relationshiprequest) property to get an interface to customer relationship request operations.</span></span> <span data-ttu-id="69b1c-115">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.getasync) para recuperar o URL.</span><span class="sxs-lookup"><span data-stu-id="69b1c-115">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.getasync) method to retrieve the URL.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var customerRelationshipRequest = partnerOperations.Customers.RelationshipRequest.Get();
```

<span data-ttu-id="69b1c-116">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="69b1c-116">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="69b1c-117">**Projeto**: Partner Center SDK Samples **Class**: GetCustomerRelationshipRequest.cs</span><span class="sxs-lookup"><span data-stu-id="69b1c-117">**Project**: Partner Center SDK Samples **Class**: GetCustomerRelationshipRequest.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="69b1c-118">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="69b1c-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="69b1c-119">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="69b1c-119">Request syntax</span></span>

| <span data-ttu-id="69b1c-120">Método</span><span class="sxs-lookup"><span data-stu-id="69b1c-120">Method</span></span>  | <span data-ttu-id="69b1c-121">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="69b1c-121">Request URI</span></span>                                                                            |
|---------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="69b1c-122">**Obter**</span><span class="sxs-lookup"><span data-stu-id="69b1c-122">**GET**</span></span> | <span data-ttu-id="69b1c-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/relacionamentosreques HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="69b1c-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/relationshiprequests HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="69b1c-124">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="69b1c-124">Request headers</span></span>

<span data-ttu-id="69b1c-125">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="69b1c-125">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="69b1c-126">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="69b1c-126">Request body</span></span>

<span data-ttu-id="69b1c-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="69b1c-127">None</span></span>

### <a name="request-example"></a><span data-ttu-id="69b1c-128">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="69b1c-128">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/relationshiprequests HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ee519026-4c67-4113-bec7-a38aca621bf0
MS-CorrelationId: 02971f0f-1029-47b2-9fdb-1932f0987470
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="69b1c-129">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="69b1c-129">REST response</span></span>

<span data-ttu-id="69b1c-130">Se for bem sucedido, a resposta contém o objeto [RelationshipRequest.](relationships-resources.md#relationshiprequest)</span><span class="sxs-lookup"><span data-stu-id="69b1c-130">If successful, the response contains the [RelationshipRequest](relationships-resources.md#relationshiprequest) object.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="69b1c-131">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="69b1c-131">Response success and error codes</span></span>

<span data-ttu-id="69b1c-132">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="69b1c-132">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="69b1c-133">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="69b1c-133">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="69b1c-134">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="69b1c-134">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="69b1c-135">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="69b1c-135">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 196
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 02971f0f-1029-47b2-9fdb-1932f0987470
MS-RequestId: ee519026-4c67-4113-bec7-a38aca621bf0
MS-CV: jbYZRWjU3E262f8o.0
MS-ServerId: 030020643
Date: Fri, 19 May 2017 22:32:07 GMT

{
    "url": "https://admin.microsoft.com/Adminportal/Home?invType=ResellerRelationship&partnerId=3b33e682-00c3-41ee-9dd2-a548adf56438&msppId=0&DAP=false#/BillingAccounts/partner-invitation",
    "attributes": {
        "objectType": "RelationshipRequest"
    }
}
```
