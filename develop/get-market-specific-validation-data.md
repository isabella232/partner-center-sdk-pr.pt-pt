---
title: Obter regras de formatação de endereços por mercado
description: Obtenha o formato de endereço esperado com base no código iso para o mercado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c755a38c11ed9803edb7777a0f661c1fbc5a6107
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769007"
---
# <a name="get-address-formatting-rules-by-market"></a><span data-ttu-id="905a4-103">Obter regras de formatação de endereços por mercado</span><span class="sxs-lookup"><span data-stu-id="905a4-103">Get address formatting rules by market</span></span>

<span data-ttu-id="905a4-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="905a4-104">**Applies To**</span></span>

- <span data-ttu-id="905a4-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="905a4-105">Partner Center</span></span>
- <span data-ttu-id="905a4-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="905a4-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="905a4-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="905a4-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="905a4-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="905a4-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="905a4-109">Obtenha o formato de endereço esperado com base no código iso para o mercado.</span><span class="sxs-lookup"><span data-stu-id="905a4-109">Get the expected address format based on the iso code for the market.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="905a4-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="905a4-110">Prerequisites</span></span>

- <span data-ttu-id="905a4-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="905a4-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="905a4-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="905a4-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="905a4-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="905a4-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="905a4-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="905a4-114">Request syntax</span></span>

| <span data-ttu-id="905a4-115">Método</span><span class="sxs-lookup"><span data-stu-id="905a4-115">Method</span></span>  | <span data-ttu-id="905a4-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="905a4-116">Request URI</span></span>                                                                                 |
|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="905a4-117">**Obter**</span><span class="sxs-lookup"><span data-stu-id="905a4-117">**GET**</span></span> | <span data-ttu-id="905a4-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/countryvalidationrules/{isocode-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="905a4-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/countryvalidationrules/{isocode-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="905a4-119">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="905a4-119">URI parameter</span></span>

| <span data-ttu-id="905a4-120">Nome</span><span class="sxs-lookup"><span data-stu-id="905a4-120">Name</span></span>           | <span data-ttu-id="905a4-121">Tipo</span><span class="sxs-lookup"><span data-stu-id="905a4-121">Type</span></span>       | <span data-ttu-id="905a4-122">Necessário</span><span class="sxs-lookup"><span data-stu-id="905a4-122">Required</span></span> | <span data-ttu-id="905a4-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="905a4-123">Description</span></span>                         |
|----------------|------------|----------|-------------------------------------|
| <span data-ttu-id="905a4-124">**isocode-id**</span><span class="sxs-lookup"><span data-stu-id="905a4-124">**isocode-id**</span></span> | <span data-ttu-id="905a4-125">**cadeia**</span><span class="sxs-lookup"><span data-stu-id="905a4-125">**string**</span></span> | <span data-ttu-id="905a4-126">Y</span><span class="sxs-lookup"><span data-stu-id="905a4-126">Y</span></span>        | <span data-ttu-id="905a4-127">O código de dois caracteres iso country.</span><span class="sxs-lookup"><span data-stu-id="905a4-127">The two-character ISO country code.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="905a4-128">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="905a4-128">Request headers</span></span>

<span data-ttu-id="905a4-129">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="905a4-129">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="905a4-130">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="905a4-130">Request body</span></span>

<span data-ttu-id="905a4-131">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="905a4-131">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="905a4-132">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="905a4-132">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/countryvalidationrules/{isocode-id} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 124b0e41-a093-4fec-b871-3eeb45fd734b
MS-CorrelationId: 5cfd634d-b936-47af-87f0-0f0217425dcc
```

## <a name="rest-response"></a><span data-ttu-id="905a4-133">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="905a4-133">REST response</span></span>

<span data-ttu-id="905a4-134">Se for bem sucedido, este método devolve um objeto **Desinformação do País** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="905a4-134">If successful, this method returns a **CountryInformation** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="905a4-135">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="905a4-135">Response success and error codes</span></span>

<span data-ttu-id="905a4-136">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="905a4-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="905a4-137">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="905a4-137">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="905a4-138">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="905a4-138">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="905a4-139">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="905a4-139">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1856
Content-Type: application/json
MS-CorrelationId: 5cfd634d-b936-47af-87f0-0f0217425dcc
MS-RequestId: 124b0e41-a093-4fec-b871-3eeb45fd734b
Date: Wed, 25 Nov 2015 06:36:47 GMT

{
    "iso2Code": "US",
    "defaultCulture": "en-US",
    "isStateRequired": true,
    "states": {
        "value": ["AK","AL","AR", "AZ","CA","CO","CT","DC","DE","FL","GA","HI","IA","ID","IL","IN",
        "KS","KY","LA","MA","MD","ME","MI","MN","MO","MS","MT","NC","ND","NE","NH","NJ","NM","NV",
        "NY","OH","OK","OR","PA","RI","SC","SD","TN","TX","UT","VA","VT","WA","WI","WV","WY"]
    },
    "supportedLanguages": {
        "value": ["en",
        "es"]
    },
    "supportedCultures": {
        "value": ["en-US",
        "es-US"]
    },
    "isPostalCodeRequired": true,
    "postalCodeRegex": "^\\d{
        5
    }(-\\d{
        4
    })?$",
    "isCityRequired": true,
    "isVatIdSupported": false,
    "taxIdFormat": "US######",
    "taxIdSample": "US999965",
    "phoneNumberRegex": "^(1[\\-\\/\\.]?)?(\((\\d{3})\)|(\\d{3}))[\\-\\/\\.]?(\\d{3})[\\-\\/\\.]?(\\d{4})$",
    "isRegistrationNumberSupported": false,
    "isTaxIdSupported": true,
    "resellerAgreementRegion": "AOC",
    "geographicRegion": "NorthAndLatinAmerica",
    "countryCallingCodes": {
        "value": ["1"]
    },
    "attributes": {
        "objectType": "CountryInformation"
    }
}
```
