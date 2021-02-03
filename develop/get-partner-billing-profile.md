---
title: Obter perfil de faturação do parceiro
description: Obtém um objeto que representa o perfil de faturação do parceiro.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 94c5ff8fc351282ca3b4721511f02ba6a0cc403c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769841"
---
# <a name="get-partner-billing-profile"></a><span data-ttu-id="97ba5-103">Obter perfil de faturação do parceiro</span><span class="sxs-lookup"><span data-stu-id="97ba5-103">Get partner billing profile</span></span>

<span data-ttu-id="97ba5-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="97ba5-104">**Applies To**</span></span>

- <span data-ttu-id="97ba5-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="97ba5-105">Partner Center</span></span>
- <span data-ttu-id="97ba5-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="97ba5-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="97ba5-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="97ba5-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="97ba5-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="97ba5-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="97ba5-109">Obtém um objeto que representa o perfil de faturação do parceiro.</span><span class="sxs-lookup"><span data-stu-id="97ba5-109">Gets an object representing the partner's billing profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="97ba5-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="97ba5-110">Prerequisites</span></span>

- <span data-ttu-id="97ba5-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="97ba5-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="97ba5-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="97ba5-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="97ba5-113">C\#</span><span class="sxs-lookup"><span data-stu-id="97ba5-113">C\#</span></span>

<span data-ttu-id="97ba5-114">Para obter um perfil de faturação de parceiros, use a sua coleção **IAggregatePartner.Profiles** e ligue para a propriedade **BillingProfile.**</span><span class="sxs-lookup"><span data-stu-id="97ba5-114">To get a partner billing profile, use your **IAggregatePartner.Profiles** collection and call the **BillingProfile** property.</span></span> <span data-ttu-id="97ba5-115">Por fim, ligue para os métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.getasync)</span><span class="sxs-lookup"><span data-stu-id="97ba5-115">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

BillingProfile billingProfile = partnerOperations.Profiles.BillingProfile.Get();
```

<span data-ttu-id="97ba5-116">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="97ba5-116">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="97ba5-117">**Projeto**: PartnerCenterSDK.FeaturesSamples **Class**: GetBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="97ba5-117">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="97ba5-118">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="97ba5-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="97ba5-119">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="97ba5-119">Request syntax</span></span>

| <span data-ttu-id="97ba5-120">Método</span><span class="sxs-lookup"><span data-stu-id="97ba5-120">Method</span></span>  | <span data-ttu-id="97ba5-121">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="97ba5-121">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="97ba5-122">**Obter**</span><span class="sxs-lookup"><span data-stu-id="97ba5-122">**GET**</span></span> | <span data-ttu-id="97ba5-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/faturação HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="97ba5-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="97ba5-124">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="97ba5-124">Request headers</span></span>

<span data-ttu-id="97ba5-125">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="97ba5-125">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="97ba5-126">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="97ba5-126">Request body</span></span>

<span data-ttu-id="97ba5-127">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="97ba5-127">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="97ba5-128">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="97ba5-128">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a0dd6cde-b24c-413c-af24-416446dc5599
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
```

## <a name="rest-response"></a><span data-ttu-id="97ba5-129">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="97ba5-129">REST response</span></span>

<span data-ttu-id="97ba5-130">Se for bem sucedido, este método devolve um objeto **BillingProfile** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="97ba5-130">If successful, this method returns a **BillingProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="97ba5-131">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="97ba5-131">Response success and error codes</span></span>

<span data-ttu-id="97ba5-132">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="97ba5-132">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="97ba5-133">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="97ba5-133">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="97ba5-134">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="97ba5-134">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="97ba5-135">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="97ba5-135">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 568
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
MS-RequestId: a0dd6cde-b24c-413c-af24-416446dc5599
Date: Tue, 22 Mar 2016 17:10:02 GMT

{
    "companyName":"TEST_TEST_BugBash1",
    "address":{
        "country":"US",
        "city":"Redmond",
        "state":"WA",
        "addressLine1":"1 Microsoft Way",
        "addressLine2":"","postalCode":"98052"
    },
    "primaryContact":{
        "firstName":"James",
        "lastName":"Burk",
        "phoneNumber":"2066017143"
    },
    "purchaseOrderNumber":"9888",
    "taxId":"12-345678",
    "billingCurrency":"USD",
    "profileType":"BillingProfile",
    "links":{
        "self":{
            "uri":"/profiles/billing",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "etag":<etag>,
        "objectType":"BillingProfile"
    }
}
```
