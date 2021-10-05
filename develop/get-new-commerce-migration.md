---
title: Obtenha uma nova migração de assinaturas de comércio
description: Como obter uma nova migração de subscrição de comércio
ms.date: 10/04/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 69c34f015d418437f080eb9d2f22a02c1f373b4f
ms.sourcegitcommit: 856b0baa4824960e13ee9672817a2d2e713fdf43
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/05/2021
ms.locfileid: "129528714"
---
#  <a name="get-a-new-commerce-subscription-migration"></a>Obtenha uma nova migração de assinaturas de comércio

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Partner Center para Microsoft Cloud Germany | Centro de Parceiros para Microsoft Cloud for US Government

Como obter uma migração de uma subscrição da New Commerce Experience para verificar o estado da migração

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no painel do Centro [de Parceiros.](https://partner.microsoft.com/dashboard) Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta**. Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um ID de subscrição atual

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                                           |
|---------|---------------------------------------------------------------------------------------------------------------------------------------|
| **OBTER** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/migrations/newcommerce/{migration-id} HTTP/1.1           |

### <a name="uri-parameter"></a>Parâmetro URI

Esta tabela enumera os parâmetros de consulta necessários para criar uma nova migração comercial.

| Nome               | Tipo   | Necessário | Descrição                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| cliente-inquilino-id | string | Yes      | Uma cadeia formatada pelo GUID que identifica o cliente. |
| id migração       | string | Yes      | Uma cadeia formatada pelo GUID que identifica o cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma recolha de recursos de [Subscrição](subscription-resources.md) no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-examples"></a>Exemplos de resposta

```http
{
    "id": "d3a0ef43-a208-4c32-8b10-f15e99d4e782",
    "currentSubscriptionId": "9beb6319-6889-4d28-a155-68ca9c783842",
    "status": "Processing",
    "customerTenantId": "a836f6d8-1b17-44af-aaf1-1e5511c5d4e1",
    "partnerTenantId": "7828d7ba-f17b-45c3-a1ce-8b6c3e3a26c0",
    "catalogItemId": "CFQ7TTC0LF8S:0002:CFQ7TTC0KSVV",
    "subscriptionEndDate": "2022-09-06T00:00:00Z",
    "quantity": 1,
    "termDuration": "P1Y",
    "billingCycle": "Monthly"
}
```
