---
title: Obtenha as qualificações de um cliente
description: Saiba como usar a validação assíncrono para obter a qualificação de um cliente através da API do Partner Center. Os parceiros podem usá-lo para validar clientes da Educação.
ms.date: 05/17/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: df605e4d400d29e14fd0b44bef34f88bbc7ca8b2
ms.sourcegitcommit: 7d59c58ee36b217bd5cac089f918059e9dbb8a62
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110027933"
---
# <a name="get-a-customers-qualification-asynchronously"></a><span data-ttu-id="8f694-104">Obtenha a qualificação de um cliente assíncronea</span><span class="sxs-lookup"><span data-stu-id="8f694-104">Get a customer's qualification asynchronously</span></span>

<span data-ttu-id="8f694-105">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="8f694-105">**Applies To**</span></span>

- <span data-ttu-id="8f694-106">Partner Center</span><span class="sxs-lookup"><span data-stu-id="8f694-106">Partner Center</span></span>

<span data-ttu-id="8f694-107">Como obter as qualificações de um cliente assíncroneamente.</span><span class="sxs-lookup"><span data-stu-id="8f694-107">How to get a customer's qualifications asynchronously.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8f694-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8f694-108">Prerequisites</span></span>

- <span data-ttu-id="8f694-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8f694-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8f694-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="8f694-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="8f694-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8f694-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8f694-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="8f694-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8f694-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="8f694-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8f694-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="8f694-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8f694-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="8f694-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8f694-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8f694-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="8f694-117">C\#</span><span class="sxs-lookup"><span data-stu-id="8f694-117">C\#</span></span>

<span data-ttu-id="8f694-118">Para obter as qualificações de um cliente, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="8f694-118">To get a customer's qualifications, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="8f694-119">Em seguida, use a propriedade [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) para recuperar uma interface [**ICustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification)</span><span class="sxs-lookup"><span data-stu-id="8f694-119">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="8f694-120">Finalmente, ligue `GetQualifications()` ou `GetQualificationsAsync()` recupere as qualificações do cliente.</span><span class="sxs-lookup"><span data-stu-id="8f694-120">Finally, call `GetQualifications()` or `GetQualificationsAsync()` to retrieve the customer's qualifications.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerQualifications = partnerOperations.Customers.ById(customerId).Qualification.GetQualifications();
```

<span data-ttu-id="8f694-121">**Amostra**: [App de amostra de consola](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="8f694-121">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="8f694-122">**Projeto**: Classe SdkSamples : GetCustomerQualifications.cs</span><span class="sxs-lookup"><span data-stu-id="8f694-122">**Project**: SdkSamples **Class**: GetCustomerQualifications.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="8f694-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="8f694-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8f694-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f694-124">Request syntax</span></span>

| <span data-ttu-id="8f694-125">Método</span><span class="sxs-lookup"><span data-stu-id="8f694-125">Method</span></span>  | <span data-ttu-id="8f694-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="8f694-126">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8f694-127">**Obter**</span><span class="sxs-lookup"><span data-stu-id="8f694-127">**GET**</span></span> | <span data-ttu-id="8f694-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/qualificações HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8f694-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualifications HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="8f694-129">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="8f694-129">URI parameter</span></span>

<span data-ttu-id="8f694-130">Esta tabela lista o parâmetro de consulta necessário para obter toda a qualificação.</span><span class="sxs-lookup"><span data-stu-id="8f694-130">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="8f694-131">Nome</span><span class="sxs-lookup"><span data-stu-id="8f694-131">Name</span></span>               | <span data-ttu-id="8f694-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="8f694-132">Type</span></span>   | <span data-ttu-id="8f694-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="8f694-133">Required</span></span> | <span data-ttu-id="8f694-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f694-134">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="8f694-135">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="8f694-135">**customer-tenant-id**</span></span> | <span data-ttu-id="8f694-136">string</span><span class="sxs-lookup"><span data-stu-id="8f694-136">string</span></span> | <span data-ttu-id="8f694-137">Yes</span><span class="sxs-lookup"><span data-stu-id="8f694-137">Yes</span></span>      | <span data-ttu-id="8f694-138">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="8f694-138">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8f694-139">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="8f694-139">Request headers</span></span>

<span data-ttu-id="8f694-140">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8f694-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8f694-141">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="8f694-141">Request body</span></span>

<span data-ttu-id="8f694-142">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8f694-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="8f694-143">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="8f694-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="8f694-144">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="8f694-144">REST response</span></span>

<span data-ttu-id="8f694-145">Se for bem sucedido, este método devolve uma coleção de qualificações no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="8f694-145">If successful, this method returns a collection of qualifications in the response body.</span></span>  <span data-ttu-id="8f694-146">Abaixo estão exemplos da chamada **GET** a um cliente com a qualificação **de Educação.**</span><span class="sxs-lookup"><span data-stu-id="8f694-146">Below are examples of the **GET** call on a customer with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8f694-147">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="8f694-147">Response success and error codes</span></span>

<span data-ttu-id="8f694-148">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="8f694-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8f694-149">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8f694-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8f694-150">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="8f694-150">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-examples"></a><span data-ttu-id="8f694-151">Exemplos de resposta</span><span class="sxs-lookup"><span data-stu-id="8f694-151">Response examples</span></span>

#### <a name="approved"></a><span data-ttu-id="8f694-152">Aprovado</span><span class="sxs-lookup"><span data-stu-id="8f694-152">Approved</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "Approved",
    }
]

```

#### <a name="in-review"></a><span data-ttu-id="8f694-153">Em Revisão</span><span class="sxs-lookup"><span data-stu-id="8f694-153">In Review</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "InReview",
        "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
    }
]

```

#### <a name="denied"></a><span data-ttu-id="8f694-154">Negado</span><span class="sxs-lookup"><span data-stu-id="8f694-154">Denied</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "Denied",
        "vettingReason": "Not an Education Customer", // example Vetting Reason
        "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
    }
]

```

#### <a name="state-owned-entity-samples"></a><span data-ttu-id="8f694-155">Amostras de entidades estatais</span><span class="sxs-lookup"><span data-stu-id="8f694-155">State Owned Entity Samples</span></span>

<span data-ttu-id="8f694-156">**Entidade Estatal através da amostra POST**</span><span class="sxs-lookup"><span data-stu-id="8f694-156">**State Owned Entity via POST sample**</span></span>

```csharp

//SOE
POST {customer_id}/qualifications
{
“qualification”: “StateOwnedEntity”
}

//

```

<span data-ttu-id="8f694-157">**Entidade Estatal através da amostra de Qualificações**</span><span class="sxs-lookup"><span data-stu-id="8f694-157">**State Owned Entity via Get Qualifications sample**</span></span>

```csharp

//SOE:
GET {customer_id}/qualifications
[
    {
        “qualification”: “StateOwnedEntity”
    }
]

```

<span data-ttu-id="8f694-158">**Entidade Estatal via Obter Qualificações com Educação**</span><span class="sxs-lookup"><span data-stu-id="8f694-158">**State Owned Entity via Get Qualifications with Education**</span></span>

```csharp

GET {customer_id}/qualifications
[
    {
        “qualification”: “Education”,
        “vettingStatus”: “Approved”
    },
{
        “qualification”: “StateOwnedEntity”
    }
]

```

<span data-ttu-id="8f694-159">**Entidade Estatal via Obter Qualificações com GCC**</span><span class="sxs-lookup"><span data-stu-id="8f694-159">**State Owned Entity via Get Qualifications with GCC**</span></span>

```csharp

GET {customer_id}/qualifications
[
    {
        “qualification”: “GovernmentCommunityCloud”,
        “vettingStatus”: “Approved”,
        “vettingCreateDate”: “2021-05-06T19:59:56.6832021+00:00”
    },
{
        “qualification”: “StateOwnedEntity”
    }
]

```

## <a name="related-articles"></a><span data-ttu-id="8f694-160">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="8f694-160">Related articles</span></span>

- [<span data-ttu-id="8f694-161">Atualizar as qualificações de um cliente</span><span class="sxs-lookup"><span data-stu-id="8f694-161">Update a customer's qualifications</span></span>](./update-customer-qualification-asynchronous.md)
