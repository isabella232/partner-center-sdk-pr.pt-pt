---
title: Obter um perfil de organização
description: Obtém um objeto que representa o perfil de organização do parceiro.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 1c7272761612e573388d4facea1a78808a5bad52
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760560"
---
# <a name="get-an-organization-profile"></a><span data-ttu-id="d60c7-103">Obter um perfil de organização</span><span class="sxs-lookup"><span data-stu-id="d60c7-103">Get an organization profile</span></span>

<span data-ttu-id="d60c7-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d60c7-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d60c7-105">Obtém um objeto que representa o perfil de organização do parceiro.</span><span class="sxs-lookup"><span data-stu-id="d60c7-105">Gets an object representing the partner's organization profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d60c7-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d60c7-106">Prerequisites</span></span>

- <span data-ttu-id="d60c7-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d60c7-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d60c7-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="d60c7-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="d60c7-109">C\#</span><span class="sxs-lookup"><span data-stu-id="d60c7-109">C\#</span></span>

<span data-ttu-id="d60c7-110">Para obter o seu perfil de organização, use a sua coleção **IAggregatePartner.Profiles** e ligue para a propriedade **OrganizationProfile.**</span><span class="sxs-lookup"><span data-stu-id="d60c7-110">To get your organization profile, use your **IAggregatePartner.Profiles** collection and call the **OrganizationProfile** property.</span></span> <span data-ttu-id="d60c7-111">Por fim, ligue para os métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.getasync)</span><span class="sxs-lookup"><span data-stu-id="d60c7-111">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.getasync) methods.</span></span>

```csharp
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.Profiles.OrganizationProfile.Get();
```

<span data-ttu-id="d60c7-112">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d60c7-112">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d60c7-113">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetOrganizationProfile.cs</span><span class="sxs-lookup"><span data-stu-id="d60c7-113">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetOrganizationProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="d60c7-114">Java</span><span class="sxs-lookup"><span data-stu-id="d60c7-114">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="d60c7-115">Para obter o seu perfil de organização, use a função **IAggregatePartner.getProfiles** e ligue para a função **getOrganizationProfile.**</span><span class="sxs-lookup"><span data-stu-id="d60c7-115">To get your organization profile, use your **IAggregatePartner.getProfiles** function and call the **getOrganizationProfile** function.</span></span> <span data-ttu-id="d60c7-116">Finalmente, chame a função **get().**</span><span class="sxs-lookup"><span data-stu-id="d60c7-116">Finally, call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.getProfiles().getOrganizationProfile().get();
```

## <a name="powershell"></a><span data-ttu-id="d60c7-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="d60c7-117">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="d60c7-118">Para obter o seu perfil de organização, execute o comando [**Get-PartnerOrganizationProfile.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOrganizationProfile.md)</span><span class="sxs-lookup"><span data-stu-id="d60c7-118">To get your organization profile, execute the [**Get-PartnerOrganizationProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOrganizationProfile.md) command.</span></span>

```powershell
Get-PartnerOrganizationProfile
```

## <a name="rest-request"></a><span data-ttu-id="d60c7-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d60c7-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d60c7-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d60c7-120">Request syntax</span></span>

| <span data-ttu-id="d60c7-121">Método</span><span class="sxs-lookup"><span data-stu-id="d60c7-121">Method</span></span>  | <span data-ttu-id="d60c7-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d60c7-122">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="d60c7-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="d60c7-123">**GET**</span></span> | <span data-ttu-id="d60c7-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/organização HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d60c7-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d60c7-125">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d60c7-125">Request headers</span></span>

<span data-ttu-id="d60c7-126">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d60c7-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d60c7-127">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="d60c7-127">Request body</span></span>

<span data-ttu-id="d60c7-128">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d60c7-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d60c7-129">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d60c7-129">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/organization HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b85cb7ab-cc2e-4966-93f0-cf0d8377a93f
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
```

## <a name="rest-response"></a><span data-ttu-id="d60c7-130">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d60c7-130">REST response</span></span>

<span data-ttu-id="d60c7-131">Se for bem sucedido, este método devolve um objeto **OrganizationProfile** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="d60c7-131">If successful, this method returns an **OrganizationProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d60c7-132">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d60c7-132">Response success and error codes</span></span>

<span data-ttu-id="d60c7-133">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d60c7-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d60c7-134">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d60c7-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d60c7-135">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d60c7-135">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d60c7-136">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d60c7-136">Response example</span></span>

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
