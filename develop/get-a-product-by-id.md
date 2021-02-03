---
title: Obter um produto por ID
description: Obtém o recurso de produto especificado usando um ID do produto.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 8aca626597e9ec903ebecca7d55577ba636c518e
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769032"
---
# <a name="get-a-product-by-id"></a><span data-ttu-id="b8e24-103">Obter um produto por ID</span><span class="sxs-lookup"><span data-stu-id="b8e24-103">Get a product by ID</span></span>

<span data-ttu-id="b8e24-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="b8e24-104">**Applies To**</span></span>

- <span data-ttu-id="b8e24-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="b8e24-105">Partner Center</span></span>

<span data-ttu-id="b8e24-106">Obtém o recurso de produto especificado usando um ID do produto.</span><span class="sxs-lookup"><span data-stu-id="b8e24-106">Gets the specified product resource using a product ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b8e24-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b8e24-107">Prerequisites</span></span>

- <span data-ttu-id="b8e24-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b8e24-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b8e24-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="b8e24-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="b8e24-110">Uma identificação de produto.</span><span class="sxs-lookup"><span data-stu-id="b8e24-110">A product ID.</span></span>

## <a name="c"></a><span data-ttu-id="b8e24-111">C\#</span><span class="sxs-lookup"><span data-stu-id="b8e24-111">C\#</span></span>

<span data-ttu-id="b8e24-112">Para encontrar um produto específico por ID, utilize a sua coleção **IAggregatePartner.Products,** selecione o país utilizando o método **ByCountry()** e, em seguida, ligue para o método **ById().**</span><span class="sxs-lookup"><span data-stu-id="b8e24-112">To find a specific product by ID, use your **IAggregatePartner.Products** collection, select the country by using the **ByCountry()** method, then call the **ById()** method.</span></span> <span data-ttu-id="b8e24-113">Por fim, ligue para o método **Get()** ou **GetAsync** para devolver o produto.</span><span class="sxs-lookup"><span data-stu-id="b8e24-113">Finally, call the **Get()** or **GetAsync()** method to return the product.</span></span>

```csharp
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.Products.ByCountry("US").ById("DZH318Z0BQ3Q").Get();
```

## <a name="java"></a><span data-ttu-id="b8e24-114">Java</span><span class="sxs-lookup"><span data-stu-id="b8e24-114">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](<../includes/java-sdk-support.md>)]

<span data-ttu-id="b8e24-115">Para encontrar um produto específico por ID, utilize a sua função **IAggregatePartner.getProducts,** selecione o país utilizando a função **byCountry()** e, em seguida, ligue para a função **byId().**</span><span class="sxs-lookup"><span data-stu-id="b8e24-115">To find a specific product by ID, use your **IAggregatePartner.getProducts** function, select the country by using the **byCountry()** function, then call the **byId()** function.</span></span> <span data-ttu-id="b8e24-116">Por fim, ligue para a função **get()** para devolver o produto.</span><span class="sxs-lookup"><span data-stu-id="b8e24-116">Finally, call the **get()** function to return the product.</span></span>

```java
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.getProducts().byCountry("US").byId("DZH318Z0BQ3Q").get();
```

## <a name="powershell"></a><span data-ttu-id="b8e24-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8e24-117">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](<../includes/powershell-module-support.md>)]

<span data-ttu-id="b8e24-118">Para encontrar um produto específico por ID, execute o comando [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) e especifique o parâmetro **ProductId.**</span><span class="sxs-lookup"><span data-stu-id="b8e24-118">To find a specific product by ID, execute the [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) command and specify the **ProductId** parameter.</span></span> <span data-ttu-id="b8e24-119">O parâmetro **CountryCode** são opções, se não for especificado, então o país associado ao revendedor será utilizado.</span><span class="sxs-lookup"><span data-stu-id="b8e24-119">The **CountryCode** parameter is options, if it isn't specified then the country associated with the reseller will be used.</span></span>

```powershell
Get-PartnerProduct -ProductId 'DZH318Z0BQ3Q'
```

## <a name="rest-request"></a><span data-ttu-id="b8e24-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b8e24-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b8e24-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8e24-121">Request syntax</span></span>

| <span data-ttu-id="b8e24-122">Método</span><span class="sxs-lookup"><span data-stu-id="b8e24-122">Method</span></span>  | <span data-ttu-id="b8e24-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b8e24-123">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="b8e24-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b8e24-124">**GET**</span></span> | <span data-ttu-id="b8e24-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}?country={country} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b8e24-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}?country={country} HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="b8e24-126">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="b8e24-126">URI parameter</span></span>

<span data-ttu-id="b8e24-127">Utilize os seguintes parâmetros de trajetória para obter o produto especificado.</span><span class="sxs-lookup"><span data-stu-id="b8e24-127">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="b8e24-128">Nome</span><span class="sxs-lookup"><span data-stu-id="b8e24-128">Name</span></span>                   | <span data-ttu-id="b8e24-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="b8e24-129">Type</span></span>     | <span data-ttu-id="b8e24-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="b8e24-130">Required</span></span> | <span data-ttu-id="b8e24-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8e24-131">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="b8e24-132">id produto</span><span class="sxs-lookup"><span data-stu-id="b8e24-132">product-id</span></span>             | <span data-ttu-id="b8e24-133">string</span><span class="sxs-lookup"><span data-stu-id="b8e24-133">string</span></span>   | <span data-ttu-id="b8e24-134">Sim</span><span class="sxs-lookup"><span data-stu-id="b8e24-134">Yes</span></span>      | <span data-ttu-id="b8e24-135">Uma corda que identifica o produto.</span><span class="sxs-lookup"><span data-stu-id="b8e24-135">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="b8e24-136">país</span><span class="sxs-lookup"><span data-stu-id="b8e24-136">country</span></span>                | <span data-ttu-id="b8e24-137">string</span><span class="sxs-lookup"><span data-stu-id="b8e24-137">string</span></span>   | <span data-ttu-id="b8e24-138">Sim</span><span class="sxs-lookup"><span data-stu-id="b8e24-138">Yes</span></span>      | <span data-ttu-id="b8e24-139">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="b8e24-139">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="b8e24-140">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b8e24-140">Request headers</span></span>

<span data-ttu-id="b8e24-141">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b8e24-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b8e24-142">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b8e24-142">Request body</span></span>

<span data-ttu-id="b8e24-143">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b8e24-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b8e24-144">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b8e24-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products/{product-id}?country=US HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="b8e24-145">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b8e24-145">REST response</span></span>

<span data-ttu-id="b8e24-146">Se for bem sucedido, o organismo de resposta contém um recurso [do Produto.](product-resources.md#product)</span><span class="sxs-lookup"><span data-stu-id="b8e24-146">If successful, the response body contains a [Product](product-resources.md#product) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b8e24-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b8e24-147">Response success and error codes</span></span>

<span data-ttu-id="b8e24-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b8e24-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b8e24-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b8e24-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b8e24-150">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b8e24-150">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="b8e24-151">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="b8e24-151">This method returns the following error codes:</span></span>

| <span data-ttu-id="b8e24-152">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="b8e24-152">HTTP Status Code</span></span>     | <span data-ttu-id="b8e24-153">Código de erro</span><span class="sxs-lookup"><span data-stu-id="b8e24-153">Error code</span></span>   | <span data-ttu-id="b8e24-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8e24-154">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="b8e24-155">404</span><span class="sxs-lookup"><span data-stu-id="b8e24-155">404</span></span>                  | <span data-ttu-id="b8e24-156">400013</span><span class="sxs-lookup"><span data-stu-id="b8e24-156">400013</span></span>       | <span data-ttu-id="b8e24-157">O produto não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="b8e24-157">Product was not found.</span></span>                                                     |

### <a name="response-example"></a><span data-ttu-id="b8e24-158">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b8e24-158">Response example</span></span>

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
