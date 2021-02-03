---
title: Obter uma lista de políticas de um cliente
description: Como recuperar uma coleção das políticas de configuração do cliente especificado.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 16886b1adca393ed2967f2a4fe74a379bef1c1c7
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769338"
---
# <a name="get-a-list-of-a-customers-policies"></a><span data-ttu-id="4200a-103">Obter uma lista de políticas de um cliente</span><span class="sxs-lookup"><span data-stu-id="4200a-103">Get a list of a customer's policies</span></span>

<span data-ttu-id="4200a-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="4200a-104">**Applies to:**</span></span>

- <span data-ttu-id="4200a-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="4200a-105">Partner Center</span></span>
- <span data-ttu-id="4200a-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="4200a-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="4200a-107">Este artigo descreve como recuperar uma coleção das políticas de configuração do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="4200a-107">This article describes how to retrieve a collection of the specified customer's configuration policies.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4200a-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4200a-108">Prerequisites</span></span>

- <span data-ttu-id="4200a-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4200a-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4200a-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="4200a-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="4200a-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4200a-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4200a-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="4200a-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4200a-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="4200a-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4200a-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="4200a-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4200a-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="4200a-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4200a-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4200a-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="4200a-117">C\#</span><span class="sxs-lookup"><span data-stu-id="4200a-117">C\#</span></span>

<span data-ttu-id="4200a-118">Para obter uma lista de todas as políticas de um cliente:</span><span class="sxs-lookup"><span data-stu-id="4200a-118">To get a list of all of a customer's policies:</span></span>

1. <span data-ttu-id="4200a-119">Ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="4200a-119">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="4200a-120">Recupere a propriedade [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) para obter uma interface para configurar operações de recolha de políticas.</span><span class="sxs-lookup"><span data-stu-id="4200a-120">Retrieve the [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) property to get an interface to configuration policy collection operations.</span></span>
3. <span data-ttu-id="4200a-121">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.getasync) para recuperar a recolha de políticas.</span><span class="sxs-lookup"><span data-stu-id="4200a-121">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.getasync) method to retrieve the collection of policies.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;

var configPolicies = partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.Get();
```

<span data-ttu-id="4200a-122">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4200a-122">For an example, see the following:</span></span>

- <span data-ttu-id="4200a-123">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="4200a-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="4200a-124">Projeto: **Partner Center SDK Samples**</span><span class="sxs-lookup"><span data-stu-id="4200a-124">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="4200a-125">Classe: **GetAllConfigurationPolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="4200a-125">Class: **GetAllConfigurationPolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="4200a-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="4200a-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4200a-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="4200a-127">Request syntax</span></span>

| <span data-ttu-id="4200a-128">Método</span><span class="sxs-lookup"><span data-stu-id="4200a-128">Method</span></span>  | <span data-ttu-id="4200a-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="4200a-129">Request URI</span></span>                                                                              |
|---------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="4200a-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="4200a-130">**GET**</span></span> | <span data-ttu-id="4200a-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/policies HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4200a-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="4200a-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="4200a-132">URI parameter</span></span>

<span data-ttu-id="4200a-133">Utilize o seguinte parâmetro de caminho ao criar o pedido:</span><span class="sxs-lookup"><span data-stu-id="4200a-133">Use the following path parameter when creating the request:</span></span>

| <span data-ttu-id="4200a-134">Nome</span><span class="sxs-lookup"><span data-stu-id="4200a-134">Name</span></span>        | <span data-ttu-id="4200a-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="4200a-135">Type</span></span>   | <span data-ttu-id="4200a-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="4200a-136">Required</span></span> | <span data-ttu-id="4200a-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="4200a-137">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="4200a-138">id cliente</span><span class="sxs-lookup"><span data-stu-id="4200a-138">customer-id</span></span> | <span data-ttu-id="4200a-139">string</span><span class="sxs-lookup"><span data-stu-id="4200a-139">string</span></span> | <span data-ttu-id="4200a-140">Sim</span><span class="sxs-lookup"><span data-stu-id="4200a-140">Yes</span></span>      | <span data-ttu-id="4200a-141">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="4200a-141">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4200a-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="4200a-142">Request headers</span></span>

<span data-ttu-id="4200a-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4200a-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4200a-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="4200a-144">Request body</span></span>

<span data-ttu-id="4200a-145">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4200a-145">None</span></span>

### <a name="request-example"></a><span data-ttu-id="4200a-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="4200a-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
Content-Length:0
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="4200a-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="4200a-147">REST response</span></span>

<span data-ttu-id="4200a-148">Se for bem sucedido, o corpo de resposta contém a recolha de recursos [configurationPolicy.](device-deployment-resources.md#configurationpolicy)</span><span class="sxs-lookup"><span data-stu-id="4200a-148">If successful, the response body contains the collection of [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4200a-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="4200a-149">Response success and error codes</span></span>

<span data-ttu-id="4200a-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="4200a-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4200a-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4200a-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4200a-152">Para obter uma lista completa, consulte [os códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4200a-152">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4200a-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="4200a-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1221
Content-Type: application/json; charset=utf-8
MS-CorrelationId: d5ff2573-3ef8-4553-aac4-4b73d97dce1b
MS-RequestId: 6eb7383d-eeb5-44d7-8570-e0ed12c0547a
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:07:49 GMT

{
    "totalCount": 3,
    "items": [{
            "id": "8c7d25aa-2dbb-409c-a1f0-f55bd9108fa9",
            "name": "Windows 10 Enterprise E3",
            "category": "o_o_b_e",
            "description": "P462017 description",
            "devicesAssigned": 0,
            "policySettings": ["oobe_user_not_local_admin", "skip_express_settings"],
            "createdDate": "2017-04-27T11:30:34.1944704-07:00",
            "lastModifiedDate": "2017-04-27T11:30:34.1944704-07:00",
            "attributes": {
                "objectType": "ConfigurationPolicy"
            }
        }, {
            "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
            "name": "Test policy",
            "category": "o_o_b_e",
            "description": "Test policy creation from API 1",
            "devicesAssigned": 0,
            "policySettings": ["skip_express_settings"],
            "createdDate": "2017-07-25T11:03:03.8457088-07:00",
            "lastModifiedDate": "2017-07-25T11:04:00.8150016-07:00",
            "attributes": {
                "objectType": "ConfigurationPolicy"
            }
        }, {
            "id": "a96b5fd9-0f3a-419a-b55c-a8aecd6b1f00",
            "name": "Windows 10 Enterprise E5",
            "category": "o_o_b_e",
            "description": "test policy creation from API",
            "devicesAssigned": 0,
            "policySettings": ["oobe_user_not_local_admin", "skip_express_settings"],
            "createdDate": "2017-07-25T11:07:36.1501184-07:00",
            "lastModifiedDate": "2017-07-25T11:07:36.1501184-07:00",
            "attributes": {
                "objectType": "ConfigurationPolicy"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
