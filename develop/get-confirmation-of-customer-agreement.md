---
title: Obter confirmação da aceitação do cliente do Contrato de Cliente Microsoft
description: Este artigo explica como obter a confirmação da aceitação pelo cliente do Acordo de Cliente da Microsoft.
ms.date: 09/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 55f63311e7bb1857fdc6c4b3d68446674542ba98
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769439"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-customer-agreement"></a>Obter confirmação da aceitação do cliente do Contrato de Cliente Microsoft

**Aplica-se a:**

- Partner Center

O recurso **Do Acordo** é atualmente suportado pelo Partner Center apenas na nuvem pública da *Microsoft.* Este recurso não se aplica a:

- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Este artigo explica como pode obter confirmação da aceitação de um cliente do Microsoft Customer Agreement.

## <a name="prerequisites"></a>Pré-requisitos

- Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.

- Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md). Este cenário suporta apenas a autenticação App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="net"></a>.NET

Para obter confirmação(s) de aceitação do cliente que foi previamente fornecida:

- Utilize a recolha **IAggregatePartner.Customers** e ligue para o método **ById** com o identificador de clientes especificado.

- Pegue na propriedade **Dos Contratos** e filtre os resultados para o Microsoft Customer Agreement, chamando o método **ByAgreementType.**

- Ligue para o método **Get** ou **GetAsync.**

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCustomerAgreement";

var customerAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

Uma amostra completa pode ser encontrada na classe [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.

## <a name="rest-request"></a>Pedido de DESCANSO

Para obter a confirmação da aceitação do cliente que foi previamente fornecida:

1. Crie um pedido DE REST para recuperar a coleção [Contratos](./agreement-resources.md) para o cliente.

2. Utilize o parâmetro de consulta de **acordoso** para estender os resultados apenas ao Microsoft Customer Agreement.

### <a name="request-syntax"></a>Solicitar sintaxe

Utilize a seguinte sintaxe de pedido:

| Método | URI do pedido                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/agreements?agreementType={agreement-type} HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

Pode utilizar os seguintes parâmetros URI com o seu pedido:

| Nome             | Tipo | Necessário | Descrição                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| cliente-inquilino-id | GUID | Sim | O valor é um **CustomerTenantId** formatado guid que lhe permite especificar um cliente. |
| tipo de acordo | cadeia (de carateres) | No | Este parâmetro devolve todos os metadados do acordo. Utilize este parâmetro para estender a resposta de consulta ao tipo de acordo específico. Os valores suportados são: <br/><br/> **MicrosoftCloudAgreement** que apenas inclui metadados de acordo do tipo *MicrosoftCloudAgreement*.<br/><br/> **MicrosoftCustomerAgreement** que só inclui metadados de acordo do tipo *MicrosoftCustomerAgreement*.<br/><br/> **\*** que devolve todos os metadados do acordo. (Não utilize **\*** a menos que o seu código tenha a lógica necessária para lidar com tipos de acordo inesperados.)<br/><br/> **Nota:** Se o parâmetro URI não for especificado, a consulta predefine o **MicrosoftCloudAgreement** para retrocompatibilidade. A Microsoft pode introduzir metadados de acordo com novos tipos de acordo a qualquer momento.  |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma recolha de recursos do **Acordo** no organismo de resposta.

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
    "totalCount": 2,
    "items":
    [
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@example.com"
                "phoneNumber":"1234567890"
            },
            "templateId":"117a77b0-9360-443b-8795-c6dedc750cf9",
            "dateAgreed":"2019-08-26T00:00:00",
            "type":"MicrosoftCustomerAgreement",
            "agreementLink":"https://aka.ms/customeragreement"
        },
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@example.com"
                "phoneNumber:"1234567890"
            },
            "templateId":"117a77b0-9360-443b-8795-c6dedc750cf9",
            "dateAgreed":"2019-08-27T00:00:00",
            "type":"MicrosoftCustomerAgreement",
            "agreementLink":"https://aka.ms/customeragreement"
        }
    ]
}
```
