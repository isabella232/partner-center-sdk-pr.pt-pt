---
title: Obter os serviços geridos para um cliente por ID
description: Obtém os serviços geridos para um cliente. Por outras palavras, obtenha links para todas as subscrições do cliente para as quais tenha delegado privilégios de administração. Pode utilizar estes links para fornecer pedidos de assistência e serviço de ficheiros com a Microsoft.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1cf7e7b62113bd96b00fdc2301e4e7ac4f5d4243
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548452"
---
# <a name="get-the-managed-services-for-a-customer-by-id"></a><span data-ttu-id="f2020-105">Obter os serviços geridos para um cliente por ID</span><span class="sxs-lookup"><span data-stu-id="f2020-105">Get the managed services for a customer by ID</span></span>

<span data-ttu-id="f2020-106">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="f2020-106">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="f2020-107">Obtém os serviços geridos para um cliente.</span><span class="sxs-lookup"><span data-stu-id="f2020-107">Gets the managed services for a customer.</span></span> <span data-ttu-id="f2020-108">Por outras palavras, obtenha links para todas as subscrições do cliente para as quais tenha delegado privilégios de administração.</span><span class="sxs-lookup"><span data-stu-id="f2020-108">In other words, get links to all of the customer's subscriptions for which you have delegated admin privileges.</span></span> <span data-ttu-id="f2020-109">Pode utilizar estes links para fornecer pedidos de assistência e serviço de ficheiros com a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f2020-109">You can use these links to provide support and file service requests with Microsoft.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2020-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f2020-110">Prerequisites</span></span>

- <span data-ttu-id="f2020-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f2020-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f2020-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="f2020-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="f2020-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f2020-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f2020-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f2020-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f2020-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="f2020-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f2020-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="f2020-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f2020-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="f2020-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f2020-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f2020-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="f2020-119">C\#</span><span class="sxs-lookup"><span data-stu-id="f2020-119">C\#</span></span>

<span data-ttu-id="f2020-120">Para apresentar uma lista de todos os serviços geridos para um cliente, utilize a sua coleção **IAggregatePartner.Customers** e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="f2020-120">To display a list of all the managed services for a customer, use your **IAggregatePartner.Customers** collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="f2020-121">Em seguida, ligue para a propriedade [**ManagedServices,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.managedservices) seguida dos métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="f2020-121">Then call the [**ManagedServices**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.managedservices) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerID as Customer;

ResourceCollection<ManagedService> managedServices = partnerOperations.Customers.ById(selectedCustomerId).ManagedServices.Get();
```

<span data-ttu-id="f2020-122">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="f2020-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="f2020-123">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span><span class="sxs-lookup"><span data-stu-id="f2020-123">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="f2020-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f2020-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f2020-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2020-125">Request syntax</span></span>

| <span data-ttu-id="f2020-126">Método</span><span class="sxs-lookup"><span data-stu-id="f2020-126">Method</span></span>  | <span data-ttu-id="f2020-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f2020-127">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f2020-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="f2020-128">**GET**</span></span> | <span data-ttu-id="f2020-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/serviços geridos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f2020-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/managedservices HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="f2020-130">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="f2020-130">URI parameter</span></span>

<span data-ttu-id="f2020-131">Utilize o seguinte parâmetro de consulta para obter os serviços geridos do cliente.</span><span class="sxs-lookup"><span data-stu-id="f2020-131">Use the following query parameter to get the customer's managed services.</span></span>

| <span data-ttu-id="f2020-132">Nome</span><span class="sxs-lookup"><span data-stu-id="f2020-132">Name</span></span>                   | <span data-ttu-id="f2020-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="f2020-133">Type</span></span>     | <span data-ttu-id="f2020-134">Necessário</span><span class="sxs-lookup"><span data-stu-id="f2020-134">Required</span></span> | <span data-ttu-id="f2020-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2020-135">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="f2020-136">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="f2020-136">**customer-tenant-id**</span></span> | <span data-ttu-id="f2020-137">**guid**</span><span class="sxs-lookup"><span data-stu-id="f2020-137">**guid**</span></span> | <span data-ttu-id="f2020-138">Y</span><span class="sxs-lookup"><span data-stu-id="f2020-138">Y</span></span>        | <span data-ttu-id="f2020-139">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="f2020-139">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f2020-140">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="f2020-140">Request headers</span></span>

<span data-ttu-id="f2020-141">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f2020-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f2020-142">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f2020-142">Request body</span></span>

<span data-ttu-id="f2020-143">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f2020-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f2020-144">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f2020-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/managedservices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4ff57220-f17b-4d8f-8e09-78334c57ba00
MS-CorrelationId: 03d6064a-f048-4aee-8892-ed46dc5c8bee
```

## <a name="rest-response"></a><span data-ttu-id="f2020-145">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f2020-145">REST response</span></span>

<span data-ttu-id="f2020-146">Se for bem sucedido, este método devolve uma coleção de objetos de **Serviço Gerido** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="f2020-146">If successful, this method returns a collection of **Managed Service** objects in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f2020-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f2020-147">Response success and error codes</span></span>

<span data-ttu-id="f2020-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f2020-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f2020-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f2020-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f2020-150">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f2020-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f2020-151">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f2020-151">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 10588
Content-Type: application/json
MS-CorrelationId: 03d6064a-f048-4aee-8892-ed46dc5c8bee
MS-RequestId: 4ff57220-f17b-4d8f-8e09-78334c57ba00
Date: Mon, 23 Nov 2015 18:02:12 GMT

{
    "totalCount": 2,
    "items": [{
        "id": "Exchange",
        "name": "Exchange",
        "groupName": "Office",
        "links": {
            "adminService": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=Exchange&InitialDomain=<domain>&PrimaryDomain=<domain>",
                "method": "GET",
                "headers": []
            },
            "serviceHealth": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=ServiceStatus",
                "method": "GET",
                "headers": []
            },
            "serviceTicket": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=Support",
                "method": "GET",
                "headers": []
            }
        },
        "attributes": {
            "objectType": "ManagedService"
        }
    },
    {
        "id": "MicrosoftCommunicationsOnline",
        "name": "SkypeforBusiness",
        "groupName": "Office",
        "links": {
            "adminService": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=MicrosoftCommunicationsOnline",
                "method": "GET",
                "headers": []
            },
            "serviceHealth": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=ServiceStatus",
                "method": "GET",
                "headers": []
            },
            "serviceTicket": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=Support",
                "method": "GET",
                "headers": []
            }
        },
        "attributes": {
            "objectType": "ManagedService"
        }
    }
```
