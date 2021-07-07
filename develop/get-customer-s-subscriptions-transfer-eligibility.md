---
title: Obter a elegibilidade de transferência de subscrições de um cliente
description: Como obter uma coleção de subscrições de um cliente que são elegíveis/ineligibile para transferência.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: fe8af76d1e1456754dec79291ec0853fb253d108
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446297"
---
# <a name="get-a-customers-subscriptions-transfer-eligibility"></a><span data-ttu-id="4f085-103">Obter a elegibilidade de transferência de subscrições de um cliente</span><span class="sxs-lookup"><span data-stu-id="4f085-103">Get a customer's subscriptions transfer eligibility</span></span>

<span data-ttu-id="4f085-104">Como obter uma coleção de subscrições de um cliente que são elegíveis/inelegíveis para transferência.</span><span class="sxs-lookup"><span data-stu-id="4f085-104">How to get a collection of a customer's subscriptions that are eligible/ineligible for transfer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4f085-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4f085-105">Prerequisites</span></span>

- <span data-ttu-id="4f085-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4f085-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4f085-107">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="4f085-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="4f085-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4f085-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4f085-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="4f085-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4f085-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="4f085-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4f085-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="4f085-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4f085-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="4f085-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4f085-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4f085-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="4f085-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="4f085-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4f085-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f085-115">Request syntax</span></span>

| <span data-ttu-id="4f085-116">Método</span><span class="sxs-lookup"><span data-stu-id="4f085-116">Method</span></span>  | <span data-ttu-id="4f085-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="4f085-117">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4f085-118">**Obter**</span><span class="sxs-lookup"><span data-stu-id="4f085-118">**GET**</span></span> | <span data-ttu-id="4f085-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/transferseligibility?transferType={transfer-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4f085-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/transferseligibility?transferType={transfer-type} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="4f085-120">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="4f085-120">URI parameter</span></span>

<span data-ttu-id="4f085-121">Esta tabela lista o parâmetro de consulta necessário para obter todas as subscrições.</span><span class="sxs-lookup"><span data-stu-id="4f085-121">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="4f085-122">Nome</span><span class="sxs-lookup"><span data-stu-id="4f085-122">Name</span></span>               | <span data-ttu-id="4f085-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="4f085-123">Type</span></span>   | <span data-ttu-id="4f085-124">Necessário</span><span class="sxs-lookup"><span data-stu-id="4f085-124">Required</span></span> | <span data-ttu-id="4f085-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f085-125">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="4f085-126">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="4f085-126">customer-tenant-id</span></span> | <span data-ttu-id="4f085-127">string</span><span class="sxs-lookup"><span data-stu-id="4f085-127">string</span></span> | <span data-ttu-id="4f085-128">Yes</span><span class="sxs-lookup"><span data-stu-id="4f085-128">Yes</span></span>      | <span data-ttu-id="4f085-129">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="4f085-129">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="4f085-130">tipo de transferência</span><span class="sxs-lookup"><span data-stu-id="4f085-130">transfer-type</span></span>      | <span data-ttu-id="4f085-131">string</span><span class="sxs-lookup"><span data-stu-id="4f085-131">string</span></span> | <span data-ttu-id="4f085-132">Yes</span><span class="sxs-lookup"><span data-stu-id="4f085-132">Yes</span></span>      | <span data-ttu-id="4f085-133">O tipo de transferência que se destina.</span><span class="sxs-lookup"><span data-stu-id="4f085-133">The type of transfer that is intended.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="4f085-134">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="4f085-134">Request headers</span></span>

<span data-ttu-id="4f085-135">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4f085-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4f085-136">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="4f085-136">Request body</span></span>

<span data-ttu-id="4f085-137">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4f085-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="4f085-138">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="4f085-138">Request example</span></span>

```http
GET /v1/customers/823c6c3f-9259-4d51-bae2-5dd06743177f/transferseligibility?transferType=directtoindirect HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 202b5e9a-ae82-4ab9-8a0a-f4e9e04eb14d
MS-CorrelationId: cd589c16-dc94-49ad-e529-125c258573d6
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="4f085-139">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="4f085-139">REST response</span></span>

<span data-ttu-id="4f085-140">Se for bem sucedido, este método devolve uma coleção de recursos de [transfereelegibilidade](transfer-eligibility-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="4f085-140">If successful, this method returns a collection of [TransferEligibility](transfer-eligibility-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4f085-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="4f085-141">Response success and error codes</span></span>

<span data-ttu-id="4f085-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="4f085-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4f085-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4f085-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4f085-144">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4f085-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4f085-145">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="4f085-145">Response example</span></span>

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
