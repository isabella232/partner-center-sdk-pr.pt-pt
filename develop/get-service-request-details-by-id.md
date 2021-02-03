---
title: Obtenha os detalhes do pedido de serviço por ID.
description: Como recuperar os detalhes de um pedido de atendimento ao cliente existente por ID.
ms.date: 02/06/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c79fd3f5e5609a1893891e9b2a8078f8678497b3
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769901"
---
# <a name="get-service-request-details-by-id"></a><span data-ttu-id="24250-103">Obter detalhes do pedido de serviço por ID</span><span class="sxs-lookup"><span data-stu-id="24250-103">Get service request details by ID</span></span>

<span data-ttu-id="24250-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="24250-104">**Applies To**</span></span>

- <span data-ttu-id="24250-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="24250-105">Partner Center</span></span>
- <span data-ttu-id="24250-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="24250-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="24250-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="24250-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="24250-108">Como recuperar os detalhes de um pedido de atendimento ao cliente existente usando o identificador de pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="24250-108">How to retrieve the details of an existing customer service request using the service request identifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24250-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="24250-109">Prerequisites</span></span>

- <span data-ttu-id="24250-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="24250-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="24250-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="24250-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="24250-112">Uma identificação de pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="24250-112">A service request ID.</span></span>

## <a name="c"></a><span data-ttu-id="24250-113">C\#</span><span class="sxs-lookup"><span data-stu-id="24250-113">C\#</span></span>

<span data-ttu-id="24250-114">Para obter os detalhes de um pedido de atendimento ao cliente existente, ligue para o método [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) e passe num [**ServiceRequest.Id**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.id#Microsoft_Store_PartnerCenter_Models_ServiceRequests_ServiceRequest_Id) para identificar e devolver uma interface ao objeto específico [**do ServiceRequest.**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest)</span><span class="sxs-lookup"><span data-stu-id="24250-114">To retrieve the details of an existing customer service request, call the [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) method, and pass in a [**ServiceRequest.Id**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.id#Microsoft_Store_PartnerCenter_Models_ServiceRequests_ServiceRequest_Id) to identify and return an interface to the specific [**ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) object.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="24250-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="24250-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="24250-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="24250-116">Request syntax</span></span>

| <span data-ttu-id="24250-117">Método</span><span class="sxs-lookup"><span data-stu-id="24250-117">Method</span></span>    | <span data-ttu-id="24250-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="24250-118">Request URI</span></span>                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="24250-119">**Obter**</span><span class="sxs-lookup"><span data-stu-id="24250-119">**GET**</span></span> | <span data-ttu-id="24250-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="24250-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="24250-121">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="24250-121">URI parameter</span></span>

<span data-ttu-id="24250-122">Utilize o seguinte parâmetro URI para obter o pedido de serviço especificado.</span><span class="sxs-lookup"><span data-stu-id="24250-122">Use the following URI parameter to get the specified service request.</span></span>

| <span data-ttu-id="24250-123">Nome</span><span class="sxs-lookup"><span data-stu-id="24250-123">Name</span></span>                  | <span data-ttu-id="24250-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="24250-124">Type</span></span>     | <span data-ttu-id="24250-125">Necessário</span><span class="sxs-lookup"><span data-stu-id="24250-125">Required</span></span> | <span data-ttu-id="24250-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="24250-126">Description</span></span>                                 |
|-----------------------|----------|----------|---------------------------------------------|
| <span data-ttu-id="24250-127">**servicerequest-id**</span><span class="sxs-lookup"><span data-stu-id="24250-127">**servicerequest-id**</span></span> | <span data-ttu-id="24250-128">**guid**</span><span class="sxs-lookup"><span data-stu-id="24250-128">**guid**</span></span> | <span data-ttu-id="24250-129">Y</span><span class="sxs-lookup"><span data-stu-id="24250-129">Y</span></span>        | <span data-ttu-id="24250-130">Um GUID que identifica o pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="24250-130">A GUID that identifies the service request.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="24250-131">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="24250-131">Request headers</span></span>

<span data-ttu-id="24250-132">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="24250-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="24250-133">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="24250-133">Request body</span></span>

<span data-ttu-id="24250-134">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="24250-134">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="24250-135">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="24250-135">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="24250-136">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="24250-136">REST response</span></span>

<span data-ttu-id="24250-137">Se for bem sucedido, este método devolve um recurso **de Pedido de Serviço** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="24250-137">If successful, this method returns a **Service Request** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="24250-138">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="24250-138">Response success and error codes</span></span>

<span data-ttu-id="24250-139">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="24250-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="24250-140">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="24250-140">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="24250-141">Para obter a lista completa, consulte [os Códigos de Erro DO Centro de Parceiros REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="24250-141">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="24250-142">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="24250-142">Response example</span></span>

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
