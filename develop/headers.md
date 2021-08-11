---
title: Cabeçalhos REST do Centro de Parceiros
description: Saiba mais sobre os cabeçalhos de pedido HTTP REST e cabeçalhos de resposta REST apoiados pela API do Partner Center REST.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9c9483e761465be1a60003dcd44cef46af3e99634d99d804d43d101d6b8ef700
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993827"
---
# <a name="partner-center-rest-and-response-headers-supported-by-the-partner-center-rest-api"></a>Parceiro Centro REST e cabeçalhos de resposta apoiados pelo Centro Parceiro REST API 

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Os seguintes cabeçalhos de pedido e resposta HTTP são suportados pela API do Centro Parceiro REST. Nem todas as chamadas da API aceitam todos os cabeçalhos.

## <a name="rest-request-headers"></a>Cabeçalhos de pedido DE REST

Os seguintes cabeçalhos de pedido HTTP são suportados pela API do Centro Parceiro REST.

| Cabeçalho                       | Description                                                                                                                                                                                                                                                                            | Tipo de Valor |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Authorization:               | Obrigatório. O sinal de autorização na ficha do Bearer &lt; &gt; .                                                                                                                                                                                                                    | string     |
| Aceitar:                      | Especifica o tipo de pedido e resposta, "aplicação/json".                                                                                                                                                                                                                           | string     |
| MS-RequestId:                | Um identificador único para a chamada, usado para garantir a potência de id. Se houver um tempo limite, a chamada de novo deve incluir o mesmo valor. Ao receber uma resposta (sucesso ou falha de negócio), o valor deve ser reposto para a próxima chamada.                                            | GUID       |
| MS-CorrelationId:            | Um identificador único para a chamada, útil em registos e traços de rede para erros de resolução de problemas. O valor deve ser reposto para cada chamada. Todas as operações devem incluir este cabeçalho. Para obter mais informações, consulte as informações de identificação da correlação no [Teste e depurar](test-and-debug.md). | GUID       |
| Versão ms-contrato:         | Obrigatório. Especifica a versão da API solicitada; geralmente versão api: v1, salvo especificação em contrário na secção [Cenários.](scenarios.md)                                                                                                                                  | string     |
| Se-corresponder:                    | Usado para o controlo da concordância. Algumas chamadas da API requerem passar o ETag através do cabeçalho If-Match. O ETag está geralmente no recurso e, portanto, requer o GET-ting o mais recente. Para obter mais informações, consulte as informações do ETag em [Teste e Depurg](test-and-debug.md).                | string     |
| Ms-PartnerCenter-Application | Opcional. Especifica o nome da aplicação que está a utilizar a API do Centro Parceiro REST.                                                                                                                                                                                             | string     |
| X-Locale:                    | Opcional. Especifica o idioma em que as taxas são devolvidas. O padrão é "en-US". Para obter uma lista de valores suportados, consulte [as línguas e locais apoiados do Partner Center.](partner-center-supported-languages-and-locales.md)                                                                                                                                                                                                  | string     |

## <a name="rest-response-headers"></a>Cabeçalhos de resposta REST

Os seguintes cabeçalhos de resposta HTTP podem ser devolvidos pela API do Centro Parceiro REST.

| Cabeçalho            | Description                                                                                                                                                                                                                                 | Tipo de Valor |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Aceitar:           | Especifica o tipo de pedido e resposta, "aplicação/json".                                                                                                                                                                                | string     |
| MS-RequestId:     | Um identificador único para a chamada, usado para garantir a potência de id. Se houver um tempo limite, a chamada de novo deve incluir o mesmo valor. Ao receber uma resposta (sucesso ou falha de negócio), o valor deve ser reposto para a próxima chamada. | GUID       |
| MS-CorrelationId: | Um identificador único para a chamada. Este valor é útil para a resolução de registos de resolução de problemas e vestígios de rede para encontrar o erro. O valor deve ser reposto para cada chamada. Todas as operações devem incluir este cabeçalho.                                                       | GUID       |
