---
title: Obter licenças atribuídas a um utilizador
description: Saiba como usar as APIs do Partner Center para obter uma lista de licenças atribuídas a um utilizador dentro de uma conta de cliente.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b754ba4ecba7067f78c6868b387bac0190bfd230
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770094"
---
# <a name="get-licenses-assigned-to-a-user-within-a-customer-account"></a><span data-ttu-id="b598e-103">Obtenha licenças atribuídas a um utilizador dentro de uma conta de cliente</span><span class="sxs-lookup"><span data-stu-id="b598e-103">Get licenses assigned to a user within a customer account</span></span>

<span data-ttu-id="b598e-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="b598e-104">**Applies to:**</span></span>

- <span data-ttu-id="b598e-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="b598e-105">Partner Center</span></span>

<span data-ttu-id="b598e-106">Como obter uma lista de licenças atribuídas a um utilizador dentro de uma conta de cliente.</span><span class="sxs-lookup"><span data-stu-id="b598e-106">How to get a list of licenses assigned to a user within a customer account.</span></span> <span data-ttu-id="b598e-107">Os exemplos mostrados aqui devolvem licenças atribuídas ao grupo1, o grupo de licenças padrão que representa licenças geridas pela Azure Ative Directory.</span><span class="sxs-lookup"><span data-stu-id="b598e-107">The examples shown here return licenses assigned from group1, the default license group that represents licenses managed by Azure Active Directory.</span></span> <span data-ttu-id="b598e-108">Para obter licenças atribuídas a grupos de licenças especificados, consulte [obter licenças atribuídas a um utilizador por grupo de licenças.](get-licenses-assigned-to-a-user-by-license-group.md)</span><span class="sxs-lookup"><span data-stu-id="b598e-108">To get licenses assigned from specified license groups, see [Get licenses assigned to a user by license group](get-licenses-assigned-to-a-user-by-license-group.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b598e-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b598e-109">Prerequisites</span></span>

- <span data-ttu-id="b598e-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b598e-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b598e-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="b598e-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="b598e-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b598e-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="b598e-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b598e-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="b598e-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="b598e-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="b598e-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="b598e-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="b598e-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="b598e-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="b598e-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b598e-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="b598e-118">Um identificador de utilizadores.</span><span class="sxs-lookup"><span data-stu-id="b598e-118">A user identifier.</span></span>

## <a name="c"></a><span data-ttu-id="b598e-119">C\#</span><span class="sxs-lookup"><span data-stu-id="b598e-119">C\#</span></span>

<span data-ttu-id="b598e-120">Para verificar quais as licenças atribuídas a um utilizador do grupo de licenças padrão grupo1, utilize primeiro o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b598e-120">To check which licenses are assigned to a user from the default group1 license group, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="b598e-121">Em seguida, ligue para o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID do utilizador para identificar o utilizador.</span><span class="sxs-lookup"><span data-stu-id="b598e-121">Then call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user.</span></span> <span data-ttu-id="b598e-122">Em seguida, obtenha uma interface para as operações de licença de utilizador do cliente a partir da propriedade [**Licenses.**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses)</span><span class="sxs-lookup"><span data-stu-id="b598e-122">Next, get an interface to customer user license operations from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses) property.</span></span> <span data-ttu-id="b598e-123">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) para recuperar a recolha das licenças atribuídas ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="b598e-123">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) or the [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) method to retrieve the collection of licenses assigned to the user.</span></span>

``` csharp
// string selectedCustomerUserId;
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var customerUserAssignedLicenses = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Licenses.Get();
```

<span data-ttu-id="b598e-124">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b598e-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b598e-125">**Projeto**: Partner Center SDK Samples **Class**: CustomerUserAssignedLicenses.cs</span><span class="sxs-lookup"><span data-stu-id="b598e-125">**Project**: Partner Center SDK Samples **Class**: CustomerUserAssignedLicenses.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b598e-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b598e-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b598e-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b598e-127">Request syntax</span></span>

| <span data-ttu-id="b598e-128">Método</span><span class="sxs-lookup"><span data-stu-id="b598e-128">Method</span></span>  | <span data-ttu-id="b598e-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b598e-129">Request URI</span></span>                                                                                              |
|---------|----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b598e-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b598e-130">**GET**</span></span> | <span data-ttu-id="b598e-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/users/{user-id}/licenses HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b598e-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="b598e-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="b598e-132">URI parameter</span></span>

<span data-ttu-id="b598e-133">Utilize os seguintes parâmetros de percurso para identificar o cliente e o utilizador.</span><span class="sxs-lookup"><span data-stu-id="b598e-133">Use the following path parameters to identify the customer and user.</span></span>

| <span data-ttu-id="b598e-134">Nome</span><span class="sxs-lookup"><span data-stu-id="b598e-134">Name</span></span>        | <span data-ttu-id="b598e-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="b598e-135">Type</span></span>   | <span data-ttu-id="b598e-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="b598e-136">Required</span></span> | <span data-ttu-id="b598e-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="b598e-137">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="b598e-138">id cliente</span><span class="sxs-lookup"><span data-stu-id="b598e-138">customer-id</span></span> | <span data-ttu-id="b598e-139">string</span><span class="sxs-lookup"><span data-stu-id="b598e-139">string</span></span> | <span data-ttu-id="b598e-140">Sim</span><span class="sxs-lookup"><span data-stu-id="b598e-140">Yes</span></span>      | <span data-ttu-id="b598e-141">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="b598e-141">A GUID formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="b598e-142">user-id</span><span class="sxs-lookup"><span data-stu-id="b598e-142">user-id</span></span>     | <span data-ttu-id="b598e-143">string</span><span class="sxs-lookup"><span data-stu-id="b598e-143">string</span></span> | <span data-ttu-id="b598e-144">Sim</span><span class="sxs-lookup"><span data-stu-id="b598e-144">Yes</span></span>      | <span data-ttu-id="b598e-145">Uma cadeia formatada GUID que identifica o utilizador.</span><span class="sxs-lookup"><span data-stu-id="b598e-145">A GUID formatted string that identifies the user.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="b598e-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b598e-146">Request headers</span></span>

<span data-ttu-id="b598e-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b598e-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b598e-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b598e-148">Request body</span></span>

<span data-ttu-id="b598e-149">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b598e-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b598e-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b598e-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/482e2152-4b49-48ec-b715-823365ce3d4c/licenses HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 68e50b00-e1ff-422a-a293-158617463d41
MS-CorrelationId: 813f15b3-eb18-4709-b2f3-668d62babf91
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="b598e-151">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b598e-151">REST response</span></span>

<span data-ttu-id="b598e-152">Se for bem sucedido, o organismo de resposta contém a recolha de recursos de [Licença.](license-resources.md#license)</span><span class="sxs-lookup"><span data-stu-id="b598e-152">If successful, the response body contains the collection of [License](license-resources.md#license) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b598e-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b598e-153">Response success and error codes</span></span>

<span data-ttu-id="b598e-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b598e-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b598e-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b598e-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b598e-156">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b598e-156">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b598e-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b598e-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 3883
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 813f15b3-eb18-4709-b2f3-668d62babf91
MS-RequestId: 68e50b00-e1ff-422a-a293-158617463d41
MS-CV: WYkHYMfWTUajFosK.0
MS-ServerId: 020021921
Date: Fri, 09 Jun 2017 00:29:24 GMT

{
    "totalCount": 1,
    "items": [{
            "servicePlans": [{
                    "displayName": "Azure Information Protection Premium P1",
                    "serviceName": "RMS_S_PREMIUM",
                    "id": "6c57d4b6-3b23-47a5-9bc9-69f17b4947b3",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Intune A Direct",
                    "serviceName": "INTUNE_A",
                    "id": "c1ec4a95-1f05-45b3-a911-aa3fa01094f5",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Azure Active Directory Rights",
                    "serviceName": "RMS_S_ENTERPRISE",
                    "id": "bea4c11e-220a-4e6d-8eb8-8ea15d019f90",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Azure Active Directory Premium P1",
                    "serviceName": "AAD_PREMIUM",
                    "id": "41781fb2-bc02-4b7c-bd55-b576c07bb09d",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Azure Multi-Factor Authentication",
                    "serviceName": "MFA_PREMIUM",
                    "id": "8a256a2b-b617-496d-b51b-e76466e88db0",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }
            ],
            "productSku": {
                "id": "efccb6f7-5641-4e0e-bd10-b4976e1bf68e",
                "name": "Enterprise Mobility + Security E3",
                "skuPartNumber": "EMS",
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