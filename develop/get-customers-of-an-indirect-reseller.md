---
title: Obter clientes de um revendedor indireto
description: Como obter uma lista dos clientes de um revendedor indireto.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: e05248b16b803529258de806c25b117f3104ad2a
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446331"
---
# <a name="get-customers-of-an-indirect-reseller"></a><span data-ttu-id="ac27f-103">Obter clientes de um revendedor indireto</span><span class="sxs-lookup"><span data-stu-id="ac27f-103">Get customers of an indirect reseller</span></span>

<span data-ttu-id="ac27f-104">Como obter uma lista dos clientes de um revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="ac27f-104">How to get a list of the customers of an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ac27f-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ac27f-105">Prerequisites</span></span>

- <span data-ttu-id="ac27f-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ac27f-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ac27f-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="ac27f-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="ac27f-108">O identificador do inquilino do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="ac27f-108">The tenant identifier of the indirect reseller.</span></span>

## <a name="c"></a><span data-ttu-id="ac27f-109">C\#</span><span class="sxs-lookup"><span data-stu-id="ac27f-109">C\#</span></span>

<span data-ttu-id="ac27f-110">Para obter uma coleção de clientes que tenham uma relação com o revendedor indireto especificado, primeiro instantaneamente um objeto [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) para criar o filtro.</span><span class="sxs-lookup"><span data-stu-id="ac27f-110">To get a collection of customers that have a relationship with the specified indirect reseller, first instantiate a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object to create the filter.</span></span> <span data-ttu-id="ac27f-111">Terá de passar o membro de enumeração [**CustomerSearchField.IndirectRese,**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield) convertido numa cadeia, e indicar [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation) como o tipo de operação de filtro.</span><span class="sxs-lookup"><span data-stu-id="ac27f-111">You'll need to pass the [**CustomerSearchField.IndirectReseller**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield) enumeration member converted to a string, and indicate [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation) as the type of filter operation.</span></span> <span data-ttu-id="ac27f-112">Também terá de fornecer o identificador de inquilino do revendedor indireto para filtrar.</span><span class="sxs-lookup"><span data-stu-id="ac27f-112">You'll also need to provide the tenant identifier of the indirect reseller to filter by.</span></span>

<span data-ttu-id="ac27f-113">Em seguida, instantânea um objeto [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) para passar para a consulta, chamando o método [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) e passando-lhe o filtro.</span><span class="sxs-lookup"><span data-stu-id="ac27f-113">Next, instantiate an [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object to pass to the query by calling the [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method and passing it the filter.</span></span> <span data-ttu-id="ac27f-114">BuildSimplyQuery é apenas um dos tipos de consulta suportados pela classe [**QueryFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)</span><span class="sxs-lookup"><span data-stu-id="ac27f-114">BuildSimplyQuery is just one of the query types supported by the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.</span></span>

<span data-ttu-id="ac27f-115">Para executar o filtro e obter o resultado, utilize primeiro [**o IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para obter uma interface para as operações do cliente do parceiro.</span><span class="sxs-lookup"><span data-stu-id="ac27f-115">To execute the filter and get the result, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="ac27f-116">Em [**seguida,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) chame o método Consulta ou [**ConsultaAsync.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync)</span><span class="sxs-lookup"><span data-stu-id="ac27f-116">Then call the [**Query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) method.</span></span>

<span data-ttu-id="ac27f-117">Para criar um enumerador para a passagem de resultados paged, obtenha a interface de fábrica do enumerador de recolha de clientes a partir da propriedade [**IAggregatePartner.Enumeradores.Clientes**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumeratorcontainer.customers) e, em seguida, ligue para [**Criar,**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create)como mostrado no código abaixo, passando a variável que detém a coleção do cliente.</span><span class="sxs-lookup"><span data-stu-id="ac27f-117">To create an enumerator for traversing paged results, get the customer collection enumerator factory interface from the [**IAggregatePartner.Enumerators.Customers**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumeratorcontainer.customers) property, and then call [**Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create), as shown in the code below, passing the variable that holds the customer collection.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string indirectResellerId;

// Create a filter.
var filter = new SimpleFieldFilter(
    CustomerSearchField.IndirectReseller.ToString(),
    FieldFilterOperation.StartsWith,
    indirectResellerId);

// Create an iQuery object to pass to the Query method.
var myQuery = QueryFactory.Instance.BuildSimpleQuery(filter);

// Get the collection of matching customers.
var customersPage = partnerOperations.Customers.Query(myQuery);

// Create a customer enumerator for traversing the customer pages.
var customersEnumerator = partnerOperations.Enumerators.Customers.Create(customersPage);
int pageNumber = 1;

while (customersEnumerator.HasValue)
{
    // Work with the current page.
     foreach (var c in customersEnumerator.Current.Items)
    {
        // Display customer tenant identifier and company name.
        Console.WriteLine(string.Format("{0} - {1}.",c.Id,c.CompanyProfile.CompanyName));
    }
    // Get the next page of customers.
    customersEnumerator.Next();
}
```

<span data-ttu-id="ac27f-118">**Amostra**: [Aplicativo de teste de consola](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetCustomersOfIndirectReseller.cs</span><span class="sxs-lookup"><span data-stu-id="ac27f-118">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetCustomersOfIndirectReseller.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="ac27f-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="ac27f-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ac27f-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac27f-120">Request syntax</span></span>

| <span data-ttu-id="ac27f-121">Método</span><span class="sxs-lookup"><span data-stu-id="ac27f-121">Method</span></span>  | <span data-ttu-id="ac27f-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="ac27f-122">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="ac27f-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="ac27f-123">**GET**</span></span> | <span data-ttu-id="ac27f-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes?size={size}?filter={{filter} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ac27f-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size}?filter={filter} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="ac27f-125">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="ac27f-125">URI parameter</span></span>

<span data-ttu-id="ac27f-126">Utilize os seguintes parâmetros de consulta para criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="ac27f-126">Use the following query parameters to create the request.</span></span>

| <span data-ttu-id="ac27f-127">Nome</span><span class="sxs-lookup"><span data-stu-id="ac27f-127">Name</span></span>   | <span data-ttu-id="ac27f-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="ac27f-128">Type</span></span>   | <span data-ttu-id="ac27f-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="ac27f-129">Required</span></span> | <span data-ttu-id="ac27f-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac27f-130">Description</span></span>                                                                                                                                                                                                                                                                                   |
|--------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ac27f-131">size</span><span class="sxs-lookup"><span data-stu-id="ac27f-131">size</span></span>   | <span data-ttu-id="ac27f-132">int</span><span class="sxs-lookup"><span data-stu-id="ac27f-132">int</span></span>    | <span data-ttu-id="ac27f-133">No</span><span class="sxs-lookup"><span data-stu-id="ac27f-133">No</span></span>       | <span data-ttu-id="ac27f-134">O número de resultados a apresentar ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ac27f-134">The number of results to be displayed at one time.</span></span> <span data-ttu-id="ac27f-135">Este parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="ac27f-135">This parameter is optional.</span></span>                                                                                                                                                                                                                |
| <span data-ttu-id="ac27f-136">filter</span><span class="sxs-lookup"><span data-stu-id="ac27f-136">filter</span></span> | <span data-ttu-id="ac27f-137">filter</span><span class="sxs-lookup"><span data-stu-id="ac27f-137">filter</span></span> | <span data-ttu-id="ac27f-138">Yes</span><span class="sxs-lookup"><span data-stu-id="ac27f-138">Yes</span></span>      | <span data-ttu-id="ac27f-139">A consulta que filtra a procura.</span><span class="sxs-lookup"><span data-stu-id="ac27f-139">The query that filters the search.</span></span> <span data-ttu-id="ac27f-140">Para recuperar os clientes de um revendedor indireto especificado, deve inserir o identificador de revendedor indireto e incluir e codificar a seguinte cadeia: {"Field":"IndirectReseller","Valor":"{{indirect reseller identificador}","Operador":"começa \_ com"}.</span><span class="sxs-lookup"><span data-stu-id="ac27f-140">To retrieve customers for a specified indirect reseller, you must insert the indirect reseller identifier and include and encode the following string: {"Field":"IndirectReseller","Value":"{indirect reseller identifier}","Operator":"starts\_with"}.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ac27f-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="ac27f-141">Request headers</span></span>

<span data-ttu-id="ac27f-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ac27f-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ac27f-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="ac27f-143">Request body</span></span>

<span data-ttu-id="ac27f-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ac27f-144">None.</span></span>

### <a name="request-example-encoded"></a><span data-ttu-id="ac27f-145">Exemplo de pedido (codificado)</span><span class="sxs-lookup"><span data-stu-id="ac27f-145">Request example (encoded)</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter=%7B%22Field%22%3A%22IndirectReseller%22%2C%22Value%22%3A%22484e548c-f5f3-4528-93a9-c16c6373cb59%22%2C%22Operator%22%3A%22starts_with%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="request-example-decoded"></a><span data-ttu-id="ac27f-146">Exemplo de pedido (descodificado)</span><span class="sxs-lookup"><span data-stu-id="ac27f-146">Request example (decoded)</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter={"Field":"IndirectReseller","Value":"484e548c-f5f3-4528-93a9-c16c6373cb59","Operator":"starts_with"} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="ac27f-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="ac27f-147">REST response</span></span>

<span data-ttu-id="ac27f-148">Se for bem sucedido, o organismo de resposta contém informações sobre os clientes do revendedor.</span><span class="sxs-lookup"><span data-stu-id="ac27f-148">If successful, the response body contains information about the reseller's customers.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ac27f-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="ac27f-149">Response success and error codes</span></span>

<span data-ttu-id="ac27f-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="ac27f-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ac27f-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="ac27f-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ac27f-152">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="ac27f-152">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ac27f-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="ac27f-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2273
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: XI2/vIHmIEGVlGL9.0
MS-ServerId: 101112012
Date: Tue, 11 Apr 2017 23:31:28 GMT

{
    "totalCount": 2,
    "items": [{
            "id": "53eb21cb-6b2d-4ee5-9e92-27dfc927e93c",
            "companyProfile": {
                "tenantId": "53eb21cb-6b2d-4ee5-9e92-27dfc927e93c",
                "domain": "FourthCoffee137.onmicrosoft.com",
                "companyName": "FourthCoffee137",
                "links": {
                    "self": {
                        "uri": "/customers/53eb21cb-6b2d-4ee5-9e92-27dfc927e93c/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/53eb21cb-6b2d-4ee5-9e92-27dfc927e93c",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "3dfe847b-cad9-4fc1-86d3-cf16c2790087",
            "companyProfile": {
                "tenantId": "3dfe847b-cad9-4fc1-86d3-cf16c2790087",
                "domain": "WingtipToys1254789149.onmicrosoft.com",
                "companyName": "Wingtip Toys1254789149",
                "links": {
                    "self": {
                        "uri": "/customers/3dfe847b-cad9-4fc1-86d3-cf16c2790087/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/3dfe847b-cad9-4fc1-86d3-cf16c2790087",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        },
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
