---
title: Remover um utilizador cliente de uma função
description: Como remover um utilizador de uma função de diretório dentro de uma conta de cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 985b80a35182aefe283a8e9bbff75a1ff7bd9790157147fb943d8b18eb5c5079
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996993"
---
# <a name="remove-a-customer-user-from-a-role"></a>Remover um utilizador cliente de uma função

Como remover um utilizador de uma função de diretório dentro de uma conta de cliente.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Para remover um utilizador de uma função de diretório, selecione o cliente com o utilizador para modificar com uma chamada para o método [**IAggregatePartner.Customers.ById,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) a partir daí, especificar a função utilizando o método [**DirectórioRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) com o ID de papel de diretório. Em seguida, aceda ao método [**UserMembers.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.byid) para identificar o utilizador a remover, e o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermember.delete) para remover o utilizador da função.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedRoleId;
// string selectedUserMemberId;

partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedRoleId).UserMembers.ById(selectedUserMemberId).Delete();
```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: RemoveCustomerUserMemberFromDirectoryRole.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método     | URI do pedido                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| **EXCLUIR** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directyroles/{role-ID}/usermembers/{user-ID} HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros URI para identificar o cliente, função e utilizador corretos.

| Nome                   | Tipo     | Necessário | Descrição                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | O valor é um **design de cliente-inquilino-inquilino** formatado guid que identifica o cliente. |
| **id role**            | **guid** | Y        | O valor é um **id de função** formatado GUID que identifica o papel.                |
| **id utilizador**            | **guid** | Y        | O valor é um **id de utilizador** formatado GUID que identifica uma única conta de utilizador.   |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04%20/directoryroles/729827e3-9c14-49f7-bb1b-9608f156bbb8/usermembers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04%20 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0a00ec08-6273-46bb-ab6f-14a13959b381
MS-CorrelationId: 87d18a45-81fc-40cf-921a-b91cb82d67fe
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 0
Connection: Keep-Alive
```

## <a name="rest-response"></a>Resposta do REST

Se o utilizador for removido da função com sucesso, o corpo de resposta está vazio.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
MS-RequestId: e784d7aa-8c8d-45ee-8f97-9e09823d7338
MS-CV: es01VX8do0u2aTXw.0
MS-ServerId: 101112616
Date: Tue, 20 Dec 2016 23:16:35 GMT
```
