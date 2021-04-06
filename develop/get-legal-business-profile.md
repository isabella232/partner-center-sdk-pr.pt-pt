---
title: Obter perfil comercial legal do parceiro
description: Aprenda a usar APIs para obter o seu perfil de negócio legal.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1d488c8deb9f01110e92327035ce0c3c023fcb46
ms.sourcegitcommit: f72173df911aee3ab29b008637190b4d85ffebfe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/06/2021
ms.locfileid: "106500027"
---
# <a name="get-the-partner-legal-business-profile"></a><span data-ttu-id="b3972-103">Obter perfil comercial legal do parceiro</span><span class="sxs-lookup"><span data-stu-id="b3972-103">Get the partner legal business profile</span></span>

<span data-ttu-id="b3972-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="b3972-104">**Applies To**</span></span>

- <span data-ttu-id="b3972-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="b3972-105">Partner Center</span></span>
- <span data-ttu-id="b3972-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="b3972-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="b3972-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="b3972-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="b3972-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b3972-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b3972-109">Como obter o perfil de negócio legal de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="b3972-109">How to get a partner's legal business profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b3972-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b3972-110">Prerequisites</span></span>

- <span data-ttu-id="b3972-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b3972-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b3972-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="b3972-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="b3972-113">C\#</span><span class="sxs-lookup"><span data-stu-id="b3972-113">C\#</span></span>

<span data-ttu-id="b3972-114">Para obter o perfil de negócio legal do parceiro, primeiro obtenha uma interface para a recolha de operações de perfil de parceiro a partir da propriedade **IAggregatePartner.Profiles.**</span><span class="sxs-lookup"><span data-stu-id="b3972-114">To get the partner legal business profile, first get an interface to the collection of partner profile operations from the **IAggregatePartner.Profiles** property.</span></span> <span data-ttu-id="b3972-115">Em seguida, obtenha o valor do **imóvel LegalBusinessProfile** para recuperar uma interface para operações de perfil de negócio legal.</span><span class="sxs-lookup"><span data-stu-id="b3972-115">Then, get the value of the **LegalBusinessProfile** property to retrieve an interface to legal business profile operations.</span></span> <span data-ttu-id="b3972-116">Por fim, ligue para o [**método Get**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.getasync) para recuperar o perfil.</span><span class="sxs-lookup"><span data-stu-id="b3972-116">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.get) or the [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.getasync) method to retrieve the profile.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var billingProfile = partnerOperations.Profiles.LegalBusinessProfile.Get();
```

<span data-ttu-id="b3972-117">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b3972-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b3972-118">**Projeto**: Partner Center SDK Samples **Class**: GetLegalBusinessProfile.cs</span><span class="sxs-lookup"><span data-stu-id="b3972-118">**Project**: Partner Center SDK Samples **Class**: GetLegalBusinessProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b3972-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b3972-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b3972-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3972-120">Request syntax</span></span>

| <span data-ttu-id="b3972-121">Método</span><span class="sxs-lookup"><span data-stu-id="b3972-121">Method</span></span>  | <span data-ttu-id="b3972-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b3972-122">Request URI</span></span>                                                                    |
|---------|--------------------------------------------------------------------------------|
| <span data-ttu-id="b3972-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b3972-123">**GET**</span></span> | <span data-ttu-id="b3972-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/negócio legal HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b3972-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/legalbusiness HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b3972-125">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b3972-125">Request headers</span></span>

<span data-ttu-id="b3972-126">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b3972-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b3972-127">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b3972-127">Request body</span></span>

<span data-ttu-id="b3972-128">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b3972-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b3972-129">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b3972-129">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="b3972-130">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b3972-130">REST response</span></span>

<span data-ttu-id="b3972-131">Se for bem sucedido, este método devolve um objeto **LegalBusinessProfile** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="b3972-131">If successful, this method returns a **LegalBusinessProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b3972-132">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b3972-132">Response success and error codes</span></span>

<span data-ttu-id="b3972-133">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b3972-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b3972-134">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b3972-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b3972-135">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b3972-135">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b3972-136">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b3972-136">Response example</span></span>

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
