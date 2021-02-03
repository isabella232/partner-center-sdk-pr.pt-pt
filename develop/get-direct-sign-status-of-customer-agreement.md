---
title: Obtenha o estado de assinatura direta do cliente para o Microsoft Customer Agreement.
description: Pode utilizar o recurso DirectSignedCustomerAgreementStatus para obter o estado da assinatura direta (aceitação direta) do Acordo de Cliente da Microsoft.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 3f1deb20a18bc6e7133cac91db528f2d1ad694e2
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768738"
---
# <a name="get-the-status-of-a-customers-direct-signing-direct-acceptance-of-microsoft-customer-agreement"></a><span data-ttu-id="35819-103">Obtenha o estado da assinatura direta de um cliente (aceitação direta) do Microsoft Customer Agreement</span><span class="sxs-lookup"><span data-stu-id="35819-103">Get the status of a customer's direct signing (direct acceptance) of Microsoft Customer Agreement</span></span>

<span data-ttu-id="35819-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="35819-104">**Applies to:**</span></span>

- <span data-ttu-id="35819-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="35819-105">Partner Center</span></span>

<span data-ttu-id="35819-106">O recurso **DirectSignedCustomerAgreementStatus** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="35819-106">The **DirectSignedCustomerAgreementStatus** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="35819-107">Este recurso não é *aplicável* a:</span><span class="sxs-lookup"><span data-stu-id="35819-107">This resource is *not applicable* to:</span></span>

- <span data-ttu-id="35819-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="35819-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="35819-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="35819-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="35819-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="35819-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="35819-111">Este artigo explica como pode recuperar o estado da aceitação direta de um cliente do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="35819-111">This article explains how you can retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="rest-request"></a><span data-ttu-id="35819-112">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="35819-112">REST request</span></span>

<span data-ttu-id="35819-113">Para recuperar o estado da aceitação direta de um cliente do Microsoft Customer Agreement, crie um pedido DEE para recuperar o [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="35819-113">To retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement, create a REST request to retrieve the [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) for the customer.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="35819-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="35819-114">Request syntax</span></span>

<span data-ttu-id="35819-115">Utilize a seguinte sintaxe de pedido:</span><span class="sxs-lookup"><span data-stu-id="35819-115">Use the following request syntax:</span></span>

| <span data-ttu-id="35819-116">Método</span><span class="sxs-lookup"><span data-stu-id="35819-116">Method</span></span> | <span data-ttu-id="35819-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="35819-117">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="35819-118">GET</span><span class="sxs-lookup"><span data-stu-id="35819-118">GET</span></span>    | <span data-ttu-id="35819-119">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="35819-119">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="35819-120">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="35819-120">URI parameters</span></span>

<span data-ttu-id="35819-121">Pode utilizar os seguintes parâmetros URI com o seu pedido:</span><span class="sxs-lookup"><span data-stu-id="35819-121">You can use the following URI parameters with your request:</span></span>

| <span data-ttu-id="35819-122">Nome</span><span class="sxs-lookup"><span data-stu-id="35819-122">Name</span></span>             | <span data-ttu-id="35819-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="35819-123">Type</span></span> | <span data-ttu-id="35819-124">Necessário</span><span class="sxs-lookup"><span data-stu-id="35819-124">Required</span></span> | <span data-ttu-id="35819-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="35819-125">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="35819-126">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="35819-126">customer-tenant-id</span></span> | <span data-ttu-id="35819-127">GUID</span><span class="sxs-lookup"><span data-stu-id="35819-127">GUID</span></span> | <span data-ttu-id="35819-128">Sim</span><span class="sxs-lookup"><span data-stu-id="35819-128">Yes</span></span> | <span data-ttu-id="35819-129">O valor é um **CustomerTenantId** formatado pelo GUID que lhe permite especificar o ID do inquilino de um cliente.</span><span class="sxs-lookup"><span data-stu-id="35819-129">The value is a GUID-formatted **CustomerTenantId** that allows you to specify the tenant ID of a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="35819-130">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="35819-130">Request headers</span></span>

<span data-ttu-id="35819-131">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="35819-131">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="35819-132">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="35819-132">Request body</span></span>

<span data-ttu-id="35819-133">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="35819-133">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="35819-134">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="35819-134">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="35819-135">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="35819-135">REST response</span></span>

<span data-ttu-id="35819-136">Se for bem sucedido, este método devolve um recurso [ **DirectSignedCustomerAgreementStatus**](./customer-agreement-direct-sign-status-resource.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="35819-136">If successful, this method returns a [**DirectSignedCustomerAgreementStatus** resource](./customer-agreement-direct-sign-status-resource.md) in the response body.</span></span>

<span data-ttu-id="35819-137">O recurso tem uma propriedade **isSigned** que indica o estado de assinatura direta (aceitação direta) do cliente.</span><span class="sxs-lookup"><span data-stu-id="35819-137">The resource has an **isSigned** property that indicates the customer's direct signing (direct acceptance) status.</span></span>

- <span data-ttu-id="35819-138">Um valor **verdadeiro** indica que o contrato foi assinado (aceite) diretamente pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="35819-138">A value of **true** indicates that the agreement has been signed (accepted) directly by the customer.</span></span>

- <span data-ttu-id="35819-139">Um valor **de falso** indica que o contrato *não* foi assinado (aceite) diretamente pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="35819-139">A value of **false** indicates that the agreement has *not* been signed (accepted) directly by the customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="35819-140">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="35819-140">Response success and error codes</span></span>

<span data-ttu-id="35819-141">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="35819-141">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="35819-142">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="35819-142">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="35819-143">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="35819-143">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="35819-144">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="35819-144">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 20
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b

{"isSigned":true}
```
