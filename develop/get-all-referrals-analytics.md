---
title: Obter todas as informações de análise de referências
description: Como obter todas as referências informações de análise.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: Kim-Davis
ms.author: kimnich
ms.openlocfilehash: 8fded9cc9d540fa1f7f3fcb38620c26b85c1c6032ef0176e9bd043943a425f65
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115992726"
---
# <a name="get-all-referrals-analytics-information"></a>Obter todas as informações de análise de referências

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Como obter todas as informações de análise de referências para os seus clientes.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais do Utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido |
|---------|-------------|
| **GET** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/referrals HTTP/1.1 |

### <a name="uri-parameters"></a>Parâmetros URI

| Parâmetro | Tipo | Description |
|-----------|------|-------------|
| filter | string | Devolve dados correspondentes à condição do filtro.</br> **Exemplo:**</br>  `.../referrals?filter=field eq 'value'` |
| groupby | string | Suporta termos e datas. Lógica de curto-circuito para limitar o número de baldes.</br> **Exemplo:**</br>  `.../referrals?groupby=termField1,dateField1,termField2` |
| agregaçãoLevel | string | O parâmetro *agregaçãoLevel* requer um *groupby*. O parâmetro *agregaçãoLevel* aplica-se a todos os campos de data presentes no *grupo*.</br> **Exemplo:**</br> `.../referrals?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
| top | string | O limite da página é 10.000. Leva qualquer valor inferior a 10.000.</br> **Exemplo:**</br> `.../referrals?top=100`</br> |
| saltar | string | Número de filas para saltar.</br> **Exemplo:**</br>  `.../referrals?top=100&skip=100` |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/referrals HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [referências.](partner-center-analytics-resources.md#referrals-resource)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
{
  "id": "112310",
  "status": "Accepted",
  "customerMarket": "US",
  "customerName": "Best Customer Ever",
  "customerOrgSize": "10to50employees",
  "acceptedDate": "2018-02-07T23:43:19",
  "acknowledgedDate": "2018-02-07T23:40:50",
  "archivedDate": null,
  "declinedDate": null,
  "expiredDate": null,
  "lostDate": null,
  "missedDate": null,
  "createdDate": "2018-02-04T23:08:59",
  "skippedDate": null,
  "wonDate": null,
  "partnerMarket": "US"
}
```

## <a name="see-also"></a>Ver também

- [Análise do Centro de Parceiros – Recursos](partner-center-analytics-resources.md)
