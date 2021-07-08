---
title: Obter metadados de contrato para o Contrato da Microsoft Cloud
description: Este artigo explica como obter metadados de acordo para o Microsoft Cloud Agreement.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 2588327e72a13de75eb9e02675edbd535491adc4
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760798"
---
# <a name="get-agreement-metadata-for-microsoft-cloud-agreement"></a><span data-ttu-id="9b59d-103">Obter metadados de contrato para o Contrato da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="9b59d-103">Get agreement metadata for Microsoft Cloud Agreement</span></span>

<span data-ttu-id="9b59d-104">**Aplica-se a**: Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="9b59d-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="9b59d-105">**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9b59d-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9b59d-106">O recurso **AgreementMetaData** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b59d-106">The **AgreementMetaData** resource is currently supported by Partner Center in the Microsoft public cloud only.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b59d-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9b59d-107">Prerequisites</span></span>

- <span data-ttu-id="9b59d-108">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.9 ou a mais recente.</span><span class="sxs-lookup"><span data-stu-id="9b59d-108">If you are using the Partner Center .NET SDK, version 1.9 or newer is required.</span></span>

- <span data-ttu-id="9b59d-109">Se estiver a utilizar o Partner Center Java SDK, é necessária a versão 1.8 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="9b59d-109">If you are using the Partner Center Java SDK, version 1.8 or newer is required.</span></span>

- <span data-ttu-id="9b59d-110">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9b59d-110">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="9b59d-111">Este cenário suporta a app + a autenticação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="9b59d-111">This scenario supports app + user authentication.</span></span>

## <a name="net-version-114-or-newer"></a><span data-ttu-id="9b59d-112">.NET (versão 1.14 ou mais recente)</span><span class="sxs-lookup"><span data-stu-id="9b59d-112">.NET (version 1.14 or newer)</span></span>

<span data-ttu-id="9b59d-113">Para recuperar os metadados do acordo para o Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="9b59d-113">To retrieve the agreement metadata for Microsoft Cloud Agreement:</span></span>

1. <span data-ttu-id="9b59d-114">Primeiro, recupere a coleção **IAggregatePartner.AgreementDetails.**</span><span class="sxs-lookup"><span data-stu-id="9b59d-114">First, retrieve the **IAggregatePartner.AgreementDetails** collection.</span></span>

2. <span data-ttu-id="9b59d-115">Ligue para o método **ByAgreementType** para filtrar a coleção para o Microsoft Cloud Agreement.</span><span class="sxs-lookup"><span data-stu-id="9b59d-115">Call **ByAgreementType** method to filter the collection to Microsoft Cloud Agreement.</span></span>

3. <span data-ttu-id="9b59d-116">Finalmente, ligue para o método **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="9b59d-116">Finally, call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCloudAgreement";

var microsoftCloudAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

<span data-ttu-id="9b59d-117">Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="9b59d-117">A complete sample can be found in the [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="net-version-19---113"></a><span data-ttu-id="9b59d-118">.NET (versão 1.9 - 1.13)</span><span class="sxs-lookup"><span data-stu-id="9b59d-118">.NET (version 1.9 - 1.13)</span></span>

<span data-ttu-id="9b59d-119">Para recuperar metadados de acordo para o Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="9b59d-119">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="9b59d-120">Primeiro, recupere a coleção **IAggregatePartner.AgreementDetails** e, em seguida, ligue para os métodos **Get** or **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="9b59d-120">First retrieve the **IAggregatePartner.AgreementDetails** collection and then call the **Get** or **GetAsync** methods.</span></span> <span data-ttu-id="9b59d-121">Em seguida, procure o item dentro da coleção, que corresponde ao Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="9b59d-121">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```csharp
// IAggregatePartner partnerOperations;

var agreements = partnerOperations.AgreementDetails.Get();

AgreementMetaData microsoftCloudAgreement = agreements.Items.FirstOrDefault (agr => agr.AgreementType == AgreementType.MicrosoftCloudAgreement);
```

## <a name="java"></a><span data-ttu-id="9b59d-122">Java</span><span class="sxs-lookup"><span data-stu-id="9b59d-122">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="9b59d-123">Para recuperar metadados de acordo para o Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="9b59d-123">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="9b59d-124">Primeiro ligue para a função **IAggregatePartner.getAgreementDetails** e, em seguida, ligue para a função **get.**</span><span class="sxs-lookup"><span data-stu-id="9b59d-124">First call the **IAggregatePartner.getAgreementDetails** function and then call the **get** function.</span></span> <span data-ttu-id="9b59d-125">Em seguida, procure o item dentro da coleção, que corresponde ao Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="9b59d-125">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```java
// IAggregatePartner partnerOperations;

ResourceCollection<AgreementMetaData> agreements = partnerOperations.getAgreements().get();

AgreementMetaData microsoftCloudAgreement;

for (AgreementMetaData metadata : agreements)
{
    if(metadata.getAgreementType() == AgreementType.MicrosoftCloudAgreement)
    {
        microsoftCloudAgreement = metadata;
    }
}
```

<span data-ttu-id="9b59d-126">Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) do projeto de [aplicações de teste](https://github.com/Microsoft/Partner-Center-Java-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="9b59d-126">A complete sample can be found in the [GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) class from the [console test app](https://github.com/Microsoft/Partner-Center-Java-Samples) project.</span></span>

## <a name="powershell"></a><span data-ttu-id="9b59d-127">PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b59d-127">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="9b59d-128">Para recuperar metadados de acordo para o Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="9b59d-128">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="9b59d-129">Utilize o comando [**Get-PartnerAgreementDetail.**](/powershell/module/partnercenter/get-partneragreementdetail)</span><span class="sxs-lookup"><span data-stu-id="9b59d-129">Use the [**Get-PartnerAgreementDetail**](/powershell/module/partnercenter/get-partneragreementdetail) command.</span></span> <span data-ttu-id="9b59d-130">Em seguida, procure o item dentro da coleção, que corresponde ao Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="9b59d-130">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```powershell
Get-PartnerAgreementDetail | Where-Object {$_.AgreementType -eq 'MicrosoftCloudAgreement'} | Select-Object -First 1
```

## <a name="rest-request"></a><span data-ttu-id="9b59d-131">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="9b59d-131">REST request</span></span>

<span data-ttu-id="9b59d-132">Para recuperar os metadados do acordo para o Microsoft Cloud Agreement, crie primeiro um pedido DE REST para recuperar a recolha **AgreementMetaData.**</span><span class="sxs-lookup"><span data-stu-id="9b59d-132">To retrieve agreement metadata for Microsoft Cloud Agreement, first create a REST Request to retrieve the **AgreementMetaData** collection.</span></span> <span data-ttu-id="9b59d-133">Em seguida, procure o item na coleção que corresponda ao Microsoft Cloud Agreement.</span><span class="sxs-lookup"><span data-stu-id="9b59d-133">Then search for the item in the collection that corresponds to the Microsoft Cloud Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9b59d-134">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b59d-134">Request syntax</span></span>

| <span data-ttu-id="9b59d-135">Método</span><span class="sxs-lookup"><span data-stu-id="9b59d-135">Method</span></span> | <span data-ttu-id="9b59d-136">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="9b59d-136">Request URI</span></span>                                                         |
|--------|---------------------------------------------------------------------|
| <span data-ttu-id="9b59d-137">GET</span><span class="sxs-lookup"><span data-stu-id="9b59d-137">GET</span></span>    | <span data-ttu-id="9b59d-138">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/acordos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9b59d-138">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/agreements HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9b59d-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="9b59d-139">Request headers</span></span>

<span data-ttu-id="9b59d-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9b59d-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9b59d-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="9b59d-141">Request body</span></span>

<span data-ttu-id="9b59d-142">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9b59d-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9b59d-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="9b59d-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="9b59d-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="9b59d-144">REST response</span></span>

<span data-ttu-id="9b59d-145">Se for bem sucedido, este método devolve uma coleção de recursos **AgreementMetaData** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="9b59d-145">If successful, this method returns a collection of **AgreementMetaData** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9b59d-146">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="9b59d-146">Response success and error codes</span></span>

<span data-ttu-id="9b59d-147">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="9b59d-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9b59d-148">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="9b59d-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9b59d-149">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="9b59d-149">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9b59d-150">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="9b59d-150">Response example</span></span>

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
            "templateId": "998b88de-aa99-4388-a42c-1b3517d49490",
            "agreementType": "MicrosoftCloudAgreement",
            "agreementLink": "https://docs.microsoft.com/partner-center/agreements",
            "versionRank": 0
        }
    ],
    "links": {
        "self": {
            "uri": "/agreements",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

<span data-ttu-id="9b59d-151">Para identificar o recurso na resposta que corresponde ao Microsoft Cloud Agreement, procure o recurso cujo **contrato a propriedadeType** tem valor "MicrosoftCloudAgreement".</span><span class="sxs-lookup"><span data-stu-id="9b59d-151">To identify the resource in the response that corresponds to the Microsoft Cloud Agreement, look for the resource whose **agreementType** property has value "MicrosoftCloudAgreement".</span></span>
