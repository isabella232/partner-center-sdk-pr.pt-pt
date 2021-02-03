---
title: Obter todas as informações de análise de pesquisas
description: Como obter toda a informação de pesquisa analítica.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 967f8d0ed2d276e0f68a047204b64d83dc69da95
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768756"
---
# <a name="get-all-search-analytics-information"></a>Obter todas as informações de análise de pesquisas

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Como obter toda a informação de pesquisa analítica para os seus clientes.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais do Utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido |
|---------|-------------|
| **Obter** | [*\{ baseURL \}*](partner-center-rest-urls.md)/parceiro/v1/analytics/search HTTP/1.1 |

### <a name="uri-parameters"></a>Parâmetros URI

|    Parâmetro     |  Tipo  |                                                                                                                   Descrição                                                                                                                    |
|------------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      filter      | string |                                                                     Devolve dados correspondentes à condição do filtro. </br> **Exemplo:**</br> `.../search?filter=field eq 'value'`                                                                     |
|     groupby      | string |                                         Suporta termos e datas. Lógica de curto-circuito para limitar o número de baldes. </br> **Exemplo:**</br> `.../search?groupby=termField1,dateField1,termField2`                                         |
| agregaçãoLevel | string | O parâmetro *agregaçãoLevel* requer um *groupby*. O parâmetro *agregaçãoLevel* aplica-se a todos os campos de data presentes no *grupo*. </br> **Exemplo:**</br>  `.../search?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
|       top        | string |                                                                     O limite da página é 10.000. Leva qualquer valor inferior a 10.000.  </br> **Exemplo:**</br>  `.../search?top=100`                                                                     |
|       saltar       | string |                                                                                  Número de filas para saltar. </br> **Exemplo:**</br> `.../search?top=100&skip=100`                                                                                   |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/search HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o corpo de resposta contém uma coleção de recursos de [pesquisa.](partner-center-analytics-resources.md#search-resource)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
{
  "companyName": "my company",
  "contactButtonClicked": false,
  "keywordCountry": null,
  "detailsViewed": true,
  "keywordIndustryFocus": null,
  "mpnId": 2604568,
  "partnerMarket": "CN",
  "keywordProduct": null,
  "referralSubmitted": false,
  "searchDate": "2018-05-30",
  "keywordSearchText": " my company"
}
```

## <a name="see-also"></a>Ver também

- [Análise do Centro de Parceiros – Recursos](partner-center-analytics-resources.md)
