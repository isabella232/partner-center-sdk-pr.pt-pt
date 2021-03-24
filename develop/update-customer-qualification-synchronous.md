---
title: Atualizar a qualificação de um cliente
description: Saiba como atualizar as qualificações de um cliente através de rastreio sincronizado ou de verificação, incluindo o endereço associado ao perfil.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 0ffe6d1a236a8a07e1ff71163e7639ef1f3437e1
ms.sourcegitcommit: bbdb5f7c9ddd42c2fc4eaadbb67d61aeeae805ca
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/24/2021
ms.locfileid: "105030594"
---
# <a name="update-a-customers-qualification-via-synchronous-validation"></a><span data-ttu-id="4b4d4-103">Atualizar a qualificação de um cliente através de validação sincronizada</span><span class="sxs-lookup"><span data-stu-id="4b4d4-103">Update a customer's qualification via synchronous validation</span></span>

<span data-ttu-id="4b4d4-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="4b4d4-104">**Applies To**</span></span>

- <span data-ttu-id="4b4d4-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="4b4d4-105">Partner Center</span></span>

<span data-ttu-id="4b4d4-106">Saiba como atualizar as qualificações de um cliente de forma sincronizada através das APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-106">Learn how to update a customer's qualifications synchronously via Partner Center APIs.</span></span> <span data-ttu-id="4b4d4-107">Para aprender a fazê-lo assíncronos, consulte [a atualização da qualificação de um cliente através de validação assíncronosa.](update-customer-qualification-asynchronous.md)</span><span class="sxs-lookup"><span data-stu-id="4b4d4-107">To learn how to do this asynchronously, see [Update a customer's qualification via asynchronous validation](update-customer-qualification-asynchronous.md).</span></span>

<span data-ttu-id="4b4d4-108">Um parceiro pode atualizar a qualificação de um cliente para ser "Education" ou "GovernmentCommunityCloud".</span><span class="sxs-lookup"><span data-stu-id="4b4d4-108">A partner can update a customer's qualification to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="4b4d4-109">Outros valores, "Nenhum" e "Sem Fins Lucrativos", não podem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-109">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b4d4-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4b4d4-110">Prerequisites</span></span>

- <span data-ttu-id="4b4d4-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4b4d4-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4b4d4-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="4b4d4-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4b4d4-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4b4d4-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4b4d4-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4b4d4-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="4b4d4-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4b4d4-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="4b4d4-117">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4b4d4-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4b4d4-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="4b4d4-119">C\#</span><span class="sxs-lookup"><span data-stu-id="4b4d4-119">C\#</span></span>

<span data-ttu-id="4b4d4-120">Para atualizar a qualificação de um cliente para "Educação", ligue **para [Update/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification.update)** sobre um  [**Cliente**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer)existente .</span><span class="sxs-lookup"><span data-stu-id="4b4d4-120">To update a customer's qualification to "Education", call **[Update/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification.update)** on an existing  [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer).</span></span>

``` csharp
// CustomerQualification is an enum

var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.Education);
```

<span data-ttu-id="4b4d4-121">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="4b4d4-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="4b4d4-122">**Projeto**: PartnerSDK.FeatureSamples **Class**: CustomerQualificationOperations.cs</span><span class="sxs-lookup"><span data-stu-id="4b4d4-122">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerQualificationOperations.cs</span></span>

<span data-ttu-id="4b4d4-123">Para atualizar a qualificação de um cliente para **o GovernmentCommunityCloud** num cliente existente sem habilitação, o parceiro é obrigado a incluir o Código de [**Validação**](utility-resources.md#validationcode)do cliente.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-123">To update a customer's qualification to **GovernmentCommunityCloud** on an existing customer without a qualification, the partner is required to include the customer's [**ValidationCode**](utility-resources.md#validationcode).</span></span>

``` csharp
// CustomerQualification is an enum
// GCC validation is type ValidationCode

var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.GovernmentCommunityCloud, gccValidation);
```

## <a name="rest-request"></a><span data-ttu-id="4b4d4-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="4b4d4-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4b4d4-125">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b4d4-125">Request syntax</span></span>

| <span data-ttu-id="4b4d4-126">Método</span><span class="sxs-lookup"><span data-stu-id="4b4d4-126">Method</span></span>  | <span data-ttu-id="4b4d4-127">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="4b4d4-127">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4b4d4-128">**PUT**</span><span class="sxs-lookup"><span data-stu-id="4b4d4-128">**PUT**</span></span> | <span data-ttu-id="4b4d4-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer_id}/qualification?code={validCode} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4b4d4-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualification?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="4b4d4-130">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="4b4d4-130">URI parameter</span></span>

<span data-ttu-id="4b4d4-131">Utilize o seguinte parâmetro de consulta para atualizar a qualificação.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-131">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="4b4d4-132">Nome</span><span class="sxs-lookup"><span data-stu-id="4b4d4-132">Name</span></span>                   | <span data-ttu-id="4b4d4-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="4b4d4-133">Type</span></span> | <span data-ttu-id="4b4d4-134">Necessário</span><span class="sxs-lookup"><span data-stu-id="4b4d4-134">Required</span></span> | <span data-ttu-id="4b4d4-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b4d4-135">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4b4d4-136">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="4b4d4-136">**customer-tenant-id**</span></span> | <span data-ttu-id="4b4d4-137">GUID</span><span class="sxs-lookup"><span data-stu-id="4b4d4-137">GUID</span></span> | <span data-ttu-id="4b4d4-138">Yes</span><span class="sxs-lookup"><span data-stu-id="4b4d4-138">Yes</span></span>      | <span data-ttu-id="4b4d4-139">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-139">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="4b4d4-140">**validaçãoDesco**</span><span class="sxs-lookup"><span data-stu-id="4b4d4-140">**validationCode**</span></span>     | <span data-ttu-id="4b4d4-141">int</span><span class="sxs-lookup"><span data-stu-id="4b4d4-141">int</span></span>  | <span data-ttu-id="4b4d4-142">No</span><span class="sxs-lookup"><span data-stu-id="4b4d4-142">No</span></span>       | <span data-ttu-id="4b4d4-143">Só era necessário para a Nuvem Comunitária do Governo.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-143">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="4b4d4-144">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="4b4d4-144">Request headers</span></span>

<span data-ttu-id="4b4d4-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4b4d4-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4b4d4-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="4b4d4-146">Request body</span></span>

<span data-ttu-id="4b4d4-147">O valor inteiro do número de [**clientesQualificação.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification)</span><span class="sxs-lookup"><span data-stu-id="4b4d4-147">The integer value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="4b4d4-148">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="4b4d4-148">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a><span data-ttu-id="4b4d4-149">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="4b4d4-149">REST response</span></span>

<span data-ttu-id="4b4d4-150">Se for bem sucedido, este método devolve a propriedade [**de qualificação**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) atualizada no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-150">If successful, this method returns updated [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4b4d4-151">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="4b4d4-151">Response success and error codes</span></span>

<span data-ttu-id="4b4d4-152">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4b4d4-153">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4b4d4-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4b4d4-154">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4b4d4-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4b4d4-155">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="4b4d4-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 14
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
"governmentcommunitycloud"
```

## <a name="related-articles"></a><span data-ttu-id="4b4d4-156">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="4b4d4-156">Related articles</span></span>

- [<span data-ttu-id="4b4d4-157">Obter a qualificação de um cliente</span><span class="sxs-lookup"><span data-stu-id="4b4d4-157">Get a customer's qualification</span></span>](./get-customer-qualification-synchronous.md)
- [<span data-ttu-id="4b4d4-158">Obter os códigos de validação de um parceiro</span><span class="sxs-lookup"><span data-stu-id="4b4d4-158">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)
