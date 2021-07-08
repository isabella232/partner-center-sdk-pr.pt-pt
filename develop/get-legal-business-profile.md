---
title: Obter perfil comercial legal do parceiro
description: Aprenda a usar APIs para obter o seu perfil de negócio legal.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ba0654e364674bc2db129a0904d411c6fb67cbb9
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549064"
---
# <a name="get-the-partner-legal-business-profile"></a><span data-ttu-id="b6c02-103">Obter perfil comercial legal do parceiro</span><span class="sxs-lookup"><span data-stu-id="b6c02-103">Get the partner legal business profile</span></span>

<span data-ttu-id="b6c02-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b6c02-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b6c02-105">Como obter o perfil de negócio legal de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="b6c02-105">How to get a partner's legal business profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6c02-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b6c02-106">Prerequisites</span></span>

- <span data-ttu-id="b6c02-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b6c02-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b6c02-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="b6c02-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="b6c02-109">C\#</span><span class="sxs-lookup"><span data-stu-id="b6c02-109">C\#</span></span>

<span data-ttu-id="b6c02-110">Para obter o perfil de negócio legal do parceiro, primeiro obtenha uma interface para a recolha de operações de perfil de parceiro a partir da propriedade **IAggregatePartner.Profiles.**</span><span class="sxs-lookup"><span data-stu-id="b6c02-110">To get the partner legal business profile, first get an interface to the collection of partner profile operations from the **IAggregatePartner.Profiles** property.</span></span> <span data-ttu-id="b6c02-111">Em seguida, obtenha o valor do **imóvel LegalBusinessProfile** para recuperar uma interface para operações de perfil de negócio legal.</span><span class="sxs-lookup"><span data-stu-id="b6c02-111">Then, get the value of the **LegalBusinessProfile** property to retrieve an interface to legal business profile operations.</span></span> <span data-ttu-id="b6c02-112">Por fim, ligue para o [**método Get**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.getasync) para recuperar o perfil.</span><span class="sxs-lookup"><span data-stu-id="b6c02-112">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.get) or the [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.getasync) method to retrieve the profile.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var billingProfile = partnerOperations.Profiles.LegalBusinessProfile.Get();
```

<span data-ttu-id="b6c02-113">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b6c02-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b6c02-114">**Project**: Partner Center SDK Samples **Class**: GetLegalBusinessProfile.cs</span><span class="sxs-lookup"><span data-stu-id="b6c02-114">**Project**: Partner Center SDK Samples **Class**: GetLegalBusinessProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b6c02-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b6c02-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b6c02-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6c02-116">Request syntax</span></span>

| <span data-ttu-id="b6c02-117">Método</span><span class="sxs-lookup"><span data-stu-id="b6c02-117">Method</span></span>  | <span data-ttu-id="b6c02-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b6c02-118">Request URI</span></span>                                                                    |
|---------|--------------------------------------------------------------------------------|
| <span data-ttu-id="b6c02-119">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b6c02-119">**GET**</span></span> | <span data-ttu-id="b6c02-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/negócio legal HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b6c02-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/legalbusiness HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b6c02-121">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b6c02-121">Request headers</span></span>

<span data-ttu-id="b6c02-122">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b6c02-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b6c02-123">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b6c02-123">Request body</span></span>

<span data-ttu-id="b6c02-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b6c02-124">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b6c02-125">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b6c02-125">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/legalbusiness?vettingVersion=Current HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 7391249f-cba0-467c-b026-7b3a60196422
MS-CorrelationId: 98a091a0-67db-4eeb-ae0d-7e8b2e39c1d2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="b6c02-126">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b6c02-126">REST response</span></span>

<span data-ttu-id="b6c02-127">Se for bem sucedido, este método devolve um objeto **LegalBusinessProfile** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="b6c02-127">If successful, this method returns a **LegalBusinessProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b6c02-128">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b6c02-128">Response success and error codes</span></span>

<span data-ttu-id="b6c02-129">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b6c02-129">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b6c02-130">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b6c02-130">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b6c02-131">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b6c02-131">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b6c02-132">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b6c02-132">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1151
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 98a091a0-67db-4eeb-ae0d-7e8b2e39c1d2
MS-RequestId: 7391249f-cba0-467c-b026-7b3a60196422
MS-CV: MEgCpJUoGUeXG+4a.0
MS-ServerId: 030011719
Date: Tue, 21 Mar 2017 17:29:52 GMT

{
    "companyName": "Lucerne Publishing",
    "address": {
        "country": "US",
        "city": "Buffalo",
        "state": "NY",
        "addressLine1": "123 Main Street",
        "addressLine2": "",
        "postalCode": "98052",
        "firstName": "Gena",
        "lastName": "Soto",
        "phoneNumber": "4255550100"
    },
    "primaryContact": {
        "firstName": "Gena",
        "lastName": "Soto",
        "email": "gena@lucernepublishing.com",
        "phoneNumber": "4255550100"
    },
    "companyApproverAddress": {
        "country": "US",
        "city": "Buffalo",
        "state": "NY",
        "addressLine1": "123 Main Street",
        "addressLine2": "",
        "postalCode": "98052"
    },
    "companyApproverEmail": "gena@lucernepublishing.com",
    "vettingStatus": "authorized",
    "vettingSubStatus": "none",
    "profileType": "LegalBusinessProfile",
    "links": {
        "self": {
            "uri": "/profiles/legalbusiness",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "LegalBusinessProfile"
    }
}
```
