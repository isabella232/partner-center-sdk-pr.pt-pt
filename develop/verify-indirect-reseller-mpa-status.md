---
title: Verifique o estado de assinatura do Acordo de Parceiro da Microsoft de um revendedor indireto
description: Pode utilizar a API AgreementStatus para verificar se um revendedor indireto assinou o Acordo de Parceiro da Microsoft.
ms.date: 07/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fa9480424eccc933bc9c28c3879a195fbd5f2bb1
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711908"
---
# <a name="verify-an-indirect-resellers-microsoft-partner-agreement-signing-status"></a>Verifique o estado de assinatura do Acordo de Parceiro da Microsoft de um revendedor indireto

**Aplica-se a:**

- Partner Center
- Centro de Parceiros do Microsoft Cloud for US Government

Pode verificar se um revendedor indireto assinou o Microsoft Partner Agreement utilizando o seu ID (MPN) (PGA/PLA) ou O ID do Fornecedor de Soluções cloud (CSP) (ID da Microsoft). Pode utilizar um destes identificadores para verificar o estado de assinatura do Acordo de Parceiro da Microsoft utilizando a API **do AgreementStatus.**

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação apenas com credenciais app+User.

- O ID MPN (PGA/PLA) ou o ID do inquilino CSP (Microsoft ID) do revendedor indireto. *Tens de usar um destes dois identificadores.*

## <a name="c"></a>C\#

Para obter o estado de assinatura do Microsoft Partner Agreement de um revendedor indireto:

1. Utilize a sua coleção **IAggregatePartner.Compliance** para ligar para a propriedade **AgreementSignatureStatus.**

2. Ligue para o método [**Get()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync)

``` csharp
// IAggregatePartner partnerOperations;

var agreementSignatureStatusByMpnId = partnerOperations.Compliance.AgreementSignatureStatus.Get(mpnId:"Enter MPN Id (PGA/PLA)");

var agreementSignatureStatusByTenantId = partnerOperations.Compliance.AgreementSignatureStatus.Get(tenantId: "Enter Tenant Id");
```

- Amostra: **[App de teste de consola](console-test-app.md)**
- Projeto: **PartnerCenterSDK.FeaturesSamples**
- Classe: **GetAgreementSignatureStatus.cs**

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido |
| ------ | ----------- |
| **Obter** | *[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus?mpnId={MpnId}}&inquilinoId={TenantId} |

#### <a name="uri-parameters"></a>Parâmetros URI

Deve fornecer um dos dois parâmetros de consulta seguintes para identificar o parceiro. Se não fornecer um destes dois parâmetros de consulta, receberá um erro de **400 (Mau pedido).**

| Nome | Tipo | Necessário | Descrição |
| ---- | ---- | -------- | ----------- |
| **MpnId** | int | No | Um ID da Rede de Parceiros da Microsoft (PGA/PLA) que identifica o revendedor indireto. |
| **TenantId** | GUID | No | Um ID da Microsoft que identifica a conta CSP do revendedor indireto. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para mais informações, consulte [Partner Center REST](headers.md).

### <a name="request-examples"></a>Solicitar exemplos

#### <a name="request-using-mpn-id-pgapla"></a>Pedido de utilização de ID MPN (PGA/PLA)

O seguinte pedido de exemplo obtém o estatuto de assinatura do Acordo de Parceiros microsoft do revendedor indireto usando o ID da Rede de Parceiros microsoft do revendedor indireto.

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?mpnid=1234567 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

#### <a name="request-using-csp-tenant-id"></a>Pedido de utilização de ID do inquilino da CSP

O seguinte pedido de exemplo obtém o estatuto de assinatura do Acordo de Parceiros da Microsoft do revendedor indireto usando o ID do inquilino CSP do revendedor indireto (Microsoft ID).

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?tenantId=a2898e3a-06ca-454e-a0d0-c73b0ee36bba HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>Resposta do REST

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte o [erro do Partner Center REST](error-codes.md).

### <a name="response-example-success"></a>Exemplo de resposta (sucesso)

A resposta de exemplo a seguir retorna com sucesso se o revendedor indireto assinou o Acordo de Parceiro da Microsoft.

```http
HTTP/1.1 200 OK
Content-Length: 29
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: jn3r+1wpE06nCt/0.0
MS-ServerId: 0000005B
Date: Tue, 15 Oct 2019 12:44:34 GMT
Connection: close
{
    "isAgreementSigned": true
}
```

### <a name="response-examples-failure"></a>Exemplos de resposta (falha)

Pode receber respostas semelhantes aos seguintes exemplos quando o estado de assinatura do Acordo de Parceiro microsoft do revendedor indireto não puder ser devolvido.

#### <a name="non-guid-formatted-csp-tenant-id"></a>ID de inquilino csp não-GUID formatado

A resposta de exemplo a seguir é devolvida quando o ID do inquilino do CSP que passou para a API não é um GUID.

```http
HTTP/1.1 400 Bad Request
Content-Length: 105
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: rbuZl5lbAkyq8WGK.0
MS-ServerId: 00000055
Date: Wed, 16 Oct 2019 08:55:23 GMT
Connection: close
{
    "code": 2000,
    "description": "Tenant Id must be a GUID.",
    "data": [],
    "source": "PartnerApiServiceControllers"
}
```

#### <a name="non-numeric-mpn-id"></a>ID de MPN não-numérico

A resposta de exemplo a seguir é devolvida quando o ID MPN (PGA/PLA) que passou para a API não é numérico.

```http
HTTP/1.1 400 Bad Request
Content-Length: 103
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: cP5JiS4sv0GJxlJ9.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 08:58:45 GMT
Connection: close
{
    "code": 2000,
    "description": "MPN Id must be numeric.",
    "data": [],
    "source": "PartnerApiServiceControllers"
}
```

#### <a name="no-mpn-id-or-csp-tenant-id"></a>Sem ID MPN ou ID de inquilino CSP

A resposta de exemplo a seguir é devolvida quando ainda não passou um ID de MPN (PGA/PLA) ou ID do inquilino CSP à API. Deve passar um dos dois tipos de identificação para a API.

```http
HTTP/1.1 400 Bad Request
Content-Length: 114
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: hEV736v4qk6joDMR.0
MS-ServerId: 00000055
Date: Wed, 16 Oct 2019 09:00:30 GMT
Connection: close
{
    "code": 2001,
    "description": "Both MPN Id and Tenant Id cannot be empty.",
    "data": [],
    "source": "ComplianceController"
}
```

#### <a name="both-mpn-id-and-csp-tenant-id-passed"></a>Tanto MPN ID como CSP inquilino ID passou

A resposta de exemplo a seguir é devolvida quando passa o ID mpn (PGA/PLA) e o ID do inquilino da CSP para a API. Deve passar *apenas um* dos dois tipos de identificador para a API.

```http
HTTP/1.1 400 Bad Request
Content-Length: 119
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: WTsLWK5UlUW9sZjH.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 09:02:30 GMT
Connection: close
{
    "code": 2000,
    "description": "Both MPN Id and Tenant Id should not be passed.",
    "data": [],
    "source": "ComplianceController"
}
```

#### <a name="csp-indirect-reseller-mpn-id-pgapla-is-either-invalid-or-not-migrated-from-partner-membership-center-to-partner-center"></a>CSP Reseller Indirect MPN Id (PGA/PLA) é inválido ou não migrado do Centro de Membros de Parceiros para Centro de Parceiros

A resposta de exemplo a seguir é devolvida quando o revendedor indireto MPN ID (PGA/PLA) passou ou é inválido ou não é migrado do Centro de Membros do Parceiro para o Partner Center. [Saiba mais](https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2200,
    "description": "MPN Id 123456 is either invalid or not yet migrated to Partner Center. Please advise your reseller to migrate the reseller MPN ID to Partner Center to continue with this order.",
    "data": [
        "https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx"
    ],
    "source": "PartnerFD"
}
```

#### <a name="csp-indirect-provider-region-and-csp-indirect-reseller-region-does-not-match"></a>Região de Fornecedor Indireto CSP e região de Revendedor Indireto CSP não correspondem

A resposta de exemplo a seguir é devolvida quando a região do revendedor indireto MPN ID (PGA/PLA) não corresponde à região do Fornecedor Indireto. [Saiba mais](/partner-center/mpa-indirect-provider-faq) sobre as Regiões da CSP.

```http
HTTP/1.1 400 Bad Request
Content-Length: 119
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: WTsLWK5UlUW9sZjH.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 09:02:30 GMT
Connection: close
{
    "code": 2201,
    "description": "The CSP region of the MPN ID 1234567 doesn’t match the CSP region from where you are placing the order. Provide the MPN ID for the CSP region where you are placing the order.",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq" 
    ],
    "source": "PartnerFD"
}
```

#### <a name="csp-indirect-reseller-account-exists-in-partner-center-but-hasnt-signed-the-mpa"></a>CSP Conta de Revendedor Indireto existe no Partner Center mas não assinou a MPA

A resposta de exemplo a seguir é devolvida quando a conta CSP Indirect Reseller no Partner Center não assinou a MPA. [Saiba mais](/partner-center/mpa-indirect-provider-faq)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2203,
    "description": "MPN Id 123456 has not signed Microsoft Partner Agreement (MPA) for the CSP region where the order is being placed. Please advise your reseller to sign MPA to continue with the order.",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```

#### <a name="no-csp-indirect-reseller-account-is-associated-with-the-given-mpn-id"></a>Nenhuma conta CSP Reseller Indirect está associada com o ID MPN dado

A resposta de exemplo a seguir é devolvida quando o Partner Center pode reconhecer o ID MPN (PGA/PLA) aprovado no pedido, mas não há nenhuma inscrição CSP associada ao ID MPN (PGA/PLA). [Saiba mais](/partner-center/mpa-indirect-provider-faq)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2204,
    "description": "MPN Id 123456 is not associated with a CSP Indirect Reseller account in Partner Center. Please advise your reseller to enroll into the CSP program as an indirect reseller in Partner Center.",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```

#### <a name="invalid-tenant-id"></a>ID do inquilino inválido

A resposta de exemplo a seguir é devolvida quando o Partner Center não encontra qualquer conta associada ao ID do Inquilino passado no pedido.

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2205,
    "description": "Partner Center doesn't find any account associated to the Tenant ID 12345678-ACBD-1234-ABCD-123456789ABC",
    "data": [],
    "source": "PartnerFD"
}
```

#### <a name="no-mpa-found-with-the-given-tenant-id"></a>Nenhuma MPA encontrada com a iD do inquilino dado

A resposta de exemplo a seguir é devolvida quando o Partner Center não consegue encontrar qualquer assinatura MPA com o ID do inquilino. [Saiba mais](/partner-center/mpa-indirect-provider-faq)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2206,
    "description": "Parnter Center Account associated to Tenant Id 12345678-ACBD-1234-ABCD-123456789ABC hasn't signed the agreement",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```