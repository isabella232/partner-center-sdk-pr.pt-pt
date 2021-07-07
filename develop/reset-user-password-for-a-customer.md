---
title: Repor a palavra-passe de utilizador para um cliente
description: A reposição de uma palavra-passe é semelhante à atualização de outros detalhes numa conta de utilizador existente para o seu cliente.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: f3661a588f566485cbd58035c63ae9f8e5d383af
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445685"
---
# <a name="reset-user-password-for-a-customer"></a>Repor a palavra-passe de utilizador para um cliente

A reposição de uma palavra-passe é semelhante à atualização de outros detalhes numa conta de utilizador existente para o seu cliente.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Para redefinir uma palavra-passe para um utilizador de cliente especificado, recupere primeiro o ID do cliente especificado e o utilizador-alvo. Em seguida, crie um novo objeto **CustomerUser** que contenha a informação para o cliente existente, mas com um novo objeto **PasswordProfile.** Em seguida, use a sua coleção **IAggregatePartner.Customers** e ligue para o método **ById().** Em seguida, ligue para a propriedade **do Utilizadores,** o método **ById()** e, em seguida, o método **Patch.**

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// CustomerUser specifiedUser;

var selectedCustomer = partnerOperations.Customers.ById(selectedCustomerId).Get();
var userToUpdate = new CustomerUser()
   {
      PasswordProfile = new PasswordProfile() { ForceChangePassword = true, Password = "newPassword" },
      DisplayName = "Roger Federer",
      FirstName = "Roger",
      LastName = "Federer",
      UsageLocation = "US",
      UserPrincipalName = Guid.NewGuid().ToString("N") + "@" + selectedCustomer.CompanyProfile.Domain.ToString()
   };

// update customer user information
User updatedCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(specifiedUser.Id).Patch(userToUpdate);

```

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método    | URI do pedido                                                                                  |
|-----------|----------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/utilizadores HTTP/1.1 |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para identificar o cliente correto.

| Nome                   | Tipo     | Necessário | Descrição                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **cliente-inquilino-id** | **guid** | Y        | O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor. |
| **id utilizador**            | **guid** | Y        | O valor é um **id de utilizador** formatado GUID que pertence a uma única conta de utilizador.                                                                       |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

### <a name="request-example"></a>Exemplo de pedido

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
{
     "passwordProfile":{
        password: "Renew456*",
        forceChangePassword: true
      },

      "attributes": {
        "objectType": "CustomerUser"
      }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve as informações do utilizador, juntamente com as informações atualizadas da palavra-passe.

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
  "usageLocation": "AX",
  "id": "95794928-9abe-4548-8b43-50ffc20b9404",
  "userPrincipalName": "aaaa4@abcdefgh1234.ccsctp.net",
  "firstName": "aaaa4",
  "lastName": "aaaa4",
  "displayName": "aaaa4",
  "passwordProfile": {
    "forceChangePassword": false,
    "password": "Renew456*"
  },
  "lastDirectorySyncTime": null,
  "userDomainType": "none",
  "state": "active",
  "softDeletionTime": null,
  "links": {
    "self": {
      "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/users/95794928-9abe-4548-8b43-50ffc20b9404",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "CustomerUser"
  }
}
```
