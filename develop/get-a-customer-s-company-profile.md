---
title: Obter o perfil empresarial de um cliente
description: Obtém o perfil da empresa de um cliente.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: c26a86ecb96e5e7942ba179f8a3cc704abab7df5
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769373"
---
# <a name="get-a-customers-company-profile"></a><span data-ttu-id="5c8f4-103">Obter o perfil empresarial de um cliente</span><span class="sxs-lookup"><span data-stu-id="5c8f4-103">Get a customer's company profile</span></span>

<span data-ttu-id="5c8f4-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="5c8f4-104">**Applies To**</span></span>

- <span data-ttu-id="5c8f4-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="5c8f4-105">Partner Center</span></span>
- <span data-ttu-id="5c8f4-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="5c8f4-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="5c8f4-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="5c8f4-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="5c8f4-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5c8f4-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5c8f4-109">Obtém o perfil da empresa de um cliente.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-109">Gets the company profile of a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5c8f4-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5c8f4-110">Prerequisites</span></span>

- <span data-ttu-id="5c8f4-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5c8f4-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5c8f4-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="5c8f4-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5c8f4-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5c8f4-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5c8f4-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5c8f4-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="5c8f4-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5c8f4-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="5c8f4-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5c8f4-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5c8f4-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="5c8f4-119">C\#</span><span class="sxs-lookup"><span data-stu-id="5c8f4-119">C\#</span></span>

<span data-ttu-id="5c8f4-120">Para obter o perfil da empresa para um cliente, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-120">To get the company profile for a customer, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="5c8f4-121">Em seguida, obtenha a interface [**ICustomerProfileCollection**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection) do cliente a partir da propriedade [**Profiles,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) de forma a aceder à sua propriedade da Empresa.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-121">Then get the customer's [**ICustomerProfileCollection**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection) interface from the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, in order to access its Company property.</span></span> <span data-ttu-id="5c8f4-122">Em seguida, obtenha a interface [**ICustomerReadonlyProfile**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1) a partir da propriedade [**ICustomerProfileCollection.Company,**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.company) e ligue para os seus métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync)</span><span class="sxs-lookup"><span data-stu-id="5c8f4-122">Next, get the [**ICustomerReadonlyProfile**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1) interface from the [**ICustomerProfileCollection.Company**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.company) property, and call its [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var companyProfile = partnerOperations.Customers.ById(customerId).Profiles.Company.Get();
```

<span data-ttu-id="5c8f4-123">**Amostra**: [Descarregue o Partner Center SDK](https://go.microsoft.com/fwlink/p/?LinkId=746681).</span><span class="sxs-lookup"><span data-stu-id="5c8f4-123">**Sample**: [Download the Partner Center SDK](https://go.microsoft.com/fwlink/p/?LinkId=746681).</span></span> <span data-ttu-id="5c8f4-124">**Projeto**: PartnerSdk.FeatureSamples **Class**: GetCustomerCompanyProfile.cs</span><span class="sxs-lookup"><span data-stu-id="5c8f4-124">**Project**: PartnerSdk.FeatureSamples **Class**: GetCustomerCompanyProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="5c8f4-125">Java</span><span class="sxs-lookup"><span data-stu-id="5c8f4-125">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="5c8f4-126">Para obter o perfil da empresa para um cliente, ligue para o **IAggregatePartner.getCustomers ().byId** função com o identificador de cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-126">To get the company profile for a customer, call the **IAggregatePartner.getCustomers().byId** function with the customer identifier to identify the customer.</span></span> <span data-ttu-id="5c8f4-127">Em seguida, obtenha a interface **ICustomerProfileCollection** do cliente a partir da função **[getProfiles**], de forma a aceder à sua propriedade da Empresa.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-127">Then get the customer's **ICustomerProfileCollection** interface from the [**getProfiles**] function, in order to access its Company property.</span></span> <span data-ttu-id="5c8f4-128">Em seguida, obtenha a interface **ICustomerReadonlyProfile** a partir da função **ICustomerProfileCollection.getCompany** e ligue para a função **get.**</span><span class="sxs-lookup"><span data-stu-id="5c8f4-128">Next, get the **ICustomerReadonlyProfile** interface from the **ICustomerProfileCollection.getCompany** function, and call the **get** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;

CustomerCompanyProfile companyProfile = partnerOperations.getCustomers().byId(customerId).getProfiles().getCompany().get();
```

## <a name="rest-request"></a><span data-ttu-id="5c8f4-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5c8f4-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5c8f4-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c8f4-130">Request syntax</span></span>

| <span data-ttu-id="5c8f4-131">Método</span><span class="sxs-lookup"><span data-stu-id="5c8f4-131">Method</span></span>  | <span data-ttu-id="5c8f4-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5c8f4-132">Request URI</span></span>                                                             |
|---------|-------------------------------------------------------------------------|
| <span data-ttu-id="5c8f4-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="5c8f4-133">**GET**</span></span> | <span data-ttu-id="5c8f4-134">*{baseURL}*/v1/clientes/{cliente-inquilino-id}/perfis/empresa HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5c8f4-134">*{baseURL}*/v1/customers/{customer-tenant-id}/profiles/company HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="5c8f4-135">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="5c8f4-135">URI parameter</span></span>

<span data-ttu-id="5c8f4-136">Utilize o seguinte parâmetro de consulta para obter o perfil da empresa.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-136">Use the following query parameter to get the company profile.</span></span>

| <span data-ttu-id="5c8f4-137">Nome</span><span class="sxs-lookup"><span data-stu-id="5c8f4-137">Name</span></span>                   | <span data-ttu-id="5c8f4-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="5c8f4-138">Type</span></span>     | <span data-ttu-id="5c8f4-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="5c8f4-139">Required</span></span> | <span data-ttu-id="5c8f4-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c8f4-140">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5c8f4-141">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="5c8f4-141">**customer-tenant-id**</span></span> | <span data-ttu-id="5c8f4-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="5c8f4-142">**guid**</span></span> | <span data-ttu-id="5c8f4-143">Y</span><span class="sxs-lookup"><span data-stu-id="5c8f4-143">Y</span></span>        | <span data-ttu-id="5c8f4-144">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-144">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5c8f4-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="5c8f4-145">Request headers</span></span>

<span data-ttu-id="5c8f4-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5c8f4-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5c8f4-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5c8f4-147">Request body</span></span>

<span data-ttu-id="5c8f4-148">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5c8f4-148">None</span></span>

### <a name="request-example"></a><span data-ttu-id="5c8f4-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5c8f4-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/profiles/company HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0b6f039c-e4b5-4b9e-bdac-b39077bb60da
MS-CorrelationId: ffa9174c-dbcb-47de-b70d-10e640a7f1b4
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="5c8f4-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5c8f4-150">REST response</span></span>

<span data-ttu-id="5c8f4-151">Se for bem sucedido, este método devolve informações no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-151">If successful, this method returns information in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5c8f4-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5c8f4-152">Response success and error codes</span></span>

<span data-ttu-id="5c8f4-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5c8f4-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5c8f4-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5c8f4-155">Para obter a lista completa, consulte [os Códigos de Erro DO Centro de Parceiros REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="5c8f4-155">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5c8f4-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5c8f4-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 488
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ffa9174c-dbcb-47de-b70d-10e640a7f1b4
MS-RequestId: 0b6f039c-e4b5-4b9e-bdac-b39077bb60da
MS-CV: /e74N8OrkE29ycwZ.0
MS-ServerId: 101112202
Date: Wed, 04 Jan 2017 19:48:51 GMT

{
    "tenantId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "domain": "dtdemocspcustomer005.onmicrosoft.com",
    "companyName": "DT Demo CSP Customer 005",
    "address": {
        "country": "US",
        "region": "WA",
        "city": "Redmond ",
        "addressLine1": "1 Microsoft Way",
        "postalCode": "98052",
        "phoneNumber": "4155551212"
    },
    "email": "daniel@hotmail.com.tw",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/profiles/company",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "CustomerCompanyProfile"
    }
}
```
