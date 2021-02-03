---
title: Obter metadados de contrato para o Contrato da Microsoft Cloud
description: Este artigo explica como obter metadados de acordo para o Microsoft Cloud Agreement.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: c6a404eb38c4c31d3e69bb598872b932d8985529
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769260"
---
# <a name="get-agreement-metadata-for-microsoft-cloud-agreement"></a><span data-ttu-id="6a8cd-103">Obter metadados de contrato para o Contrato da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="6a8cd-103">Get agreement metadata for Microsoft Cloud Agreement</span></span>

<span data-ttu-id="6a8cd-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-104">**Applies To**</span></span>

- <span data-ttu-id="6a8cd-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="6a8cd-105">Partner Center</span></span>

> [!NOTE]
> <span data-ttu-id="6a8cd-106">O recurso **AgreementMetaData** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-106">The **AgreementMetaData** resource is currently supported by Partner Center in the Microsoft public cloud only.</span></span> <span data-ttu-id="6a8cd-107">Não é aplicável a:</span><span class="sxs-lookup"><span data-stu-id="6a8cd-107">It isn't applicable to:</span></span>
> - <span data-ttu-id="6a8cd-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="6a8cd-108">Partner Center operated by 21Vianet</span></span>
> - <span data-ttu-id="6a8cd-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="6a8cd-109">Partner Center for Microsoft Cloud Germany</span></span>
> - <span data-ttu-id="6a8cd-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6a8cd-110">Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6a8cd-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6a8cd-111">Prerequisites</span></span>

- <span data-ttu-id="6a8cd-112">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.9 ou a mais recente.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-112">If you are using the Partner Center .NET SDK, version 1.9 or newer is required.</span></span>

- <span data-ttu-id="6a8cd-113">Se estiver a utilizar o Partner Center Java SDK, é necessária a versão 1.8 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-113">If you are using the Partner Center Java SDK, version 1.8 or newer is required.</span></span>

- <span data-ttu-id="6a8cd-114">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6a8cd-114">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="6a8cd-115">Este cenário suporta app + autenticação do utilizador..</span><span class="sxs-lookup"><span data-stu-id="6a8cd-115">This scenario supports app + user authentication..</span></span>

## <a name="net-version-114-or-newer"></a><span data-ttu-id="6a8cd-116">.NET (versão 1.14 ou mais recente)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-116">.NET (version 1.14 or newer)</span></span>

<span data-ttu-id="6a8cd-117">Para recuperar os metadados do acordo para o Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="6a8cd-117">To retrieve the agreement metadata for Microsoft Cloud Agreement:</span></span>

1. <span data-ttu-id="6a8cd-118">Primeiro, recupere a coleção **IAggregatePartner.AgreementDetails.**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-118">First, retrieve the **IAggregatePartner.AgreementDetails** collection.</span></span>

2. <span data-ttu-id="6a8cd-119">Ligue para o método **ByAgreementType** para filtrar a coleção para o Microsoft Cloud Agreement.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-119">Call **ByAgreementType** method to filter the collection to Microsoft Cloud Agreement.</span></span>

3. <span data-ttu-id="6a8cd-120">Finalmente, ligue para o método **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-120">Finally, call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCloudAgreement";

var microsoftCloudAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

<span data-ttu-id="6a8cd-121">Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-121">A complete sample can be found in the [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="net-version-19---113"></a><span data-ttu-id="6a8cd-122">.NET (versão 1.9 - 1.13)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-122">.NET (version 1.9 - 1.13)</span></span>

<span data-ttu-id="6a8cd-123">Para recuperar metadados de acordo para o Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="6a8cd-123">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="6a8cd-124">Primeiro, recupere a coleção **IAggregatePartner.AgreementDetails** e, em seguida, ligue para os métodos **Get** or **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-124">First retrieve the **IAggregatePartner.AgreementDetails** collection and then call the **Get** or **GetAsync** methods.</span></span> <span data-ttu-id="6a8cd-125">Em seguida, procure o item dentro da coleção, que corresponde ao Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="6a8cd-125">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```csharp
// IAggregatePartner partnerOperations;

var agreements = partnerOperations.AgreementDetails.Get();

AgreementMetaData microsoftCloudAgreement = agreements.Items.FirstOrDefault (agr => agr.AgreementType == AgreementType.MicrosoftCloudAgreement);
```

## <a name="java"></a><span data-ttu-id="6a8cd-126">Java</span><span class="sxs-lookup"><span data-stu-id="6a8cd-126">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="6a8cd-127">Para recuperar metadados de acordo para o Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="6a8cd-127">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="6a8cd-128">Primeiro ligue para a função **IAggregatePartner.getAgreementDetails** e, em seguida, ligue para a função **get.**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-128">First call the **IAggregatePartner.getAgreementDetails** function and then call the **get** function.</span></span> <span data-ttu-id="6a8cd-129">Em seguida, procure o item dentro da coleção, que corresponde ao Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="6a8cd-129">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

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

<span data-ttu-id="6a8cd-130">Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) do projeto de [aplicações de teste](https://github.com/Microsoft/Partner-Center-Java-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-130">A complete sample can be found in the [GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) class from the [console test app](https://github.com/Microsoft/Partner-Center-Java-Samples) project.</span></span>

## <a name="powershell"></a><span data-ttu-id="6a8cd-131">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a8cd-131">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="6a8cd-132">Para recuperar metadados de acordo para o Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="6a8cd-132">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="6a8cd-133">Utilize o comando [**Get-PartnerAgreementDetail.**](/powershell/module/partnercenter/get-partneragreementdetail)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-133">Use the [**Get-PartnerAgreementDetail**](/powershell/module/partnercenter/get-partneragreementdetail) command.</span></span> <span data-ttu-id="6a8cd-134">Em seguida, procure o item dentro da coleção, que corresponde ao Microsoft Cloud Agreement:</span><span class="sxs-lookup"><span data-stu-id="6a8cd-134">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```powershell
Get-PartnerAgreementDetail | Where-Object {$_.AgreementType -eq 'MicrosoftCloudAgreement'} | Select-Object -First 1
```

## <a name="rest-request"></a><span data-ttu-id="6a8cd-135">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6a8cd-135">REST request</span></span>

<span data-ttu-id="6a8cd-136">Para recuperar os metadados do acordo para o Microsoft Cloud Agreement, crie primeiro um pedido DE REST para recuperar a recolha **AgreementMetaData.**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-136">To retrieve agreement metadata for Microsoft Cloud Agreement, first create a REST Request to retrieve the **AgreementMetaData** collection.</span></span> <span data-ttu-id="6a8cd-137">Em seguida, procure o item na coleção que corresponde ao Microsoft Cloud Agreement.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-137">Then search for the item in the collection which corresponds to the Microsoft Cloud Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6a8cd-138">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a8cd-138">Request syntax</span></span>

| <span data-ttu-id="6a8cd-139">Método</span><span class="sxs-lookup"><span data-stu-id="6a8cd-139">Method</span></span> | <span data-ttu-id="6a8cd-140">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6a8cd-140">Request URI</span></span>                                                         |
|--------|---------------------------------------------------------------------|
| <span data-ttu-id="6a8cd-141">GET</span><span class="sxs-lookup"><span data-stu-id="6a8cd-141">GET</span></span>    | <span data-ttu-id="6a8cd-142">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/acordos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6a8cd-142">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/agreements HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6a8cd-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6a8cd-143">Request headers</span></span>

<span data-ttu-id="6a8cd-144">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6a8cd-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6a8cd-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6a8cd-145">Request body</span></span>

<span data-ttu-id="6a8cd-146">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6a8cd-147">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6a8cd-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="6a8cd-148">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6a8cd-148">REST response</span></span>

<span data-ttu-id="6a8cd-149">Se for bem sucedido, este método devolve uma coleção de recursos **AgreementMetaData** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-149">If successful, this method returns a collection of **AgreementMetaData** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6a8cd-150">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6a8cd-150">Response success and error codes</span></span>

<span data-ttu-id="6a8cd-151">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6a8cd-152">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6a8cd-153">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6a8cd-153">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6a8cd-154">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6a8cd-154">Response example</span></span>

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

<span data-ttu-id="6a8cd-155">Para identificar o recurso na resposta que corresponde ao Microsoft Cloud Agreement, procure o recurso cujo **contrato a propriedadeType** tem valor "MicrosoftCloudAgreement".</span><span class="sxs-lookup"><span data-stu-id="6a8cd-155">To identify the resource in the response which corresponds to the Microsoft Cloud Agreement, look for the resource whose **agreementType** property has value "MicrosoftCloudAgreement".</span></span>
