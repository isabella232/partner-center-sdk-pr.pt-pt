---
title: Obter um produto por ID
description: Obtém o recurso de produto especificado usando um ID do produto.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 769a4307dc3cebdc7ebbdcf51d9f2b67a9f4b7c2
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874028"
---
# <a name="get-a-product-by-id"></a><span data-ttu-id="11db8-103">Obter um produto por ID</span><span class="sxs-lookup"><span data-stu-id="11db8-103">Get a product by ID</span></span>

<span data-ttu-id="11db8-104">Obtém o recurso de produto especificado usando um ID do produto.</span><span class="sxs-lookup"><span data-stu-id="11db8-104">Gets the specified product resource using a product ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="11db8-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="11db8-105">Prerequisites</span></span>

- <span data-ttu-id="11db8-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="11db8-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="11db8-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="11db8-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="11db8-108">Uma identificação de produto.</span><span class="sxs-lookup"><span data-stu-id="11db8-108">A product ID.</span></span>

## <a name="c"></a><span data-ttu-id="11db8-109">C\#</span><span class="sxs-lookup"><span data-stu-id="11db8-109">C\#</span></span>

<span data-ttu-id="11db8-110">Para encontrar um produto específico por ID, utilize a sua coleção **IAggregatePartner.Products,** selecione o país utilizando o método **ByCountry()** e, em seguida, ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="11db8-110">To find a specific product by ID, use your **IAggregatePartner.Products** collection, select the country by using the **ByCountry()** method, then call the **ById()** method.</span></span> <span data-ttu-id="11db8-111">Por fim, ligue para o método **Get()** ou **GetAsync** para devolver o produto.</span><span class="sxs-lookup"><span data-stu-id="11db8-111">Finally, call the **Get()** or **GetAsync()** method to return the product.</span></span>

```csharp
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.Products.ByCountry("US").ById("DZH318Z0BQ3Q").Get();
```

## <a name="java"></a><span data-ttu-id="11db8-112">Java</span><span class="sxs-lookup"><span data-stu-id="11db8-112">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](<../includes/java-sdk-support.md>)]

<span data-ttu-id="11db8-113">Para encontrar um produto específico por ID, utilize a sua função **IAggregatePartner.getProducts,** selecione o país utilizando a função **byCountry()** e, em seguida, ligue para a função **byId().**</span><span class="sxs-lookup"><span data-stu-id="11db8-113">To find a specific product by ID, use your **IAggregatePartner.getProducts** function, select the country by using the **byCountry()** function, then call the **byId()** function.</span></span> <span data-ttu-id="11db8-114">Por fim, ligue para a função **get()** para devolver o produto.</span><span class="sxs-lookup"><span data-stu-id="11db8-114">Finally, call the **get()** function to return the product.</span></span>

```java
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.getProducts().byCountry("US").byId("DZH318Z0BQ3Q").get();
```

## <a name="powershell"></a><span data-ttu-id="11db8-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="11db8-115">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](<../includes/powershell-module-support.md>)]

<span data-ttu-id="11db8-116">Para encontrar um produto específico por ID, execute o comando [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) e especifique o parâmetro **ProductId.**</span><span class="sxs-lookup"><span data-stu-id="11db8-116">To find a specific product by ID, execute the [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) command and specify the **ProductId** parameter.</span></span> <span data-ttu-id="11db8-117">O parâmetro **CountryCode** são opções, se não for especificado, então o país associado ao revendedor será utilizado.</span><span class="sxs-lookup"><span data-stu-id="11db8-117">The **CountryCode** parameter is options, if it isn't specified then the country associated with the reseller will be used.</span></span>

```powershell
Get-PartnerProduct -ProductId 'DZH318Z0BQ3Q'
```

## <a name="rest-request"></a><span data-ttu-id="11db8-118">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="11db8-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="11db8-119">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="11db8-119">Request syntax</span></span>

| <span data-ttu-id="11db8-120">Método</span><span class="sxs-lookup"><span data-stu-id="11db8-120">Method</span></span>  | <span data-ttu-id="11db8-121">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="11db8-121">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="11db8-122">**Obter**</span><span class="sxs-lookup"><span data-stu-id="11db8-122">**GET**</span></span> | <span data-ttu-id="11db8-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}?country={country} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="11db8-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}?country={country} HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="11db8-124">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="11db8-124">URI parameter</span></span>

<span data-ttu-id="11db8-125">Utilize os seguintes parâmetros de trajetória para obter o produto especificado.</span><span class="sxs-lookup"><span data-stu-id="11db8-125">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="11db8-126">Nome</span><span class="sxs-lookup"><span data-stu-id="11db8-126">Name</span></span>                   | <span data-ttu-id="11db8-127">Tipo</span><span class="sxs-lookup"><span data-stu-id="11db8-127">Type</span></span>     | <span data-ttu-id="11db8-128">Necessário</span><span class="sxs-lookup"><span data-stu-id="11db8-128">Required</span></span> | <span data-ttu-id="11db8-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="11db8-129">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="11db8-130">id produto</span><span class="sxs-lookup"><span data-stu-id="11db8-130">product-id</span></span>             | <span data-ttu-id="11db8-131">string</span><span class="sxs-lookup"><span data-stu-id="11db8-131">string</span></span>   | <span data-ttu-id="11db8-132">Yes</span><span class="sxs-lookup"><span data-stu-id="11db8-132">Yes</span></span>      | <span data-ttu-id="11db8-133">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="11db8-133">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="11db8-134">país</span><span class="sxs-lookup"><span data-stu-id="11db8-134">country</span></span>                | <span data-ttu-id="11db8-135">string</span><span class="sxs-lookup"><span data-stu-id="11db8-135">string</span></span>   | <span data-ttu-id="11db8-136">Yes</span><span class="sxs-lookup"><span data-stu-id="11db8-136">Yes</span></span>      | <span data-ttu-id="11db8-137">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="11db8-137">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="11db8-138">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="11db8-138">Request headers</span></span>

<span data-ttu-id="11db8-139">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="11db8-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="11db8-140">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="11db8-140">Request body</span></span>

<span data-ttu-id="11db8-141">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="11db8-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="11db8-142">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="11db8-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products/{product-id}?country=US HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="11db8-143">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="11db8-143">REST response</span></span>

<span data-ttu-id="11db8-144">Se for bem sucedido, o organismo de resposta contém um recurso [do Produto.](product-resources.md#product)</span><span class="sxs-lookup"><span data-stu-id="11db8-144">If successful, the response body contains a [Product](product-resources.md#product) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="11db8-145">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="11db8-145">Response success and error codes</span></span>

<span data-ttu-id="11db8-146">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="11db8-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="11db8-147">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="11db8-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="11db8-148">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="11db8-148">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="11db8-149">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="11db8-149">This method returns the following error codes:</span></span>

| <span data-ttu-id="11db8-150">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="11db8-150">HTTP Status Code</span></span>     | <span data-ttu-id="11db8-151">Código de erro</span><span class="sxs-lookup"><span data-stu-id="11db8-151">Error code</span></span>   | <span data-ttu-id="11db8-152">Description</span><span class="sxs-lookup"><span data-stu-id="11db8-152">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="11db8-153">404</span><span class="sxs-lookup"><span data-stu-id="11db8-153">404</span></span>                  | <span data-ttu-id="11db8-154">400013</span><span class="sxs-lookup"><span data-stu-id="11db8-154">400013</span></span>       | <span data-ttu-id="11db8-155">O produto não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="11db8-155">Product was not found.</span></span>                                                     |

### <a name="response-example"></a><span data-ttu-id="11db8-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="11db8-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1918
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
Date: Tue, 23 Jan 2018 23:13:01 GMT

{
    "id": "DZH318Z0BQ3Q",
    "title": "Virtual Machines DSv2 Series",
    "description": "Dsv2-series instances are the latest generation of D-series instances that will carry more powerful CPUs which are on average about 35% faster than D-series instances, and carry the same memory and disk configurations as the D-series. Dsv2-series instances are based on the latest generation 2.4 GHz Intel Xeon® E5-2673 v3 (Haswell) processor, and with Intel Turbo Boost Technology 2.0 can go to 3.2 GHz.",
    "productType": {
        "id": "Azure",
        "displayName": "Azure",
        "subType": {
            "id": "VirtualMachines",
            "displayName": "VirtualMachines"
        }
    },
    "isMicrosoftProduct": true,
    "publisherName": "Microsoft",
    "links": {
        "skus": {
            "uri": "/products/DZH318Z0BQ3Q/skus?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BQ3Q?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
