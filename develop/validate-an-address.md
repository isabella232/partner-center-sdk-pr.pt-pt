---
title: Validar um endereço
description: Como validar um endereço utilizando a API de validação de endereços.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2eeca91b0e5a507dac6df4ecf61a56aed2d2d921
ms.sourcegitcommit: 51237e7e98d71a7e0590b4d6a4034b6409542126
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/09/2021
ms.locfileid: "113572085"
---
# <a name="validate-an-address"></a><span data-ttu-id="fb3d5-103">Validar um endereço</span><span class="sxs-lookup"><span data-stu-id="fb3d5-103">Validate an address</span></span>

<span data-ttu-id="fb3d5-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fb3d5-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fb3d5-105">Como validar um endereço utilizando a API de validação de endereços.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-105">How to validate an address using the address validation API.</span></span>

<span data-ttu-id="fb3d5-106">A API de validação de endereços só deve ser utilizada para pré-validação de atualizações de perfis de clientes.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-106">The address validation API should only be used for pre-validation of customer profile updates.</span></span> <span data-ttu-id="fb3d5-107">Use-o com o entendimento de que se o país for os Estados Unidos, Canadá, China ou México, o campo estatal é validado contra uma lista de Estados válidos para o respetivo país.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-107">Use it with the understanding that if the country is the United States, Canada, China, or Mexico, the state field is validated against a list of valid states for the respective country.</span></span> <span data-ttu-id="fb3d5-108">Em todos os outros países, este teste não ocorre, e a API apenas verifica que o Estado é uma cadeia válida.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-108">In all other countries, this test does not occur, and the API only checks that the state is a valid string.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fb3d5-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fb3d5-109">Prerequisites</span></span>

<span data-ttu-id="fb3d5-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fb3d5-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fb3d5-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="fb3d5-112">C\#</span><span class="sxs-lookup"><span data-stu-id="fb3d5-112">C\#</span></span>

<span data-ttu-id="fb3d5-113">Para validar um endereço, primeiro instantaneamente um novo objeto **Address** e povoá-lo com o endereço para validar.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-113">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="fb3d5-114">Em seguida, recupere uma interface para **operações de Validações** a partir da propriedade **IAggregatePartner.Validations,** e ligue para o método **IsAddressValid** com o objeto de endereço.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-114">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.Validations** property, and call the **IsAddressValid** method with the address object.</span></span>

```csharp
IAggregatePartner partnerOperations;

// Create an address to validate.
Address address = new Address()
{
    AddressLine1 = "One Microsoft Way",
    City = "Redmond",
    State = "WA",
    PostalCode = "98052",
    Country = "US"
};

// Validate the address.
AddressValidationResponse result = partnerOperations.Validations.IsAddressValid(address);

// If the request completes successfully, you can inspect the response object.

// See the status of the validation.
Console.WriteLine($"Status: {addressValidationResult.Status}");

// See the validation message returned.
Console.WriteLine($"Validation Message Returned: {addressValidationResult.ValidationMessage ?? "No message returned."}");

// See the original address submitted for validation.
Console.WriteLine($"Original Address:\n{this.DisplayAddress(addressValidationResult.OriginalAddress)}");

// See the suggested addresses returned by the API, if any exist.
Console.WriteLine($"Suggested Addresses Returned: {addressValidationResult.SuggestedAddresses?.Count ?? "None."}");

if (addressValidationResult.SuggestedAddresses != null && addressValidationResult.SuggestedAddresses.Any())
{
    addressValidationResult.SuggestedAddresses.ForEach(a => Console.WriteLine(this.DisplayAddress(a)));
}

// Helper method to pretty-print an Address object.
private string DisplayAddress(Address address)
{
    StringBuilder sb = new StringBuilder();

    foreach (var property in address.GetType().GetProperties())
    {
        sb.AppendLine($"{property.Name}: {property.GetValue(address) ?? "None to Display."}");
    }

    return sb.ToString();
}
```

## <a name="rest-request"></a><span data-ttu-id="fb3d5-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="fb3d5-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fb3d5-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb3d5-116">Request syntax</span></span>

| <span data-ttu-id="fb3d5-117">Método</span><span class="sxs-lookup"><span data-stu-id="fb3d5-117">Method</span></span>   | <span data-ttu-id="fb3d5-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="fb3d5-118">Request URI</span></span>                                                                 |
|----------|-----------------------------------------------------------------------------|
| <span data-ttu-id="fb3d5-119">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="fb3d5-119">**POST**</span></span> | <span data-ttu-id="fb3d5-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/validações/endereço HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fb3d5-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fb3d5-121">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="fb3d5-121">Request headers</span></span>

<span data-ttu-id="fb3d5-122">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="fb3d5-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fb3d5-123">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="fb3d5-123">Request body</span></span>

<span data-ttu-id="fb3d5-124">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-124">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="fb3d5-125">Nome</span><span class="sxs-lookup"><span data-stu-id="fb3d5-125">Name</span></span>         | <span data-ttu-id="fb3d5-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="fb3d5-126">Type</span></span>   | <span data-ttu-id="fb3d5-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="fb3d5-127">Required</span></span> | <span data-ttu-id="fb3d5-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb3d5-128">Description</span></span>                                                |
|--------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="fb3d5-129">linha de endereço1</span><span class="sxs-lookup"><span data-stu-id="fb3d5-129">addressline1</span></span> | <span data-ttu-id="fb3d5-130">string</span><span class="sxs-lookup"><span data-stu-id="fb3d5-130">string</span></span> | <span data-ttu-id="fb3d5-131">Y</span><span class="sxs-lookup"><span data-stu-id="fb3d5-131">Y</span></span>        | <span data-ttu-id="fb3d5-132">A primeira linha do endereço.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-132">The first line of the address.</span></span>                             |
| <span data-ttu-id="fb3d5-133">linha de endereço2</span><span class="sxs-lookup"><span data-stu-id="fb3d5-133">addressline2</span></span> | <span data-ttu-id="fb3d5-134">string</span><span class="sxs-lookup"><span data-stu-id="fb3d5-134">string</span></span> | <span data-ttu-id="fb3d5-135">N</span><span class="sxs-lookup"><span data-stu-id="fb3d5-135">N</span></span>        | <span data-ttu-id="fb3d5-136">A segunda linha do endereço.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-136">The second line of the address.</span></span> <span data-ttu-id="fb3d5-137">Esta propriedade é opcional.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-137">This property is optional.</span></span> |
| <span data-ttu-id="fb3d5-138">city</span><span class="sxs-lookup"><span data-stu-id="fb3d5-138">city</span></span>         | <span data-ttu-id="fb3d5-139">string</span><span class="sxs-lookup"><span data-stu-id="fb3d5-139">string</span></span> | <span data-ttu-id="fb3d5-140">Y</span><span class="sxs-lookup"><span data-stu-id="fb3d5-140">Y</span></span>        | <span data-ttu-id="fb3d5-141">A cidade.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-141">The city.</span></span>                                                  |
| <span data-ttu-id="fb3d5-142">state</span><span class="sxs-lookup"><span data-stu-id="fb3d5-142">state</span></span>        | <span data-ttu-id="fb3d5-143">string</span><span class="sxs-lookup"><span data-stu-id="fb3d5-143">string</span></span> | <span data-ttu-id="fb3d5-144">Y</span><span class="sxs-lookup"><span data-stu-id="fb3d5-144">Y</span></span>        | <span data-ttu-id="fb3d5-145">O Estado.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-145">The state.</span></span>                                                 |
| <span data-ttu-id="fb3d5-146">código postal</span><span class="sxs-lookup"><span data-stu-id="fb3d5-146">postalcode</span></span>   | <span data-ttu-id="fb3d5-147">string</span><span class="sxs-lookup"><span data-stu-id="fb3d5-147">string</span></span> | <span data-ttu-id="fb3d5-148">Y</span><span class="sxs-lookup"><span data-stu-id="fb3d5-148">Y</span></span>        | <span data-ttu-id="fb3d5-149">O código postal.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-149">The postal code.</span></span>                                           |
| <span data-ttu-id="fb3d5-150">país</span><span class="sxs-lookup"><span data-stu-id="fb3d5-150">country</span></span>      | <span data-ttu-id="fb3d5-151">string</span><span class="sxs-lookup"><span data-stu-id="fb3d5-151">string</span></span> | <span data-ttu-id="fb3d5-152">Y</span><span class="sxs-lookup"><span data-stu-id="fb3d5-152">Y</span></span>        | <span data-ttu-id="fb3d5-153">O código de campo ISO alpha-2 de dois caracteres.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-153">The two-character ISO alpha-2 country code.</span></span>                |

### <a name="response-details"></a><span data-ttu-id="fb3d5-154">Detalhes da resposta</span><span class="sxs-lookup"><span data-stu-id="fb3d5-154">Response details</span></span>

<span data-ttu-id="fb3d5-155">A resposta devolverá uma das seguintes mensagens de estado:</span><span class="sxs-lookup"><span data-stu-id="fb3d5-155">The response will return one of the following status messages:</span></span>

| <span data-ttu-id="fb3d5-156">Estado</span><span class="sxs-lookup"><span data-stu-id="fb3d5-156">Status</span></span>     | <span data-ttu-id="fb3d5-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb3d5-157">Description</span></span> |    <span data-ttu-id="fb3d5-158">Número de endereços sugeridos devolvidos</span><span class="sxs-lookup"><span data-stu-id="fb3d5-158">Number of suggested addresses returned</span></span> |
|-------|---------------|-------------------|
|<span data-ttu-id="fb3d5-159">Envio verificado</span><span class="sxs-lookup"><span data-stu-id="fb3d5-159">Verified shippable</span></span> | <span data-ttu-id="fb3d5-160">O endereço é verificado e pode ser enviado para.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-160">Address is verified and can be shipped to.</span></span> | <span data-ttu-id="fb3d5-161">Único</span><span class="sxs-lookup"><span data-stu-id="fb3d5-161">Single</span></span> |
|<span data-ttu-id="fb3d5-162">Verificado</span><span class="sxs-lookup"><span data-stu-id="fb3d5-162">Verified</span></span> | <span data-ttu-id="fb3d5-163">O endereço está verificado.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-163">Address is verified.</span></span> | <span data-ttu-id="fb3d5-164">Único</span><span class="sxs-lookup"><span data-stu-id="fb3d5-164">Single</span></span> |
|<span data-ttu-id="fb3d5-165">Interação necessária</span><span class="sxs-lookup"><span data-stu-id="fb3d5-165">Interaction required</span></span> | <span data-ttu-id="fb3d5-166">O endereço sugerido foi alterado significativamente e precisa de confirmação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-166">Suggested address has been changed significantly and needs user confirmation.</span></span> | <span data-ttu-id="fb3d5-167">Único</span><span class="sxs-lookup"><span data-stu-id="fb3d5-167">Single</span></span> |
|<span data-ttu-id="fb3d5-168">Parcial de rua</span><span class="sxs-lookup"><span data-stu-id="fb3d5-168">Street partial</span></span> | <span data-ttu-id="fb3d5-169">A rua dada no endereço é parcial e precisa de mais informações.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-169">The given street in the address is partial and needs more info.</span></span> | <span data-ttu-id="fb3d5-170">Múltiplos — máximo de três</span><span class="sxs-lookup"><span data-stu-id="fb3d5-170">Multiple—maximum of three</span></span> |
|<span data-ttu-id="fb3d5-171">Instalações parciais</span><span class="sxs-lookup"><span data-stu-id="fb3d5-171">Premises partial</span></span> | <span data-ttu-id="fb3d5-172">As instalações dadas (número de edifício, número de suite, entre outras) são parciais e precisam de mais informações.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-172">The given premises (building number, suite number, and others) are partial and need more info.</span></span> | <span data-ttu-id="fb3d5-173">Múltiplos — máximo de três</span><span class="sxs-lookup"><span data-stu-id="fb3d5-173">Multiple—maximum of three</span></span> |
|<span data-ttu-id="fb3d5-174">Vários</span><span class="sxs-lookup"><span data-stu-id="fb3d5-174">Multiple</span></span> | <span data-ttu-id="fb3d5-175">Existem vários campos que são parciais no endereço (potencialmente também incluindo a parcial da rua e as instalações parciais).</span><span class="sxs-lookup"><span data-stu-id="fb3d5-175">There are multiple fields that are partial in the address (potentially also including street partial and premises partial).</span></span> | <span data-ttu-id="fb3d5-176">Múltiplos — máximo de três</span><span class="sxs-lookup"><span data-stu-id="fb3d5-176">Multiple—maximum of three</span></span> |
|<span data-ttu-id="fb3d5-177">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="fb3d5-177">None</span></span> | <span data-ttu-id="fb3d5-178">O endereço está incorreto.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-178">Address is incorrect.</span></span> | <span data-ttu-id="fb3d5-179">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="fb3d5-179">None</span></span> |
|<span data-ttu-id="fb3d5-180">Não validado</span><span class="sxs-lookup"><span data-stu-id="fb3d5-180">Not validated</span></span> | <span data-ttu-id="fb3d5-181">O endereço não pôde ser enviado através do processo de validação.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-181">Address was not able to be sent through the validation process.</span></span> | <span data-ttu-id="fb3d5-182">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="fb3d5-182">None</span></span> |

### <a name="request-example"></a><span data-ttu-id="fb3d5-183">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="fb3d5-183">Request example</span></span>

```http
# "VerifiedShippable" Request Example

POST https://api.partnercenter.microsoft.com/v1/validations/address HTTP/1.1
Accept: application/json
Content-Type: application/json
Authorization: Bearer <token>
MS-CorrelationId: 29624f3c-90cb-4d34-a7e9-bd2de6d35218
MS-RequestId: eb55c2b8-6f4b-4b44-9557-f76df624b8c0
Host: api.partnercenter.microsoft.com
Content-Length: 137
X-Locale: en-US

{
    "AddressLine1": "1 Microsoft Way",
    "City": "Redmond",
    "State": "WA",
    "PostalCode": "98052",
    "Country": "US"
}

# "StreetPartial" Request Example

POST https://api.partnercenter.microsoft.com/v1/validations/address HTTP/1.1
Accept: application/json
Content-Type: application/json
Authorization: Bearer <token>
MS-CorrelationId: 2c95c9bc-fdfb-4c6a-84f4-57c9b0826b43
MS-RequestId: ee6cf74c-3ab5-48d6-9269-4a4b75bd59dc
Host: api.partnercenter.microsoft.com
Content-Length: 135
X-Locale: en-US

{
    "AddressLine1": "Microsoft Way",
    "City": "Redmond",
    "State": "WA",
    "PostalCode": "98052",
    "Country": "US"
}
```

## <a name="rest-response"></a><span data-ttu-id="fb3d5-184">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="fb3d5-184">REST response</span></span>

<span data-ttu-id="fb3d5-185">Se for bem sucedido, o método devolve um objeto **AddressValidationResponse** no organismo de resposta, com um código de estado **HTTP 200.**</span><span class="sxs-lookup"><span data-stu-id="fb3d5-185">If successful, the method returns an **AddressValidationResponse** object in the response body, with a **HTTP 200** status code.</span></span> <span data-ttu-id="fb3d5-186">Apresentamos um exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-186">An example is shown below.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fb3d5-187">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="fb3d5-187">Response success and error codes</span></span>

<span data-ttu-id="fb3d5-188">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-188">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fb3d5-189">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="fb3d5-189">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fb3d5-190">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="fb3d5-190">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fb3d5-191">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="fb3d5-191">Response example</span></span>

```http
# "VerifiedShippable" Response Example

HTTP/1.1 200 OK
Date: Mon, 17 May 2021 23:19:19 GMT
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 29624f3c-90cb-4d34-a7e9-bd2de6d35218
MS-RequestId: eb55c2b8-6f4b-4b44-9557-f76df624b8c0
X-Locale: en-US
 
{
    "originalAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "1 Microsoft Way",
        "postalCode": "98052"
    },
    "suggestedAddresses": [
        {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "1 Microsoft Way",
            "postalCode": "98052-8300"
        }
    ],
    "status": "VerifiedShippable"
}

# "StreetPartial" Response Example

HTTP/1.1 200 OK
Date: Mon, 17 May 2021 23:34:08 GMT
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 2c95c9bc-fdfb-4c6a-84f4-57c9b0826b43
MS-RequestId: ee6cf74c-3ab5-48d6-9269-4a4b75bd59dc
X-Locale: en-US
 
{
    "originalAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "Microsoft Way",
        "postalCode": "98052"
    },
    "suggestedAddresses": [
        {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "1 Microsoft Way",
            "postalCode": "98052-6399"
        }
    ],
    "status": "StreetPartial",
    "validationMessage": "Address field invalid for property: 'Region', 'PostalCode', 'City'"
}
```
