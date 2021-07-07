---
title: Retirar uma transferência
description: Como retirar uma transferência criada de subscrições para um cliente.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3c15cf09b4e466e178c7afb5f9d324fe1199418e
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445209"
---
# <a name="withdraw-a-transfer"></a><span data-ttu-id="7ca09-103">Retirar uma transferência</span><span class="sxs-lookup"><span data-stu-id="7ca09-103">Withdraw a transfer</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7ca09-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7ca09-104">Prerequisites</span></span>

- <span data-ttu-id="7ca09-105">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7ca09-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7ca09-106">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="7ca09-106">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="7ca09-107">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7ca09-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7ca09-108">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="7ca09-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7ca09-109">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="7ca09-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7ca09-110">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="7ca09-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7ca09-111">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="7ca09-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7ca09-112">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7ca09-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7ca09-113">Um identificador de transferência para uma transferência existente.</span><span class="sxs-lookup"><span data-stu-id="7ca09-113">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="7ca09-114">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="7ca09-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7ca09-115">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ca09-115">Request syntax</span></span>

| <span data-ttu-id="7ca09-116">Método</span><span class="sxs-lookup"><span data-stu-id="7ca09-116">Method</span></span>    | <span data-ttu-id="7ca09-117">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="7ca09-117">Request URI</span></span>                                                                                                 |
|-----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7ca09-118">**EXCLUIR**</span><span class="sxs-lookup"><span data-stu-id="7ca09-118">**DELETE**</span></span>| <span data-ttu-id="7ca09-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/transfers/{transfer-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7ca09-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>      |

### <a name="uri-parameter"></a><span data-ttu-id="7ca09-120">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="7ca09-120">URI parameter</span></span>

<span data-ttu-id="7ca09-121">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="7ca09-121">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="7ca09-122">Nome</span><span class="sxs-lookup"><span data-stu-id="7ca09-122">Name</span></span>            | <span data-ttu-id="7ca09-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="7ca09-123">Type</span></span>     | <span data-ttu-id="7ca09-124">Necessário</span><span class="sxs-lookup"><span data-stu-id="7ca09-124">Required</span></span> | <span data-ttu-id="7ca09-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ca09-125">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="7ca09-126">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="7ca09-126">**customer-id**</span></span> | <span data-ttu-id="7ca09-127">string</span><span class="sxs-lookup"><span data-stu-id="7ca09-127">string</span></span>   | <span data-ttu-id="7ca09-128">Yes</span><span class="sxs-lookup"><span data-stu-id="7ca09-128">Yes</span></span>      | <span data-ttu-id="7ca09-129">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="7ca09-129">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="7ca09-130">**transferência id**</span><span class="sxs-lookup"><span data-stu-id="7ca09-130">**transfer-id**</span></span> | <span data-ttu-id="7ca09-131">string</span><span class="sxs-lookup"><span data-stu-id="7ca09-131">string</span></span>   | <span data-ttu-id="7ca09-132">Yes</span><span class="sxs-lookup"><span data-stu-id="7ca09-132">Yes</span></span>      | <span data-ttu-id="7ca09-133">Um id de transferência formatado GUID que identifica a transferência.</span><span class="sxs-lookup"><span data-stu-id="7ca09-133">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="7ca09-134">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="7ca09-134">Request headers</span></span>

<span data-ttu-id="7ca09-135">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7ca09-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-example"></a><span data-ttu-id="7ca09-136">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="7ca09-136">Request example</span></span>

```http
DELETE /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers/67c5b05b-09b5-47ba-9047-5056fe2afa4f HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: cdf6e25c-7b32-4cc3-d8bc-53e0b37eebd8
MS-CorrelationId: 9041d76d-8915-43a8-8e82-00ca46a1a73d
Connection: keep-alive
```

## <a name="rest-response"></a><span data-ttu-id="7ca09-137">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="7ca09-137">REST response</span></span>

<span data-ttu-id="7ca09-138">Se for bem sucedido, este método retorna No Content (204).</span><span class="sxs-lookup"><span data-stu-id="7ca09-138">If successful, this method returns No Content (204).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7ca09-139">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="7ca09-139">Response success and error codes</span></span>

<span data-ttu-id="7ca09-140">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="7ca09-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7ca09-141">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="7ca09-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7ca09-142">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="7ca09-142">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7ca09-143">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="7ca09-143">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 9041d76d-8915-43a8-8e82-00ca46a1a73d
MS-RequestId: cdf6e25c-7b32-4cc3-d8bc-53e0b37eebd8
Date: Tue, 24 Mar 2020 23:44:06 GMT
```
