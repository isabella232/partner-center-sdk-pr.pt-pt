---
title: Rejeitar uma transferência
description: Como rejeitar uma transferência de subscrições para um cliente.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e4a182ff92a21cf72ca1c2da9de7e211b433725f
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768978"
---
# <a name="reject-a-transfer"></a><span data-ttu-id="6d19d-103">Rejeitar uma transferência</span><span class="sxs-lookup"><span data-stu-id="6d19d-103">Reject a transfer</span></span>

<span data-ttu-id="6d19d-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="6d19d-104">**Applies to:**</span></span>

- <span data-ttu-id="6d19d-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="6d19d-105">Partner Center</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d19d-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6d19d-106">Prerequisites</span></span>

- <span data-ttu-id="6d19d-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6d19d-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6d19d-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="6d19d-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6d19d-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6d19d-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6d19d-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="6d19d-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6d19d-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="6d19d-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6d19d-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="6d19d-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6d19d-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="6d19d-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6d19d-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6d19d-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="6d19d-115">Um identificador de transferência para uma transferência existente.</span><span class="sxs-lookup"><span data-stu-id="6d19d-115">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="6d19d-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6d19d-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6d19d-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d19d-117">Request syntax</span></span>

| <span data-ttu-id="6d19d-118">Método</span><span class="sxs-lookup"><span data-stu-id="6d19d-118">Method</span></span>   | <span data-ttu-id="6d19d-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6d19d-119">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6d19d-120">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="6d19d-120">**PATCH**</span></span> | <span data-ttu-id="6d19d-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/transfers/{transfer-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6d19d-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="6d19d-122">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="6d19d-122">URI parameter</span></span>

<span data-ttu-id="6d19d-123">Utilize o seguinte parâmetro de percurso para identificar o cliente e especificar a transferência a aceitar.</span><span class="sxs-lookup"><span data-stu-id="6d19d-123">Use the following path parameter to identify the customer and specify the transfer to be accepted.</span></span>

| <span data-ttu-id="6d19d-124">Nome</span><span class="sxs-lookup"><span data-stu-id="6d19d-124">Name</span></span>            | <span data-ttu-id="6d19d-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="6d19d-125">Type</span></span>     | <span data-ttu-id="6d19d-126">Necessário</span><span class="sxs-lookup"><span data-stu-id="6d19d-126">Required</span></span> | <span data-ttu-id="6d19d-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d19d-127">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="6d19d-128">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="6d19d-128">**customer-id**</span></span> | <span data-ttu-id="6d19d-129">string</span><span class="sxs-lookup"><span data-stu-id="6d19d-129">string</span></span>   | <span data-ttu-id="6d19d-130">Sim</span><span class="sxs-lookup"><span data-stu-id="6d19d-130">Yes</span></span>      | <span data-ttu-id="6d19d-131">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="6d19d-131">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="6d19d-132">**transferência id**</span><span class="sxs-lookup"><span data-stu-id="6d19d-132">**transfer-id**</span></span> | <span data-ttu-id="6d19d-133">string</span><span class="sxs-lookup"><span data-stu-id="6d19d-133">string</span></span>   | <span data-ttu-id="6d19d-134">Sim</span><span class="sxs-lookup"><span data-stu-id="6d19d-134">Yes</span></span>      | <span data-ttu-id="6d19d-135">Um id de transferência formatado GUID que identifica a transferência.</span><span class="sxs-lookup"><span data-stu-id="6d19d-135">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="6d19d-136">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6d19d-136">Request headers</span></span>

<span data-ttu-id="6d19d-137">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6d19d-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6d19d-138">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6d19d-138">Request body</span></span>

<span data-ttu-id="6d19d-139">Esta tabela descreve as propriedades da [Entidade transferina](transfer-entity-resources.md) no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="6d19d-139">This table describes the [TransferEntity](transfer-entity-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="6d19d-140">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6d19d-140">Property</span></span>              | <span data-ttu-id="6d19d-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="6d19d-141">Type</span></span>          | <span data-ttu-id="6d19d-142">Necessário</span><span class="sxs-lookup"><span data-stu-id="6d19d-142">Required</span></span>  | <span data-ttu-id="6d19d-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d19d-143">Description</span></span>                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="6d19d-144">ID</span><span class="sxs-lookup"><span data-stu-id="6d19d-144">id</span></span>                    | <span data-ttu-id="6d19d-145">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6d19d-145">string</span></span>        | <span data-ttu-id="6d19d-146">No</span><span class="sxs-lookup"><span data-stu-id="6d19d-146">No</span></span>    | <span data-ttu-id="6d19d-147">Um identificador de entidade de transferência que é fornecido após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="6d19d-147">A transferEntity identifier that is supplied upon successful creation of the transferEntity.</span></span>                               |
| <span data-ttu-id="6d19d-148">status</span><span class="sxs-lookup"><span data-stu-id="6d19d-148">status</span></span>                | <span data-ttu-id="6d19d-149">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="6d19d-149">string</span></span>        | <span data-ttu-id="6d19d-150">No</span><span class="sxs-lookup"><span data-stu-id="6d19d-150">No</span></span>    | <span data-ttu-id="6d19d-151">O estado da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="6d19d-151">The status of the transferEntity.</span></span> <span data-ttu-id="6d19d-152">Para rejeitar uma transferência, o valor deve ser definido como "rejeitar"</span><span class="sxs-lookup"><span data-stu-id="6d19d-152">To reject a transfer, the value is to be set as "reject"</span></span>|

### <a name="request-example"></a><span data-ttu-id="6d19d-153">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6d19d-153">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="6d19d-154">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6d19d-154">REST response</span></span>

<span data-ttu-id="6d19d-155">Se for bem sucedido, este método devolve o recurso [da Entidade de Transferência](transfer-entity-resources.md) povoada no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="6d19d-155">If successful, this method returns the populated [TransferEntity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6d19d-156">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6d19d-156">Response success and error codes</span></span>

<span data-ttu-id="6d19d-157">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6d19d-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6d19d-158">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6d19d-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6d19d-159">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6d19d-159">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6d19d-160">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6d19d-160">Response example</span></span>

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
