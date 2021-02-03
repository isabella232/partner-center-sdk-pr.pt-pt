---
title: Obter o perfil de faturação de um cliente
description: Obtém o perfil de faturação de um cliente. No painel partner Center, esta operação pode ser realizada selecionando primeiro um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 6c837c1c220e334df82e75eb680b6012862c9686
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769733"
---
# <a name="get-a-customers-billing-profile"></a><span data-ttu-id="72377-103">Obter o perfil de faturação de um cliente</span><span class="sxs-lookup"><span data-stu-id="72377-103">Get a customer's billing profile</span></span>

<span data-ttu-id="72377-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="72377-104">**Applies To**</span></span>

- <span data-ttu-id="72377-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="72377-105">Partner Center</span></span>
- <span data-ttu-id="72377-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="72377-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="72377-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="72377-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="72377-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="72377-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="72377-109">Obtém o perfil de faturação de um cliente.</span><span class="sxs-lookup"><span data-stu-id="72377-109">Gets the billing profile of a customer.</span></span>

<span data-ttu-id="72377-110">No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="72377-110">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="72377-111">Em seguida, sob o nome do cliente na barra lateral esquerda, selecione **Conta**.</span><span class="sxs-lookup"><span data-stu-id="72377-111">Then, under the customer's name in the left sidebar, select **Account**.</span></span> <span data-ttu-id="72377-112">O perfil de faturação pode ser encontrado no título **de informação do Bill-to.**</span><span class="sxs-lookup"><span data-stu-id="72377-112">The billing profile can be found under the **Bill-to info** heading.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72377-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="72377-113">Prerequisites</span></span>

- <span data-ttu-id="72377-114">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="72377-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="72377-115">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="72377-115">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="72377-116">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="72377-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="72377-117">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="72377-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="72377-118">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="72377-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="72377-119">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="72377-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="72377-120">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="72377-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="72377-121">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="72377-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="72377-122">C\#</span><span class="sxs-lookup"><span data-stu-id="72377-122">C\#</span></span>

<span data-ttu-id="72377-123">Para obter o perfil de faturação de um cliente, utilize a sua coleção [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="72377-123">To get a customer's billing profile, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="72377-124">Em seguida, ligue para a propriedade [**Profiles,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) seguida pela propriedade [**Billing.**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing)</span><span class="sxs-lookup"><span data-stu-id="72377-124">Then call the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, followed by the [**Billing**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) property.</span></span> <span data-ttu-id="72377-125">Por fim, ligue para os métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync)</span><span class="sxs-lookup"><span data-stu-id="72377-125">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;

var billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Get();
```

<span data-ttu-id="72377-126">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="72377-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="72377-127">**Projeto**: PartnerSDK.FeatureSamples **Class**: GetCustomerBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="72377-127">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="72377-128">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="72377-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="72377-129">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="72377-129">Request syntax</span></span>

| <span data-ttu-id="72377-130">Método</span><span class="sxs-lookup"><span data-stu-id="72377-130">Method</span></span>  | <span data-ttu-id="72377-131">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="72377-131">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="72377-132">**Obter**</span><span class="sxs-lookup"><span data-stu-id="72377-132">**GET**</span></span> | <span data-ttu-id="72377-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/perfis/faturação HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="72377-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="72377-134">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="72377-134">URI parameter</span></span>

<span data-ttu-id="72377-135">Utilize o seguinte parâmetro de consulta para obter o perfil de faturação.</span><span class="sxs-lookup"><span data-stu-id="72377-135">Use the following query parameter to get the billing profile.</span></span>

| <span data-ttu-id="72377-136">Nome</span><span class="sxs-lookup"><span data-stu-id="72377-136">Name</span></span>                   | <span data-ttu-id="72377-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="72377-137">Type</span></span>     | <span data-ttu-id="72377-138">Necessário</span><span class="sxs-lookup"><span data-stu-id="72377-138">Required</span></span> | <span data-ttu-id="72377-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="72377-139">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="72377-140">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="72377-140">**customer-tenant-id**</span></span> | <span data-ttu-id="72377-141">**guid**</span><span class="sxs-lookup"><span data-stu-id="72377-141">**guid**</span></span> | <span data-ttu-id="72377-142">Y</span><span class="sxs-lookup"><span data-stu-id="72377-142">Y</span></span>        | <span data-ttu-id="72377-143">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="72377-143">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="72377-144">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="72377-144">Request headers</span></span>

<span data-ttu-id="72377-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="72377-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="72377-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="72377-146">Request body</span></span>

<span data-ttu-id="72377-147">Nenhum</span><span class="sxs-lookup"><span data-stu-id="72377-147">None</span></span>

### <a name="request-example"></a><span data-ttu-id="72377-148">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="72377-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a5581a74-2778-4e34-9172-18baa4877081
MS-CorrelationId: 51d521b3-62db-4682-b75d-fb8ab09113b2
```

## <a name="rest-response"></a><span data-ttu-id="72377-149">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="72377-149">REST response</span></span>

<span data-ttu-id="72377-150">Se for bem sucedido, este método devolve uma coleção de recursos de [perfil](profile-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="72377-150">If successful, this method returns a collection of [Profile](profile-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="72377-151">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="72377-151">Response success and error codes</span></span>

<span data-ttu-id="72377-152">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="72377-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="72377-153">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="72377-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="72377-154">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="72377-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="72377-155">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="72377-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1206
Content-Type: application/json
MS-CorrelationId: 51d521b3-62db-4682-b75d-fb8ab09113b2
MS-RequestId: a5581a74-2778-4e34-9172-18baa4877081
Date: Mon, 23 Nov 2015 18:13:43 GMT

{
    "id": "<billing-profile-id>",
    "firstName": "FirstName",
    "lastName": "LastName",
    "email": "email@sample.com",
    "culture": "en-US",
    "language": "en",
    "companyName": "CompanyName",
    "defaultAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "1 Microsoft Way",
        "postalCode": "98052",
        "firstName": "FirstName",
        "lastName": "LastName",
        "phoneNumber": "4255555555"
    },
    "links": {
        "self": {
            "uri": "/v1/customers/<customer-tenant-id>/profiles/billing",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "<etag>",
        "objectType": "CustomerBillingProfile"
    }
}
```
