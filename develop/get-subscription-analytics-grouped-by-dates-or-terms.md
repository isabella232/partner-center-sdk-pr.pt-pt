---
title: Obter análise de subscrição agrupada por datas ou termos
description: Como obter informações de análise de subscrição agrupadas por datas ou termos.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4a9946027fa89f5a93fff5eede86e36a6be5b721
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769050"
---
# <a name="get-subscription-analytics-grouped-by-dates-or-terms"></a>Obter análise de subscrição agrupada por datas ou termos

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Como obter informações de análise de subscrição para os seus clientes agrupados por datas ou termos.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais do Utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido |
|--------|-------------|
| **Obter** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?groupby={groupby_queries} |

### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros de caminho necessários para identificar a sua organização e para agrupar os resultados.

| Nome | Tipo | Necessário | Descrição |
|------|------|----------|-------------|
| groupby_queries | pares de cordas e dataTime | Sim | Os termos e datas para filtrar o resultado. |

### <a name="groupby-syntax"></a>Sintaxe GroupBy

O grupo por parâmetro deve ser composto como uma série de vírgulas separadas, valores de campo.

Um exemplo não codificado é o seguinte:

```http
?groupby=termField1,dateField1,termField2
```

A tabela seguinte mostra uma lista dos campos suportados para grupo por.

| Campo | Tipo | Descrição |
|-------|------|-------------|
| customerTenantId | string | Uma cadeia formatada pelo GUID que identifica o inquilino do cliente. |
| nome do cliente | string | O nome do cliente. |
| customerMarket | string | O país/região em que o cliente faz negócios. |
| ID | string | Uma cadeia formatada por GUID que identifica a subscrição. |
| status | string | O estado da subscrição. Os valores suportados são: "ATIVE", "SUSPENDED", ou "DEPROVISIONED". |
| produtoName | string | O nome do produto. |
| Tipo de subscrição | string | O tipo de assinatura. Nota: Este campo é sensível a casos. Os valores suportados são: "Office", "Azure", "Microsoft365", "Dynamics", "EMS". |
| autoRenewEnabled | Booleano | Um valor que indica se a subscrição é renovada automaticamente. |
| partnerId  | string | A identificação do MPN. Para um revendedor direto, este parâmetro será o ID MPN do parceiro. Para um revendedor indireto, este parâmetro será o ID MPN do revendedor indireto. |
| nome amigável | string | O nome da assinatura. |
| nome parceiro | string | Nome do parceiro para quem a assinatura foi comprada |
| provedorName | string | Quando a transação de subscrição é para o revendedor indireto, o nome do fornecedor é o fornecedor indireto que comprou a subscrição.
| criaçãoDate | cadeia no formato de hora de data UTC | A data em que a subscrição foi criada. |
| effectiveStartDate | cadeia no formato de hora de data UTC | A data em que a subscrição começa. |
| compromissoEndDate | cadeia no formato de hora de data UTC | A data em que a subscrição termina. |
| actualStateEndDate | cadeia no formato de hora de data UTC | A data em que o estado atual da subscrição será alterado. |
| trialToPaidConversionDate | cadeia no formato de hora de data UTC | A data em que a subscrição converte do julgamento para o pagamento. O valor por defeito é nulo. |
| trialStartDate | cadeia no formato de hora de data UTC | A data em que o período experimental da subscrição começou. O valor por defeito é nulo. |
| lastUsageDate | cadeia no formato de hora de data UTC | A data em que a assinatura foi usada pela última vez. O valor por defeito é nulo. |
| deprovisionedDate | cadeia no formato de hora de data UTC | A data em que a subscrição foi desprovisionada. O valor por defeito é nulo. |
| último Aniversário deRenewal | cadeia no formato de hora de data UTC | A data em que a subscrição foi renovada pela última vez. O valor por defeito é nulo. |

### <a name="filter-fields"></a>Campos de filtragem

A tabela que se segue lista os campos de filtro opcionais e as suas descrições:

| Campo | Tipo |  Descrição |
|-------|------|--------------|
| top | int | O número de filas de dados a devolver no pedido. Se o valor não for especificado, o valor máximo e o valor predefinido são 10000. Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados. |
| saltar | int | O número de filas para saltar na consulta. Utilize este parâmetro para páginar através de grandes conjuntos de dados. Por exemplo, top=10000 e skip=0 recupera as primeiras 10000 linhas de dados, top=10000 e skip=10000 recupera as próximas 10000 linhas de dados. |
| filter | string | Uma ou mais declarações que filtram as linhas na resposta. Cada declaração de filtro contém um nome de campo do corpo de resposta e um valor que está associado ao **`eq`** , ou para certos **`ne`** campos, o **`contains`** operador. As declarações podem ser combinadas utilizando **`and`** ou **`or`** . Os valores das cordas devem ser rodeados por citações únicas no parâmetro do filtro. Consulte a secção seguinte para obter uma lista de campos que podem ser filtrados e os operadores que são apoiados nesses campos. |
| agregaçãoLevel | string | Especifica o intervalo de tempo para a recuperação de dados agregados. Pode ser uma das seguintes cordas: **dia,** **semana,** **ou mês.** Se o valor não for especificado, o padrão é **dataRange**. **Nota:** Este parâmetro só se aplica quando um campo de data é passado como parte do parâmetro groupBy. |
| grupoBy | string | Uma declaração que aplica agregação de dados apenas aos campos especificados. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?groupBy=subscriptionType
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma recolha de recursos de [subscrição](partner-center-analytics-resources.md#subscription-resource) agrupados pelos termos e datas especificados.

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
  "Value": [
    {
      "subscriptionType": "Azure",
      "subscriptionCount": "63",
      "licenseCount": "0"
    },
    {
      "subscriptionType": "Dynamics",
      "subscriptionCount": "62",
      "licenseCount": "405"
    },
    {
      "subscriptionType": "EMS",
      "subscriptionCount": "39",
      "licenseCount": "193"
    },
    {
      "subscriptionType": "M365",
      "subscriptionCount": "2",
      "licenseCount": "5"
    },
    {
      "subscriptionType": "Office",
      "subscriptionCount": "906",
      "licenseCount": "7485"
    },
    {
      "subscriptionType": "UNKNOWN",
      "subscriptionCount": "104",
      "licenseCount": "439"
    },
    {
      "subscriptionType": "Windows",
      "subscriptionCount": "2",
      "licenseCount": "2"
    }
  ],
  "@nextLink": null,
  "TotalCount": 7
}
```

## <a name="see-also"></a>Ver também

[Análise do Centro de Parceiros – Recursos](partner-center-analytics-resources.md)
