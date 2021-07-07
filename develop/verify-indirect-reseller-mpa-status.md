---
title: Verifique o estado de assinatura do Acordo de Parceiro da Microsoft de um revendedor indireto
description: Pode utilizar a API AgreementStatus para verificar se um revendedor indireto assinou o Acordo de Parceiro da Microsoft.
ms.date: 07/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f83acc61624a72354c390905b1250bc021dd39aa
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529839"
---
# <a name="verify-an-indirect-resellers-microsoft-partner-agreement-signing-status"></a><span data-ttu-id="2638c-103">Verifique o estado de assinatura do Acordo de Parceiro da Microsoft de um revendedor indireto</span><span class="sxs-lookup"><span data-stu-id="2638c-103">Verify an indirect reseller's Microsoft Partner Agreement signing status</span></span>

<span data-ttu-id="2638c-104">**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2638c-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2638c-105">Pode verificar se um revendedor indireto assinou o Microsoft Partner Agreement utilizando o seu ID (MPN) (PGA/PLA) ou Fornecedor de Soluções em Nuvem (CSP) (ID) de inquilinos(Microsoft ID).</span><span class="sxs-lookup"><span data-stu-id="2638c-105">You can verify whether an indirect reseller has signed the Microsoft Partner Agreement using their Microsoft Partner Network (MPN) ID (PGA/PLA) or Cloud Solution Provider (CSP) tenant ID (Microsoft ID).</span></span> <span data-ttu-id="2638c-106">Pode utilizar um destes identificadores para verificar o estado de assinatura do Acordo de Parceiro da Microsoft utilizando a API **do AgreementStatus.**</span><span class="sxs-lookup"><span data-stu-id="2638c-106">You can use one of these identifiers to check the Microsoft Partner Agreement signing status using the **AgreementStatus** API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2638c-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2638c-107">Prerequisites</span></span>

- <span data-ttu-id="2638c-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2638c-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2638c-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="2638c-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="2638c-110">O ID MPN (PGA/PLA) ou o ID do inquilino CSP (Microsoft ID) do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="2638c-110">The MPN ID (PGA/PLA) or the CSP tenant ID (Microsoft ID) of the indirect reseller.</span></span> <span data-ttu-id="2638c-111">*Tens de usar um destes dois identificadores.*</span><span class="sxs-lookup"><span data-stu-id="2638c-111">*You must use one of these two identifiers.*</span></span>

## <a name="c"></a><span data-ttu-id="2638c-112">C\#</span><span class="sxs-lookup"><span data-stu-id="2638c-112">C\#</span></span>

<span data-ttu-id="2638c-113">Para obter o estado de assinatura do Microsoft Partner Agreement de um revendedor indireto:</span><span class="sxs-lookup"><span data-stu-id="2638c-113">To get the Microsoft Partner Agreement signature status of an indirect reseller:</span></span>

1. <span data-ttu-id="2638c-114">Utilize a sua coleção **IAggregatePartner.Compliance** para ligar para a propriedade **AgreementSignatureStatus.**</span><span class="sxs-lookup"><span data-stu-id="2638c-114">Use your **IAggregatePartner.Compliance** collection to call the **AgreementSignatureStatus** property.</span></span>

2. <span data-ttu-id="2638c-115">Ligue para o método [**Get()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) ou [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync)</span><span class="sxs-lookup"><span data-stu-id="2638c-115">Call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var agreementSignatureStatusByMpnId = partnerOperations.Compliance.AgreementSignatureStatus.Get(mpnId:"Enter MPN Id (PGA/PLA)");

var agreementSignatureStatusByTenantId = partnerOperations.Compliance.AgreementSignatureStatus.Get(tenantId: "Enter Tenant Id");
```

- <span data-ttu-id="2638c-116">Amostra: **[App de teste de consola](console-test-app.md)**</span><span class="sxs-lookup"><span data-stu-id="2638c-116">Sample: **[Console test app](console-test-app.md)**</span></span>
- <span data-ttu-id="2638c-117">Project: **PartnerCenterSDK.FeaturesSamples**</span><span class="sxs-lookup"><span data-stu-id="2638c-117">Project: **PartnerCenterSDK.FeaturesSamples**</span></span>
- <span data-ttu-id="2638c-118">Classe: **GetAgreementSignatureStatus.cs**</span><span class="sxs-lookup"><span data-stu-id="2638c-118">Class: **GetAgreementSignatureStatus.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="2638c-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2638c-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2638c-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2638c-120">Request syntax</span></span>

| <span data-ttu-id="2638c-121">Método</span><span class="sxs-lookup"><span data-stu-id="2638c-121">Method</span></span> | <span data-ttu-id="2638c-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2638c-122">Request URI</span></span> |
| ------ | ----------- |
| <span data-ttu-id="2638c-123">**Obter**</span><span class="sxs-lookup"><span data-stu-id="2638c-123">**GET**</span></span> | <span data-ttu-id="2638c-124">*[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus?mpnId={MpnId}}&inquilinoId={TenantId}</span><span class="sxs-lookup"><span data-stu-id="2638c-124">*[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus?mpnId={MpnId}&tenantId={TenantId}</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="2638c-125">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="2638c-125">URI parameters</span></span>

<span data-ttu-id="2638c-126">Deve fornecer um dos dois parâmetros de consulta seguintes para identificar o parceiro.</span><span class="sxs-lookup"><span data-stu-id="2638c-126">You must provide one of the following two query parameters to identify the partner.</span></span> <span data-ttu-id="2638c-127">Se não fornecer um destes dois parâmetros de consulta, receberá um erro de **400 (Mau pedido).**</span><span class="sxs-lookup"><span data-stu-id="2638c-127">If you don't provide one of these two query parameters, you will receive a **400 (Bad request)** error.</span></span>

| <span data-ttu-id="2638c-128">Nome</span><span class="sxs-lookup"><span data-stu-id="2638c-128">Name</span></span> | <span data-ttu-id="2638c-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="2638c-129">Type</span></span> | <span data-ttu-id="2638c-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="2638c-130">Required</span></span> | <span data-ttu-id="2638c-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="2638c-131">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="2638c-132">**MpnId**</span><span class="sxs-lookup"><span data-stu-id="2638c-132">**MpnId**</span></span> | <span data-ttu-id="2638c-133">int</span><span class="sxs-lookup"><span data-stu-id="2638c-133">int</span></span> | <span data-ttu-id="2638c-134">No</span><span class="sxs-lookup"><span data-stu-id="2638c-134">No</span></span> | <span data-ttu-id="2638c-135">Um ID da Rede de Parceiros da Microsoft (PGA/PLA) que identifica o revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="2638c-135">A Microsoft Partner Network ID (PGA/PLA) that identifies the indirect reseller.</span></span> |
| <span data-ttu-id="2638c-136">**TenantId**</span><span class="sxs-lookup"><span data-stu-id="2638c-136">**TenantId**</span></span> | <span data-ttu-id="2638c-137">GUID</span><span class="sxs-lookup"><span data-stu-id="2638c-137">GUID</span></span> | <span data-ttu-id="2638c-138">No</span><span class="sxs-lookup"><span data-stu-id="2638c-138">No</span></span> | <span data-ttu-id="2638c-139">Um ID da Microsoft que identifica a conta CSP do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="2638c-139">A Microsoft ID that identifies the CSP account of the indirect reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2638c-140">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2638c-140">Request headers</span></span>

<span data-ttu-id="2638c-141">Para mais informações, consulte [Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2638c-141">For more information, see [Partner Center REST](headers.md).</span></span>

### <a name="request-examples"></a><span data-ttu-id="2638c-142">Solicitar exemplos</span><span class="sxs-lookup"><span data-stu-id="2638c-142">Request examples</span></span>

#### <a name="request-using-mpn-id-pgapla"></a><span data-ttu-id="2638c-143">Pedido de utilização de ID MPN (PGA/PLA)</span><span class="sxs-lookup"><span data-stu-id="2638c-143">Request using MPN ID (PGA/PLA)</span></span>

<span data-ttu-id="2638c-144">O seguinte pedido de exemplo obtém o estatuto de assinatura do Acordo de Parceiros microsoft do revendedor indireto usando o ID da Rede de Parceiros microsoft do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="2638c-144">The following example request gets the indirect reseller's Microsoft Partner Agreement signing status using the indirect reseller's Microsoft Partner Network ID.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?mpnid=1234567 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

#### <a name="request-using-csp-tenant-id"></a><span data-ttu-id="2638c-145">Pedido de utilização de ID do inquilino da CSP</span><span class="sxs-lookup"><span data-stu-id="2638c-145">Request using CSP tenant ID</span></span>

<span data-ttu-id="2638c-146">O seguinte pedido de exemplo obtém o estatuto de assinatura do Acordo de Parceiros da Microsoft do revendedor indireto usando o ID do inquilino CSP do revendedor indireto (Microsoft ID).</span><span class="sxs-lookup"><span data-stu-id="2638c-146">The following example request gets the indirect reseller's Microsoft Partner Agreement signing status using the indirect reseller's CSP tenant ID (Microsoft ID).</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?tenantId=a2898e3a-06ca-454e-a0d0-c73b0ee36bba HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="2638c-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2638c-147">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2638c-148">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2638c-148">Response success and error codes</span></span>

<span data-ttu-id="2638c-149">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2638c-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2638c-150">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2638c-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2638c-151">Para obter a lista completa, consulte o [erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2638c-151">For the full list, see [Partner Center REST error](error-codes.md).</span></span>

### <a name="response-example-success"></a><span data-ttu-id="2638c-152">Exemplo de resposta (sucesso)</span><span class="sxs-lookup"><span data-stu-id="2638c-152">Response example (success)</span></span>

<span data-ttu-id="2638c-153">A resposta de exemplo a seguir retorna com sucesso se o revendedor indireto assinou o Acordo de Parceiro da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2638c-153">The following example response successfully returns whether the indirect reseller has signed the Microsoft Partner Agreement.</span></span>

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

### <a name="response-examples-failure"></a><span data-ttu-id="2638c-154">Exemplos de resposta (falha)</span><span class="sxs-lookup"><span data-stu-id="2638c-154">Response examples (failure)</span></span>

<span data-ttu-id="2638c-155">Pode receber respostas semelhantes aos seguintes exemplos quando o estado de assinatura do Acordo de Parceiro microsoft do revendedor indireto não puder ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="2638c-155">You may receive responses similar to the following examples when the signing status of the indirect reseller's Microsoft Partner Agreement can't be returned.</span></span>

#### <a name="non-guid-formatted-csp-tenant-id"></a><span data-ttu-id="2638c-156">ID de inquilino csp não-GUID formatado</span><span class="sxs-lookup"><span data-stu-id="2638c-156">Non-GUID formatted CSP tenant ID</span></span>

<span data-ttu-id="2638c-157">A resposta de exemplo a seguir é devolvida quando o ID do inquilino do CSP que passou para a API não é um GUID.</span><span class="sxs-lookup"><span data-stu-id="2638c-157">The following example response is returned when the CSP tenant ID that you passed to the API isn't a GUID.</span></span>

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

#### <a name="non-numeric-mpn-id"></a><span data-ttu-id="2638c-158">ID de MPN não-numérico</span><span class="sxs-lookup"><span data-stu-id="2638c-158">Non-numeric MPN ID</span></span>

<span data-ttu-id="2638c-159">A resposta de exemplo a seguir é devolvida quando o ID MPN (PGA/PLA) que passou para a API não é numérico.</span><span class="sxs-lookup"><span data-stu-id="2638c-159">The following example response is returned when the MPN ID (PGA/PLA) that you passed to the API is non-numeric.</span></span>

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

#### <a name="no-mpn-id-or-csp-tenant-id"></a><span data-ttu-id="2638c-160">Sem ID MPN ou ID de inquilino CSP</span><span class="sxs-lookup"><span data-stu-id="2638c-160">No MPN ID or CSP tenant ID</span></span>

<span data-ttu-id="2638c-161">A resposta de exemplo a seguir é devolvida quando ainda não passou um ID de MPN (PGA/PLA) ou ID do inquilino CSP à API.</span><span class="sxs-lookup"><span data-stu-id="2638c-161">The following example response is returned when you haven't passed an MPN ID (PGA/PLA) or CSP tenant ID to the API.</span></span> <span data-ttu-id="2638c-162">Deve passar um dos dois tipos de identificação para a API.</span><span class="sxs-lookup"><span data-stu-id="2638c-162">You must pass one of the two ID types to the API.</span></span>

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

#### <a name="both-mpn-id-and-csp-tenant-id-passed"></a><span data-ttu-id="2638c-163">Tanto MPN ID como CSP inquilino ID passou</span><span class="sxs-lookup"><span data-stu-id="2638c-163">Both MPN ID and CSP tenant ID passed</span></span>

<span data-ttu-id="2638c-164">A resposta de exemplo a seguir é devolvida quando passa o ID mpn (PGA/PLA) e o ID do inquilino da CSP para a API.</span><span class="sxs-lookup"><span data-stu-id="2638c-164">The following example response is returned when you pass both the MPN ID (PGA/PLA) and CSP tenant ID to the API.</span></span> <span data-ttu-id="2638c-165">Deve passar *apenas um* dos dois tipos de identificador para a API.</span><span class="sxs-lookup"><span data-stu-id="2638c-165">You must pass *only one* of the two identifier types to the API.</span></span>

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

#### <a name="csp-indirect-reseller-mpn-id-pgapla-is-either-invalid-or-not-migrated-from-partner-membership-center-to-partner-center"></a><span data-ttu-id="2638c-166">CSP Reseller Indirect MPN ID (PGA/PLA) é inválido ou não migrado do Centro de Membros de Parceiros para Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="2638c-166">CSP Indirect Reseller MPN ID (PGA/PLA) is either invalid or not migrated from Partner Membership Center to Partner Center</span></span>

<span data-ttu-id="2638c-167">A resposta de exemplo a seguir é devolvida quando o revendedor indireto MPN ID (PGA/PLA) passou ou é inválido ou não é migrado do Centro de Membros do Parceiro para o Partner Center.</span><span class="sxs-lookup"><span data-stu-id="2638c-167">The following example response is returned when Indirect reseller MPN ID (PGA/PLA) passed is either invalid or it is not migrated from Partner Membership Center to Partner Center.</span></span> [<span data-ttu-id="2638c-168">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="2638c-168">Learn More</span></span>](https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx)

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

#### <a name="csp-indirect-provider-region-and-csp-indirect-reseller-region-does-not-match"></a><span data-ttu-id="2638c-169">Região de Fornecedor Indireto CSP e região de Revendedor Indireto CSP não correspondem</span><span class="sxs-lookup"><span data-stu-id="2638c-169">CSP Indirect Provider region and CSP Indirect Reseller region does not match</span></span>

<span data-ttu-id="2638c-170">A resposta de exemplo a seguir é devolvida quando a região do revendedor indireto MPN ID (PGA/PLA) não corresponde à região do Fornecedor Indireto.</span><span class="sxs-lookup"><span data-stu-id="2638c-170">The following example response is returned when region of Indirect reseller MPN ID (PGA/PLA) doesn't match with region of the Indirect Provider.</span></span> <span data-ttu-id="2638c-171">[Saiba mais](/partner-center/mpa-indirect-provider-faq) sobre as Regiões da CSP.</span><span class="sxs-lookup"><span data-stu-id="2638c-171">[Learn more](/partner-center/mpa-indirect-provider-faq) about CSP Regions.</span></span>

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

#### <a name="csp-indirect-reseller-account-exists-in-partner-center-but-hasnt-signed-the-mpa"></a><span data-ttu-id="2638c-172">CSP Conta de Revendedor Indireto existe no Partner Center mas não assinou a MPA</span><span class="sxs-lookup"><span data-stu-id="2638c-172">CSP Indirect Reseller account exists in Partner Center but hasn't signed the MPA</span></span>

<span data-ttu-id="2638c-173">A resposta de exemplo a seguir é devolvida quando a conta CSP Indirect Reseller no Partner Center não assinou a MPA.</span><span class="sxs-lookup"><span data-stu-id="2638c-173">The following example response is returned when CSP Indirect Reseller account in Partner Center hasn't signed the MPA.</span></span> [<span data-ttu-id="2638c-174">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="2638c-174">Learn More</span></span>](/partner-center/mpa-indirect-provider-faq)

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

#### <a name="no-csp-indirect-reseller-account-is-associated-with-the-given-mpn-id"></a><span data-ttu-id="2638c-175">Nenhuma conta CSP Reseller Indirect está associada com o ID MPN dado</span><span class="sxs-lookup"><span data-stu-id="2638c-175">No CSP Indirect Reseller account is associated with the given MPN ID</span></span>

<span data-ttu-id="2638c-176">A resposta de exemplo a seguir é devolvida quando o Partner Center pode reconhecer o ID MPN (PGA/PLA) aprovado no pedido, mas não há nenhuma inscrição CSP associada ao ID MPN (PGA/PLA).</span><span class="sxs-lookup"><span data-stu-id="2638c-176">The following example response is returned when Partner Center can recognize the MPN ID (PGA/PLA) passed in the request but there is no CSP enrollment associated to the given MPN ID (PGA/PLA).</span></span> [<span data-ttu-id="2638c-177">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="2638c-177">Learn More</span></span>](/partner-center/mpa-indirect-provider-faq)

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

#### <a name="invalid-tenant-id"></a><span data-ttu-id="2638c-178">ID do inquilino inválido</span><span class="sxs-lookup"><span data-stu-id="2638c-178">Invalid Tenant ID</span></span>

<span data-ttu-id="2638c-179">A resposta de exemplo a seguir é devolvida quando o Partner Center não encontra qualquer conta associada ao ID do Inquilino passado no pedido.</span><span class="sxs-lookup"><span data-stu-id="2638c-179">The following example response is returned when Partner Center doesn't find any account associated to the Tenant ID passed in the request.</span></span>

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

#### <a name="no-mpa-found-with-the-given-tenant-id"></a><span data-ttu-id="2638c-180">Nenhuma MPA encontrada com a iD do inquilino dado</span><span class="sxs-lookup"><span data-stu-id="2638c-180">No MPA found with the given Tenant ID</span></span>

<span data-ttu-id="2638c-181">A resposta de exemplo a seguir é devolvida quando o Partner Center não consegue encontrar qualquer assinatura MPA com o ID do inquilino.</span><span class="sxs-lookup"><span data-stu-id="2638c-181">The following example response is returned when Partner Center can't find any MPA signature with the given Tenant ID.</span></span> [<span data-ttu-id="2638c-182">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="2638c-182">Learn More</span></span>](/partner-center/mpa-indirect-provider-faq)

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