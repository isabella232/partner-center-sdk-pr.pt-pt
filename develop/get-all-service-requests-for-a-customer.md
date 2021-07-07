---
title: Obter todos os pedidos de serviço para um cliente
description: Recebe todos os pedidos de atendimento de um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ffcbbb9cf14b1b2a5b3becab541d3042c3cad508
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760679"
---
# <a name="get-all-service-requests-for-a-customer"></a><span data-ttu-id="02633-103">Obter todos os pedidos de serviço para um cliente</span><span class="sxs-lookup"><span data-stu-id="02633-103">Get all service requests for a customer</span></span>

<span data-ttu-id="02633-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="02633-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="02633-105">Recebe todos os pedidos de atendimento de um cliente.</span><span class="sxs-lookup"><span data-stu-id="02633-105">Gets all of a customer's service requests.</span></span>

<span data-ttu-id="02633-106">No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="02633-106">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="02633-107">Em seguida, selecione **a gestão** de serviço na barra lateral esquerda.</span><span class="sxs-lookup"><span data-stu-id="02633-107">Then, select **Service management** on the left sidebar.</span></span> <span data-ttu-id="02633-108">Os pedidos de atendimento do cliente são apresentados nos **bilhetes de Apoio.**</span><span class="sxs-lookup"><span data-stu-id="02633-108">The customer's service requests are displayed under **Support tickets**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="02633-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="02633-109">Prerequisites</span></span>

- <span data-ttu-id="02633-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="02633-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="02633-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="02633-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="02633-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="02633-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="02633-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="02633-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="02633-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="02633-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="02633-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="02633-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="02633-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="02633-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="02633-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="02633-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="02633-118">C\#</span><span class="sxs-lookup"><span data-stu-id="02633-118">C\#</span></span>

<span data-ttu-id="02633-119">Para apresentar uma lista de todos os pedidos de serviço de um cliente, utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="02633-119">To display a list of all of a customer's service requests, use your **IAggregatePartner.Customers** collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="02633-120">Em seguida, ligue para a propriedade [**ServiceRequests,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicerequests) seguida dos métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="02633-120">Then call the [**ServiceRequests**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicerequests) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId as string;

ResourceCollection<ServiceRequest> serviceRequests = partnerOperations.Customers.ById(customerId).ServiceRequests.Get();
```

<span data-ttu-id="02633-121">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="02633-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="02633-122">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span><span class="sxs-lookup"><span data-stu-id="02633-122">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="02633-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="02633-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="02633-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="02633-124">Request syntax</span></span>

| <span data-ttu-id="02633-125">Método</span><span class="sxs-lookup"><span data-stu-id="02633-125">Method</span></span>  | <span data-ttu-id="02633-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="02633-126">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="02633-127">**Obter**</span><span class="sxs-lookup"><span data-stu-id="02633-127">**GET**</span></span> | <span data-ttu-id="02633-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/servicerequests HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="02633-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/servicerequests HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="02633-129">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="02633-129">URI parameter</span></span>

<span data-ttu-id="02633-130">Utilize o seguinte parâmetro de consulta para obter todos os pedidos de serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="02633-130">Use the following query parameter to get all service requests for the customer.</span></span>

| <span data-ttu-id="02633-131">Nome</span><span class="sxs-lookup"><span data-stu-id="02633-131">Name</span></span>                   | <span data-ttu-id="02633-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="02633-132">Type</span></span>     | <span data-ttu-id="02633-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="02633-133">Required</span></span> | <span data-ttu-id="02633-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="02633-134">Description</span></span>                            |
|------------------------|----------|----------|----------------------------------------|
| <span data-ttu-id="02633-135">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="02633-135">**customer-tenant-id**</span></span> | <span data-ttu-id="02633-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="02633-136">**guid**</span></span> | <span data-ttu-id="02633-137">Y</span><span class="sxs-lookup"><span data-stu-id="02633-137">Y</span></span>        | <span data-ttu-id="02633-138">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="02633-138">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="02633-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="02633-139">Request headers</span></span>

<span data-ttu-id="02633-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="02633-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="02633-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="02633-141">Request body</span></span>

<span data-ttu-id="02633-142">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="02633-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="02633-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="02633-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/servicerequests HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 53d5d48c-9693-46b6-8071-2eed07797d6c
MS-CorrelationId: 998e31a1-3f17-4471-a9ee-7678dd72e033
```

## <a name="rest-response"></a><span data-ttu-id="02633-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="02633-144">REST response</span></span>

<span data-ttu-id="02633-145">Se for bem sucedido, este método devolve uma recolha de recursos **de Pedido** de Serviço no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="02633-145">If successful, this method returns a collection of **Service Request** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="02633-146">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="02633-146">Response success and error codes</span></span>

<span data-ttu-id="02633-147">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="02633-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="02633-148">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="02633-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="02633-149">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="02633-149">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="02633-150">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="02633-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 742
Content-Type: application/json
MS-CorrelationId: 998e31a1-3f17-4471-a9ee-7678dd72e033
MS-RequestId: 53d5d48c-9693-46b6-8071-2eed07797d6c
Date: Tue, 24 Nov 2015 07:19:21 GMT

{
    "totalCount": 1,
    "items": [{
        "title": "Test",
        "severity": 0,
        "id": "615112491169010",
        "status": 1,
        "primaryContact": {
            "lastName": "LastName",
            "firstName": "FirstName"
        },
        "createdDate": "2015-11-24T01:07:00.863",
        "lastModifiedDate": "2015-11-24T01:17:10.61",
        "lastClosedDate": "0001-01-01T00:00:00",
        "attributes": {
            "objectType": "ServiceRequest"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
