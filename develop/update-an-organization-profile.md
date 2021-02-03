---
title: Atualizar um perfil de organização
description: Atualiza o perfil de faturação de uma organização.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ccf938fff285704f54d4717b2678e1419d857d8d
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768995"
---
# <a name="update-an-organization-profile"></a><span data-ttu-id="72d25-103">Atualizar um perfil de organização</span><span class="sxs-lookup"><span data-stu-id="72d25-103">Update an organization profile</span></span>

<span data-ttu-id="72d25-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="72d25-104">**Applies To**</span></span>

- <span data-ttu-id="72d25-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="72d25-105">Partner Center</span></span>
- <span data-ttu-id="72d25-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="72d25-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="72d25-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="72d25-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="72d25-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="72d25-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="72d25-109">Atualiza o perfil de faturação de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="72d25-109">Updates a partner's billing profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72d25-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="72d25-110">Prerequisites</span></span>

- <span data-ttu-id="72d25-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="72d25-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="72d25-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="72d25-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="72d25-113">C\#</span><span class="sxs-lookup"><span data-stu-id="72d25-113">C\#</span></span>

<span data-ttu-id="72d25-114">Para atualizar o seu perfil de organização, recupere o perfil e faça as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="72d25-114">To update your organization profile, retrieve the profile and make any necessary changes.</span></span> <span data-ttu-id="72d25-115">Em seguida, use a sua coleção **IAggregatePartner.Profiles** e ligue para a propriedade **OrganizationProfile.**</span><span class="sxs-lookup"><span data-stu-id="72d25-115">Then, use your **IAggregatePartner.Profiles** collection and call the **OrganizationProfile** property.</span></span> <span data-ttu-id="72d25-116">Por fim, ligue para o método **'Atualização).).**</span><span class="sxs-lookup"><span data-stu-id="72d25-116">Finally, call the **Update()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.Profiles.OrganizationProfile.Get();

// Generating a random phone number to update in the organization profile
organizationProfile.DefaultAddress.PhoneNumber = ((long)(new Random().NextDouble() * 9000000000) + 1000000000).ToString(CultureInfo.InvariantCulture);

OrganizationProfile updatedOrganizationProfile = partnerOperations.Profiles.OrganizationProfile.Update(organizationProfile);
```

<span data-ttu-id="72d25-117">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="72d25-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="72d25-118">**Projeto**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateOrganizationProfile.cs</span><span class="sxs-lookup"><span data-stu-id="72d25-118">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateOrganizationProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="72d25-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="72d25-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="72d25-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="72d25-120">Request syntax</span></span>

| <span data-ttu-id="72d25-121">Método</span><span class="sxs-lookup"><span data-stu-id="72d25-121">Method</span></span>  | <span data-ttu-id="72d25-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="72d25-122">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="72d25-123">**PUT**</span><span class="sxs-lookup"><span data-stu-id="72d25-123">**PUT**</span></span> | <span data-ttu-id="72d25-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/organização HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="72d25-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="72d25-125">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="72d25-125">Request headers</span></span>

<span data-ttu-id="72d25-126">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="72d25-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="72d25-127">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="72d25-127">Request body</span></span>

<span data-ttu-id="72d25-128">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="72d25-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="72d25-129">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="72d25-129">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="72d25-130">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="72d25-130">REST response</span></span>

<span data-ttu-id="72d25-131">Se for bem sucedido, este método devolve um objeto **OrganizationProfile** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="72d25-131">If successful, this method returns an **OrganizationProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="72d25-132">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="72d25-132">Response success and error codes</span></span>

<span data-ttu-id="72d25-133">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="72d25-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="72d25-134">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="72d25-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="72d25-135">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="72d25-135">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="72d25-136">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="72d25-136">Response example</span></span>

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
