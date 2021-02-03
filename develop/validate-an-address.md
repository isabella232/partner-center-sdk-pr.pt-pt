---
title: Validar um endereço
description: Como validar um endereço utilizando a API de validação de endereços.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 22d5faec2fdab4907067bb01cb74e110032dea9a
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768930"
---
# <a name="validate-an-address"></a><span data-ttu-id="1df6a-103">Validar um endereço</span><span class="sxs-lookup"><span data-stu-id="1df6a-103">Validate an address</span></span>

<span data-ttu-id="1df6a-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="1df6a-104">**Applies To**</span></span>

- <span data-ttu-id="1df6a-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="1df6a-105">Partner Center</span></span>
- <span data-ttu-id="1df6a-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="1df6a-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="1df6a-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="1df6a-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="1df6a-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1df6a-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1df6a-109">Como validar um endereço utilizando a API de validação de endereços.</span><span class="sxs-lookup"><span data-stu-id="1df6a-109">How to validate an address using the address validation API.</span></span>

<span data-ttu-id="1df6a-110">A API de validação de endereços só deve ser utilizada para pré-validação de atualizações de perfis de clientes.</span><span class="sxs-lookup"><span data-stu-id="1df6a-110">The address validation API should only be used for pre-validation of customer profile updates.</span></span> <span data-ttu-id="1df6a-111">Use-o com o entendimento de que se o país for os Estados Unidos, Canadá, China ou México, o campo estatal é validado contra uma lista de Estados válidos para o respetivo país.</span><span class="sxs-lookup"><span data-stu-id="1df6a-111">Use it with the understanding that if the country is the United States, Canada, China, or Mexico, the state field is validated against a list of valid states for the respective country.</span></span> <span data-ttu-id="1df6a-112">Em todos os outros países, este teste não ocorre, e a API apenas verifica que o Estado é uma cadeia válida.</span><span class="sxs-lookup"><span data-stu-id="1df6a-112">In all other countries, this test does not occur, and the API only checks that the state is a valid string.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1df6a-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1df6a-113">Prerequisites</span></span>

<span data-ttu-id="1df6a-114">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1df6a-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1df6a-115">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="1df6a-115">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="1df6a-116">C\#</span><span class="sxs-lookup"><span data-stu-id="1df6a-116">C\#</span></span>

<span data-ttu-id="1df6a-117">Para validar um endereço, primeiro instantaneamente um novo objeto **Address** e povoá-lo com o endereço para validar.</span><span class="sxs-lookup"><span data-stu-id="1df6a-117">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="1df6a-118">Em seguida, recupere uma interface para **operações de Validações** a partir da propriedade **IAggregatePartner.Validations,** e ligue para o método **IsAddressValid** com o objeto de endereço.</span><span class="sxs-lookup"><span data-stu-id="1df6a-118">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.Validations** property, and call the **IsAddressValid** method with the address object.</span></span>

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

## <a name="java"></a><span data-ttu-id="1df6a-119">Java</span><span class="sxs-lookup"><span data-stu-id="1df6a-119">Java</span></span>

<span data-ttu-id="1df6a-120">Para validar um endereço, primeiro instantaneamente um novo objeto **Address** e povoá-lo com o endereço para validar.</span><span class="sxs-lookup"><span data-stu-id="1df6a-120">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="1df6a-121">Em seguida, recupere uma interface para operações de **Validações** a partir da função **IAggregatePartner.getValidations** e ligue para o método **isAddressValid** com o objeto de endereço.</span><span class="sxs-lookup"><span data-stu-id="1df6a-121">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.getValidations** function, and call the **isAddressValid** method with the address object.</span></span>

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

## <a name="powershell"></a><span data-ttu-id="1df6a-122">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1df6a-122">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="1df6a-123">Para validar um endereço, execute o [**Test-PartnerAddress**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) com os parâmetros de endereço povoados.</span><span class="sxs-lookup"><span data-stu-id="1df6a-123">To validate an address, execute the [**Test-PartnerAddress**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) with the address parameters populated.</span></span>

```powershell
Test-PartnerAddress -AddressLine1 '700 Bellevue Way NE' -City 'Bellevue' -Country 'US' -PostalCode '98004' -State 'WA'
```

## <a name="rest-request"></a><span data-ttu-id="1df6a-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="1df6a-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1df6a-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="1df6a-125">Request syntax</span></span>

| <span data-ttu-id="1df6a-126">Método</span><span class="sxs-lookup"><span data-stu-id="1df6a-126">Method</span></span>   | <span data-ttu-id="1df6a-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="1df6a-127">Request URI</span></span>                                                                 |
|----------|-----------------------------------------------------------------------------|
| <span data-ttu-id="1df6a-128">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="1df6a-128">**POST**</span></span> | <span data-ttu-id="1df6a-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/validações/endereço HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1df6a-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1df6a-130">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="1df6a-130">Request headers</span></span>

<span data-ttu-id="1df6a-131">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1df6a-131">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1df6a-132">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="1df6a-132">Request body</span></span>

<span data-ttu-id="1df6a-133">Esta tabela descreve as propriedades necessárias no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="1df6a-133">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="1df6a-134">Nome</span><span class="sxs-lookup"><span data-stu-id="1df6a-134">Name</span></span>         | <span data-ttu-id="1df6a-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="1df6a-135">Type</span></span>   | <span data-ttu-id="1df6a-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="1df6a-136">Required</span></span> | <span data-ttu-id="1df6a-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="1df6a-137">Description</span></span>                                                |
|--------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="1df6a-138">linha de endereço1</span><span class="sxs-lookup"><span data-stu-id="1df6a-138">addressline1</span></span> | <span data-ttu-id="1df6a-139">string</span><span class="sxs-lookup"><span data-stu-id="1df6a-139">string</span></span> | <span data-ttu-id="1df6a-140">Y</span><span class="sxs-lookup"><span data-stu-id="1df6a-140">Y</span></span>        | <span data-ttu-id="1df6a-141">A primeira linha do endereço.</span><span class="sxs-lookup"><span data-stu-id="1df6a-141">The first line of the address.</span></span>                             |
| <span data-ttu-id="1df6a-142">linha de endereço2</span><span class="sxs-lookup"><span data-stu-id="1df6a-142">addressline2</span></span> | <span data-ttu-id="1df6a-143">string</span><span class="sxs-lookup"><span data-stu-id="1df6a-143">string</span></span> | <span data-ttu-id="1df6a-144">N</span><span class="sxs-lookup"><span data-stu-id="1df6a-144">N</span></span>        | <span data-ttu-id="1df6a-145">A segunda linha do endereço.</span><span class="sxs-lookup"><span data-stu-id="1df6a-145">The second line of the address.</span></span> <span data-ttu-id="1df6a-146">Esta propriedade é opcional.</span><span class="sxs-lookup"><span data-stu-id="1df6a-146">This property is optional.</span></span> |
| <span data-ttu-id="1df6a-147">city</span><span class="sxs-lookup"><span data-stu-id="1df6a-147">city</span></span>         | <span data-ttu-id="1df6a-148">string</span><span class="sxs-lookup"><span data-stu-id="1df6a-148">string</span></span> | <span data-ttu-id="1df6a-149">Y</span><span class="sxs-lookup"><span data-stu-id="1df6a-149">Y</span></span>        | <span data-ttu-id="1df6a-150">A cidade.</span><span class="sxs-lookup"><span data-stu-id="1df6a-150">The city.</span></span>                                                  |
| <span data-ttu-id="1df6a-151">state</span><span class="sxs-lookup"><span data-stu-id="1df6a-151">state</span></span>        | <span data-ttu-id="1df6a-152">string</span><span class="sxs-lookup"><span data-stu-id="1df6a-152">string</span></span> | <span data-ttu-id="1df6a-153">Y</span><span class="sxs-lookup"><span data-stu-id="1df6a-153">Y</span></span>        | <span data-ttu-id="1df6a-154">O Estado.</span><span class="sxs-lookup"><span data-stu-id="1df6a-154">The state.</span></span>                                                 |
| <span data-ttu-id="1df6a-155">código postal</span><span class="sxs-lookup"><span data-stu-id="1df6a-155">postalcode</span></span>   | <span data-ttu-id="1df6a-156">string</span><span class="sxs-lookup"><span data-stu-id="1df6a-156">string</span></span> | <span data-ttu-id="1df6a-157">Y</span><span class="sxs-lookup"><span data-stu-id="1df6a-157">Y</span></span>        | <span data-ttu-id="1df6a-158">O código postal.</span><span class="sxs-lookup"><span data-stu-id="1df6a-158">The postal code.</span></span>                                           |
| <span data-ttu-id="1df6a-159">país</span><span class="sxs-lookup"><span data-stu-id="1df6a-159">country</span></span>      | <span data-ttu-id="1df6a-160">string</span><span class="sxs-lookup"><span data-stu-id="1df6a-160">string</span></span> | <span data-ttu-id="1df6a-161">Y</span><span class="sxs-lookup"><span data-stu-id="1df6a-161">Y</span></span>        | <span data-ttu-id="1df6a-162">O código de campo ISO alpha-2 de dois caracteres.</span><span class="sxs-lookup"><span data-stu-id="1df6a-162">The two-character ISO alpha-2 country code.</span></span>                |

### <a name="request-example"></a><span data-ttu-id="1df6a-163">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="1df6a-163">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="1df6a-164">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="1df6a-164">REST response</span></span>

<span data-ttu-id="1df6a-165">Se for bem sucedido, o método devolve um código de estado 200, como demonstrado na Resposta - exemplo de validação bem sucedido mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="1df6a-165">If successful, the method returns a status code 200 as demonstrated in the Response - validation succeeded example shown below.</span></span>

<span data-ttu-id="1df6a-166">Se o pedido falhar, o método devolve um código de estado 400, como demonstrado na Resposta - exemplo falhado de validação apresentado abaixo.</span><span class="sxs-lookup"><span data-stu-id="1df6a-166">If the request fails, the method returns a status code 400 as demonstrated in the Response - validation failed example shown below.</span></span> <span data-ttu-id="1df6a-167">O corpo de resposta contém uma carga útil JSON com informações adicionais sobre o erro.</span><span class="sxs-lookup"><span data-stu-id="1df6a-167">The response body contains a JSON payload with additional information about the error.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1df6a-168">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="1df6a-168">Response success and error codes</span></span>

<span data-ttu-id="1df6a-169">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="1df6a-169">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1df6a-170">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="1df6a-170">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1df6a-171">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="1df6a-171">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response---validation-succeeded-example"></a><span data-ttu-id="1df6a-172">Resposta - validação sucedeu exemplo</span><span class="sxs-lookup"><span data-stu-id="1df6a-172">Response - validation succeeded example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CV: IqhjoWVyq0Kl81dO.0
MS-ServerId: 030011719
Date: Mon, 13 Mar 2017 23:56:12 GMT
```

### <a name="response---validation-failed-example"></a><span data-ttu-id="1df6a-173">Resposta - exemplo falhado de validação</span><span class="sxs-lookup"><span data-stu-id="1df6a-173">Response - validation failed example</span></span>

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
