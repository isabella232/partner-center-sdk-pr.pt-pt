---
title: Obter uma lista de clientes filtrados por um campo de pesquisa
description: Recebe uma coleção de recursos do Cliente que combinam com um filtro. Pode configurar opcionalmente o tamanho da página. Pode filtrar pelo nome da empresa, domínio, revendedor indireto ou fornecedor de solução de nuvem indireta (CSP).
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 663b8509d8704f9c443796d9fbcf72fb9c5b7fb2
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874963"
---
# <a name="get-a-list-of-customers-filtered-by-a-search-field"></a><span data-ttu-id="1cf82-105">Obter uma lista de clientes filtrados por um campo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="1cf82-105">Get a list of customers filtered by a search field</span></span>

<span data-ttu-id="1cf82-106">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1cf82-106">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1cf82-107">Recebe uma coleção de recursos do [Cliente](customer-resources.md#customer) que combinam com um filtro.</span><span class="sxs-lookup"><span data-stu-id="1cf82-107">Gets a collection of [Customer](customer-resources.md#customer) resources that match a filter.</span></span> <span data-ttu-id="1cf82-108">Pode configurar opcionalmente o tamanho da página.</span><span class="sxs-lookup"><span data-stu-id="1cf82-108">You can optionally set a page size.</span></span> <span data-ttu-id="1cf82-109">Pode filtrar pelo nome da empresa, domínio, revendedor indireto ou fornecedor de solução de nuvem indireta (CSP).</span><span class="sxs-lookup"><span data-stu-id="1cf82-109">You can filter by company name, domain, indirect reseller, or indirect cloud solution provider (CSP).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1cf82-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1cf82-110">Prerequisites</span></span>

- <span data-ttu-id="1cf82-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1cf82-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1cf82-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="1cf82-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="1cf82-113">Um filtro construído pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="1cf82-113">A user-constructed filter.</span></span>

## <a name="c"></a><span data-ttu-id="1cf82-114">C\#</span><span class="sxs-lookup"><span data-stu-id="1cf82-114">C\#</span></span>

<span data-ttu-id="1cf82-115">Para obter uma coleção de clientes que correspondam a um filtro, primeiro instantaneamente um objeto [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) para criar o filtro.</span><span class="sxs-lookup"><span data-stu-id="1cf82-115">To get a collection of customers that match a filter, first instantiate a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object to create the filter.</span></span> <span data-ttu-id="1cf82-116">Terá de passar uma corda que contenha o [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield)e indicar o tipo de operação de filtro como [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation).</span><span class="sxs-lookup"><span data-stu-id="1cf82-116">You'll need to pass a string that contains the [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield), and indicate the type of filter operation as [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation).</span></span> <span data-ttu-id="1cf82-117">É a única operação de filtro de campo suportada pelo ponto final dos clientes.</span><span class="sxs-lookup"><span data-stu-id="1cf82-117">That's the only field filter operation supported by the customers end point.</span></span> <span data-ttu-id="1cf82-118">Também terá de fornecer a corda para filtrar.</span><span class="sxs-lookup"><span data-stu-id="1cf82-118">You'll also need to provide the string to filter by.</span></span>

<span data-ttu-id="1cf82-119">Em seguida, instantânea um objeto [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) para passar para a consulta, chamando o método [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) e passando-lhe o filtro.</span><span class="sxs-lookup"><span data-stu-id="1cf82-119">Next, instantiate an [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object to pass to the query by calling the [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method and passing it the filter.</span></span> <span data-ttu-id="1cf82-120">BuildSimplyQuery é apenas um dos tipos de consulta suportados pela classe [**QueryFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)</span><span class="sxs-lookup"><span data-stu-id="1cf82-120">BuildSimplyQuery is just one of the query types supported by the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.</span></span>

<span data-ttu-id="1cf82-121">Finalmente, para executar o filtro e obter o resultado, use primeiro [**o IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para obter uma interface para as operações do cliente do parceiro.</span><span class="sxs-lookup"><span data-stu-id="1cf82-121">Finally, to execute the filter and get the result, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="1cf82-122">Em [**seguida,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) chame o método Consulta ou [**ConsultaAsync.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync)</span><span class="sxs-lookup"><span data-stu-id="1cf82-122">Then call the [**Query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) method.</span></span>

``` csharp
IAggregatePartner partnerOperations;

// Specify the partial string to filter by (to match Contoso).
string searchPrefix = "cont"

// Create a simple field filter.
var fieldFilter = new SimpleFieldFilter(
    CustomerSearchField.CompanyName.ToString(),
    FieldFilterOperation.StartsWith,
    searchPrefix);

// Create an iQuery object to pass to the Query method.
var myQuery = QueryFactory.Instance.BuildSimpleQuery(fieldFilter);

// Get the collection of matching customers.
var customers = partnerOperations.Customers.Query(myQuery);
```

<span data-ttu-id="1cf82-123">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="1cf82-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="1cf82-124">**Project**: Partner Center SDK Samples **Class**: FilterCustomers.cs</span><span class="sxs-lookup"><span data-stu-id="1cf82-124">**Project**: Partner Center SDK Samples **Class**: FilterCustomers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="1cf82-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="1cf82-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1cf82-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cf82-126">Request syntax</span></span>

| <span data-ttu-id="1cf82-127">Método</span><span class="sxs-lookup"><span data-stu-id="1cf82-127">Method</span></span>  | <span data-ttu-id="1cf82-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="1cf82-128">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="1cf82-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="1cf82-129">**GET**</span></span> | <span data-ttu-id="1cf82-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes?size={size}&filtro={{filter} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1cf82-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size}&filter={filter} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="1cf82-131">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="1cf82-131">URI parameters</span></span>

<span data-ttu-id="1cf82-132">Utilize os seguintes parâmetros de consulta.</span><span class="sxs-lookup"><span data-stu-id="1cf82-132">Use the following query parameters.</span></span>

| <span data-ttu-id="1cf82-133">Nome</span><span class="sxs-lookup"><span data-stu-id="1cf82-133">Name</span></span>   | <span data-ttu-id="1cf82-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="1cf82-134">Type</span></span>   | <span data-ttu-id="1cf82-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="1cf82-135">Required</span></span> | <span data-ttu-id="1cf82-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="1cf82-136">Description</span></span>                                                                    |
|--------|--------|----------|--------------------------------------------------------------------------------|
| <span data-ttu-id="1cf82-137">size</span><span class="sxs-lookup"><span data-stu-id="1cf82-137">size</span></span>   | <span data-ttu-id="1cf82-138">int</span><span class="sxs-lookup"><span data-stu-id="1cf82-138">int</span></span>    | <span data-ttu-id="1cf82-139">No</span><span class="sxs-lookup"><span data-stu-id="1cf82-139">No</span></span>       | <span data-ttu-id="1cf82-140">O número de resultados a apresentar ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="1cf82-140">The number of results to be displayed at one time.</span></span> <span data-ttu-id="1cf82-141">Este parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="1cf82-141">This parameter is optional.</span></span> |
| <span data-ttu-id="1cf82-142">filter</span><span class="sxs-lookup"><span data-stu-id="1cf82-142">filter</span></span> | <span data-ttu-id="1cf82-143">filter</span><span class="sxs-lookup"><span data-stu-id="1cf82-143">filter</span></span> | <span data-ttu-id="1cf82-144">Yes</span><span class="sxs-lookup"><span data-stu-id="1cf82-144">Yes</span></span>      | <span data-ttu-id="1cf82-145">O filtro para aplicar aos clientes.</span><span class="sxs-lookup"><span data-stu-id="1cf82-145">The filter to apply to customers.</span></span> <span data-ttu-id="1cf82-146">Isto deve ser uma corda codificada.</span><span class="sxs-lookup"><span data-stu-id="1cf82-146">This must be an encoded string.</span></span>              |

### <a name="filter-syntax"></a><span data-ttu-id="1cf82-147">Sintaxe do filtro</span><span class="sxs-lookup"><span data-stu-id="1cf82-147">Filter Syntax</span></span>

<span data-ttu-id="1cf82-148">Deve compor o parâmetro do filtro como uma série de pares separados de vírgula.</span><span class="sxs-lookup"><span data-stu-id="1cf82-148">You must compose the filter parameter as a series of comma separated, key-value pairs.</span></span> <span data-ttu-id="1cf82-149">Cada chave e valor devem ser citados individualmente e separados por um cólon.</span><span class="sxs-lookup"><span data-stu-id="1cf82-149">Each key and value must be individually quoted and separated by a colon.</span></span> <span data-ttu-id="1cf82-150">Todo o filtro deve ser codificado.</span><span class="sxs-lookup"><span data-stu-id="1cf82-150">The entire filter must be encoded.</span></span>

<span data-ttu-id="1cf82-151">Um exemplo não codificado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1cf82-151">An unencoded example looks like this:</span></span>

```http
?filter{"Field":"CompanyName","Value":"cont","Operator":"starts_with"}
```

<span data-ttu-id="1cf82-152">A tabela a seguir descreve os pares de valor-chave necessários:</span><span class="sxs-lookup"><span data-stu-id="1cf82-152">The following table describes the required key-value pairs:</span></span>

| <span data-ttu-id="1cf82-153">Chave</span><span class="sxs-lookup"><span data-stu-id="1cf82-153">Key</span></span>      | <span data-ttu-id="1cf82-154">Valor</span><span class="sxs-lookup"><span data-stu-id="1cf82-154">Value</span></span>                                                                                                                    |
|----------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1cf82-155">Campo</span><span class="sxs-lookup"><span data-stu-id="1cf82-155">Field</span></span>    | <span data-ttu-id="1cf82-156">O campo para filtrar.</span><span class="sxs-lookup"><span data-stu-id="1cf82-156">The field to filter.</span></span> <span data-ttu-id="1cf82-157">Os valores válidos podem ser encontrados no [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield).</span><span class="sxs-lookup"><span data-stu-id="1cf82-157">The valid values can be found in [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield).</span></span> |
| <span data-ttu-id="1cf82-158">Valor</span><span class="sxs-lookup"><span data-stu-id="1cf82-158">Value</span></span>    | <span data-ttu-id="1cf82-159">O valor a filtrar.</span><span class="sxs-lookup"><span data-stu-id="1cf82-159">The value to filter by.</span></span> <span data-ttu-id="1cf82-160">O caso do valor é ignorado.</span><span class="sxs-lookup"><span data-stu-id="1cf82-160">The case of the value is ignored.</span></span>                                                                |
| <span data-ttu-id="1cf82-161">Operador</span><span class="sxs-lookup"><span data-stu-id="1cf82-161">Operator</span></span> | <span data-ttu-id="1cf82-162">O operador a candidatar-se.</span><span class="sxs-lookup"><span data-stu-id="1cf82-162">The operator to apply.</span></span> <span data-ttu-id="1cf82-163">O único valor suportado para este cenário de cliente é "começa \_ por".</span><span class="sxs-lookup"><span data-stu-id="1cf82-163">The only supported value for this customer scenario is "starts\_with".</span></span>                            |

### <a name="request-headers"></a><span data-ttu-id="1cf82-164">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="1cf82-164">Request headers</span></span>

<span data-ttu-id="1cf82-165">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1cf82-165">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1cf82-166">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="1cf82-166">Request body</span></span>

<span data-ttu-id="1cf82-167">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1cf82-167">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="1cf82-168">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="1cf82-168">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter=%7B%22Field%22%3A%22CompanyName%22%2C%22Value%22%3A%22Cont%22%2C%22Operator%22%3A%22starts_with%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 5ce66de5-eea9-486f-a11c-c852aa3d1502
MS-CorrelationId: a2a912ee-d595-47e2-97ae-1b0ae1efa13d
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="1cf82-169">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="1cf82-169">REST response</span></span>

<span data-ttu-id="1cf82-170">Se for bem sucedido, este método devolve uma coleção de recursos [do Cliente](customer-resources.md#customer) correspondentes no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="1cf82-170">If successful, this method returns a collection of matching [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1cf82-171">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="1cf82-171">Response success and error codes</span></span>

<span data-ttu-id="1cf82-172">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="1cf82-172">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1cf82-173">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="1cf82-173">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1cf82-174">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="1cf82-174">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1cf82-175">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="1cf82-175">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1839
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a2a912ee-d595-47e2-97ae-1b0ae1efa13d
MS-RequestId: dfeda56c-1af5-43fc-a9c0-346b9e85dc96
MS-CV: n0lMNyJtaUC802pO.0
MS-ServerId: 202010223
Date: Fri, 24 Feb 2017 22:08:20 GMT

{
    "totalCount": 3,
    "items": [{
            "id": "c5757d70-06f3-4f23-8367-5a9e55019f94",
            "companyProfile": {
                "tenantId": "c5757d70-06f3-4f23-8367-5a9e55019f94",
                "domain": "contoso190.onmicrosoft.com",
                "companyName": "Contoso190",
                "links": {
                    "self": {
                        "uri": "/customers/c5757d70-06f3-4f23-8367-5a9e55019f94/profiles/company",
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
                    "uri": "/customers/c5757d70-06f3-4f23-8367-5a9e55019f94",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "7b26b357-9ca3-48b8-a58e-4febe2662a5d",
            "companyProfile": {
                "tenantId": "7b26b357-9ca3-48b8-a58e-4febe2662a5d",
                "domain": "ContosoCorpCo.onmicrosoft.com",
                "companyName": "Contoso",
                "links": {
                    "self": {
                        "uri": "/customers/7b26b357-9ca3-48b8-a58e-4febe2662a5d/profiles/company",
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
                    "uri": "/customers/7b26b357-9ca3-48b8-a58e-4febe2662a5d",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
            "companyProfile": {
                "tenantId": "bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
                "domain": "contosocorpdemo.onmicrosoft.com",
                "companyName": "Contoso",
                "links": {
                    "self": {
                        "uri": "/customers/bfbd6ef0-311f-47ec-bbd7-0fcb7846661b/profiles/company",
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
                    "uri": "/customers/bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers?size=0&filter=%7B%22Field%22%3A%22Domain%22%2C%22Value%22%3A%22cont%22%2C%22Operator%22%3A%22starts_with%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
