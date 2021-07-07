---
title: Atualizar perfil de faturação do parceiro
description: Atualiza o perfil de faturação de um parceiro.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: parthpandyaMSFT
ms.author: parthp
ms.openlocfilehash: 2b09a0045df15d774c892a59fba8502d4d4f7024
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529771"
---
# <a name="update-the-partner-billing-profile"></a><span data-ttu-id="17e71-103">Atualizar perfil de faturação do parceiro</span><span class="sxs-lookup"><span data-stu-id="17e71-103">Update the partner billing profile</span></span>

<span data-ttu-id="17e71-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="17e71-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="17e71-105">Atualiza o perfil de faturação de um parceiro</span><span class="sxs-lookup"><span data-stu-id="17e71-105">Updates a partner's billing profile</span></span>

## <a name="prerequisites"></a><span data-ttu-id="17e71-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="17e71-106">Prerequisites</span></span>

- <span data-ttu-id="17e71-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="17e71-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="17e71-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="17e71-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="17e71-109">C\#</span><span class="sxs-lookup"><span data-stu-id="17e71-109">C\#</span></span>

<span data-ttu-id="17e71-110">Para atualizar um perfil de faturação de parceiros, recupere o perfil existente.</span><span class="sxs-lookup"><span data-stu-id="17e71-110">To update a partner billing profile, retrieve the existing profile.</span></span> <span data-ttu-id="17e71-111">Assim que atualizar o perfil, utilize a sua coleção **IAggregatePartner.Profiles** e ligue para a propriedade **BillingProfile.**</span><span class="sxs-lookup"><span data-stu-id="17e71-111">Once you have updated the profile, use your **IAggregatePartner.Profiles** collection and call the **BillingProfile** property.</span></span> <span data-ttu-id="17e71-112">Por fim, ligue para o método **'Atualização).).**</span><span class="sxs-lookup"><span data-stu-id="17e71-112">Finally, call the **Update()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

BillingProfile existingBillingProfile = partnerOperations.Profiles.BillingProfile.Get();

// update the profile with a purchase order number
existingBillingProfile.PurchaseOrderNumber = new Random().Next(9000, 10000).ToString(CultureInfo.InvariantCulture);

BillingProfile updatedPartnerBillingProfile = partnerOperations.Profiles.BillingProfile.Update(existingBillingProfile);
```

<span data-ttu-id="17e71-113">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="17e71-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="17e71-114">**Project**: Partner Center SDK Samples **Class**: UpdateBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="17e71-114">**Project**: Partner Center SDK Samples **Class**: UpdateBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="17e71-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="17e71-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="17e71-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="17e71-116">Request syntax</span></span>

| <span data-ttu-id="17e71-117">Método</span><span class="sxs-lookup"><span data-stu-id="17e71-117">Method</span></span>  | <span data-ttu-id="17e71-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="17e71-118">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="17e71-119">**PUT**</span><span class="sxs-lookup"><span data-stu-id="17e71-119">**PUT**</span></span> | <span data-ttu-id="17e71-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/faturação HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="17e71-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="17e71-121">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="17e71-121">Request headers</span></span>

<span data-ttu-id="17e71-122">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="17e71-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="17e71-123">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="17e71-123">Request body</span></span>

<span data-ttu-id="17e71-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="17e71-124">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="17e71-125">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="17e71-125">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 9231559e-ed95-41e4-810b-e754ae32dc2f
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
Content-Length: 613
Expect: 100-continue

{
    "CompanyName":"TEST_TEST_BugBash1",
    "Address":{
        "Country":"US",
        "Region":null,
        "City":"Redmond",
        "State":"WA",
        "AddressLine1":"1 Microsoft Way",
        "AddressLine2":"","PostalCode":"98052",
        "FirstName":null,
        "LastName":null,
        "PhoneNumber":null
    },
    "PrimaryContact":{
        "FirstName":"Test",
        "LastName":"Customer",
        "Email":null,
        "PhoneNumber":""
    },
    "PurchaseOrderNumber":"9888",
    "TaxId":<TaxId>,
    "BillingCurrency":"USD",
    "Links":{
        "Self":{
            "Uri":"/profiles/billing",
            "Method":"GET","Headers":[]
        }
    },
    "Attributes":{
        "Etag":<etag>,
        "ObjectType":"BillingProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="17e71-126">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="17e71-126">REST response</span></span>

<span data-ttu-id="17e71-127">Se for bem sucedido, este método devolve um objeto **BillingProfile** no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="17e71-127">If successful, this method returns a **BillingProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="17e71-128">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="17e71-128">Response success and error codes</span></span>

<span data-ttu-id="17e71-129">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="17e71-129">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="17e71-130">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="17e71-130">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="17e71-131">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="17e71-131">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="17e71-132">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="17e71-132">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 568
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
MS-RequestId: 9231559e-ed95-41e4-810b-e754ae32dc2f
Date: Mon, 21 Mar 2016 05:47:16 GMT

{
    "CompanyName":"TEST_TEST_BugBash1",
    "Address":{
        "Country":"US",
        "Region":null,
        "City":"Redmond",
        "State":"WA",
        "AddressLine1":"1 Microsoft Way",
        "AddressLine2":"","PostalCode":"98052",
        "FirstName":null,
        "LastName":null,
        "PhoneNumber":null
    },
    "PrimaryContact":{
        "FirstName":"Test",
        "LastName":"Customer",
        "Email":null,
        "PhoneNumber":""
    },
    "PurchaseOrderNumber":"9888",
    "TaxId":<TaxId>,
    "BillingCurrency":"USD",
    "Links":{
        "Self":{
            "Uri":"/profiles/billing",
            "Method":"GET","Headers":[]
        }
    },
    "Attributes":{
        "Etag":<etag>,
        "ObjectType":"BillingProfile"
    }
}
```
