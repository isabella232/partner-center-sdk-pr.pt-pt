---
title: Obtém estatuto de excesso de idade para um determinado cliente
description: Obtém estatuto de excesso de idade para um determinado cliente.
ms.date: 10/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 8dabd811c61583a38f832eae54ce92402bfb5c29
ms.sourcegitcommit: 856c14b6b351697e3b3d33f1fe376adbb80517c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2021
ms.locfileid: "129383451"
---
# <a name="get-overage"></a>Obter excesso de tempo

**Aplica-se a**

- Partner Center

**Funções adequadas**

- Administrador global
- Agente administrativo

> [!Note] 
> As novas mudanças de Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da Microsoft 365/Dynamics 365 nova experiência técnica de experiência técnica.

Costumava ter excesso de tempo para um cliente. O overage permite que um cliente continue a utilizar os serviços se utilizar o serviço para além dos limites indicados. A overage define a sobreatenção da subscrição de consumo que o pay-as-you-go irá acumular.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no painel do Centro [de Parceiros.](https://partner.microsoft.com/dashboard) Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta**. Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de subscrição para a subscrição transitada.

## <a name="rest-request"></a>Pedido de DESCANSO
[GET] /clientes/{cliente-inquilino-id}/subscrições/overage
### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **OBTER**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/overage HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de consulta para devolver o excesso de tempo de um cliente.

| Nome                    | Tipo     | Necessário | Descrição                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **cliente-inquilino-id**  | **guid** | Y        | Um GUID correspondente ao inquilino do cliente.             |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhuma

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/overage HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve a sobreagem a um cliente.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [Códigos de Erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "totalCount": 1,
    "items": [
        {
            "azureEntitlementId": "ea1c26b7-8c99-42bb-ba7d-c535831fae8e",
            "partnerId": "1234",
            "type": "PhoneServices",
            "overageEnabled": true,
            "links": {
                "overage": {
                    "uri": "/customers/f62cf10b-8f76-4fc4-9774-c5291f8faf86/subscriptions/overage",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Overage"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
