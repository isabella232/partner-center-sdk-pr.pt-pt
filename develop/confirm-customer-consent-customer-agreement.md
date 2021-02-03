---
title: Confirmar aceitação do cliente do Contrato de Cliente Microsoft
description: Saiba como confirmar a aceitação do Cliente do Microsoft Customer Agreement utilizando APIs do Partner Center.
ms.date: 02/04/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 239ca43c70fb8aa7f0d06e564e6c0726b235ffbe
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770075"
---
# <a name="confirm-customer-acceptance-of-the-microsoft-customer-agreement-using-partner-center-apis"></a>Confirme a aceitação do cliente do Acordo de Cliente da Microsoft utilizando APIs do Partner Center

**Aplica-se a:**

- Partner Center

O Partner Center suporta atualmente a confirmação da aceitação pelo cliente do Microsoft Customer Agreement apenas na nuvem pública da *Microsoft.* Esta funcionalidade não se aplica atualmente a:

- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Este artigo descreve como confirmar ou re-confirmar a aceitação do cliente do Microsoft Customer Agreement.

## <a name="prerequisites"></a>Pré-requisitos

- Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.

- Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md). *Este cenário suporta apenas a autenticação App+User.*

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- A data **(data Acordada)** quando o cliente aceitou o Acordo de Cliente da Microsoft.

- Informação sobre o utilizador da organização do cliente que aceitou o Acordo de Cliente da Microsoft. O que está incluído:
  - Nome próprio
  - Apelido
  - Endereço de e-mail
  - Número de telefone (opcional)

## <a name="net"></a>.NET

Para confirmar ou confirmar a aceitação do cliente do Acordo de Cliente da Microsoft:

1. Recupere os metadados do acordo para o Acordo de Cliente da Microsoft. Tem de obter o **modeloId** do Microsoft Customer Agreement. Para mais detalhes, consulte [obter metadados de acordo para o Acordo de Cliente da Microsoft.](get-customer-agreement-metadata.md)

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
   ```

2. Crie um novo objeto **do Acordo** que contenha detalhes da confirmação.

3. Utilize a coleção **IAgreggatePartner.Customers** e ligue para o método **ById** com o id específico **cliente-inquilino.**

4. Utilize a propriedade **Agreements,** seguida de chamar **Create** or **CreateAsync**.

   ```csharp
   // string selectedCustomerId;

   var agreementToCreate = new Agreement
   {
       DateAgreed = DateTime.UtcNow,
       TemplateId = microsoftCustomerAgreementDetails.TemplateId,
       PrimaryContact = new Contact
       {
           FirstName = "Tania",
           LastName = "Carr",
           Email = "someone@example.com",
           PhoneNumber = "1234567890"
       }
   };

   Agreement agreement = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Create(agreementToCreate);
   ```

Uma amostra completa pode ser encontrada na classe [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.

## <a name="rest-request"></a>Pedido de DESCANSO

Para confirmar ou confirmar a aceitação do cliente do Acordo de Cliente da Microsoft:

1. Recupere os metadados do acordo para o Acordo de Cliente da Microsoft. Tem de obter o **modeloId** do Microsoft Customer Agreement. Para mais detalhes, consulte [obter metadados de acordo para o Acordo de Cliente da Microsoft.](get-customer-agreement-metadata.md)

2. Crie um novo recurso [ **do Agreement**](agreement-resources.md) para confirmar que um cliente aceitou o Acordo de Cliente da Microsoft. Utilize a seguinte [sintaxe de pedido DEE](#request-syntax).

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| POST   | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/acordos HTTP/1.1 |

#### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para especificar o cliente que está a confirmar.

| Nome               | Tipo | Necessário | Descrição                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| cliente-inquilino-id | GUID | Sim | O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades necessárias no corpo de pedido REST.

| Nome      | Tipo   | Descrição                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| Contrato | objeto | Detalhes fornecidos pelo parceiro para confirmar a aceitação do cliente do Acordo de Cliente da Microsoft. |

#### <a name="agreement"></a>Contrato

Esta tabela descreve os campos mínimos necessários para criar um recurso [ **do Acordo.**](agreement-resources.md)

| Propriedade       | Tipo   | Descrição                              |
|----------------|--------|------------------------------------------|
| principalContact | [Contacto](./utility-resources.md#contact) | Informações sobre o utilizador da organização do cliente que aceitou o Acordo de Cliente da Microsoft, incluindo:  **primeiro Nome,** **último Nome,** **e-mail** e **telefoneNumber** (opcional) |
| dataA acordado     | cadeia no formato de hora de data UTC |A data em que o cliente aceitou o contrato. |
| templateId     | string | Identificador único do tipo de contrato aceite pelo cliente. Pode obter o **modeloId** para o Acordo de Cliente da Microsoft recuperando os metadados do acordo para o Microsoft Customer Agreement. Consulte [os metadados de acordo para o Microsoft Customer Agreement](./get-customer-agreement-metadata.md) para obter mais detalhes. |
| tipo           | string | Tipo de acordo aceite pelo cliente. Utilize "MicrosoftCustomerAgreement" se o cliente aceitar o Acordo de Cliente da Microsoft. |

#### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um recurso [ **do Acordo**](./agreement-resources.md).

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.

Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

#### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 201 Created
Content-Length: 261
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "userId": "3d6f2c09-eb40-48ca-a4b3-d24c9c007531",
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```
