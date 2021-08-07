---
title: Criar uma transferência
description: Como criar uma transferência de subscrições para um cliente.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8414bbcfa0940742339eeba24b3b6a16ddfb6e3424670a4c064cbd995ba50851
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991587"
---
# <a name="create-a-transfer"></a>Criar uma transferência

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **PUBLICAR** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/transfers HTTP/1.1                    |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de percurso para identificar o cliente.

| Nome            | Tipo     | Necessário | Descrição                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **id cliente** | string   | Yes      | Um id de cliente formatado GUID que identifica o cliente.             |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades da [Entidade transferina](transfer-entity-resources.md) no organismo de pedido.

| Propriedade              | Tipo          | Necessário  | Descrição                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| ID                    | string        | No    | Um identificador de entidade de transferência que é fornecido após a criação bem sucedida da Entidade de Transferência.                               |
| createdTime           | DateTime      | No    | A data em que a Entidade de Transferência foi criada, em formato de data-hora. Aplicada após a criação bem sucedida da Entidade de Transferência.      |
| última Hora DaModified      | DateTime      | No    | A data em que a Entidade de Transferência foi atualizada pela última vez, em formato de data-hora. Aplicada após a criação bem sucedida da Entidade de Transferência. |
| últimoModifiedUser      | cadeia (de carateres)        | No    | O utilizador que atualizou pela última vez a Entidade de Transferência. Aplicada após a criação bem sucedida da Entidade de Transferência.                          |
| nome do cliente          | cadeia (de carateres)        | No    | Opcional. O nome do cliente cujas assinaturas estão a ser transferidas.                                              |
| customerTenantId      | cadeia (de carateres)        | No    | Um id de cliente formatado GUID que identifica o cliente. Aplicada após a criação bem sucedida da Entidade de Transferência.         |
| partnertenantid       | cadeia (de carateres)        | No    | Um parceiro-id formatado GUID que identifica o parceiro.                                                                   |
| fontePartnerName     | cadeia (de carateres)        | No    | Opcional. O nome da organização do parceiro que está a iniciar a transferência.                                           |
| sourcePartnerTenantId | string        | Yes   | Um parceiro-id formatado GUID que identifica o parceiro que inicia a transferência.                                           |
| targetPartnerName     | cadeia (de carateres)        | No    | Opcional. O nome da organização do parceiro a quem a transferência é dirigida.                                         |
| targetPartnerTenantId | string        | Yes   | Um parceiro-id formatado GUID que identifica o parceiro a quem a transferência é alvo.                                  |
| lineitems             | Matriz de objetos | Yes| Uma matriz de recursos [TransferLineItem.](transfer-entity-resources.md#transferlineitem)                                   |
| status                | cadeia (de carateres)        | No    | O estado da Entidade de Transferência. Os valores possíveis são "Ative" (pode ser eliminado/submetido) e "Concluído" (já foi concluído). Aplicada após a criação bem sucedida da Entidade de Transferência.|

Esta tabela descreve as propriedades [transferLineItem](transfer-entity-resources.md#transferlineitem) no corpo de pedido.

|      Propriedade       |            Tipo             | Necessário | Descrição                                                                                     |
|---------------------|-----------------------------|----------|-------------------------------------------------------------------------------------------------|
| ID                   | string                     | No       | Um identificador único para um item de linha de transferência. Aplicada após a criação bem sucedida da Entidade de Transferência.|
| subscriptionId       | string                     | Yes      | O identificador de assinatura.                                                                         |
| quantidade             | int                        | No       | O número de licenças ou instâncias.                                                                 |
| billingCycle         | Objeto                     | No       | O tipo de ciclo de faturação definido para o período atual.                                                |
| nome amigável         | cadeia (de carateres)                     | No       | Opcional. O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.                |
| partnerIdOnRecord    | cadeia (de carateres)                     | No       | PartnerId on Record (MPN ID) sobre a compra que acontece quando a transferência é aceite.              |
| offerId              | cadeia (de carateres)                     | No       | O identificador da oferta.                                                                                |
| addonItems           | Lista de objetos **TransferLineItem** | No | Uma recolha de itens de linha da TransferEntity para addons que serão transferidos juntamente com a subscrição base que está a ser transferida. Aplicada após a criação bem sucedida da Entidade de Transferência.|
| transferEror        | cadeia (de carateres)                     | No       | Aplicada após transferência A Entidade é aceite se houver um erro.                                        |
| status               | cadeia (de carateres)                     | No       | O estado do lineitem na Entidade de Transferência.                                                    |

### <a name="request-example"></a>Exemplo de pedido

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Expect: 100-continue

{
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lineItems": [
        {
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "partnerIdOnRecord": "517285"
        },
        {
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "partnerIdOnRecord": "517285"
        }
    ]
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve o recurso [transferenity](transfer-entity-resources.md) povoado no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 201 Created
Content-Length: 138
Content-Type: application/json; charset=utf-8
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US,en-US
{
    "id": "67c5b05b-09b5-47ba-9047-5056fe2afa4f",
    "status": "Active",
    "createdTime": "2020-03-24T20:44:14.9602781Z",
    "lastModifiedTime": "2020-03-24T20:44:15Z",
    "customerTenantId": "823c6c3f-9259-4d51-bae2-5dd06743177f",
    "partnertenantid": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lastModifiedUser": "d0648481-b615-45c9-8cd1-ff87940dbdc4",
    "lineItems": [
        {
            "id": 0,
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "offerId": "50E9A47A-7B4D-4970-9D90-CAE927F53753",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 for Sales Enterprise Attach to Qualifying Dynamics 365 Base Offer",
            "quantity": 1,
            "addonItems": [
                {
                    "id": 0,
                    "subscriptionId": "D738C6C9-DDBD-46E9-B316-65F9D9B3ECB4",
                    "offerId": "2BCF9FE8-8B65-4FCF-9240-419203FB8CF4",
                    "billingCycle": "annual",
                    "friendlyName": "Dynamics 365 - Additional Production Instance (Qualified Offer)",
                    "quantity": 4
                }
            ]
        },
        {
            "id": 0,
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "offerId": "455DDD41-32ED-4E2D-B3A2-BBCB22CAA467",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 Customer Engagement Plan Patch",
            "quantity": 8,
            "addonItems": []
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/823c6c3f-9259-4d51-bae2-5dd06743177f/transfers/67c5b05b-09b5-47ba-9047-5056fe2afa4f",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "TransferEntity"
    }
}
```
