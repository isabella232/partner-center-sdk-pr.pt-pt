---
title: Validar um endereço
description: Como validar um endereço utilizando a API de validação de endereços.
ms.date: 05/17/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0d3c27a763887e89e1116dbaf605db349369036c38378011dcca3fa07732a738
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989242"
---
# <a name="validate-an-address"></a>Validar um endereço

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Como validar um endereço utilizando a API de validação de endereços.

A API de validação de endereços só deve ser utilizada para pré-validação de atualizações de perfis de clientes. Use-o com o entendimento de que se o país for os Estados Unidos, Canadá, China ou México, o campo estatal é validado contra uma lista de Estados válidos para o respetivo país. Em todos os outros países, este teste não ocorre, e a API apenas verifica que o Estado é uma cadeia válida.

## <a name="prerequisites"></a>Pré-requisitos

Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

## <a name="c"></a>C\#

Para validar um endereço, primeiro instantaneamente um novo objeto **Address** e povoá-lo com o endereço para validar. Em seguida, recupere uma interface para **operações de Validações** a partir da propriedade **IAggregatePartner.Validations,** e ligue para o método **IsAddressValid** com o objeto de endereço.

```csharp
IAggregatePartner partnerOperations;

// Create an address to validate.
Address address = new Address()
{
    AddressLine1 = "One Microsoft Way",
    City = "Redmond",
    State = "WA",
    PostalCode = "98052",
    Country = "US"
};

// Validate the address.
AddressValidationResponse result = partnerOperations.Validations.IsAddressValid(address);

// If the request completes successfully, you can inspect the response object.

// See the status of the validation.
Console.WriteLine($"Status: {addressValidationResult.Status}");

// See the validation message returned.
Console.WriteLine($"Validation Message Returned: {addressValidationResult.ValidationMessage ?? "No message returned."}");

// See the original address submitted for validation.
Console.WriteLine($"Original Address:\n{this.DisplayAddress(addressValidationResult.OriginalAddress)}");

// See the suggested addresses returned by the API, if any exist.
Console.WriteLine($"Suggested Addresses Returned: {addressValidationResult.SuggestedAddresses?.Count ?? "None."}");

if (addressValidationResult.SuggestedAddresses != null && addressValidationResult.SuggestedAddresses.Any())
{
    addressValidationResult.SuggestedAddresses.ForEach(a => Console.WriteLine(this.DisplayAddress(a)));
}

// Helper method to pretty-print an Address object.
private string DisplayAddress(Address address)
{
    StringBuilder sb = new StringBuilder();

    foreach (var property in address.GetType().GetProperties())
    {
        sb.AppendLine($"{property.Name}: {property.GetValue(address) ?? "None to Display."}");
    }

    return sb.ToString();
}
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                 |
|----------|-----------------------------------------------------------------------------|
| **PUBLICAR** | [*{baseURL}*](partner-center-rest-urls.md)/v1/validações/endereço HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades necessárias no corpo de pedido.

| Nome         | Tipo   | Necessário | Descrição                                                |
|--------------|--------|----------|------------------------------------------------------------|
| linha de endereço1 | string | Y        | A primeira linha do endereço.                             |
| linha de endereço2 | string | N        | A segunda linha do endereço. Esta propriedade é opcional. |
| city         | string | Y        | A cidade.                                                  |
| state        | string | Y        | O Estado.                                                 |
| código postal   | string | Y        | O código postal.                                           |
| país      | string | Y        | O código de campo ISO alpha-2 de dois caracteres.                |

### <a name="response-details"></a>Detalhes da resposta

A resposta devolverá uma das seguintes mensagens de estado:

| Estado     | Descrição |    Número de endereços sugeridos devolvidos |
|-------|---------------|-------------------|
|Envio verificado | O endereço é verificado e pode ser enviado para. | Único |
|Verificado | O endereço está verificado. | Único |
|Interação necessária | O endereço sugerido foi alterado significativamente e precisa de confirmação do utilizador. | Único |
|Parcial de rua | A rua dada no endereço é parcial e precisa de mais informações. | Múltiplos — máximo de três |
|Instalações parciais | As instalações dadas (número de edifício, número de suite, entre outras) são parciais e precisam de mais informações. | Múltiplos — máximo de três |
|Vários | Existem vários campos que são parciais no endereço (potencialmente também incluindo a parcial da rua e as instalações parciais). | Múltiplos — máximo de três |
|Nenhuma | O endereço está incorreto. | Nenhuma |
|Não validado | O endereço não pôde ser enviado através do processo de validação. | Nenhuma |

### <a name="request-example"></a>Exemplo de pedido

```http
# "VerifiedShippable" Request Example

POST https://api.partnercenter.microsoft.com/v1/validations/address HTTP/1.1
Accept: application/json
Content-Type: application/json
Authorization: Bearer <token>
MS-CorrelationId: 29624f3c-90cb-4d34-a7e9-bd2de6d35218
MS-RequestId: eb55c2b8-6f4b-4b44-9557-f76df624b8c0
Host: api.partnercenter.microsoft.com
Content-Length: 137
X-Locale: en-US

{
    "AddressLine1": "1 Microsoft Way",
    "City": "Redmond",
    "State": "WA",
    "PostalCode": "98052",
    "Country": "US"
}

# "StreetPartial" Request Example

POST https://api.partnercenter.microsoft.com/v1/validations/address HTTP/1.1
Accept: application/json
Content-Type: application/json
Authorization: Bearer <token>
MS-CorrelationId: 2c95c9bc-fdfb-4c6a-84f4-57c9b0826b43
MS-RequestId: ee6cf74c-3ab5-48d6-9269-4a4b75bd59dc
Host: api.partnercenter.microsoft.com
Content-Length: 135
X-Locale: en-US

{
    "AddressLine1": "Microsoft Way",
    "City": "Redmond",
    "State": "WA",
    "PostalCode": "98052",
    "Country": "US"
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o método devolve um objeto **AddressValidationResponse** no organismo de resposta, com um código de estado **HTTP 200.** Apresentamos um exemplo abaixo.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
# "VerifiedShippable" Response Example

HTTP/1.1 200 OK
Date: Mon, 17 May 2021 23:19:19 GMT
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 29624f3c-90cb-4d34-a7e9-bd2de6d35218
MS-RequestId: eb55c2b8-6f4b-4b44-9557-f76df624b8c0
X-Locale: en-US
 
{
    "originalAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "1 Microsoft Way",
        "postalCode": "98052"
    },
    "suggestedAddresses": [
        {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "1 Microsoft Way",
            "postalCode": "98052-8300"
        }
    ],
    "status": "VerifiedShippable"
}

# "StreetPartial" Response Example

HTTP/1.1 200 OK
Date: Mon, 17 May 2021 23:34:08 GMT
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 2c95c9bc-fdfb-4c6a-84f4-57c9b0826b43
MS-RequestId: ee6cf74c-3ab5-48d6-9269-4a4b75bd59dc
X-Locale: en-US
 
{
    "originalAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "Microsoft Way",
        "postalCode": "98052"
    },
    "suggestedAddresses": [
        {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "1 Microsoft Way",
            "postalCode": "98052-6399"
        }
    ],
    "status": "StreetPartial",
    "validationMessage": "Address field invalid for property: 'Region', 'PostalCode', 'City'"
}
```
