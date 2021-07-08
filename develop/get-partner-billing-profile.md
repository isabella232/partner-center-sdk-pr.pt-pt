---
title: Obter perfil de faturação do parceiro
description: Obtém um objeto que representa o perfil de faturação do parceiro.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 225d8ea2d92933838ae47eaf3308276aa1f1684c
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548979"
---
# <a name="get-partner-billing-profile"></a><span data-ttu-id="b05fc-103">Obter perfil de faturação do parceiro</span><span class="sxs-lookup"><span data-stu-id="b05fc-103">Get partner billing profile</span></span>

<span data-ttu-id="b05fc-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b05fc-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b05fc-105">Obtém um objeto que representa o perfil de faturação do parceiro.</span><span class="sxs-lookup"><span data-stu-id="b05fc-105">Gets an object representing the partner's billing profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b05fc-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b05fc-106">Prerequisites</span></span>

- <span data-ttu-id="b05fc-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b05fc-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b05fc-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="b05fc-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="b05fc-109">C\#</span><span class="sxs-lookup"><span data-stu-id="b05fc-109">C\#</span></span>

<span data-ttu-id="b05fc-110">Para obter um perfil de faturação de parceiros, use a sua coleção **IAggregatePartner.Profiles** e ligue para a propriedade **BillingProfile.**</span><span class="sxs-lookup"><span data-stu-id="b05fc-110">To get a partner billing profile, use your **IAggregatePartner.Profiles** collection and call the **BillingProfile** property.</span></span> <span data-ttu-id="b05fc-111">Por fim, ligue para os métodos [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.getasync)</span><span class="sxs-lookup"><span data-stu-id="b05fc-111">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

BillingProfile billingProfile = partnerOperations.Profiles.BillingProfile.Get();
```

<span data-ttu-id="b05fc-112">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b05fc-112">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b05fc-113">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="b05fc-113">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b05fc-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b05fc-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b05fc-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b05fc-115">Request syntax</span></span>

| <span data-ttu-id="b05fc-116">Método</span><span class="sxs-lookup"><span data-stu-id="b05fc-116">Method</span></span>  | <span data-ttu-id="b05fc-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b05fc-117">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="b05fc-118">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b05fc-118">**GET**</span></span> | <span data-ttu-id="b05fc-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/faturação HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b05fc-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b05fc-120">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b05fc-120">Request headers</span></span>

<span data-ttu-id="b05fc-121">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b05fc-121">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b05fc-122">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b05fc-122">Request body</span></span>

<span data-ttu-id="b05fc-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b05fc-123">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b05fc-124">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b05fc-124">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a0dd6cde-b24c-413c-af24-416446dc5599
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
```

## <a name="rest-response"></a><span data-ttu-id="b05fc-125">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b05fc-125">REST response</span></span>

<span data-ttu-id="b05fc-126">Se for bem sucedido, este método devolve um objeto **BillingProfile** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="b05fc-126">If successful, this method returns a **BillingProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b05fc-127">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b05fc-127">Response success and error codes</span></span>

<span data-ttu-id="b05fc-128">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b05fc-128">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b05fc-129">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b05fc-129">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b05fc-130">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b05fc-130">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b05fc-131">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b05fc-131">Response example</span></span>

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
