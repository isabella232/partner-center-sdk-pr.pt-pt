---
title: Restaurar um utilizador eliminado para um cliente
description: Como restaurar um Utilizador eliminado pelo ID do cliente e iD do utilizador.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 04cca2f7c99023ef277f0f265a755be3e4692fa5e786ce37939b6aebd32a3ba3
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996908"
---
# <a name="restore-a-deleted-user-for-a-customer"></a>Restaurar um utilizador eliminado para um cliente

Como restaurar um **Utilizador** eliminado pelo ID do cliente e iD do utilizador.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- A identificação do utilizador. Se não tiver o ID do utilizador, consulte [utilizadores eliminados para um cliente](view-a-deleted-user.md).

## <a name="when-can-you-restore-a-deleted-user-account"></a>Quando pode restaurar uma conta de utilizador eliminada?

O estado do utilizador está definido para "inativo" quando apaga uma conta de utilizador. Permanece assim durante 30 dias, após o que a conta de utilizador e os seus dados associados são purgados e tornados irrecuperáveis. Só é possível restaurar uma conta de utilizador eliminada durante esta janela de 30 dias. Uma vez eliminada e marcada como "inativa", a conta de utilizador deixou de ser devolvida como membro da coleção de utilizadores (por exemplo, utilizando [a lista de todas as contas de utilizador para um cliente).](get-a-list-of-all-user-accounts-for-a-customer.md)

## <a name="c"></a>C\#

Para restaurar um utilizador, crie uma nova instância da classe [**CustomerUser**](/dotnet/api/microsoft.store.partnercenter.models.users.customeruser) e desaculte o valor da propriedade [**User.State**](/dotnet/api/microsoft.store.partnercenter.models.users.user.state) para [**UserState.Ative**](/dotnet/api/microsoft.store.partnercenter.models.users.userstate).

Restaura um utilizador eliminado definindo o estado do utilizador para ativo. Não é preciso repovoar os restantes campos no recurso do utilizador. Estes valores serão automaticamente restaurados a partir do recurso de utilizador eliminado e inativo. Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente e o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) para identificar o utilizador.

Por fim, ligue para o método [**Patch**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.patch) e passe a instância **CustomerUser** para enviar o pedido para restaurar o utilizador.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedCustomerUserId;

var updatedCustomerUser = new CustomerUser()
{
    State = UserState.Active
};

// Restore customer user information.
var restoredCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Patch(updatedCustomerUser);
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: CustomerUserRestore.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método    | URI do pedido                                                                                            |
|-----------|--------------------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de consulta para especificar o ID do cliente e o ID do utilizador.

| Nome                   | Tipo     | Necessário | Descrição                                                                                                              |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados a um determinado cliente. |
| **id utilizador**            | **guid** | Y        | O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.                                         |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades necessárias no corpo de pedido.

| Nome       | Tipo   | Necessário | Descrição                                                            |
|------------|--------|----------|------------------------------------------------------------------------|
| Estado      | string | Y        | O estado de utilizador. Para restaurar um utilizador eliminado, esta cadeia deve conter "ativo". |
| Atributos | objeto | N        | Contém "ObjectType": "CustomerUser".                                 |

### <a name="request-example"></a>Exemplo de pedido

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 6e668bc0-5bd7-44d6-b6fa-529d41ce9659
MS-CorrelationId: 32be760f-8282-4e01-a37b-829c8a700e8a
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 269
Expect: 100-continue

{
    "State": "active",
    "Attributes": {
        "ObjectType": "CustomerUser"
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedida, a resposta devolve a informação restaurada do utilizador no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [os Códigos de Erro DO Centro de Parceiros REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 465
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 32be760f-8282-4e01-a37b-829c8a700e8a
MS-RequestId: 6e668bc0-5bd7-44d6-b6fa-529d41ce9659
MS-CV: ZTeBriO7mEaiM13+.0
MS-ServerId: 101112616
Date: Fri, 20 Jan 2017 22:24:55 GMT

{
    "usageLocation": "US",
    "id": "a45f1416-3300-4f65-9e8d-f123b397a4ea",
    "userPrincipalName": "e83763f7f2204ac384cfcd49f79f2749@dtdemocspcustomer005.onmicrosoft.com",
    "firstName": "Ferdinand",
    "lastName": "Filibuster",
    "displayName": "Ferdinand",
    "userDomainType": "none",
    "state": "active",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "CustomerUser"
    }
}
```
