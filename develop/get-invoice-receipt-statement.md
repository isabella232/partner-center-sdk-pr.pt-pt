---
title: Obter declaração do recibo da fatura
description: Recupera uma declaração de recibo de fatura usando o ID da fatura e o ID do recibo.
ms.date: 02/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 96cef11d6778de2d9bf28e466d88a39f9415727d
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768713"
---
# <a name="get-invoice-receipt-statement"></a>Obter declaração do recibo da fatura

**Aplica-se a**

- Partner Center

Recupera uma declaração de recibo de fatura usando o ID da fatura e o ID do recibo.

> [!IMPORTANT]
> Esta funcionalidade aplica-se apenas às receitas fiscais de Taiwan.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID de fatura válido e um documento de recibo correspondente.

## <a name="c"></a>C\#

Para obter uma declaração de recibo de fatura por ID, a começar pelo Partner Center SDK v1.12.0, utilize a sua coleção **IPartner.Faturas** e ligue para o método **ById()** utilizando o ID da fatura, depois ligue para a recolha **de Recibos** e ligue para o **ById()** e ligue para os **métodos de documentos()** e **declaração()** para aceder à declaração de recibo de fatura. Por fim, ligue para os métodos **Get()** ou **GetAsync().**

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Receipts.ById(selectedReceipt).Documents.Statement.Get();
```

**Amostra**: [App de teste de consola](console-test-app.md). **Projeto**: PartnerSDK.FeatureSample **Class**: GetInvoiceReceiptStatement.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/faturas/{fatura-id}/recibos/{recibo-id}/documentos/declaração HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para obter a declaração de recibo de fatura.

| Nome       | Tipo   | Necessário | Descrição                                                                                    |
|------------|--------|-----------------------------------------------------------------------------------------------------------|
| fatura id | string | Sim      | O valor é um id de fatura que permite ao revendedor filtrar os resultados de uma determinada fatura. |
| recibo id | string | Sim      | O valor é um recibo-id que permite ao revendedor filtrar os recibos de uma determinada fatura. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/receipts/<receipt-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um fluxo pdf no corpo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 195556
Content-Type: application/pdf
MS-CorrelationId: a1d6ab41-5a30-4643-898b-b30d65d3a0a1
MS-RequestId: cc1ba6db-ab26-404a-9196-712b6395f518
Date: Tue, 05 Feb 2019 04:08:23 GMT

{
    _content    {System.Net.Http.ByteArrayContent}    System.Net.Http.HttpContent {System.Net.Http.ByteArrayContent}
    _content    {byte[195556]}    byte[]
    _headers    {Content-Type: application/pdf Content-Disposition: attachment; filename=E-Tax-8602768.pdf}
}
```
