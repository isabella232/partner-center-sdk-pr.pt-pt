---
title: Verificar a disponibilidade do domínio
description: Como determinar se um domínio está disponível para utilização.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 84edb5b7510642ec44dad3d4f92349e40eb10b24
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769607"
---
# <a name="verify-domain-availability"></a>Verificar a disponibilidade do domínio

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Como determinar se um domínio está disponível para utilização.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um domínio (por `contoso.onmicrosoft.com` exemplo).

## <a name="c"></a>C\#

Para verificar se um domínio está disponível, ligue pela primeira vez [**iAggregatePartner.Domains**](/dotnet/api/microsoft.store.partnercenter.ipartner.domains) para obter uma interface para operações de domínio. Em seguida, ligue para o método [**ByDomain**](/dotnet/api/microsoft.store.partnercenter.domains.idomaincollection.bydomain) com o domínio para verificar. Este método recupera uma interface para as operações disponíveis para um domínio específico. Finalmente, ligue para o método [**Exista**](/dotnet/api/microsoft.store.partnercenter.domains.idomain.exists) para ver se o domínio já existe.

``` csharp
// IAggregatePartner partnerOperations;
// const string domain = "contoso.onmicrosoft.com";

bool result = partnerOperations.Domains.ByDomain(domain).Exists();
```

**Amostra**: [App de teste de consola](console-test-app.md). **Projeto**: Partner Center SDK Samples **Class**: CheckDomainAvailability.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                              |
|----------|--------------------------------------------------------------------------|
| **CABEÇA** | [*{baseURL}*](partner-center-rest-urls.md)/v1/domínios/{domínio} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para verificar a disponibilidade de domínio.

| Nome       | Tipo       | Necessário | Descrição                                   |
|------------|------------|----------|-----------------------------------------------|
| **domínio** | **cadeia** | Y        | Uma corda que identifica o domínio para verificar. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum

### <a name="request-example"></a>Exemplo de pedido

```http
HEAD https://api.partnercenter.microsoft.com/v1/domains/contoso.onmicrosoft.com HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>Resposta do REST

Se o domínio existir, não está disponível para utilização e é devolvido um código de estado de resposta 200 OK. Se o domínio não for encontrado, está disponível para utilização e é devolvido um código de estado de resposta 404 Não Encontrado.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example-for-when-the-domain-is-already-in-use"></a>Exemplo de resposta para quando o domínio já está em uso

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CV: 7UXAHds8J0mNUCSp.0
MS-ServerId: 201022015
Date: Tue, 31 Jan 2017 22:22:35 GMT
```

### <a name="response-example-for-when-the-domain-is-available"></a>Exemplo de resposta para quando o domínio está disponível

```http
HTTP/1.1 404 Not Found
Content-Length: 0
MS-CorrelationId: 54770745-17f0-433c-bd7b-0265e5b38f98
MS-RequestId: 1169a4cd-3be7-4e29-9cb3-0f78ffa2e91e
MS-CV: RRmc+bEw9U2e97CC.0
MS-ServerId: 202010406
Date: Tue, 31 Jan 2017 22:36:01 GMT
```
