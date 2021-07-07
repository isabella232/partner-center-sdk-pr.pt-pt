---
title: Obter oferta por ID
description: Obtém um recurso de Oferta que corresponda ao ID da oferta.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: brentserbus
ms.author: brserbus
ms.openlocfilehash: f759cbdeefb4f550c41b41de40e9979e72e4ddeb
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760645"
---
# <a name="get-an-offer-by-id"></a><span data-ttu-id="790c7-103">Obter oferta por ID</span><span class="sxs-lookup"><span data-stu-id="790c7-103">Get an offer by ID</span></span>

<span data-ttu-id="790c7-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="790c7-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="790c7-105">Obtém um recurso **de Oferta** que corresponda ao ID da oferta.</span><span class="sxs-lookup"><span data-stu-id="790c7-105">Gets an **Offer** resource that matches the offer ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="790c7-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="790c7-106">Prerequisites</span></span>

- <span data-ttu-id="790c7-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="790c7-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="790c7-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="790c7-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="790c7-109">Uma identificação de oferta.</span><span class="sxs-lookup"><span data-stu-id="790c7-109">An offer ID.</span></span>

## <a name="c"></a><span data-ttu-id="790c7-110">C\#</span><span class="sxs-lookup"><span data-stu-id="790c7-110">C\#</span></span>

<span data-ttu-id="790c7-111">Para encontrar uma oferta específica por ID, use a sua coleção **IAggregatePartner.Offers,** estabeleça o país com uma chamada para **ByCountry()** e, em seguida, ligue para o método [**ByID().**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="790c7-111">To find a specific offer by ID, use your **IAggregatePartner.Offers** collection, establish the country with a call to **ByCountry()**, and then call the [**ByID()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid) method.</span></span> <span data-ttu-id="790c7-112">Em seguida, ligue para o método [**Get()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.get) ou [**Get Async().**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="790c7-112">Then, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.get) or [**Get Async()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.getasync) method.</span></span>

```csharp
// IAggretagePartner partnerOperations;
// string countryCode;
// string offerId;

// retrieve the offer
var offer = partnerOperations.Offers.ByCountry(countryCode).ById(offerId).Get();
```

<span data-ttu-id="790c7-113">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="790c7-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="790c7-114">**Project**: PartnerSDK.FeatureSample **Class**: GetOffer.cs</span><span class="sxs-lookup"><span data-stu-id="790c7-114">**Project**: PartnerSDK.FeatureSample **Class**: GetOffer.cs</span></span>

## <a name="java"></a><span data-ttu-id="790c7-115">Java</span><span class="sxs-lookup"><span data-stu-id="790c7-115">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="790c7-116">Para encontrar uma oferta específica por ID, use a sua função **IAggregatePartner.getOffers,** estabeleça o país com uma chamada para a função **byCountry()** e, em seguida, ligue para a função **byID().**</span><span class="sxs-lookup"><span data-stu-id="790c7-116">To find a specific offer by ID, use your **IAggregatePartner.getOffers** function, establish the country with a call to the **byCountry()** function, and then call the **byID()** function.</span></span> <span data-ttu-id="790c7-117">Em seguida, ligue para a função **get().**</span><span class="sxs-lookup"><span data-stu-id="790c7-117">Then call the **get()** function.</span></span>

```java
// IAggretagePartner partnerOperations;
// String countryCode;
// String offerId;

// Retrieve the offer
Offer offer = partnerOperations.getOffers().byCountry(countryCode).byId(offerId).get();
```

## <a name="powershell"></a><span data-ttu-id="790c7-118">PowerShell</span><span class="sxs-lookup"><span data-stu-id="790c7-118">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="790c7-119">Para encontrar uma oferta específica por ID, execute o comando [**Get-PartnerOffer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOffer.md) e especifique os parâmetros **CountryCode** e **OfferId.**</span><span class="sxs-lookup"><span data-stu-id="790c7-119">To find a specific offer by ID, execute the [**Get-PartnerOffer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOffer.md) command, and specify the **CountryCode** and **OfferId** parameters.</span></span>

```powershell
# $countryCode
# $offerId

Get-PartnerOffer -Country $countryCode -OfferId $offerId
```

## <a name="rest-request"></a><span data-ttu-id="790c7-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="790c7-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="790c7-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="790c7-121">Request syntax</span></span>

| <span data-ttu-id="790c7-122">Método</span><span class="sxs-lookup"><span data-stu-id="790c7-122">Method</span></span>  | <span data-ttu-id="790c7-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="790c7-123">Request URI</span></span>                                                                                    |
|---------|------------------------------------------------------------------------------------------------|
| <span data-ttu-id="790c7-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="790c7-124">**GET**</span></span> | <span data-ttu-id="790c7-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}?country={country-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="790c7-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}?country={country-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="790c7-126">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="790c7-126">URI parameter</span></span>

| <span data-ttu-id="790c7-127">Nome</span><span class="sxs-lookup"><span data-stu-id="790c7-127">Name</span></span>           | <span data-ttu-id="790c7-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="790c7-128">Type</span></span>       | <span data-ttu-id="790c7-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="790c7-129">Required</span></span> | <span data-ttu-id="790c7-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="790c7-130">Description</span></span>                           |
|----------------|------------|----------|---------------------------------------|
| <span data-ttu-id="790c7-131">**oferta id**</span><span class="sxs-lookup"><span data-stu-id="790c7-131">**offer-id**</span></span>   | <span data-ttu-id="790c7-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="790c7-132">**guid**</span></span>   | <span data-ttu-id="790c7-133">Y</span><span class="sxs-lookup"><span data-stu-id="790c7-133">Y</span></span>        | <span data-ttu-id="790c7-134">Um GUID que corresponda à oferta.</span><span class="sxs-lookup"><span data-stu-id="790c7-134">A GUID that corresponds to the offer.</span></span> |
| <span data-ttu-id="790c7-135">**país id**</span><span class="sxs-lookup"><span data-stu-id="790c7-135">**country-id**</span></span> | <span data-ttu-id="790c7-136">**string**</span><span class="sxs-lookup"><span data-stu-id="790c7-136">**string**</span></span> | <span data-ttu-id="790c7-137">Y</span><span class="sxs-lookup"><span data-stu-id="790c7-137">Y</span></span>        | <span data-ttu-id="790c7-138">O ID do país/região.</span><span class="sxs-lookup"><span data-stu-id="790c7-138">The country/region ID.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="790c7-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="790c7-139">Request headers</span></span>

- <span data-ttu-id="790c7-140">É necessário **um local formatoformado** como uma corda.</span><span class="sxs-lookup"><span data-stu-id="790c7-140">A **locale-id** formatted as a string is required.</span></span>
<span data-ttu-id="790c7-141">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="790c7-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="790c7-142">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="790c7-142">Request body</span></span>

<span data-ttu-id="790c7-143">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="790c7-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="790c7-144">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="790c7-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offers/<offer-id>?country=<country-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
X-Locale: <locale-id>
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="790c7-145">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="790c7-145">REST response</span></span>

<span data-ttu-id="790c7-146">Se for bem sucedido, este método devolve um recurso **de Oferta** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="790c7-146">If successful, this method returns an **Offer** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="790c7-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="790c7-147">Response success and error codes</span></span>

<span data-ttu-id="790c7-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="790c7-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="790c7-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="790c7-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="790c7-150">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="790c7-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="790c7-151">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="790c7-151">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1918
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
Date: Mon, 23 Nov 2015 23:13:01 GMT

{
    "id": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "name": "Office 365 Business Premium",
    "description": "For businesses with 1 to 300 users that need the latest desktop version of Office,
                    plus anywhere access to email, filesharing, and online conferencing.",
    "minimumQuantity": 1,
    "maximumQuantity": 300,
    "rank": 56,
    "uri": "/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/031C9E47-4802-4248-838E-778FB1D2CC05",
    "locale": "en-us",
    "country": "US",
    "category": {
        "id": "SmallBusiness_Key",
        "name": "Small Business",
        "rank": 30,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    "prerequisiteOffers": [],
    "isAddOn": false,
    "isAvailableForPurchase": true,
    "billing": "license",
    "isAutoRenewable": true,
    "product": {
        "id": "f245ecc8-75af-4f8e-b61f-27d8114de5f3",
        "name": "Office 365 Business Premium",
        "unit": "Licenses"
    },
    "unitType": "Licenses",
    "links": {
        "learnMore": {
            "uri": "http: //g.microsoftonline.com/0BXPS00en/909",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Offer"
    }
}
```
