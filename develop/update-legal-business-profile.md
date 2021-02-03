---
title: Atualizar perfil comercial legal do parceiro
description: Como atualizar o perfil de negócio legal do parceiro.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: parthpandyaMSFT
ms.author: parthp
ms.openlocfilehash: 6c61b51ab0680e36daa99c11dc8e8c3506259d29
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769601"
---
# <a name="update-the-partner-legal-business-profile"></a><span data-ttu-id="72b63-103">Atualizar perfil comercial legal do parceiro</span><span class="sxs-lookup"><span data-stu-id="72b63-103">Update the partner legal business profile</span></span>

<span data-ttu-id="72b63-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="72b63-104">**Applies To**</span></span>

- <span data-ttu-id="72b63-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="72b63-105">Partner Center</span></span>
- <span data-ttu-id="72b63-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="72b63-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="72b63-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="72b63-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="72b63-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="72b63-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="72b63-109">Como atualizar o perfil de negócio legal do parceiro.</span><span class="sxs-lookup"><span data-stu-id="72b63-109">How to update the partner legal business profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72b63-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="72b63-110">Prerequisites</span></span>

- <span data-ttu-id="72b63-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="72b63-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="72b63-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="72b63-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="72b63-113">C\#</span><span class="sxs-lookup"><span data-stu-id="72b63-113">C\#</span></span>

<span data-ttu-id="72b63-114">Para atualizar o perfil de negócio legal do parceiro, primeiro instantaneamente um objeto **LegalBusinessProfile** e povoá-lo com o perfil existente.</span><span class="sxs-lookup"><span data-stu-id="72b63-114">To update the partner legal business profile, first instantiate a **LegalBusinessProfile** object and populate it with the existing profile.</span></span> <span data-ttu-id="72b63-115">Para mais informações, consulte [o perfil de negócios do parceiro.](get-legal-business-profile.md)</span><span class="sxs-lookup"><span data-stu-id="72b63-115">For more information, see [Get the partner legal business profile](get-legal-business-profile.md).</span></span> <span data-ttu-id="72b63-116">Em seguida, atualize as propriedades que precisa de alterar.</span><span class="sxs-lookup"><span data-stu-id="72b63-116">Then, update the properties that you need to change.</span></span> <span data-ttu-id="72b63-117">O exemplo de código que se segue ilustra a alteração do endereço e dos números de telefone de contacto primários.</span><span class="sxs-lookup"><span data-stu-id="72b63-117">The following code example illustrates changing the address and primary contact phone numbers.</span></span>

<span data-ttu-id="72b63-118">Em seguida, obtenha uma interface para a coleção de operações de perfil de parceiro da propriedade **IAggregatePartner.Profiles.**</span><span class="sxs-lookup"><span data-stu-id="72b63-118">Next, get an interface to the partner profile operations collection from the **IAggregatePartner.Profiles** property.</span></span> <span data-ttu-id="72b63-119">Em seguida, recupere o valor do **imóvel LegalBusinessProfile** para obter uma interface para operações de perfil de negócio legal.</span><span class="sxs-lookup"><span data-stu-id="72b63-119">Then, retrieve the value of the **LegalBusinessProfile** property to get an interface to legal business profile operations.</span></span> <span data-ttu-id="72b63-120">Por fim, ligue para o método [**Update**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.update) ou [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.updateasync) com o objeto alterado para atualizar o perfil.</span><span class="sxs-lookup"><span data-stu-id="72b63-120">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.update) or [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.updateasync) method with the changed object to update the profile.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var legalBusinessProfile = partnerOperations.Profiles.LegalBusinessProfile.Get();

// Change the address and primary contact phone number.
legalBusinessProfile.Address.PhoneNumber = "4255550110";
legalBusinessProfile.PrimaryContact.PhoneNumber = "4255550110";

// Apply changes to the profile.
var updatedLegalBusinessProfile = partnerOperations.Profiles.LegalBusinessProfile.Update(legalBusinessProfile);
```

## <a name="rest-request"></a><span data-ttu-id="72b63-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="72b63-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="72b63-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="72b63-122">Request syntax</span></span>

| <span data-ttu-id="72b63-123">Método</span><span class="sxs-lookup"><span data-stu-id="72b63-123">Method</span></span>  | <span data-ttu-id="72b63-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="72b63-124">Request URI</span></span>                                                                    |
|---------|--------------------------------------------------------------------------------|
| <span data-ttu-id="72b63-125">**PUT**</span><span class="sxs-lookup"><span data-stu-id="72b63-125">**PUT**</span></span> | <span data-ttu-id="72b63-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/perfis/negócio legal HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="72b63-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/legalbusiness HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="72b63-127">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="72b63-127">Request headers</span></span>

<span data-ttu-id="72b63-128">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="72b63-128">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="72b63-129">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="72b63-129">Request body</span></span>

<span data-ttu-id="72b63-130">O recurso de perfil de negócio legal.</span><span class="sxs-lookup"><span data-stu-id="72b63-130">The legal business profile resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="72b63-131">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="72b63-131">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/legalbusiness HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4549ac0c-0f1d-4d8f-b02f-6d36fadcccee
MS-CorrelationId: aa2a0d8c-7a41-470f-97ae-b82e6c338ee4
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 806
Expect: 100-continue

{
    "CompanyName": "Lucerne Publishing",
    "Address": {
        "Country": "US",
        "Region": null,
        "City": "Redmond",
        "State": "WA",
        "AddressLine1": "123 Main Street",
        "AddressLine2": "",
        "PostalCode": "98052",
        "FirstName": "Gena",
        "LastName": "Soto",
        "PhoneNumber": "4255550110"
    },
    "PrimaryContact": {
        "FirstName": "Gena",
        "LastName": "Soto",
        "Email": "gena@lucernepublishing.com",
        "PhoneNumber": "4255550110"
    },
    "CompanyApproverAddress": {
        "Country": "US",
        "Region": null,
        "City": "Redmond",
        "State": "WA",
        "AddressLine1": "123 Main Street",
        "AddressLine2": "",
        "PostalCode": "98052",
        "FirstName": null,
        "LastName": null,
        "PhoneNumber": null
    },
    "CompanyApproverEmail": "gena@lucernepublishing.com",
    "VettingStatus": "authorized",
    "VettingSubStatus": "none",
    "Links": {
        "Self": {
            "Uri": "/profiles/legalbusiness",
            "Method": "GET",
            "Headers": []
        }
    },
    "Attributes": {
        "ObjectType": "LegalBusinessProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="72b63-132">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="72b63-132">REST response</span></span>

<span data-ttu-id="72b63-133">Se for bem sucedido, o organismo de resposta contém o **LegalBusinessProfile** atualizado</span><span class="sxs-lookup"><span data-stu-id="72b63-133">If successful, the response body contains the updated **LegalBusinessProfile**</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="72b63-134">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="72b63-134">Response success and error codes</span></span>

<span data-ttu-id="72b63-135">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="72b63-135">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="72b63-136">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="72b63-136">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="72b63-137">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="72b63-137">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="72b63-138">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="72b63-138">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1157
Content-Type: application/json; charset=utf-8
MS-CorrelationId: aa2a0d8c-7a41-470f-97ae-b82e6c338ee4
MS-RequestId: 4549ac0c-0f1d-4d8f-b02f-6d36fadcccee
MS-CV: KZLU42qJ4EObO75q.0
MS-ServerId: 030020643
Date: Tue, 21 Mar 2017 22:03:15 GMT

{
    "companyName": "Lucerne Publishing",
    "address": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "123 Main Street",
        "addressLine2": "",
        "postalCode": "98052",
        "firstName": "Gena",
        "lastName": "Soto",
        "phoneNumber": "4255550110"
    },
    "primaryContact": {
        "firstName": "Gena",
        "lastName": "Soto",
        "email": "gena@lucernepublishing.com",
        "phoneNumber": "4255550110"
    },
    "companyApproverAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "123 Main Street",
        "addressLine2": "",
        "postalCode": "98052"
    },
    "companyApproverEmail": "gena@lucernepublishing.com",
    "vettingStatus": "authorized",
    "vettingSubStatus": "none",
    "profileType": "LegalBusinessProfile",
    "links": {
        "self": {
            "uri": "/profiles/legalbusiness",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "LegalBusinessProfile"
    }
}
```
