---
title: Obter uma lista de clientes
description: Como obter uma coleção de recursos representando todos os clientes de um parceiro.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 2dd8469458809ab38b6d6081adc91d6d1184d2d0
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769631"
---
# <a name="get-a-list-of-customers"></a><span data-ttu-id="8b791-103">Obter uma lista de clientes</span><span class="sxs-lookup"><span data-stu-id="8b791-103">Get a list of customers</span></span>

<span data-ttu-id="8b791-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="8b791-104">**Applies to:**</span></span>

- <span data-ttu-id="8b791-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="8b791-105">Partner Center</span></span>
- <span data-ttu-id="8b791-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="8b791-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="8b791-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="8b791-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="8b791-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8b791-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8b791-109">Este artigo descreve como obter uma coleção de recursos que representa todos os clientes de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="8b791-109">This article describes how to get a collection of resources that represents all of a partner's customers.</span></span>

> [!TIP]
> <span data-ttu-id="8b791-110">Também pode efetuar esta operação no painel partner Center.</span><span class="sxs-lookup"><span data-stu-id="8b791-110">You can also perform this operation in the Partner Center dashboard.</span></span> <span data-ttu-id="8b791-111">Na página principal, sob **gestão do Cliente,** selecione **Ver Clientes.**</span><span class="sxs-lookup"><span data-stu-id="8b791-111">On the main page, under **Customer management**, select **View Customers**.</span></span> <span data-ttu-id="8b791-112">Ou, na barra lateral, selecione **Clientes.**</span><span class="sxs-lookup"><span data-stu-id="8b791-112">Or, on the sidebar, select **Customers**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8b791-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8b791-113">Prerequisites</span></span>

- <span data-ttu-id="8b791-114">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8b791-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8b791-115">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="8b791-115">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="8b791-116">C\#</span><span class="sxs-lookup"><span data-stu-id="8b791-116">C\#</span></span>

<span data-ttu-id="8b791-117">Para obter uma lista de todos os clientes:</span><span class="sxs-lookup"><span data-stu-id="8b791-117">To get a list of all customers:</span></span>

1. <span data-ttu-id="8b791-118">Utilize a coleção [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para criar um objeto **IPartner.**</span><span class="sxs-lookup"><span data-stu-id="8b791-118">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection to create an **IPartner** object.</span></span>

2. <span data-ttu-id="8b791-119">Recupere a lista de clientes utilizando os métodos [**De consulta**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) ou [**QueryAsync..**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync)</span><span class="sxs-lookup"><span data-stu-id="8b791-119">Retrieve the customer list using the [**Query()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) methods.</span></span> <span data-ttu-id="8b791-120">(Para obter instruções sobre a criação de uma consulta, consulte a classe [**QueriaFactory.)**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)</span><span class="sxs-lookup"><span data-stu-id="8b791-120">(For instructions on creating a query, see the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.)</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// read customers into chunks of 40s
var customersBatch = scopedPartnerOperations.Customers.Query(QueryFactory.Instance.BuildIndexedQuery(40));
var customersEnumerator = scopedPartnerOperations.Enumerators.Customers.Create(customersBatch);
```

<span data-ttu-id="8b791-121">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8b791-121">For an example, see the following:</span></span>

- <span data-ttu-id="8b791-122">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="8b791-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="8b791-123">Projeto: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="8b791-123">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="8b791-124">Classe: **CustomerPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="8b791-124">Class: **CustomerPaging.cs**</span></span>

## <a name="java"></a><span data-ttu-id="8b791-125">Java</span><span class="sxs-lookup"><span data-stu-id="8b791-125">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="8b791-126">Para obter uma lista de todos os clientes:</span><span class="sxs-lookup"><span data-stu-id="8b791-126">To get a list of all customers:</span></span>

1. <span data-ttu-id="8b791-127">Utilize a função **[IAggregatePartner.getCustomers]** para obter uma referência às operações do cliente.</span><span class="sxs-lookup"><span data-stu-id="8b791-127">Use the [**IAggregatePartner.getCustomers**] function to get a reference to the customer operations.</span></span>

2. <span data-ttu-id="8b791-128">Recupere a lista de clientes utilizando a função **de consulta.**</span><span class="sxs-lookup"><span data-stu-id="8b791-128">Retrieve the customer list using the **query()** function.</span></span>

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

## <a name="powershell"></a><span data-ttu-id="8b791-129">PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b791-129">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="8b791-130">Execute o comando [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) sem parâmetros para obter uma lista completa de clientes.</span><span class="sxs-lookup"><span data-stu-id="8b791-130">Execute the [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) command with no parameters to get a complete list of customers.</span></span>

```powershell
Get-PartnerCustomer
```

## <a name="rest-request"></a><span data-ttu-id="8b791-131">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="8b791-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8b791-132">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b791-132">Request syntax</span></span>

| <span data-ttu-id="8b791-133">Método</span><span class="sxs-lookup"><span data-stu-id="8b791-133">Method</span></span>  | <span data-ttu-id="8b791-134">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="8b791-134">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="8b791-135">**Obter**</span><span class="sxs-lookup"><span data-stu-id="8b791-135">**GET**</span></span> | <span data-ttu-id="8b791-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes?size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8b791-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="8b791-137">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="8b791-137">URI parameter</span></span>

<span data-ttu-id="8b791-138">Use o seguinte parâmetro de consulta para obter uma lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="8b791-138">Use the following query parameter to get a list of customers.</span></span>

| <span data-ttu-id="8b791-139">Nome</span><span class="sxs-lookup"><span data-stu-id="8b791-139">Name</span></span>     | <span data-ttu-id="8b791-140">Tipo</span><span class="sxs-lookup"><span data-stu-id="8b791-140">Type</span></span>    | <span data-ttu-id="8b791-141">Necessário</span><span class="sxs-lookup"><span data-stu-id="8b791-141">Required</span></span> | <span data-ttu-id="8b791-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b791-142">Description</span></span>                                        |
|----------|---------|----------|----------------------------------------------------|
| <span data-ttu-id="8b791-143">**tamanho**</span><span class="sxs-lookup"><span data-stu-id="8b791-143">**size**</span></span> | <span data-ttu-id="8b791-144">**int**</span><span class="sxs-lookup"><span data-stu-id="8b791-144">**int**</span></span> | <span data-ttu-id="8b791-145">Y</span><span class="sxs-lookup"><span data-stu-id="8b791-145">Y</span></span>        | <span data-ttu-id="8b791-146">O número de resultados a apresentar ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="8b791-146">The number of results to be displayed at one time.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8b791-147">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="8b791-147">Request headers</span></span>

<span data-ttu-id="8b791-148">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8b791-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8b791-149">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="8b791-149">Request body</span></span>

<span data-ttu-id="8b791-150">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8b791-150">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="8b791-151">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="8b791-151">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=40 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="8b791-152">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="8b791-152">REST response</span></span>

<span data-ttu-id="8b791-153">Se for bem sucedido, este método devolve uma coleção de recursos do [Cliente](customer-resources.md#customer) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="8b791-153">If successful, this method returns a collection of [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8b791-154">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="8b791-154">Response success and error codes</span></span>

<span data-ttu-id="8b791-155">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="8b791-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8b791-156">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8b791-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8b791-157">Para obter uma lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="8b791-157">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8b791-158">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="8b791-158">Response example</span></span>

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
