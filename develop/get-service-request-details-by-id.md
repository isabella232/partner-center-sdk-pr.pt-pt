---
title: Obtenha os detalhes do pedido de serviço por ID.
description: Como recuperar os detalhes de um pedido de atendimento ao cliente existente por ID.
ms.date: 02/06/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 66488cf9592d630cb1f0237d379e8df5ead6a3a8
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548775"
---
# <a name="get-service-request-details-by-id"></a><span data-ttu-id="31aa6-103">Obter detalhes do pedido de serviço por ID</span><span class="sxs-lookup"><span data-stu-id="31aa6-103">Get service request details by ID</span></span>

<span data-ttu-id="31aa6-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="31aa6-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="31aa6-105">Como recuperar os detalhes de um pedido de atendimento ao cliente existente usando o identificador de pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="31aa6-105">How to retrieve the details of an existing customer service request using the service request identifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31aa6-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="31aa6-106">Prerequisites</span></span>

- <span data-ttu-id="31aa6-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="31aa6-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="31aa6-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="31aa6-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="31aa6-109">Uma identificação de pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="31aa6-109">A service request ID.</span></span>

## <a name="c"></a><span data-ttu-id="31aa6-110">C\#</span><span class="sxs-lookup"><span data-stu-id="31aa6-110">C\#</span></span>

<span data-ttu-id="31aa6-111">Para obter os detalhes de um pedido de atendimento ao cliente existente, ligue para o método [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) e passe num [**ServiceRequest.Id**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.id#Microsoft_Store_PartnerCenter_Models_ServiceRequests_ServiceRequest_Id) para identificar e devolver uma interface ao objeto específico [**do ServiceRequest.**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest)</span><span class="sxs-lookup"><span data-stu-id="31aa6-111">To retrieve the details of an existing customer service request, call the [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) method, and pass in a [**ServiceRequest.Id**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.id#Microsoft_Store_PartnerCenter_Models_ServiceRequests_ServiceRequest_Id) to identify and return an interface to the specific [**ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) object.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// ServiceRequest existingServiceRequest as ServiceRequest;

ServiceRequest serviceRequestDetails = partnerOperations.ServiceRequests.ById(existingServiceRequest.Id).Get();

Console.WriteLine(string.Format("The primary contact for the service request {0} is {1} {2}.",
    serviceRequestDetails.Title,
    serviceRequestDetails.PrimaryContact.FirstName,
    serviceRequestDetails.PrimaryContact.LastName,
));
```

## <a name="rest-request"></a><span data-ttu-id="31aa6-112">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="31aa6-112">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="31aa6-113">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="31aa6-113">Request syntax</span></span>

| <span data-ttu-id="31aa6-114">Método</span><span class="sxs-lookup"><span data-stu-id="31aa6-114">Method</span></span>    | <span data-ttu-id="31aa6-115">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="31aa6-115">Request URI</span></span>                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="31aa6-116">**Obter**</span><span class="sxs-lookup"><span data-stu-id="31aa6-116">**GET**</span></span> | <span data-ttu-id="31aa6-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="31aa6-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="31aa6-118">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="31aa6-118">URI parameter</span></span>

<span data-ttu-id="31aa6-119">Utilize o seguinte parâmetro URI para obter o pedido de serviço especificado.</span><span class="sxs-lookup"><span data-stu-id="31aa6-119">Use the following URI parameter to get the specified service request.</span></span>

| <span data-ttu-id="31aa6-120">Nome</span><span class="sxs-lookup"><span data-stu-id="31aa6-120">Name</span></span>                  | <span data-ttu-id="31aa6-121">Tipo</span><span class="sxs-lookup"><span data-stu-id="31aa6-121">Type</span></span>     | <span data-ttu-id="31aa6-122">Necessário</span><span class="sxs-lookup"><span data-stu-id="31aa6-122">Required</span></span> | <span data-ttu-id="31aa6-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="31aa6-123">Description</span></span>                                 |
|-----------------------|----------|----------|---------------------------------------------|
| <span data-ttu-id="31aa6-124">**servicerequest-id**</span><span class="sxs-lookup"><span data-stu-id="31aa6-124">**servicerequest-id**</span></span> | <span data-ttu-id="31aa6-125">**guid**</span><span class="sxs-lookup"><span data-stu-id="31aa6-125">**guid**</span></span> | <span data-ttu-id="31aa6-126">Y</span><span class="sxs-lookup"><span data-stu-id="31aa6-126">Y</span></span>        | <span data-ttu-id="31aa6-127">Um GUID que identifica o pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="31aa6-127">A GUID that identifies the service request.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="31aa6-128">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="31aa6-128">Request headers</span></span>

<span data-ttu-id="31aa6-129">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="31aa6-129">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="31aa6-130">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="31aa6-130">Request body</span></span>

<span data-ttu-id="31aa6-131">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="31aa6-131">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="31aa6-132">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="31aa6-132">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/servicerequests/616122292874576 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f9a030bd-e492-4c1a-9c70-021f18234981
MS-CorrelationId: fd969070-4e5f-4c6b-a3c6-1941283b39ae
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="31aa6-133">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="31aa6-133">REST response</span></span>

<span data-ttu-id="31aa6-134">Se for bem sucedido, este método devolve um recurso **de Pedido de Serviço** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="31aa6-134">If successful, this method returns a **Service Request** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="31aa6-135">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="31aa6-135">Response success and error codes</span></span>

<span data-ttu-id="31aa6-136">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="31aa6-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="31aa6-137">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="31aa6-137">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="31aa6-138">Para obter a lista completa, consulte [os Códigos de Erro DO Centro de Parceiros REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="31aa6-138">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="31aa6-139">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="31aa6-139">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 566
Content-Type: application/json; charset=utf-8
MS-CorrelationId: fd969070-4e5f-4c6b-a3c6-1941283b39ae
MS-RequestId: f9a030bd-e492-4c1a-9c70-021f18234981
MS-CV: rjLONPum/Uq94UQA.0
MS-ServerId: 030011719
Date: Mon, 09 Jan 2017 23:31:15 GMT

{
    "title": "TrialSR",
    "description": "Ignore this SR",
    "severity": "critical",
    "supportTopicId": "32444671",
    "supportTopicName": "Cannot manage my profile",
    "id": "616122292874576",
    "status": "open",
    "organization": {
        "id": "3b33e682-00c3-41ee-9dd2-a548adf56438",
        "name": "TEST_TEST_BugBash1"
    },
    "productId": "15960",
    "createdDate": "2016-12-22T20:31:17.24Z",
    "lastModifiedDate": "2017-01-09T23:31:15.373Z",
    "lastClosedDate": "0001-01-01T00:00:00",
    "notes": [{
            "createdByName": "Account",
            "createdDate": "2017-01-09T23:31:15.373",
            "text": "Sample Note"
        }
    ],
    "attributes": {
        "objectType": "ServiceRequest"
    }
}
```
