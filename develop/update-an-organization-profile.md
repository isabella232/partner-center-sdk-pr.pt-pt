---
title: Atualizar um perfil de organização
description: Atualiza o perfil de faturação de uma organização.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0ef736a722cde16f95ed6dfdbdab278c98fcf738
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530060"
---
# <a name="update-an-organization-profile"></a><span data-ttu-id="5d8b3-103">Atualizar um perfil de organização</span><span class="sxs-lookup"><span data-stu-id="5d8b3-103">Update an organization profile</span></span>

<span data-ttu-id="5d8b3-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5d8b3-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5d8b3-105">Atualiza o perfil de faturação de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="5d8b3-105">Updates a partner's billing profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5d8b3-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5d8b3-106">Prerequisites</span></span>

- <span data-ttu-id="5d8b3-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5d8b3-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5d8b3-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="5d8b3-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="5d8b3-109">C\#</span><span class="sxs-lookup"><span data-stu-id="5d8b3-109">C\#</span></span>

<span data-ttu-id="5d8b3-110">Para atualizar o seu perfil de organização, recupere o perfil e faça as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="5d8b3-110">To update your organization profile, retrieve the profile and make any necessary changes.</span></span> <span data-ttu-id="5d8b3-111">Em seguida, use a sua coleção **IAggregatePartner.Profiles** e ligue para a propriedade **OrganizationProfile.**</span><span class="sxs-lookup"><span data-stu-id="5d8b3-111">Then, use your **IAggregatePartner.Profiles** collection and call the **OrganizationProfile** property.</span></span> <span data-ttu-id="5d8b3-112">Por fim, ligue para o método **'Atualização).).**</span><span class="sxs-lookup"><span data-stu-id="5d8b3-112">Finally, call the **Update()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.Profiles.OrganizationProfile.Get();

// Generating a random phone number to update in the organization profile
organizationProfile.DefaultAddress.PhoneNumber = ((long)(new Random().NextDouble() * 9000000000) + 1000000000).ToString(CultureInfo.InvariantCulture);

OrganizationProfile updatedOrganizationProfile = partnerOperations.Profiles.OrganizationProfile.Update(organizationProfile);
```

<span data-ttu-id="5d8b3-113">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="5d8b3-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="5d8b3-114">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateOrganizationProfile.cs</span><span class="sxs-lookup"><span data-stu-id="5d8b3-114">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateOrganizationProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="5d8b3-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5d8b3-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5d8b3-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d8b3-116">Request syntax</span></span>

| <span data-ttu-id="5d8b3-117">Método</span><span class="sxs-lookup"><span data-stu-id="5d8b3-117">Method</span></span>  | <span data-ttu-id="5d8b3-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5d8b3-118">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="5d8b3-119">**PUT**</span><span class="sxs-lookup"><span data-stu-id="5d8b3-119">**PUT**</span></span> | <span data-ttu-id="5d8b3-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/organização HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5d8b3-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5d8b3-121">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="5d8b3-121">Request headers</span></span>

<span data-ttu-id="5d8b3-122">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5d8b3-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5d8b3-123">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5d8b3-123">Request body</span></span>

<span data-ttu-id="5d8b3-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5d8b3-124">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5d8b3-125">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5d8b3-125">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/organization HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: fe76387b-9658-47d7-939d-0c70032ef589
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
Content-Length: 624
Expect: 100-continue

{
    "id":<id>,
    "companyName":"TEST_TEST_BugBash1",
    "defaultAddress":{
        "country":"US",
        "city":"Redmond",
        "state":"WA",
        "addressLine1":"Two Microsoft Way",
        "addressLine2":"",
        "postalCode":"98052",
        "firstName":"Test",
        "lastName":"Account",
        "phoneNumber":""
    },
    "tenantId":<tenantID>,
    "domain":"testtestbugbash1.onmicrosoft.com",
    "email":"test-partner@microsoft.com",
    "language":"es",
    "culture":"es-US",
    "links":{
        "self":{
            "uri":"/profiles/organization",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "etag":<etag>,
        "objectType":"OrganizationProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="5d8b3-126">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5d8b3-126">REST response</span></span>

<span data-ttu-id="5d8b3-127">Se for bem sucedido, este método devolve um objeto **OrganizationProfile** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="5d8b3-127">If successful, this method returns an **OrganizationProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5d8b3-128">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5d8b3-128">Response success and error codes</span></span>

<span data-ttu-id="5d8b3-129">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5d8b3-129">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5d8b3-130">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5d8b3-130">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5d8b3-131">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="5d8b3-131">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5d8b3-132">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5d8b3-132">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 648
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
MS-RequestId: fe76387b-9658-47d7-939d-0c70032ef589
Date: Mon, 21 Mar 2016 05:48:41 GMT

{
    "id":<id>,
    "companyName":"TEST_TEST_BugBash1",
    "defaultAddress":{
        "country":"US",
        "city":"Redmond",
        "state":"WA",
        "addressLine1":"Two Microsoft Way",
        "addressLine2":"",
        "postalCode":"98052",
        "firstName":"Test",
        "lastName":"Account",
        "phoneNumber":""
    },
    "tenantId":<tenantID>,
    "domain":"testtestbugbash1.onmicrosoft.com",
    "email":"test-partner@microsoft.com",
    "language":"es",
    "culture":"es-US",
    "profileType":"OrganizationProfile",
    "links":{
        "self":{
            "uri":"/profiles/organization",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "etag":<etag>,
        "objectType":"OrganizationProfile"
    }
}
```
