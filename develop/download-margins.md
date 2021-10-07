---
title: Obtém uma lista de margens em formato delimitado em vírgula para um determinado parceiro.
description: Obtém uma lista de margens em formato delimitado em vírgula para um determinado parceiro.
ms.date: 09/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 6328ab962b2f210cee76b585ce2cf883c41eac3f
ms.sourcegitcommit: deb3207935fb5a74df515ed0fd4ffec90e6a143c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/07/2021
ms.locfileid: "129646411"
---
# <a name="download-margins"></a>Baixar margens


**Aplica-se a**: Centro de Parceiros 

**Funções adequadas**: Administração global | Agente administrativo

Os parceiros podem obter uma lista de margens ativas para um determinado parceiro. Este método devolve margens com base no parceiro e datas de início e fim disponíveis. As margens de descarregamento devolvem os dados num formato delimitado em vírgula.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.


## <a name="rest-request"></a>Pedido de DESCANSO
[GET] /v1/margins

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **OBTER**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/margins/download HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhuma

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/margins/download HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve a lista de preços como um fluxo de ficheiros como a.csv ficheiro

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e mais informações de depurações. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e mais parâmetros. Para obter a lista completa, consulte [Códigos de Erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

"id","productId","publisherName","productTitle","productType"","marginPercentage","startDate","endDate","status","statusDate"
"97620c21cc32_97cdce68-cce4-42aa-9410-233fd0269502","DZH318Z08L40","Market Place Test","Software As A Service Support Preview App","SaaS","10.0","2021-08-04T23:16:22.4736653Z","2022-03-31T23:59:59Z","live","2021-08-04T23:16:22.4736653Z"

```
