---
title: Atualizar perfil de suporte
description: Atualiza o perfil de suporte de um utilizador.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 605c509eeb18f301144fec6287c9611d5a5acfe2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769595"
---
# <a name="update-support-profile"></a><span data-ttu-id="4acf5-103">Atualizar perfil de suporte</span><span class="sxs-lookup"><span data-stu-id="4acf5-103">Update support profile</span></span>

<span data-ttu-id="4acf5-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="4acf5-104">**Applies To**</span></span>

- <span data-ttu-id="4acf5-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="4acf5-105">Partner Center</span></span>
- <span data-ttu-id="4acf5-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="4acf5-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="4acf5-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="4acf5-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="4acf5-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4acf5-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4acf5-109">Atualiza o perfil de suporte de um utilizador.</span><span class="sxs-lookup"><span data-stu-id="4acf5-109">Updates a user's support profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4acf5-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4acf5-110">Prerequisites</span></span>

- <span data-ttu-id="4acf5-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4acf5-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4acf5-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="4acf5-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="4acf5-113">C\#</span><span class="sxs-lookup"><span data-stu-id="4acf5-113">C\#</span></span>

<span data-ttu-id="4acf5-114">Para atualizar o seu perfil de suporte, obtenha primeiro [o seu perfil de suporte](get-support-profile.md) e faça quaisquer alterações que desejar.</span><span class="sxs-lookup"><span data-stu-id="4acf5-114">To update your support profile, first [get your support profile](get-support-profile.md) and make any changes you wish.</span></span> <span data-ttu-id="4acf5-115">Em seguida, use a sua coleção [**IPartnerOperations.Profiles.**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles)</span><span class="sxs-lookup"><span data-stu-id="4acf5-115">Then, use your [**IPartnerOperations.Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) collection.</span></span> <span data-ttu-id="4acf5-116">Ligue para a propriedade [**SupportProfile,**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) seguida do método [**Update()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.update) ou [**UpdateAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.updateasync)</span><span class="sxs-lookup"><span data-stu-id="4acf5-116">Call the [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) property, followed by the [**Update()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.update) or [**UpdateAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.updateasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// updated profile
SupportProfile newSupportProfile = new SupportProfile
{
   Email = supportProfile.Email,
   Website = supportProfile.Website,
   Telephone = new Random().Next(10000000, 99999999).ToString(CultureInfo.InvariantCulture)
};

SupportProfile updatedSupportProfile = partnerOperations.Profiles.SupportProfile.Update(newSupportProfile);
```

<span data-ttu-id="4acf5-117">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="4acf5-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="4acf5-118">**Projeto**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateSupportProfile.cs</span><span class="sxs-lookup"><span data-stu-id="4acf5-118">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateSupportProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="4acf5-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="4acf5-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4acf5-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="4acf5-120">Request syntax</span></span>

| <span data-ttu-id="4acf5-121">Método</span><span class="sxs-lookup"><span data-stu-id="4acf5-121">Method</span></span>  | <span data-ttu-id="4acf5-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="4acf5-122">Request URI</span></span>                                                                     |
|---------|---------------------------------------------------------------------------------|
| <span data-ttu-id="4acf5-123">**PUT**</span><span class="sxs-lookup"><span data-stu-id="4acf5-123">**PUT**</span></span> | <span data-ttu-id="4acf5-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/supportprofile HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4acf5-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/supportprofile HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4acf5-125">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="4acf5-125">Request headers</span></span>

<span data-ttu-id="4acf5-126">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4acf5-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4acf5-127">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="4acf5-127">Request body</span></span>

<span data-ttu-id="4acf5-128">O recurso de perfil de suporte completo.</span><span class="sxs-lookup"><span data-stu-id="4acf5-128">The full support profile resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="4acf5-129">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="4acf5-129">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/supportprofile HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 603f3cd9-01b8-48f2-b65d-855a246f5bfd
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
Content-Type: application/json
Content-Length: 167
Expect: 100-continue

{
    "Email": "email@sample.com",
    "Telephone": "4255555555",
    "Website": "www.microsoft.com",
    "ProfileType": "support_profile",
    "Attributes": {
        "ObjectType": "PartnerSupportProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="4acf5-130">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="4acf5-130">REST response</span></span>

<span data-ttu-id="4acf5-131">Se for bem sucedido, este método devolve as propriedades atualizadas do objeto **SupportProfile** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="4acf5-131">If successful, this method returns updated **SupportProfile** object properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4acf5-132">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="4acf5-132">Response success and error codes</span></span>

<span data-ttu-id="4acf5-133">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="4acf5-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4acf5-134">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4acf5-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4acf5-135">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4acf5-135">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4acf5-136">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="4acf5-136">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 502
Content-Type: application/json
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
MS-RequestId: 603f3cd9-01b8-48f2-b65d-855a246f5bfd
Date: Wed, 25 Nov 2015 07:16:18 GMT

{
    "email": "email@sample.com",
    "telephone": "4255555555",
    "website": "www.microsoft.com",
    "profileType": "support_profile",
    "links": {
        "self": {
            "uri": "/v1/profiles/support",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "PartnerSupportProfile"
    }
}
```
