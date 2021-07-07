---
title: Definir funções de utilizador para um cliente
description: Dentro de uma conta de cliente, há um conjunto de funções de diretório. Pode atribuir contas de utilizador a essas funções.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a035d711ffa91200fa7b479ed5ec53929aa4feaf
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446705"
---
# <a name="set-user-roles-for-a-customer"></a>Definir funções de utilizador para um cliente

Dentro de uma conta de cliente, há um conjunto de funções de diretório. Pode atribuir contas de utilizador a essas funções.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Para atribuir uma função de diretório a um utilizador do cliente, crie um novo [**UserMember**](/dotnet/api/microsoft.store.partnercenter.models.roles.usermember) com os detalhes relevantes do utilizador. Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente especificado para identificar o cliente. A partir daí, utilize o método [**Diretório.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) com o ID de papel de diretório para especificar a função. Em seguida, aceda à coleção **UserMembers** e use o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.create) para adicionar o novo membro do utilizador à recolha de membros do utilizador atribuídos a essa função.

``` csharp
// UserMember createdUser;
// IAggregatePartner partnerOperations;
// Customer selectedCustomer;
// IDirectoryRole selectedRole;

// Create the new user member.
UserMember userMemberToAdd = new UserMember()
{
    UserPrincipalName = createdUser.UserPrincipalName,
    DisplayName = createdUser.DisplayName,
    Id = createdUser.Id
};

// Add the new user member to the role.
var userMemberAdded = partnerOperations.Customers.ById(selectedCustomer.Id).DirectoryRoles.ById(selectedRole.Id).UserMembers.Create(userMemberToAdd);
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: AddUserMemberToDirectoryRole.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| **Publicar** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directyroles/{role-ID}/usermembers HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros URI para identificar o cliente e a função corretos. Para identificar o utilizador a quem atribuir a função, forneça a informação de identificação no organismo de pedido.

| Nome                   | Tipo     | Necessário | Descrição                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor. |
| **id role**            | **guid** | Y        | O valor é um **id de função** formatado GUID que identifica a função a atribuir ao utilizador.                                                              |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades necessárias no corpo de pedido.

| Nome                  | Tipo       | Necessário | Descrição                            |
|-----------------------|------------|----------|----------------------------------------|
| **ID**                | **string** | Y        | O ID do utilizador para adicionar ao papel. |
| **DisplayName**       | **string** | Y        | O nome de exibição amigável do utilizador. |
| **Nome do UtilizadorPrincipal** | **string** | Y        | O nome do diretor do utilizador.        |
| **Atributos**        | **objeto** | Y        | Contém "ObjectType":"UserMember"     |

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/directoryroles/f023fd81-a637-4b56-95fd-791ac0226033/usermembers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a56cb2e5-a156-4f68-9155-57ffe2b93d18
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 180
Expect: 100-continue

{
    "Id": "a9ef48bb-8758-4590-a312-d4a47bfaded4",
    "DisplayName": "Daniel Tsai",
    "UserPrincipalName": "Daniel@dtdemocspcustomer005.onmicrosoft.com",
    "Attributes": {
        "ObjectType": "UserMember"
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Este método devolve a conta do utilizador com o ID de função anexado quando o utilizador é atribuído com sucesso a função.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 201 Created
Content-Length: 231
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
MS-RequestId: a56cb2e5-a156-4f68-9155-57ffe2b93d18
MS-CV: aia94+gnrEeQqkGr.0
MS-ServerId: 101112202
Date: Tue, 20 Dec 2016 23:36:55 GMT

{
    "displayName": "Daniel Tsai",
    "userPrincipalName": "Daniel@dtdemocspcustomer005.onmicrosoft.com",
    "roleId": "f023fd81-a637-4b56-95fd-791ac0226033",
    "id": "a9ef48bb-8758-4590-a312-d4a47bfaded4",
    "attributes": {
        "objectType": "UserMember"
    }
}
```
