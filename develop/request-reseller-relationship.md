---
title: Obter um URL de pedido de relação
description: Como recuperar um URL de pedido de relacionamento para enviar a um cliente.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 07804b36dfe0892cf8b531e0731188260c014f49
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547460"
---
# <a name="retrieve-a-relationship-request-url"></a><span data-ttu-id="1d043-103">Obter um URL de pedido de relação</span><span class="sxs-lookup"><span data-stu-id="1d043-103">Retrieve a relationship request URL</span></span>

<span data-ttu-id="1d043-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="1d043-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="1d043-105">Como recuperar um URL de pedido de relacionamento para enviar a um cliente.</span><span class="sxs-lookup"><span data-stu-id="1d043-105">How to retrieve a relationship request URL to send to a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1d043-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1d043-106">Prerequisites</span></span>

- <span data-ttu-id="1d043-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1d043-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1d043-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="1d043-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="1d043-109">C\#</span><span class="sxs-lookup"><span data-stu-id="1d043-109">C\#</span></span>

<span data-ttu-id="1d043-110">Para recuperar um URL de pedido de relacionamento, utilize primeiro [**o IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para obter uma interface para as operações do cliente do parceiro.</span><span class="sxs-lookup"><span data-stu-id="1d043-110">To retrieve a relationship request URL, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="1d043-111">Em seguida, use a propriedade [**RelationshipRequest**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.relationshiprequest) para obter uma interface para operações de pedido de relacionamento com o cliente.</span><span class="sxs-lookup"><span data-stu-id="1d043-111">Next, use the [**RelationshipRequest**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.relationshiprequest) property to get an interface to customer relationship request operations.</span></span> <span data-ttu-id="1d043-112">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.getasync) para recuperar o URL.</span><span class="sxs-lookup"><span data-stu-id="1d043-112">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.getasync) method to retrieve the URL.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var customerRelationshipRequest = partnerOperations.Customers.RelationshipRequest.Get();
```

<span data-ttu-id="1d043-113">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="1d043-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="1d043-114">**Project**: Partner Center SDK Samples **Class**: GetCustomerRelationshipRequest.cs</span><span class="sxs-lookup"><span data-stu-id="1d043-114">**Project**: Partner Center SDK Samples **Class**: GetCustomerRelationshipRequest.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="1d043-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="1d043-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1d043-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d043-116">Request syntax</span></span>

| <span data-ttu-id="1d043-117">Método</span><span class="sxs-lookup"><span data-stu-id="1d043-117">Method</span></span>  | <span data-ttu-id="1d043-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="1d043-118">Request URI</span></span>                                                                            |
|---------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="1d043-119">**Obter**</span><span class="sxs-lookup"><span data-stu-id="1d043-119">**GET**</span></span> | <span data-ttu-id="1d043-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/relacionamentosreques HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1d043-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/relationshiprequests HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1d043-121">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="1d043-121">Request headers</span></span>

<span data-ttu-id="1d043-122">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1d043-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1d043-123">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="1d043-123">Request body</span></span>

<span data-ttu-id="1d043-124">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="1d043-124">None</span></span>

### <a name="request-example"></a><span data-ttu-id="1d043-125">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="1d043-125">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="1d043-126">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="1d043-126">REST response</span></span>

<span data-ttu-id="1d043-127">Se for bem sucedido, a resposta contém o objeto [RelationshipRequest.](relationships-resources.md#relationshiprequest)</span><span class="sxs-lookup"><span data-stu-id="1d043-127">If successful, the response contains the [RelationshipRequest](relationships-resources.md#relationshiprequest) object.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1d043-128">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="1d043-128">Response success and error codes</span></span>

<span data-ttu-id="1d043-129">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="1d043-129">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1d043-130">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="1d043-130">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1d043-131">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="1d043-131">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1d043-132">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="1d043-132">Response example</span></span>

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
