---
title: Atualizar o perfil de faturação de um cliente
description: Atualiza o perfil de faturação de um cliente, incluindo o endereço associado ao perfil.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: adf4e3de9941fded632e0561624d91d854c5aa24
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769776"
---
# <a name="update-a-customers-billing-profile"></a><span data-ttu-id="e21c4-103">Atualizar o perfil de faturação de um cliente</span><span class="sxs-lookup"><span data-stu-id="e21c4-103">Update a customer's billing profile</span></span>

<span data-ttu-id="e21c4-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="e21c4-104">**Applies To**</span></span>

- <span data-ttu-id="e21c4-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="e21c4-105">Partner Center</span></span>
- <span data-ttu-id="e21c4-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="e21c4-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="e21c4-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="e21c4-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="e21c4-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e21c4-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e21c4-109">Atualiza o perfil de faturação de um cliente, incluindo o endereço associado ao perfil.</span><span class="sxs-lookup"><span data-stu-id="e21c4-109">Updates a customer's billing profile, including the address associated with the profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e21c4-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e21c4-110">Prerequisites</span></span>

- <span data-ttu-id="e21c4-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e21c4-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e21c4-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="e21c4-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e21c4-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e21c4-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e21c4-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e21c4-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e21c4-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="e21c4-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e21c4-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="e21c4-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e21c4-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="e21c4-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e21c4-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e21c4-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="e21c4-119">C\#</span><span class="sxs-lookup"><span data-stu-id="e21c4-119">C\#</span></span>

<span data-ttu-id="e21c4-120">Para atualizar o perfil de faturação de um cliente, recupere o perfil de faturação e atualize as propriedades conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e21c4-120">To update a customer's billing profile, retrieve the billing profile and update the properties as necessary.</span></span> <span data-ttu-id="e21c4-121">Em seguida, recupere a sua coleção [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) e, em seguida, ligue para o método [**ById().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="e21c4-121">Then, retrieve your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection, and then call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="e21c4-122">Em seguida, ligue para a propriedade [**Profiles,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) seguida pela propriedade [**Billing.**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing)</span><span class="sxs-lookup"><span data-stu-id="e21c4-122">Then call the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, followed by the [**Billing**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) property.</span></span> <span data-ttu-id="e21c4-123">Em seguida, termine ligando para os métodos [**Update()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.update) ou [**UpdateAsync().**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.updateasync)</span><span class="sxs-lookup"><span data-stu-id="e21c4-123">Then, finish by calling the [**Update()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.update) or [**UpdateAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.updateasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;

var billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Get();

// Apply changes to profile;

billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Update(billingProfile);
```

<span data-ttu-id="e21c4-124">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e21c4-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e21c4-125">**Projeto**: PartnerSDK.FeatureSamples **Class**: UpdateCustomerBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="e21c4-125">**Project**: PartnerSDK.FeatureSamples **Class**: UpdateCustomerBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e21c4-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="e21c4-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e21c4-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="e21c4-127">Request syntax</span></span>

| <span data-ttu-id="e21c4-128">Método</span><span class="sxs-lookup"><span data-stu-id="e21c4-128">Method</span></span>  | <span data-ttu-id="e21c4-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="e21c4-129">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e21c4-130">**PUT**</span><span class="sxs-lookup"><span data-stu-id="e21c4-130">**PUT**</span></span> | <span data-ttu-id="e21c4-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/perfis/faturação HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e21c4-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e21c4-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="e21c4-132">URI parameter</span></span>

<span data-ttu-id="e21c4-133">Utilize o seguinte parâmetro de consulta para atualizar o perfil de faturação.</span><span class="sxs-lookup"><span data-stu-id="e21c4-133">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="e21c4-134">Nome</span><span class="sxs-lookup"><span data-stu-id="e21c4-134">Name</span></span>                   | <span data-ttu-id="e21c4-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="e21c4-135">Type</span></span>     | <span data-ttu-id="e21c4-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="e21c4-136">Required</span></span> | <span data-ttu-id="e21c4-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="e21c4-137">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e21c4-138">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="e21c4-138">**customer-tenant-id**</span></span> | <span data-ttu-id="e21c4-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="e21c4-139">**guid**</span></span> | <span data-ttu-id="e21c4-140">Y</span><span class="sxs-lookup"><span data-stu-id="e21c4-140">Y</span></span>        | <span data-ttu-id="e21c4-141">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="e21c4-141">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e21c4-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="e21c4-142">Request headers</span></span>

- <span data-ttu-id="e21c4-143">**Se-Match**: " &lt; ETag &gt; " é necessário para deteção de concuência.</span><span class="sxs-lookup"><span data-stu-id="e21c4-143">**If-Match**: "&lt;ETag&gt;" is required for concurrency detection.</span></span>
<span data-ttu-id="e21c4-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e21c4-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e21c4-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="e21c4-145">Request body</span></span>

<span data-ttu-id="e21c4-146">O recurso completo.</span><span class="sxs-lookup"><span data-stu-id="e21c4-146">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="e21c4-147">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e21c4-147">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e21c4-148">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="e21c4-148">REST response</span></span>

<span data-ttu-id="e21c4-149">Se for bem sucedido, este método devolve as propriedades [atualizadas](profile-resources.md) dos recursos de perfil no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="e21c4-149">If successful, this method returns updated [Profile](profile-resources.md) resource properties in the response body.</span></span> <span data-ttu-id="e21c4-150">Esta chamada requer um ETag para deteção de concordância.</span><span class="sxs-lookup"><span data-stu-id="e21c4-150">This call requires an ETag for concurrency detection.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e21c4-151">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="e21c4-151">Response success and error codes</span></span>

<span data-ttu-id="e21c4-152">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="e21c4-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e21c4-153">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="e21c4-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e21c4-154">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="e21c4-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e21c4-155">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e21c4-155">Response example</span></span>

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
