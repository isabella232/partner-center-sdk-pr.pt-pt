---
title: Rejeitar uma transferência
description: Como rejeitar uma transferência de subscrições para um cliente.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d09905979a89c9b2092462512c485524cd681d5f
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445379"
---
# <a name="reject-a-transfer"></a><span data-ttu-id="023cd-103">Rejeitar uma transferência</span><span class="sxs-lookup"><span data-stu-id="023cd-103">Reject a transfer</span></span>

## <a name="prerequisites"></a><span data-ttu-id="023cd-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="023cd-104">Prerequisites</span></span>

- <span data-ttu-id="023cd-105">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="023cd-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="023cd-106">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="023cd-106">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="023cd-107">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="023cd-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="023cd-108">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="023cd-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="023cd-109">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="023cd-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="023cd-110">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="023cd-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="023cd-111">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="023cd-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="023cd-112">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="023cd-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="023cd-113">Um identificador de transferência para uma transferência existente.</span><span class="sxs-lookup"><span data-stu-id="023cd-113">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="023cd-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="023cd-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="023cd-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="023cd-115">Request syntax</span></span>

| <span data-ttu-id="023cd-116">Método</span><span class="sxs-lookup"><span data-stu-id="023cd-116">Method</span></span>   | <span data-ttu-id="023cd-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="023cd-117">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="023cd-118">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="023cd-118">**PATCH**</span></span> | <span data-ttu-id="023cd-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/transfers/{transfer-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="023cd-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="023cd-120">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="023cd-120">URI parameter</span></span>

<span data-ttu-id="023cd-121">Utilize o seguinte parâmetro de percurso para identificar o cliente e especificar a transferência a aceitar.</span><span class="sxs-lookup"><span data-stu-id="023cd-121">Use the following path parameter to identify the customer and specify the transfer to be accepted.</span></span>

| <span data-ttu-id="023cd-122">Nome</span><span class="sxs-lookup"><span data-stu-id="023cd-122">Name</span></span>            | <span data-ttu-id="023cd-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="023cd-123">Type</span></span>     | <span data-ttu-id="023cd-124">Necessário</span><span class="sxs-lookup"><span data-stu-id="023cd-124">Required</span></span> | <span data-ttu-id="023cd-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="023cd-125">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="023cd-126">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="023cd-126">**customer-id**</span></span> | <span data-ttu-id="023cd-127">string</span><span class="sxs-lookup"><span data-stu-id="023cd-127">string</span></span>   | <span data-ttu-id="023cd-128">Yes</span><span class="sxs-lookup"><span data-stu-id="023cd-128">Yes</span></span>      | <span data-ttu-id="023cd-129">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="023cd-129">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="023cd-130">**transferência id**</span><span class="sxs-lookup"><span data-stu-id="023cd-130">**transfer-id**</span></span> | <span data-ttu-id="023cd-131">string</span><span class="sxs-lookup"><span data-stu-id="023cd-131">string</span></span>   | <span data-ttu-id="023cd-132">Yes</span><span class="sxs-lookup"><span data-stu-id="023cd-132">Yes</span></span>      | <span data-ttu-id="023cd-133">Um id de transferência formatado GUID que identifica a transferência.</span><span class="sxs-lookup"><span data-stu-id="023cd-133">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="023cd-134">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="023cd-134">Request headers</span></span>

<span data-ttu-id="023cd-135">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="023cd-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="023cd-136">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="023cd-136">Request body</span></span>

<span data-ttu-id="023cd-137">Esta tabela descreve as propriedades da [Entidade transferina](transfer-entity-resources.md) no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="023cd-137">This table describes the [TransferEntity](transfer-entity-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="023cd-138">Propriedade</span><span class="sxs-lookup"><span data-stu-id="023cd-138">Property</span></span>              | <span data-ttu-id="023cd-139">Tipo</span><span class="sxs-lookup"><span data-stu-id="023cd-139">Type</span></span>          | <span data-ttu-id="023cd-140">Necessário</span><span class="sxs-lookup"><span data-stu-id="023cd-140">Required</span></span>  | <span data-ttu-id="023cd-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="023cd-141">Description</span></span>                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="023cd-142">ID</span><span class="sxs-lookup"><span data-stu-id="023cd-142">id</span></span>                    | <span data-ttu-id="023cd-143">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="023cd-143">string</span></span>        | <span data-ttu-id="023cd-144">No</span><span class="sxs-lookup"><span data-stu-id="023cd-144">No</span></span>    | <span data-ttu-id="023cd-145">Um identificador de entidade de transferência que é fornecido após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="023cd-145">A transferEntity identifier that is supplied upon successful creation of the transferEntity.</span></span>                               |
| <span data-ttu-id="023cd-146">status</span><span class="sxs-lookup"><span data-stu-id="023cd-146">status</span></span>                | <span data-ttu-id="023cd-147">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="023cd-147">string</span></span>        | <span data-ttu-id="023cd-148">No</span><span class="sxs-lookup"><span data-stu-id="023cd-148">No</span></span>    | <span data-ttu-id="023cd-149">O estado da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="023cd-149">The status of the transferEntity.</span></span> <span data-ttu-id="023cd-150">Para rejeitar uma transferência, o valor deve ser definido como "rejeitar"</span><span class="sxs-lookup"><span data-stu-id="023cd-150">To reject a transfer, the value is to be set as "reject"</span></span>|

### <a name="request-example"></a><span data-ttu-id="023cd-151">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="023cd-151">Request example</span></span>

```http
PATCH /v1/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/transfers/ac4a9d22-ba07-444e-890f-cfe084eed498 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: efa4c6f5-153a-4f76-e458-1375e181cc14
MS-RequestId: 5b46e795-b661-428e-a2e7-f208b8d0d25c
Connection: keep-alive
Content-Length: 63

{"id":"ac4a9d22-ba07-444e-890f-cfe084eed498","status":"reject"}

```

## <a name="rest-response"></a><span data-ttu-id="023cd-152">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="023cd-152">REST response</span></span>

<span data-ttu-id="023cd-153">Se for bem sucedido, este método devolve o recurso [da Entidade de Transferência](transfer-entity-resources.md) povoada no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="023cd-153">If successful, this method returns the populated [TransferEntity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="023cd-154">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="023cd-154">Response success and error codes</span></span>

<span data-ttu-id="023cd-155">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="023cd-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="023cd-156">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="023cd-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="023cd-157">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="023cd-157">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="023cd-158">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="023cd-158">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1069
Content-Type: application/json; charset=utf-8
MS-CorrelationId: efa4c6f5-153a-4f76-e458-1375e181cc14
MS-RequestId: 5b46e795-b661-428e-a2e7-f208b8d0d25c
X-Locale: en-US
Date: Fri, 27 Mar 2020 17:50:33 GMT

{
  "id": "ac4a9d22-ba07-444e-890f-cfe084eed498",
  "status": "Reject",
  "createdTime": "2020-03-25T22:05:25.1057725Z",
  "lastModifiedTime": "2020-03-27T17:50:32Z",
  "customerTenantId": "b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0",
  "partnertenantid": "3a9a35ce-d5be-4814-ab58-4451c36fe157",
  "sourcePartnerName": "Test_Test_09092019GBL",
  "sourcePartnerTenantId": "7c8db11f-1e5e-4472-8386-f0b627d1f3e1",
  "targetPartnerName": "Test_Test_09032019GBL",
  "targetPartnerTenantId": "3a9a35ce-d5be-4814-ab58-4451c36fe157",
  "lastModifiedUser": "01a7548d-1136-4cf0-ba9a-300f921ffb22",
  "lineItems": [
    {
      "id": 0,
      "subscriptionId": "1151B8CE-125C-49D7-8C48-E62FC9101B77",
      "offerId": "13D32E13-A1B0-400D-96C0-4EAAA14DCED5",
      "billingCycle": "monthly",
      "friendlyName": "Dynamics 365 for Supply Chain Management Attach to Qualifying Dynamics 365 Base Offer (Qualified Offer)",
      "quantity": 20,
      "partnerIdOnRecord": "5139005",
      "addonItems": [

      ]
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/transfers/ac4a9d22-ba07-444e-890f-cfe084eed498",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "TransferEntity"
  }
}
```
