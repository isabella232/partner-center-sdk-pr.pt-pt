---
title: Obter metadados de contrato para o Contrato de Cliente Microsoft
description: Este artigo explica como obter metadados de acordo para o Microsoft Customer Agreement.
ms.date: 8/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: c3ebecc51859c9d2240d319d823f7e555eaecc27
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769433"
---
# <a name="get-agreement-metadata-for-the-microsoft-customer-agreement"></a><span data-ttu-id="2cf92-103">Obter metadados de contrato para o Contrato de Cliente Microsoft</span><span class="sxs-lookup"><span data-stu-id="2cf92-103">Get agreement metadata for the Microsoft Customer Agreement</span></span>

<span data-ttu-id="2cf92-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="2cf92-104">**Applies to:**</span></span>

- <span data-ttu-id="2cf92-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="2cf92-105">Partner Center</span></span>

<span data-ttu-id="2cf92-106">Os metadados de acordo para o Acordo de Cliente da Microsoft são atualmente suportados pelo Partner Center apenas na nuvem pública da *Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="2cf92-106">Agreement metadata for Microsoft Customer Agreement is currently supported by Partner Center only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="2cf92-107">Não se aplica a:</span><span class="sxs-lookup"><span data-stu-id="2cf92-107">It doesn't apply to:</span></span>

- <span data-ttu-id="2cf92-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="2cf92-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="2cf92-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="2cf92-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="2cf92-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2cf92-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2cf92-111">Tem de recuperar os metadados do acordo para o Acordo de Cliente da Microsoft antes de poder:</span><span class="sxs-lookup"><span data-stu-id="2cf92-111">You must retrieve the agreement metadata for the Microsoft Customer Agreement before you can:</span></span>

- [<span data-ttu-id="2cf92-112">Confirme a aceitação de um cliente do Acordo de Cliente da Microsoft</span><span class="sxs-lookup"><span data-stu-id="2cf92-112">Confirm a customer's acceptance of the Microsoft Customer Agreement</span></span>](./confirm-customer-consent-customer-agreement.md)
- [<span data-ttu-id="2cf92-113">Recupere um link de descarregamento para o modelo do Contrato de Cliente da Microsoft</span><span class="sxs-lookup"><span data-stu-id="2cf92-113">Retrieve a download link for the Microsoft Customer Agreement template</span></span>](./download-customer-agreement-template.md)

## <a name="prerequisites"></a><span data-ttu-id="2cf92-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2cf92-114">Prerequisites</span></span>

- <span data-ttu-id="2cf92-115">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="2cf92-115">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="2cf92-116">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2cf92-116">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="2cf92-117">Este cenário suporta apenas a autenticação app+Utilizador.</span><span class="sxs-lookup"><span data-stu-id="2cf92-117">This scenario supports App+User authentication only.</span></span>

## <a name="net-version-114-or-newer"></a><span data-ttu-id="2cf92-118">.NET (versão 1.14 ou mais recente)</span><span class="sxs-lookup"><span data-stu-id="2cf92-118">.NET (version 1.14 or newer)</span></span>

<span data-ttu-id="2cf92-119">Para recuperar os metadados do acordo para o Acordo de Cliente da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="2cf92-119">To retrieve the agreement metadata for Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="2cf92-120">Primeiro, recupere a coleção **IAggregatePartner.AgreementDetails.**</span><span class="sxs-lookup"><span data-stu-id="2cf92-120">First, retrieve the **IAggregatePartner.AgreementDetails** collection.</span></span>

2. <span data-ttu-id="2cf92-121">Ligue para o método **ByAgreementType** para filtrar a coleção para o Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="2cf92-121">Call **ByAgreementType** method to filter the collection to Microsoft Customer Agreement.</span></span>

3. <span data-ttu-id="2cf92-122">Finalmente, ligue para o método **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="2cf92-122">Finally, call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCustomerAgreement";

var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

<span data-ttu-id="2cf92-123">Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="2cf92-123">A complete sample can be found in the [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="2cf92-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2cf92-124">REST request</span></span>

<span data-ttu-id="2cf92-125">Para recuperar os metadados do acordo para o Acordo de Cliente da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="2cf92-125">To retrieve the agreement metadata for Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="2cf92-126">Crie um pedido DE REST para recuperar a coleção [AgreementMetaData.](./agreement-metadata-resources.md)</span><span class="sxs-lookup"><span data-stu-id="2cf92-126">Create a REST request to retrieve the [AgreementMetaData](./agreement-metadata-resources.md) collection.</span></span>

2. <span data-ttu-id="2cf92-127">Utilize o parâmetro de consulta de **acordoso** para estender o resultado apenas ao Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="2cf92-127">Use the **agreementType** query parameter to scope the result to only the Microsoft Customer Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2cf92-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cf92-128">Request syntax</span></span>

| <span data-ttu-id="2cf92-129">Método</span><span class="sxs-lookup"><span data-stu-id="2cf92-129">Method</span></span> | <span data-ttu-id="2cf92-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2cf92-130">Request URI</span></span>                                                         |
|--------|---------------------------------------------------------------------|
| <span data-ttu-id="2cf92-131">GET</span><span class="sxs-lookup"><span data-stu-id="2cf92-131">GET</span></span>    | <span data-ttu-id="2cf92-132">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2cf92-132">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="2cf92-133">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="2cf92-133">URI parameters</span></span>

| <span data-ttu-id="2cf92-134">Nome</span><span class="sxs-lookup"><span data-stu-id="2cf92-134">Name</span></span>                   | <span data-ttu-id="2cf92-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="2cf92-135">Type</span></span>     | <span data-ttu-id="2cf92-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="2cf92-136">Required</span></span> | <span data-ttu-id="2cf92-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="2cf92-137">Description</span></span>                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| <span data-ttu-id="2cf92-138">tipo de acordo</span><span class="sxs-lookup"><span data-stu-id="2cf92-138">agreement-type</span></span> | <span data-ttu-id="2cf92-139">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="2cf92-139">string</span></span> | <span data-ttu-id="2cf92-140">No</span><span class="sxs-lookup"><span data-stu-id="2cf92-140">No</span></span> | <span data-ttu-id="2cf92-141">Utilize este parâmetro para estender a resposta de consulta ao tipo de acordo específico.</span><span class="sxs-lookup"><span data-stu-id="2cf92-141">Use this parameter to scope the query response to specific agreement type.</span></span> <span data-ttu-id="2cf92-142">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="2cf92-142">The supported values are:</span></span> <br/><br/><span data-ttu-id="2cf92-143">**MicrosoftCloudAgreement** que inclui metadados de acordo apenas do tipo *MicrosoftCloudAgreement*</span><span class="sxs-lookup"><span data-stu-id="2cf92-143">**MicrosoftCloudAgreement** that includes agreement metadata only of the type *MicrosoftCloudAgreement*</span></span><br/><br/><span data-ttu-id="2cf92-144">**MicrosoftCustomerAgreement** que inclui metadados de acordo apenas do tipo *MicrosoftCustomerAgreement*.</span><span class="sxs-lookup"><span data-stu-id="2cf92-144">**MicrosoftCustomerAgreement** that includes agreement metadata only of the type *MicrosoftCustomerAgreement*.</span></span><br/><br/><span data-ttu-id="2cf92-145">**\*** que devolve todos os metadados do acordo.</span><span class="sxs-lookup"><span data-stu-id="2cf92-145">**\*** that returns all agreement metadata.</span></span> <span data-ttu-id="2cf92-146">(Não utilize **\*** a menos que o seu código tenha a lógica de tempo de execução necessária para lidar com tipos de acordos desconhecidos porque a Microsoft pode introduzir metadados de acordo com novos tipos de acordo a qualquer momento.)</span><span class="sxs-lookup"><span data-stu-id="2cf92-146">(Don't use **\*** unless your code has the necessary runtime logic to handle unfamiliar agreement types because Microsoft may introduce agreement metadata with new agreement types at any time.)</span></span><br/><br/> <span data-ttu-id="2cf92-147">**Nota:** Se o parâmetro URI não for especificado, a consulta predefine o **MicrosoftCloudAgreement** para retrocompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="2cf92-147">**Note:** If the URI parameter isn't specified, the query defaults to **MicrosoftCloudAgreement** for backward compatibility.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="2cf92-148">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2cf92-148">Request headers</span></span>

<span data-ttu-id="2cf92-149">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2cf92-149">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2cf92-150">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="2cf92-150">Request body</span></span>

<span data-ttu-id="2cf92-151">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2cf92-151">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="2cf92-152">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="2cf92-152">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="2cf92-153">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2cf92-153">REST response</span></span>

<span data-ttu-id="2cf92-154">Se for bem sucedido, este método devolve uma coleção de recursos [ **AgreementMetaData**](./agreement-metadata-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="2cf92-154">If successful, this method returns a collection of [**AgreementMetaData** resources](./agreement-metadata-resources.md) in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2cf92-155">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2cf92-155">Response success and error codes</span></span>

<span data-ttu-id="2cf92-156">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2cf92-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="2cf92-157">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2cf92-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2cf92-158">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2cf92-158">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2cf92-159">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="2cf92-159">Response example</span></span>

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
