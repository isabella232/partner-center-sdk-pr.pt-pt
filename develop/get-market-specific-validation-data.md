---
title: Obter regras de formatação de endereços por mercado
description: Obtenha o formato de endereço esperado com base no código iso para o mercado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d5233d059ea6e71c28df36b2242659c28c5dd857
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549047"
---
# <a name="get-address-formatting-rules-by-market"></a><span data-ttu-id="ca7ab-103">Obter regras de formatação de endereços por mercado</span><span class="sxs-lookup"><span data-stu-id="ca7ab-103">Get address formatting rules by market</span></span>

<span data-ttu-id="ca7ab-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ca7ab-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>


<span data-ttu-id="ca7ab-105">Obtenha o formato de endereço esperado com base no código iso para o mercado.</span><span class="sxs-lookup"><span data-stu-id="ca7ab-105">Get the expected address format based on the iso code for the market.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca7ab-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ca7ab-106">Prerequisites</span></span>

- <span data-ttu-id="ca7ab-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ca7ab-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ca7ab-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="ca7ab-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="ca7ab-109">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="ca7ab-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ca7ab-110">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca7ab-110">Request syntax</span></span>

| <span data-ttu-id="ca7ab-111">Método</span><span class="sxs-lookup"><span data-stu-id="ca7ab-111">Method</span></span>  | <span data-ttu-id="ca7ab-112">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="ca7ab-112">Request URI</span></span>                                                                                 |
|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="ca7ab-113">**Obter**</span><span class="sxs-lookup"><span data-stu-id="ca7ab-113">**GET**</span></span> | <span data-ttu-id="ca7ab-114">[*{baseURL}*](partner-center-rest-urls.md)/v1/countryvalidationrules/{isocode-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ca7ab-114">[*{baseURL}*](partner-center-rest-urls.md)/v1/countryvalidationrules/{isocode-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="ca7ab-115">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="ca7ab-115">URI parameter</span></span>

| <span data-ttu-id="ca7ab-116">Nome</span><span class="sxs-lookup"><span data-stu-id="ca7ab-116">Name</span></span>           | <span data-ttu-id="ca7ab-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="ca7ab-117">Type</span></span>       | <span data-ttu-id="ca7ab-118">Necessário</span><span class="sxs-lookup"><span data-stu-id="ca7ab-118">Required</span></span> | <span data-ttu-id="ca7ab-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca7ab-119">Description</span></span>                         |
|----------------|------------|----------|-------------------------------------|
| <span data-ttu-id="ca7ab-120">**isocode-id**</span><span class="sxs-lookup"><span data-stu-id="ca7ab-120">**isocode-id**</span></span> | <span data-ttu-id="ca7ab-121">**string**</span><span class="sxs-lookup"><span data-stu-id="ca7ab-121">**string**</span></span> | <span data-ttu-id="ca7ab-122">Y</span><span class="sxs-lookup"><span data-stu-id="ca7ab-122">Y</span></span>        | <span data-ttu-id="ca7ab-123">O código de dois caracteres iso country.</span><span class="sxs-lookup"><span data-stu-id="ca7ab-123">The two-character ISO country code.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ca7ab-124">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="ca7ab-124">Request headers</span></span>

<span data-ttu-id="ca7ab-125">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ca7ab-125">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ca7ab-126">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="ca7ab-126">Request body</span></span>

<span data-ttu-id="ca7ab-127">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ca7ab-127">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ca7ab-128">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="ca7ab-128">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/countryvalidationrules/{isocode-id} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 124b0e41-a093-4fec-b871-3eeb45fd734b
MS-CorrelationId: 5cfd634d-b936-47af-87f0-0f0217425dcc
```

## <a name="rest-response"></a><span data-ttu-id="ca7ab-129">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="ca7ab-129">REST response</span></span>

<span data-ttu-id="ca7ab-130">Se for bem sucedido, este método devolve um objeto **Desinformação do País** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="ca7ab-130">If successful, this method returns a **CountryInformation** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ca7ab-131">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="ca7ab-131">Response success and error codes</span></span>

<span data-ttu-id="ca7ab-132">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="ca7ab-132">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ca7ab-133">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="ca7ab-133">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ca7ab-134">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="ca7ab-134">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ca7ab-135">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="ca7ab-135">Response example</span></span>

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
