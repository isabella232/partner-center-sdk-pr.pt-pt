---
title: Obter um cliente por ID
description: Obtém um recurso do Cliente que corresponde a uma identificação do cliente.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 196d653c789c4b4e1327f0c6e5d2531a18681a71
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874997"
---
# <a name="get-a-customer-by-id"></a><span data-ttu-id="98616-103">Obter um cliente por ID</span><span class="sxs-lookup"><span data-stu-id="98616-103">Get a customer by ID</span></span>

<span data-ttu-id="98616-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="98616-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="98616-105">Obtém um recurso **do Cliente** que corresponde a uma identificação do cliente.</span><span class="sxs-lookup"><span data-stu-id="98616-105">Gets a **Customer** resource that corresponds to a customer ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="98616-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="98616-106">Prerequisites</span></span>

- <span data-ttu-id="98616-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="98616-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="98616-108">Este cenário suporta credenciais de app+user ou autenticação apenas para aplicações.</span><span class="sxs-lookup"><span data-stu-id="98616-108">This scenario supports app+user credentials or app-only authentication.</span></span>

- <span data-ttu-id="98616-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="98616-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="98616-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="98616-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="98616-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="98616-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="98616-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="98616-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="98616-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="98616-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="98616-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="98616-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="98616-115">C\#</span><span class="sxs-lookup"><span data-stu-id="98616-115">C\#</span></span>

<span data-ttu-id="98616-116">Para obter um cliente por ID, use a sua coleção [**IAggregatePartner.Customers,**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) ligue para o método [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) e, em seguida, ligue para os métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.getasync)</span><span class="sxs-lookup"><span data-stu-id="98616-116">To get a customer by ID, use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection, call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method, then call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

Customer customerInfo = partnerOperations.Customers.ById(customerIdToRetrieve).Get();
```

<span data-ttu-id="98616-117">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="98616-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="98616-118">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerInformation.cs</span><span class="sxs-lookup"><span data-stu-id="98616-118">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerInformation.cs</span></span>

## <a name="java"></a><span data-ttu-id="98616-119">Java</span><span class="sxs-lookup"><span data-stu-id="98616-119">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="98616-120">Para obter um cliente por ID, use a função **IAggregatePartner.getCustomers,** ligue para a função **byId()** e, em seguida, ligue para a função **get().**</span><span class="sxs-lookup"><span data-stu-id="98616-120">To get a customer by ID, use your **IAggregatePartner.getCustomers** function, call the **byId()** function, then call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerIdToRetrieve;

Customer customerInfo = partnerOperations.getCustomers().byId(customerIdToRetrieve).get();
```

## <a name="powershell"></a><span data-ttu-id="98616-121">PowerShell</span><span class="sxs-lookup"><span data-stu-id="98616-121">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="98616-122">Para obter um cliente por ID, execute o comando [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) e especifique o parâmetro **CustomerId.**</span><span class="sxs-lookup"><span data-stu-id="98616-122">To get a customer by ID, execute the [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) command and specify the **CustomerId** parameter.</span></span>

```powershell
Get-PartnerCustomer -CustomerId '2ca7de6c-c05c-46b5-b689-32e53573a97a'
```

## <a name="rest-request"></a><span data-ttu-id="98616-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="98616-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="98616-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="98616-124">Request syntax</span></span>

| <span data-ttu-id="98616-125">Método</span><span class="sxs-lookup"><span data-stu-id="98616-125">Method</span></span>  | <span data-ttu-id="98616-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="98616-126">Request URI</span></span>                                                                            |
|---------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="98616-127">**Obter**</span><span class="sxs-lookup"><span data-stu-id="98616-127">**GET**</span></span> | <span data-ttu-id="98616-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="98616-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="98616-129">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="98616-129">URI parameter</span></span>

<span data-ttu-id="98616-130">Utilize o seguinte parâmetro de consulta a um cliente específico.</span><span class="sxs-lookup"><span data-stu-id="98616-130">Use the following query parameter to a specific customer.</span></span>

| <span data-ttu-id="98616-131">Nome</span><span class="sxs-lookup"><span data-stu-id="98616-131">Name</span></span>                   | <span data-ttu-id="98616-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="98616-132">Type</span></span>     | <span data-ttu-id="98616-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="98616-133">Required</span></span> | <span data-ttu-id="98616-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="98616-134">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="98616-135">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="98616-135">**customer-tenant-id**</span></span> | <span data-ttu-id="98616-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="98616-136">**guid**</span></span> | <span data-ttu-id="98616-137">Y</span><span class="sxs-lookup"><span data-stu-id="98616-137">Y</span></span>        | <span data-ttu-id="98616-138">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="98616-138">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="98616-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="98616-139">Request headers</span></span>

<span data-ttu-id="98616-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="98616-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="98616-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="98616-141">Request body</span></span>

<span data-ttu-id="98616-142">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="98616-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="98616-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="98616-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: a176c585-b5de-4d65-824c-67a6deb45cd9
MS-RequestId: 74ca1db9-df92-41c6-a362-a16433b0542b
```

## <a name="rest-response"></a><span data-ttu-id="98616-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="98616-144">REST response</span></span>

<span data-ttu-id="98616-145">Se for bem sucedido, este método devolve um recurso [do Cliente](customer-resources.md#customer) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="98616-145">If successful, this method returns a [Customer](customer-resources.md#customer) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="98616-146">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="98616-146">Response success and error codes</span></span>

<span data-ttu-id="98616-147">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="98616-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="98616-148">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="98616-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="98616-149">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="98616-149">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="98616-150">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="98616-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1530
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a176c585-b5de-4d65-824c-67a6deb45cd9
MS-RequestId: 74ca1db9-df92-41c6-a362-a16433b0542b

{
  "id": "eebd1b55-5360-4438-a11d-5c06918c3014",
  "commerceId": "99e6a635-48e7-424d-9059-c9db944e3c54",
  "companyProfile": {
    "tenantId": "eebd1b55-5360-4438-a11d-5c06918c3014",
    "domain": "abcdefgh1234.ccsctp.net",
    "companyName": "1kl as kjk",
    "address": {
      "country": "US",
      "region": "wa",
      "city": "redmond",
      "addressLine1": "1 ms way",
      "postalCode": "98052",
      "phoneNumber": "1234567890"
    },
    "email": "a@a.com",
    "links": {
      "self": {
        "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/profiles/company",
        "method": "GET",
        "headers": []
      }
    },
    "attributes": {
      "objectType": "CustomerCompanyProfile"
    }
  },
  "billingProfile": {
    "id": "eeada110-69d6-4cc9-b093-75feb7ca9d3f",
    "firstName": "d0d89d776d03471c819bf772191ed728",
    "lastName": "kjkAJJAAAAAAAAAAAAAAAAAAAA",
    "email": "a@a.com",
    "culture": "en-US",
    "language": "en",
    "companyName": "1kl as kjkAAAAAAAAAAAAAAAJJJJJJJJJJJAAAAAJJJJJJJJJJJAAJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJAJJJJJAJJAAAAJAJJAAAAAAAAAAAAAAAAAAAA",
    "defaultAddress": {
      "country": "US",
      "city": "redmond",
      "state": "WA",
      "addressLine1": "1 ms way",
      "postalCode": "98052",
      "firstName": "1kl as",
      "lastName": "kjk",
      "phoneNumber": "1234567890"
    },
    "links": {
      "self": {
        "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/profiles/billing",
        "method": "GET",
        "headers": [

        ]
      }
    },
    "attributes": {
      "etag": "-4242348048554929329",
      "objectType": "CustomerBillingProfile"
    }
  },
  "relationshipToPartner": "reseller",
  "allowDelegatedAccess": true,
  "customDomains": [
    "abcdefgh1234.ccsctp.net"
  ],
  "links": {
    "self": {
      "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Customer"
  }
}
```
