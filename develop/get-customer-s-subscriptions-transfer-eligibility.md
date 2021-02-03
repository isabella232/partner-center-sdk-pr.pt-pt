---
title: Obter a elegibilidade de transferência de subscrições de um cliente
description: Como obter uma coleção de subscrições de um cliente que são elegíveis/ineligibile para transferência.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 43086a32fa0dbbdecf65aac167c687f26fc4c2c6
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768743"
---
# <a name="get-a-customers-subscriptions-transfer-eligibility"></a><span data-ttu-id="662ca-103">Obter a elegibilidade de transferência de subscrições de um cliente</span><span class="sxs-lookup"><span data-stu-id="662ca-103">Get a customer's subscriptions transfer eligibility</span></span>

<span data-ttu-id="662ca-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="662ca-104">**Applies To**</span></span>

- <span data-ttu-id="662ca-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="662ca-105">Partner Center</span></span>

<span data-ttu-id="662ca-106">Como obter uma coleção de subscrições de um cliente que são elegíveis/inelegíveis para transferência.</span><span class="sxs-lookup"><span data-stu-id="662ca-106">How to get a collection of a customer's subscriptions that are eligible/ineligible for transfer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="662ca-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="662ca-107">Prerequisites</span></span>

- <span data-ttu-id="662ca-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="662ca-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="662ca-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="662ca-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="662ca-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="662ca-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="662ca-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="662ca-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="662ca-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="662ca-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="662ca-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="662ca-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="662ca-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="662ca-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="662ca-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="662ca-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="662ca-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="662ca-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="662ca-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="662ca-117">Request syntax</span></span>

| <span data-ttu-id="662ca-118">Método</span><span class="sxs-lookup"><span data-stu-id="662ca-118">Method</span></span>  | <span data-ttu-id="662ca-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="662ca-119">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="662ca-120">**Obter**</span><span class="sxs-lookup"><span data-stu-id="662ca-120">**GET**</span></span> | <span data-ttu-id="662ca-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/transferseligibility?transferType={transfer-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="662ca-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/transferseligibility?transferType={transfer-type} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="662ca-122">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="662ca-122">URI parameter</span></span>

<span data-ttu-id="662ca-123">Esta tabela lista o parâmetro de consulta necessário para obter todas as subscrições.</span><span class="sxs-lookup"><span data-stu-id="662ca-123">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="662ca-124">Nome</span><span class="sxs-lookup"><span data-stu-id="662ca-124">Name</span></span>               | <span data-ttu-id="662ca-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="662ca-125">Type</span></span>   | <span data-ttu-id="662ca-126">Necessário</span><span class="sxs-lookup"><span data-stu-id="662ca-126">Required</span></span> | <span data-ttu-id="662ca-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="662ca-127">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="662ca-128">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="662ca-128">customer-tenant-id</span></span> | <span data-ttu-id="662ca-129">string</span><span class="sxs-lookup"><span data-stu-id="662ca-129">string</span></span> | <span data-ttu-id="662ca-130">Sim</span><span class="sxs-lookup"><span data-stu-id="662ca-130">Yes</span></span>      | <span data-ttu-id="662ca-131">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="662ca-131">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="662ca-132">tipo de transferência</span><span class="sxs-lookup"><span data-stu-id="662ca-132">transfer-type</span></span>      | <span data-ttu-id="662ca-133">string</span><span class="sxs-lookup"><span data-stu-id="662ca-133">string</span></span> | <span data-ttu-id="662ca-134">Sim</span><span class="sxs-lookup"><span data-stu-id="662ca-134">Yes</span></span>      | <span data-ttu-id="662ca-135">O tipo de transferência que se destina.</span><span class="sxs-lookup"><span data-stu-id="662ca-135">The type of transfer that is intended.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="662ca-136">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="662ca-136">Request headers</span></span>

<span data-ttu-id="662ca-137">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="662ca-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="662ca-138">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="662ca-138">Request body</span></span>

<span data-ttu-id="662ca-139">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="662ca-139">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="662ca-140">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="662ca-140">Request example</span></span>

```http
GET /v1/customers/823c6c3f-9259-4d51-bae2-5dd06743177f/transferseligibility?transferType=directtoindirect HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 202b5e9a-ae82-4ab9-8a0a-f4e9e04eb14d
MS-CorrelationId: cd589c16-dc94-49ad-e529-125c258573d6
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="662ca-141">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="662ca-141">REST response</span></span>

<span data-ttu-id="662ca-142">Se for bem sucedido, este método devolve uma coleção de recursos de [transfereelegibilidade](transfer-eligibility-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="662ca-142">If successful, this method returns a collection of [TransferEligibility](transfer-eligibility-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="662ca-143">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="662ca-143">Response success and error codes</span></span>

<span data-ttu-id="662ca-144">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="662ca-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="662ca-145">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="662ca-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="662ca-146">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="662ca-146">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="662ca-147">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="662ca-147">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: cd589c16-dc94-49ad-e529-125c258573d6
MS-RequestId: 202b5e9a-ae82-4ab9-8a0a-f4e9e04eb14d
Date: Tue, 24 Mar 2020 23:43:25 GMT

[
  {
    "id": "548FA265-5F40-4765-9A6B-47826F72A4BF",
    "isEligible": false,
    "reason": "Subscription: 548FA265-5F40-4765-9A6B-47826F72A4BF is in state: Deleted"
  },
  {
    "id": "E2A3AEB3-70A7-42E3-930C-7519EEDDC45A",
    "isEligible": false,
    "reason": "Subscription: E2A3AEB3-70A7-42E3-930C-7519EEDDC45A is in state: Suspended"
  },
  {
    "id": "4B600A9A-DF56-4564-A75A-6CC6D2D0C9F9",
    "isEligible": false,
    "reason": "subscription is already part of another transfer request id : 31a06eac-c527-458a-a6b4-0de197a45996"
  },
  {
    "id": "D3350F46-AA29-4F6F-95A0-E3011988915C",
    "isEligible": true
  }
  {
    "id": "E82B2F4A-736A-4E2B-955C-C1A4C56C0171",
    "isEligible": true
  }
]
```
