---
title: Ativar uma subscrição de sandbox para produtos de mercado comercial
description: Saiba como usar as APIs do C/# e do Partner Center REST para ativar uma subscrição de sandbox para produtos de mercado comercial.
ms.date: 09/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a78b2c84368b29f1378f46971c4814929094e299
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "97769950"
---
# <a name="activate-a-sandbox-subscription-for-commercial-marketplace-saas-products-to-enable-billing"></a>Ativar uma subscrição de sandbox para produtos SaaS de marketplace comercial para permitir faturação

**Aplica-se a:**

- Partner Center

Como ativar uma subscrição para marketplace comercial Software como um serviço (SaaS) produtos de integração de contas de sandbox para permitir a faturação.

> [!NOTE]
> Só é possível ativar uma subscrição de produtos SaaS de marketplace comercial a partir de contas de sandbox de integração. Se tiver uma subscrição de produção, deve visitar o site da editora para concluir o processo de configuração. A faturação da subscrição só começará depois de a configuração estar concluída.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Uma conta parceira de sandbox de integração com um cliente com uma subscrição ativa para produtos SaaS de marketplace comercial.

- Para os parceiros que utilizam o Partner Center .NET SDK, tem de utilizar a versão SDK 1.14.0 ou superior para aceder a esta capacidade.

## <a name="c"></a>C\#

Utilize os seguintes passos para ativar uma subscrição de produtos SaaS de marketplace comercial:

1. Disponibilizar uma interface às operações de subscrição. Deve identificar o cliente e especificar o identificador de subscrição da subscrição do ensaio.

   ```csharp
   var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
   ```

2. Ative a subscrição utilizando a operação **Ativação.**

   ```csharp
   var subscriptionActivationResult = subscriptionOperations.Activate();
   ```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método     | URI do pedido                                                                            |
|------------|----------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/ativar HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

| Nome                   | Tipo     | Necessário | Descrição                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y | O valor é um identificador de inquilino de clientes com formato GUID (**cliente-inquilino-id),** que lhe permite especificar um cliente. |
| **id de subscrição** | **guid** | Y | O valor é um identificador de subscrição formatado guid **(id de subscrição),** que lhe permite especificar uma subscrição. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/42b5f772-5c5c-4bce-b9d7-bdadeecca411/subscriptions/87363db7-39ab-dd25-d371-94340aaa2f97/activate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

```

## <a name="rest-response"></a>Resposta do REST

Este método devolve as propriedades **de id de subscrição** e **status.**

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 79
Content-Type: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "subscriptionId":"87363db7-39ab-dd25-d371-94340aaa2f97",
    "status":"Success"
}
```
