---
title: Eliminar uma conta de utilizador para um cliente
description: Como eliminar uma conta de utilizador existente para um cliente.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c45646da43b8926f911942374de5da07f318c526
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973065"
---
# <a name="delete-a-user-account-for-a-customer"></a>Eliminar uma conta de utilizador para um cliente

Este artigo explica como eliminar uma conta de utilizador existente para um cliente.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Uma identificação de utilizador. Se não tiver o ID do utilizador, consulte [obter uma lista de todas as contas do utilizador para um cliente.](get-a-list-of-all-user-accounts-for-a-customer.md)

## <a name="deleting-a-user-account"></a>Apagar uma conta de utilizador

Quando elimina uma conta de utilizador, o estado do utilizador está definido para **inativo** durante 30 dias. Após 330 dias, a conta de utilizador e os seus dados associados são purgados e tornados irrecuperáveis.

Pode [restaurar uma conta de utilizador eliminada para um cliente](restore-a-user-for-a-customer.md) se a conta inativa estiver dentro da janela de 30 dias. No entanto, quando restaura uma conta que foi eliminada e marcada como inativa, a conta deixou de ser devolvida como membro da coleção de utilizadores (por exemplo, quando [obtém uma lista de todas as contas de utilizador de um cliente).](get-a-list-of-all-user-accounts-for-a-customer.md)

## <a name="c"></a>C\#

Para eliminar uma conta de utilizador do cliente existente:

1. Utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.

2. Ligue para o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para identificar o utilizador.

3. Ligue para o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) para eliminar o utilizador e definir o estado do utilizador para inativo.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string customerUserIdToDelete;

partnerOperations.Customers.ById(selectedCustomerId).Users.ById(customerUserIdToDelete).Delete();
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: DeleteCustomerUser.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método     | URI do pedido                                                                                            |
|------------|--------------------------------------------------------------------------------------------------------|
| DELETE     | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id} HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros de consulta para identificar o cliente e o utilizador.

| Nome                   | Tipo     | Necessário | Descrição                                                                                                               |
|------------------------|----------|----------|---------------------------------------------------------------------------------------------------------------------------|
| cliente-inquilino-id     | GUID     | Y        | O valor é um **design de cliente-inquilino** formatado pelo GUID que permite ao revendedor filtrar os resultados de um determinado cliente. |
| user-id                | GUID     | Y        | O valor é um **id** de utilizador com formato GUID que pertence a uma única conta de utilizador.                                          |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 0
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um código de estado **204 No Content.**

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [os Códigos de Erro DO Centro de Parceiros REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CV: 90KUJA7HKEaG8wHu.0
MS-ServerId: 101112616
Date: Tue, 24 Jan 2017 23:27:18 GMT
```
