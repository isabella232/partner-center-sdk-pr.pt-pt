---
title: Obtenha análise de subscrição por consulta de pesquisa
description: Como obter informações de análise de subscrição filtradas por uma consulta de pesquisa.
ms.date: 05/10/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: dc6ef8d2136c5ffac3278a372980e9a601ef49bb485ef54187865fc9431b3404
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115995684"
---
# <a name="get-subscription-analytics-information-filtered-by-a-search-query"></a>Obter informações de análise de subscrições filtradas por uma consulta de pesquisa

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Como obter informações de análise de subscrição para os seus clientes filtrados por uma consulta de pesquisa.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais do Utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido |
|--------|-------------|
| **GET** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscrições?filter={{filter_string} |

### <a name="uri-parameters"></a>Parâmetros URI

Utilize o seguinte parâmetro de caminho necessário para identificar a sua organização e filtrar a pesquisa.

| Nome | Tipo | Necessário | Descrição |
|------|------|----------|-------------|
| filter_string | string | Yes | O filtro para aplicar à análise da subscrição. Consulte as secções de sintaxe do filtro e filtrar as secções para a sintaxe, campos e operadores utilizarem neste parâmetro. |

### <a name="filter-syntax"></a>Sintaxe de filtro

O parâmetro do filtro deve ser composto como uma série de combinações de campo, valor e operador. Várias combinações podem ser combinadas usando **`and`** ou **`or`** operadores.

Um exemplo não codificado é o seguinte:

- Corda: `?filter=Field operator 'Value'`
- Boolean: `?filter=Field operator Value`
- Contém `?filter=contains(field,'value')`

### <a name="filter-fields"></a>Campos de filtragem

O parâmetro do filtro do pedido contém uma ou mais declarações que filtram as linhas na resposta. Cada declaração contém um campo e valor que estão associados aos **`eq`** **`ne`** ou operadores. Alguns campos também apoiam os **`contains`** **`gt`** , e **`lt`** **`ge`** **`le`** operadores. As declarações podem ser combinadas utilizando **`and`** ou **`or`** operadores.

Seguem-se exemplos de cordas de filtro:

```http
autoRenewEnabled eq true

autoRenewEnabled eq true and customerMarket eq 'US'
```

A tabela a seguir mostra uma lista dos campos suportados e dos operadores de apoio para o parâmetro do filtro. Os valores das cordas devem estar rodeados de citações únicas.

| Parâmetro | Operadores apoiados | Description |
|-----------|---------------------|-------------|
| autoRenewEnabled | `eq`, `ne` | Um valor que indica se a subscrição é renovada automaticamente. |
| compromissoEndDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | A data em que a subscrição termina. |
| criaçãoDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | A data em que a subscrição foi criada. |
| actualStateEndDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | A data em que o estado atual da subscrição será alterado. |
| customerMarket | `eq`, `ne` | O país/região em que o cliente faz negócios. |
| nome do cliente | `contains` | O nome do cliente. |
| customerTenantId | `eq`, `ne` | Uma cadeia formatada pelo GUID que identifica o inquilino do cliente. |
| deprovisionedDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | A data em que a subscrição foi desprovisionada. O valor por defeito é nulo. |
| effectiveStartDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | A data em que a subscrição começa. |
| nome amigável | `contains` | O nome da assinatura. |
| ID | `eq`, `ne` | Uma cadeia formatada por GUID que identifica a subscrição. |
| último Aniversário deRenewal | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | A data em que a subscrição foi renovada pela última vez. O valor por defeito é nulo. |
| lastUsageDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | A data em que a assinatura foi usada pela última vez. O valor por defeito é nulo. |
| partnerId | `eq`, `ne` | A identificação do MPN. Para um revendedor direto, este valor será o ID MPN do parceiro. Para um revendedor indireto, este valor será o ID MPN do revendedor indireto. |
| nome parceiro | string | Nome do parceiro para quem a assinatura foi comprada |
| produtoName | `contains`, `eq`, `ne` | O nome do produto. |
| provedorName | string | Quando a transação de subscrição é para o revendedor indireto, o nome do fornecedor é o fornecedor indireto que comprou a subscrição.|
| status | `eq`, `ne` | O estado da subscrição. Os valores suportados são: "ATIVE", "SUSPENDED", ou "DEPROVISIONED". |
| Tipo de subscrição | `eq`, `ne` | O tipo de assinatura. **Nota:** Este campo é sensível a casos. Os valores suportados são: "Office", "Azure", "Microsoft365", "Dynamics", "EMS". |
| trialStartDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | A data em que o período experimental da subscrição começou. O valor por defeito é nulo. |
| trialToPaidConversionDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | A data em que a subscrição converte do julgamento para o pagamento. O valor por defeito é nulo. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?filter=autoRenewEnabled eq true
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [Subscrição](partner-center-analytics-resources.md#subscription-resource) que satisfazem os critérios do filtro.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123

{
    "customerTenantId": "735920EB-A564-4C72-9FE5-52632562712C",
    "customerName": "SURFACE TEST2",
    "customerMarket": "US",
    "id": "B76412DA-D382-4688-A6A4-711A207C1C2E",
    "status": "ACTIVE",
    "productName": "UNKNOWN",
    "subscriptionType": "Azure",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "MICROSOFT AZURE",
    "creationDate": "2017-06-02T23:11:58.747",
    "effectiveStartDate": "2017-06-02T00:00:00",
    "commitmentEndDate": null,
    "currentStateEndDate": null,
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": null,
    "licenseCount": 0
}
```

## <a name="see-also"></a>Ver também

- [Análise do Centro de Parceiros – Recursos](partner-center-analytics-resources.md)
