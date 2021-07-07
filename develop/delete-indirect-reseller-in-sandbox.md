---
title: Eliminar Revendedor Indireto na Caixa de Areia
description: Fornece informações sobre a eliminação de Revendedores Indiretos da Caixa de Areia e a capacitação de testes de ponta a ponta utilizando APIs.
ms.date: 5/24/2021
ms.author: vijvala
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ba1fd002ac62aba4e414d263b33ecc8153054602
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973014"
---
# <a name="delete-indirect-reseller-in-sandbox"></a>Eliminar Revendedor Indireto na Caixa de Areia

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud Germany

Este documento mostra como eliminar os Fornecedores Indiretos da Sandbox e permitir testes de ponta a ponta utilizando APIs.

> [!Important]
> Este documento descreve funcionalidades que só são permitidas no ambiente Sandbox para experiências de Modelo Indireto.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [Autenticação do Centro de Parceiros.](partner-center-authentication.md) Este cenário suporta a autenticação com credenciais app+utilizador.

## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller"></a>Sandbox Fornecedor Indireto – Eliminar Revendedor Indireto Sandbox 

Esta funcionalidade só está disponível na Sandbox e dá aos Fornecedores Indiretos sandbox a capacidade de criar revendedores indiretos sandbox.

1. Pré-requisitos para a eliminação de um Revendedor Indireto Sandbox
    1. Suspender as assinaturas para cada cliente da Sandbox Reseller Indirect
    2. Eliminar todos os clientes do Revendedor Indireto
2. Limite de cinco Revendedores Indiretos Sandbox permitidos por Sandbox Indirect Provider. Uma vez eliminado o revendedor Sandbox Indirect, a quota será reposta.

## <a name="delete-sandbox-indirect-reseller-through-api"></a>Eliminar Revendor Indireto Sandbox através da API

### <a name="rest-request"></a>Pedido de DESCANSO

#### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido                                                                             |
|------------|-------------------------------------------------------------------------------------|
| **EXCLUIR** | [*{baseURL}*](partner-center-rest-urls.md)/v1//sandboxIndirectReseller/{revendedorD} |

#### <a name="request-headers"></a>Cabeçalhos do pedido

- Esta API é idempotente (não produzirá um resultado diferente se lhe chamar várias vezes)
- É necessário um ID de pedido e uma iD de correlação
- Para mais informações, consulte [os cabeçalhos REST do Partner Center](headers.md)

### <a name="request-example"></a>Exemplo de pedido

EXCLUIR https://api.partnercenter.microsoft.com/v1/sandboxIndirectReseller/{resellerID}

```http
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

####  <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Feb 2021 00:43:02 GMT
```

#### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e outras informações de depurações. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

Este método devolve os seguintes códigos de sucesso e erro:

| Código de Estado HTTP                     | Código de erro     | Description                                      |
|--------------------------------------|----------------|--------------------------------------------------|
| 401                                  | 6002           | Token não autorizado ou não uma conta de fornecedor de gorjeta |
| 403                                  | 6003           | Não é permitido eliminar o IR da Caixa de Areia                 |
| 403                                  | 6004           | Criar operação IR sandbox não permitida          |
| 409                                  | 1003           | Conflito ao criar inquilino                   |
