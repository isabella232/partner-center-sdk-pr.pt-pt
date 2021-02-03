---
title: Obter um perfil de organização
description: Obtém um objeto que representa o perfil de organização do parceiro.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 132a1e0efa3efea69d4bf649e55b412e300b0685
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769866"
---
# <a name="get-an-organization-profile"></a><span data-ttu-id="6a0cf-103">Obter um perfil de organização</span><span class="sxs-lookup"><span data-stu-id="6a0cf-103">Get an organization profile</span></span>

<span data-ttu-id="6a0cf-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="6a0cf-104">**Applies To**</span></span>

- <span data-ttu-id="6a0cf-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="6a0cf-105">Partner Center</span></span>
- <span data-ttu-id="6a0cf-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="6a0cf-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="6a0cf-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="6a0cf-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="6a0cf-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6a0cf-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6a0cf-109">Obtém um objeto que representa o perfil de organização do parceiro.</span><span class="sxs-lookup"><span data-stu-id="6a0cf-109">Gets an object representing the partner's organization profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6a0cf-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6a0cf-110">Prerequisites</span></span>

- <span data-ttu-id="6a0cf-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6a0cf-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6a0cf-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="6a0cf-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="6a0cf-113">C\#</span><span class="sxs-lookup"><span data-stu-id="6a0cf-113">C\#</span></span>

<span data-ttu-id="6a0cf-114">Para obter o seu perfil de organização, use a sua coleção **IAggregatePartner.Profiles** e ligue para a propriedade **OrganizationProfile.**</span><span class="sxs-lookup"><span data-stu-id="6a0cf-114">To get your organization profile, use your **IAggregatePartner.Profiles** collection and call the **OrganizationProfile** property.</span></span> <span data-ttu-id="6a0cf-115">Por fim, ligue para os métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.getasync)</span><span class="sxs-lookup"><span data-stu-id="6a0cf-115">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.getasync) methods.</span></span>

```csharp
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.Profiles.OrganizationProfile.Get();
```

<span data-ttu-id="6a0cf-116">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="6a0cf-116">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="6a0cf-117">**Projeto**: PartnerCenterSDK.FeaturesSamples **Class**: GetOrganizationProfile.cs</span><span class="sxs-lookup"><span data-stu-id="6a0cf-117">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetOrganizationProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="6a0cf-118">Java</span><span class="sxs-lookup"><span data-stu-id="6a0cf-118">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="6a0cf-119">Para obter o seu perfil de organização, use a função **IAggregatePartner.getProfiles** e ligue para a função **getOrganizationProfile.**</span><span class="sxs-lookup"><span data-stu-id="6a0cf-119">To get your organization profile, use your **IAggregatePartner.getProfiles** function and call the **getOrganizationProfile** function.</span></span> <span data-ttu-id="6a0cf-120">Finalmente, chame a função **get().**</span><span class="sxs-lookup"><span data-stu-id="6a0cf-120">Finally, call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.getProfiles().getOrganizationProfile().get();
```

## <a name="powershell"></a><span data-ttu-id="6a0cf-121">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a0cf-121">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="6a0cf-122">Para obter o seu perfil de organização, execute o comando [**Get-PartnerOrganizationProfile.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOrganizationProfile.md)</span><span class="sxs-lookup"><span data-stu-id="6a0cf-122">To get your organization profile, execute the [**Get-PartnerOrganizationProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOrganizationProfile.md) command.</span></span>

```powershell
Get-PartnerOrganizationProfile
```

## <a name="rest-request"></a><span data-ttu-id="6a0cf-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6a0cf-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6a0cf-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a0cf-124">Request syntax</span></span>

| <span data-ttu-id="6a0cf-125">Método</span><span class="sxs-lookup"><span data-stu-id="6a0cf-125">Method</span></span>  | <span data-ttu-id="6a0cf-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6a0cf-126">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="6a0cf-127">**Obter**</span><span class="sxs-lookup"><span data-stu-id="6a0cf-127">**GET**</span></span> | <span data-ttu-id="6a0cf-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/organização HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6a0cf-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6a0cf-129">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6a0cf-129">Request headers</span></span>

<span data-ttu-id="6a0cf-130">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6a0cf-130">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6a0cf-131">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6a0cf-131">Request body</span></span>

<span data-ttu-id="6a0cf-132">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6a0cf-132">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6a0cf-133">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6a0cf-133">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/organization HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b85cb7ab-cc2e-4966-93f0-cf0d8377a93f
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
```

## <a name="rest-response"></a><span data-ttu-id="6a0cf-134">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6a0cf-134">REST response</span></span>

<span data-ttu-id="6a0cf-135">Se for bem sucedido, este método devolve um objeto **OrganizationProfile** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="6a0cf-135">If successful, this method returns an **OrganizationProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6a0cf-136">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6a0cf-136">Response success and error codes</span></span>

<span data-ttu-id="6a0cf-137">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6a0cf-137">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6a0cf-138">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6a0cf-138">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6a0cf-139">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6a0cf-139">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6a0cf-140">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6a0cf-140">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 648
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
MS-RequestId: b85cb7ab-cc2e-4966-93f0-cf0d8377a93f
Date: Tue, 22 Mar 2016 17:11:06 GMT

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
