---
title: Atualizar a qualificação de um cliente
description: Saiba como atualizar as qualificações de um cliente através de rastreio sincronizado ou de verificação, incluindo o endereço associado ao perfil.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 5047743afdef02033d9494e3d8c16c9ab96b3fe9
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446654"
---
# <a name="update-a-customers-qualification-via-synchronous-validation"></a>Atualizar a qualificação de um cliente através de validação sincronizada

Saiba como atualizar as qualificações de um cliente de forma sincronizada através das APIs do Partner Center. Para aprender a fazê-lo assíncronos, consulte [a atualização da qualificação de um cliente através de validação assíncronosa.](update-customer-qualification-asynchronous.md)

Um parceiro pode atualizar a qualificação de um cliente para ser "Education" ou "GovernmentCommunityCloud". Outros valores, "Nenhum" e "Sem Fins Lucrativos", não podem ser definidos.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Para atualizar a qualificação de um cliente para "Educação", ligue **para [Update/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification.update)** sobre um  [**Cliente**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer)existente .

``` csharp
// CustomerQualification is an enum

var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.Education);
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: PartnerSDK.FeatureSamples **Class**: CustomerQualificationOperations.cs

Para atualizar a qualificação de um cliente para **o GovernmentCommunityCloud** num cliente existente sem habilitação, o parceiro é obrigado a incluir o Código de [**Validação**](utility-resources.md#validationcode)do cliente.

``` csharp
// CustomerQualification is an enum
// GCC validation is type ValidationCode

var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.GovernmentCommunityCloud, gccValidation);
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer_id}/qualification?code={validCode} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para atualizar a qualificação.

| Nome                   | Tipo | Necessário | Descrição                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | GUID | Yes      | O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor. |
| **validaçãoDesco**     | int  | No       | Só era necessário para Nuvem da Comunidade Governamental.                                                                                                            |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

O valor inteiro do número de [**clientesQualificação.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification)

### <a name="request-example"></a>Exemplo de pedido

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve a propriedade [**de qualificação**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) atualizada no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 14
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
"governmentcommunitycloud"
```

## <a name="related-articles"></a>Artigos relacionados

- [Obter a qualificação de um cliente](./get-customer-qualification-synchronous.md)
- [Obter os códigos de validação de um parceiro](get-a-partner-s-validation-codes.md)
