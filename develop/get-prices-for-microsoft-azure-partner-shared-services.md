---
title: Obter preços do Microsoft Azure Partner Shared Services
description: Como obter um Cartão Azure Rate com preços para Microsoft Azure Serviços Partilhados de Parceiros.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0008d7474f7e57bbbd765afdf2487ee279848ac3
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548809"
---
# <a name="get-prices-for-microsoft-azure-partner-shared-services"></a><span data-ttu-id="be991-103">Obter preços do Microsoft Azure Partner Shared Services</span><span class="sxs-lookup"><span data-stu-id="be991-103">Get prices for Microsoft Azure Partner Shared Services</span></span>

<span data-ttu-id="be991-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="be991-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="be991-105">Como obter um [Cartão Azure Rate](azure-rate-card-resources.md) com preços para Microsoft Azure Serviços Partilhados de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="be991-105">How to get an [Azure Rate Card](azure-rate-card-resources.md) with prices for Microsoft Azure Partner Shared Services.</span></span>

<span data-ttu-id="be991-106">Os preços diferem por mercado e por moeda, e esta API tem em conta a localização.</span><span class="sxs-lookup"><span data-stu-id="be991-106">Prices differ by market and currency, and this API takes location into consideration.</span></span> <span data-ttu-id="be991-107">Por padrão, a API utiliza as definições de perfil do seu parceiro no Partner Center e no seu idioma do navegador, e essas definições são personalizáveis.</span><span class="sxs-lookup"><span data-stu-id="be991-107">By default, the API uses your partner profile settings in Partner Center and your browser language, and those settings are customizable.</span></span> <span data-ttu-id="be991-108">A consciência da localização é especialmente relevante se você gerir vendas em vários mercados a partir de um único escritório centralizado.</span><span class="sxs-lookup"><span data-stu-id="be991-108">The location awareness is especially relevant if you manage sales in multiple markets from a single, centralized office.</span></span>

## <a name="example-code"></a><span data-ttu-id="be991-109">Código exemplo</span><span class="sxs-lookup"><span data-stu-id="be991-109">Example Code</span></span>

## <a name="c"></a><span data-ttu-id="be991-110">C\#</span><span class="sxs-lookup"><span data-stu-id="be991-110">C\#</span></span>

<span data-ttu-id="be991-111">Para obter o Cartão Azure Rate, ligue para o método [**IAzureRateCard.GetShared**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.getshared) para devolver um recurso [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) que contenha os preços Azure.</span><span class="sxs-lookup"><span data-stu-id="be991-111">To obtain the Azure Rate Card, call the [**IAzureRateCard.GetShared**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.getshared) method to return an [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) resource that contains the Azure prices.</span></span>

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.GetShared();
```

## <a name="java"></a><span data-ttu-id="be991-112">Java</span><span class="sxs-lookup"><span data-stu-id="be991-112">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="be991-113">Para obter o Cartão Azure Rate, ligue para a função **IAzureRateCard.getPartimento** para devolver detalhes do cartão de retorno que contenham os preços do Azure.</span><span class="sxs-lookup"><span data-stu-id="be991-113">To obtain the Azure Rate Card, call the **IAzureRateCard.getShared** function to return rate card details that contains the Azure prices.</span></span>

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().getShared();
```

## <a name="powershell"></a><span data-ttu-id="be991-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="be991-114">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="be991-115">Para obter o Cartão Azure, execute o comando [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) e especifique o parâmetro **SharedServices** para devolver detalhes do cartão de retorno que contenham os preços do Azure.</span><span class="sxs-lookup"><span data-stu-id="be991-115">To obtain the Azure Card, execute the [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) command and specify the **SharedServices** parameter to return rate card details that contains the Azure prices.</span></span>

```powershell
Get-PartnerAzureRateCard -SharedServices
```

## <a name="rest-request"></a><span data-ttu-id="be991-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="be991-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="be991-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="be991-117">Request syntax</span></span>

| <span data-ttu-id="be991-118">Método</span><span class="sxs-lookup"><span data-stu-id="be991-118">Method</span></span>  | <span data-ttu-id="be991-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="be991-119">Request URI</span></span>                                                               |
|---------|---------------------------------------------------------------------------|
| <span data-ttu-id="be991-120">**Obter**</span><span class="sxs-lookup"><span data-stu-id="be991-120">**GET**</span></span> | <span data-ttu-id="be991-121">*{baseURL}*/v1/ratecards/azure-shared?currency={currency}&região={região}</span><span class="sxs-lookup"><span data-stu-id="be991-121">*{baseURL}*/v1/ratecards/azure-shared?currency={currency}&region={region}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="be991-122">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="be991-122">URI parameters</span></span>

| <span data-ttu-id="be991-123">Nome</span><span class="sxs-lookup"><span data-stu-id="be991-123">Name</span></span>     | <span data-ttu-id="be991-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="be991-124">Type</span></span>   | <span data-ttu-id="be991-125">Necessário</span><span class="sxs-lookup"><span data-stu-id="be991-125">Required</span></span> | <span data-ttu-id="be991-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="be991-126">Description</span></span>                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="be991-127">moeda</span><span class="sxs-lookup"><span data-stu-id="be991-127">currency</span></span> | <span data-ttu-id="be991-128">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="be991-128">string</span></span> | <span data-ttu-id="be991-129">No</span><span class="sxs-lookup"><span data-stu-id="be991-129">No</span></span>       | <span data-ttu-id="be991-130">Código ISO de três letras opcionais para a moeda em que serão fornecidas as taxas de recursos (por `EUR` exemplo).</span><span class="sxs-lookup"><span data-stu-id="be991-130">Optional three letter ISO code for the currency in which the resource rates will be provided (for example `EUR`).</span></span> <span data-ttu-id="be991-131">O padrão é a moeda associada ao mercado no perfil do parceiro.</span><span class="sxs-lookup"><span data-stu-id="be991-131">The default is the currency associated with the market in the partner profile.</span></span> |
| <span data-ttu-id="be991-132">region</span><span class="sxs-lookup"><span data-stu-id="be991-132">region</span></span>   | <span data-ttu-id="be991-133">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="be991-133">string</span></span> | <span data-ttu-id="be991-134">No</span><span class="sxs-lookup"><span data-stu-id="be991-134">No</span></span>       | <span data-ttu-id="be991-135">Código opcional iso país/região de duas letras que indica o mercado onde a oferta é adquirida (por `FR` exemplo).</span><span class="sxs-lookup"><span data-stu-id="be991-135">Optional two-letter ISO country/region code that indicates the market where the offer is purchased (for example `FR`).</span></span> <span data-ttu-id="be991-136">O padrão é o código país/região definido no perfil do parceiro.</span><span class="sxs-lookup"><span data-stu-id="be991-136">The default is the country/region code set in the partner profile.</span></span>        |

<span data-ttu-id="be991-137">Se o cabeçalho X-Locale opcional estiver incluído no pedido, o seu valor determina o idioma utilizado para os detalhes na resposta.</span><span class="sxs-lookup"><span data-stu-id="be991-137">If the optional X-Locale header is included in the request, its value determines the language used for the details in the response.</span></span>

### <a name="request-headers"></a><span data-ttu-id="be991-138">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="be991-138">Request headers</span></span>

<span data-ttu-id="be991-139">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="be991-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="be991-140">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="be991-140">Request body</span></span>

<span data-ttu-id="be991-141">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="be991-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="be991-142">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="be991-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/ratecards/azure-shared HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07ced227-3f32-4eeb-8062-f0bef849a9bc
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="be991-143">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="be991-143">REST response</span></span>

<span data-ttu-id="be991-144">Se o pedido for bem sucedido, devolve um recurso [de Cartão Azure Rate.](azure-rate-card-resources.md)</span><span class="sxs-lookup"><span data-stu-id="be991-144">If the request is successful, it returns an [Azure Rate Card](azure-rate-card-resources.md) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="be991-145">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="be991-145">Response success and error codes</span></span>

<span data-ttu-id="be991-146">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="be991-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="be991-147">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="be991-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="be991-148">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="be991-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="be991-149">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="be991-149">Response example</span></span>

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
    "locale": "en-US",
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
