---
title: Validar um endereço
description: Como validar um endereço utilizando a API de validação de endereços.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 14d45977f3af6e8bba1b7cb7f969aa7c5bb671da
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529890"
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
// IAggregatePartner partnerOperations;

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
bool result = partnerOperations.Validations.IsAddressValid(address);

// If the address is valid, the result should equal true.
Console.WriteLine("Result: " + result.ToString());

// The following is an example that causes address validation to fail.
try
{
    // Change to an invalid postal code for this address.
    address.PostalCode = "98007";

    // Validate the address.
    result = partnerOperations.Validations.IsAddressValid(address);

    Console.WriteLine("ERROR: The code should have thrown an exception - BadRequest(400).");
}
catch (PartnerException exception)
{
    if (exception.ErrorCategory == PartnerErrorCategory.BadInput)
    {
        Console.WriteLine(exception.ErrorCategory.ToString());
        Console.WriteLine("Exception:");
        Console.WriteLine("Message: {0}", exception.Message);
    }
    else
    {
        throw;
    }
}
```

## <a name="java"></a>Java

Para validar um endereço, primeiro instantaneamente um novo objeto **Address** e povoá-lo com o endereço para validar. Em seguida, recupere uma interface para operações de **Validações** a partir da função **IAggregatePartner.getValidations** e ligue para o método **isAddressValid** com o objeto de endereço.

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

```java
// IAggregatePartner partnerOperations;

// Create an address to validate.
Address address = new Address();

address.setAddressLine1("One Microsoft Way");
address.setCity("Redmond");
address.setState("WA");
address.setCountry("US");
address.setPostalCode("98052");

try
{
    // Validate the address
    Boolean validationResult = partnerOperations.getValidations().isAddressValid(address);

    System.out.println(validationResult ? "The address is valid." : "Invalid address");
}
catch (Exception exception)
{
    System.out.println("Address is invalid");

    if (! StringHelper.isNullOrWhiteSpace(exception.getMessage()))
    {
        System.out.println(exception.getMessage());
    }
}
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Para validar um endereço, execute o [**Test-PartnerAddress**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) com os parâmetros de endereço povoados.

```powershell
Test-PartnerAddress -AddressLine1 '700 Bellevue Way NE' -City 'Bellevue' -Country 'US' -PostalCode '98004' -State 'WA'
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                 |
|----------|-----------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/validações/endereço HTTP/1.1 |

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

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/validations/address HTTP/1.1
Content-Type: application/json
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 129

{
    "AddressLine1": "One Microsoft Way",
    "City": "Redmond",
    "State": "WA",
    "PostalCode": "98052",
    "Country": "US"
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o método devolve um código de estado 200, como demonstrado na Resposta - exemplo de validação bem sucedido mostrado abaixo.

Se o pedido falhar, o método devolve um código de estado 400, como demonstrado na Resposta - exemplo falhado de validação apresentado abaixo. O corpo de resposta contém uma carga útil JSON com informações adicionais sobre o erro.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response---validation-succeeded-example"></a>Resposta - validação sucedeu exemplo

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CV: IqhjoWVyq0Kl81dO.0
MS-ServerId: 030011719
Date: Mon, 13 Mar 2017 23:56:12 GMT
```

### <a name="response---validation-failed-example"></a>Resposta - exemplo falhado de validação

```http
HTTP/1.1 400 Bad Request
Content-Length: 418
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CV: pdlItMyvtkmGHDWt.0
MS-ServerId: 101112012
Date: Tue, 14 Mar 2017 01:57:55 GMT

{
    "code": 2007,
    "description": "{\"code\":\"60071\",\"reason\":\"ZipCityInvalid - Details: Field - &#39;City&#39; is corrected from OldValue: &#39;Redmond&#39; to NewValue: &#39;BELLEVUE&#39;.\",\"corrected_address\":{\"country\":\"US\",\"region\":\"WA\",\"city\":\"BELLEVUE\",\"address_line1\":\"One Microsoft Way\",\"postal_code\":\"98007\"},\"object_type\":\"AddressValidation\",\"resource_status\":\"Active\"}",
    "data": [],
    "source": "PartnerFD"
}
```
