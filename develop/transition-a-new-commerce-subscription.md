---
title: Transição de uma nova subscrição de comércio
description: Atualiza a nova subscrição de commmerce de um cliente para uma subscrição-alvo especificada.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 2bbf2f63cec416e4d4b4a671d2e2b2914b5f5713
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123457322"
---
# <a name="transition-a-new-commerce-subscription"></a>Transição de uma nova subscrição de comércio

**Aplica-se a**: Centro de Parceiros

**Funções adequadas**

- Administrador global
- Agente administrativo

> [!Note] 
> As novas alterações de Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.

Usado para atualizar a nova subscrição de commmerce de um cliente para uma subscrição-alvo. Primeiro obtenha transições elegíveis para obter os SKUs disponíveis para upgrade. Em seguida, após a transição para executar a transição. Estes métodos suportam assinaturas tradicionais e novas fontes de comércio.  

## <a name="get-transition-eligibilities"></a>Obtenha elegibilidades de transição

Devolve uma lista de transições elegíveis para um determinado cliente, subscrição e tipo solicitado.

### <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de assinatura para a subscrição inicial.

### <a name="rest-request"></a>Pedido de DESCANSO

#### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **GET**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscrições/{subscrição-Id}/transiçãoEligibilities?elegibilidadeType={immediate, scheduled} HTTP/1.1 |

#### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de consulta para devolver as transições elegíveis.

| Nome                    | Tipo     | Necessário | Descrição                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **cliente-inquilino-id**  | **guid** | Y        | Um GUID correspondente ao inquilino do cliente.             |
| **subscrituro-Id** | **guid** | Y        | Um GUID correspondente à subscrição inicial. |
| **elegibilidadeTip**       | **string** | Y        | Descreve quando a transção deve ser executada, pode ser imediata ou agendada.  |

#### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

#### <a name="request-body"></a>Corpo do pedido

Nenhuma

#### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-Id}/transitionEligibilities?eligibilityType=immediate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

### <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma lista de transições elegíveis no organismo de resposta.

#### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

#### <a name="eligibility-errors"></a>Erros de elegibilidade

Descrições de erros e significado.

| Descrição do erro | Significado  |
|-------------------------|----------|
|A subscrição não pode ser transitada - a subscrição de fonte não está ativa. | Sub status original não ativo |
|A subscrição não pode ser transitada - a subscrição de fonte ainda não está prevista. | Original sub FulfillmentState não é sucesso |
|O tipo de transição não é compatível - é necessário mapear a subscrição AzureAD. | LegacyCannotConvertSubscriptionId ao ligar para GetSubscriptionUpgradeConflicts |
|O tipo de transição não é compatível - existem assinaturas contraditórias para transferência de licença. | Se qualquer serviço AAD tiver ids de subscrição de uma subscrição diferente, adicione-o à lista de conflitos (inclui compras feitas com fluxo de compra legado ou moderno) |

#### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "totalCount": 2,
    "items": [
        {
            "catalogItemId": "CFQ7TTC0KZCR:0001:CFQ7TTC0K71H",
            "title": "Microsoft 365 E5 Test Sku Title",
            "description": "Microsoft 365 E5 Test Sku Description",
            "quantity": 1,
            "eligibilities": [
{
                    "isEligible": true,
                    "transitionType": "transition_only",
                    "errors": []
                },
                
{
                    "isEligible": false,
                    "transitionType": "transition_with_license_transfer",
                    "errors": [
                        {
                            "code": 3,
                            "description": "Subscription cannot be transitioned because there are conflicting services."
                        }
                    ]
                }
            ],
            "attributes": {
                "objectType": "TransitionEligibility"
            }
        },
        {
            "catalogItemId": "CFQ7TTC0L4M3:0001:CFQ7TTC0K78T",
            "title": "Business Premium Test Sku Title",
            "description": "Business Premium Test Sku Description",
            "quantity": 1,
            "eligibilities": [
                {
                    "isEligible": false,
                    "transitionType": "transition_with_license_transfer",
                    "errors": [
                        {
                            "code": 3,
                            "description": "Subscription cannot be transitioned because there are conflicting services."
                        }
                    ]
                }
            ],
            "attributes": {
                "objectType": "TransitionEligibility"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="post-transition"></a>Pós-Transição

Publica um pedido de transição para um determinado cliente e subscrição. Devolve a transição com estatuto intial.

### <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de assinatura para a subscrição inicial.

### <a name="rest-request"></a>Pedido de DESCANSO

#### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **PUBLICAR**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscrições/{subscriptoin-Id}/transições HTTP/1.1 |


#### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de consulta para executar uma transição.

| Nome                    | Tipo     | Necessário | Descrição                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **cliente-inquilino-id**  | **guid** | Y        | Um GUID correspondente ao inquilino do cliente.             |
| **subscrituro-Id** | **guid** | Y        | Um GUID correspondente à subscrição inicial. |

#### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

#### <a name="request-body"></a>Corpo do pedido

É necessário um recurso **de transição** completo no organismo de pedido.

#### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customerId}/subscriptions/{subscriptionId}/transitions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US

{
    "toCatalogItemId": "CFQ7TTC0KZ59:0001:CFQ7TTC0KZ59",
    "quantity": 5,
    "transitionType": "transition_with_license_transfer",
    "events": []
}
```

### <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um recurso de transição com os eventos iniciais.

#### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

#### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "FromCatalogItemId": "CFQ7TTC0LDPB:0001:CFQ7TTC0LGNT",
    "ToCatalogItemId": "CFQ7TTC0LF8S:0001:CFQ7TTC0K9G9",
    "quantity": 1,
    "transitionType": "transition_with_license_transfer",
    "Events": [
        {
            "name": "Conversion",
            "status": "Started ",
            "timestamp": "2021-01-08T18:01:14.7488618Z",
            "attributes":
            {
                "objectType": "TransitionEvent"
            }
        }
    ],
    "attributes":
    {
        "objectType": "Transition"
    }
}
```
