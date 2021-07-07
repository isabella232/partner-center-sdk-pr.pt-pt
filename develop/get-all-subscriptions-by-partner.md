---
title: Obter as subscrições de um cliente por ID do MPN do parceiro
description: Como obter uma lista de subscrições fornecidas por um determinado parceiro a um cliente especificado.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 857caa667245503f111b27379a5c8f93aa1fb0b0
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760662"
---
# <a name="get-a-customers-subscriptions-by-partner-mpn-id"></a><span data-ttu-id="f0c1d-103">Obter as subscrições de um cliente por ID do MPN do parceiro</span><span class="sxs-lookup"><span data-stu-id="f0c1d-103">Get a customer's subscriptions by partner MPN ID</span></span>

<span data-ttu-id="f0c1d-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="f0c1d-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="f0c1d-105">Como obter uma lista de subscrições fornecidas por um determinado parceiro da Microsoft Partner Network (MPN) a um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-105">How to get a list of subscriptions provided by a given Microsoft Partner Network (MPN) partner to a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f0c1d-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f0c1d-106">Prerequisites</span></span>

- <span data-ttu-id="f0c1d-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f0c1d-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f0c1d-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="f0c1d-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f0c1d-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f0c1d-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f0c1d-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f0c1d-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="f0c1d-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f0c1d-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="f0c1d-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f0c1d-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f0c1d-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f0c1d-115">Um identificador mpn parceiro.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-115">A partner MPN identifier.</span></span>

## <a name="c"></a><span data-ttu-id="f0c1d-116">C\#</span><span class="sxs-lookup"><span data-stu-id="f0c1d-116">C\#</span></span>

<span data-ttu-id="f0c1d-117">Para obter uma lista de subscrições fornecidas por um determinado parceiro a um cliente especificado, utilize primeiro o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-117">To get a list of subscriptions provided by a given partner to a specified customer, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="f0c1d-118">Em seguida, obtenha uma interface para as operações de recolha de subscrição de clientes a partir da propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) e ligue para o método [**ByPartner**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.bypartner) com o MPN ID para identificar o parceiro e recuperar uma interface para operações de subscrição de parceiros.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-118">Then get an interface to customer subscription collection operations from the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, and call the [**ByPartner**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.bypartner) method with the MPN ID to identify the partner and retrieve an interface to partner subscription operations.</span></span> <span data-ttu-id="f0c1d-119">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync) para obter a coleção.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-119">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync) method to get the collection.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string partnerMpnId;

var customerSubscriptionsByMpnId = partnerOperations.Customers.ById(customerId).Subscriptions.ByPartner(partnerMpnId).Get();
```

<span data-ttu-id="f0c1d-120">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="f0c1d-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="f0c1d-121">**Project**: Partner Center SDK Samples **Class**: GetSubscriptionsByMpnid.cs</span><span class="sxs-lookup"><span data-stu-id="f0c1d-121">**Project**: Partner Center SDK Samples **Class**: GetSubscriptionsByMpnid.cs</span></span>

## <a name="java"></a><span data-ttu-id="f0c1d-122">Java</span><span class="sxs-lookup"><span data-stu-id="f0c1d-122">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="f0c1d-123">Para obter uma lista de subscrições fornecidas por um determinado parceiro a um cliente especificado, utilize primeiro a função **IAggregatePartner.getCustomers.byId** com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-123">To get a list of subscriptions provided by a given partner to a specified customer, first use the **IAggregatePartner.getCustomers.byId** function with the customer ID to identify the customer.</span></span> <span data-ttu-id="f0c1d-124">Em seguida, obtenha uma interface para as operações de recolha de subscrição de clientes a partir da função **getSubscriptions,** e ligue para a função **byPartner** com o MPN ID para identificar o parceiro e recuperar uma interface para operações de subscrição de parceiros.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-124">Then get an interface to customer subscription collection operations from the **getSubscriptions** function, and call the **byPartner** function with the MPN ID to identify the partner and retrieve an interface to partner subscription operations.</span></span> <span data-ttu-id="f0c1d-125">Finalmente, ligue para a função **get** para obter a coleção.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-125">Finally, call the **get** function to get the collection.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String partnerMpnId;

ResourceCollection<Subscription> customerSubscriptionsByMpnId = partnerOperations.getCustomers().byId(customerId).getSubscriptions().byPartner(partnerMpnId).get();
```

## <a name="powershell"></a><span data-ttu-id="f0c1d-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0c1d-126">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="f0c1d-127">Para obter uma lista de subscrições fornecidas por um determinado parceiro a um cliente especificado, execute o comando [**Get-PartnerCustomerSubscription.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscription.md)</span><span class="sxs-lookup"><span data-stu-id="f0c1d-127">To get a list of subscriptions provided by a given partner to a specified customer, execute the [**Get-PartnerCustomerSubscription**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscription.md) command.</span></span> <span data-ttu-id="f0c1d-128">Especifique o ID do cliente para identificar o cliente utilizando o parâmetro **CustomerId** e povoe o parâmetro **MpnId** com o ID MPN para identificar o parceiro.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-128">Specify the customer ID to identify the customer using the **CustomerId** parameter, and populate the **MpnId** parameter with the MPN ID to identify the partner.</span></span>

```powershell
# $customerId
# $partnerMpnId

Get-PartnerCustomerSubscription -CustomerId $customerId -MpnId $partnerMpnId
```

## <a name="rest-request"></a><span data-ttu-id="f0c1d-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f0c1d-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f0c1d-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0c1d-130">Request syntax</span></span>

| <span data-ttu-id="f0c1d-131">Método</span><span class="sxs-lookup"><span data-stu-id="f0c1d-131">Method</span></span>  | <span data-ttu-id="f0c1d-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f0c1d-132">Request URI</span></span> |
|---------|----------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f0c1d-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="f0c1d-133">**GET**</span></span> | <span data-ttu-id="f0c1d-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscrições?mpn \_ id={mpn-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f0c1d-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions?mpn\_id={mpn-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="f0c1d-135">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="f0c1d-135">URI parameters</span></span>

<span data-ttu-id="f0c1d-136">Utilize os seguintes parâmetros de percurso e consulta para identificar o cliente e o parceiro.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-136">Use the following path and query parameters to identify the customer and partner.</span></span>

| <span data-ttu-id="f0c1d-137">Nome</span><span class="sxs-lookup"><span data-stu-id="f0c1d-137">Name</span></span>        | <span data-ttu-id="f0c1d-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="f0c1d-138">Type</span></span>   | <span data-ttu-id="f0c1d-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="f0c1d-139">Required</span></span> | <span data-ttu-id="f0c1d-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0c1d-140">Description</span></span>                                                 |
|-------------|--------|----------|-------------------------------------------------------------|
| <span data-ttu-id="f0c1d-141">id cliente</span><span class="sxs-lookup"><span data-stu-id="f0c1d-141">customer-id</span></span> | <span data-ttu-id="f0c1d-142">string</span><span class="sxs-lookup"><span data-stu-id="f0c1d-142">string</span></span> | <span data-ttu-id="f0c1d-143">Yes</span><span class="sxs-lookup"><span data-stu-id="f0c1d-143">Yes</span></span>      | <span data-ttu-id="f0c1d-144">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-144">A GUID formatted string that identifies the customer.</span></span>       |
| <span data-ttu-id="f0c1d-145">mpn-id</span><span class="sxs-lookup"><span data-stu-id="f0c1d-145">mpn-id</span></span>      | <span data-ttu-id="f0c1d-146">int</span><span class="sxs-lookup"><span data-stu-id="f0c1d-146">int</span></span>    | <span data-ttu-id="f0c1d-147">Yes</span><span class="sxs-lookup"><span data-stu-id="f0c1d-147">Yes</span></span>      | <span data-ttu-id="f0c1d-148">Um ID da Rede de Parceiros da Microsoft que identifica o parceiro.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-148">A Microsoft Partner Network ID that identifies the partner.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f0c1d-149">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="f0c1d-149">Request headers</span></span>

<span data-ttu-id="f0c1d-150">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f0c1d-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f0c1d-151">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f0c1d-151">Request body</span></span>

<span data-ttu-id="f0c1d-152">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f0c1d-153">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f0c1d-153">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/subscriptions?mpn_id=4847383 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="f0c1d-154">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f0c1d-154">REST response</span></span>

<span data-ttu-id="f0c1d-155">Se for bem sucedido, o organismo de resposta contém a recolha de recursos de [Subscrição.](subscription-resources.md)</span><span class="sxs-lookup"><span data-stu-id="f0c1d-155">If successful, the response body contains the collection of [Subscription](subscription-resources.md) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f0c1d-156">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f0c1d-156">Response success and error codes</span></span>

<span data-ttu-id="f0c1d-157">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f0c1d-158">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f0c1d-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f0c1d-159">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f0c1d-159">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f0c1d-160">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f0c1d-160">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 985
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CV: LdFhumtx6Ea0Kl5Z.0
MS-ServerId: 101112202
Date: Thu, 13 Apr 2017 20:58:08 GMT

{
    "totalCount": 1,
    "items": [{
            "id": "42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
            "offerId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "offerName": "Intune Device",
            "friendlyName": "new offer purchase",
            "quantity": 5,
            "unitType": "Licenses",
            "creationDate": "2017-04-10T23:02:26.02Z",
            "effectiveStartDate": "2017-04-10T00:00:00Z",
            "commitmentEndDate": "2018-05-07T00:00:00Z",
            "status": "active",
            "autoRenewEnabled": true,
            "isTrial": false,
            "billingType": "license",
            "billingCycle": "monthly",
            "partnerId": "4847383",
            "contractType": "subscription",
            "links": {
                "offer": {
                    "uri": "/offers/DB2E705F-B82A-4024-A3D5-D88E12F2DB35?country=US",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/subscriptions/42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
                    "method": "GET",
                    "headers": []
                }
            },
            "orderId": "3EDDCAC6-63B2-4C40-B0B6-F47E18301492",
            "attributes": {
                "etag": "eyJpZCI6IjQyMjI2ZWQ2LTA3MGEtNGUwZi1iODBjLTRjZGZiM2U5N2FhNyIsInZlcnNpb24iOjF9",
                "objectType": "Subscription"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="see-also"></a><span data-ttu-id="f0c1d-161">Ver também</span><span class="sxs-lookup"><span data-stu-id="f0c1d-161">See also</span></span>

- [<span data-ttu-id="f0c1d-162">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="f0c1d-162">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
