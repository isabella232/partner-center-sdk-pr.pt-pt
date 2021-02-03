---
title: Verificar um ID do MPN do parceiro
description: Saiba como verificar o identificador da Microsoft Partner Network (MPN ID) de um parceiro, solicitando o perfil DE MPN do parceiro via C \# ou a API do Partner Center REST.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6ef7bcb35274a6bcbaddbe0553ca0cb4dc1b2f9c
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "97769938"
---
# <a name="verify-a-partner-mpn-id-via-c-or-the-partner-center-rest-api"></a><span data-ttu-id="9482b-103">Verifique um parceiro MPN ID via C \# ou o Partner Center REST API</span><span class="sxs-lookup"><span data-stu-id="9482b-103">Verify a partner MPN ID via C\# or the Partner Center REST API</span></span>

<span data-ttu-id="9482b-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="9482b-104">**Applies To**</span></span>

- <span data-ttu-id="9482b-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="9482b-105">Partner Center</span></span>
- <span data-ttu-id="9482b-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="9482b-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="9482b-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="9482b-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="9482b-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9482b-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9482b-109">Como verificar o identificador da Microsoft Partner Network (MPN ID) de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="9482b-109">How to verify a partner's Microsoft Partner Network identifier (MPN ID).</span></span>

<span data-ttu-id="9482b-110">A técnica mostrada aqui verifica o identificador da Microsoft Partner Network do parceiro, solicitando o perfil MPN do parceiro do centro parceiro.</span><span class="sxs-lookup"><span data-stu-id="9482b-110">The technique shown here verifies the partner's Microsoft Partner Network identifier by requesting the partner's MPN profile from partner center.</span></span> <span data-ttu-id="9482b-111">O identificador é considerado válido se o pedido for bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="9482b-111">The identifier is considered valid if the request succeeds.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9482b-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9482b-112">Prerequisites</span></span>

- <span data-ttu-id="9482b-113">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9482b-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9482b-114">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="9482b-114">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="9482b-115">O sócio MPN ID para verificar.</span><span class="sxs-lookup"><span data-stu-id="9482b-115">The partner MPN ID to verify.</span></span> <span data-ttu-id="9482b-116">Se omitir este valor, o pedido recupera o perfil MPN do parceiro inscrito.</span><span class="sxs-lookup"><span data-stu-id="9482b-116">If you omit this value, the request retrieves the MPN profile of the signed-in partner.</span></span>

## <a name="c"></a><span data-ttu-id="9482b-117">C\#</span><span class="sxs-lookup"><span data-stu-id="9482b-117">C\#</span></span>

<span data-ttu-id="9482b-118">Para verificar o ID MPN de um parceiro, primeiro recupere uma interface para operar a recolha de perfis de parceiros a partir da propriedade [**IAggregatePartner.Profiles.**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles)</span><span class="sxs-lookup"><span data-stu-id="9482b-118">To verify a partner's MPN ID, first retrieve an interface to partner profile collection operations from the [**IAggregatePartner.Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) property.</span></span> <span data-ttu-id="9482b-119">Em seguida, obtenha uma interface para as operações de perfil MPN da propriedade [**MpnProfile.**](/dotnet/api/microsoft.store.partnercenter.profiles.ipartnerprofilecollection.mpnprofile)</span><span class="sxs-lookup"><span data-stu-id="9482b-119">Then get an interface to MPN profile operations from the [**MpnProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.ipartnerprofilecollection.mpnprofile) property.</span></span> <span data-ttu-id="9482b-120">Por fim, ligue para os métodos [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) com o ID MPN para recuperar o perfil MPN.</span><span class="sxs-lookup"><span data-stu-id="9482b-120">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) methods with the MPN ID to retrieve the MPN profile.</span></span> <span data-ttu-id="9482b-121">Se omitir o ID mpn da chamada Get or GetAsync, o pedido tenta recuperar o perfil MPN do parceiro inscrito.</span><span class="sxs-lookup"><span data-stu-id="9482b-121">If you omit the MPN ID from the Get or GetAsync call, the request attempts to retrieve the MPN profile of the signed-in partner.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string partnerMpnId;

var partnerProfile = partnerOperations.Profiles.MpnProfile.Get(partnerMpnId);
```

<span data-ttu-id="9482b-122">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="9482b-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="9482b-123">**Projeto**: Partner Center SDK Samples **Class**: VerifyPartnerMpnId.cs</span><span class="sxs-lookup"><span data-stu-id="9482b-123">**Project**: Partner Center SDK Samples **Class**: VerifyPartnerMpnId.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="9482b-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="9482b-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9482b-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="9482b-125">Request syntax</span></span>

| <span data-ttu-id="9482b-126">Método</span><span class="sxs-lookup"><span data-stu-id="9482b-126">Method</span></span>  | <span data-ttu-id="9482b-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="9482b-127">Request URI</span></span>                                                                         |
|---------|-------------------------------------------------------------------------------------|
| <span data-ttu-id="9482b-128">**Obter**</span><span class="sxs-lookup"><span data-stu-id="9482b-128">**GET**</span></span> | <span data-ttu-id="9482b-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn?mpnId={mpn-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9482b-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn?mpnId={mpn-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="9482b-130">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="9482b-130">URI parameter</span></span>

<span data-ttu-id="9482b-131">Forneça o seguinte parâmetro de consulta para identificar o parceiro.</span><span class="sxs-lookup"><span data-stu-id="9482b-131">Provide the following query parameter to identify the partner.</span></span> <span data-ttu-id="9482b-132">Se omitir este parâmetro de consulta, o pedido devolve o perfil MPN do parceiro inscrito.</span><span class="sxs-lookup"><span data-stu-id="9482b-132">If you omit this query parameter, the request returns the MPN profile of the signed-in partner.</span></span>

| <span data-ttu-id="9482b-133">Nome</span><span class="sxs-lookup"><span data-stu-id="9482b-133">Name</span></span>   | <span data-ttu-id="9482b-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="9482b-134">Type</span></span> | <span data-ttu-id="9482b-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="9482b-135">Required</span></span> | <span data-ttu-id="9482b-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="9482b-136">Description</span></span>                                                 |
|--------|------|----------|-------------------------------------------------------------|
| <span data-ttu-id="9482b-137">mpn-id</span><span class="sxs-lookup"><span data-stu-id="9482b-137">mpn-id</span></span> | <span data-ttu-id="9482b-138">int</span><span class="sxs-lookup"><span data-stu-id="9482b-138">int</span></span>  | <span data-ttu-id="9482b-139">Não</span><span class="sxs-lookup"><span data-stu-id="9482b-139">No</span></span>       | <span data-ttu-id="9482b-140">Um ID da Rede de Parceiros da Microsoft que identifica o parceiro.</span><span class="sxs-lookup"><span data-stu-id="9482b-140">A Microsoft Partner Network ID that identifies the partner.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9482b-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="9482b-141">Request headers</span></span>

<span data-ttu-id="9482b-142">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9482b-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9482b-143">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="9482b-143">Request body</span></span>

<span data-ttu-id="9482b-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9482b-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9482b-145">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="9482b-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/mpn?mpnId=9999999 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 560df6b9-6e53-4954-aed7-133477ac1194
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="9482b-146">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="9482b-146">REST response</span></span>

<span data-ttu-id="9482b-147">Se for bem sucedido, o organismo de resposta contém o recurso [MpnProfile](profile-resources.md#mpnprofile) para o parceiro.</span><span class="sxs-lookup"><span data-stu-id="9482b-147">If successful, the response body contains the [MpnProfile](profile-resources.md#mpnprofile) resource for the partner.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9482b-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="9482b-148">Response success and error codes</span></span>

<span data-ttu-id="9482b-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="9482b-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9482b-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="9482b-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9482b-151">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="9482b-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-success"></a><span data-ttu-id="9482b-152">Exemplo de resposta (sucesso)</span><span class="sxs-lookup"><span data-stu-id="9482b-152">Response example (success)</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 159
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: e39e0ddf-3fd0-4b7e-bb4e-8aebe242d3ee
MS-CV: s2GvkNgZsUSadxQX.0
MS-ServerId: 030011719
Date: Thu, 13 Apr 2017 18:13:40 GMT

{
    "mpnId": "4391507",
    "profileType": "MpnProfile",
    "links": {
        "self": {
            "uri": "/profiles/mpn",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "MpnProfile"
    }
}
```

### <a name="response-example-failure"></a><span data-ttu-id="9482b-153">Exemplo de resposta (falha)</span><span class="sxs-lookup"><span data-stu-id="9482b-153">Response example (failure)</span></span>

```http
HTTP/1.1 404 Not Found
Content-Length: 124
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: 560df6b9-6e53-4954-aed7-133477ac1194
MS-CV: sLRFZMWm+EKuL47u.0
MS-ServerId: 102030524
Date: Thu, 13 Apr 2017 18:26:51 GMT

{
    "code": 3000,
    "description": "Partner Organization with partner_id 9999999 could not be found",
    "data": [],
    "source": "PartnerFD"
}
```
