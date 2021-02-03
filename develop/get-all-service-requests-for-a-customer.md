---
title: Obter todos os pedidos de serviço para um cliente
description: Recebe todos os pedidos de atendimento de um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 6f473c7a7d43b1a3929d983fb23dae92fdafbc0f
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769896"
---
# <a name="get-all-service-requests-for-a-customer"></a><span data-ttu-id="3b6f6-103">Obter todos os pedidos de serviço para um cliente</span><span class="sxs-lookup"><span data-stu-id="3b6f6-103">Get all service requests for a customer</span></span>

<span data-ttu-id="3b6f6-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="3b6f6-104">**Applies To**</span></span>

- <span data-ttu-id="3b6f6-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="3b6f6-105">Partner Center</span></span>
- <span data-ttu-id="3b6f6-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="3b6f6-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="3b6f6-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="3b6f6-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="3b6f6-108">Recebe todos os pedidos de atendimento de um cliente.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-108">Gets all of a customer's service requests.</span></span>

<span data-ttu-id="3b6f6-109">No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="3b6f6-109">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="3b6f6-110">Em seguida, selecione **a gestão** de serviço na barra lateral esquerda.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-110">Then, select **Service management** on the left sidebar.</span></span> <span data-ttu-id="3b6f6-111">Os pedidos de atendimento do cliente são apresentados nos **bilhetes de Apoio.**</span><span class="sxs-lookup"><span data-stu-id="3b6f6-111">The customer's service requests are displayed under **Support tickets**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3b6f6-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3b6f6-112">Prerequisites</span></span>

- <span data-ttu-id="3b6f6-113">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3b6f6-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3b6f6-114">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-114">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="3b6f6-115">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b6f6-115">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="3b6f6-116">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-116">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="3b6f6-117">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-117">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="3b6f6-118">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="3b6f6-118">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="3b6f6-119">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="3b6f6-119">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="3b6f6-120">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b6f6-120">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="3b6f6-121">C\#</span><span class="sxs-lookup"><span data-stu-id="3b6f6-121">C\#</span></span>

<span data-ttu-id="3b6f6-122">Para apresentar uma lista de todos os pedidos de serviço de um cliente, utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="3b6f6-122">To display a list of all of a customer's service requests, use your **IAggregatePartner.Customers** collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="3b6f6-123">Em seguida, ligue para a propriedade [**ServiceRequests,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicerequests) seguida dos métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="3b6f6-123">Then call the [**ServiceRequests**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicerequests) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId as string;

ResourceCollection<ServiceRequest> serviceRequests = partnerOperations.Customers.ById(customerId).ServiceRequests.Get();
```

<span data-ttu-id="3b6f6-124">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="3b6f6-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="3b6f6-125">**Projeto**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span><span class="sxs-lookup"><span data-stu-id="3b6f6-125">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="3b6f6-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="3b6f6-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3b6f6-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b6f6-127">Request syntax</span></span>

| <span data-ttu-id="3b6f6-128">Método</span><span class="sxs-lookup"><span data-stu-id="3b6f6-128">Method</span></span>  | <span data-ttu-id="3b6f6-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="3b6f6-129">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3b6f6-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="3b6f6-130">**GET**</span></span> | <span data-ttu-id="3b6f6-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/servicerequests HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="3b6f6-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/servicerequests HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="3b6f6-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="3b6f6-132">URI parameter</span></span>

<span data-ttu-id="3b6f6-133">Utilize o seguinte parâmetro de consulta para obter todos os pedidos de serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-133">Use the following query parameter to get all service requests for the customer.</span></span>

| <span data-ttu-id="3b6f6-134">Nome</span><span class="sxs-lookup"><span data-stu-id="3b6f6-134">Name</span></span>                   | <span data-ttu-id="3b6f6-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="3b6f6-135">Type</span></span>     | <span data-ttu-id="3b6f6-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="3b6f6-136">Required</span></span> | <span data-ttu-id="3b6f6-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b6f6-137">Description</span></span>                            |
|------------------------|----------|----------|----------------------------------------|
| <span data-ttu-id="3b6f6-138">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="3b6f6-138">**customer-tenant-id**</span></span> | <span data-ttu-id="3b6f6-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="3b6f6-139">**guid**</span></span> | <span data-ttu-id="3b6f6-140">Y</span><span class="sxs-lookup"><span data-stu-id="3b6f6-140">Y</span></span>        | <span data-ttu-id="3b6f6-141">Um GUID correspondente ao cliente..</span><span class="sxs-lookup"><span data-stu-id="3b6f6-141">A GUID corresponding to the customer..</span></span> |

### <a name="request-headers"></a><span data-ttu-id="3b6f6-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="3b6f6-142">Request headers</span></span>

<span data-ttu-id="3b6f6-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3b6f6-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3b6f6-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="3b6f6-144">Request body</span></span>

<span data-ttu-id="3b6f6-145">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="3b6f6-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="3b6f6-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/servicerequests HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 53d5d48c-9693-46b6-8071-2eed07797d6c
MS-CorrelationId: 998e31a1-3f17-4471-a9ee-7678dd72e033
```

## <a name="rest-response"></a><span data-ttu-id="3b6f6-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="3b6f6-147">REST response</span></span>

<span data-ttu-id="3b6f6-148">Se for bem sucedido, este método devolve uma recolha de recursos **de Pedido** de Serviço no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-148">If successful, this method returns a collection of **Service Request** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3b6f6-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="3b6f6-149">Response success and error codes</span></span>

<span data-ttu-id="3b6f6-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3b6f6-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="3b6f6-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3b6f6-152">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="3b6f6-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3b6f6-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="3b6f6-153">Response example</span></span>

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
