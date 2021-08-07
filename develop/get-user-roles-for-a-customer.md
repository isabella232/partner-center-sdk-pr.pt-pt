---
title: Obter funções de utilizador para um cliente
description: Obtenha uma lista de todas as funções/permissões anexadas a uma conta de utilizador. As variações incluem obter uma lista de todas as permissões em todas as contas de utilizador para um cliente, e obter uma lista de utilizadores que têm uma determinada função.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b139ee69ae5148896b1a438b061907e022175f318956667cebb91ead15b863f6
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989343"
---
# <a name="get-user-roles-for-a-customer"></a>Obter funções de utilizador para um cliente

Obtenha uma lista de todas as funções/permissões anexadas a uma conta de utilizador. As variações incluem obter uma lista de todas as permissões em todas as contas de utilizador para um cliente, e obter uma lista de utilizadores que têm uma determinada função.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Para recuperar todas as funções de diretório para um cliente especificado, recupere primeiro o ID do cliente especificado. Em seguida, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().** Em seguida, ligue para a propriedade **DirectoryRoles,** seguida do método **Get()** ou **GetAsync().**

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var directoryRoles = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.Get();
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: GetCustomerDirectoryRoles.cs

Para recuperar uma lista de utilizadores de clientes que têm uma determinada função, primeiro recupere o ID do cliente especificado e o ID de papel de diretório. Em seguida, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().** Em seguida, ligue para a propriedade **Do Diretório,** em seguida, o método **ById()** e, em seguida, a propriedade **UserMembers,** o seguido pelo método **Get()** ou **GetAsync().**

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;
// string selectedDirectoryRoleId;

var userMembers = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedDirectoryRoleId).UserMembers.Get();
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerDirectoryRoleUserMembers.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/users/{user-id}/diretórios HTTP/1.1 |
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/diretórios HTTP/1.1                 |
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directyroles/{role-ID}/usermembers    |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para identificar o cliente correto.

| Nome                   | Tipo     | Necessário | Descrição                                                                                                                                                                                                 |
|------------------------|----------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.                                                      |
| **id utilizador**            | **guid** | N        | O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.                                                                                                                            |
| **id role**            | **guid** | N        | O valor é um **id de função** formatado GUID que pertence a um tipo de papel. Você pode obter estes IDs consultando todas as funções de diretório para um cliente, em todas as contas do utilizador. (O segundo cenário, acima). |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id>/directoryroles HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma lista das funções associadas à conta de utilizador dada.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST

{
      "totalCount": 2,
      "items": [
        {
          "name": "Helpdesk Administrator",
          "id": "729827e3-9c14-49f7-bb1b-9608f156bbb8",
          "attributes": { "objectType": "DirectoryRole" }
        },
        {
          "name": "User Account Administrator",
          "id": "fe930be7-5e62-47db-91af-98c3a49a38b1",
          "attributes": { "objectType": "DirectoryRole" }
        }
      ],
      "attributes": { "objectType": "Collection" }
}
```
