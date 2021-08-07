---
title: Obter confirmação da aceitação do cliente do Contrato da Microsoft Cloud
description: Este artigo explica como obter a confirmação da aceitação pelo cliente do Microsoft Cloud Agreement.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
aauthor: khakiali
ms.author: alikhaki
ms.openlocfilehash: eb1f9ec5a7e96984f9c458419268fb305cf13ffd44d92fd01823ad94c2fb1798
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115990805"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-cloud-agreement"></a>Obter confirmação da aceitação do cliente do Contrato da Microsoft Cloud

**Aplica-se a**: Centro de Parceiros

**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

O recurso **Do Acordo** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.

## <a name="prerequisites"></a>Pré-requisitos

- Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.9 ou a mais recente.

- Se estiver a utilizar o Partner Center Java SDK, é necessária a versão 1.8 ou mais recente.

- Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md). Este cenário apenas suporta app + autenticação do utilizador.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="net-version-14-or-newer"></a>.NET (versão 1.4 ou mais recente)

Para obter confirmação(s) de aceitação do cliente que foi previamente fornecida:

- Utilize a recolha **IAggregatePartner.Customers** e ligue para o método **ById** com o identificador de clientes especificado.

- Pegue na propriedade **Dos Contratos** e filtre os resultados para o Microsoft Cloud Agreement chamando o método **ByAgreementType.**

- Ligue para o método **Get** ou **GetAsync.**

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCloudAgreement";

var cloudAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

Uma amostra completa pode ser encontrada na classe [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.

## <a name="net-version-19---113"></a>.NET (versão 1.9 - 1.13)

Para obter a confirmação da aceitação do cliente fornecida anteriormente:

Utilize a recolha **IAggregatePartner.Customers** e ligue para o método **ById** com o identificador do cliente especificado. Em seguida, obtenha a propriedade **Dos Acordos,** seguida de chamar os métodos **Get** ou **GetAsync.**

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var agreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Get();
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Para obter a confirmação da aceitação do cliente fornecida anteriormente:

Utilize a função **IAggregatePartner.getCustomers** e ligue para a função **byId** com o identificador do cliente especificado. Em seguida, obtenha a função **getAgreements,** seguido chamando a função **get.**

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;

ResourceCollection<Agreement> agreements = partnerOperations.getCustomers().byId(selectedCustomerId).getAgreements().get();
```

Uma amostra completa pode ser encontrada na classe [GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) do projeto de [aplicações de teste](https://github.com/Microsoft/Partner-Center-Java-Samples) de consola.

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Para obter a confirmação da aceitação do cliente fornecida anteriormente:

Utilize o comando [**Get-PartnerCustomerAgreement.**](/powershell/module/partnercenter/get-partnercustomeragreement)

```powershell
Get-PartnerCustomerAgreement -CustomerId '14876998-c0dc-46e6-9d0c-65a57a6c32ec'
```

## <a name="rest-request"></a>Pedido de DESCANSO

Para obter a confirmação da aceitação do cliente fornecida anteriormente, consulte as seguintes instruções.

Criar um novo recurso **do Acordo** com as informações de certificação relevantes.

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/acordos HTTP/1.1 |

#### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para especificar o cliente que está a confirmar.

| Nome             | Tipo | Necessário | Descrição                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| CustomerTenantId | GUID | Y        | O valor é um **CustomerTenantId** formatado guid que lhe permite especificar um cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma recolha de recursos do **Acordo** no organismo de resposta.

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
    "totalCount": 2,
    "items":
    [
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@Outlook.com"
                "phoneNumber":"1234567890"
            },
            "templateId":"998b88de-aa99-4388-a42c-1b3517d49490",
            "dateAgreed":"2018-07-28T00:00:00",
            "type":"MicrosoftCloudAgreement",
            "agreementLink":"https://docs.microsoft.com/partner-center/agreements"
        },
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@Outlook.com"
                "phoneNumber:"1234567890"
            },
            "templateId":"998b88de-aa99-4388-a42c-1b3517d49490",
            "dateAgreed":"2017-08-01T00:00:00",
            "type":"MicrosoftCloudAgreement",
            "agreementLink":"https://docs.microsoft.com/partner-center/agreements"
        }
    ]
}
```
