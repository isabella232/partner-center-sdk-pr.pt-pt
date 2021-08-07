---
title: Obter metadados de contrato para o Contrato de Cliente Microsoft
description: Este artigo explica como obter metadados de acordo para o Microsoft Customer Agreement.
ms.date: 8/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: 384fa227a103ed10dc2fd055afa7688d3b2a418504360eb4a5025615cf2a4f67
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989360"
---
# <a name="get-agreement-metadata-for-the-microsoft-customer-agreement"></a>Obter metadados de contrato para o Contrato de Cliente Microsoft

**Aplica-se a**: Centro de Parceiros

**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Os metadados de acordo para o Microsoft Customer Agreement são atualmente suportados pelo Partner Center apenas na nuvem pública da Microsoft.

Tem de recuperar os metadados do acordo para o Acordo de Cliente da Microsoft antes de poder:

- [Confirme a aceitação de um cliente do Acordo de Cliente da Microsoft](./confirm-customer-consent-customer-agreement.md)
- [Recupere um link de descarregamento para o modelo do Contrato de Cliente da Microsoft](./download-customer-agreement-template.md)

## <a name="prerequisites"></a>Pré-requisitos

- Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.

- Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md). Este cenário suporta apenas a autenticação app+Utilizador.

## <a name="net-version-114-or-newer"></a>.NET (versão 1.14 ou mais recente)

Para recuperar os metadados do acordo para o Acordo de Cliente da Microsoft:

1. Primeiro, recupere a coleção **IAggregatePartner.AgreementDetails.**

2. Ligue para o método **ByAgreementType** para filtrar a coleção para o Microsoft Customer Agreement.

3. Finalmente, ligue para o método **Get** ou **GetAsync.**

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCustomerAgreement";

var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.

## <a name="rest-request"></a>Pedido de DESCANSO

Para recuperar os metadados do acordo para o Acordo de Cliente da Microsoft:

1. Crie um pedido DE REST para recuperar a coleção [AgreementMetaData.](./agreement-metadata-resources.md)

2. Utilize o parâmetro de consulta de **acordoso** para estender o resultado apenas ao Microsoft Customer Agreement.

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido                                                         |
|--------|---------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

| Nome                   | Tipo     | Necessário | Descrição                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| tipo de acordo | cadeia (de carateres) | No | Utilize este parâmetro para estender a resposta de consulta ao tipo de acordo específico. Os valores suportados são: <br/><br/>**MicrosoftCloudAgreement** que inclui metadados de acordo apenas do tipo *MicrosoftCloudAgreement*<br/><br/>**MicrosoftCustomerAgreement** que inclui metadados de acordo apenas do tipo *MicrosoftCustomerAgreement*.<br/><br/>**\**_ que devolve todos os metadados do acordo. (Não use _* \* *_ a menos que o seu código tenha a lógica de tempo de execução necessária para lidar com tipos de acordos desconhecidos, porque a Microsoft pode introduzir metadados de acordo com novos tipos de acordo a qualquer momento.) <br/> <br/> _* Nota:** Se o parâmetro URI não for especificado, a consulta predefine o **MicrosoftCloudAgreement** para retrocompatibilidade.  |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma coleção de recursos [ **AgreementMetaData**](./agreement-metadata-resources.md) no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.

Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

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
