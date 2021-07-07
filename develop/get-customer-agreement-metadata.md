---
title: Obter metadados de contrato para o Contrato de Cliente Microsoft
description: Este artigo explica como obter metadados de acordo para o Microsoft Customer Agreement.
ms.date: 8/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: 5c20b317edf16b159050884070683880cf7e45bb
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025726"
---
# <a name="get-agreement-metadata-for-the-microsoft-customer-agreement"></a><span data-ttu-id="01d04-103">Obter metadados de contrato para o Contrato de Cliente Microsoft</span><span class="sxs-lookup"><span data-stu-id="01d04-103">Get agreement metadata for the Microsoft Customer Agreement</span></span>

<span data-ttu-id="01d04-104">**Aplica-se a**: Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="01d04-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="01d04-105">**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="01d04-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="01d04-106">Os metadados de acordo para o Microsoft Customer Agreement são atualmente suportados pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="01d04-106">Agreement metadata for Microsoft Customer Agreement is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="01d04-107">Tem de recuperar os metadados do acordo para o Acordo de Cliente da Microsoft antes de poder:</span><span class="sxs-lookup"><span data-stu-id="01d04-107">You must retrieve the agreement metadata for the Microsoft Customer Agreement before you can:</span></span>

- [<span data-ttu-id="01d04-108">Confirme a aceitação de um cliente do Acordo de Cliente da Microsoft</span><span class="sxs-lookup"><span data-stu-id="01d04-108">Confirm a customer's acceptance of the Microsoft Customer Agreement</span></span>](./confirm-customer-consent-customer-agreement.md)
- [<span data-ttu-id="01d04-109">Recupere um link de descarregamento para o modelo do Contrato de Cliente da Microsoft</span><span class="sxs-lookup"><span data-stu-id="01d04-109">Retrieve a download link for the Microsoft Customer Agreement template</span></span>](./download-customer-agreement-template.md)

## <a name="prerequisites"></a><span data-ttu-id="01d04-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="01d04-110">Prerequisites</span></span>

- <span data-ttu-id="01d04-111">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="01d04-111">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="01d04-112">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="01d04-112">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="01d04-113">Este cenário suporta apenas a autenticação app+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="01d04-113">This scenario supports App+User authentication only.</span></span>

## <a name="net-version-114-or-newer"></a><span data-ttu-id="01d04-114">.NET (versão 1.14 ou mais recente)</span><span class="sxs-lookup"><span data-stu-id="01d04-114">.NET (version 1.14 or newer)</span></span>

<span data-ttu-id="01d04-115">Para recuperar os metadados do acordo para o Acordo de Cliente da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="01d04-115">To retrieve the agreement metadata for Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="01d04-116">Primeiro, recupere a coleção **IAggregatePartner.AgreementDetails.**</span><span class="sxs-lookup"><span data-stu-id="01d04-116">First, retrieve the **IAggregatePartner.AgreementDetails** collection.</span></span>

2. <span data-ttu-id="01d04-117">Ligue para o método **ByAgreementType** para filtrar a coleção para o Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="01d04-117">Call **ByAgreementType** method to filter the collection to Microsoft Customer Agreement.</span></span>

3. <span data-ttu-id="01d04-118">Finalmente, ligue para o método **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="01d04-118">Finally, call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCustomerAgreement";

var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

<span data-ttu-id="01d04-119">Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="01d04-119">A complete sample can be found in the [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="01d04-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="01d04-120">REST request</span></span>

<span data-ttu-id="01d04-121">Para recuperar os metadados do acordo para o Acordo de Cliente da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="01d04-121">To retrieve the agreement metadata for Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="01d04-122">Crie um pedido DE REST para recuperar a coleção [AgreementMetaData.](./agreement-metadata-resources.md)</span><span class="sxs-lookup"><span data-stu-id="01d04-122">Create a REST request to retrieve the [AgreementMetaData](./agreement-metadata-resources.md) collection.</span></span>

2. <span data-ttu-id="01d04-123">Utilize o parâmetro de consulta de **acordoso** para estender o resultado apenas ao Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="01d04-123">Use the **agreementType** query parameter to scope the result to only the Microsoft Customer Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="01d04-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="01d04-124">Request syntax</span></span>

| <span data-ttu-id="01d04-125">Método</span><span class="sxs-lookup"><span data-stu-id="01d04-125">Method</span></span> | <span data-ttu-id="01d04-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="01d04-126">Request URI</span></span>                                                         |
|--------|---------------------------------------------------------------------|
| <span data-ttu-id="01d04-127">GET</span><span class="sxs-lookup"><span data-stu-id="01d04-127">GET</span></span>    | <span data-ttu-id="01d04-128">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="01d04-128">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="01d04-129">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="01d04-129">URI parameters</span></span>

| <span data-ttu-id="01d04-130">Nome</span><span class="sxs-lookup"><span data-stu-id="01d04-130">Name</span></span>                   | <span data-ttu-id="01d04-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="01d04-131">Type</span></span>     | <span data-ttu-id="01d04-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="01d04-132">Required</span></span> | <span data-ttu-id="01d04-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="01d04-133">Description</span></span>                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| <span data-ttu-id="01d04-134">tipo de acordo</span><span class="sxs-lookup"><span data-stu-id="01d04-134">agreement-type</span></span> | <span data-ttu-id="01d04-135">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="01d04-135">string</span></span> | <span data-ttu-id="01d04-136">No</span><span class="sxs-lookup"><span data-stu-id="01d04-136">No</span></span> | <span data-ttu-id="01d04-137">Utilize este parâmetro para estender a resposta de consulta ao tipo de acordo específico.</span><span class="sxs-lookup"><span data-stu-id="01d04-137">Use this parameter to scope the query response to specific agreement type.</span></span> <span data-ttu-id="01d04-138">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="01d04-138">The supported values are:</span></span> <br/><br/><span data-ttu-id="01d04-139">**MicrosoftCloudAgreement** que inclui metadados de acordo apenas do tipo *MicrosoftCloudAgreement*</span><span class="sxs-lookup"><span data-stu-id="01d04-139">**MicrosoftCloudAgreement** that includes agreement metadata only of the type *MicrosoftCloudAgreement*</span></span><br/><br/><span data-ttu-id="01d04-140">**MicrosoftCustomerAgreement** que inclui metadados de acordo apenas do tipo *MicrosoftCustomerAgreement*.</span><span class="sxs-lookup"><span data-stu-id="01d04-140">**MicrosoftCustomerAgreement** that includes agreement metadata only of the type *MicrosoftCustomerAgreement*.</span></span><br/><br/><span data-ttu-id="01d04-141">**\**_ que devolve todos os metadados do acordo. (Não use _\* \* \*_ a menos que o seu código tenha a lógica de tempo de execução necessária para lidar com tipos de acordos desconhecidos, porque a Microsoft pode introduzir metadados de acordo com novos tipos de acordo a qualquer momento.) <br/> <br/> _\* Nota:*\* Se o parâmetro URI não for especificado, a consulta predefine o **MicrosoftCloudAgreement** para retrocompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="01d04-141">**\**_ that returns all agreement metadata. (Don't use _*\**_ unless your code has the necessary runtime logic to handle unfamiliar agreement types because Microsoft may introduce agreement metadata with new agreement types at any time.)<br/><br/> _\* Note:*\* If the URI parameter isn't specified, the query defaults to **MicrosoftCloudAgreement** for backward compatibility.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="01d04-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="01d04-142">Request headers</span></span>

<span data-ttu-id="01d04-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="01d04-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="01d04-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="01d04-144">Request body</span></span>

<span data-ttu-id="01d04-145">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="01d04-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="01d04-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="01d04-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="01d04-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="01d04-147">REST response</span></span>

<span data-ttu-id="01d04-148">Se for bem sucedido, este método devolve uma coleção de recursos [ **AgreementMetaData**](./agreement-metadata-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="01d04-148">If successful, this method returns a collection of [**AgreementMetaData** resources](./agreement-metadata-resources.md) in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="01d04-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="01d04-149">Response success and error codes</span></span>

<span data-ttu-id="01d04-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="01d04-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="01d04-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="01d04-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="01d04-152">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="01d04-152">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="01d04-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="01d04-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 620
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "totalCount": 1,
    "items": [
        {
            "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
            "agreementType": "MicrosoftCustomerAgreement",
            "agreementLink": "https://aka.ms/customeragreement",
            "versionRank": 0
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
