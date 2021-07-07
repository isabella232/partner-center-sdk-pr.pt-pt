---
title: Ativar uma subscrição de sandbox para produtos de mercado comercial
description: Saiba como usar as APIs do C/# e do Partner Center REST para ativar uma subscrição de sandbox para produtos de mercado comercial.
ms.date: 09/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b32c3e87462f58218771fc5da7da56ed177489cb
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025705"
---
# <a name="activate-a-sandbox-subscription-for-commercial-marketplace-saas-products-to-enable-billing"></a><span data-ttu-id="c381a-103">Ativar uma subscrição de sandbox para produtos SaaS de marketplace comercial para permitir faturação</span><span class="sxs-lookup"><span data-stu-id="c381a-103">Activate a sandbox subscription for commercial marketplace SaaS products to enable billing</span></span>

<span data-ttu-id="c381a-104">Como ativar uma subscrição para marketplace comercial Software como um serviço (SaaS) produtos de integração de contas de sandbox para permitir a faturação.</span><span class="sxs-lookup"><span data-stu-id="c381a-104">How to activate a subscription for commercial marketplace Software as a Service (SaaS) products from integration sandbox accounts to enable billing.</span></span>

> [!NOTE]
> <span data-ttu-id="c381a-105">Só é possível ativar uma subscrição de produtos SaaS de marketplace comercial a partir de contas de sandbox de integração.</span><span class="sxs-lookup"><span data-stu-id="c381a-105">It's only possible to activate a subscription for commercial marketplace SaaS products from integration sandbox accounts.</span></span> <span data-ttu-id="c381a-106">Se tiver uma subscrição de produção, deve visitar o site da editora para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c381a-106">If you have a production subscription, you must visit the publisher's site to complete the setup process.</span></span> <span data-ttu-id="c381a-107">A faturação da subscrição só começará depois de a configuração estar concluída.</span><span class="sxs-lookup"><span data-stu-id="c381a-107">Subscription billing will begin only after setup is complete.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c381a-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c381a-108">Prerequisites</span></span>

- <span data-ttu-id="c381a-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c381a-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c381a-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="c381a-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="c381a-111">Uma conta parceira de sandbox de integração com um cliente com uma subscrição ativa para produtos SaaS de marketplace comercial.</span><span class="sxs-lookup"><span data-stu-id="c381a-111">An integration sandbox partner account with a customer having an active subscription for commercial marketplace SaaS products.</span></span>

- <span data-ttu-id="c381a-112">Para os parceiros que utilizam o Partner Center .NET SDK, tem de utilizar a versão SDK 1.14.0 ou superior para aceder a esta capacidade.</span><span class="sxs-lookup"><span data-stu-id="c381a-112">For partners using Partner Center .NET SDK, you must use SDK version 1.14.0 or higher to access this capability.</span></span>

## <a name="c"></a><span data-ttu-id="c381a-113">C\#</span><span class="sxs-lookup"><span data-stu-id="c381a-113">C\#</span></span>

<span data-ttu-id="c381a-114">Utilize os seguintes passos para ativar uma subscrição de produtos SaaS de marketplace comercial:</span><span class="sxs-lookup"><span data-stu-id="c381a-114">Use the following steps to activate a subscription for commercial marketplace SaaS products:</span></span>

1. <span data-ttu-id="c381a-115">Disponibilizar uma interface às operações de subscrição.</span><span class="sxs-lookup"><span data-stu-id="c381a-115">Make an interface to the subscription operations available.</span></span> <span data-ttu-id="c381a-116">Deve identificar o cliente e especificar o identificador de subscrição da subscrição do ensaio.</span><span class="sxs-lookup"><span data-stu-id="c381a-116">You must identify the customer and specify the subscription identifier of the trial subscription.</span></span>

   ```csharp
   var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
   ```

2. <span data-ttu-id="c381a-117">Ative a subscrição utilizando a operação **Ativação.**</span><span class="sxs-lookup"><span data-stu-id="c381a-117">Activate the subscription using the **Activate** operation.</span></span>

   ```csharp
   var subscriptionActivationResult = subscriptionOperations.Activate();
   ```

## <a name="rest-request"></a><span data-ttu-id="c381a-118">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c381a-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c381a-119">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c381a-119">Request syntax</span></span>

| <span data-ttu-id="c381a-120">Método</span><span class="sxs-lookup"><span data-stu-id="c381a-120">Method</span></span>     | <span data-ttu-id="c381a-121">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c381a-121">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="c381a-122">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="c381a-122">**POST**</span></span> | <span data-ttu-id="c381a-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{subscrição-id}/ativar HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c381a-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/activate HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="c381a-124">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="c381a-124">URI parameter</span></span>

| <span data-ttu-id="c381a-125">Nome</span><span class="sxs-lookup"><span data-stu-id="c381a-125">Name</span></span>                   | <span data-ttu-id="c381a-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="c381a-126">Type</span></span>     | <span data-ttu-id="c381a-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="c381a-127">Required</span></span> | <span data-ttu-id="c381a-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="c381a-128">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c381a-129">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="c381a-129">**customer-tenant-id**</span></span> | <span data-ttu-id="c381a-130">**guid**</span><span class="sxs-lookup"><span data-stu-id="c381a-130">**guid**</span></span> | <span data-ttu-id="c381a-131">Y</span><span class="sxs-lookup"><span data-stu-id="c381a-131">Y</span></span> | <span data-ttu-id="c381a-132">O valor é um identificador de inquilino de clientes com formato GUID (**cliente-inquilino-id),** que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="c381a-132">The value is a GUID-formatted customer tenant identifier (**customer-tenant-id**), which allows you to specify a customer.</span></span> |
| <span data-ttu-id="c381a-133">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="c381a-133">**subscription-id**</span></span> | <span data-ttu-id="c381a-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="c381a-134">**guid**</span></span> | <span data-ttu-id="c381a-135">Y</span><span class="sxs-lookup"><span data-stu-id="c381a-135">Y</span></span> | <span data-ttu-id="c381a-136">O valor é um identificador de subscrição formatado guid **(id de subscrição),** que lhe permite especificar uma subscrição.</span><span class="sxs-lookup"><span data-stu-id="c381a-136">The value is a GUID-formatted subscription identifier (**subscription-id**), which allows you to specify a subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c381a-137">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c381a-137">Request headers</span></span>

<span data-ttu-id="c381a-138">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c381a-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c381a-139">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="c381a-139">Request body</span></span>

<span data-ttu-id="c381a-140">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c381a-140">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c381a-141">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c381a-141">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/42b5f772-5c5c-4bce-b9d7-bdadeecca411/subscriptions/87363db7-39ab-dd25-d371-94340aaa2f97/activate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

```

## <a name="rest-response"></a><span data-ttu-id="c381a-142">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c381a-142">REST response</span></span>

<span data-ttu-id="c381a-143">Este método devolve as propriedades **de id de subscrição** e **status.**</span><span class="sxs-lookup"><span data-stu-id="c381a-143">This method returns the **subscription-id** and **status** properties.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c381a-144">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c381a-144">Response success and error codes</span></span>

<span data-ttu-id="c381a-145">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c381a-145">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c381a-146">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c381a-146">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c381a-147">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c381a-147">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c381a-148">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="c381a-148">Response example</span></span>

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
