---
title: Obter uma lista de elegibilidade do Azure para uma subscrição
description: Você pode usar o recurso AzureEntitlement para obter uma coleção de recursos de direito Azure que pertencem a uma subscrição.
ms.date: 07/06/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 280da155122ed9efd99838d7819fb34f8f7ec52c
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874368"
---
# <a name="get-a-list-of-azure-entitlements-for-a-subscription"></a><span data-ttu-id="a8248-103">Obter uma lista de elegibilidade do Azure para uma subscrição</span><span class="sxs-lookup"><span data-stu-id="a8248-103">Get a list of Azure entitlements for a subscription</span></span>

<span data-ttu-id="a8248-104">Você pode usar o [recurso de direito Azure](subscription-resources.md#azureentitlement) **(AzureEntitlement**) para obter uma coleção de recursos que pertencem a uma subscrição.</span><span class="sxs-lookup"><span data-stu-id="a8248-104">You can use the [Azure entitlement resource](subscription-resources.md#azureentitlement) (**AzureEntitlement**) to get a collection of resources that belong to a subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8248-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a8248-105">Prerequisites</span></span>

- <span data-ttu-id="a8248-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a8248-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a8248-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="a8248-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="a8248-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a8248-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a8248-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="a8248-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a8248-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="a8248-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a8248-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="a8248-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a8248-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="a8248-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a8248-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a8248-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="a8248-114">Um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="a8248-114">A subscription identifier.</span></span>

## <a name="rest-request"></a><span data-ttu-id="a8248-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="a8248-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a8248-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8248-116">Request syntax</span></span>

| <span data-ttu-id="a8248-117">Método</span><span class="sxs-lookup"><span data-stu-id="a8248-117">Method</span></span>  | <span data-ttu-id="a8248-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="a8248-118">Request URI</span></span>                                                                                                                   |
|---------|---------------------------------------------------------------------------------|
| <span data-ttu-id="a8248-119">**Obter**</span><span class="sxs-lookup"><span data-stu-id="a8248-119">**GET**</span></span> | <span data-ttu-id="a8248-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscrições/{subscription-id}/azureentitledments HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a8248-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/azureentitlements HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="a8248-121">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="a8248-121">URI parameters</span></span>

<span data-ttu-id="a8248-122">A tabela que se segue lista os parâmetros de consulta necessários para obter todos os direitos Azure para uma subscrição.</span><span class="sxs-lookup"><span data-stu-id="a8248-122">The following table lists the required query parameters to get all the Azure entitlements for a subscription.</span></span>

| <span data-ttu-id="a8248-123">Nome</span><span class="sxs-lookup"><span data-stu-id="a8248-123">Name</span></span>                   | <span data-ttu-id="a8248-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="a8248-124">Type</span></span>     | <span data-ttu-id="a8248-125">Necessário</span><span class="sxs-lookup"><span data-stu-id="a8248-125">Required</span></span> | <span data-ttu-id="a8248-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8248-126">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="a8248-127">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="a8248-127">**customer-tenant-id**</span></span> | <span data-ttu-id="a8248-128">**guid**</span><span class="sxs-lookup"><span data-stu-id="a8248-128">**guid**</span></span> | <span data-ttu-id="a8248-129">Y</span><span class="sxs-lookup"><span data-stu-id="a8248-129">Y</span></span>        | <span data-ttu-id="a8248-130">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="a8248-130">A GUID corresponding to the customer.</span></span> |
| <span data-ttu-id="a8248-131">**id de subscrição**</span><span class="sxs-lookup"><span data-stu-id="a8248-131">**subscription-id**</span></span>       | <span data-ttu-id="a8248-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="a8248-132">**guid**</span></span> | <span data-ttu-id="a8248-133">Y</span><span class="sxs-lookup"><span data-stu-id="a8248-133">Y</span></span>        | <span data-ttu-id="a8248-134">Um GUID correspondente à subscrição.</span><span class="sxs-lookup"><span data-stu-id="a8248-134">A GUID corresponding to the subscription.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="a8248-135">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="a8248-135">Request headers</span></span>

<span data-ttu-id="a8248-136">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a8248-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a8248-137">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="a8248-137">Request body</span></span>

<span data-ttu-id="a8248-138">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a8248-138">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="a8248-139">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a8248-139">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/11f9bc2a-1f38-431c-a0b0-9455c6f5bbc0/subscriptions/3f15978e-005c-b763-bb78-2a8fab289c58/azureEntitlements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="a8248-140">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="a8248-140">REST response</span></span>

<span data-ttu-id="a8248-141">Se for bem sucedido, este método devolve uma coleção de recursos [**AzureEntitlement**](subscription-resources.md#azureentitlement) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="a8248-141">If successful, this method returns a collection of [**AzureEntitlement**](subscription-resources.md#azureentitlement) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a8248-142">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="a8248-142">Response success and error codes</span></span>

<span data-ttu-id="a8248-143">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="a8248-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a8248-144">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="a8248-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a8248-145">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="a8248-145">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a8248-146">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a8248-146">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
Date: Wed, 04 Oct 2019 05:50:45 GMT

{
"totalCount":1,
"items":[
  {
    "id":"899ae6f1-8a74-4d5e-b6c6-e6b5019bbff8",
    "friendlyName":"Microsoft Azure",
    "status":"active",
    "subscriptionId":"3f15978e-005c-b763-bb78-2a8fab289c58"
   }],
    "attributes":{"objectType":"Collection"}
  }
```
