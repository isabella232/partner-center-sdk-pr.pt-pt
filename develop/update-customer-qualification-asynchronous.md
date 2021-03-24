---
title: Atualizar as qualificações de um cliente
description: Atualiza as qualificações de um cliente assíncroneamente, incluindo o endereço associado ao perfil.
ms.date: 03/23/2021
ms.service: partner-dashboard
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 7606eeaac4df158ec0fad6ffd4e565bb250f448e
ms.sourcegitcommit: bbdb5f7c9ddd42c2fc4eaadbb67d61aeeae805ca
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/24/2021
ms.locfileid: "105030611"
---
# <a name="update-a-customers-qualifications-asynchronously"></a><span data-ttu-id="00e60-103">Atualizar as qualificações de um cliente assíncroneamente</span><span class="sxs-lookup"><span data-stu-id="00e60-103">Update a customer's qualifications asynchronously</span></span>

<span data-ttu-id="00e60-104">Atualiza as qualificações de um cliente assíncroneamente.</span><span class="sxs-lookup"><span data-stu-id="00e60-104">Updates a customer's qualifications asynchronously.</span></span>

<span data-ttu-id="00e60-105">Um parceiro pode atualizar as qualificações de um cliente assíncroneamente para ser "Education" ou "GovernmentCommunityCloud".</span><span class="sxs-lookup"><span data-stu-id="00e60-105">A partner can update a customer's qualifications asynchronously to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="00e60-106">Outros valores, "Nenhum" e "Sem Fins Lucrativos", não podem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="00e60-106">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00e60-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="00e60-107">Prerequisites</span></span>

- <span data-ttu-id="00e60-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="00e60-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="00e60-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="00e60-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="00e60-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="00e60-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="00e60-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="00e60-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="00e60-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="00e60-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="00e60-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="00e60-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="00e60-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="00e60-114">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="00e60-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="00e60-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="00e60-116">C\#</span><span class="sxs-lookup"><span data-stu-id="00e60-116">C\#</span></span>

<span data-ttu-id="00e60-117">Para criar a qualificação de um cliente para "Educação", primeiro criar um objeto que represente o tipo de qualificação.</span><span class="sxs-lookup"><span data-stu-id="00e60-117">To create a customer's qualification for "Education", first create an object representing the qualification type.</span></span> <span data-ttu-id="00e60-118">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="00e60-118">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="00e60-119">Em seguida, use a propriedade [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) para recuperar uma interface [**ICustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification)</span><span class="sxs-lookup"><span data-stu-id="00e60-119">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="00e60-120">Finalmente, ligue `CreateQualifications()` ou com o objeto do tipo de `CreateQualificationsAsync()` qualificação como parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="00e60-120">Finally, call `CreateQualifications()` or `CreateQualificationsAsync()` with the qualification type object as an input parameter.</span></span>

``` csharp
var qualificationType = { Qualification = "education" };
var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType);
```

<span data-ttu-id="00e60-121">**Amostra**: [App de amostra de consola](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="00e60-121">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="00e60-122">**Projeto**: Classe SdkSamples : CreateCustomerQualification.cs</span><span class="sxs-lookup"><span data-stu-id="00e60-122">**Project**: SdkSamples **Class**: CreateCustomerQualification.cs</span></span>

<span data-ttu-id="00e60-123">Para atualizar a qualificação de um cliente para **o GovernmentCommunityCloud** num cliente existente sem habilitação, o parceiro também é obrigado a incluir o Código de [**Validação**](utility-resources.md#validationcode)do cliente.</span><span class="sxs-lookup"><span data-stu-id="00e60-123">To update a customer's qualification to **GovernmentCommunityCloud** on an existing customer without a qualification, the partner is also required to include the customer's [**ValidationCode**](utility-resources.md#validationcode).</span></span> <span data-ttu-id="00e60-124">Primeiro, criar um objeto que represente o tipo de qualificação.</span><span class="sxs-lookup"><span data-stu-id="00e60-124">First, create an object representing the qualification type.</span></span> <span data-ttu-id="00e60-125">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="00e60-125">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="00e60-126">Em seguida, use a propriedade [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) para recuperar uma interface [**ICustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification)</span><span class="sxs-lookup"><span data-stu-id="00e60-126">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="00e60-127">Finalmente, ligue `CreateQualifications()` ou com o objeto tipo de `CreateQualificationsAsync()` qualificação e o código de validação como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="00e60-127">Finally, call `CreateQualifications()` or `CreateQualificationsAsync()` with the qualification type object and the validation code as input parameters.</span></span>

``` csharp
// GCC validation is type ValidationCode
var qualificationType = { Qualification = "GovernmentCommunityCloud" };
var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType, gccValidation);
```

<span data-ttu-id="00e60-128">**Amostra**: [App de amostra de consola](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="00e60-128">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="00e60-129">**Projeto**: Classe SdkSamples : CreateCustomerQualificationWithGCC.cs</span><span class="sxs-lookup"><span data-stu-id="00e60-129">**Project**: SdkSamples **Class**: CreateCustomerQualificationWithGCC.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="00e60-130">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="00e60-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="00e60-131">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="00e60-131">Request syntax</span></span>

| <span data-ttu-id="00e60-132">Método</span><span class="sxs-lookup"><span data-stu-id="00e60-132">Method</span></span>  | <span data-ttu-id="00e60-133">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="00e60-133">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="00e60-134">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="00e60-134">**POST**</span></span> | <span data-ttu-id="00e60-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer_id}/qualificações?código={validaçãoD} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="00e60-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualifications?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="00e60-136">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="00e60-136">URI parameter</span></span>

<span data-ttu-id="00e60-137">Utilize o seguinte parâmetro de consulta para atualizar a qualificação.</span><span class="sxs-lookup"><span data-stu-id="00e60-137">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="00e60-138">Nome</span><span class="sxs-lookup"><span data-stu-id="00e60-138">Name</span></span>                   | <span data-ttu-id="00e60-139">Tipo</span><span class="sxs-lookup"><span data-stu-id="00e60-139">Type</span></span> | <span data-ttu-id="00e60-140">Necessário</span><span class="sxs-lookup"><span data-stu-id="00e60-140">Required</span></span> | <span data-ttu-id="00e60-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="00e60-141">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="00e60-142">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="00e60-142">**customer-tenant-id**</span></span> | <span data-ttu-id="00e60-143">GUID</span><span class="sxs-lookup"><span data-stu-id="00e60-143">GUID</span></span> | <span data-ttu-id="00e60-144">Yes</span><span class="sxs-lookup"><span data-stu-id="00e60-144">Yes</span></span>      | <span data-ttu-id="00e60-145">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="00e60-145">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="00e60-146">**validaçãoDesco**</span><span class="sxs-lookup"><span data-stu-id="00e60-146">**validationCode**</span></span>     | <span data-ttu-id="00e60-147">int</span><span class="sxs-lookup"><span data-stu-id="00e60-147">int</span></span>  | <span data-ttu-id="00e60-148">No</span><span class="sxs-lookup"><span data-stu-id="00e60-148">No</span></span>       | <span data-ttu-id="00e60-149">Só era necessário para a Nuvem Comunitária do Governo.</span><span class="sxs-lookup"><span data-stu-id="00e60-149">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="00e60-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="00e60-150">Request headers</span></span>

<span data-ttu-id="00e60-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="00e60-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="00e60-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="00e60-152">Request body</span></span>

<span data-ttu-id="00e60-153">Esta tabela descreve o objeto de qualificação no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="00e60-153">This table describes the qualification object in the request body.</span></span>

<span data-ttu-id="00e60-154">Propriedade</span><span class="sxs-lookup"><span data-stu-id="00e60-154">Property</span></span> | <span data-ttu-id="00e60-155">Tipo</span><span class="sxs-lookup"><span data-stu-id="00e60-155">Type</span></span> | <span data-ttu-id="00e60-156">Necessário</span><span class="sxs-lookup"><span data-stu-id="00e60-156">Required</span></span> | <span data-ttu-id="00e60-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="00e60-157">Description</span></span>
-------- | ---- | -------- | -----------
<span data-ttu-id="00e60-158">Qualificação</span><span class="sxs-lookup"><span data-stu-id="00e60-158">Qualification</span></span> | <span data-ttu-id="00e60-159">string</span><span class="sxs-lookup"><span data-stu-id="00e60-159">string</span></span> | <span data-ttu-id="00e60-160">Yes</span><span class="sxs-lookup"><span data-stu-id="00e60-160">Yes</span></span> | <span data-ttu-id="00e60-161">O valor de cadeia da [**enum de Qualificação**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) do Cliente.</span><span class="sxs-lookup"><span data-stu-id="00e60-161">The string value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="00e60-162">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="00e60-162">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

{
    "Qualification": "Education"
}

```

## <a name="rest-response"></a><span data-ttu-id="00e60-163">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="00e60-163">REST response</span></span>

<span data-ttu-id="00e60-164">Se for bem sucedido, este método devolve um objeto de qualificações no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="00e60-164">If successful, this method returns a qualifications object in the response body.</span></span> <span data-ttu-id="00e60-165">Abaixo está um exemplo da chamada **do POST** sobre um cliente (com uma qualificação anterior de **Nenhum)** com a qualificação **de Educação.**</span><span class="sxs-lookup"><span data-stu-id="00e60-165">Below is an example of the **POST** call on a customer (with a previous qualification of **None**) with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="00e60-166">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="00e60-166">Response success and error codes</span></span>

<span data-ttu-id="00e60-167">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="00e60-167">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="00e60-168">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="00e60-168">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="00e60-169">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="00e60-169">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="00e60-170">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="00e60-170">Response example</span></span>

```http
HTTP/1.1 201 CREATED
Content-Length: 29
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualification": "Education",
    "vettingStatus": "InReview",
    "vettingCreateDate": "2020-12-04T20:54:24Z" // UTC
}
```

## <a name="related-articles"></a><span data-ttu-id="00e60-171">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="00e60-171">Related articles</span></span>

- [<span data-ttu-id="00e60-172">Obtenha as qualificações de um cliente</span><span class="sxs-lookup"><span data-stu-id="00e60-172">Get a customer's qualifications</span></span>](./get-customer-qualification-asynchronous.md)
- [<span data-ttu-id="00e60-173">Obter os códigos de validação de um parceiro</span><span class="sxs-lookup"><span data-stu-id="00e60-173">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)
