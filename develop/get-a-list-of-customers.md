---
title: Obter uma lista de clientes
description: Como obter uma coleção de recursos representando todos os clientes de um parceiro.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 840c9d1a61451763d37a19639f99b12f1deb7521
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874351"
---
# <a name="get-a-list-of-customers"></a><span data-ttu-id="700ca-103">Obter uma lista de clientes</span><span class="sxs-lookup"><span data-stu-id="700ca-103">Get a list of customers</span></span>

<span data-ttu-id="700ca-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="700ca-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="700ca-105">Este artigo descreve como obter uma coleção de recursos que representa todos os clientes de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="700ca-105">This article describes how to get a collection of resources that represents all of a partner's customers.</span></span>

> [!TIP]
> <span data-ttu-id="700ca-106">Também pode efetuar esta operação no painel partner Center.</span><span class="sxs-lookup"><span data-stu-id="700ca-106">You can also perform this operation in the Partner Center dashboard.</span></span> <span data-ttu-id="700ca-107">Na página principal, sob **gestão do Cliente,** selecione **Ver Clientes.**</span><span class="sxs-lookup"><span data-stu-id="700ca-107">On the main page, under **Customer management**, select **View Customers**.</span></span> <span data-ttu-id="700ca-108">Ou, na barra lateral, selecione **Clientes.**</span><span class="sxs-lookup"><span data-stu-id="700ca-108">Or, on the sidebar, select **Customers**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="700ca-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="700ca-109">Prerequisites</span></span>

- <span data-ttu-id="700ca-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="700ca-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="700ca-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="700ca-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="700ca-112">C\#</span><span class="sxs-lookup"><span data-stu-id="700ca-112">C\#</span></span>

<span data-ttu-id="700ca-113">Para obter uma lista de todos os clientes:</span><span class="sxs-lookup"><span data-stu-id="700ca-113">To get a list of all customers:</span></span>

1. <span data-ttu-id="700ca-114">Utilize a coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para criar um objeto **IPartner.**</span><span class="sxs-lookup"><span data-stu-id="700ca-114">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection to create an **IPartner** object.</span></span>

2. <span data-ttu-id="700ca-115">Recupere a lista de clientes utilizando os métodos [**De consulta**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) ou [**QueryAsync..**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync)</span><span class="sxs-lookup"><span data-stu-id="700ca-115">Retrieve the customer list using the [**Query()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) methods.</span></span> <span data-ttu-id="700ca-116">(Para obter instruções sobre a criação de uma consulta, consulte a classe [**QueriaFactory.)**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)</span><span class="sxs-lookup"><span data-stu-id="700ca-116">(For instructions on creating a query, see the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.)</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// read customers into chunks of 40s
var customersBatch = scopedPartnerOperations.Customers.Query(QueryFactory.Instance.BuildIndexedQuery(40));
var customersEnumerator = scopedPartnerOperations.Enumerators.Customers.Create(customersBatch);
```

<span data-ttu-id="700ca-117">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="700ca-117">For an example, see the following:</span></span>

- <span data-ttu-id="700ca-118">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="700ca-118">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="700ca-119">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="700ca-119">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="700ca-120">Classe: **CustomerPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="700ca-120">Class: **CustomerPaging.cs**</span></span>

## <a name="java"></a><span data-ttu-id="700ca-121">Java</span><span class="sxs-lookup"><span data-stu-id="700ca-121">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="700ca-122">Para obter uma lista de todos os clientes:</span><span class="sxs-lookup"><span data-stu-id="700ca-122">To get a list of all customers:</span></span>

1. <span data-ttu-id="700ca-123">Utilize a função **[IAggregatePartner.getCustomers]** para obter uma referência às operações do cliente.</span><span class="sxs-lookup"><span data-stu-id="700ca-123">Use the [**IAggregatePartner.getCustomers**] function to get a reference to the customer operations.</span></span>

2. <span data-ttu-id="700ca-124">Recupere a lista de clientes utilizando a função **de consulta.**</span><span class="sxs-lookup"><span data-stu-id="700ca-124">Retrieve the customer list using the **query()** function.</span></span>

```java
// Query the customers, get the first page if a page size was set, otherwise get all customers
SeekBasedResourceCollection<Customer> customersPage = partnerOperations.getCustomers().query(QueryFactory.getInstance().buildIndexedQuery(40));

// Create a customer enumerator which will aid us in traversing the customer pages
IResourceCollectionEnumerator<SeekBasedResourceCollection<Customer>> customersEnumerator =
    partnerOperations.getEnumerators().getCustomers().create( customersPage );

int pageNumber = 1;

while (customersEnumerator.hasValue())
{
    /*
     * Use the customersEnumerator.getCurrent() function to
     * access the current page of customers.
     */

    // Get the next page of customers
    customersEnumerator.next();
}
```

## <a name="powershell"></a><span data-ttu-id="700ca-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="700ca-125">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="700ca-126">Execute o comando [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) sem parâmetros para obter uma lista completa de clientes.</span><span class="sxs-lookup"><span data-stu-id="700ca-126">Execute the [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) command with no parameters to get a complete list of customers.</span></span>

```powershell
Get-PartnerCustomer
```

## <a name="rest-request"></a><span data-ttu-id="700ca-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="700ca-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="700ca-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="700ca-128">Request syntax</span></span>

| <span data-ttu-id="700ca-129">Método</span><span class="sxs-lookup"><span data-stu-id="700ca-129">Method</span></span>  | <span data-ttu-id="700ca-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="700ca-130">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="700ca-131">**Obter**</span><span class="sxs-lookup"><span data-stu-id="700ca-131">**GET**</span></span> | <span data-ttu-id="700ca-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes?size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="700ca-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="700ca-133">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="700ca-133">URI parameter</span></span>

<span data-ttu-id="700ca-134">Use o seguinte parâmetro de consulta para obter uma lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="700ca-134">Use the following query parameter to get a list of customers.</span></span>

| <span data-ttu-id="700ca-135">Nome</span><span class="sxs-lookup"><span data-stu-id="700ca-135">Name</span></span>     | <span data-ttu-id="700ca-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="700ca-136">Type</span></span>    | <span data-ttu-id="700ca-137">Necessário</span><span class="sxs-lookup"><span data-stu-id="700ca-137">Required</span></span> | <span data-ttu-id="700ca-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="700ca-138">Description</span></span>                                        |
|----------|---------|----------|----------------------------------------------------|
| <span data-ttu-id="700ca-139">**tamanho**</span><span class="sxs-lookup"><span data-stu-id="700ca-139">**size**</span></span> | <span data-ttu-id="700ca-140">**int**</span><span class="sxs-lookup"><span data-stu-id="700ca-140">**int**</span></span> | <span data-ttu-id="700ca-141">Y</span><span class="sxs-lookup"><span data-stu-id="700ca-141">Y</span></span>        | <span data-ttu-id="700ca-142">O número de resultados a apresentar ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="700ca-142">The number of results to be displayed at one time.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="700ca-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="700ca-143">Request headers</span></span>

<span data-ttu-id="700ca-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="700ca-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="700ca-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="700ca-145">Request body</span></span>

<span data-ttu-id="700ca-146">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="700ca-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="700ca-147">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="700ca-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=40 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="700ca-148">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="700ca-148">REST response</span></span>

<span data-ttu-id="700ca-149">Se for bem sucedido, este método devolve uma coleção de recursos do [Cliente](customer-resources.md#customer) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="700ca-149">If successful, this method returns a collection of [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="700ca-150">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="700ca-150">Response success and error codes</span></span>

<span data-ttu-id="700ca-151">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="700ca-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="700ca-152">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="700ca-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="700ca-153">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="700ca-153">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="700ca-154">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="700ca-154">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 15650
Content-Type: application/json
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
Date: Fri, 20 Nov 2015 01:08:23 GMT

{
    "totalCount": 2,
    "items": [{
        "id": "b44bb1fb-c595-45b0-9e09-d657365580bf",
        "companyProfile": {
            "tenantId": "<guid>",
            "domain": "domain",
            "companyName": "companyName",
            "attributes": {
                "objectType": "CustomerCompanyProfile"
            }
        },
        "relationshipToPartner": "reseller",
        "attributes": {
            "objectType": "Customer"
        }
    },
    {
        "id": "45c44870-ef77-4fdd-b6fe-3dacb075cff2",
        "companyProfile": {
            "tenantId": "<guid>",
            "domain": "domain",
            "companyName": "companyName",
            "attributes": {
                "objectType": "CustomerCompanyProfile"
            }
        },
        "relationshipToPartner": "reseller",
        "attributes": {
            "objectType": "Customer"
        }
    }],
    "links": {
        "self": {
            "uri": "/v1/customers?size=40",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
