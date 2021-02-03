---
title: Obtenha o estado de assinatura direta do cliente para o Microsoft Customer Agreement.
description: Pode utilizar o recurso DirectSignedCustomerAgreementStatus para obter o estado da assinatura direta (aceitação direta) do Acordo de Cliente da Microsoft.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 3f1deb20a18bc6e7133cac91db528f2d1ad694e2
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768738"
---
# <a name="get-the-status-of-a-customers-direct-signing-direct-acceptance-of-microsoft-customer-agreement"></a>Obtenha o estado da assinatura direta de um cliente (aceitação direta) do Microsoft Customer Agreement

**Aplica-se a:**

- Partner Center

O recurso **DirectSignedCustomerAgreementStatus** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.

Este recurso não é *aplicável* a:

- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Este artigo explica como pode recuperar o estado da aceitação direta de um cliente do Microsoft Customer Agreement.

## <a name="rest-request"></a>Pedido de DESCANSO

Para recuperar o estado da aceitação direta de um cliente do Microsoft Customer Agreement, crie um pedido DEE para recuperar o [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) para o cliente.

### <a name="request-syntax"></a>Solicitar sintaxe

Utilize a seguinte sintaxe de pedido:

| Método | URI do pedido                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1 |

### <a name="uri-parameters"></a>Parâmetros URI

Pode utilizar os seguintes parâmetros URI com o seu pedido:

| Nome             | Tipo | Necessário | Descrição                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| cliente-inquilino-id | GUID | Sim | O valor é um **CustomerTenantId** formatado pelo GUID que lhe permite especificar o ID do inquilino de um cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um recurso [ **DirectSignedCustomerAgreementStatus**](./customer-agreement-direct-sign-status-resource.md) no organismo de resposta.

O recurso tem uma propriedade **isSigned** que indica o estado de assinatura direta (aceitação direta) do cliente.

- Um valor **verdadeiro** indica que o contrato foi assinado (aceite) diretamente pelo cliente.

- Um valor **de falso** indica que o contrato *não* foi assinado (aceite) diretamente pelo cliente.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.

Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 20
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b

{"isSigned":true}
```
