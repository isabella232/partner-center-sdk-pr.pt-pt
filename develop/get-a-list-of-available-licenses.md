---
title: Obter uma lista de licenças disponíveis
description: Como obter uma lista de licenças disponíveis para os utilizadores do cliente especificado.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 02a6fccc2cf7f3f4dc929b96ec0f17e0f4a31b06
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874504"
---
# <a name="get-a-list-of-available-licenses"></a><span data-ttu-id="6b1dd-103">Obter uma lista de licenças disponíveis</span><span class="sxs-lookup"><span data-stu-id="6b1dd-103">Get a list of available licenses</span></span>

<span data-ttu-id="6b1dd-104">Este artigo descreve como obter uma lista de licenças disponíveis para os utilizadores do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-104">This article describes how to get a list of licenses available to users of the specified customer.</span></span>

<span data-ttu-id="6b1dd-105">Os exemplos seguintes devolvem licenças disponíveis do **grupo1,** o grupo de licenças padrão que representa licenças geridas por Azure Ative Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="6b1dd-105">The following examples return licenses available from **group1**, the default license group that represents licenses managed by Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="6b1dd-106">Para obter licenças disponíveis para um grupo de licenças especificado, consulte [obter uma lista de licenças disponíveis por grupo de licenças.](get-a-list-of-available-licenses-by-license-group.md)</span><span class="sxs-lookup"><span data-stu-id="6b1dd-106">To get available licenses for a specified license group, see [Get a list of available licenses by license group](get-a-list-of-available-licenses-by-license-group.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b1dd-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6b1dd-107">Prerequisites</span></span>

- <span data-ttu-id="6b1dd-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6b1dd-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6b1dd-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="6b1dd-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6b1dd-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6b1dd-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6b1dd-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6b1dd-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="6b1dd-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6b1dd-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="6b1dd-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6b1dd-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6b1dd-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="6b1dd-116">C\#</span><span class="sxs-lookup"><span data-stu-id="6b1dd-116">C\#</span></span>

<span data-ttu-id="6b1dd-117">Para recuperar a lista de licenças disponíveis do grupo de licenças predefinidos para utilizadores de um cliente:</span><span class="sxs-lookup"><span data-stu-id="6b1dd-117">To retrieve the list of licenses available from the default license group to users of a customer:</span></span>

1. <span data-ttu-id="6b1dd-118">Utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-118">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="6b1dd-119">Obtenha o valor da propriedade [**SubscritaSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) para recuperar uma interface para as operações de recolha SKU subscritas pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-119">Get the value of the [**SubscribedSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) property to retrieve an interface to customer subscribed SKU collection operations.</span></span>

3. <span data-ttu-id="6b1dd-120">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) para recuperar a lista de licenças.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-120">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to retrieve the list of licenses.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var customerUserSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
```

<span data-ttu-id="6b1dd-121">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6b1dd-121">For an example, see the following:</span></span>

- <span data-ttu-id="6b1dd-122">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="6b1dd-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="6b1dd-123">Project: **Amostras SDK do Centro Parceiro**</span><span class="sxs-lookup"><span data-stu-id="6b1dd-123">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="6b1dd-124">Classe: **GetCustomerSubsubskus.cs**</span><span class="sxs-lookup"><span data-stu-id="6b1dd-124">Class: **GetCustomerSubscribedSkus.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="6b1dd-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6b1dd-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6b1dd-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b1dd-126">Request syntax</span></span>

| <span data-ttu-id="6b1dd-127">Método</span><span class="sxs-lookup"><span data-stu-id="6b1dd-127">Method</span></span>  | <span data-ttu-id="6b1dd-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6b1dd-128">Request URI</span></span>                                                                                    |
|---------|------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6b1dd-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="6b1dd-129">**GET**</span></span> | <span data-ttu-id="6b1dd-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subsskus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6b1dd-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="6b1dd-131">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="6b1dd-131">URI parameter</span></span>

<span data-ttu-id="6b1dd-132">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-132">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="6b1dd-133">Nome</span><span class="sxs-lookup"><span data-stu-id="6b1dd-133">Name</span></span>        | <span data-ttu-id="6b1dd-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="6b1dd-134">Type</span></span>   | <span data-ttu-id="6b1dd-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="6b1dd-135">Required</span></span> | <span data-ttu-id="6b1dd-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b1dd-136">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="6b1dd-137">id cliente</span><span class="sxs-lookup"><span data-stu-id="6b1dd-137">customer-id</span></span> | <span data-ttu-id="6b1dd-138">string</span><span class="sxs-lookup"><span data-stu-id="6b1dd-138">string</span></span> | <span data-ttu-id="6b1dd-139">Yes</span><span class="sxs-lookup"><span data-stu-id="6b1dd-139">Yes</span></span>      | <span data-ttu-id="6b1dd-140">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-140">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6b1dd-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6b1dd-141">Request headers</span></span>

<span data-ttu-id="6b1dd-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6b1dd-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6b1dd-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6b1dd-143">Request body</span></span>

<span data-ttu-id="6b1dd-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6b1dd-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6b1dd-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscribedskus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 53308f82-1bf7-44e2-8dda-4517e4688bd4
MS-CorrelationId: 95660db2-7425-4021-babe-a26ddbcb0187
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="6b1dd-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6b1dd-146">REST response</span></span>

<span data-ttu-id="6b1dd-147">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [SubscrevidosSku.](license-resources.md#subscribedsku)</span><span class="sxs-lookup"><span data-stu-id="6b1dd-147">If successful, the response body contains a collection of [SubscribedSku](license-resources.md#subscribedsku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6b1dd-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6b1dd-148">Response success and error codes</span></span>

<span data-ttu-id="6b1dd-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6b1dd-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6b1dd-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6b1dd-151">Para obter uma lista completa, consulte [os códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6b1dd-151">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6b1dd-152">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6b1dd-152">Response example</span></span>

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
