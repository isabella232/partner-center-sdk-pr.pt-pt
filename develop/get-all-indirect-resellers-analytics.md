---
title: Obter todas as informações de análise de revendedores indiretos
description: Como obter todas as informações de análise de revendedores indiretos.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 4252f5fcbbcb038f382408074c8fd6ede3fd1f58
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760747"
---
# <a name="get-all-indirect-resellers-analytics-information"></a>Obter todas as informações de análise de revendedores indiretos

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Como obter todas as informações de análise de revendedores indiretos para os seus clientes.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais do Utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido |
|---------|-------------|
| **Obter** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/indirectresellers HTTP/1.1 |

### <a name="uri-parameters"></a>Parâmetros URI

| Parâmetro                             | Tipo     | Description                              |
|:--------------------------------------|:---------|:-----------------------------------------|
| partnerTenantId                       | string   | A Identificação do Inquilino do parceiro para o qual pretende recuperar dados de revendedores indiretos. |
| ID                                    | string   | ID do revendedor indireto                                                                 |
| name                                  | string   | O Nome do parceiro para o qual pretende recuperar dados de revendedores indiretos.      |
| mercado                                | string   | O Mercado do parceiro para o qual pretende recuperar dados de revendedores indiretos.    |
| firstSubscriptionCreationDate         | cadeia no formato de hora de data UTC  | A data de criação da primeira subscrição com base na qual pretende recuperar dados de revendedores indiretos.  |
| mais recenteSubscriçãoCreationDate        | cadeia no formato de hora de data UTC  | A data de criação da última subscrição.                 |
| firstSubscriptionEndDate              | cadeia no formato de hora de data UTC  | É a primeira vez que qualquer subscrição foi terminada.                        |
| mais recenteSubscriçãoEndDate             | cadeia no formato de hora de data UTC  | Data mais recente quando qualquer subscrição foi terminada.                  |
| firstSubscriptionSuspendedDate        | cadeia na hora da data UTC         | É a primeira vez que qualquer assinatura foi suspensa.                    |
| mais recentesSubscriçãoSuspendedDate       | cadeia no formato de hora de data UTC  | Data mais recente quando qualquer subscrição foi suspensa.              |
| firstSubscriptionDeprovisionedDate    | cadeia no formato de hora de data UTC  | É a primeira vez que qualquer subscrição foi desprovisionada.                |
| mais recentesSsubscriptionDeprovisionedDate   | cadeia no formato de hora de data UTC  | Data mais recente quando qualquer subscrição foi desprovisionada.          |
| subscriçãoCount                     | double   | Contagem de assinaturas para todos os revendedores de valor acrescentado                                     |
| licençaCount                          | double   | Contagem de licenças para todos os revendedores de valor acrescentado.                                         |
| indiretResellerCount                 | double   | Contagem de revendedores indiretos                                                             |
|  top                                  | string   | O número de filas de dados a devolver no pedido. O valor máximo e o valor predefinido se não especificado for 10000. Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.  |
| saltar                                  | int      | O número de filas para saltar na consulta. Utilize este parâmetro para páginar através de grandes conjuntos de dados. Por exemplo, **`top=10000 and skip=0`** recupera as primeiras 10000 linhas de **`top=10000 and skip=10000`** dados, recupera as próximas 10000 linhas de dados, e assim por diante.              |
| filter                                | string   | O parâmetro do *filtro* do pedido contém uma ou mais declarações que filtram as linhas na resposta. Cada declaração contém um campo e valor que estão associados aos **`eq`** **`ne`** ou operadores, e as declarações podem ser combinadas usando **`and`** ou **`or`** . Pode especificar os seguintes campos:<br/><br/>     *partnerTenantId*<br/> *id*<br/> *Nome*<br/>                *mercado*<br/> *firstSubscriptionCreationDate*<br/> *mais recenteSubscriçãoCreationDate*<br/>                *firstSubscriptionEndDate*<br/>                *mais recenteSubscriçãoEndDate*<br/>                *firstSubscriptionSuspendedDate*<br/>                *mais recentesSubscriçãoSuspendedDate*<br/>                *firstSubscriptionDeprovisionedDate*<br/>                *mais recentesSsubscriptionDeprovisionedDate*<br/><br/>         **Exemplo:**<br/>              `.../indirectresellers?filter=market eq 'US'`<br/><br/>            **Exemplo:**<br/>                `.../indirectresellers?filter=market eq 'US' or (firstSubscriptionCreationDate le cast('2018-01-01',Edm.DateTimeOffset) and firstSubscriptionCreationDate le cast('2018-04-01',Edm.DateTimeOffset))` |              
| agregaçãoLevel                     | string    | Especifica o intervalo de tempo para a recuperação de dados agregados. Pode ser uma das seguintes cordas: &quot; &quot; dia, &quot; &quot; semana, &quot; ou &quot; mês. Se não for especificado, o padrão é &quot; dia &quot; .<br/><br/>                                 `aggregationLevel` não é apoiado sem um `aggregationLevel` . `aggregationLevel` aplica-se a todos os **campos de datas presentes** no `aggregationLevel`                         |
| orderby                              | string    | Uma declaração que encomenda os valores de dados de resultados para cada instalação. A sintaxe é `...&orderby=field[order],field [order],...`. O parâmetro de campo pode ser uma das seguintes cordas:<br/><br/>                &quot;partnerTenantId&quot;<br/>                &quot;id&quot;<br/>                &quot;nome&quot;<br/>                &quot;mercado&quot;<br/>                &quot;firstSubscriptionCreationDate&quot;<br/>               &quot;mais recenteSubscriçãoCreationDate&quot;<br/>                &quot;firstSubscriptionEndDate&quot;<br/>               &quot;mais recenteSubscriçãoEndDate&quot;<br/>                &quot;firstSubscriptionSuspendedDate&quot;<br/>                &quot;mais recentesSubscriçãoSuspendedDate&quot;<br/>               &quot;firstSubscriptionDeprovisionedDate&quot;<br/>                &quot;mais recentesSsubscriptionDeprovisionedDate&quot;<br/>                &quot;subscriçãoCount&quot;<br/>                &quot;licençaCount&quot;<br/><br/>   O parâmetro *de encomenda* é opcional, e pode ser ou `asc` ; `desc` especificar a ordem ascendente ou descendente para cada campo. A predefinição é `asc`.<br/><br/>    **Exemplo:**<br/>                `...&orderby=market,subscriptionCount`                                       |                   
| groupby                              | string    | Uma declaração que aplica agregação de dados apenas aos campos especificados. Pode especificar os seguintes campos:<br/><br/>         *partnerTenantId*<br/>    *id*<br/>               *Nome*<br/>                *mercado*<br/>                *firstSubscriptionCreationDate*<br/>                *mais recenteSubscriçãoCreationDate*<br/>                *firstSubscriptionEndDate*<br/>                *mais recenteSubscriçãoEndDate*<br/>                *firstSubscriptionSuspendedDate*<br/>                *mais recentesSubscriçãoSuspendedDate*<br/>                *firstSubscriptionDeprovisionedDate*<br/>                *mais recentesSsubscriptionDeprovisionedDate*<br/><br/>                 As linhas de dados devolvidas contêm os campos especificados na `groupby` cláusula, e os seguintes campos:<br/><br/>            *indiretResellerCount*<br/>                *licençaCount*<br/>                *subscriçãoCount*<br/><br/>            O `groupby` parâmetro pode ser usado com o `aggregationLevel` parâmetro.<br/><br/>            **Exemplo:**</br>               `...&groupby=ageGroup,market&aggregationLevel=week`                         |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/indirectresellers HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [de revendedores indiretos.](partner-center-analytics-resources.md#csp-program-indirect-resellers-analytics)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
{
    "partnerTenantId": "AAAAAAAA-BBBB-CCCC-DDDD-EEEEEEEEEEEE",
    "id": "1111111",
    "name": "RESELLER NAME",
    "market": "US",
    "firstSubscriptionCreationDate": "2016-10-18T19:16:25.107",
    "latestSubscriptionCreationDate": "2016-10-18T19:16:25.107",
    "firstSubscriptionEndDate": "2018-11-07T00:00:00",
    "latestSubscriptionEndDate": "2018-11-07T00:00:00",
    "firstSubscriptionSuspendedDate": "0001-01-01T00:00:00",
    "latestSubscriptionSuspendedDate": "0001-01-01T00:00:00",
    "firstSubscriptionDeprovisionedDate": "0001-01-01T00:00:00",
    "latestSubscriptionDeprovisionedEndDate": "0001-01-01T00:00:00",
    "subscriptionCount": 10,
    "licenseCount": 20
}
```

## <a name="see-also"></a>Ver também

- [Análise do Centro de Parceiros – Recursos](partner-center-analytics-resources.md)
