---
title: Obter as subscrições de um cliente por ID do MPN do parceiro
description: Como obter uma lista de subscrições fornecidas por um determinado parceiro a um cliente especificado.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: c95488b62449e1ab6bd2eeefea58d6686c291f4c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769710"
---
# <a name="get-a-customers-subscriptions-by-partner-mpn-id"></a><span data-ttu-id="17e10-103">Obter as subscrições de um cliente por ID do MPN do parceiro</span><span class="sxs-lookup"><span data-stu-id="17e10-103">Get a customer's subscriptions by partner MPN ID</span></span>

<span data-ttu-id="17e10-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="17e10-104">**Applies To**</span></span>

- <span data-ttu-id="17e10-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="17e10-105">Partner Center</span></span>
- <span data-ttu-id="17e10-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="17e10-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="17e10-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="17e10-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="17e10-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="17e10-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="17e10-109">Como obter uma lista de subscrições fornecidas por um determinado parceiro a um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="17e10-109">How to get a list of subscriptions provided by a given partner to a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="17e10-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="17e10-110">Prerequisites</span></span>

- <span data-ttu-id="17e10-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="17e10-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="17e10-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="17e10-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="17e10-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="17e10-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="17e10-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="17e10-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="17e10-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="17e10-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="17e10-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="17e10-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="17e10-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="17e10-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="17e10-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="17e10-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="17e10-119">Um identificador parceiro da Microsoft Partner Network (MPN).</span><span class="sxs-lookup"><span data-stu-id="17e10-119">A partner Microsoft Partner Network (MPN) identifier.</span></span>

## <a name="c"></a><span data-ttu-id="17e10-120">C\#</span><span class="sxs-lookup"><span data-stu-id="17e10-120">C\#</span></span>

<span data-ttu-id="17e10-121">Para obter uma lista de subscrições fornecidas por um determinado parceiro a um cliente especificado, utilize primeiro o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="17e10-121">To get a list of subscriptions provided by a given partner to a specified customer, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="17e10-122">Em seguida, obtenha uma interface para as operações de recolha de subscrição de clientes a partir da propriedade [**Subscrições,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) e ligue para o método [**ByPartner**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.bypartner) com o MPN ID para identificar o parceiro e recuperar uma interface para operações de subscrição de parceiros.</span><span class="sxs-lookup"><span data-stu-id="17e10-122">Then get an interface to customer subscription collection operations from the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, and call the [**ByPartner**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.bypartner) method with the MPN ID to identify the partner and retrieve an interface to partner subscription operations.</span></span> <span data-ttu-id="17e10-123">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync) para obter a coleção.</span><span class="sxs-lookup"><span data-stu-id="17e10-123">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync) method to get the collection.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string partnerMpnId;

var customerSubscriptionsByMpnId = partnerOperations.Customers.ById(customerId).Subscriptions.ByPartner(partnerMpnId).Get();
```

<span data-ttu-id="17e10-124">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="17e10-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="17e10-125">**Projeto**: Partner Center SDK Samples **Class**: GetSubscriptionsByMpnid.cs</span><span class="sxs-lookup"><span data-stu-id="17e10-125">**Project**: Partner Center SDK Samples **Class**: GetSubscriptionsByMpnid.cs</span></span>

## <a name="java"></a><span data-ttu-id="17e10-126">Java</span><span class="sxs-lookup"><span data-stu-id="17e10-126">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="17e10-127">Para obter uma lista de subscrições fornecidas por um determinado parceiro a um cliente especificado, utilize primeiro a função **IAggregatePartner.getCustomers.byId** com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="17e10-127">To get a list of subscriptions provided by a given partner to a specified customer, first use the **IAggregatePartner.getCustomers.byId** function with the customer ID to identify the customer.</span></span> <span data-ttu-id="17e10-128">Em seguida, obtenha uma interface para as operações de recolha de subscrição de clientes a partir da função **getSubscriptions,** e ligue para a função **byPartner** com o MPN ID para identificar o parceiro e recuperar uma interface para operações de subscrição de parceiros.</span><span class="sxs-lookup"><span data-stu-id="17e10-128">Then get an interface to customer subscription collection operations from the **getSubscriptions** function, and call the **byPartner** function with the MPN ID to identify the partner and retrieve an interface to partner subscription operations.</span></span> <span data-ttu-id="17e10-129">Finalmente, ligue para a função **get** para obter a coleção.</span><span class="sxs-lookup"><span data-stu-id="17e10-129">Finally, call the **get** function to get the collection.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String partnerMpnId;

ResourceCollection<Subscription> customerSubscriptionsByMpnId = partnerOperations.getCustomers().byId(customerId).getSubscriptions().byPartner(partnerMpnId).get();
```

## <a name="powershell"></a><span data-ttu-id="17e10-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="17e10-130">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="17e10-131">Para obter uma lista de subscrições fornecidas por um determinado parceiro a um cliente especificado, execute o comando [**Get-PartnerCustomerSubscription.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscription.md)</span><span class="sxs-lookup"><span data-stu-id="17e10-131">To get a list of subscriptions provided by a given partner to a specified customer, execute the [**Get-PartnerCustomerSubscription**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscription.md) command.</span></span> <span data-ttu-id="17e10-132">Especifique o ID do cliente para identificar o cliente utilizando o parâmetro **CustomerId** e povoe o parâmetro **MpnId** com o ID MPN para identificar o parceiro.</span><span class="sxs-lookup"><span data-stu-id="17e10-132">Specify the customer ID to identify the customer using the **CustomerId** parameter, and populate the **MpnId** parameter with the MPN ID to identify the partner.</span></span>

```powershell
# $customerId
# $partnerMpnId

Get-PartnerCustomerSubscription -CustomerId $customerId -MpnId $partnerMpnId
```

## <a name="rest-request"></a><span data-ttu-id="17e10-133">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="17e10-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="17e10-134">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="17e10-134">Request syntax</span></span>

| <span data-ttu-id="17e10-135">Método</span><span class="sxs-lookup"><span data-stu-id="17e10-135">Method</span></span>  | <span data-ttu-id="17e10-136">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="17e10-136">Request URI</span></span> |
|---------|----------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="17e10-137">**Obter**</span><span class="sxs-lookup"><span data-stu-id="17e10-137">**GET**</span></span> | <span data-ttu-id="17e10-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscrições?mpn \_ id={mpn-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="17e10-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions?mpn\_id={mpn-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="17e10-139">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="17e10-139">URI parameters</span></span>

<span data-ttu-id="17e10-140">Utilize os seguintes parâmetros de percurso e consulta para identificar o cliente e o parceiro.</span><span class="sxs-lookup"><span data-stu-id="17e10-140">Use the following path and query parameters to identify the customer and partner.</span></span>

| <span data-ttu-id="17e10-141">Nome</span><span class="sxs-lookup"><span data-stu-id="17e10-141">Name</span></span>        | <span data-ttu-id="17e10-142">Tipo</span><span class="sxs-lookup"><span data-stu-id="17e10-142">Type</span></span>   | <span data-ttu-id="17e10-143">Necessário</span><span class="sxs-lookup"><span data-stu-id="17e10-143">Required</span></span> | <span data-ttu-id="17e10-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="17e10-144">Description</span></span>                                                 |
|-------------|--------|----------|-------------------------------------------------------------|
| <span data-ttu-id="17e10-145">id cliente</span><span class="sxs-lookup"><span data-stu-id="17e10-145">customer-id</span></span> | <span data-ttu-id="17e10-146">string</span><span class="sxs-lookup"><span data-stu-id="17e10-146">string</span></span> | <span data-ttu-id="17e10-147">Sim</span><span class="sxs-lookup"><span data-stu-id="17e10-147">Yes</span></span>      | <span data-ttu-id="17e10-148">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="17e10-148">A GUID formatted string that identifies the customer.</span></span>       |
| <span data-ttu-id="17e10-149">mpn-id</span><span class="sxs-lookup"><span data-stu-id="17e10-149">mpn-id</span></span>      | <span data-ttu-id="17e10-150">int</span><span class="sxs-lookup"><span data-stu-id="17e10-150">int</span></span>    | <span data-ttu-id="17e10-151">Sim</span><span class="sxs-lookup"><span data-stu-id="17e10-151">Yes</span></span>      | <span data-ttu-id="17e10-152">Um ID da Rede de Parceiros da Microsoft que identifica o parceiro.</span><span class="sxs-lookup"><span data-stu-id="17e10-152">A Microsoft Partner Network ID that identifies the partner.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="17e10-153">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="17e10-153">Request headers</span></span>

<span data-ttu-id="17e10-154">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="17e10-154">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="17e10-155">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="17e10-155">Request body</span></span>

<span data-ttu-id="17e10-156">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="17e10-156">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="17e10-157">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="17e10-157">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="17e10-158">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="17e10-158">REST response</span></span>

<span data-ttu-id="17e10-159">Se for bem sucedido, o organismo de resposta contém a recolha de recursos de [Subscrição.](subscription-resources.md)</span><span class="sxs-lookup"><span data-stu-id="17e10-159">If successful, the response body contains the collection of [Subscription](subscription-resources.md) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="17e10-160">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="17e10-160">Response success and error codes</span></span>

<span data-ttu-id="17e10-161">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="17e10-161">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="17e10-162">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="17e10-162">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="17e10-163">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="17e10-163">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="17e10-164">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="17e10-164">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="17e10-165">Ver também</span><span class="sxs-lookup"><span data-stu-id="17e10-165">See also</span></span>

- [<span data-ttu-id="17e10-166">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="17e10-166">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
