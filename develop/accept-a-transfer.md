---
title: Aceitar uma transferência de subscrições
description: Saiba como utilizar a API do Partner Center REST para aceitar uma transferência de subscrições para um cliente. Inclui sintaxe de pedido de REST, cabeçalhos e respostas REST.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fd9a6788b3dd022470e516ba928a6cd873970e53
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "97769962"
---
# <a name="accept-a-transfer-of-subscriptions-for-a-customer-using-partner-center-rest-apis"></a><span data-ttu-id="aa7c4-104">Aceitar uma transferência de subscrições para um cliente usando As APIs do Partner Center REST</span><span class="sxs-lookup"><span data-stu-id="aa7c4-104">Accept a transfer of subscriptions for a customer using Partner Center REST APIs</span></span>

<span data-ttu-id="aa7c4-105">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="aa7c4-105">**Applies to:**</span></span>

- <span data-ttu-id="aa7c4-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="aa7c4-106">Partner Center</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aa7c4-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="aa7c4-107">Prerequisites</span></span>

- <span data-ttu-id="aa7c4-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="aa7c4-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="aa7c4-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="aa7c4-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="aa7c4-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="aa7c4-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="aa7c4-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="aa7c4-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="aa7c4-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="aa7c4-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="aa7c4-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="aa7c4-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="aa7c4-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="aa7c4-116">Um identificador de transferência para uma transferência existente.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-116">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="aa7c4-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="aa7c4-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="aa7c4-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa7c4-118">Request syntax</span></span>

| <span data-ttu-id="aa7c4-119">Método</span><span class="sxs-lookup"><span data-stu-id="aa7c4-119">Method</span></span>   | <span data-ttu-id="aa7c4-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="aa7c4-120">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="aa7c4-121">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="aa7c4-121">**POST**</span></span> | <span data-ttu-id="aa7c4-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/transfers/{transfer-id}/aceitar HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="aa7c4-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id}/accept HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="aa7c4-123">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="aa7c4-123">URI parameter</span></span>

<span data-ttu-id="aa7c4-124">Utilize o seguinte parâmetro de percurso para identificar o cliente e especificar a transferência a aceitar.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-124">Use the following path parameter to identify the customer and specify the transfer to be accepted.</span></span>

| <span data-ttu-id="aa7c4-125">Nome</span><span class="sxs-lookup"><span data-stu-id="aa7c4-125">Name</span></span>            | <span data-ttu-id="aa7c4-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="aa7c4-126">Type</span></span>     | <span data-ttu-id="aa7c4-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="aa7c4-127">Required</span></span> | <span data-ttu-id="aa7c4-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa7c4-128">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="aa7c4-129">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="aa7c4-129">**customer-id**</span></span> | <span data-ttu-id="aa7c4-130">string</span><span class="sxs-lookup"><span data-stu-id="aa7c4-130">string</span></span>   | <span data-ttu-id="aa7c4-131">Sim</span><span class="sxs-lookup"><span data-stu-id="aa7c4-131">Yes</span></span>      | <span data-ttu-id="aa7c4-132">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-132">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="aa7c4-133">**transferência id**</span><span class="sxs-lookup"><span data-stu-id="aa7c4-133">**transfer-id**</span></span> | <span data-ttu-id="aa7c4-134">string</span><span class="sxs-lookup"><span data-stu-id="aa7c4-134">string</span></span>   | <span data-ttu-id="aa7c4-135">Sim</span><span class="sxs-lookup"><span data-stu-id="aa7c4-135">Yes</span></span>      | <span data-ttu-id="aa7c4-136">Um id de transferência formatado GUID que identifica a transferência.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-136">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="aa7c4-137">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="aa7c4-137">Request headers</span></span>

<span data-ttu-id="aa7c4-138">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="aa7c4-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-example"></a><span data-ttu-id="aa7c4-139">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="aa7c4-139">Request example</span></span>

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers/aa2bddb6-9cc8-4949-80fe-a37d5e0a13ba/accept HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 4827b753-8541-428b-8c90-059b6b4851bd
MS-RequestId: 8389053b-731c-4261-9899-1583d7859153
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 0

```

## <a name="rest-response"></a><span data-ttu-id="aa7c4-140">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="aa7c4-140">REST response</span></span>

<span data-ttu-id="aa7c4-141">Se for bem sucedido, este método devolve o recurso [TransferSubmitResult](transfer-entity-resources.md#transfersubmitresult) povoado no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-141">If successful, this method returns the populated [TransferSubmitResult](transfer-entity-resources.md#transfersubmitresult) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="aa7c4-142">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="aa7c4-142">Response success and error codes</span></span>

<span data-ttu-id="aa7c4-143">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="aa7c4-144">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="aa7c4-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="aa7c4-145">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="aa7c4-145">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="aa7c4-146">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="aa7c4-146">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 3389
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4827b753-8541-428b-8c90-059b6b4851bd
MS-RequestId: 8389053b-731c-4261-9899-1583d7859153
X-Locale: en-US
Date: Wed, 25 Mar 2020 19:13:06 GMT

{
  "orders": [
    {
      "id": "21b92393-ffce-4bc7-87c5-62cfa897d8f9",
      "alternateId": "21b92393-ffce-4bc7-87c5-62cfa897d8f9",
      "referenceCustomerId": "b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0",
      "billingCycle": "annual",
      "currencyCode": "USD",
      "lineItems": [
        {
          "lineItemNumber": 0,
          "offerId": "5344C201-3099-44E5-B333-C3EB0401EDE0",
          "termDuration": "P1Y",
          "transactionType": "New",
          "friendlyName": "Dynamics 365 Customer Engagement Plan (36 mo)",
          "quantity": 1,
          "partnerIdOnRecord": "5139005",
          "links": {
          }
        }
      ],
      "creationDate": "2020-03-25T22:24:23.183+00:00",
      "status": "completed",
      "transactionType": "UserPurchase",
      "links": {
        "self": {
          "uri": "/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/orders/21b92393-ffce-4bc7-87c5-62cfa897d8f9",
          "method": "GET",
          "headers": [ ]
        },
        "patchOperation": {
          "uri": "/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/orders/21b92393-ffce-4bc7-87c5-62cfa897d8f9",
          "method": "PATCH",
          "headers": [ ]
        }
      },
      "attributes": {
        "etag": "eyJpZCI6IjIxYjkyMzkzLWZmY2UtNGJjNy04N2M1LTYyY2ZhODk3ZDhmOSIsInZlcnNpb24iOjF9",
        "objectType": "Order"
      }
    },
    {
      "id": "7414b8ea-c167-4cc4-bc8e-b43efc177a46",
      "alternateId": "7414b8ea-c167-4cc4-bc8e-b43efc177a46",
      "referenceCustomerId": "b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0",
      "billingCycle": "annual",
      "currencyCode": "USD",
      "lineItems": [
        {
          "lineItemNumber": 0,
          "offerId": "1A90EE13-2CB4-4785-BB0F-542813F00A37",
          "termDuration": "P1Y",
          "transactionType": "New",
          "friendlyName": "Dynamics 365 Business Central Essential",
          "quantity": 1,
          "partnerIdOnRecord": "5139005",
          "links": {
          }
        }
      ],
      "creationDate": "2020-03-25T22:24:34.59+00:00",
      "status": "completed",
      "transactionType": "UserPurchase",
      "links": {
        "self": {
          "uri": "/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/orders/7414b8ea-c167-4cc4-bc8e-b43efc177a46",
          "method": "GET",
          "headers": [ ]
        },
        "patchOperation": {
          "uri": "/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/orders/7414b8ea-c167-4cc4-bc8e-b43efc177a46",
          "method": "PATCH",
          "headers": [ ]
        }
      },
      "attributes": {
        "etag": "eyJpZCI6Ijc0MTRiOGVhLWMxNjctNGNjNC1iYzhlLWI0M2VmYzE3N2E0NiIsInZlcnNpb24iOjF9",
        "objectType": "Order"
      }
    }
  ],
  "transferErrors": [
    {
      "transferGroupId": "1",
      "lineItems": [
        {
          "id": 1,
          "subscriptionId": "637FF8F6-D842-4573-8DA8-89765356CD1A",
          "entitlementId": "637FF8F6-D842-4573-8DA8-89765356CD1A",
          "offerId": "A4179D30-CC09-49F0-977E-DC2CB70B874F",
          "friendlyName": "Project Online Essentials",
          "quantity": 1,
          "transferGroupId": "1",
          "addonItems": [ ],
          "partnerIdOnRecord": "5139005",
          "billingCycle": "annual",
          "sourceSubscriptionId": "637FF8F6-D842-4573-8DA8-89765356CD1A"
        }
      ],
      "code": 900103,
      "description": "Subscription SyncState must be SyncComplete for the Subscription to be a source in a Subscription Ownership Transfer. Subscription: 637ff8f6-d842-4573-8da8-89765356cd1a, current state: None",
      "attributes": {
        "objectType": "TransferError"
      }
    }
  ],
  "attributes": {
    "objectType": "TransferSubmitResult"
  }
}
```
