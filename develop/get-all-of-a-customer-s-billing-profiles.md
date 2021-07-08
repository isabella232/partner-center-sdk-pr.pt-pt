---
title: Obter o perfil de faturação de um cliente
description: Obtém o perfil de faturação de um cliente. No painel partner Center, esta operação pode ser realizada selecionando primeiro um cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: d22be53a5be4efcda76a568578468615495febb6
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760594"
---
# <a name="get-a-customers-billing-profile"></a><span data-ttu-id="49501-104">Obter o perfil de faturação de um cliente</span><span class="sxs-lookup"><span data-stu-id="49501-104">Get a customer's billing profile</span></span>

<span data-ttu-id="49501-105">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="49501-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="49501-106">Obtém o perfil de faturação de um cliente.</span><span class="sxs-lookup"><span data-stu-id="49501-106">Gets the billing profile of a customer.</span></span>

<span data-ttu-id="49501-107">No painel partner Center, esta operação pode ser realizada selecionando primeiro [um cliente.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="49501-107">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="49501-108">Em seguida, sob o nome do cliente na barra lateral esquerda, selecione **Conta**.</span><span class="sxs-lookup"><span data-stu-id="49501-108">Then, under the customer's name in the left sidebar, select **Account**.</span></span> <span data-ttu-id="49501-109">O perfil de faturação pode ser encontrado no título **de informação do Bill-to.**</span><span class="sxs-lookup"><span data-stu-id="49501-109">The billing profile can be found under the **Bill-to info** heading.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49501-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="49501-110">Prerequisites</span></span>

- <span data-ttu-id="49501-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="49501-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="49501-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="49501-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="49501-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="49501-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="49501-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="49501-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="49501-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="49501-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="49501-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="49501-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="49501-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="49501-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="49501-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="49501-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="49501-119">C\#</span><span class="sxs-lookup"><span data-stu-id="49501-119">C\#</span></span>

<span data-ttu-id="49501-120">Para obter o perfil de faturação de um cliente, utilize a sua coleção [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="49501-120">To get a customer's billing profile, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="49501-121">Em seguida, ligue para a propriedade [**Profiles,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) seguida pela propriedade [**Billing.**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing)</span><span class="sxs-lookup"><span data-stu-id="49501-121">Then call the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, followed by the [**Billing**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) property.</span></span> <span data-ttu-id="49501-122">Por fim, ligue para os métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync)</span><span class="sxs-lookup"><span data-stu-id="49501-122">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;

var billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Get();
```

<span data-ttu-id="49501-123">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="49501-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="49501-124">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="49501-124">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="49501-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="49501-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="49501-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="49501-126">Request syntax</span></span>

| <span data-ttu-id="49501-127">Método</span><span class="sxs-lookup"><span data-stu-id="49501-127">Method</span></span>  | <span data-ttu-id="49501-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="49501-128">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="49501-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="49501-129">**GET**</span></span> | <span data-ttu-id="49501-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/perfis/faturação HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="49501-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="49501-131">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="49501-131">URI parameter</span></span>

<span data-ttu-id="49501-132">Utilize o seguinte parâmetro de consulta para obter o perfil de faturação.</span><span class="sxs-lookup"><span data-stu-id="49501-132">Use the following query parameter to get the billing profile.</span></span>

| <span data-ttu-id="49501-133">Nome</span><span class="sxs-lookup"><span data-stu-id="49501-133">Name</span></span>                   | <span data-ttu-id="49501-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="49501-134">Type</span></span>     | <span data-ttu-id="49501-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="49501-135">Required</span></span> | <span data-ttu-id="49501-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="49501-136">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="49501-137">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="49501-137">**customer-tenant-id**</span></span> | <span data-ttu-id="49501-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="49501-138">**guid**</span></span> | <span data-ttu-id="49501-139">Y</span><span class="sxs-lookup"><span data-stu-id="49501-139">Y</span></span>        | <span data-ttu-id="49501-140">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="49501-140">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="49501-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="49501-141">Request headers</span></span>

<span data-ttu-id="49501-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="49501-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="49501-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="49501-143">Request body</span></span>

<span data-ttu-id="49501-144">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="49501-144">None</span></span>

### <a name="request-example"></a><span data-ttu-id="49501-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="49501-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a5581a74-2778-4e34-9172-18baa4877081
MS-CorrelationId: 51d521b3-62db-4682-b75d-fb8ab09113b2
```

## <a name="rest-response"></a><span data-ttu-id="49501-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="49501-146">REST response</span></span>

<span data-ttu-id="49501-147">Se for bem sucedido, este método devolve uma coleção de recursos de [perfil](profile-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="49501-147">If successful, this method returns a collection of [Profile](profile-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="49501-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="49501-148">Response success and error codes</span></span>

<span data-ttu-id="49501-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="49501-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="49501-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="49501-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="49501-151">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="49501-151">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="49501-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="49501-152">Response example</span></span>

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
