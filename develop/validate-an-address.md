---
title: Validar um endereço
description: Como validar um endereço utilizando a API de validação de endereços.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 14d45977f3af6e8bba1b7cb7f969aa7c5bb671da
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529890"
---
# <a name="validate-an-address"></a><span data-ttu-id="ea1fe-103">Validar um endereço</span><span class="sxs-lookup"><span data-stu-id="ea1fe-103">Validate an address</span></span>

<span data-ttu-id="ea1fe-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ea1fe-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ea1fe-105">Como validar um endereço utilizando a API de validação de endereços.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-105">How to validate an address using the address validation API.</span></span>

<span data-ttu-id="ea1fe-106">A API de validação de endereços só deve ser utilizada para pré-validação de atualizações de perfis de clientes.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-106">The address validation API should only be used for pre-validation of customer profile updates.</span></span> <span data-ttu-id="ea1fe-107">Use-o com o entendimento de que se o país for os Estados Unidos, Canadá, China ou México, o campo estatal é validado contra uma lista de Estados válidos para o respetivo país.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-107">Use it with the understanding that if the country is the United States, Canada, China, or Mexico, the state field is validated against a list of valid states for the respective country.</span></span> <span data-ttu-id="ea1fe-108">Em todos os outros países, este teste não ocorre, e a API apenas verifica que o Estado é uma cadeia válida.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-108">In all other countries, this test does not occur, and the API only checks that the state is a valid string.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea1fe-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ea1fe-109">Prerequisites</span></span>

<span data-ttu-id="ea1fe-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ea1fe-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ea1fe-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="ea1fe-112">C\#</span><span class="sxs-lookup"><span data-stu-id="ea1fe-112">C\#</span></span>

<span data-ttu-id="ea1fe-113">Para validar um endereço, primeiro instantaneamente um novo objeto **Address** e povoá-lo com o endereço para validar.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-113">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="ea1fe-114">Em seguida, recupere uma interface para **operações de Validações** a partir da propriedade **IAggregatePartner.Validations,** e ligue para o método **IsAddressValid** com o objeto de endereço.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-114">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.Validations** property, and call the **IsAddressValid** method with the address object.</span></span>

```csharp
// IAggregatePartner partnerOperations;

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
bool result = partnerOperations.Validations.IsAddressValid(address);

// If the address is valid, the result should equal true.
Console.WriteLine("Result: " + result.ToString());

// The following is an example that causes address validation to fail.
try
{
    // Change to an invalid postal code for this address.
    address.PostalCode = "98007";

    // Validate the address.
    result = partnerOperations.Validations.IsAddressValid(address);

    Console.WriteLine("ERROR: The code should have thrown an exception - BadRequest(400).");
}
catch (PartnerException exception)
{
    if (exception.ErrorCategory == PartnerErrorCategory.BadInput)
    {
        Console.WriteLine(exception.ErrorCategory.ToString());
        Console.WriteLine("Exception:");
        Console.WriteLine("Message: {0}", exception.Message);
    }
    else
    {
        throw;
    }
}
```

## <a name="java"></a><span data-ttu-id="ea1fe-115">Java</span><span class="sxs-lookup"><span data-stu-id="ea1fe-115">Java</span></span>

<span data-ttu-id="ea1fe-116">Para validar um endereço, primeiro instantaneamente um novo objeto **Address** e povoá-lo com o endereço para validar.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-116">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="ea1fe-117">Em seguida, recupere uma interface para operações de **Validações** a partir da função **IAggregatePartner.getValidations** e ligue para o método **isAddressValid** com o objeto de endereço.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-117">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.getValidations** function, and call the **isAddressValid** method with the address object.</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

```java
// IAggregatePartner partnerOperations;

// Create an address to validate.
Address address = new Address();

address.setAddressLine1("One Microsoft Way");
address.setCity("Redmond");
address.setState("WA");
address.setCountry("US");
address.setPostalCode("98052");

try
{
    // Validate the address
    Boolean validationResult = partnerOperations.getValidations().isAddressValid(address);

    System.out.println(validationResult ? "The address is valid." : "Invalid address");
}
catch (Exception exception)
{
    System.out.println("Address is invalid");

    if (! StringHelper.isNullOrWhiteSpace(exception.getMessage()))
    {
        System.out.println(exception.getMessage());
    }
}
```

## <a name="powershell"></a><span data-ttu-id="ea1fe-118">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea1fe-118">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="ea1fe-119">Para validar um endereço, execute o [**Test-PartnerAddress**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) com os parâmetros de endereço povoados.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-119">To validate an address, execute the [**Test-PartnerAddress**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) with the address parameters populated.</span></span>

```powershell
Test-PartnerAddress -AddressLine1 '700 Bellevue Way NE' -City 'Bellevue' -Country 'US' -PostalCode '98004' -State 'WA'
```

## <a name="rest-request"></a><span data-ttu-id="ea1fe-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="ea1fe-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ea1fe-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea1fe-121">Request syntax</span></span>

| <span data-ttu-id="ea1fe-122">Método</span><span class="sxs-lookup"><span data-stu-id="ea1fe-122">Method</span></span>   | <span data-ttu-id="ea1fe-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="ea1fe-123">Request URI</span></span>                                                                 |
|----------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ea1fe-124">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="ea1fe-124">**POST**</span></span> | <span data-ttu-id="ea1fe-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/validações/endereço HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ea1fe-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ea1fe-126">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="ea1fe-126">Request headers</span></span>

<span data-ttu-id="ea1fe-127">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ea1fe-127">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ea1fe-128">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="ea1fe-128">Request body</span></span>

<span data-ttu-id="ea1fe-129">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-129">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="ea1fe-130">Nome</span><span class="sxs-lookup"><span data-stu-id="ea1fe-130">Name</span></span>         | <span data-ttu-id="ea1fe-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="ea1fe-131">Type</span></span>   | <span data-ttu-id="ea1fe-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="ea1fe-132">Required</span></span> | <span data-ttu-id="ea1fe-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea1fe-133">Description</span></span>                                                |
|--------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="ea1fe-134">linha de endereço1</span><span class="sxs-lookup"><span data-stu-id="ea1fe-134">addressline1</span></span> | <span data-ttu-id="ea1fe-135">string</span><span class="sxs-lookup"><span data-stu-id="ea1fe-135">string</span></span> | <span data-ttu-id="ea1fe-136">Y</span><span class="sxs-lookup"><span data-stu-id="ea1fe-136">Y</span></span>        | <span data-ttu-id="ea1fe-137">A primeira linha do endereço.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-137">The first line of the address.</span></span>                             |
| <span data-ttu-id="ea1fe-138">linha de endereço2</span><span class="sxs-lookup"><span data-stu-id="ea1fe-138">addressline2</span></span> | <span data-ttu-id="ea1fe-139">string</span><span class="sxs-lookup"><span data-stu-id="ea1fe-139">string</span></span> | <span data-ttu-id="ea1fe-140">N</span><span class="sxs-lookup"><span data-stu-id="ea1fe-140">N</span></span>        | <span data-ttu-id="ea1fe-141">A segunda linha do endereço.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-141">The second line of the address.</span></span> <span data-ttu-id="ea1fe-142">Esta propriedade é opcional.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-142">This property is optional.</span></span> |
| <span data-ttu-id="ea1fe-143">city</span><span class="sxs-lookup"><span data-stu-id="ea1fe-143">city</span></span>         | <span data-ttu-id="ea1fe-144">string</span><span class="sxs-lookup"><span data-stu-id="ea1fe-144">string</span></span> | <span data-ttu-id="ea1fe-145">Y</span><span class="sxs-lookup"><span data-stu-id="ea1fe-145">Y</span></span>        | <span data-ttu-id="ea1fe-146">A cidade.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-146">The city.</span></span>                                                  |
| <span data-ttu-id="ea1fe-147">state</span><span class="sxs-lookup"><span data-stu-id="ea1fe-147">state</span></span>        | <span data-ttu-id="ea1fe-148">string</span><span class="sxs-lookup"><span data-stu-id="ea1fe-148">string</span></span> | <span data-ttu-id="ea1fe-149">Y</span><span class="sxs-lookup"><span data-stu-id="ea1fe-149">Y</span></span>        | <span data-ttu-id="ea1fe-150">O Estado.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-150">The state.</span></span>                                                 |
| <span data-ttu-id="ea1fe-151">código postal</span><span class="sxs-lookup"><span data-stu-id="ea1fe-151">postalcode</span></span>   | <span data-ttu-id="ea1fe-152">string</span><span class="sxs-lookup"><span data-stu-id="ea1fe-152">string</span></span> | <span data-ttu-id="ea1fe-153">Y</span><span class="sxs-lookup"><span data-stu-id="ea1fe-153">Y</span></span>        | <span data-ttu-id="ea1fe-154">O código postal.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-154">The postal code.</span></span>                                           |
| <span data-ttu-id="ea1fe-155">país</span><span class="sxs-lookup"><span data-stu-id="ea1fe-155">country</span></span>      | <span data-ttu-id="ea1fe-156">string</span><span class="sxs-lookup"><span data-stu-id="ea1fe-156">string</span></span> | <span data-ttu-id="ea1fe-157">Y</span><span class="sxs-lookup"><span data-stu-id="ea1fe-157">Y</span></span>        | <span data-ttu-id="ea1fe-158">O código de campo ISO alpha-2 de dois caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-158">The two-character ISO alpha-2 country code.</span></span>                |

### <a name="request-example"></a><span data-ttu-id="ea1fe-159">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="ea1fe-159">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/validations/address HTTP/1.1
Content-Type: application/json
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 129

{
    "AddressLine1": "One Microsoft Way",
    "City": "Redmond",
    "State": "WA",
    "PostalCode": "98052",
    "Country": "US"
}
```

## <a name="rest-response"></a><span data-ttu-id="ea1fe-160">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="ea1fe-160">REST response</span></span>

<span data-ttu-id="ea1fe-161">Se for bem sucedido, o método devolve um código de estado 200, como demonstrado na Resposta - exemplo de validação bem sucedido mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-161">If successful, the method returns a status code 200 as demonstrated in the Response - validation succeeded example shown below.</span></span>

<span data-ttu-id="ea1fe-162">Se o pedido falhar, o método devolve um código de estado 400, como demonstrado na Resposta - exemplo falhado de validação apresentado abaixo.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-162">If the request fails, the method returns a status code 400 as demonstrated in the Response - validation failed example shown below.</span></span> <span data-ttu-id="ea1fe-163">O corpo de resposta contém uma carga útil JSON com informações adicionais sobre o erro.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-163">The response body contains a JSON payload with additional information about the error.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ea1fe-164">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="ea1fe-164">Response success and error codes</span></span>

<span data-ttu-id="ea1fe-165">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-165">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ea1fe-166">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="ea1fe-166">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ea1fe-167">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="ea1fe-167">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response---validation-succeeded-example"></a><span data-ttu-id="ea1fe-168">Resposta - validação sucedeu exemplo</span><span class="sxs-lookup"><span data-stu-id="ea1fe-168">Response - validation succeeded example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CV: IqhjoWVyq0Kl81dO.0
MS-ServerId: 030011719
Date: Mon, 13 Mar 2017 23:56:12 GMT
```

### <a name="response---validation-failed-example"></a><span data-ttu-id="ea1fe-169">Resposta - exemplo falhado de validação</span><span class="sxs-lookup"><span data-stu-id="ea1fe-169">Response - validation failed example</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 418
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CV: pdlItMyvtkmGHDWt.0
MS-ServerId: 101112012
Date: Tue, 14 Mar 2017 01:57:55 GMT

{
    "code": 2007,
    "description": "{\"code\":\"60071\",\"reason\":\"ZipCityInvalid - Details: Field - &#39;City&#39; is corrected from OldValue: &#39;Redmond&#39; to NewValue: &#39;BELLEVUE&#39;.\",\"corrected_address\":{\"country\":\"US\",\"region\":\"WA\",\"city\":\"BELLEVUE\",\"address_line1\":\"One Microsoft Way\",\"postal_code\":\"98007\"},\"object_type\":\"AddressValidation\",\"resource_status\":\"Active\"}",
    "data": [],
    "source": "PartnerFD"
}
```
