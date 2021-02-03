---
title: Obter preços do Microsoft Azure
description: Como obter um Cartão Azure Rate com preços em tempo real para uma oferta Azure. Os preços do Azure são bastante dinâmicos e mudam frequentemente.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0716f0428b13604105b435a2ce8287a8b4609fea
ms.sourcegitcommit: 64c498d3571f2287305968890578bc7396779621
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2020
ms.locfileid: "97770295"
---
# <a name="get-prices-for-microsoft-azure"></a><span data-ttu-id="d7711-104">Obter preços do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="d7711-104">Get prices for Microsoft Azure</span></span>

<span data-ttu-id="d7711-105">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="d7711-105">**Applies To**</span></span>

- <span data-ttu-id="d7711-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="d7711-106">Partner Center</span></span>
- <span data-ttu-id="d7711-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="d7711-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="d7711-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d7711-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d7711-109">Como obter um [Cartão Azure Rate](azure-rate-card-resources.md) com preços em tempo real para uma oferta Azure.</span><span class="sxs-lookup"><span data-stu-id="d7711-109">How to get an [Azure Rate Card](azure-rate-card-resources.md) with real-time prices for an Azure offer.</span></span> <span data-ttu-id="d7711-110">Os preços do Azure são bastante dinâmicos e mudam frequentemente.</span><span class="sxs-lookup"><span data-stu-id="d7711-110">Azure pricing is quite dynamic and changes frequently.</span></span>

<span data-ttu-id="d7711-111">Para acompanhar o uso e ajudar a prever a sua fatura mensal e as contas para clientes individuais, pode combinar esta consulta do Azure Rate Card para obter preços para o Microsoft Azure com um pedido para [obter os registos de utilização de um cliente para o Azure.](get-a-customer-s-utilization-record-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="d7711-111">To track usage and help predict your monthly bill and the bills for individual customers, you can combine this Azure Rate Card query to get prices for Microsoft Azure with a request to [Get a customer's utilization records for Azure](get-a-customer-s-utilization-record-for-azure.md).</span></span>

<span data-ttu-id="d7711-112">Os preços diferem por mercado e por moeda, e esta API tem em conta a localização.</span><span class="sxs-lookup"><span data-stu-id="d7711-112">Prices differ by market and currency, and this API takes location into consideration.</span></span> <span data-ttu-id="d7711-113">Por padrão, a API utiliza as definições de perfil do seu parceiro no Partner Center e no seu idioma do navegador, e essas definições são personalizáveis.</span><span class="sxs-lookup"><span data-stu-id="d7711-113">By default, the API uses your partner profile settings in Partner Center and your browser language, and those settings are customizable.</span></span> <span data-ttu-id="d7711-114">A consciência da localização é especialmente relevante se você gerir vendas em vários mercados a partir de um único escritório centralizado.</span><span class="sxs-lookup"><span data-stu-id="d7711-114">The location awareness is especially relevant if you manage sales in multiple markets from a single, centralized office.</span></span> <span data-ttu-id="d7711-115">Para obter mais informações, consulte [os parâmetros URI.](#uri-parameters)</span><span class="sxs-lookup"><span data-stu-id="d7711-115">For more information, see [URI parameters](#uri-parameters).</span></span>

## <a name="c"></a><span data-ttu-id="d7711-116">C\#</span><span class="sxs-lookup"><span data-stu-id="d7711-116">C\#</span></span>

<span data-ttu-id="d7711-117">Para obter o Cartão Azure Rate, ligue para o método [**IAzureRateCard.Get**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.get) para devolver um recurso [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) que contenha os preços Azure.</span><span class="sxs-lookup"><span data-stu-id="d7711-117">To obtain the Azure Rate Card, call the [**IAzureRateCard.Get**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.get) method to return an [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) resource that contains the Azure prices.</span></span>

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.Get();
```

<span data-ttu-id="d7711-118">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d7711-118">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d7711-119">**Projeto**: Partner Center SDK Samples **Class**: GetAzureRateCard.cs</span><span class="sxs-lookup"><span data-stu-id="d7711-119">**Project**: Partner Center SDK Samples **Class**: GetAzureRateCard.cs</span></span>

## <a name="java"></a><span data-ttu-id="d7711-120">Java</span><span class="sxs-lookup"><span data-stu-id="d7711-120">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="d7711-121">Para obter o Cartão Azure Rate, ligue para o **IAzureRateCard.obter** função para devolver detalhes do cartão de retorno que contenham os preços do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7711-121">To obtain the Azure Rate Card, call the **IAzureRateCard.get** function to return rate card details that contains the Azure prices.</span></span>

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().get();
```

## <a name="powershell"></a><span data-ttu-id="d7711-122">PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7711-122">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="d7711-123">Para obter o Cartão Azure, execute o comando [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) para devolver os detalhes do cartão de retorno que contenham os preços do Azure.</span><span class="sxs-lookup"><span data-stu-id="d7711-123">To obtain the Azure Card, execute the [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) command to return rate card details that contains the Azure prices.</span></span>

```powershell
Get-PartnerAzureRateCard
```

## <a name="rest-request"></a><span data-ttu-id="d7711-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d7711-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d7711-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7711-125">Request syntax</span></span>

| <span data-ttu-id="d7711-126">Método</span><span class="sxs-lookup"><span data-stu-id="d7711-126">Method</span></span>  | <span data-ttu-id="d7711-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d7711-127">Request URI</span></span>                                                        |
|---------|--------------------------------------------------------------------|
| <span data-ttu-id="d7711-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d7711-128">**GET**</span></span> | <span data-ttu-id="d7711-129">*{baseURL}*/v1/ratecards/azure?currency={currency}&região={região}</span><span class="sxs-lookup"><span data-stu-id="d7711-129">*{baseURL}*/v1/ratecards/azure?currency={currency}&region={region}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="d7711-130">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="d7711-130">URI parameters</span></span>

| <span data-ttu-id="d7711-131">Nome</span><span class="sxs-lookup"><span data-stu-id="d7711-131">Name</span></span>     | <span data-ttu-id="d7711-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="d7711-132">Type</span></span>   | <span data-ttu-id="d7711-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="d7711-133">Required</span></span> | <span data-ttu-id="d7711-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7711-134">Description</span></span>                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d7711-135">moeda</span><span class="sxs-lookup"><span data-stu-id="d7711-135">currency</span></span> | <span data-ttu-id="d7711-136">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="d7711-136">string</span></span> | <span data-ttu-id="d7711-137">No</span><span class="sxs-lookup"><span data-stu-id="d7711-137">No</span></span>       | <span data-ttu-id="d7711-138">Código ISO de três letras opcionais para a moeda em que serão fornecidas as taxas de recursos (por `EUR` exemplo).</span><span class="sxs-lookup"><span data-stu-id="d7711-138">Optional three letter ISO code for the currency in which the resource rates will be provided (for example `EUR`).</span></span> <span data-ttu-id="d7711-139">A predefinição é `USD`.</span><span class="sxs-lookup"><span data-stu-id="d7711-139">The default is `USD`.</span></span> |
| <span data-ttu-id="d7711-140">region</span><span class="sxs-lookup"><span data-stu-id="d7711-140">region</span></span>   | <span data-ttu-id="d7711-141">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="d7711-141">string</span></span> | <span data-ttu-id="d7711-142">No</span><span class="sxs-lookup"><span data-stu-id="d7711-142">No</span></span>       | <span data-ttu-id="d7711-143">Código opcional iso país/região de duas letras que indica o mercado onde a oferta é adquirida (por `FR` exemplo).</span><span class="sxs-lookup"><span data-stu-id="d7711-143">Optional two-letter ISO country/region code that indicates the market where the offer is purchased (for example `FR`).</span></span> <span data-ttu-id="d7711-144">A predefinição é `US`.</span><span class="sxs-lookup"><span data-stu-id="d7711-144">The default is `US`.</span></span>        |

<span data-ttu-id="d7711-145">Pode incluir o [cabeçalho](headers.md#rest-request-headers) X-Locale opcional no seu pedido.</span><span class="sxs-lookup"><span data-stu-id="d7711-145">You can include the optional X-Locale [header](headers.md#rest-request-headers) in your request.</span></span> <span data-ttu-id="d7711-146">Se não incluir o cabeçalho X-Locale, o valor predefinido ("en-US") é utilizado.</span><span class="sxs-lookup"><span data-stu-id="d7711-146">If you don't include the X-Locale header, the default value ("en-US") is used.</span></span>

- <span data-ttu-id="d7711-147">Se fornecer parâmetros de moeda e região no seu pedido, o valor do X-Locale é usado para determinar a linguagem da resposta.</span><span class="sxs-lookup"><span data-stu-id="d7711-147">If you provide currency and region parameters in your request, the value of X-Locale is used to determine the response's language.</span></span>

- <span data-ttu-id="d7711-148">Se não fornecer parâmetros de região e moeda no seu pedido, o valor do X-Locale é usado para determinar a região, a moeda e a língua da resposta.</span><span class="sxs-lookup"><span data-stu-id="d7711-148">If you don't provide region and currency parameters in your request, the value of X-Locale is used to determine the response's region, currency, and language.</span></span>

### <a name="request-header"></a><span data-ttu-id="d7711-149">Cabeçalho do pedido</span><span class="sxs-lookup"><span data-stu-id="d7711-149">Request header</span></span>

<span data-ttu-id="d7711-150">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d7711-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d7711-151">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d7711-151">Request body</span></span>

<span data-ttu-id="d7711-152">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d7711-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d7711-153">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d7711-153">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/ratecards/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07ced227-3f32-4eeb-8062-f0bef849a9bc
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="d7711-154">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d7711-154">REST response</span></span>

<span data-ttu-id="d7711-155">Se o pedido for bem sucedido, devolve um recurso [de Cartão Azure Rate.](azure-rate-card-resources.md)</span><span class="sxs-lookup"><span data-stu-id="d7711-155">If the request is successful, it returns an [Azure Rate Card](azure-rate-card-resources.md) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d7711-156">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d7711-156">Response success and error codes</span></span>

<span data-ttu-id="d7711-157">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d7711-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d7711-158">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d7711-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d7711-159">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d7711-159">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d7711-160">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d7711-160">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1545508
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57b25659-fc00-4215-87e7-2b09bac6845d
MS-RequestId: 870118d0-adbb-41a3-82d2-a3d45ade3c73
MS-CV: CYBB8PXMsEukJBIn.0
MS-ServerId: 201021413
Date: Wed, 01 Feb 2017 00:13:45 GMT

{
    "locale": "en",
    "currency": "USD",
    "isTaxIncluded": false,
    "meters": [{
            "id": "4b836326-7e19-46e6-8bce-1b19bb6cd91e",
            "name": "Unlimited Data - 1 Gbps",
            "rates": {
                "0": 7395.0
            },
            "tags": [],
            "category": "Networking",
            "subcategory": "ExpressRoute",
            "region": "Zone 2",
            "unit": "Connections",
            "includedQuantity": 0.0,
            "effectiveDate": "2015-09-01T00:00:00Z"
        }, {
            "id": "1e8f6d9f-8b40-4c97-80cc-cff87a290a93",
            "name": "Compute Hours",
            "rates": {
                "0": 3.9729
            },
            "tags": [],
            "category": "Cloud Services",
            "subcategory": "Standard_L16 Cloud Services",
            "region": "AU East",
            "unit": "1 Hour",
            "includedQuantity": 0.0,
            "effectiveDate": "2016-09-01T00:00:00Z"
        }, {
            "id": "7a2639ce-ae47-4413-9837-6b4f4b78be3d",
            "name": "Compute Hours",
            "rates": {
                "0": 0.1122
            },
            "tags": [],
            "category": "Virtual Machines",
            "subcategory": "Standard_D1_v2 VM (Windows)",
            "region": "BR South",
            "unit": "Hours",
            "includedQuantity": 0.0,
            "effectiveDate": "2017-01-01T00:00:00Z"
        }
    ],
    "offerTerms": [{
            "name": "Overage discount",
            "discount": 0.15,
            "excludedMeterIds": ["53cc0061-0fe2-4249-bf62-e1008c811f5c", "c82dbd27-c978-43a7-ad41-525a90d8962b"],
            "effectiveDate": "2014-01-01T00:00:00"
        }
    ],
    "attributes": {
        "objectType": "AzureRateCard"
    }
}
```
