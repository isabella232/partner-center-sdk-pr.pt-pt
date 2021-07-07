---
title: Atualizar a qualificação de um cliente
description: Saiba como atualizar as qualificações de um cliente através de rastreio sincronizado ou de verificação, incluindo o endereço associado ao perfil.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 5047743afdef02033d9494e3d8c16c9ab96b3fe9
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446654"
---
# <a name="update-a-customers-qualification-via-synchronous-validation"></a><span data-ttu-id="b34c9-103">Atualizar a qualificação de um cliente através de validação sincronizada</span><span class="sxs-lookup"><span data-stu-id="b34c9-103">Update a customer's qualification via synchronous validation</span></span>

<span data-ttu-id="b34c9-104">Saiba como atualizar as qualificações de um cliente de forma sincronizada através das APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b34c9-104">Learn how to update a customer's qualifications synchronously via Partner Center APIs.</span></span> <span data-ttu-id="b34c9-105">Para aprender a fazê-lo assíncronos, consulte [a atualização da qualificação de um cliente através de validação assíncronosa.](update-customer-qualification-asynchronous.md)</span><span class="sxs-lookup"><span data-stu-id="b34c9-105">To learn how to do this asynchronously, see [Update a customer's qualification via asynchronous validation](update-customer-qualification-asynchronous.md).</span></span>

<span data-ttu-id="b34c9-106">Um parceiro pode atualizar a qualificação de um cliente para ser "Education" ou "GovernmentCommunityCloud".</span><span class="sxs-lookup"><span data-stu-id="b34c9-106">A partner can update a customer's qualification to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="b34c9-107">Outros valores, "Nenhum" e "Sem Fins Lucrativos", não podem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="b34c9-107">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b34c9-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b34c9-108">Prerequisites</span></span>

- <span data-ttu-id="b34c9-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b34c9-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b34c9-110">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="b34c9-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="b34c9-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b34c9-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="b34c9-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b34c9-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="b34c9-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="b34c9-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="b34c9-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="b34c9-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="b34c9-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="b34c9-115">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="b34c9-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b34c9-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="b34c9-117">C\#</span><span class="sxs-lookup"><span data-stu-id="b34c9-117">C\#</span></span>

<span data-ttu-id="b34c9-118">Para atualizar a qualificação de um cliente para "Educação", ligue **para [Update/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification.update)** sobre um  [**Cliente**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer)existente .</span><span class="sxs-lookup"><span data-stu-id="b34c9-118">To update a customer's qualification to "Education", call **[Update/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification.update)** on an existing  [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer).</span></span>

``` csharp
// CustomerQualification is an enum

var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.Education);
```

<span data-ttu-id="b34c9-119">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b34c9-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b34c9-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerQualificationOperations.cs</span><span class="sxs-lookup"><span data-stu-id="b34c9-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerQualificationOperations.cs</span></span>

<span data-ttu-id="b34c9-121">Para atualizar a qualificação de um cliente para **o GovernmentCommunityCloud** num cliente existente sem habilitação, o parceiro é obrigado a incluir o Código de [**Validação**](utility-resources.md#validationcode)do cliente.</span><span class="sxs-lookup"><span data-stu-id="b34c9-121">To update a customer's qualification to **GovernmentCommunityCloud** on an existing customer without a qualification, the partner is required to include the customer's [**ValidationCode**](utility-resources.md#validationcode).</span></span>

``` csharp
// CustomerQualification is an enum
// GCC validation is type ValidationCode

var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.GovernmentCommunityCloud, gccValidation);
```

## <a name="rest-request"></a><span data-ttu-id="b34c9-122">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b34c9-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b34c9-123">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b34c9-123">Request syntax</span></span>

| <span data-ttu-id="b34c9-124">Método</span><span class="sxs-lookup"><span data-stu-id="b34c9-124">Method</span></span>  | <span data-ttu-id="b34c9-125">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b34c9-125">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b34c9-126">**PUT**</span><span class="sxs-lookup"><span data-stu-id="b34c9-126">**PUT**</span></span> | <span data-ttu-id="b34c9-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer_id}/qualification?code={validCode} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b34c9-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualification?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="b34c9-128">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="b34c9-128">URI parameter</span></span>

<span data-ttu-id="b34c9-129">Utilize o seguinte parâmetro de consulta para atualizar a qualificação.</span><span class="sxs-lookup"><span data-stu-id="b34c9-129">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="b34c9-130">Nome</span><span class="sxs-lookup"><span data-stu-id="b34c9-130">Name</span></span>                   | <span data-ttu-id="b34c9-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="b34c9-131">Type</span></span> | <span data-ttu-id="b34c9-132">Necessário</span><span class="sxs-lookup"><span data-stu-id="b34c9-132">Required</span></span> | <span data-ttu-id="b34c9-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="b34c9-133">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b34c9-134">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="b34c9-134">**customer-tenant-id**</span></span> | <span data-ttu-id="b34c9-135">GUID</span><span class="sxs-lookup"><span data-stu-id="b34c9-135">GUID</span></span> | <span data-ttu-id="b34c9-136">Yes</span><span class="sxs-lookup"><span data-stu-id="b34c9-136">Yes</span></span>      | <span data-ttu-id="b34c9-137">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="b34c9-137">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="b34c9-138">**validaçãoDesco**</span><span class="sxs-lookup"><span data-stu-id="b34c9-138">**validationCode**</span></span>     | <span data-ttu-id="b34c9-139">int</span><span class="sxs-lookup"><span data-stu-id="b34c9-139">int</span></span>  | <span data-ttu-id="b34c9-140">No</span><span class="sxs-lookup"><span data-stu-id="b34c9-140">No</span></span>       | <span data-ttu-id="b34c9-141">Só era necessário para Nuvem da Comunidade Governamental.</span><span class="sxs-lookup"><span data-stu-id="b34c9-141">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="b34c9-142">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b34c9-142">Request headers</span></span>

<span data-ttu-id="b34c9-143">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b34c9-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b34c9-144">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b34c9-144">Request body</span></span>

<span data-ttu-id="b34c9-145">O valor inteiro do número de [**clientesQualificação.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification)</span><span class="sxs-lookup"><span data-stu-id="b34c9-145">The integer value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="b34c9-146">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b34c9-146">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a><span data-ttu-id="b34c9-147">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b34c9-147">REST response</span></span>

<span data-ttu-id="b34c9-148">Se for bem sucedido, este método devolve a propriedade [**de qualificação**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) atualizada no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="b34c9-148">If successful, this method returns updated [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b34c9-149">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b34c9-149">Response success and error codes</span></span>

<span data-ttu-id="b34c9-150">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b34c9-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b34c9-151">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b34c9-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b34c9-152">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b34c9-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b34c9-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b34c9-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 14
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
"governmentcommunitycloud"
```

## <a name="related-articles"></a><span data-ttu-id="b34c9-154">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="b34c9-154">Related articles</span></span>

- [<span data-ttu-id="b34c9-155">Obter a qualificação de um cliente</span><span class="sxs-lookup"><span data-stu-id="b34c9-155">Get a customer's qualification</span></span>](./get-customer-qualification-synchronous.md)
- [<span data-ttu-id="b34c9-156">Obter os códigos de validação de um parceiro</span><span class="sxs-lookup"><span data-stu-id="b34c9-156">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)
