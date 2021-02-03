---
title: Obter uma lista de licenças disponíveis
description: Como obter uma lista de licenças disponíveis para os utilizadores do cliente especificado.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: f675e5b96b2f2040d662c0dc7f1e06625f267689
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769547"
---
# <a name="get-a-list-of-available-licenses"></a><span data-ttu-id="f3854-103">Obter uma lista de licenças disponíveis</span><span class="sxs-lookup"><span data-stu-id="f3854-103">Get a list of available licenses</span></span>

<span data-ttu-id="f3854-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="f3854-104">**Applies to:**</span></span>

- <span data-ttu-id="f3854-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="f3854-105">Partner Center</span></span>

<span data-ttu-id="f3854-106">Este artigo descreve como obter uma lista de licenças disponíveis para os utilizadores do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="f3854-106">This article describes how to get a list of licenses available to users of the specified customer.</span></span>

<span data-ttu-id="f3854-107">Os seguintes exemplos devolvem licenças disponíveis do **grupo1,** o grupo de licenças padrão que representa licenças geridas pela Azure Ative Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="f3854-107">The following examples return licenses available from **group1**, the default license group that represents licenses managed by Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="f3854-108">Para obter licenças disponíveis para um grupo de licenças especificado, consulte [obter uma lista de licenças disponíveis por grupo de licenças.](get-a-list-of-available-licenses-by-license-group.md)</span><span class="sxs-lookup"><span data-stu-id="f3854-108">To get available licenses for a specified license group, see [Get a list of available licenses by license group](get-a-list-of-available-licenses-by-license-group.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f3854-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f3854-109">Prerequisites</span></span>

- <span data-ttu-id="f3854-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f3854-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f3854-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="f3854-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="f3854-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f3854-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f3854-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="f3854-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f3854-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="f3854-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f3854-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="f3854-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f3854-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="f3854-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f3854-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f3854-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="f3854-118">C\#</span><span class="sxs-lookup"><span data-stu-id="f3854-118">C\#</span></span>

<span data-ttu-id="f3854-119">Para recuperar a lista de licenças disponíveis do grupo de licenças predefinidos para utilizadores de um cliente:</span><span class="sxs-lookup"><span data-stu-id="f3854-119">To retrieve the list of licenses available from the default license group to users of a customer:</span></span>

1. <span data-ttu-id="f3854-120">Utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f3854-120">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="f3854-121">Obtenha o valor da propriedade [**SubscritaSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) para recuperar uma interface para as operações de recolha SKU subscritas pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="f3854-121">Get the value of the [**SubscribedSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) property to retrieve an interface to customer subscribed SKU collection operations.</span></span>

3. <span data-ttu-id="f3854-122">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) para recuperar a lista de licenças.</span><span class="sxs-lookup"><span data-stu-id="f3854-122">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to retrieve the list of licenses.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var customerUserSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
```

<span data-ttu-id="f3854-123">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f3854-123">For an example, see the following:</span></span>

- <span data-ttu-id="f3854-124">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="f3854-124">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="f3854-125">Projeto: **Partner Center SDK Samples**</span><span class="sxs-lookup"><span data-stu-id="f3854-125">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="f3854-126">Classe: **GetCustomerSubscribedSkus.cs**</span><span class="sxs-lookup"><span data-stu-id="f3854-126">Class: **GetCustomerSubscribedSkus.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="f3854-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="f3854-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f3854-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3854-128">Request syntax</span></span>

| <span data-ttu-id="f3854-129">Método</span><span class="sxs-lookup"><span data-stu-id="f3854-129">Method</span></span>  | <span data-ttu-id="f3854-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="f3854-130">Request URI</span></span>                                                                                    |
|---------|------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f3854-131">**Obter**</span><span class="sxs-lookup"><span data-stu-id="f3854-131">**GET**</span></span> | <span data-ttu-id="f3854-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subsskus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f3854-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="f3854-133">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="f3854-133">URI parameter</span></span>

<span data-ttu-id="f3854-134">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="f3854-134">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="f3854-135">Nome</span><span class="sxs-lookup"><span data-stu-id="f3854-135">Name</span></span>        | <span data-ttu-id="f3854-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="f3854-136">Type</span></span>   | <span data-ttu-id="f3854-137">Necessário</span><span class="sxs-lookup"><span data-stu-id="f3854-137">Required</span></span> | <span data-ttu-id="f3854-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3854-138">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="f3854-139">id cliente</span><span class="sxs-lookup"><span data-stu-id="f3854-139">customer-id</span></span> | <span data-ttu-id="f3854-140">string</span><span class="sxs-lookup"><span data-stu-id="f3854-140">string</span></span> | <span data-ttu-id="f3854-141">Sim</span><span class="sxs-lookup"><span data-stu-id="f3854-141">Yes</span></span>      | <span data-ttu-id="f3854-142">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="f3854-142">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f3854-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="f3854-143">Request headers</span></span>

<span data-ttu-id="f3854-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f3854-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f3854-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="f3854-145">Request body</span></span>

<span data-ttu-id="f3854-146">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f3854-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f3854-147">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="f3854-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscribedskus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 53308f82-1bf7-44e2-8dda-4517e4688bd4
MS-CorrelationId: 95660db2-7425-4021-babe-a26ddbcb0187
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="f3854-148">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="f3854-148">REST response</span></span>

<span data-ttu-id="f3854-149">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [SubscrevidosSku.](license-resources.md#subscribedsku)</span><span class="sxs-lookup"><span data-stu-id="f3854-149">If successful, the response body contains a collection of [SubscribedSku](license-resources.md#subscribedsku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f3854-150">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="f3854-150">Response success and error codes</span></span>

<span data-ttu-id="f3854-151">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="f3854-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f3854-152">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="f3854-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f3854-153">Para obter uma lista completa, consulte [os códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f3854-153">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f3854-154">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="f3854-154">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 4859
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 95660db2-7425-4021-babe-a26ddbcb0187
MS-RequestId: 53308f82-1bf7-44e2-8dda-4517e4688bd4
MS-CV: 7BQ0jitzXUCLwRM6.0
MS-ServerId: 020021921
Date: Fri, 09 Jun 2017 17:50:46 GMT

 {
    "totalCount": 2,
    "items": [{
            "availableUnits": 4,
            "activeUnits": 5,
            "consumedUnits": 1,
            "suspendedUnits": 0,
            "totalUnits": 5,
            "warningUnits": 0,
            "productSku": {
                "id": "efccb6f7-5641-4e0e-bd10-b4976e1bf68e",
                "name": "Enterprise Mobility + Security E3",
                "skuPartNumber": "EMS",
                "targetType": "User",
                "licenseGroupId": "group1"
            },
            "servicePlans": [{
                    "displayName": "Azure Information Protection Premium P1",
                    "serviceName": "RMS_S_PREMIUM",
                    "id": "6c57d4b6-3b23-47a5-9bc9-69f17b4947b3",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Intune A Direct",
                    "serviceName": "INTUNE_A",
                    "id": "c1ec4a95-1f05-45b3-a911-aa3fa01094f5",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Azure Active Directory Rights",
                    "serviceName": "RMS_S_ENTERPRISE",
                    "id": "bea4c11e-220a-4e6d-8eb8-8ea15d019f90",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Azure Active Directory Premium P1",
                    "serviceName": "AAD_PREMIUM",
                    "id": "41781fb2-bc02-4b7c-bd55-b576c07bb09d",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Azure Multi-Factor Authentication",
                    "serviceName": "MFA_PREMIUM",
                    "id": "8a256a2b-b617-496d-b51b-e76466e88db0",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }
            ],
            "capabilityStatus": "Enabled",
            "attributes": {
                "objectType": "SubscribedSku"
            }
        },  {
            "availableUnits": 0,
            "activeUnits": 1,
            "consumedUnits": 1,
            "suspendedUnits": 0,
            "totalUnits": 1,
            "warningUnits": 0,
            "productSku": {
                "id": "f8a1db68-be16-40ed-86d5-cb42ce701560",
                "name": "Power BI Pro",
                "skuPartNumber": "POWER_BI_PRO",
                "targetType": "User",
                "licenseGroupId": "group1"
            },
            "servicePlans": [{
                    "displayName": "Exchange Foundation",
                    "serviceName": "EXCHANGE_S_FOUNDATION",
                    "id": "113feb6c-3fe4-4440-bddc-54d774bf0318",
                    "capabilityStatus": "Enabled",
                    "targetType": "Tenant"
                }, {
                    "displayName": "Power BI Pro",
                    "serviceName": "BI_AZURE_P2",
                    "id": "70d33638-9c74-4d01-bfd3-562de28bd4ba",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }
            ],
            "capabilityStatus": "Enabled",
            "attributes": {
                "objectType": "SubscribedSku"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
