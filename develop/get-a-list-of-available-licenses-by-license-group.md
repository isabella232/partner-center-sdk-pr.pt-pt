---
title: Obter uma lista de licenças disponíveis por grupo de licenças
description: Como obter uma lista de licenças para os grupos de licença especificados disponíveis para os utilizadores do cliente especificado.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: de59dfccf723c8f2411d9dadc51beb88688d5b02
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874521"
---
# <a name="get-a-list-of-available-licenses-by-license-group"></a><span data-ttu-id="78615-103">Obter uma lista de licenças disponíveis por grupo de licenças</span><span class="sxs-lookup"><span data-stu-id="78615-103">Get a list of available licenses by license group</span></span>

<span data-ttu-id="78615-104">Como obter uma lista de licenças para os grupos de licença especificados disponíveis para os utilizadores do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="78615-104">How to get a list of licenses for the specified license groups available to users of the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78615-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="78615-105">Prerequisites</span></span>

- <span data-ttu-id="78615-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="78615-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="78615-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="78615-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="78615-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="78615-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="78615-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="78615-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="78615-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="78615-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="78615-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="78615-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="78615-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="78615-112">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="78615-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="78615-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="78615-114">Uma lista de um ou mais identificadores de grupos de licença.</span><span class="sxs-lookup"><span data-stu-id="78615-114">A list of one or more license group identifiers.</span></span>

## <a name="c"></a><span data-ttu-id="78615-115">C\#</span><span class="sxs-lookup"><span data-stu-id="78615-115">C\#</span></span>

<span data-ttu-id="78615-116">Para obter uma lista de licenças disponíveis para os grupos de licença especificados, comece por instantanear uma [Lista](/dotnet/api/system.collections.generic.list-1) do tipo [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid)e, em seguida, adicione os grupos de licença à lista.</span><span class="sxs-lookup"><span data-stu-id="78615-116">To get a list of available licenses for the specified license groups, start by instantiating a [List](/dotnet/api/system.collections.generic.list-1) of type [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid), and then add the license groups to the list.</span></span> <span data-ttu-id="78615-117">Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="78615-117">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="78615-118">Em seguida, obtenha o valor da propriedade [**SubscritaSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) para recuperar uma interface para as operações de recolha SKU subscritas pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="78615-118">Then, get the value of the [**SubscribedSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) property to retrieve an interface to customer subscribed SKU collection operations.</span></span> <span data-ttu-id="78615-119">Por fim, passe a lista de grupos de licenças para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) para recuperar a lista de SKUs subscritos com detalhes sobre as unidades de licença disponíveis.</span><span class="sxs-lookup"><span data-stu-id="78615-119">Finally, pass the list of license groups to the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to retrieve the list of subscribed SKUs with details on available license units.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

// To get subscribed SKUs available for group1, the license group for Azure Active Directory (AAD).
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>() { LicenseGroupId.Group1};
var customerUserAadSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get(licenseGroupIds);

// To get subscribed SKUs available for group2, the license group for Minecraft product licenses.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>() { LicenseGroupId.Group2};
var customerUserSfbSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get(licenseGroupIds);

// To get both AAD and Minecraft subscribed SKUs.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>() { LicenseGroupId.Group1, LicenseGroupId.Group2};
var customerUserBothAadAndSfbSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get(licenseGroupIds);
```

## <a name="rest-request"></a><span data-ttu-id="78615-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="78615-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="78615-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="78615-121">Request syntax</span></span>

| <span data-ttu-id="78615-122">Método</span><span class="sxs-lookup"><span data-stu-id="78615-122">Method</span></span>  | <span data-ttu-id="78615-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="78615-123">Request URI</span></span>                                                                                                                                  |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="78615-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="78615-124">**GET**</span></span> | <span data-ttu-id="78615-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subskus?licenseGroupIds=Group1 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="78615-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1 HTTP/1.1</span></span>                        |
| <span data-ttu-id="78615-126">**Obter**</span><span class="sxs-lookup"><span data-stu-id="78615-126">**GET**</span></span> | <span data-ttu-id="78615-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subskus?licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="78615-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group2 HTTP/1.1</span></span>                        |
| <span data-ttu-id="78615-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="78615-128">**GET**</span></span> | <span data-ttu-id="78615-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="78615-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="78615-130">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="78615-130">URI parameter</span></span>

<span data-ttu-id="78615-131">Utilize os seguintes parâmetros de percurso e consulta para identificar o cliente e os grupos de licença.</span><span class="sxs-lookup"><span data-stu-id="78615-131">Use the following path and query parameters to identify the customer and the license groups.</span></span>

| <span data-ttu-id="78615-132">Nome</span><span class="sxs-lookup"><span data-stu-id="78615-132">Name</span></span>            | <span data-ttu-id="78615-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="78615-133">Type</span></span>   | <span data-ttu-id="78615-134">Necessário</span><span class="sxs-lookup"><span data-stu-id="78615-134">Required</span></span> | <span data-ttu-id="78615-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="78615-135">Description</span></span>                                                                                                                                                                                                                                                           |
|-----------------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="78615-136">id cliente</span><span class="sxs-lookup"><span data-stu-id="78615-136">customer-id</span></span>     | <span data-ttu-id="78615-137">string</span><span class="sxs-lookup"><span data-stu-id="78615-137">string</span></span> | <span data-ttu-id="78615-138">Yes</span><span class="sxs-lookup"><span data-stu-id="78615-138">Yes</span></span>      | <span data-ttu-id="78615-139">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="78615-139">A GUID formatted string that identifies the customer.</span></span>                                                                                                                                                                                                                 |
| <span data-ttu-id="78615-140">licenseGroupIds</span><span class="sxs-lookup"><span data-stu-id="78615-140">licenseGroupIds</span></span> | <span data-ttu-id="78615-141">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="78615-141">string</span></span> | <span data-ttu-id="78615-142">No</span><span class="sxs-lookup"><span data-stu-id="78615-142">No</span></span>       | <span data-ttu-id="78615-143">Um valor enum que indica o grupo de licenças das licenças atribuídas.</span><span class="sxs-lookup"><span data-stu-id="78615-143">An enum value that indicates the license group of the assigned licenses.</span></span> <span data-ttu-id="78615-144">Valores válidos: Grupo1, Grupo 1 - Este grupo tem todos os produtos cuja licença pode ser gerida no Azure Ative Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="78615-144">Valid values: Group1, Group2 Group1 - This group has all products whose license can be managed in the Azure Active Directory (AAD).</span></span> <span data-ttu-id="78615-145">Grupo2 - Este grupo tem apenas Minecraft licenças de produtos.</span><span class="sxs-lookup"><span data-stu-id="78615-145">Group2 - This group has only Minecraft product licenses.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="78615-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="78615-146">Request headers</span></span>

<span data-ttu-id="78615-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="78615-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="78615-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="78615-148">Request body</span></span>

<span data-ttu-id="78615-149">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="78615-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="78615-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="78615-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscribedskus?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="78615-151">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="78615-151">REST response</span></span>

<span data-ttu-id="78615-152">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [SubscrevidosSku.](license-resources.md#subscribedsku)</span><span class="sxs-lookup"><span data-stu-id="78615-152">If successful, the response body contains a collection of [SubscribedSku](license-resources.md#subscribedsku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="78615-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="78615-153">Response success and error codes</span></span>

<span data-ttu-id="78615-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="78615-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="78615-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="78615-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="78615-156">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="78615-156">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="78615-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="78615-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 4328
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CV: S6Pd5XQAx0Ss/zQi.0
MS-ServerId: 030011719
Date: Sat, 10 Jun 2017 00:19:44 GMT

{
    "totalCount": 04,
    "items": [{
            "availableUnits": 15,
            "activeUnits": 15,
            "consumedUnits": 0,
            "suspendedUnits": 0,
            "totalUnits": 15,
            "warningUnits": 0,
            "productSku": {
                "id": "078d2b04-f1bd-4111-bbd4-b4b1b354cef4",
                "name": "Azure Active Directory Premium P1",
                "skuPartNumber": "AAD_PREMIUM",
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
        }, {
            "availableUnits": 1,
            "activeUnits": 1,
            "consumedUnits": 0,
            "suspendedUnits": 0,
            "totalUnits": 1,
            "warningUnits": 0,
            "productSku": {
                "id": "54b84594-9c77-4499-8d65-5e0d5f410e78",
                "name": "Dynamics AX Task",
                "skuPartNumber": "AX_TASK_USER",
                "targetType": "User",
                "licenseGroupId": "group1"
            },
            "servicePlans": [

            ],
            "capabilityStatus": "Enabled",
            "attributes": {
                "objectType": "SubscribedSku"
            }
        }, {
            "availableUnits": 23,
            "activeUnits": 72,
            "consumedUnits": 49,
            "suspendedUnits": 0,
            "totalUnits": 72,
            "warningUnits": 0,
            "productSku": {
                "id": "984df360-9a74-4647-8cf8-696749f6247a",
                "name": "Minecraft Education Edition Faculty",
                "skuPartNumber": "CFQ7TTC0K5DR/0002",
                "targetType": "User",
                "licenseGroupId": "group2"
            },
            "servicePlans": [

            ],
            "capabilityStatus": "Enabled",
            "attributes": {
                "objectType": "SubscribedSku"
            }
        }, {
            "availableUnits": 71,
            "activeUnits": 112,
            "consumedUnits": 41,
            "suspendedUnits": 0,
            "totalUnits": 112,
            "warningUnits": 0,
            "productSku": {
                "id": "1e7e1070-8ccb-4aca-b470-d7cb538cb07e",
                "name": "Windows 10 Enterprise E5",
                "skuPartNumber": "WIN_ENT_E5",
                "targetType": "User",
                "licenseGroupId": "group1"
            },
            "servicePlans": [{
                    "displayName": "Windows Defender Advanced Threat Protection",
                    "serviceName": "WINDEFATP",
                    "id": "871d91ec-ec1a-452b-a83f-bd76c7d770ef",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Windows 10 Enterprise E3",
                    "serviceName": "WIN10_PRO_ENT_SUB",
                    "id": "21b439ba-a0ca-424f-a6cc-52f954a5b111",
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

### <a name="response-example-no-matching-skus-found"></a><span data-ttu-id="78615-158">Exemplo de resposta (não foram encontrados SKUs correspondentes)</span><span class="sxs-lookup"><span data-stu-id="78615-158">Response example (no matching SKUs found)</span></span>

<span data-ttu-id="78615-159">Se não for possível encontrar SKUs correspondentes para os grupos de licença especificados, a resposta contém uma coleção vazia com um elemento TotalCount cujo valor é 0.</span><span class="sxs-lookup"><span data-stu-id="78615-159">If no matching subscribed SKUs can be found for the specified license groups, the response contains an empty collection with a totalCount element whose value is 0.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 71
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CV: q05xrhUeDUKvhrFt.0
MS-ServerId: 030020525
Date: Fri, 09 Jun 2017 22:50:11 GMT

{
    "totalCount": 0,
    "items": [],
    "attributes": {
        "objectType": "Collection"
    }
}
```
