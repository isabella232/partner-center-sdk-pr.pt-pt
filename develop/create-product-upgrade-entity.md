---
title: Criar uma entidade de atualização de produtos para um cliente
description: Pode utilizar o recurso ProductUpgradeRequest para criar uma entidade de upgrade de produtos para atualizar um cliente para uma determinada família de produtos.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 45830033d93e0906eafc169cf04b997e2ff7c3d8
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768815"
---
# <a name="create-a-product-upgrade-entity-for-a-customer"></a>Criar uma entidade de atualização de produtos para um cliente

**Aplica-se a:**

- Partner Center

Pode criar uma entidade de upgrade de produtos para atualizar um cliente para uma determinada família de produtos (por exemplo, plano Azure) utilizando o recurso **ProductUpgradeRequest.**

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com credenciais app+utilizador. Siga o [modelo de aplicação seguro](enable-secure-app-model.md) ao utilizar a autenticação App+User com APIs do Partner Center.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- A família de produtos à qual pretende atualizar o cliente.

## <a name="c"></a>C\#

Para atualizar um cliente para o plano Azure:

1. Crie um objeto **ProductUpgradesRequest** e especifique o identificador do cliente e o "Azure" como a família do produto.

2. Utilize a coleção **IAggregatePartner.ProductUpgrades.**

3. Ligue para o método **Criar** e passe no objeto **ProductUpgradesRequest,** que irá devolver uma corda **de cabeçalho de localização.**

4. Extrair o **id de atualização** da cadeia do cabeçalho de localização que pode ser usada para [consultar o estado de atualização](get-product-upgrade-status.md).

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "Azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

var productUpgradeLocationHeader = partnerOperations.ProductUpgrades.Create(productUpgradeRequest);

var upgradeId = Regex.Split(productUpgradeLocationHeader, "/")[1];

```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/productupgrades HTTP/1.1 |

#### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

#### <a name="request-body"></a>Corpo do pedido

O organismo de pedido deve conter um recurso [ProductUpgradeRequest.](product-upgrade-resources.md#productupgraderequest)

#### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c245d5f2-1de3-4ae0-9e42-95e38e3cb8ff
MS-CorrelationId: e3f26e6a-044f-4371-ad52-0d91ce4200be
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 340
Expect: 100-continue
Connection: Keep-Alive
{
  "customerId": "4c721420-72ad-4708-a0a7-371a2f7b0969",
  "productFamily": "Azure"
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedida, a resposta contém um **cabeçalho de localização** que tem um URI que pode ser usado para recuperar o estado de atualização do produto. Guarde este URI para utilização com outras APIs de REST relacionadas.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: productUpgrades/42d075a4-bfe7-43e7-af6d-7c68a57edcb4
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 28 Sep 2019 20:35:35 GMT
```
