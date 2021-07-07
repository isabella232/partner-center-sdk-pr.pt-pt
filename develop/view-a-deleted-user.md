---
title: Ver utilizadores eliminados para um cliente
description: Obtém uma lista de recursos do CustomerUser eliminados para um cliente por identificação do cliente. Pode configurar opcionalmente o tamanho da página. Deve fornecer um filtro.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f4fec958a9a6bb580d35de1cf3007e1db3b2b650
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445311"
---
# <a name="view-deleted-users-for-a-customer"></a>Ver utilizadores eliminados para um cliente

Obtém uma lista de recursos do CustomerUser eliminados para um cliente por identificação do cliente. Pode configurar opcionalmente o tamanho da página. Deve fornecer um filtro.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="what-happens-when-you-delete-a-user-account"></a>O que acontece quando se apaga uma conta de utilizador?

O estado do utilizador está definido para "inativo" quando apaga uma conta de utilizador. Permanece assim durante 30 dias, após o que a conta de utilizador e os seus dados associados são purgados e tornados irrecuperáveis. Se pretender restaurar uma conta de utilizador eliminada dentro da janela de 30 dias, consulte [Restaurar um utilizador eliminado para um cliente](restore-a-user-for-a-customer.md). Uma vez eliminada e marcada como "inativa", a conta de utilizador deixou de ser devolvida como membro da coleção de utilizadores (por exemplo, utilizando [a lista de todas as contas de utilizador para um cliente).](get-a-list-of-all-user-accounts-for-a-customer.md) Para obter uma lista de utilizadores eliminados que ainda não foram purgados, é necessário consultar as contas dos utilizadores que tenham sido definidas como inativas.

## <a name="c"></a>C\#

Para recuperar uma lista de utilizadores eliminados, construa uma consulta que filtra para os utilizadores do cliente cujo estado está definido para inativo. Em primeiro lugar, crie o filtro instantaneamente um objeto [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) com os parâmetros mostrados no seguinte corte de código. Em seguida, crie a consulta utilizando o método [**BuildIndexedQuery.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) Se não quiser resultados em página, pode utilizar o método [**BuildSimpleQuery.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente. Finalmente, ligue para o método [**de consulta**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.query) para enviar o pedido.

``` csharp
// IAggregatePartner partnerOperations;
// int customerUserPageSize;

// Create a filter for users whose status is inactive (i.e. deleted).
var filter = new SimpleFieldFilter("UserState", FieldFilterOperation.Equals, "Inactive");

// Build a paged query.
var simpleQueryWithFilter = QueryFactory.Instance.BuildIndexedQuery(customerUserPageSize, 0, filter);

// Send the request.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.Query(simpleQueryWithFilter);
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: GetCustomerInactiveUsers.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users?size={size}&filtro={{filter} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de percurso e consulta ao criar o pedido.

| Nome        | Tipo   | Necessário | Descrição                                                                                                                                                                        |
|-------------|--------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id cliente | guid   | Yes      | O valor é um id de cliente formatado GUID que identifica o cliente.                                                                                                            |
| size        | int    | No       | O número de resultados a apresentar ao mesmo tempo. Este parâmetro é opcional.                                                                                                     |
| filter      | filter | Yes      | A consulta que filtra a procura do utilizador. Para recuperar os utilizadores eliminados, deve incluir e codificar a seguinte cadeia: {"Field":"UserState","Value":"Inative", "Operador":"igual"}. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users?size=500&filter=%7B%22Field%22%3A%22UserState%22%2C%22Value%22%3A%22Inactive%22%2C%22Operator%22%3A%22equals%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c11feb95-55d2-45b6-9d1b-74b55d2221fb
MS-CorrelationId: 2b4ab588-f48c-4874-b479-a61895e107b2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma coleção de recursos [CustomerUser](user-resources.md#customeruser) no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 802
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 690b34ca-07c8-4f8a-ab13-f22a50594a43
MS-RequestId: 1187f9ad-02b4-4d96-b668-7cf3d289467b
MS-CV: 3TLmR9gz6EaCVCjR.0
MS-ServerId: 101112616
Date: Fri, 20 Jan 2017 19:13:14 GMT

{
    "totalCount": 1,
    "items": [{
            "usageLocation": "US",
            "id": "a45f1416-3300-4f65-9e8d-f123b397a4ea",
            "userPrincipalName": "e83763f7f2204ac384cfcd49f79f2749@dtdemocspcustomer005.onmicrosoft.com",
            "firstName": "Ferdinand",
            "lastName": "Filibuster",
            "displayName": "Ferdinand",
            "userDomainType": "none",
            "state": "inactive",
            "softDeletionTime": "2017-01-20T00:33:34Z",
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
    ],
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users?size=500&filter=%7B%22Field%22%3A%22UserStatus%22%2C%22Value%22%3A%22Inactive%22%2C%22Operator%22%3A%22equals%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
