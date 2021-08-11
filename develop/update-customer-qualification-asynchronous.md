---
title: Atualizar as qualificações de um cliente
description: Atualiza as qualificações de um cliente assíncroneamente, incluindo o endereço associado ao perfil.
ms.date: 03/23/2021
ms.service: partner-dashboard
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 6d46d6a170e4ebcd441e678c482469c4041b2435bf7ee946dc91db554ec4932a
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997962"
---
# <a name="update-a-customers-qualifications-asynchronously"></a>Atualizar as qualificações de um cliente assíncroneamente

Atualiza as qualificações de um cliente assíncroneamente.

Um parceiro pode atualizar as qualificações de um cliente assíncroneamente para ser "Education" ou "GovernmentCommunityCloud". Outros valores, "Nenhum" e "Sem Fins Lucrativos", não podem ser definidos.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Para criar a qualificação de um cliente para "Educação", primeiro criar um objeto que represente o tipo de qualificação. Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes. Em seguida, use a propriedade [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) para recuperar uma interface [**ICustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) Finalmente, ligue `CreateQualifications()` ou com o objeto do tipo de `CreateQualificationsAsync()` qualificação como parâmetro de entrada.

``` csharp
var qualificationToCreate = "education";    // can also be "StateOwnedEntity" or "GovernmentCommunityCloud". See GCC example below.
var qualificationType = { Qualification = qualificationToCreate };
var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType);
```

**Amostra**: [App de amostra de consola](https://github.com/microsoft/Partner-Center-DotNet-Samples). **Project**: **Classe** SdkSamples : CreateCustomerQualification.cs

Para atualizar a qualificação de um cliente para **o GovernmentCommunityCloud** num cliente existente sem habilitação, o parceiro também é obrigado a incluir o Código de [**Validação**](utility-resources.md#validationcode)do cliente. Primeiro, criar um objeto que represente o tipo de qualificação. Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes. Em seguida, use a propriedade [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) para recuperar uma interface [**ICustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) Finalmente, ligue `CreateQualifications()` ou com o objeto tipo de `CreateQualificationsAsync()` qualificação e o código de validação como parâmetros de entrada.

``` csharp
// GCC validation is type ValidationCode
var qualificationType = { Qualification = "GovernmentCommunityCloud" };
var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType, gccValidation);
```

**Amostra**: [App de amostra de consola](https://github.com/microsoft/Partner-Center-DotNet-Samples). **Project**: **Classe** SdkSamples : CreateCustomerQualificationWithGCC.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| **PUBLICAR** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer_id}/qualificações?código={validaçãoD} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para atualizar a qualificação.

| Nome                   | Tipo | Necessário | Descrição                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | GUID | Yes      | O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor. |
| **validaçãoDesco**     | int  | No       | Só era necessário para Nuvem da Comunidade Governamental.                                                                                                            |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve o objeto de qualificação no corpo de pedido.

Propriedade | Tipo | Necessário | Descrição
-------- | ---- | -------- | -----------
Qualificação | string | Yes | O valor de cadeia da [**enum de Qualificação**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) do Cliente.

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

{
    "Qualification": "Education"
}

```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um objeto de qualificações no corpo de resposta. Abaixo está um exemplo da chamada **do POST** sobre um cliente (com uma qualificação anterior de **Nenhum)** com a qualificação **de Educação.**

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 201 CREATED
Content-Length: 29
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualification": "Education",
    "vettingStatus": "InReview",
    "vettingCreateDate": "2020-12-04T20:54:24Z" // UTC
}
```

## <a name="related-articles"></a>Artigos relacionados

- [Obtenha as qualificações de um cliente](./get-customer-qualification-asynchronous.md)
- [Obter os códigos de validação de um parceiro](get-a-partner-s-validation-codes.md)
