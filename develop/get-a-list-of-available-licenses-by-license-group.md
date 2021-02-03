---
title: Obter uma lista de licenças disponíveis por grupo de licenças
description: Como obter uma lista de licenças para os grupos de licença especificados disponíveis para os utilizadores do cliente especificado.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 5092bc73107231d602c1465c8d157cdf5499c913
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769554"
---
# <a name="get-a-list-of-available-licenses-by-license-group"></a><span data-ttu-id="91ae4-103">Obter uma lista de licenças disponíveis por grupo de licenças</span><span class="sxs-lookup"><span data-stu-id="91ae4-103">Get a list of available licenses by license group</span></span>

<span data-ttu-id="91ae4-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="91ae4-104">**Applies To**</span></span>

- <span data-ttu-id="91ae4-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="91ae4-105">Partner Center</span></span>

<span data-ttu-id="91ae4-106">Como obter uma lista de licenças para os grupos de licença especificados disponíveis para os utilizadores do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="91ae4-106">How to get a list of licenses for the specified license groups available to users of the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91ae4-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="91ae4-107">Prerequisites</span></span>

- <span data-ttu-id="91ae4-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="91ae4-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="91ae4-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="91ae4-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="91ae4-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="91ae4-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="91ae4-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="91ae4-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="91ae4-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="91ae4-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="91ae4-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="91ae4-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="91ae4-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="91ae4-114">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="91ae4-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="91ae4-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="91ae4-116">Uma lista de um ou mais identificadores de grupos de licença.</span><span class="sxs-lookup"><span data-stu-id="91ae4-116">A list of one or more license group identifiers.</span></span>

## <a name="c"></a><span data-ttu-id="91ae4-117">C\#</span><span class="sxs-lookup"><span data-stu-id="91ae4-117">C\#</span></span>

<span data-ttu-id="91ae4-118">Para obter uma lista de licenças disponíveis para os grupos de licença especificados, comece por instantanear uma [Lista](/dotnet/api/system.collections.generic.list-1) do tipo [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid)e, em seguida, adicione os grupos de licença à lista.</span><span class="sxs-lookup"><span data-stu-id="91ae4-118">To get a list of available licenses for the specified license groups, start by instantiating a [List](/dotnet/api/system.collections.generic.list-1) of type [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid), and then add the license groups to the list.</span></span> <span data-ttu-id="91ae4-119">Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="91ae4-119">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="91ae4-120">Em seguida, obtenha o valor da propriedade [**SubscritaSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) para recuperar uma interface para as operações de recolha SKU subscritas pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="91ae4-120">Then, get the value of the [**SubscribedSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) property to retrieve an interface to customer subscribed SKU collection operations.</span></span> <span data-ttu-id="91ae4-121">Por fim, passe a lista de grupos de licenças para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) para recuperar a lista de SKUs subscritos com detalhes sobre as unidades de licença disponíveis.</span><span class="sxs-lookup"><span data-stu-id="91ae4-121">Finally, pass the list of license groups to the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to retrieve the list of subscribed SKUs with details on available license units.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="91ae4-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="91ae4-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="91ae4-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="91ae4-123">Request syntax</span></span>

| <span data-ttu-id="91ae4-124">Método</span><span class="sxs-lookup"><span data-stu-id="91ae4-124">Method</span></span>  | <span data-ttu-id="91ae4-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="91ae4-125">Request URI</span></span>                                                                                                                                  |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="91ae4-126">**Obter**</span><span class="sxs-lookup"><span data-stu-id="91ae4-126">**GET**</span></span> | <span data-ttu-id="91ae4-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subskus?licenseGroupIds=Group1 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="91ae4-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1 HTTP/1.1</span></span>                        |
| <span data-ttu-id="91ae4-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="91ae4-128">**GET**</span></span> | <span data-ttu-id="91ae4-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subskus?licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="91ae4-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group2 HTTP/1.1</span></span>                        |
| <span data-ttu-id="91ae4-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="91ae4-130">**GET**</span></span> | <span data-ttu-id="91ae4-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="91ae4-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="91ae4-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="91ae4-132">URI parameter</span></span>

<span data-ttu-id="91ae4-133">Utilize os seguintes parâmetros de percurso e consulta para identificar o cliente e os grupos de licença.</span><span class="sxs-lookup"><span data-stu-id="91ae4-133">Use the following path and query parameters to identify the customer and the license groups.</span></span>

| <span data-ttu-id="91ae4-134">Nome</span><span class="sxs-lookup"><span data-stu-id="91ae4-134">Name</span></span>            | <span data-ttu-id="91ae4-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="91ae4-135">Type</span></span>   | <span data-ttu-id="91ae4-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="91ae4-136">Required</span></span> | <span data-ttu-id="91ae4-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="91ae4-137">Description</span></span>                                                                                                                                                                                                                                                           |
|-----------------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="91ae4-138">id cliente</span><span class="sxs-lookup"><span data-stu-id="91ae4-138">customer-id</span></span>     | <span data-ttu-id="91ae4-139">string</span><span class="sxs-lookup"><span data-stu-id="91ae4-139">string</span></span> | <span data-ttu-id="91ae4-140">Sim</span><span class="sxs-lookup"><span data-stu-id="91ae4-140">Yes</span></span>      | <span data-ttu-id="91ae4-141">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="91ae4-141">A GUID formatted string that identifies the customer.</span></span>                                                                                                                                                                                                                 |
| <span data-ttu-id="91ae4-142">licenseGroupIds</span><span class="sxs-lookup"><span data-stu-id="91ae4-142">licenseGroupIds</span></span> | <span data-ttu-id="91ae4-143">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="91ae4-143">string</span></span> | <span data-ttu-id="91ae4-144">No</span><span class="sxs-lookup"><span data-stu-id="91ae4-144">No</span></span>       | <span data-ttu-id="91ae4-145">Um valor enum que indica o grupo de licenças das licenças atribuídas.</span><span class="sxs-lookup"><span data-stu-id="91ae4-145">An enum value that indicates the license group of the assigned licenses.</span></span> <span data-ttu-id="91ae4-146">Valores válidos: Grupo1, Grupo 1 - Este grupo tem todos os produtos cuja licença pode ser gerida no Diretório Ativo Azure (AAD).</span><span class="sxs-lookup"><span data-stu-id="91ae4-146">Valid values: Group1, Group2 Group1 - This group has all products whose license can be managed in the Azure Active Directory (AAD).</span></span> <span data-ttu-id="91ae4-147">Grupo2 - Este grupo tem apenas licenças de produtos Minecraft.</span><span class="sxs-lookup"><span data-stu-id="91ae4-147">Group2 - This group has only Minecraft product licenses.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="91ae4-148">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="91ae4-148">Request headers</span></span>

<span data-ttu-id="91ae4-149">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="91ae4-149">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="91ae4-150">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="91ae4-150">Request body</span></span>

<span data-ttu-id="91ae4-151">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="91ae4-151">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="91ae4-152">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="91ae4-152">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscribedskus?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="91ae4-153">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="91ae4-153">REST response</span></span>

<span data-ttu-id="91ae4-154">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [SubscrevidosSku.](license-resources.md#subscribedsku)</span><span class="sxs-lookup"><span data-stu-id="91ae4-154">If successful, the response body contains a collection of [SubscribedSku](license-resources.md#subscribedsku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="91ae4-155">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="91ae4-155">Response success and error codes</span></span>

<span data-ttu-id="91ae4-156">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="91ae4-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="91ae4-157">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="91ae4-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="91ae4-158">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="91ae4-158">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="91ae4-159">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="91ae4-159">Response example</span></span>

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

### <a name="response-example-no-matching-skus-found"></a><span data-ttu-id="91ae4-160">Exemplo de resposta (não foram encontrados SKUs correspondentes)</span><span class="sxs-lookup"><span data-stu-id="91ae4-160">Response example (no matching SKUs found)</span></span>

<span data-ttu-id="91ae4-161">Se não for possível encontrar SKUs correspondentes para os grupos de licença especificados, a resposta contém uma coleção vazia com um elemento TotalCount cujo valor é 0.</span><span class="sxs-lookup"><span data-stu-id="91ae4-161">If no matching subscribed SKUs can be found for the specified license groups, the response contains an empty collection with a totalCount element whose value is 0.</span></span>

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
