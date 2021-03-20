---
title: Atualizar as qualificações de um cliente
description: Saiba como atualizar as qualificações de um cliente através de rastreio ou verificação assíncronos, incluindo o endereço associado ao perfil.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 703585eeaba93b6d7a510a3174a78a28f22e1510
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711938"
---
# <a name="update-a-customers-qualifications-asynchronously"></a><span data-ttu-id="844fa-103">Atualizar as qualificações de um cliente assíncroneamente</span><span class="sxs-lookup"><span data-stu-id="844fa-103">Update a customer's qualifications asynchronously</span></span>

<span data-ttu-id="844fa-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="844fa-104">**Applies To**</span></span>

- <span data-ttu-id="844fa-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="844fa-105">Partner Center</span></span>

<span data-ttu-id="844fa-106">Saiba como atualizar as qualificações de um cliente de forma assíncronea através das APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="844fa-106">Learn how to update a customer's qualifications asynchronously via Partner Center APIs.</span></span> <span data-ttu-id="844fa-107">Para aprender a fazer isto de forma sincronizada, consulte atualizar a [qualificação de um cliente através de validação sincronizada](update-customer-qualification-synchronous.md).</span><span class="sxs-lookup"><span data-stu-id="844fa-107">To learn how to do this synchronously, see [Update a customer's qualification via synchronous validation](update-customer-qualification-synchronous.md).</span></span>

<span data-ttu-id="844fa-108">Um parceiro pode atualizar as qualificações de um cliente assíncroneamente para ser "Education" ou "GovernmentCommunityCloud".</span><span class="sxs-lookup"><span data-stu-id="844fa-108">A partner can update a customer's qualifications asynchronously to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="844fa-109">Outros valores, "Nenhum" e "Sem Fins Lucrativos", não podem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="844fa-109">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="844fa-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="844fa-110">Prerequisites</span></span>

- <span data-ttu-id="844fa-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="844fa-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="844fa-112">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="844fa-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="844fa-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="844fa-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="844fa-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="844fa-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="844fa-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="844fa-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="844fa-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="844fa-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="844fa-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="844fa-117">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="844fa-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="844fa-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="844fa-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="844fa-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="844fa-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="844fa-120">Request syntax</span></span>

| <span data-ttu-id="844fa-121">Método</span><span class="sxs-lookup"><span data-stu-id="844fa-121">Method</span></span>  | <span data-ttu-id="844fa-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="844fa-122">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="844fa-123">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="844fa-123">**POST**</span></span> | <span data-ttu-id="844fa-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer_id}/qualificações?código={validaçãoD} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="844fa-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualifications?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="844fa-125">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="844fa-125">URI parameter</span></span>

<span data-ttu-id="844fa-126">Utilize o seguinte parâmetro de consulta para atualizar a qualificação.</span><span class="sxs-lookup"><span data-stu-id="844fa-126">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="844fa-127">Nome</span><span class="sxs-lookup"><span data-stu-id="844fa-127">Name</span></span>                   | <span data-ttu-id="844fa-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="844fa-128">Type</span></span> | <span data-ttu-id="844fa-129">Necessário</span><span class="sxs-lookup"><span data-stu-id="844fa-129">Required</span></span> | <span data-ttu-id="844fa-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="844fa-130">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="844fa-131">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="844fa-131">**customer-tenant-id**</span></span> | <span data-ttu-id="844fa-132">GUID</span><span class="sxs-lookup"><span data-stu-id="844fa-132">GUID</span></span> | <span data-ttu-id="844fa-133">Yes</span><span class="sxs-lookup"><span data-stu-id="844fa-133">Yes</span></span>      | <span data-ttu-id="844fa-134">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="844fa-134">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="844fa-135">**validaçãoDesco**</span><span class="sxs-lookup"><span data-stu-id="844fa-135">**validationCode**</span></span>     | <span data-ttu-id="844fa-136">int</span><span class="sxs-lookup"><span data-stu-id="844fa-136">int</span></span>  | <span data-ttu-id="844fa-137">No</span><span class="sxs-lookup"><span data-stu-id="844fa-137">No</span></span>       | <span data-ttu-id="844fa-138">Só era necessário para a Nuvem Comunitária do Governo.</span><span class="sxs-lookup"><span data-stu-id="844fa-138">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="844fa-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="844fa-139">Request headers</span></span>

<span data-ttu-id="844fa-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="844fa-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="844fa-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="844fa-141">Request body</span></span>

<span data-ttu-id="844fa-142">O valor inteiro do número de [**clientesQualificação.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification)</span><span class="sxs-lookup"><span data-stu-id="844fa-142">The integer value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="844fa-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="844fa-143">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a><span data-ttu-id="844fa-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="844fa-144">REST response</span></span>

<span data-ttu-id="844fa-145">Se for bem sucedido, este método devolve um objeto de qualificações no corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="844fa-145">If successful, this method returns a qualifications object in the response body.</span></span> <span data-ttu-id="844fa-146">Abaixo está um exemplo da chamada **do POST** sobre um cliente (com uma qualificação anterior de **Nenhum)** com a qualificação **de Educação.**</span><span class="sxs-lookup"><span data-stu-id="844fa-146">Below is an example of the **POST** call on a customer (with a previous qualification of **None**) with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="844fa-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="844fa-147">Response success and error codes</span></span>

<span data-ttu-id="844fa-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="844fa-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="844fa-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="844fa-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="844fa-150">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="844fa-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="844fa-151">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="844fa-151">Response example</span></span>

```http
HTTP/1.1 201 CREATED
Content-Length: 29
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualification": "Education",
    "vettingStatus": "InReview",
    "vettingCreateDate": "2020-12-04T20:54:24Z" // UTC
}
```

## <a name="related-articles"></a><span data-ttu-id="844fa-152">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="844fa-152">Related articles</span></span>

- [<span data-ttu-id="844fa-153">Obtenha as qualificações de um cliente</span><span class="sxs-lookup"><span data-stu-id="844fa-153">Get a customer's qualifications</span></span>](./get-customer-qualification-asynchronous.md)
- [<span data-ttu-id="844fa-154">Obter os códigos de validação de um parceiro</span><span class="sxs-lookup"><span data-stu-id="844fa-154">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)