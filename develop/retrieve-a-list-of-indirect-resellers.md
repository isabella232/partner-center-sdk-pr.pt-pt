---
title: Obter uma lista de revendedores indiretos
description: Como recuperar uma lista dos revendedores indiretos do parceiro inscrito.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 58f5c3378b5b941fdc9dafcf28f5efbc58c29c7c
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446569"
---
# <a name="retrieve-a-list-of-indirect-resellers"></a><span data-ttu-id="6816a-103">Obter uma lista de revendedores indiretos</span><span class="sxs-lookup"><span data-stu-id="6816a-103">Retrieve a list of indirect resellers</span></span>

<span data-ttu-id="6816a-104">Como recuperar uma lista dos revendedores indiretos do parceiro inscrito.</span><span class="sxs-lookup"><span data-stu-id="6816a-104">How to retrieve a list of the signed-in partner's indirect resellers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6816a-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6816a-105">Prerequisites</span></span>

- <span data-ttu-id="6816a-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6816a-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6816a-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="6816a-107">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="6816a-108">C\#</span><span class="sxs-lookup"><span data-stu-id="6816a-108">C\#</span></span>

<span data-ttu-id="6816a-109">Para recuperar uma lista de revendedores indiretos com quem o parceiro inscrito tem uma relação, primeiro obter uma interface para operações de recolha de relacionamentos a partir da propriedade [**partnerOperations.Relationships.**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships)</span><span class="sxs-lookup"><span data-stu-id="6816a-109">To retrieve a list of indirect resellers with whom the signed-in partner has a relationship, first get an interface to relationship collection operations from the [**partnerOperations.Relationships**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) property.</span></span> <span data-ttu-id="6816a-110">Em seguida, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.get) or [**Get \_ Async,**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.getasync) passando um membro da enumeração [**PartnerRelationshipType**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype) para identificar o tipo de relacionamento.</span><span class="sxs-lookup"><span data-stu-id="6816a-110">Then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.get) or [**Get\_Async**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.getasync) method, passing a member of the [**PartnerRelationshipType**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype) enumeration to identify the relationship type.</span></span> <span data-ttu-id="6816a-111">Para recuperar revendedores indiretos, tem de utilizar o IsIndirectCloudSolutionProviderOf.</span><span class="sxs-lookup"><span data-stu-id="6816a-111">To retrieve indirect resellers, you must use IsIndirectCloudSolutionProviderOf.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);
```

<span data-ttu-id="6816a-112">**Amostra**: [Aplicativo de teste de consola](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetIndirectResellers.cs</span><span class="sxs-lookup"><span data-stu-id="6816a-112">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetIndirectResellers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="6816a-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6816a-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6816a-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6816a-114">Request syntax</span></span>

| <span data-ttu-id="6816a-115">Método</span><span class="sxs-lookup"><span data-stu-id="6816a-115">Method</span></span>  | <span data-ttu-id="6816a-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6816a-116">Request URI</span></span>                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6816a-117">**Obter**</span><span class="sxs-lookup"><span data-stu-id="6816a-117">**GET**</span></span> | <span data-ttu-id="6816a-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/relationships?relationship \_ type=IsIndirectCloudSolutionProviderOf HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6816a-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/relationships?relationship\_type=IsIndirectCloudSolutionProviderOf HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="6816a-119">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="6816a-119">URI parameter</span></span>

<span data-ttu-id="6816a-120">Utilize o seguinte parâmetro de consulta para identificar o tipo de relacionamento.</span><span class="sxs-lookup"><span data-stu-id="6816a-120">Use the following query parameter to identify the relationship type.</span></span>

| <span data-ttu-id="6816a-121">Nome</span><span class="sxs-lookup"><span data-stu-id="6816a-121">Name</span></span>               | <span data-ttu-id="6816a-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="6816a-122">Type</span></span>    | <span data-ttu-id="6816a-123">Necessário</span><span class="sxs-lookup"><span data-stu-id="6816a-123">Required</span></span>  | <span data-ttu-id="6816a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="6816a-124">Description</span></span>                         |
|--------------------|---------|-----------|-------------------------------------|
| <span data-ttu-id="6816a-125">relationship_type</span><span class="sxs-lookup"><span data-stu-id="6816a-125">relationship_type</span></span>  | <span data-ttu-id="6816a-126">string</span><span class="sxs-lookup"><span data-stu-id="6816a-126">string</span></span>  | <span data-ttu-id="6816a-127">Yes</span><span class="sxs-lookup"><span data-stu-id="6816a-127">Yes</span></span>       | <span data-ttu-id="6816a-128">O valor é a representação de uma das cordas encontradas no [PartnerRelationshipType](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype).</span><span class="sxs-lookup"><span data-stu-id="6816a-128">The value is the string representation of one of the member names found in [PartnerRelationshipType](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype).</span></span><br/><br/> <span data-ttu-id="6816a-129">Se o parceiro estiver inscrito como fornecedor e pretender obter uma lista dos revendedores indiretos com quem estabeleceram uma relação, utilize o IsIndirectCloudSolutionProviderOf.</span><span class="sxs-lookup"><span data-stu-id="6816a-129">If the partner is signed in as a provider and you want to get a list of the indirect resellers with whom they have established a relationship, use IsIndirectCloudSolutionProviderOf.</span></span><br/><br/> <span data-ttu-id="6816a-130">Se o parceiro for inscrito como revendedor e pretender obter uma lista dos fornecedores indiretos com quem estabeleceram uma relação, utilize o IsIndirectResellerOf.</span><span class="sxs-lookup"><span data-stu-id="6816a-130">If the partner is signed in as a reseller and you want to get a list of the indirect providers with whom they have established a relationship, use IsIndirectResellerOf.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="6816a-131">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6816a-131">Request headers</span></span>

<span data-ttu-id="6816a-132">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6816a-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6816a-133">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6816a-133">Request body</span></span>

<span data-ttu-id="6816a-134">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6816a-134">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6816a-135">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6816a-135">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/relationships?relationship_type=IsIndirectCloudSolutionProviderOf HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 144391a4-fb06-41ae-b684-3308ce4706bd
MS-CorrelationId: 72524ef8-81aa-4141-a049-45a4fece5d84
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="6816a-136">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6816a-136">REST response</span></span>

<span data-ttu-id="6816a-137">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [partnerRelationship](relationships-resources.md) para identificar os revendedores.</span><span class="sxs-lookup"><span data-stu-id="6816a-137">If successful, the response body contains a collection of [PartnerRelationship](relationships-resources.md) resources to identify the resellers.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6816a-138">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6816a-138">Response success and error codes</span></span>

<span data-ttu-id="6816a-139">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6816a-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6816a-140">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6816a-140">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6816a-141">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6816a-141">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6816a-142">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6816a-142">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 298
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 72524ef8-81aa-4141-a049-45a4fece5d84
MS-RequestId: 144391a4-fb06-41ae-b684-3308ce4706bd
MS-CV: b21Ll1miM0yFMPQQ.0
MS-ServerId: 030020643
Date: Wed, 05 Apr 2017 21:08:44 GMT

{
    "totalCount": 2,
    "items": [{
            "id": "484e548c-f5f3-4528-93a9-c16c6373cb59",
            "name": "First Up Consultants",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "state": "Active",
            "mpnId": "4847383",
            "location": "US",
            "attributes": {
                "objectType": "PartnerRelationship"
            }
        }, {
            "id": "b01b1487-b36e-4e6d-9b5e-0b58974c4b28",
            "name": "ReleCloud",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "state": "Active",
            "mpnId": "4847433",
            "location": "BR",
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