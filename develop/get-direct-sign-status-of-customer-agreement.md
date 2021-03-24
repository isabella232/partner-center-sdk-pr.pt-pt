---
title: Obtenha o estado de assinatura direta do cliente para o Microsoft Customer Agreement.
description: Pode utilizar o recurso DirectSignedCustomerAgreementStatus para obter o estado da assinatura direta (aceitação direta) do Acordo de Cliente da Microsoft.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 267e3aa63a94c5045977ad566eb5061df3b59882
ms.sourcegitcommit: bbdb5f7c9ddd42c2fc4eaadbb67d61aeeae805ca
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/24/2021
ms.locfileid: "105030569"
---
# <a name="get-the-status-of-a-customers-direct-signing-direct-acceptance-of-microsoft-customer-agreement"></a><span data-ttu-id="295af-103">Obtenha o estado da assinatura direta de um cliente (aceitação direta) do Microsoft Customer Agreement</span><span class="sxs-lookup"><span data-stu-id="295af-103">Get the status of a customer's direct signing (direct acceptance) of Microsoft Customer Agreement</span></span>

<span data-ttu-id="295af-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="295af-104">**Applies to:**</span></span>

- <span data-ttu-id="295af-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="295af-105">Partner Center</span></span>

<span data-ttu-id="295af-106">O recurso **DirectSignedCustomerAgreementStatus** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="295af-106">The **DirectSignedCustomerAgreementStatus** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="295af-107">Este recurso não é *aplicável* a:</span><span class="sxs-lookup"><span data-stu-id="295af-107">This resource is *not applicable* to:</span></span>

- <span data-ttu-id="295af-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="295af-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="295af-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="295af-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="295af-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="295af-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="295af-111">Este artigo explica como pode recuperar o estado da aceitação direta de um cliente do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="295af-111">This article explains how you can retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="295af-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="295af-112">Prerequisites</span></span>

- <span data-ttu-id="295af-113">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="295af-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="295af-114">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="295af-114">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="295af-115">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="295af-115">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="295af-116">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="295af-116">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="295af-117">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="295af-117">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="295af-118">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="295af-118">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="295af-119">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="295af-119">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="295af-120">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="295af-120">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="295af-121">C\#</span><span class="sxs-lookup"><span data-stu-id="295af-121">C\#</span></span>

<span data-ttu-id="295af-122">Para recuperar o estado da aceitação direta de um cliente do Microsoft Customer Agreement, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador do cliente.</span><span class="sxs-lookup"><span data-stu-id="295af-122">To retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="295af-123">Em seguida, use a propriedade [**Agreements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.agreements) para recuperar uma interface [**ICustomerAgreementCollection.**](/dotnet/api/microsoft.store.partnercenter.agreements.icustomeragreementcollection)</span><span class="sxs-lookup"><span data-stu-id="295af-123">Then use the [**Agreements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.agreements) property to retrieve a [**ICustomerAgreementCollection**](/dotnet/api/microsoft.store.partnercenter.agreements.icustomeragreementcollection) interface.</span></span> <span data-ttu-id="295af-124">Finalmente, ligue `GetDirectSignedCustomerAgreementStatus()` ou `GetDirectSignedCustomerAgreementStatusAsync()` recupere o estado.</span><span class="sxs-lookup"><span data-stu-id="295af-124">Finally, call `GetDirectSignedCustomerAgreementStatus()` or `GetDirectSignedCustomerAgreementStatusAsync()` to retrieve the status.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerDirectSigningStatus = partnerOperations.Customers.ById(selectedCustomerId).Agreements.GetDirectSignedCustomerAgreementStatus();
```

<span data-ttu-id="295af-125">**Amostra**: [App de amostra de consola](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="295af-125">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="295af-126">**Projeto**: Classe SdkSamples : GetDirectSignedCustomerAgreementStatus.cs</span><span class="sxs-lookup"><span data-stu-id="295af-126">**Project**: SdkSamples **Class**: GetDirectSignedCustomerAgreementStatus.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="295af-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="295af-127">REST request</span></span>

<span data-ttu-id="295af-128">Para recuperar o estado da aceitação direta de um cliente do Microsoft Customer Agreement, crie um pedido DEE para recuperar o [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="295af-128">To retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement, create a REST request to retrieve the [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) for the customer.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="295af-129">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="295af-129">Request syntax</span></span>

<span data-ttu-id="295af-130">Utilize a seguinte sintaxe de pedido:</span><span class="sxs-lookup"><span data-stu-id="295af-130">Use the following request syntax:</span></span>

| <span data-ttu-id="295af-131">Método</span><span class="sxs-lookup"><span data-stu-id="295af-131">Method</span></span> | <span data-ttu-id="295af-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="295af-132">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="295af-133">GET</span><span class="sxs-lookup"><span data-stu-id="295af-133">GET</span></span>    | <span data-ttu-id="295af-134">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="295af-134">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="295af-135">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="295af-135">URI parameters</span></span>

<span data-ttu-id="295af-136">Pode utilizar os seguintes parâmetros URI com o seu pedido:</span><span class="sxs-lookup"><span data-stu-id="295af-136">You can use the following URI parameters with your request:</span></span>

| <span data-ttu-id="295af-137">Nome</span><span class="sxs-lookup"><span data-stu-id="295af-137">Name</span></span>             | <span data-ttu-id="295af-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="295af-138">Type</span></span> | <span data-ttu-id="295af-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="295af-139">Required</span></span> | <span data-ttu-id="295af-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="295af-140">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="295af-141">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="295af-141">customer-tenant-id</span></span> | <span data-ttu-id="295af-142">GUID</span><span class="sxs-lookup"><span data-stu-id="295af-142">GUID</span></span> | <span data-ttu-id="295af-143">Yes</span><span class="sxs-lookup"><span data-stu-id="295af-143">Yes</span></span> | <span data-ttu-id="295af-144">O valor é um **CustomerTenantId** formatado pelo GUID que lhe permite especificar o ID do inquilino de um cliente.</span><span class="sxs-lookup"><span data-stu-id="295af-144">The value is a GUID-formatted **CustomerTenantId** that allows you to specify the tenant ID of a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="295af-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="295af-145">Request headers</span></span>

<span data-ttu-id="295af-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="295af-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="295af-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="295af-147">Request body</span></span>

<span data-ttu-id="295af-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="295af-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="295af-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="295af-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="295af-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="295af-150">REST response</span></span>

<span data-ttu-id="295af-151">Se for bem sucedido, este método devolve um recurso [ **DirectSignedCustomerAgreementStatus**](./customer-agreement-direct-sign-status-resource.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="295af-151">If successful, this method returns a [**DirectSignedCustomerAgreementStatus** resource](./customer-agreement-direct-sign-status-resource.md) in the response body.</span></span>

<span data-ttu-id="295af-152">O recurso tem uma propriedade **isSigned** que indica o estado de assinatura direta (aceitação direta) do cliente.</span><span class="sxs-lookup"><span data-stu-id="295af-152">The resource has an **isSigned** property that indicates the customer's direct signing (direct acceptance) status.</span></span>

- <span data-ttu-id="295af-153">Um valor **verdadeiro** indica que o contrato foi assinado (aceite) diretamente pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="295af-153">A value of **true** indicates that the agreement has been signed (accepted) directly by the customer.</span></span>

- <span data-ttu-id="295af-154">Um valor **de falso** indica que o contrato *não* foi assinado (aceite) diretamente pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="295af-154">A value of **false** indicates that the agreement has *not* been signed (accepted) directly by the customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="295af-155">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="295af-155">Response success and error codes</span></span>

<span data-ttu-id="295af-156">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="295af-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="295af-157">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="295af-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="295af-158">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="295af-158">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="295af-159">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="295af-159">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 20
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b

{"isSigned":true}
```
