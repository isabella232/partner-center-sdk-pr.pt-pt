---
title: Obter oferta por ID
description: Obtém um recurso de Oferta que corresponda ao ID da oferta.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: brentserbus
ms.author: brserbus
ms.openlocfilehash: 9448276e817affb823eddabbcab8757c79615fbd
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769908"
---
# <a name="get-an-offer-by-id"></a><span data-ttu-id="06fa7-103">Obter oferta por ID</span><span class="sxs-lookup"><span data-stu-id="06fa7-103">Get an offer by ID</span></span>

<span data-ttu-id="06fa7-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="06fa7-104">**Applies To**</span></span>

- <span data-ttu-id="06fa7-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="06fa7-105">Partner Center</span></span>
- <span data-ttu-id="06fa7-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="06fa7-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="06fa7-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="06fa7-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="06fa7-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="06fa7-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="06fa7-109">Obtém um recurso **de Oferta** que corresponda ao ID da oferta.</span><span class="sxs-lookup"><span data-stu-id="06fa7-109">Gets an **Offer** resource that matches the offer ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="06fa7-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="06fa7-110">Prerequisites</span></span>

- <span data-ttu-id="06fa7-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="06fa7-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="06fa7-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="06fa7-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="06fa7-113">Uma identificação de oferta.</span><span class="sxs-lookup"><span data-stu-id="06fa7-113">An offer ID.</span></span>

## <a name="c"></a><span data-ttu-id="06fa7-114">C\#</span><span class="sxs-lookup"><span data-stu-id="06fa7-114">C\#</span></span>

<span data-ttu-id="06fa7-115">Para encontrar uma oferta específica por ID, use a sua coleção **IAggregatePartner.Offers,** estabeleça o país com uma chamada para **ByCountry()** e, em seguida, ligue para o método [**ByID().**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="06fa7-115">To find a specific offer by ID, use your **IAggregatePartner.Offers** collection, establish the country with a call to **ByCountry()**, and then call the [**ByID()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid) method.</span></span> <span data-ttu-id="06fa7-116">Em seguida, ligue para o método [**Get()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.get) ou [**Get Async().**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="06fa7-116">Then, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.get) or [**Get Async()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.getasync) method.</span></span>

```csharp
// IAggretagePartner partnerOperations;
// string countryCode;
// string offerId;

// retrieve the offer
var offer = partnerOperations.Offers.ByCountry(countryCode).ById(offerId).Get();
```

<span data-ttu-id="06fa7-117">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="06fa7-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="06fa7-118">**Projeto**: PartnerSDK.FeatureSample **Class**: GetOffer.cs</span><span class="sxs-lookup"><span data-stu-id="06fa7-118">**Project**: PartnerSDK.FeatureSample **Class**: GetOffer.cs</span></span>

## <a name="java"></a><span data-ttu-id="06fa7-119">Java</span><span class="sxs-lookup"><span data-stu-id="06fa7-119">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="06fa7-120">Para encontrar uma oferta específica por ID, use a sua função **IAggregatePartner.getOffers,** estabeleça o país com uma chamada para a função **byCountry()** e, em seguida, ligue para a função **byID().**</span><span class="sxs-lookup"><span data-stu-id="06fa7-120">To find a specific offer by ID, use your **IAggregatePartner.getOffers** function, establish the country with a call to the **byCountry()** function, and then call the **byID()** function.</span></span> <span data-ttu-id="06fa7-121">Em seguida, ligue para a função **get().**</span><span class="sxs-lookup"><span data-stu-id="06fa7-121">Then call the **get()** function.</span></span>

```java
// IAggretagePartner partnerOperations;
// String countryCode;
// String offerId;

// Retrieve the offer
Offer offer = partnerOperations.getOffers().byCountry(countryCode).byId(offerId).get();
```

## <a name="powershell"></a><span data-ttu-id="06fa7-122">PowerShell</span><span class="sxs-lookup"><span data-stu-id="06fa7-122">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="06fa7-123">Para encontrar uma oferta específica por ID, execute o comando [**Get-PartnerOffer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOffer.md) e especifique os parâmetros **CountryCode** e **OfferId.**</span><span class="sxs-lookup"><span data-stu-id="06fa7-123">To find a specific offer by ID, execute the [**Get-PartnerOffer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOffer.md) command, and specify the **CountryCode** and **OfferId** parameters.</span></span>

```powershell
# $countryCode
# $offerId

Get-PartnerOffer -Country $countryCode -OfferId $offerId
```

## <a name="rest-request"></a><span data-ttu-id="06fa7-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="06fa7-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="06fa7-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="06fa7-125">Request syntax</span></span>

| <span data-ttu-id="06fa7-126">Método</span><span class="sxs-lookup"><span data-stu-id="06fa7-126">Method</span></span>  | <span data-ttu-id="06fa7-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="06fa7-127">Request URI</span></span>                                                                                    |
|---------|------------------------------------------------------------------------------------------------|
| <span data-ttu-id="06fa7-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="06fa7-128">**GET**</span></span> | <span data-ttu-id="06fa7-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}?country={country-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="06fa7-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}?country={country-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="06fa7-130">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="06fa7-130">URI parameter</span></span>

| <span data-ttu-id="06fa7-131">Nome</span><span class="sxs-lookup"><span data-stu-id="06fa7-131">Name</span></span>           | <span data-ttu-id="06fa7-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="06fa7-132">Type</span></span>       | <span data-ttu-id="06fa7-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="06fa7-133">Required</span></span> | <span data-ttu-id="06fa7-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="06fa7-134">Description</span></span>                           |
|----------------|------------|----------|---------------------------------------|
| <span data-ttu-id="06fa7-135">**oferta id**</span><span class="sxs-lookup"><span data-stu-id="06fa7-135">**offer-id**</span></span>   | <span data-ttu-id="06fa7-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="06fa7-136">**guid**</span></span>   | <span data-ttu-id="06fa7-137">Y</span><span class="sxs-lookup"><span data-stu-id="06fa7-137">Y</span></span>        | <span data-ttu-id="06fa7-138">Um GUID que corresponda à oferta.</span><span class="sxs-lookup"><span data-stu-id="06fa7-138">A GUID that corresponds to the offer.</span></span> |
| <span data-ttu-id="06fa7-139">**país id**</span><span class="sxs-lookup"><span data-stu-id="06fa7-139">**country-id**</span></span> | <span data-ttu-id="06fa7-140">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="06fa7-140">**string**</span></span> | <span data-ttu-id="06fa7-141">Y</span><span class="sxs-lookup"><span data-stu-id="06fa7-141">Y</span></span>        | <span data-ttu-id="06fa7-142">O ID do país/região.</span><span class="sxs-lookup"><span data-stu-id="06fa7-142">The country/region ID.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="06fa7-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="06fa7-143">Request headers</span></span>

- <span data-ttu-id="06fa7-144">É necessário **um local formatoformado** como uma corda.</span><span class="sxs-lookup"><span data-stu-id="06fa7-144">A **locale-id** formatted as a string is required.</span></span>
<span data-ttu-id="06fa7-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="06fa7-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="06fa7-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="06fa7-146">Request body</span></span>

<span data-ttu-id="06fa7-147">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="06fa7-147">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="06fa7-148">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="06fa7-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offers/<offer-id>?country=<country-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
X-Locale: <locale-id>
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="06fa7-149">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="06fa7-149">REST response</span></span>

<span data-ttu-id="06fa7-150">Se for bem sucedido, este método devolve um recurso **de Oferta** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="06fa7-150">If successful, this method returns an **Offer** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="06fa7-151">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="06fa7-151">Response success and error codes</span></span>

<span data-ttu-id="06fa7-152">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="06fa7-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="06fa7-153">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="06fa7-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="06fa7-154">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="06fa7-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="06fa7-155">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="06fa7-155">Response example</span></span>

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
