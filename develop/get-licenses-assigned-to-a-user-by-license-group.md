---
title: Obter licenças atribuídas a um utilizador por grupo de licenças
description: Como obter uma lista de licenças atribuídas pelo utilizador para os grupos de licença especificados.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 54acf6f315e3062d03903a98d0c6c1946065f95e
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446008"
---
# <a name="get-licenses-assigned-to-a-user-by-license-group"></a><span data-ttu-id="d3183-103">Obter licenças atribuídas a um utilizador por grupo de licenças</span><span class="sxs-lookup"><span data-stu-id="d3183-103">Get licenses assigned to a user by license group</span></span>

<span data-ttu-id="d3183-104">Como obter uma lista de licenças atribuídas pelo utilizador para os grupos de licença especificados.</span><span class="sxs-lookup"><span data-stu-id="d3183-104">How to get a list of user assigned licenses for the specified license groups.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3183-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d3183-105">Prerequisites</span></span>

- <span data-ttu-id="d3183-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d3183-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d3183-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="d3183-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="d3183-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d3183-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d3183-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d3183-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d3183-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d3183-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d3183-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d3183-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d3183-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d3183-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d3183-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d3183-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d3183-114">Um identificador de utilizadores.</span><span class="sxs-lookup"><span data-stu-id="d3183-114">A user identifier.</span></span>

- <span data-ttu-id="d3183-115">Uma lista de um ou mais identificadores de grupos de licença.</span><span class="sxs-lookup"><span data-stu-id="d3183-115">A list of one or more license group identifiers.</span></span>

## <a name="c"></a><span data-ttu-id="d3183-116">C\#</span><span class="sxs-lookup"><span data-stu-id="d3183-116">C\#</span></span>

<span data-ttu-id="d3183-117">Para verificar quais as licenças atribuídas a um utilizador de grupos de licença especificados, comece por instantanear uma [List/dotnet/api/system.collections.generic.list-1) do tipo [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid), e, em seguida, adicione os grupos de licença à lista.</span><span class="sxs-lookup"><span data-stu-id="d3183-117">To check which licenses are assigned to a user from specified license groups, start by instantiating a [List/dotnet/api/system.collections.generic.list-1) of type [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid), and then add the license groups to the list.</span></span> <span data-ttu-id="d3183-118">Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="d3183-118">Then, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="d3183-119">Em seguida, ligue para o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID do utilizador para identificar o utilizador.</span><span class="sxs-lookup"><span data-stu-id="d3183-119">Next, call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user.</span></span> <span data-ttu-id="d3183-120">Em seguida, obtenha uma interface para as operações de licença de utilizador do cliente a partir da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses)</span><span class="sxs-lookup"><span data-stu-id="d3183-120">Then, get an interface to customer user license operations from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses) property.</span></span> <span data-ttu-id="d3183-121">Por fim, passe a lista de grupos de licenças para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) para recuperar a recolha de licenças atribuídas ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="d3183-121">Finally, pass the list of license groups to the [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) method to retrieve the collection of licenses assigned to the user.</span></span>

``` csharp
// string selectedCustomerUserId;
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

// To get the group1 (Azure Active Directory (AAD)) assigned licenses.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>(){ LicenseGroupId.Group1 };
var customerUserAadAssignedLicenses = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Licenses.Get(licenseGroupIds);

// To get the group2 (Minecraft) assigned licenses.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>(){ LicenseGroupId.Group2 };
var customerUserSfbAssignedLicenses = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Licenses.Get(licenseGroupIds);

// To get both AAD and Minecraft assigned licenses.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>(){ LicenseGroupId.Group1, LicenseGroupId.Group2 };
var customerUserBothAadAndSfbAssignedLicenses = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Licenses.Get(licenseGroupIds);
```

## <a name="rest-request"></a><span data-ttu-id="d3183-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d3183-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d3183-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3183-123">Request syntax</span></span>

| <span data-ttu-id="d3183-124">Método</span><span class="sxs-lookup"><span data-stu-id="d3183-124">Method</span></span>  | <span data-ttu-id="d3183-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d3183-125">Request URI</span></span>                                                                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d3183-126">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d3183-126">**GET**</span></span> | <span data-ttu-id="d3183-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d3183-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1 HTTP/1.1</span></span>                        |
| <span data-ttu-id="d3183-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d3183-128">**GET**</span></span> | <span data-ttu-id="d3183-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d3183-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group2 HTTP/1.1</span></span>                        |
| <span data-ttu-id="d3183-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d3183-130">**GET**</span></span> | <span data-ttu-id="d3183-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d3183-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="d3183-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="d3183-132">URI parameter</span></span>

<span data-ttu-id="d3183-133">Utilize os seguintes parâmetros de percurso e consulta para identificar o cliente, o utilizador e os grupos de licença.</span><span class="sxs-lookup"><span data-stu-id="d3183-133">Use the following path and query parameters to identify the customer, user, and license groups.</span></span>

| <span data-ttu-id="d3183-134">Nome</span><span class="sxs-lookup"><span data-stu-id="d3183-134">Name</span></span>            | <span data-ttu-id="d3183-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="d3183-135">Type</span></span>   | <span data-ttu-id="d3183-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="d3183-136">Required</span></span> | <span data-ttu-id="d3183-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3183-137">Description</span></span>                                                                                                                                                                                                                                                           |
|-----------------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d3183-138">id cliente</span><span class="sxs-lookup"><span data-stu-id="d3183-138">customer-id</span></span>     | <span data-ttu-id="d3183-139">string</span><span class="sxs-lookup"><span data-stu-id="d3183-139">string</span></span> | <span data-ttu-id="d3183-140">Yes</span><span class="sxs-lookup"><span data-stu-id="d3183-140">Yes</span></span>      | <span data-ttu-id="d3183-141">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="d3183-141">A GUID formatted string that identifies the customer.</span></span>                                                                                                                                                                                                                 |
| <span data-ttu-id="d3183-142">user-id</span><span class="sxs-lookup"><span data-stu-id="d3183-142">user-id</span></span>         | <span data-ttu-id="d3183-143">string</span><span class="sxs-lookup"><span data-stu-id="d3183-143">string</span></span> | <span data-ttu-id="d3183-144">Yes</span><span class="sxs-lookup"><span data-stu-id="d3183-144">Yes</span></span>      | <span data-ttu-id="d3183-145">Uma cadeia formatada GUID que identifica o utilizador.</span><span class="sxs-lookup"><span data-stu-id="d3183-145">A GUID formatted string that identifies the user.</span></span>                                                                                                                                                                                                                     |
| <span data-ttu-id="d3183-146">licenseGroupIds</span><span class="sxs-lookup"><span data-stu-id="d3183-146">licenseGroupIds</span></span> | <span data-ttu-id="d3183-147">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="d3183-147">string</span></span> | <span data-ttu-id="d3183-148">No</span><span class="sxs-lookup"><span data-stu-id="d3183-148">No</span></span>       | <span data-ttu-id="d3183-149">Um valor enum que indica o grupo de licenças das licenças atribuídas.</span><span class="sxs-lookup"><span data-stu-id="d3183-149">An enum value that indicates the license group of the assigned licenses.</span></span> <span data-ttu-id="d3183-150">Valores válidos: Grupo1, Grupo 1 - Este grupo tem todos os produtos cuja licença pode ser gerida no Azure Ative Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="d3183-150">Valid values: Group1, Group2 Group1 - This group has all products whose license can be managed in the Azure Active Directory (AAD).</span></span> <span data-ttu-id="d3183-151">Grupo2 - Este grupo tem apenas Minecraft licenças de produtos.</span><span class="sxs-lookup"><span data-stu-id="d3183-151">Group2 - This group has only Minecraft product licenses.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d3183-152">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d3183-152">Request headers</span></span>

<span data-ttu-id="d3183-153">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d3183-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d3183-154">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d3183-154">Request body</span></span>

<span data-ttu-id="d3183-155">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d3183-155">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d3183-156">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d3183-156">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/482e2152-4b49-48ec-b715-823365ce3d4c/licenses?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="d3183-157">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d3183-157">REST response</span></span>

<span data-ttu-id="d3183-158">Se for bem sucedido, o organismo de resposta contém a recolha de recursos de [Licença.](license-resources.md#license)</span><span class="sxs-lookup"><span data-stu-id="d3183-158">If successful, the response body contains the collection of [License](license-resources.md#license) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d3183-159">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d3183-159">Response success and error codes</span></span>

<span data-ttu-id="d3183-160">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d3183-160">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d3183-161">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d3183-161">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d3183-162">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d3183-162">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d3183-163">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d3183-163">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST

{
    "totalCount": 2,
    "items": [{
            "servicePlans": [

            ],
            "productSku": {
                "id": "984df360-9a74-4647-8cf8-696749f6247a",
                "name": "Minecraft Education Edition Faculty",
                "skuPartNumber": "CFQ7TTC0K5DR/0002",
                "licenseGroupId": "group2"
            },
            "attributes": {
                "objectType": "License"
            }
        }, {
            "servicePlans": [{
                    "displayName": "Windows Defender Advanced Threat Protection",
                    "serviceName": "WINDEFATP",
                    "id": "871d91ec-ec1a-452b-a83f-bd76c7d770ef",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Windows 10 Enterprise E3",
                    "serviceName": "WIN10_PRO_ENT_SUB",
                    "id": "21b439ba-a0ca-424f-a6cc-52f954a5b111",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }
            ],
            "productSku": {
                "id": "1e7e1070-8ccb-4aca-b470-d7cb538cb07e",
                "name": "Windows 10 Enterprise E5",
                "skuPartNumber": "WIN_ENT_E5",
                "licenseGroupId": "group1"
            },
            "attributes": {
                "objectType": "License"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="response-example-no-matching-licenses-found"></a><span data-ttu-id="d3183-164">Exemplo de resposta (não foram encontradas licenças correspondentes)</span><span class="sxs-lookup"><span data-stu-id="d3183-164">Response example (no matching licenses found)</span></span>

<span data-ttu-id="d3183-165">Se não forem encontradas licenças correspondentes para os grupos de licença especificados, a resposta contém uma coleção vazia com um elemento TotalCount cujo valor é 0.</span><span class="sxs-lookup"><span data-stu-id="d3183-165">If no matching licenses can be found for the specified license groups, the response contains an empty collection with a totalCount element whose value is 0.</span></span>

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
