---
title: Obter revendedores indiretos de um cliente
description: Como obter uma lista dos revendedores indiretos que têm uma relação com um cliente especificado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: d69abf9530548f110820ca04fefb698e0e37556c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769691"
---
# <a name="get-indirect-resellers-of-a-customer"></a><span data-ttu-id="a0fa8-103">Obter revendedores indiretos de um cliente</span><span class="sxs-lookup"><span data-stu-id="a0fa8-103">Get indirect resellers of a customer</span></span>

<span data-ttu-id="a0fa8-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="a0fa8-104">**Applies To**</span></span>

- <span data-ttu-id="a0fa8-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="a0fa8-105">Partner Center</span></span>

<span data-ttu-id="a0fa8-106">Como obter uma lista dos revendedores indiretos que têm uma relação com um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-106">How to get a list of the indirect resellers that have a relationship with a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0fa8-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a0fa8-107">Prerequisites</span></span>

- <span data-ttu-id="a0fa8-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a0fa8-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a0fa8-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="a0fa8-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a0fa8-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a0fa8-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a0fa8-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a0fa8-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="a0fa8-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a0fa8-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="a0fa8-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a0fa8-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a0fa8-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="a0fa8-116">C\#</span><span class="sxs-lookup"><span data-stu-id="a0fa8-116">C\#</span></span>

<span data-ttu-id="a0fa8-117">Para recuperar uma lista de revendedores indiretos com quem o cliente especificado tem uma relação, primeiro obtenha uma interface para as operações de recolha do cliente para o cliente específico a partir da propriedade [**partnerOperations.Customers,**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) fornecendo o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-117">To retrieve a list of indirect resellers with whom the specified customer has a relationship, first get an interface to customer collection operations for the specific customer from the [**partnerOperations.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) property by providing the customer ID to identify the customer.</span></span> <span data-ttu-id="a0fa8-118">Em seguida, ligue para o método [**Relacionamentos.Get**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.get) ou [**Get \_ Async**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.getasync) para obter a lista de revendedores indiretos.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-118">Then call the [**Relationships.Get**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.get) or [**Get\_Async**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.getasync) method to get the list of indirect resellers.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

 var indirectResellers = partnerOperations.Customers[customerId].Relationships.Get();
```

<span data-ttu-id="a0fa8-119">**Amostra**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetIndirectResellersOfCustomer.cs</span><span class="sxs-lookup"><span data-stu-id="a0fa8-119">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetIndirectResellersOfCustomer.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="a0fa8-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="a0fa8-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a0fa8-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0fa8-121">Request syntax</span></span>

| <span data-ttu-id="a0fa8-122">Método</span><span class="sxs-lookup"><span data-stu-id="a0fa8-122">Method</span></span>  | <span data-ttu-id="a0fa8-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="a0fa8-123">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="a0fa8-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="a0fa8-124">**GET**</span></span> | <span data-ttu-id="a0fa8-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/relationships HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a0fa8-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/relationships HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="a0fa8-126">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="a0fa8-126">URI parameter</span></span>

<span data-ttu-id="a0fa8-127">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-127">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="a0fa8-128">Nome</span><span class="sxs-lookup"><span data-stu-id="a0fa8-128">Name</span></span>        | <span data-ttu-id="a0fa8-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="a0fa8-129">Type</span></span>   | <span data-ttu-id="a0fa8-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="a0fa8-130">Required</span></span> | <span data-ttu-id="a0fa8-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0fa8-131">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="a0fa8-132">id cliente</span><span class="sxs-lookup"><span data-stu-id="a0fa8-132">customer-id</span></span> | <span data-ttu-id="a0fa8-133">string</span><span class="sxs-lookup"><span data-stu-id="a0fa8-133">string</span></span> | <span data-ttu-id="a0fa8-134">Sim</span><span class="sxs-lookup"><span data-stu-id="a0fa8-134">Yes</span></span>      | <span data-ttu-id="a0fa8-135">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-135">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a0fa8-136">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="a0fa8-136">Request headers</span></span>

<span data-ttu-id="a0fa8-137">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a0fa8-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a0fa8-138">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="a0fa8-138">Request body</span></span>

<span data-ttu-id="a0fa8-139">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-139">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="a0fa8-140">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a0fa8-140">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/relationships HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c9251710-5a30-4cd3-891a-c42d550af9a8
MS-CorrelationId: a96f326c-a392-44f4-bcfe-43152a756ba8
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="a0fa8-141">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="a0fa8-141">REST response</span></span>

<span data-ttu-id="a0fa8-142">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [partnerRelationship](relationships-resources.md) para identificar os revendedores.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-142">If successful, the response body contains a collection of [PartnerRelationship](relationships-resources.md) resources to identify the resellers.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a0fa8-143">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="a0fa8-143">Response success and error codes</span></span>

<span data-ttu-id="a0fa8-144">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a0fa8-145">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="a0fa8-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a0fa8-146">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="a0fa8-146">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a0fa8-147">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a0fa8-147">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 264
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a96f326c-a392-44f4-bcfe-43152a756ba8
MS-RequestId: c9251710-5a30-4cd3-891a-c42d550af9a8
MS-CV: plJP3ufU0UqXMeuh.0
MS-ServerId: 020021921
Date: Fri, 07 Apr 2017 23:42:11 GMT

{
    "totalCount": 1,
    "items": [{
            "id": "484e548c-f5f3-4528-93a9-c16c6373cb59",
            "name": "First Up Consultants",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "mpnId": "4847383",
            "attributes": {
                "objectType": "PartnerRelationship"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
