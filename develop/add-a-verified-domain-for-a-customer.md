---
title: Adicionar um domínio verificado para um cliente
description: Saiba como adicionar um domínio verificado à lista de domínios aprovados para um cliente no Partner Center. Faça-o utilizando APIs do Partner Center e REST APIs.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b634e7e3276fdabeac8175e09a6ae8d12732f409
ms.sourcegitcommit: b0534995c36d644cc5f7bdf31b2afd5355cf7149
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/16/2021
ms.locfileid: "122208097"
---
# <a name="add-a-verified-domain-to-the-list-of-approved-domains-for-an-existing-customer"></a>Adicione um domínio verificado à lista de domínios aprovados para um cliente existente 

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Como adicionar um domínio verificado à lista de domínios aprovados para um cliente existente.

## <a name="prerequisites"></a>Pré-requisitos

- Deve ser um parceiro que é um registrador de domínio.

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

## <a name="adding-a-verified-domain"></a>Adicionar um domínio verificado

Se for um Parceiro que seja um registrador de domínio, pode utilizar a `verifieddomain` API para publicar um novo recurso [de Domínio](#domain) na lista de domínios para um cliente existente. Para isso, identifique o cliente utilizando o seu CustomerTenantId. Especifique um valor para a propriedade VerifiedDomainName. Passe um recurso [de domínio](#domain) no Pedido com as propriedades de Nome, Capacidade, Autenticação, Estado e Verificação Incluídos. Para especificar que o novo [Domínio](#domain) é um domínio federado, desenrique a propriedade AuthenticationType no recurso [Domínio](#domain) para `Federated` , e inclua um recurso [Defederationsettings de domínio](#domain-federation-settings) no Pedido. Se o método for bem sucedido, a Resposta incluirá um recurso [de Domínio](#domain) para o novo domínio verificado.

### <a name="custom-verified-domains"></a>Domínios verificados personalizados

Ao adicionar um domínio verificado personalizado, um domínio que não esteja registado no **onmicrosoft.com,** tem de definir a propriedade [CustomerUser.immutableId](user-resources.md#customeruser) para um valor de ID único para o cliente para o qual está a adicionar o domínio. Este identificador único é necessário durante o processo de validação quando o domínio está a ser verificado. Para obter mais informações sobre as contas do utilizador do cliente, consulte [criar contas de utilizador para um cliente](create-user-accounts-for-a-customer.md).

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| POST   | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{CustomerTenantId}/verifieddomain HTTP/1.1 |

#### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para especificar o cliente para o qual está a adicionar um domínio verificado.

| Nome                   | Tipo     | Necessário | Descrição                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| CustomerTenantId | guid | Y        | O valor é um **CustomerTenantId** formatado guid que lhe permite especificar um cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades necessárias no corpo de pedido.

| Nome                                                  | Tipo   | Necessário                                      | Descrição                                                |
|-------------------------------------------------------|--------|-----------------------------------------------|--------------------------------------------------------|
| Nome deDomain Verificado                                    | string | Yes                                           | O nome de domínio verificado. |
| [Domínio](#domain)                                     | objeto | Yes                                           | Contém a informação de domínio. |
| [Restrições de Domínio](#domain-federation-settings) | objeto | Sim (Se AutenticaçãoType = `Federated` )     | As definições da federação de domínio a serem utilizadas se o domínio for um `Federated` domínio e não um `Managed` domínio. |

### <a name="domain"></a>Domínio

Esta tabela descreve as propriedades de **domínio** necessárias e opcionais no corpo de pedido.

| Nome               | Tipo                                     | Necessário | Descrição                                                                                                                                                                                                     |
|--------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AutenticaçãoType                                    | string           | Yes      | Define se o domínio é um `Managed` domínio ou um `Federated` domínio. Valores suportados: `Managed` `Federated` . . .|
| Funcionalidade                                            | string           | Yes      | Especifica a capacidade de domínio. Por exemplo, `Email`.                  |
| IsDefault                                             | booleano nupável | Não       | Indica se o domínio é o domínio padrão para o inquilino. Valores suportados: `True` `False` . . . `Null` .        |
| IsInitial                                             | booleano nupável | Não       | Indica se o domínio é um domínio inicial. Valores suportados: `True` `False` . . . `Null` .                       |
| Name                                                  | string           | Yes      | O nome de domínio.                                                          |
| RootDomain                                            | cadeia (de carateres)           | No       | O nome do domínio raiz.                                              |
| Estado                                                | string           | Yes      | O estado do domínio. Por exemplo, `Verified`. Valores suportados:  `Unverified` `Verified` . . . `PendingDeletion` .                               |
| VerificaçãoMethod                                    | string           | Yes      | O tipo de método de verificação de domínio. Valores suportados: `None` `DnsRecord` . . . `Email` .                                    |

### <a name="domain-federation-settings"></a>Definições da federação de domínio

Esta tabela descreve as propriedades necessárias e opcionais **de DomínioFederationSettings** no corpo de pedido.

| Nome   | Tipo   | Necessário | Descrição                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| ActiveLogOnUri                         | cadeia (de carateres)           | No      | A logon URI usada por clientes ricos. Esta propriedade é a URL STS Auth do Parceiro. |
| DefaultInteractiveAuthenticationMethod | cadeia (de carateres)           | No      | Indica o método de autenticação predefinido que deve ser utilizado quando uma aplicação requer que o utilizador tenha início de sessão interativo. |
| Federação Nome de Marca                    | cadeia (de carateres)           | No      | O nome da marca da federação.        |
| EmitenteUri                              | string           | Yes     | O nome do emitente dos certificados.                        |
| LogOffUri                              | string           | Yes     | O logoff URI. Esta propriedade descreve o URI de sedupro de domínio federado.        |
| MetadadataExchangeUri                    | cadeia (de carateres)           | No      | O URL que especifica o ponto final de troca de metadados utilizado para a autenticação a partir de aplicações ricas do cliente. |
| NextSigningCertificate                 | cadeia (de carateres)           | No      | O certificado utilizado para o futuro próximo pela ADFS V2 STS para assinar reclamações. Esta propriedade é uma representação codificada base64 do certificado. |
| OpenIdConnectDiscoveryEndpoint         | cadeia (de carateres)           | No      | O OpenID Ligação Discovery Endpoint do IDP STS federado. |
| PassiveLogOnUri                        | string           | Yes     | O logon URI usado por clientes passivos mais velhos. Esta propriedade é o endereço para enviar pedidos de inscrição federados. |
| Autoria DesferiçãoProtocol        | string           | Yes     | O formato para o token de autenticação. Por exemplo, `WsFed`. Valores suportados: `WsFed` , `Samlp` |
| PromptLoginBehavior                    | string           | Yes     | O tipo de comportamento de login rápido.  Por exemplo, `TranslateToFreshPasswordAuth`. Valores suportados: `TranslateToFreshPasswordAuth` `NativeSupport` , `Disabled` |
| AssinaturaCertificada                     | string           | Yes     | O certificado atualmente utilizado pela ADFS V2 STS para assinar reclamações. Esta propriedade é uma representação codificada base64 do certificado. |
| AssinaturaCertificateUpdateStatus         | cadeia (de carateres)           | No      | Indica o estado de atualização do certificado de assinatura. |
| AssinaturaCertificateUpdateStatus         | booleano nupável | Não      | Indica se o IDP STS suporta O MFA. Valores suportados: `True` `False` . . . `Null` .|

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/{CustomerTenantId}/verifieddomain HTTP/1.1
Authorization: Bearer <token>
Accept: application/json, text/plain, */*
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
Content-Type: application/json;charset=utf-8
X-Locale: "en-US"

{
    "VerifiedDomainName": "Example.com",
    "Domain": {
        "AuthenticationType": "Federated",
        "Capability": "Email",
        "IsDefault": Null,
        "IsInitial": Null,
        "Name": "Example.com",
        "RootDomain": null,
        "Status": "Verified",
        "VerificationMethod": "None"
    },
    "DomainFederationSettings": {
        "ActiveLogOnUri": "https://sts.microsoftonline.com/FederationPassive/",
        "DefaultInteractiveAuthenticationMethod": "http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password",
        "FederationBrandName": "FederationBrandName",
        "IssuerUri": "Example.com",
        "LogOffUri": "https://sts.microsoftonline.com/FederationPassive/",
        "MetadataExchangeUri": null,
        "NextSigningCertificate": null,
        "OpenIdConnectDiscoveryEndpoint": "https://sts.contoso.com/adfs/.well-known/openid-configuration",
        "PassiveLogOnUri": "https://sts.microsoftonline.com/Trust/2005/UsernameMixed",
        "PreferredAuthenticationProtocol": "WsFed",
        "PromptLoginBehavior": "TranslateToFreshPasswordAuth",
        "SigningCertificate": <Certificate Signature goes here>,
        "SigningCertificateUpdateStatus": null,
        "SupportsMfa": true
    }
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, esta API devolve um recurso [de Domínio](#domain) para o novo domínio verificado.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 201 Created
Content-Length: 206
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
Date: Tue, 14 Feb 2017 20:06:02 GMT

{
    "authenticationType": "federated",
    "capability": "email",
    "isDefault": false,
    "isInitial": false,
    "name": "Example.com",
    "status": "verified",
    "verificationMethod": "dns_record"
}
```
