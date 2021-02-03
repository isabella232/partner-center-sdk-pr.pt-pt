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
# <a name="get-agreement-metadata-for-microsoft-cloud-agreement"></a>Obter metadados de contrato para o Contrato da Microsoft Cloud

**Aplica-se a**

- Partner Center

> [!NOTE]
> O recurso **AgreementMetaData** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft. Não é aplicável a:
> - Centro de Parceiros operado pela 21Vianet
> - Centro de Parceiros para Microsoft Cloud Germany
> - Centro de Parceiros do Microsoft Cloud for US Government

## <a name="prerequisites"></a>Pré-requisitos

- Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.9 ou a mais recente.

- Se estiver a utilizar o Partner Center Java SDK, é necessária a versão 1.8 ou mais recente.

- Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md). Este cenário suporta app + autenticação do utilizador..

## <a name="net-version-114-or-newer"></a>.NET (versão 1.14 ou mais recente)

Para recuperar os metadados do acordo para o Microsoft Cloud Agreement:

1. Primeiro, recupere a coleção **IAggregatePartner.AgreementDetails.**

2. Ligue para o método **ByAgreementType** para filtrar a coleção para o Microsoft Cloud Agreement.

3. Finalmente, ligue para o método **Get** ou **GetAsync.**

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCloudAgreement";

var microsoftCloudAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.

## <a name="net-version-19---113"></a>.NET (versão 1.9 - 1.13)

Para recuperar metadados de acordo para o Microsoft Cloud Agreement:

Primeiro, recupere a coleção **IAggregatePartner.AgreementDetails** e, em seguida, ligue para os métodos **Get** or **GetAsync.** Em seguida, procure o item dentro da coleção, que corresponde ao Microsoft Cloud Agreement:

```csharp
// IAggregatePartner partnerOperations;

var agreements = partnerOperations.AgreementDetails.Get();

AgreementMetaData microsoftCloudAgreement = agreements.Items.FirstOrDefault (agr => agr.AgreementType == AgreementType.MicrosoftCloudAgreement);
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Para recuperar metadados de acordo para o Microsoft Cloud Agreement:

Primeiro ligue para a função **IAggregatePartner.getAgreementDetails** e, em seguida, ligue para a função **get.** Em seguida, procure o item dentro da coleção, que corresponde ao Microsoft Cloud Agreement:

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

Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) do projeto de [aplicações de teste](https://github.com/Microsoft/Partner-Center-Java-Samples) de consola.

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Para recuperar metadados de acordo para o Microsoft Cloud Agreement:

Utilize o comando [**Get-PartnerAgreementDetail.**](/powershell/module/partnercenter/get-partneragreementdetail) Em seguida, procure o item dentro da coleção, que corresponde ao Microsoft Cloud Agreement:

```powershell
Get-PartnerAgreementDetail | Where-Object {$_.AgreementType -eq 'MicrosoftCloudAgreement'} | Select-Object -First 1
```

## <a name="rest-request"></a>Pedido de DESCANSO

Para recuperar os metadados do acordo para o Microsoft Cloud Agreement, crie primeiro um pedido DE REST para recuperar a recolha **AgreementMetaData.** Em seguida, procure o item na coleção que corresponde ao Microsoft Cloud Agreement.

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido                                                         |
|--------|---------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/acordos HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma coleção de recursos **AgreementMetaData** no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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

Para identificar o recurso na resposta que corresponde ao Microsoft Cloud Agreement, procure o recurso cujo **contrato a propriedadeType** tem valor "MicrosoftCloudAgreement".
