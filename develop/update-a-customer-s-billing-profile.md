---
title: Atualizar o perfil de faturação de um cliente
description: Atualiza o perfil de faturação de um cliente, incluindo o endereço associado ao perfil.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 1605c3e8cb050717209cb482d2299e2a42b9b186
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530043"
---
# <a name="update-a-customers-billing-profile"></a><span data-ttu-id="95aa3-103">Atualizar o perfil de faturação de um cliente</span><span class="sxs-lookup"><span data-stu-id="95aa3-103">Update a customer's billing profile</span></span>

<span data-ttu-id="95aa3-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="95aa3-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="95aa3-105">Atualiza o perfil de faturação de um cliente, incluindo o endereço associado ao perfil.</span><span class="sxs-lookup"><span data-stu-id="95aa3-105">Updates a customer's billing profile, including the address associated with the profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95aa3-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="95aa3-106">Prerequisites</span></span>

- <span data-ttu-id="95aa3-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="95aa3-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="95aa3-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="95aa3-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="95aa3-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="95aa3-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="95aa3-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="95aa3-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="95aa3-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="95aa3-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="95aa3-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="95aa3-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="95aa3-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="95aa3-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="95aa3-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="95aa3-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="95aa3-115">C\#</span><span class="sxs-lookup"><span data-stu-id="95aa3-115">C\#</span></span>

<span data-ttu-id="95aa3-116">Para atualizar o perfil de faturação de um cliente, recupere o perfil de faturação e atualize as propriedades conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="95aa3-116">To update a customer's billing profile, retrieve the billing profile and update the properties as necessary.</span></span> <span data-ttu-id="95aa3-117">Em seguida, recupere a sua coleção [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e, em seguida, ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="95aa3-117">Then, retrieve your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection, and then call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="95aa3-118">Em seguida, ligue para a propriedade [**Profiles,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) seguida pela propriedade [**Billing.**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing)</span><span class="sxs-lookup"><span data-stu-id="95aa3-118">Then call the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, followed by the [**Billing**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) property.</span></span> <span data-ttu-id="95aa3-119">Em seguida, termine ligando para os métodos [**Update()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.update) ou [**UpdateAsync().**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.updateasync)</span><span class="sxs-lookup"><span data-stu-id="95aa3-119">Then, finish by calling the [**Update()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.update) or [**UpdateAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.updateasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;

var billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Get();

// Apply changes to profile;

billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Update(billingProfile);
```

<span data-ttu-id="95aa3-120">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="95aa3-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="95aa3-121">**Project**: PartnerSDK.FeatureSamples **Class**: UpdateCustomerBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="95aa3-121">**Project**: PartnerSDK.FeatureSamples **Class**: UpdateCustomerBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="95aa3-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="95aa3-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="95aa3-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="95aa3-123">Request syntax</span></span>

| <span data-ttu-id="95aa3-124">Método</span><span class="sxs-lookup"><span data-stu-id="95aa3-124">Method</span></span>  | <span data-ttu-id="95aa3-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="95aa3-125">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="95aa3-126">**PUT**</span><span class="sxs-lookup"><span data-stu-id="95aa3-126">**PUT**</span></span> | <span data-ttu-id="95aa3-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/perfis/faturação HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="95aa3-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="95aa3-128">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="95aa3-128">URI parameter</span></span>

<span data-ttu-id="95aa3-129">Utilize o seguinte parâmetro de consulta para atualizar o perfil de faturação.</span><span class="sxs-lookup"><span data-stu-id="95aa3-129">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="95aa3-130">Nome</span><span class="sxs-lookup"><span data-stu-id="95aa3-130">Name</span></span>                   | <span data-ttu-id="95aa3-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="95aa3-131">Type</span></span>     | <span data-ttu-id="95aa3-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="95aa3-132">Required</span></span> | <span data-ttu-id="95aa3-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="95aa3-133">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="95aa3-134">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="95aa3-134">**customer-tenant-id**</span></span> | <span data-ttu-id="95aa3-135">**guid**</span><span class="sxs-lookup"><span data-stu-id="95aa3-135">**guid**</span></span> | <span data-ttu-id="95aa3-136">Y</span><span class="sxs-lookup"><span data-stu-id="95aa3-136">Y</span></span>        | <span data-ttu-id="95aa3-137">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="95aa3-137">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="95aa3-138">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="95aa3-138">Request headers</span></span>

- <span data-ttu-id="95aa3-139">**Se-Match**: " &lt; ETag &gt; " é necessário para deteção de concuência.</span><span class="sxs-lookup"><span data-stu-id="95aa3-139">**If-Match**: "&lt;ETag&gt;" is required for concurrency detection.</span></span>
<span data-ttu-id="95aa3-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="95aa3-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="95aa3-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="95aa3-141">Request body</span></span>

<span data-ttu-id="95aa3-142">O recurso completo.</span><span class="sxs-lookup"><span data-stu-id="95aa3-142">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="95aa3-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="95aa3-143">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ff85f13a-eb65-4b8e-9b67-05beb0565410
MS-CorrelationId: ff1b757d-cfaf-463a-b48b-0f96d05e95d7
Content-Type: application/json
Content-Length: 639
Expect: 100-continue

{
    "Id": "a58ceba5-60ac-48e4-a0bc-2a855811807a",
    "FirstName": "FirstName",
    "LastName": "LastName",
    "Email": "email@sample.com",
    "Culture": "en-US",
    "Language": "en",
    "CompanyName": "CompanyName",
    "DefaultAddress": {
        "Country": "US",
        "Region": null,
        "City": "Redmond",
        "State": "WA",
        "AddressLine1": "One Microsoft Way",
        "AddressLine2": null,
        "PostalCode": "98052",
        "FirstName": "FirstName",
        "LastName": "LastName",
        "PhoneNumber": "4255555555"
    },
    "Links": {
        "Self": {
            "Uri": "/v1/customers/<customer-tenant-id>/profiles/billing",
            "Method": "GET",
            "Headers": []
        }
    },
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "CustomerBillingProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="95aa3-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="95aa3-144">REST response</span></span>

<span data-ttu-id="95aa3-145">Se for bem sucedido, este método devolve as propriedades [atualizadas](profile-resources.md) dos recursos de perfil no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="95aa3-145">If successful, this method returns updated [Profile](profile-resources.md) resource properties in the response body.</span></span> <span data-ttu-id="95aa3-146">Esta chamada requer um ETag para deteção de concordância.</span><span class="sxs-lookup"><span data-stu-id="95aa3-146">This call requires an ETag for concurrency detection.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="95aa3-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="95aa3-147">Response success and error codes</span></span>

<span data-ttu-id="95aa3-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="95aa3-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="95aa3-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="95aa3-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="95aa3-150">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="95aa3-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="95aa3-151">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="95aa3-151">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1210
Content-Type: application/json
MS-CorrelationId: ff1b757d-cfaf-463a-b48b-0f96d05e95d7
MS-RequestId: ff85f13a-eb65-4b8e-9b67-05beb0565410
Date: Mon, 23 Nov 2015 18:20:43 GMT

{
    "id": "a58ceba5-60ac-48e4-a0bc-2a855811807a",
    "firstName": "FirstName",
    "lastName": "LastName",
    "email": "email@sample.com",
    "culture": "en-US",
    "language": "en",
    "companyName": "companyName",
    "defaultAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "One Microsoft Way",
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
