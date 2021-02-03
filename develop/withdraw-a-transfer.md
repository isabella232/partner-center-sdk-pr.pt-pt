---
title: Retirar uma transferência
description: Como retirar uma transferência criada de subscrições para um cliente.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a9e1e2a33d21fc1338a36b8ac96b528e70b61c86
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768702"
---
# <a name="withdraw-a-transfer"></a><span data-ttu-id="d1bd6-103">Retirar uma transferência</span><span class="sxs-lookup"><span data-stu-id="d1bd6-103">Withdraw a transfer</span></span>

<span data-ttu-id="d1bd6-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="d1bd6-104">**Applies to:**</span></span>

- <span data-ttu-id="d1bd6-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="d1bd6-105">Partner Center</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1bd6-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d1bd6-106">Prerequisites</span></span>

- <span data-ttu-id="d1bd6-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d1bd6-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d1bd6-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="d1bd6-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="d1bd6-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d1bd6-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d1bd6-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d1bd6-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d1bd6-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d1bd6-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d1bd6-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d1bd6-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d1bd6-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d1bd6-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d1bd6-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d1bd6-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d1bd6-115">Um identificador de transferência para uma transferência existente.</span><span class="sxs-lookup"><span data-stu-id="d1bd6-115">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="d1bd6-116">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="d1bd6-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d1bd6-117">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1bd6-117">Request syntax</span></span>

| <span data-ttu-id="d1bd6-118">Método</span><span class="sxs-lookup"><span data-stu-id="d1bd6-118">Method</span></span>    | <span data-ttu-id="d1bd6-119">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="d1bd6-119">Request URI</span></span>                                                                                                 |
|-----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d1bd6-120">**EXCLUIR**</span><span class="sxs-lookup"><span data-stu-id="d1bd6-120">**DELETE**</span></span>| <span data-ttu-id="d1bd6-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/transfers/{transfer-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d1bd6-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>      |

### <a name="uri-parameter"></a><span data-ttu-id="d1bd6-122">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="d1bd6-122">URI parameter</span></span>

<span data-ttu-id="d1bd6-123">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="d1bd6-123">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="d1bd6-124">Nome</span><span class="sxs-lookup"><span data-stu-id="d1bd6-124">Name</span></span>            | <span data-ttu-id="d1bd6-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="d1bd6-125">Type</span></span>     | <span data-ttu-id="d1bd6-126">Necessário</span><span class="sxs-lookup"><span data-stu-id="d1bd6-126">Required</span></span> | <span data-ttu-id="d1bd6-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1bd6-127">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="d1bd6-128">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="d1bd6-128">**customer-id**</span></span> | <span data-ttu-id="d1bd6-129">string</span><span class="sxs-lookup"><span data-stu-id="d1bd6-129">string</span></span>   | <span data-ttu-id="d1bd6-130">Sim</span><span class="sxs-lookup"><span data-stu-id="d1bd6-130">Yes</span></span>      | <span data-ttu-id="d1bd6-131">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="d1bd6-131">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="d1bd6-132">**transferência id**</span><span class="sxs-lookup"><span data-stu-id="d1bd6-132">**transfer-id**</span></span> | <span data-ttu-id="d1bd6-133">string</span><span class="sxs-lookup"><span data-stu-id="d1bd6-133">string</span></span>   | <span data-ttu-id="d1bd6-134">Sim</span><span class="sxs-lookup"><span data-stu-id="d1bd6-134">Yes</span></span>      | <span data-ttu-id="d1bd6-135">Um id de transferência formatado GUID que identifica a transferência.</span><span class="sxs-lookup"><span data-stu-id="d1bd6-135">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="d1bd6-136">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="d1bd6-136">Request headers</span></span>

<span data-ttu-id="d1bd6-137">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d1bd6-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-example"></a><span data-ttu-id="d1bd6-138">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="d1bd6-138">Request example</span></span>

```http
DELETE /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers/67c5b05b-09b5-47ba-9047-5056fe2afa4f HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: cdf6e25c-7b32-4cc3-d8bc-53e0b37eebd8
MS-CorrelationId: 9041d76d-8915-43a8-8e82-00ca46a1a73d
Connection: keep-alive
```

## <a name="rest-response"></a><span data-ttu-id="d1bd6-139">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="d1bd6-139">REST response</span></span>

<span data-ttu-id="d1bd6-140">Se for bem sucedido, este método retorna No Content (204).</span><span class="sxs-lookup"><span data-stu-id="d1bd6-140">If successful, this method returns No Content (204).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d1bd6-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d1bd6-141">Response success and error codes</span></span>

<span data-ttu-id="d1bd6-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d1bd6-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d1bd6-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d1bd6-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d1bd6-144">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d1bd6-144">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d1bd6-145">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="d1bd6-145">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 9041d76d-8915-43a8-8e82-00ca46a1a73d
MS-RequestId: cdf6e25c-7b32-4cc3-d8bc-53e0b37eebd8
Date: Tue, 24 Mar 2020 23:44:06 GMT
```
