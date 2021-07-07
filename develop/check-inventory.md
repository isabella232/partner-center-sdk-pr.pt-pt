---
title: Verifique o inventário
description: Saiba como usar as APIs do Partner Center para verificar o inventário para obter um conjunto específico de itens de catálogo. Pode fazê-lo para identificar os produtos de um cliente ou SKUs.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b982dbd7e5e10d454ef87a1e750546ea50eb8438
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974085"
---
# <a name="check-the-inventory-of-catalog-items-using-partner-center-apis"></a><span data-ttu-id="9ac1f-104">Verifique o inventário de itens de catálogo usando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="9ac1f-104">Check the inventory of catalog items using Partner Center APIs</span></span>

<span data-ttu-id="9ac1f-105">Como verificar o inventário para obter um conjunto específico de itens de catálogo.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-105">How to check the inventory for a specific set of catalog items.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ac1f-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9ac1f-106">Prerequisites</span></span>

- <span data-ttu-id="9ac1f-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9ac1f-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9ac1f-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="9ac1f-109">Uma ou mais identificações de produtos.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-109">One or more product IDs.</span></span> <span data-ttu-id="9ac1f-110">Opcionalmente, os IDs SKU também podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-110">Optionally, SKU IDs can also be specified.</span></span>

- <span data-ttu-id="9ac1f-111">Qualquer contexto adicional necessário para verificar o inventário dos SKU(s) referenciados pelo produto fornecido/SKU ID(s).</span><span class="sxs-lookup"><span data-stu-id="9ac1f-111">Any additional context needed for verifying the inventory of the SKU(s) referenced by the provided product/SKU ID(s).</span></span> <span data-ttu-id="9ac1f-112">Estes requisitos podem variar por tipo de produto/SKU e podem ser determinados a partir da propriedade [Da SKU's](product-resources.md#sku) **InventoryVariables.**</span><span class="sxs-lookup"><span data-stu-id="9ac1f-112">These requirements may vary by type of product/SKU and can be determined from the [SKU's](product-resources.md#sku) **InventoryVariables** property.</span></span>

## <a name="c"></a><span data-ttu-id="9ac1f-113">C\#</span><span class="sxs-lookup"><span data-stu-id="9ac1f-113">C\#</span></span>

<span data-ttu-id="9ac1f-114">Para verificar o inventário, construa um objeto [InventoryCheckRequest](product-resources.md#inventorycheckrequest) utilizando um objeto [InventoryItem](product-resources.md#inventoryitem) para cada item a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-114">To check the inventory, build an [InventoryCheckRequest](product-resources.md#inventorycheckrequest) object using an [InventoryItem](product-resources.md#inventoryitem) object for each item to be checked.</span></span> <span data-ttu-id="9ac1f-115">Em seguida, utilize um acessório **IAggregatePartner.Extensions,** passe-o para **o Produto** e, em seguida, selecione o país utilizando o método **ByCountry().**</span><span class="sxs-lookup"><span data-stu-id="9ac1f-115">Then, use an **IAggregatePartner.Extensions** accessor, scope it down to **Product** and then select the country using the **ByCountry()** method.</span></span> <span data-ttu-id="9ac1f-116">Por fim, ligue para o método **CheckInventory()** com o seu objeto **InventoryCheckRequest.**</span><span class="sxs-lookup"><span data-stu-id="9ac1f-116">Finally, call the **CheckInventory()** method with your **InventoryCheckRequest** object.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string subscriptionId;
string countryCode;
string productId;

// Build the inventory check request details object.
var inventoryCheckRequest = new InventoryCheckRequest()
{
    TargetItems = new InventoryItem[]{ new InventoryItem { ProductId = productId } },
    InventoryContext = new Dictionary<string, string>()
    {
      { "customerId", customerId },
      { "azureSubscriptionId", subscriptionId }
      { "armRegionName", armRegionName }
    }
};

// Get the inventory results.
var inventoryResults = partnerOperations.Extensions.Product.ByCountry(countryCode).CheckInventory(inventoryCheckRequest);
```

## <a name="rest-request"></a><span data-ttu-id="9ac1f-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="9ac1f-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9ac1f-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ac1f-118">Request syntax</span></span>

| <span data-ttu-id="9ac1f-119">Método</span><span class="sxs-lookup"><span data-stu-id="9ac1f-119">Method</span></span>   | <span data-ttu-id="9ac1f-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="9ac1f-120">Request URI</span></span>                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9ac1f-121">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="9ac1f-121">**POST**</span></span> | <span data-ttu-id="9ac1f-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/extensions/product/checkInventory?country={country-code} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9ac1f-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/extensions/product/checkInventory?country={country-code} HTTP/1.1</span></span>                        |

### <a name="uri-parameter"></a><span data-ttu-id="9ac1f-123">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="9ac1f-123">URI parameter</span></span>

<span data-ttu-id="9ac1f-124">Utilize o seguinte parâmetro de consulta para verificar o inventário.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-124">Use the following query parameter to check the inventory.</span></span>

| <span data-ttu-id="9ac1f-125">Nome</span><span class="sxs-lookup"><span data-stu-id="9ac1f-125">Name</span></span>                   | <span data-ttu-id="9ac1f-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="9ac1f-126">Type</span></span>     | <span data-ttu-id="9ac1f-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="9ac1f-127">Required</span></span> | <span data-ttu-id="9ac1f-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ac1f-128">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="9ac1f-129">código de país</span><span class="sxs-lookup"><span data-stu-id="9ac1f-129">country-code</span></span>           | <span data-ttu-id="9ac1f-130">string</span><span class="sxs-lookup"><span data-stu-id="9ac1f-130">string</span></span>   | <span data-ttu-id="9ac1f-131">Yes</span><span class="sxs-lookup"><span data-stu-id="9ac1f-131">Yes</span></span>      | <span data-ttu-id="9ac1f-132">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-132">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="9ac1f-133">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="9ac1f-133">Request headers</span></span>

<span data-ttu-id="9ac1f-134">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9ac1f-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9ac1f-135">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="9ac1f-135">Request body</span></span>

<span data-ttu-id="9ac1f-136">Os detalhes do pedido de inventário, constituído por um recurso [InventoryCheckRequest](product-resources.md#inventorycheckrequest) contendo um ou mais recursos [do InventárioItem.](product-resources.md#inventoryitem)</span><span class="sxs-lookup"><span data-stu-id="9ac1f-136">The inventory request details, consisting of an [InventoryCheckRequest](product-resources.md#inventorycheckrequest) resource containing one or more [InventoryItem](product-resources.md#inventoryitem) resources.</span></span>

### <a name="request-example"></a><span data-ttu-id="9ac1f-137">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="9ac1f-137">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/extensions/product/checkinventory?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: d1b1981a-e088-4610-870a-eebec96d6bcd
MS-CorrelationId: 4acb26a1-3536-4081-bc7d-092869a4961a
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json

{"TargetItems":[{"ProductId":"DZH318Z0BQ3P"}],"InventoryContext":{"customerId":"d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d","azureSubscriptionId":"3A231FBE-37FE-4410-93FD-730D3D5D4C75","armRegionName":"Europe"}}
```

## <a name="rest-response"></a><span data-ttu-id="9ac1f-138">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="9ac1f-138">REST response</span></span>

<span data-ttu-id="9ac1f-139">Se for bem sucedido, o corpo de resposta contém uma coleção de objetos [InventoryItem](product-resources.md#inventoryitem) povoados com os detalhes da restrição, se algum for aplicável.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-139">If successful, the response body contains a collection of [InventoryItem](product-resources.md#inventoryitem) objects populated with the restriction details, if any apply.</span></span>

>[!NOTE]
><span data-ttu-id="9ac1f-140">Se uma entrada InventoryItem representar um item que não foi encontrado no catálogo, não será incluído na coleção de saída.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-140">If an input InventoryItem represents an item that could not be found in the catalog, it will not be included in the output collection.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9ac1f-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="9ac1f-141">Response success and error codes</span></span>

<span data-ttu-id="9ac1f-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9ac1f-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="9ac1f-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9ac1f-144">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="9ac1f-144">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9ac1f-145">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="9ac1f-145">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1021
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4acb26a1-3536-4081-bc7d-092869a4961a
MS-RequestId: d1b1981a-e088-4610-870a-eebec96d6bcd
X-Locale: en-US
[
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "0039",
        "isRestricted": true,
        "restrictions": [
            {
                "reasonCode": "NotAvailableForSubscription",
                "description": "Restriction identified of type 'Location' with values 'japanwest'.",
                "properties": {
                    "type": "Location",
                    "values": "japanwest"
                }
            }
        ]
    },
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "0038",
        "isRestricted": true,
        "restrictions": [
            {
                "reasonCode": "NotAvailableForSubscription",
                "description": "Restriction identified of type 'Location' with values 'japanwest'.",
                "properties": {
                    "type": "Location",
                    "values": "japanwest"
                }
            }
        ]
    },
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "000S",
        "isRestricted": false,
        "restrictions": []
    },
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "0011",
        "isRestricted": false,
        "restrictions": []
    }
]
```
