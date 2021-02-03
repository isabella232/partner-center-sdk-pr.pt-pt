---
title: Ativar uma subscrição de sandbox para produtos de mercado comercial
description: Saiba como usar as APIs do C/# e do Partner Center REST para ativar uma subscrição de sandbox para produtos de mercado comercial.
ms.date: 09/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a78b2c84368b29f1378f46971c4814929094e299
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "97769950"
---
# <a name="activate-a-sandbox-subscription-for-commercial-marketplace-saas-products-to-enable-billing"></a><span data-ttu-id="725cf-103">Ativar uma subscrição de sandbox para produtos SaaS de marketplace comercial para permitir faturação</span><span class="sxs-lookup"><span data-stu-id="725cf-103">Activate a sandbox subscription for commercial marketplace SaaS products to enable billing</span></span>

<span data-ttu-id="725cf-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="725cf-104">**Applies to:**</span></span>

- <span data-ttu-id="725cf-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="725cf-105">Partner Center</span></span>

<span data-ttu-id="725cf-106">Como ativar uma subscrição para marketplace comercial Software como um serviço (SaaS) produtos de integração de contas de sandbox para permitir a faturação.</span><span class="sxs-lookup"><span data-stu-id="725cf-106">How to activate a subscription for commercial marketplace Software as a Service (SaaS) products from integration sandbox accounts to enable billing.</span></span>

> [!NOTE]
> <span data-ttu-id="725cf-107">Só é possível ativar uma subscrição de produtos SaaS de marketplace comercial a partir de contas de sandbox de integração.</span><span class="sxs-lookup"><span data-stu-id="725cf-107">It's only possible to activate a subscription for commercial marketplace SaaS products from integration sandbox accounts.</span></span> <span data-ttu-id="725cf-108">Se tiver uma subscrição de produção, deve visitar o site da editora para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="725cf-108">If you have a production subscription, you must visit the publisher's site to complete the setup process.</span></span> <span data-ttu-id="725cf-109">A faturação da subscrição só começará depois de a configuração estar concluída.</span><span class="sxs-lookup"><span data-stu-id="725cf-109">Subscription billing will begin only after setup is complete.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="725cf-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="725cf-110">Prerequisites</span></span>

- <span data-ttu-id="725cf-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="725cf-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="725cf-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="725cf-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="725cf-113">Uma conta parceira de sandbox de integração com um cliente com uma subscrição ativa para produtos SaaS de marketplace comercial.</span><span class="sxs-lookup"><span data-stu-id="725cf-113">An integration sandbox partner account with a customer having an active subscription for commercial marketplace SaaS products.</span></span>

- <span data-ttu-id="725cf-114">Para os parceiros que utilizam o Partner Center .NET SDK, tem de utilizar a versão SDK 1.14.0 ou superior para aceder a esta capacidade.</span><span class="sxs-lookup"><span data-stu-id="725cf-114">For partners using Partner Center .NET SDK, you must use SDK version 1.14.0 or higher to access this capability.</span></span>

## <a name="c"></a><span data-ttu-id="725cf-115">C\#</span><span class="sxs-lookup"><span data-stu-id="725cf-115">C\#</span></span>

<span data-ttu-id="725cf-116">Utilize os seguintes passos para ativar uma subscrição de produtos SaaS de marketplace comercial:</span><span class="sxs-lookup"><span data-stu-id="725cf-116">Use the following steps to activate a subscription for commercial marketplace SaaS products:</span></span>

1. <span data-ttu-id="725cf-117">Disponibilizar uma interface às operações de subscrição.</span><span class="sxs-lookup"><span data-stu-id="725cf-117">Make an interface to the subscription operations available.</span></span> <span data-ttu-id="725cf-118">Deve identificar o cliente e especificar o identificador de subscrição da subscrição do ensaio.</span><span class="sxs-lookup"><span data-stu-id="725cf-118">You must identify the customer and specify the subscription identifier of the trial subscription.</span></span>

   ```csharp
   var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
   ```

2. <span data-ttu-id="725cf-119">Ative a subscrição utilizando a operação **Ativação.**</span><span class="sxs-lookup"><span data-stu-id="725cf-119">Activate the subscription using the **Activate** operation.</span></span>

   ```csharp
   var subscriptionActivationResult = subscriptionOperations.Activate();
   ```

## <a name="rest-request"></a><span data-ttu-id="725cf-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="725cf-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="725cf-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="725cf-121">Request syntax</span></span>

| <span data-ttu-id="725cf-122">Método</span><span class="sxs-lookup"><span data-stu-id="725cf-122">Method</span></span>     | <span data-ttu-id="725cf-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="725cf-123">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="725cf-124">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="725cf-124">**POST**</span></span> | <span data-ttu-id="725cf-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/ativar HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="725cf-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/activate HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="725cf-126">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="725cf-126">URI parameter</span></span>

| <span data-ttu-id="725cf-127">Nome</span><span class="sxs-lookup"><span data-stu-id="725cf-127">Name</span></span>                   | <span data-ttu-id="725cf-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="725cf-128">Type</span></span>     | <span data-ttu-id="725cf-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="725cf-129">Required</span></span> | <span data-ttu-id="725cf-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="725cf-130">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="725cf-131">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="725cf-131">**customer-tenant-id**</span></span> | <span data-ttu-id="725cf-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="725cf-132">**guid**</span></span> | <span data-ttu-id="725cf-133">Y</span><span class="sxs-lookup"><span data-stu-id="725cf-133">Y</span></span> | <span data-ttu-id="725cf-134">O valor é um identificador de inquilino de clientes com formato GUID (**cliente-inquilino-id),** que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="725cf-134">The value is a GUID-formatted customer tenant identifier (**customer-tenant-id**), which allows you to specify a customer.</span></span> |
| <span data-ttu-id="725cf-135">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="725cf-135">**subscription-id**</span></span> | <span data-ttu-id="725cf-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="725cf-136">**guid**</span></span> | <span data-ttu-id="725cf-137">Y</span><span class="sxs-lookup"><span data-stu-id="725cf-137">Y</span></span> | <span data-ttu-id="725cf-138">O valor é um identificador de subscrição formatado guid **(id de subscrição),** que lhe permite especificar uma subscrição.</span><span class="sxs-lookup"><span data-stu-id="725cf-138">The value is a GUID-formatted subscription identifier (**subscription-id**), which allows you to specify a subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="725cf-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="725cf-139">Request headers</span></span>

<span data-ttu-id="725cf-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="725cf-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="725cf-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="725cf-141">Request body</span></span>

<span data-ttu-id="725cf-142">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="725cf-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="725cf-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="725cf-143">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/42b5f772-5c5c-4bce-b9d7-bdadeecca411/subscriptions/87363db7-39ab-dd25-d371-94340aaa2f97/activate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

```

## <a name="rest-response"></a><span data-ttu-id="725cf-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="725cf-144">REST response</span></span>

<span data-ttu-id="725cf-145">Este método devolve as propriedades **de id de subscrição** e **status.**</span><span class="sxs-lookup"><span data-stu-id="725cf-145">This method returns the **subscription-id** and **status** properties.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="725cf-146">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="725cf-146">Response success and error codes</span></span>

<span data-ttu-id="725cf-147">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="725cf-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="725cf-148">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="725cf-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="725cf-149">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="725cf-149">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="725cf-150">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="725cf-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 79
Content-Type: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "subscriptionId":"87363db7-39ab-dd25-d371-94340aaa2f97",
    "status":"Success"
}
```
