---
title: Eliminar Revendedor Indireto na Caixa de Areia
description: Fornece informações sobre a eliminação de Revendedores Indiretos da Caixa de Areia e a capacitação de testes de ponta a ponta utilizando APIs.
ms.date: 5/24/2021
ms.author: vijvala
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ba1fd002ac62aba4e414d263b33ecc8153054602
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973014"
---
# <a name="delete-indirect-reseller-in-sandbox"></a><span data-ttu-id="6dbe5-103">Eliminar Revendedor Indireto na Caixa de Areia</span><span class="sxs-lookup"><span data-stu-id="6dbe5-103">Delete Indirect Reseller in Sandbox</span></span>

<span data-ttu-id="6dbe5-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="6dbe5-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="6dbe5-105">Este documento mostra como eliminar os Fornecedores Indiretos da Sandbox e permitir testes de ponta a ponta utilizando APIs.</span><span class="sxs-lookup"><span data-stu-id="6dbe5-105">This document shows how to delete Sandbox Indirect Providers and enable end-to-end testing using APIs.</span></span>

> [!Important]
> <span data-ttu-id="6dbe5-106">Este documento descreve funcionalidades que só são permitidas no ambiente Sandbox para experiências de Modelo Indireto.</span><span class="sxs-lookup"><span data-stu-id="6dbe5-106">This document describes features that are only allowed in the Sandbox environment for Indirect Model experiences.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6dbe5-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6dbe5-107">Prerequisites</span></span>

- <span data-ttu-id="6dbe5-108">Credenciais descritas na [Autenticação do Centro de Parceiros.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="6dbe5-108">Credentials as described in [Partner Center Authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6dbe5-109">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="6dbe5-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller"></a><span data-ttu-id="6dbe5-110">Sandbox Fornecedor Indireto – Eliminar Revendedor Indireto Sandbox</span><span class="sxs-lookup"><span data-stu-id="6dbe5-110">Sandbox Indirect Provider – Delete Sandbox Indirect Reseller</span></span> 

<span data-ttu-id="6dbe5-111">Esta funcionalidade só está disponível na Sandbox e dá aos Fornecedores Indiretos sandbox a capacidade de criar revendedores indiretos sandbox.</span><span class="sxs-lookup"><span data-stu-id="6dbe5-111">This feature is only available in the Sandbox and gives Sandbox Indirect Providers an ability to create Sandbox Indirect Resellers.</span></span>

1. <span data-ttu-id="6dbe5-112">Pré-requisitos para a eliminação de um Revendedor Indireto Sandbox</span><span class="sxs-lookup"><span data-stu-id="6dbe5-112">Prerequisites for Deleting a Sandbox Indirect Reseller</span></span>
    1. <span data-ttu-id="6dbe5-113">Suspender as assinaturas para cada cliente da Sandbox Reseller Indirect</span><span class="sxs-lookup"><span data-stu-id="6dbe5-113">Suspend the subscriptions for each customer of Sandbox Indirect Reseller</span></span>
    2. <span data-ttu-id="6dbe5-114">Eliminar todos os clientes do Revendedor Indireto</span><span class="sxs-lookup"><span data-stu-id="6dbe5-114">Delete all customers of Indirect Reseller</span></span>
2. <span data-ttu-id="6dbe5-115">Limite de cinco Revendedores Indiretos Sandbox permitidos por Sandbox Indirect Provider.</span><span class="sxs-lookup"><span data-stu-id="6dbe5-115">Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> <span data-ttu-id="6dbe5-116">Uma vez eliminado o revendedor Sandbox Indirect, a quota será reposta.</span><span class="sxs-lookup"><span data-stu-id="6dbe5-116">Once the Sandbox Indirect reseller is deleted, the quota will be reset.</span></span>

## <a name="delete-sandbox-indirect-reseller-through-api"></a><span data-ttu-id="6dbe5-117">Eliminar Revendor Indireto Sandbox através da API</span><span class="sxs-lookup"><span data-stu-id="6dbe5-117">Delete Sandbox Indirect Reseller through API</span></span>

### <a name="rest-request"></a><span data-ttu-id="6dbe5-118">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6dbe5-118">REST request</span></span>

#### <a name="request-syntax"></a><span data-ttu-id="6dbe5-119">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6dbe5-119">Request syntax</span></span>

| <span data-ttu-id="6dbe5-120">Método</span><span class="sxs-lookup"><span data-stu-id="6dbe5-120">Method</span></span> | <span data-ttu-id="6dbe5-121">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6dbe5-121">Request URI</span></span>                                                                             |
|------------|-------------------------------------------------------------------------------------|
| <span data-ttu-id="6dbe5-122">**EXCLUIR**</span><span class="sxs-lookup"><span data-stu-id="6dbe5-122">**DELETE**</span></span> | <span data-ttu-id="6dbe5-123">[*{baseURL}*](partner-center-rest-urls.md)/v1//sandboxIndirectReseller/{revendedorD}</span><span class="sxs-lookup"><span data-stu-id="6dbe5-123">[*{baseURL}*](partner-center-rest-urls.md)/v1//sandboxIndirectReseller/{resellerId}</span></span> |

#### <a name="request-headers"></a><span data-ttu-id="6dbe5-124">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6dbe5-124">Request headers</span></span>

- <span data-ttu-id="6dbe5-125">Esta API é idempotente (não produzirá um resultado diferente se lhe chamar várias vezes)</span><span class="sxs-lookup"><span data-stu-id="6dbe5-125">This API is idempotent (it will not yield a different result if you call it multiple times)</span></span>
- <span data-ttu-id="6dbe5-126">É necessário um ID de pedido e uma iD de correlação</span><span class="sxs-lookup"><span data-stu-id="6dbe5-126">A request ID and correlation ID are required</span></span>
- <span data-ttu-id="6dbe5-127">Para mais informações, consulte [os cabeçalhos REST do Partner Center](headers.md)</span><span class="sxs-lookup"><span data-stu-id="6dbe5-127">For more information, see [Partner Center REST headers](headers.md)</span></span>

### <a name="request-example"></a><span data-ttu-id="6dbe5-128">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6dbe5-128">Request Example</span></span>

<span data-ttu-id="6dbe5-129">EXCLUIR https://api.partnercenter.microsoft.com/v1/sandboxIndirectReseller/{resellerID}</span><span class="sxs-lookup"><span data-stu-id="6dbe5-129">DELETE https://api.partnercenter.microsoft.com/v1/sandboxIndirectReseller/{resellerID}</span></span>

```http
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

####  <a name="response-example"></a><span data-ttu-id="6dbe5-130">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6dbe5-130">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Feb 2021 00:43:02 GMT
```

#### <a name="response-success-and-error-codes"></a><span data-ttu-id="6dbe5-131">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6dbe5-131">Response success and error codes</span></span>

<span data-ttu-id="6dbe5-132">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e outras informações de depurações.</span><span class="sxs-lookup"><span data-stu-id="6dbe5-132">Each response comes with an HTTP status code that indicates success or failure and other debugging information.</span></span> <span data-ttu-id="6dbe5-133">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6dbe5-133">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6dbe5-134">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6dbe5-134">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="6dbe5-135">Este método devolve os seguintes códigos de sucesso e erro:</span><span class="sxs-lookup"><span data-stu-id="6dbe5-135">This method returns the following status success and error codes:</span></span>

| <span data-ttu-id="6dbe5-136">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="6dbe5-136">HTTP Status Code</span></span>                     | <span data-ttu-id="6dbe5-137">Código de erro</span><span class="sxs-lookup"><span data-stu-id="6dbe5-137">Error code</span></span>     | <span data-ttu-id="6dbe5-138">Description</span><span class="sxs-lookup"><span data-stu-id="6dbe5-138">Description</span></span>                                      |
|--------------------------------------|----------------|--------------------------------------------------|
| <span data-ttu-id="6dbe5-139">401</span><span class="sxs-lookup"><span data-stu-id="6dbe5-139">401</span></span>                                  | <span data-ttu-id="6dbe5-140">6002</span><span class="sxs-lookup"><span data-stu-id="6dbe5-140">6002</span></span>           | <span data-ttu-id="6dbe5-141">Token não autorizado ou não uma conta de fornecedor de gorjeta</span><span class="sxs-lookup"><span data-stu-id="6dbe5-141">Unauthorized token or Not a Tip Provider Account</span></span> |
| <span data-ttu-id="6dbe5-142">403</span><span class="sxs-lookup"><span data-stu-id="6dbe5-142">403</span></span>                                  | <span data-ttu-id="6dbe5-143">6003</span><span class="sxs-lookup"><span data-stu-id="6dbe5-143">6003</span></span>           | <span data-ttu-id="6dbe5-144">Não é permitido eliminar o IR da Caixa de Areia</span><span class="sxs-lookup"><span data-stu-id="6dbe5-144">Delete Sandbox IR is not allowed</span></span>                 |
| <span data-ttu-id="6dbe5-145">403</span><span class="sxs-lookup"><span data-stu-id="6dbe5-145">403</span></span>                                  | <span data-ttu-id="6dbe5-146">6004</span><span class="sxs-lookup"><span data-stu-id="6dbe5-146">6004</span></span>           | <span data-ttu-id="6dbe5-147">Criar operação IR sandbox não permitida</span><span class="sxs-lookup"><span data-stu-id="6dbe5-147">Create Sandbox IR operation not allowed</span></span>          |
| <span data-ttu-id="6dbe5-148">409</span><span class="sxs-lookup"><span data-stu-id="6dbe5-148">409</span></span>                                  | <span data-ttu-id="6dbe5-149">1003</span><span class="sxs-lookup"><span data-stu-id="6dbe5-149">1003</span></span>           | <span data-ttu-id="6dbe5-150">Conflito ao criar inquilino</span><span class="sxs-lookup"><span data-stu-id="6dbe5-150">Conflict while creating tenant</span></span>                   |
