---
title: Validar uma subscrição para migração
description: Como validar se uma subscrição é elegível para migração.
ms.date: 10/04/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c8d2ae596901a45a794230c79cfb54815963e300
ms.sourcegitcommit: 856b0baa4824960e13ee9672817a2d2e713fdf43
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/05/2021
ms.locfileid: "129528713"
---
# <a name="validate-a-subscription-for-migration"></a>Validar uma subscrição para migração

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Partner Center para Microsoft Cloud Germany | Centro de Parceiros para Microsoft Cloud for US Government

Como validar uma subscrição para migração para a New Commerce Experience

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no painel do Centro [de Parceiros.](https://partner.microsoft.com/dashboard) Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta**. Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de subscrição atual

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
|**PUBLICAR** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/migrações/newcommerce/validar HTTP/1.1  |

### <a name="uri-parameter"></a>Parâmetro URI

Esta tabela lista os parâmetros de consulta necessários para validar uma subscrição para migração.

| Nome               | Tipo   | Necessário | Descrição                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| cliente-inquilino-id | string | Yes      | Uma cadeia formatada pelo GUID que identifica o cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades [de Subscrição](subscription-resources.md) no organismo de pedido.

| Propriedade              | Tipo             | Necessário        | Descrição |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| ActualSubscriptionId | string           | Yes             | Um identificador de subscrição que indica qual a subscrição que requer validação para migração.            |

### <a name="request-example"></a>Exemplo de pedido

```http
"currentSubscriptionId" : "9beb6319-6889-4d28-a155-68ca9c783842"
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um booleano "isEligível" no organismo de resposta, indicando se a subscrição atual é elegível para migração para novo comércio.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-examples"></a>Exemplos de resposta

```http
1. 
    {
        "currentSubscriptionId": "9beb6319-6889-4d28-a155-68ca9c783842",
        "isEligible": false,
        "errors": [
            {
                "code": 5,
                "description": "Subscription cannot be migrated to New Commerce because the equivalent offer is not yet available in New Commerce",
            }
        ]
    }

2. 
    {
        "currentSubscriptionId": "9beb6319-6889-4d28-a155-68ca9c783842",
        "isEligible": true,
    "catalogItemId": "CFQ7TTC0LF8S:0002:CFQ7TTC0KSVV",
    }
```
