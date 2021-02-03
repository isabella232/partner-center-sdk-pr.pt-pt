---
title: Atualizar um pedido de serviço
description: Como atualizar um pedido de atendimento ao cliente existente que um Fornecedor de Soluções Cloud apresentou com a Microsoft em nome do cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a1df0d1f5fa4630b346d1c8b9cffabb86ce34cfb
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769740"
---
# <a name="update-a-service-request"></a><span data-ttu-id="88c5d-103">Atualizar um pedido de serviço</span><span class="sxs-lookup"><span data-stu-id="88c5d-103">Update a service request</span></span>

<span data-ttu-id="88c5d-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="88c5d-104">**Applies To**</span></span>

- <span data-ttu-id="88c5d-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="88c5d-105">Partner Center</span></span>
- <span data-ttu-id="88c5d-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="88c5d-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="88c5d-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="88c5d-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="88c5d-108">Como atualizar um pedido de atendimento ao cliente existente que um Fornecedor de Soluções Cloud apresentou com a Microsoft em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="88c5d-108">How to update an existing customer service request that a Cloud Solution Provider has filed with Microsoft on the customer's behalf.</span></span>

<span data-ttu-id="88c5d-109">No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="88c5d-109">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="88c5d-110">Em seguida, selecione **a gestão** de serviço na barra lateral esquerda.</span><span class="sxs-lookup"><span data-stu-id="88c5d-110">Then, select **Service management** on the left sidebar.</span></span> <span data-ttu-id="88c5d-111">No cabeçalho **de pedidos de apoio,** selecione o pedido de serviço em questão.</span><span class="sxs-lookup"><span data-stu-id="88c5d-111">Under the **Support requests** header, select the service request in question.</span></span> <span data-ttu-id="88c5d-112">Para terminar, faça as alterações desejadas ao pedido de serviço e, em seguida, **selecione Enviar.**</span><span class="sxs-lookup"><span data-stu-id="88c5d-112">To finish, make the desired changes to the service request then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88c5d-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="88c5d-113">Prerequisites</span></span>

- <span data-ttu-id="88c5d-114">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="88c5d-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="88c5d-115">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="88c5d-115">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="88c5d-116">Uma identificação de pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="88c5d-116">A service request ID.</span></span>

## <a name="c"></a><span data-ttu-id="88c5d-117">C\#</span><span class="sxs-lookup"><span data-stu-id="88c5d-117">C\#</span></span>

<span data-ttu-id="88c5d-118">Para atualizar um pedido de serviço do cliente, ligue para o método [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) com o id pedido de serviço para identificar e devolver a interface de pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="88c5d-118">To update a customer's service request, call the [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) method with the service request id to identify and return the service request interface.</span></span> <span data-ttu-id="88c5d-119">Em seguida, ligue para o método [**IServiceRequest.Patch**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patch) ou [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patchasync) para atualizar o pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="88c5d-119">Then call the [**IServiceRequest.Patch**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patch) or [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patchasync) method to update the service request.</span></span> <span data-ttu-id="88c5d-120">Para fornecer os valores atualizados, crie um novo objeto [**de ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) vazio e desaje assimte apenas os valores de propriedade que pretende alterar.</span><span class="sxs-lookup"><span data-stu-id="88c5d-120">To provide the updated values, create a new, empty [**ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) object and set only the property values that you want to change.</span></span> <span data-ttu-id="88c5d-121">Em seguida, passe esse objeto na chamada para o método Patch ou PatchAsync.</span><span class="sxs-lookup"><span data-stu-id="88c5d-121">Then pass that object in the call to the Patch or PatchAsync method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// ServiceRequest existingServiceRequest;

ServiceRequest updatedServiceRequest = partnerOperations.ServiceRequests.ById(existingServiceRequest.Id).Patch(new ServiceRequest
{
   NewNote = note
});
```

<span data-ttu-id="88c5d-122">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="88c5d-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="88c5d-123">**Projeto**: Partner Center SDK Samples **Class**: UpdatePartnerServiceRequest.cs</span><span class="sxs-lookup"><span data-stu-id="88c5d-123">**Project**: Partner Center SDK Samples **Class**: UpdatePartnerServiceRequest.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="88c5d-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="88c5d-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="88c5d-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="88c5d-125">Request syntax</span></span>

| <span data-ttu-id="88c5d-126">Método</span><span class="sxs-lookup"><span data-stu-id="88c5d-126">Method</span></span>    | <span data-ttu-id="88c5d-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="88c5d-127">Request URI</span></span>                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="88c5d-128">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="88c5d-128">**PATCH**</span></span> | <span data-ttu-id="88c5d-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="88c5d-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="88c5d-130">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="88c5d-130">URI parameter</span></span>

<span data-ttu-id="88c5d-131">Utilize o seguinte parâmetro URI para atualizar o pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="88c5d-131">Use the following URI parameter to update the service request.</span></span>

| <span data-ttu-id="88c5d-132">Nome</span><span class="sxs-lookup"><span data-stu-id="88c5d-132">Name</span></span>                  | <span data-ttu-id="88c5d-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="88c5d-133">Type</span></span>     | <span data-ttu-id="88c5d-134">Necessário</span><span class="sxs-lookup"><span data-stu-id="88c5d-134">Required</span></span> | <span data-ttu-id="88c5d-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="88c5d-135">Description</span></span>                                 |
|-----------------------|----------|----------|---------------------------------------------|
| <span data-ttu-id="88c5d-136">**servicerequest-id**</span><span class="sxs-lookup"><span data-stu-id="88c5d-136">**servicerequest-id**</span></span> | <span data-ttu-id="88c5d-137">**guid**</span><span class="sxs-lookup"><span data-stu-id="88c5d-137">**guid**</span></span> | <span data-ttu-id="88c5d-138">Y</span><span class="sxs-lookup"><span data-stu-id="88c5d-138">Y</span></span>        | <span data-ttu-id="88c5d-139">Um GUID que identifica o pedido de serviço.</span><span class="sxs-lookup"><span data-stu-id="88c5d-139">A GUID that identifies the service request.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="88c5d-140">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="88c5d-140">Request headers</span></span>

<span data-ttu-id="88c5d-141">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="88c5d-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="88c5d-142">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="88c5d-142">Request body</span></span>

<span data-ttu-id="88c5d-143">O organismo de pedido deve conter um recurso [ServiceRequest.](service-request-resources.md)</span><span class="sxs-lookup"><span data-stu-id="88c5d-143">The request body should contain a [ServiceRequest](service-request-resources.md) resource.</span></span> <span data-ttu-id="88c5d-144">Os únicos valores necessários são os que devem ser atualizados.</span><span class="sxs-lookup"><span data-stu-id="88c5d-144">The only required values are those to be updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="88c5d-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="88c5d-145">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/servicerequests/616122292874576 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f9a030bd-e492-4c1a-9c70-021f18234981
MS-CorrelationId: fd969070-4e5f-4c6b-a3c6-1941283b39ae
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 508
Expect: 100-continue

{
    "Id": null,
    "Title": null,
    "Description": null,
    "Severity": "unknown",
    "SupportTopicId": null,
    "SupportTopicName": null,
    "Status": "none",
    "Organization": null,
    "PrimaryContact": null,
    "LastUpdatedBy": null,
    "ProductName": null,
    "ProductId": null,
    "CreatedDate": "0001-01-01T00:00:00",
    "LastModifiedDate": "0001-01-01T00:00:00",
    "LastClosedDate": "0001-01-01T00:00:00",
    "NewNote": {
        "CreatedByName": null,
        "CreatedDate": null,
        "Text": "Sample Note"
    },
    "Notes": null,
    "CountryCode": null,
    "FileLinks": null,
    "Attributes": {
        "ObjectType": "ServiceRequest"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="88c5d-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="88c5d-146">REST response</span></span>

<span data-ttu-id="88c5d-147">Se for bem sucedido, este método devolve um recurso **de Pedido de Serviço** com propriedades atualizadas no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="88c5d-147">If successful, this method returns a **Service Request** resource with updated properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="88c5d-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="88c5d-148">Response success and error codes</span></span>

<span data-ttu-id="88c5d-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="88c5d-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="88c5d-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="88c5d-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="88c5d-151">Para obter a lista completa, consulte [os Códigos de Erro DO Centro de Parceiros REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="88c5d-151">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="88c5d-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="88c5d-152">Response example</span></span>

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
