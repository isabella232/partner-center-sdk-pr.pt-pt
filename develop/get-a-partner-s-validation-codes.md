---
title: Obtenha os códigos de validação Nuvem da Comunidade Governamental de um parceiro
description: Como obter os códigos de validação Nuvem da Comunidade Governamental de um parceiro.
ms.date: 11/08/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: 04bccf587628337004a5825b534048945f791839
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873875"
---
# <a name="get-a-partners-validation-codes"></a><span data-ttu-id="ca0c5-103">Obter os códigos de validação de um parceiro</span><span class="sxs-lookup"><span data-stu-id="ca0c5-103">Get a partner's validation codes</span></span>

<span data-ttu-id="ca0c5-104">Este artigo descreve como obter uma coleção de códigos de validação Nuvem da Comunidade Governamental de um parceiro.</span><span class="sxs-lookup"><span data-stu-id="ca0c5-104">This article describes how to get a collection of a partner's Government Community Cloud validation codes.</span></span> <span data-ttu-id="ca0c5-105">Um código de validação é necessário para criar um cliente na nuvem comunitária do governo.</span><span class="sxs-lookup"><span data-stu-id="ca0c5-105">A validation code is required to create a customer in the government community cloud.</span></span>

<span data-ttu-id="ca0c5-106">Se estiver interessado em ter a sua organização ou organização do seu cliente aprovada para Office 365 Administração Pública GCC para CSP, consulte [Office 365 Administração Pública GCC para critérios de elegibilidade do CSP Partner e do Cliente.](/partner-center/csp-gcc-validate)</span><span class="sxs-lookup"><span data-stu-id="ca0c5-106">If you are interested in having your organization or your customer's organization approved for Office 365 Government GCC for CSP, see [Office 365 Government GCC for CSP Partner and Customer eligibility criteria](/partner-center/csp-gcc-validate).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca0c5-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ca0c5-107">Prerequisites</span></span>

- <span data-ttu-id="ca0c5-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ca0c5-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ca0c5-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="ca0c5-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="ca0c5-110">Validação confirmada após o preenchimento do formulário [aqui.](https://products.office.com/government/eligibility-validation?ReqType=CSPPartner)</span><span class="sxs-lookup"><span data-stu-id="ca0c5-110">Confirmed validation after filling out form [here](https://products.office.com/government/eligibility-validation?ReqType=CSPPartner).</span></span>

- <span data-ttu-id="ca0c5-111">Um cliente sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="ca0c5-111">A customer without a qualification.</span></span>

## <a name="c"></a><span data-ttu-id="ca0c5-112">C\#</span><span class="sxs-lookup"><span data-stu-id="ca0c5-112">C\#</span></span>

<span data-ttu-id="ca0c5-113">Para obter uma lista de todos os códigos de validação de um parceiro, ligue para **GetValidationCodes**.</span><span class="sxs-lookup"><span data-stu-id="ca0c5-113">To get a list of all of a partner's validation codes, call **GetValidationCodes**.</span></span>

``` csharp
// create the partner operations
IAggregatePartner partnerOperations = PartnerService.Instance.CreatePartnerOperations(credentials);

var gccValidations = partnerOperations.Validations.GetValidationCodes();
```

## <a name="rest-request"></a><span data-ttu-id="ca0c5-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="ca0c5-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ca0c5-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca0c5-115">Request syntax</span></span>

| <span data-ttu-id="ca0c5-116">Método</span><span class="sxs-lookup"><span data-stu-id="ca0c5-116">Method</span></span>  | <span data-ttu-id="ca0c5-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="ca0c5-117">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ca0c5-118">**Obter**</span><span class="sxs-lookup"><span data-stu-id="ca0c5-118">**GET**</span></span> | <span data-ttu-id="ca0c5-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/all/validations HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ca0c5-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/all/validations HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ca0c5-120">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="ca0c5-120">Request headers</span></span>

<span data-ttu-id="ca0c5-121">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ca0c5-121">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ca0c5-122">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="ca0c5-122">Request body</span></span>

<span data-ttu-id="ca0c5-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ca0c5-123">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ca0c5-124">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="ca0c5-124">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/all/validations HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 283b9b70-963a-4159-9920-f2bdf7ab7fce
MS-RequestId: 7266f5f6-30ca-4672-9eb6-6c9d6dd0e9d3
```

## <a name="rest-response"></a><span data-ttu-id="ca0c5-125">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="ca0c5-125">REST response</span></span>

<span data-ttu-id="ca0c5-126">Se for bem sucedido, este método devolve uma lista de recursos [**validationCode**](utility-resources.md#validationcode) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="ca0c5-126">If successful, this method returns a list of [**ValidationCode**](utility-resources.md#validationcode) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ca0c5-127">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="ca0c5-127">Response success and error codes</span></span>

<span data-ttu-id="ca0c5-128">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="ca0c5-128">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ca0c5-129">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="ca0c5-129">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ca0c5-130">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="ca0c5-130">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ca0c5-131">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="ca0c5-131">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 434
Content-Type: application/json
MS-CorrelationId: 283b9b70-963a-4159-9920-f2bdf7ab7fce
MS-RequestId: 7266f5f6-30ca-4672-9eb6-6c9d6dd0e9d3

[
  {
    "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d",
    "organizationName": "Contoso, Inc.",
    "validationId": "12345",
    "maxCreates": 5,
    "remainingCreates": 4,
    "eTag": "W/\"datetime'2018-10-10T18%3A49%3A58.727348Z'\""
  },
  {
    "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d",
    "organizationName": "Contoso, Inc. Finance Department",
    "validationId": "987654",
    "maxCreates": 5,
    "remainingCreates": 5,
    "eTag": "W/\"datetime'2018-10-19T17%3A51%3A45.6584512Z'\""
  }
]
```
