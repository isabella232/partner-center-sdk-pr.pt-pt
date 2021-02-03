---
title: Verifique o inventário
description: Saiba como usar as APIs do Partner Center para verificar o inventário para obter um conjunto específico de itens de catálogo. Pode fazê-lo para identificar os produtos de um cliente ou SKUs.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6921760abc0b95aff820467e84b3e8e9435731cd
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770087"
---
# <a name="check-the-inventory-of-catalog-items-using-partner-center-apis"></a><span data-ttu-id="18ca4-104">Verifique o inventário de itens de catálogo usando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="18ca4-104">Check the inventory of catalog items using Partner Center APIs</span></span>

<span data-ttu-id="18ca4-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="18ca4-105">**Applies to:**</span></span>

- <span data-ttu-id="18ca4-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="18ca4-106">Partner Center</span></span>

<span data-ttu-id="18ca4-107">Como verificar o inventário para obter um conjunto específico de itens de catálogo.</span><span class="sxs-lookup"><span data-stu-id="18ca4-107">How to check the inventory for a specific set of catalog items.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18ca4-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="18ca4-108">Prerequisites</span></span>

- <span data-ttu-id="18ca4-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="18ca4-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="18ca4-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="18ca4-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="18ca4-111">Uma ou mais identificações de produtos.</span><span class="sxs-lookup"><span data-stu-id="18ca4-111">One or more product IDs.</span></span> <span data-ttu-id="18ca4-112">Opcionalmente, os IDs SKU também podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="18ca4-112">Optionally, SKU IDs can also be specified.</span></span>

- <span data-ttu-id="18ca4-113">Qualquer contexto adicional necessário para verificar o inventário dos SKU(s) referenciados pelo produto fornecido/SKU ID(s).</span><span class="sxs-lookup"><span data-stu-id="18ca4-113">Any additional context needed for verifying the inventory of the SKU(s) referenced by the provided product/SKU ID(s).</span></span> <span data-ttu-id="18ca4-114">Estes requisitos podem variar por tipo de produto/SKU e podem ser determinados a partir da propriedade [Da SKU's](product-resources.md#sku) **InventoryVariables.**</span><span class="sxs-lookup"><span data-stu-id="18ca4-114">These requirements may vary by type of product/SKU and can be determined from the [SKU's](product-resources.md#sku) **InventoryVariables** property.</span></span>

## <a name="c"></a><span data-ttu-id="18ca4-115">C\#</span><span class="sxs-lookup"><span data-stu-id="18ca4-115">C\#</span></span>

<span data-ttu-id="18ca4-116">Para verificar o inventário, construa um objeto [InventoryCheckRequest](product-resources.md#inventorycheckrequest) utilizando um objeto [InventoryItem](product-resources.md#inventoryitem) para cada item a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="18ca4-116">To check the inventory, build an [InventoryCheckRequest](product-resources.md#inventorycheckrequest) object using an [InventoryItem](product-resources.md#inventoryitem) object for each item to be checked.</span></span> <span data-ttu-id="18ca4-117">Em seguida, utilize um acessório **IAggregatePartner.Extensions,** passe-o para **o Produto** e, em seguida, selecione o país utilizando o método **ByCountry().**</span><span class="sxs-lookup"><span data-stu-id="18ca4-117">Then, use an **IAggregatePartner.Extensions** accessor, scope it down to **Product** and then select the country using the **ByCountry()** method.</span></span> <span data-ttu-id="18ca4-118">Por fim, ligue para o método **CheckInventory()** com o seu objeto **InventoryCheckRequest.**</span><span class="sxs-lookup"><span data-stu-id="18ca4-118">Finally, call the **CheckInventory()** method with your **InventoryCheckRequest** object.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="18ca4-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="18ca4-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="18ca4-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="18ca4-120">Request syntax</span></span>

| <span data-ttu-id="18ca4-121">Método</span><span class="sxs-lookup"><span data-stu-id="18ca4-121">Method</span></span>   | <span data-ttu-id="18ca4-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="18ca4-122">Request URI</span></span>                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="18ca4-123">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="18ca4-123">**POST**</span></span> | <span data-ttu-id="18ca4-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/extensions/product/checkInventory?country={country-code} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="18ca4-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/extensions/product/checkInventory?country={country-code} HTTP/1.1</span></span>                        |

### <a name="uri-parameter"></a><span data-ttu-id="18ca4-125">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="18ca4-125">URI parameter</span></span>

<span data-ttu-id="18ca4-126">Utilize o seguinte parâmetro de consulta para verificar o inventário.</span><span class="sxs-lookup"><span data-stu-id="18ca4-126">Use the following query parameter to check the inventory.</span></span>

| <span data-ttu-id="18ca4-127">Nome</span><span class="sxs-lookup"><span data-stu-id="18ca4-127">Name</span></span>                   | <span data-ttu-id="18ca4-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="18ca4-128">Type</span></span>     | <span data-ttu-id="18ca4-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="18ca4-129">Required</span></span> | <span data-ttu-id="18ca4-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="18ca4-130">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="18ca4-131">código de país</span><span class="sxs-lookup"><span data-stu-id="18ca4-131">country-code</span></span>           | <span data-ttu-id="18ca4-132">string</span><span class="sxs-lookup"><span data-stu-id="18ca4-132">string</span></span>   | <span data-ttu-id="18ca4-133">Sim</span><span class="sxs-lookup"><span data-stu-id="18ca4-133">Yes</span></span>      | <span data-ttu-id="18ca4-134">Uma identificação país/região.</span><span class="sxs-lookup"><span data-stu-id="18ca4-134">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="18ca4-135">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="18ca4-135">Request headers</span></span>

<span data-ttu-id="18ca4-136">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="18ca4-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="18ca4-137">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="18ca4-137">Request body</span></span>

<span data-ttu-id="18ca4-138">Os detalhes do pedido de inventário, constituído por um recurso [InventoryCheckRequest](product-resources.md#inventorycheckrequest) contendo um ou mais recursos [do InventárioItem.](product-resources.md#inventoryitem)</span><span class="sxs-lookup"><span data-stu-id="18ca4-138">The inventory request details, consisting of an [InventoryCheckRequest](product-resources.md#inventorycheckrequest) resource containing one or more [InventoryItem](product-resources.md#inventoryitem) resources.</span></span>

### <a name="request-example"></a><span data-ttu-id="18ca4-139">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="18ca4-139">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="18ca4-140">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="18ca4-140">REST response</span></span>

<span data-ttu-id="18ca4-141">Se for bem sucedido, o corpo de resposta contém uma coleção de objetos [InventoryItem](product-resources.md#inventoryitem) povoados com os detalhes da restrição, se algum for aplicável.</span><span class="sxs-lookup"><span data-stu-id="18ca4-141">If successful, the response body contains a collection of [InventoryItem](product-resources.md#inventoryitem) objects populated with the restriction details, if any apply.</span></span>

>[!NOTE]
><span data-ttu-id="18ca4-142">Se uma entrada InventoryItem representar um item que não foi encontrado no catálogo, não será incluído na coleção de saída.</span><span class="sxs-lookup"><span data-stu-id="18ca4-142">If an input InventoryItem represents an item that could not be found in the catalog, it will not be included in the output collection.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="18ca4-143">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="18ca4-143">Response success and error codes</span></span>

<span data-ttu-id="18ca4-144">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="18ca4-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="18ca4-145">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="18ca4-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="18ca4-146">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="18ca4-146">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="18ca4-147">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="18ca4-147">Response example</span></span>

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
