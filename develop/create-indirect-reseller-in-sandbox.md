---
title: Criar Revendedor Indireto na Caixa de Areia
description: Fornece informações aos fornecedores indiretos da Sandbox sobre a ativação de testes de ponta a ponta utilizando APIs.
ms.date: 5/24/2021
ms.author: vijvala
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 93e26792b66e447a0047bd550f4302c7fca4e87b
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973439"
---
# <a name="create-indirect-reseller-in-sandbox"></a>Criar Revendedor Indireto na Caixa de Areia

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud Germany

Este documento mostra como criar fornecedores indiretos sandbox e permitir testes de ponta a ponta utilizando APIs.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [Autenticação do Centro de Parceiros.](partner-center-authentication.md) Este cenário suporta a autenticação com credenciais app+utilizador.

## <a name="csp-indirect-provider"></a>CSP Indirect Provider

| Capacidades de produção             | Capacidades de caixa de areia                            |
|-------------------------------------|-------------------------------------------------|
| Vende através do revendedor indireto ao cliente final | Suportado |
| Detém todas as vendas, faturação, provisionamento e gestão/suporte | Suportado |
| Solicite uma parceria com os revendedores | Suportado |
| Ver clientes por Revendedor | Suportado |
| Adicionar novos clientes por revendedores | Suportado |
| Convidar clientes | Pedido de relacionamento com o cliente não suportado na Sandbox |
| Sandbox Indireta Fornecedor pode selecionar Sandbox IR (MPN ID) como o POR enquanto coloca a transação | Suportado |
| Não apoiado na produção | Sandbox Fornecedor Indireto pode criar Revendedor Indireto Sandbox |
| Sandbox MPN ID deve ser introduzido, o produto MPN ID não funcionará | Não apoiado na produção |
| Não apoiado na produção | Sandbox Fornecedor Indireto pode eliminar Revendedor Indireto Sandbox |

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller"></a>Sandbox Fornecedor Indireto – Criar Revendedor Indireto Sandbox

Esta funcionalidade só está disponível na Sandbox e dá aos Fornecedores Indiretos sandbox a capacidade de criar revendedores indiretos sandbox.

1. Limite de cinco revendedores indiretos sandbox permitidos por Sandbox Fornecedor Indireto
2. Sandbox Indirect Providers pode criar clientes com `associatedPartnerId` revendedor indireto Sandbox
3. Introduza o [ID MPN](/partner-center/mpn-create-a-partner-center-account) de uma região específica enquanto cria um Revendedor Indireto Sandbox. Vários Revendedores Indiretos sandbox podem ser criados com o mesmo ID MPN da Sandbox.
4. Apenas 75 clientes são permitidos por Sandbox Indireto Fornecedor

## <a name="sandbox-indirect-resellers--view-customers"></a>Sandbox Revendedores Indiretos – Ver clientes

1. Os Revendedores Indiretos sandbox podem ver a lista de clientes de sandbox por fornecedores indiretos da Sandbox.
2. Os Revendedores Indiretos sandbox podem gerir a conta do cliente utilizando permissões de administrador delegadas.

## <a name="create-sandbox-indirect-reseller-through-api"></a>Criar Sandbox Reseller Indireto através da API

### <a name="rest-request"></a>Pedido de DESCANSO

#### <a name="request-syntax"></a>Solicitar sintaxe

| **Método** | **URI do pedido**                                                        |
|------------|------------------------------------------------------------------------|
| **Publicar**   | [*{baseURL}*](partner-center-rest-urls.md)/v1//sandboxIndirectReseller |

#### <a name="request-headers"></a>Cabeçalhos do pedido

- Esta API é idempotente (não produzirá um resultado diferente se lhe chamar várias vezes).
- É necessária uma identificação de pedido e uma identificação de correlação.
- Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

#### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades necessárias no corpo de pedido.

| Propriedade             | Tipo           | Description                                      |
|----------------------|----------------|--------------------------------------------------|
| mpnId                | string         | O ID do MPN para o IR em região específica         |
| inquilino               | Cadeia de &lt; dicionário, corda&gt; | Recolha de informação básica que define uma conta a ser criada |
| legalBusinessProfile | Cadeia de &lt; dicionário, corda&gt; | Recolha de informação que represente a entidade empresarial legal, como contacto, morada e nome |
| organizaçãoProfileLanguage | Cadeia de &lt; dicionário, corda&gt; | O identificador de linguagem da organização |

Esta tabela descreve os imóveis exigidos no atributo do **inquilino.**

| Propriedade           | Tipo           | Description                         |
|--------------------|----------------|-------------------------------------|
| domínioPrefixo       | Corda; único | Domínio para a conta do inquilino       |
| name               | string         | Nome amigável do inquilino         |
| displayName        | string         | Mostrar o nome da conta        |
| adminUserName      | string         | Nome do utilizador para a conta de login |
| nome adminfirst     | string         | Primeiro nome para o utilizador administrador       |
| nome adminlastname      | string         | Apelido para o utilizador administrador        |
| adminAlernateEmail | string         | e-mail para o utilizador administrador            |
| país            | string         | País da conta              |
| cultura            | string         | Preferência linguística por conta     |

Esta tabela descreve as propriedades necessárias no atributo **legal BusinessinessProfile.**

| Propriedade       | Tipo                             | Description                          |
|----------------|----------------------------------|--------------------------------------|
| nome da empresa    | string                           | Nome da empresa para entidade jurídica        |
| address        | Cadeia de &lt; dicionário, corda&gt; | Endereço da localização da entidade jurídica |
| principalContact | Cadeia de &lt; dicionário, corda&gt; | Detalhes de contato da empresa       |
| cultura        | string                           | Linguagem preferida pela empresa    |

### <a name="request-example"></a>Exemplo de pedido

```http
{
    "mpnId": "6363276",
    "tenant": {
        "domainPrefix": "TipIRIntTest705",
        "name": "TipIRIntTest705",
        "displayName": "TipIRIntTest705",
        "adminUserName": "admin",
        "adminFirstName": "TipIRIntTest705",
        "adminLastName": "TipIRIntTest705",
        "adminAlternateEmail": "TipIRIntTest705@test.com",
        "country": "US",
        "culture": "en-us"
    },
    "legalBusinessProfile": {
        "companyName": "TipIRIntTest705",
        "address": {
            "country": "FR",
            "city": "Issy-les-Moulineaux",
            "state": "",
            "addressLine1": "39-41 quai du Président Roosevelt",
            "addressLine2": "",
            "postalCode": "92130"
        },
        "primaryContact": {
            "firstName": "Sandbox",
            "lastName": "Scenario",
            "email": "Sandbox.Scenario@test.com",
            "phoneNumber": "1234567890"
        },
        "culture": "en-US"
    },
    "organizationProfileLanguage": "en"
}
```

### <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve o recurso IV de Sandbox povoado no organismo de resposta.

```http
{

    "accountId": "6f94b119-793c-44c7-862b-c327c9057eab",
    "mpnId": "6363276",
    "tenant": {
        "id": "6f94b119-793c-44c7-862b-c327c9057eab",
        "adminUserAccount": "admin@TipIRIntTest705.onmicrosoft.com",
        "password": "\*\*\*\*\*\*”
    },
    "agreementSignature": {
        "id": "30ac23e7-e200-42cf-a5bc-dd9148cdc632",
        "accountId": "6f94b119-793c-44c7-862b-c327c9057eab",
        "agreementId": "1e18c5b2-e42a-4b84-82c8-d0155aa94c6e",
        "agreementType": "ValueAddedReseller",
        "dateSigned": "2021-02-23T18:10:14.8461137Z",
        "signedByFirstName": "Test123@PLAMUATT2NetNewTip.onmicrosoft.com",
        "signedByUserPrincipalName": "Test123@PLAMUATT2NetNewTip.onmicrosoft.com",
        "signedByUserObjectId": "e6e0c29d-acda-4ef2-b370-d37a4e06fb98",
        "signedByUserTenantId": "0e195b37-4574-4539-bc42-0e539b9684c0",
        "attributes": {
            "objectType": "AgreementSignatureResponse"
        }
    },
    "partnerRelationship": {
        "id": "0e195b37-4574-4539-bc42-0e539b9684c0",
        "name": "PLAMUATT2NetNew",
        "relationshipType": "is\_indirect\_reseller\_of",
        "state": "Active",
        "mpnId": "6363276",
        "attributes": {
            "objectType": "PartnerRelationshipResponse"
        }
    }
}
```
