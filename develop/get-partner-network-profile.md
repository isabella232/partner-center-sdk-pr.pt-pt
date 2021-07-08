---
title: Obter perfil do Microsoft Partner Network
description: Obtém um objeto que representa o perfil de MPN do parceiro.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 38c12a9a9755b9838b7742d9f38c5cbd52b81210
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548860"
---
# <a name="get-microsoft-partner-network-profile"></a><span data-ttu-id="cdb3d-103">Obter perfil do Microsoft Partner Network</span><span class="sxs-lookup"><span data-stu-id="cdb3d-103">Get Microsoft Partner Network profile</span></span>

<span data-ttu-id="cdb3d-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cdb3d-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cdb3d-105">Obtém um objeto que representa o perfil de MPN do parceiro.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-105">Gets an object representing the partner's MPN profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cdb3d-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="cdb3d-106">Prerequisites</span></span>

- <span data-ttu-id="cdb3d-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cdb3d-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cdb3d-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="cdb3d-109">C\#</span><span class="sxs-lookup"><span data-stu-id="cdb3d-109">C\#</span></span>

<span data-ttu-id="cdb3d-110">Para obter um perfil de rede de parceiros, use a sua coleção **IAggregatePartner.Profiles** e ligue para a propriedade **MpnProfile.**</span><span class="sxs-lookup"><span data-stu-id="cdb3d-110">To get a partner network profile, use your **IAggregatePartner.Profiles** collection and call the **MpnProfile** property.</span></span> <span data-ttu-id="cdb3d-111">Por fim, ligue para os métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync)</span><span class="sxs-lookup"><span data-stu-id="cdb3d-111">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var mpnProfile = partnerOperations.Profiles.MpnProfile.Get();
```

<span data-ttu-id="cdb3d-112">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cdb3d-112">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cdb3d-113">**Project**:P artnerCenterSDK.FeaturesSamples **Class**: GetMPNProfile.cs</span><span class="sxs-lookup"><span data-stu-id="cdb3d-113">**Project**:PartnerCenterSDK.FeaturesSamples **Class**: GetMPNProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="cdb3d-114">Java</span><span class="sxs-lookup"><span data-stu-id="cdb3d-114">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="cdb3d-115">Para obter um perfil de rede de parceiros, utilize a função **IAggregatePartner.getProfiles** e ligue para a função **getMpnProfile.**</span><span class="sxs-lookup"><span data-stu-id="cdb3d-115">To get a partner network profile, use your **IAggregatePartner.getProfiles** function and call the **getMpnProfile** function.</span></span> <span data-ttu-id="cdb3d-116">Finalmente, chame a função **get().**</span><span class="sxs-lookup"><span data-stu-id="cdb3d-116">Finally, call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;

MpnProfile mpnProfile = partnerOperations.getProfiles().getMpnProfile().get();
```

## <a name="powershell"></a><span data-ttu-id="cdb3d-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="cdb3d-117">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="cdb3d-118">Para obter um perfil de rede de parceiros, execute o comando [**Get-PartnerMpnProfile.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerMpnProfile.md)</span><span class="sxs-lookup"><span data-stu-id="cdb3d-118">To get a partner network profile, execute the [**Get-PartnerMpnProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerMpnProfile.md) command.</span></span>

```powershell
Get-PartnerMpnProfile
```

## <a name="rest-request"></a><span data-ttu-id="cdb3d-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="cdb3d-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cdb3d-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdb3d-120">Request syntax</span></span>

| <span data-ttu-id="cdb3d-121">Método</span><span class="sxs-lookup"><span data-stu-id="cdb3d-121">Method</span></span>  | <span data-ttu-id="cdb3d-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="cdb3d-122">Request URI</span></span>                                                          |
|---------|----------------------------------------------------------------------|
| <span data-ttu-id="cdb3d-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="cdb3d-123">**GET**</span></span> | <span data-ttu-id="cdb3d-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="cdb3d-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cdb3d-125">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="cdb3d-125">Request headers</span></span>

<span data-ttu-id="cdb3d-126">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cdb3d-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cdb3d-127">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="cdb3d-127">Request body</span></span>

<span data-ttu-id="cdb3d-128">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="cdb3d-129">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="cdb3d-129">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/mpn HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 76879323-92d1-437e-90dd-c84dbb9f7dec
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="cdb3d-130">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="cdb3d-130">REST response</span></span>

<span data-ttu-id="cdb3d-131">Se for bem sucedido, este método devolve um objeto **MPNProfile** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-131">If successful, this method returns a **MPNProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cdb3d-132">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="cdb3d-132">Response success and error codes</span></span>

<span data-ttu-id="cdb3d-133">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cdb3d-134">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cdb3d-135">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="cdb3d-135">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cdb3d-136">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="cdb3d-136">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
MS-RequestId: 76879323-92d1-437e-90dd-c84dbb9f7dec
Date: Mon, 21 Mar 2016 05:51:29 GMT

{
    "mpnId":"<mpnID>",
    "profileType":"MpnProfile",
    "links":{
        "self":{
            "uri":"/profiles/mpn",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"MpnProfile"
    }
}
```
