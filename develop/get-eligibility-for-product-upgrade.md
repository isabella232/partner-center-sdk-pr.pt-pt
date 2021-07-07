---
title: Verifique a elegibilidade de um cliente para a atualização de um plano Azure
description: Pode utilizar o recurso ProductUpgradeRequest para devolver um recurso de melhoria de produtos para determinar se um cliente é elegível para atualizar a partir de uma subscrição de Microsoft Azure (MS-AZR-0145P) para um plano Azure.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 34a20611c7d92042b5432c5ffb3ba4702d77e0c2
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446263"
---
# <a name="check-a-customers-eligibility-for-upgrading-to-an-azure-plan"></a>Verifique a elegibilidade de um cliente para a atualização de um plano Azure

Pode utilizar o recurso [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) para verificar se um cliente é elegível para atualizar para um plano Azure a partir de uma subscrição de Microsoft Azure (MS-AZR-0145P) Este método devolve um recurso [**de edição do Produto**](product-upgrade-resources.md#productupgradeseligibility) Com a elegibilidade do produto para upgrade do cliente.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com credenciais app+utilizador. Siga o [modelo de aplicação seguro](enable-secure-app-model.md) ao utilizar a autenticação App+User com APIs do Partner Center.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- A família dos produtos.

## <a name="c"></a>C\#

Para verificar se um cliente é elegível para fazer upgrade para o plano Azure:

1. Crie um objeto **ProductUpgradesRequest** e especifique o identificador do cliente e o "Azure" como a família do produto.

2. Utilize a coleção **IAggregatePartner.ProductUpgrades.**
3. Ligue para o método **checkEelegibilidade** e passe no objeto **ProductUpgradesRequest,** que devolverá um objeto **de Melhoria de Produto.**

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

ProductUpgradesEligibility productUpgradeEligibility = partnerOperations.ProductUpgrades.CheckEligibility(productUpgradeRequest);

if (productUpgradeEligibility.IsEligibile)
{
    ....
}

```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/elegibilidade HTTP/1.1 |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

O organismo de pedido deve conter um recurso [**ProductUpgradeRequest.**](product-upgrade-resources.md#productupgraderequest)

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades/eligibility HTTP/1.1
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
        "productFamily": "azure"
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um recurso [**de melhoria de identidade do produto**](product-upgrade-resources.md#productupgradeseligibility) no organismo.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 Ok
Content-Length: 150
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 04 Oct 2019 20:35:35 GMT

{
    "customerId": "c1958bc7-3284-4952-a257-de594ee64743",
    "isEligible": true,
    "productFamily": "azure"
}
```
