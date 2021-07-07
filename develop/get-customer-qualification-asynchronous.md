---
title: Obtenha as qualificações de um cliente
description: Saiba como usar a validação assíncrono para obter a qualificação de um cliente através da API do Partner Center. Os parceiros podem usá-lo para validar clientes da Educação.
ms.date: 05/17/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 4795b6e1ad008f9d854dc7efbee0c2099aefa609
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446314"
---
# <a name="get-a-customers-qualification-asynchronously"></a><span data-ttu-id="c4530-104">Obtenha a qualificação de um cliente assíncronea</span><span class="sxs-lookup"><span data-stu-id="c4530-104">Get a customer's qualification asynchronously</span></span>

<span data-ttu-id="c4530-105">Como obter as qualificações de um cliente assíncroneamente.</span><span class="sxs-lookup"><span data-stu-id="c4530-105">How to get a customer's qualifications asynchronously.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c4530-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c4530-106">Prerequisites</span></span>

- <span data-ttu-id="c4530-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c4530-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c4530-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="c4530-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="c4530-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c4530-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c4530-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="c4530-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c4530-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="c4530-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c4530-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="c4530-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c4530-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="c4530-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c4530-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c4530-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="c4530-115">C\#</span><span class="sxs-lookup"><span data-stu-id="c4530-115">C\#</span></span>

<span data-ttu-id="c4530-116">Para obter as qualificações de um cliente, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes.</span><span class="sxs-lookup"><span data-stu-id="c4530-116">To get a customer's qualifications, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="c4530-117">Em seguida, use a propriedade [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) para recuperar uma interface [**ICustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification)</span><span class="sxs-lookup"><span data-stu-id="c4530-117">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="c4530-118">Finalmente, ligue `GetQualifications()` ou `GetQualificationsAsync()` recupere as qualificações do cliente.</span><span class="sxs-lookup"><span data-stu-id="c4530-118">Finally, call `GetQualifications()` or `GetQualificationsAsync()` to retrieve the customer's qualifications.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerQualifications = partnerOperations.Customers.ById(customerId).Qualification.GetQualifications();
```

<span data-ttu-id="c4530-119">**Amostra**: [App de amostra de consola](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="c4530-119">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="c4530-120">**Project**: Classe SdkSamples : GetCustomerQualifications.cs</span><span class="sxs-lookup"><span data-stu-id="c4530-120">**Project**: SdkSamples **Class**: GetCustomerQualifications.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="c4530-121">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="c4530-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c4530-122">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4530-122">Request syntax</span></span>

| <span data-ttu-id="c4530-123">Método</span><span class="sxs-lookup"><span data-stu-id="c4530-123">Method</span></span>  | <span data-ttu-id="c4530-124">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="c4530-124">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c4530-125">**Obter**</span><span class="sxs-lookup"><span data-stu-id="c4530-125">**GET**</span></span> | <span data-ttu-id="c4530-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/qualificações HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c4530-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualifications HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="c4530-127">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="c4530-127">URI parameter</span></span>

<span data-ttu-id="c4530-128">Esta tabela lista o parâmetro de consulta necessário para obter toda a qualificação.</span><span class="sxs-lookup"><span data-stu-id="c4530-128">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="c4530-129">Nome</span><span class="sxs-lookup"><span data-stu-id="c4530-129">Name</span></span>               | <span data-ttu-id="c4530-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="c4530-130">Type</span></span>   | <span data-ttu-id="c4530-131">Necessário</span><span class="sxs-lookup"><span data-stu-id="c4530-131">Required</span></span> | <span data-ttu-id="c4530-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4530-132">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="c4530-133">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="c4530-133">**customer-tenant-id**</span></span> | <span data-ttu-id="c4530-134">string</span><span class="sxs-lookup"><span data-stu-id="c4530-134">string</span></span> | <span data-ttu-id="c4530-135">Yes</span><span class="sxs-lookup"><span data-stu-id="c4530-135">Yes</span></span>      | <span data-ttu-id="c4530-136">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="c4530-136">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c4530-137">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="c4530-137">Request headers</span></span>

<span data-ttu-id="c4530-138">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c4530-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c4530-139">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="c4530-139">Request body</span></span>

<span data-ttu-id="c4530-140">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c4530-140">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c4530-141">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="c4530-141">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="c4530-142">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="c4530-142">REST response</span></span>

<span data-ttu-id="c4530-143">Se for bem sucedido, este método devolve uma coleção de qualificações no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="c4530-143">If successful, this method returns a collection of qualifications in the response body.</span></span>  <span data-ttu-id="c4530-144">Abaixo estão exemplos da chamada **GET** a um cliente com a qualificação **de Educação.**</span><span class="sxs-lookup"><span data-stu-id="c4530-144">Below are examples of the **GET** call on a customer with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c4530-145">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="c4530-145">Response success and error codes</span></span>

<span data-ttu-id="c4530-146">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="c4530-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c4530-147">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="c4530-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c4530-148">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c4530-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-examples"></a><span data-ttu-id="c4530-149">Exemplos de resposta</span><span class="sxs-lookup"><span data-stu-id="c4530-149">Response examples</span></span>

#### <a name="approved"></a><span data-ttu-id="c4530-150">Aprovado</span><span class="sxs-lookup"><span data-stu-id="c4530-150">Approved</span></span>

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

#### <a name="in-review"></a><span data-ttu-id="c4530-151">Em Revisão</span><span class="sxs-lookup"><span data-stu-id="c4530-151">In Review</span></span>

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

#### <a name="denied"></a><span data-ttu-id="c4530-152">Negado</span><span class="sxs-lookup"><span data-stu-id="c4530-152">Denied</span></span>

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

#### <a name="state-owned-entity-samples"></a><span data-ttu-id="c4530-153">Amostras de entidades estatais</span><span class="sxs-lookup"><span data-stu-id="c4530-153">State Owned Entity Samples</span></span>

<span data-ttu-id="c4530-154">**Entidade Estatal através da amostra POST**</span><span class="sxs-lookup"><span data-stu-id="c4530-154">**State Owned Entity via POST sample**</span></span>

```csharp

//SOE
POST {customer_id}/qualifications
{
“qualification”: “StateOwnedEntity”
}

//

```

<span data-ttu-id="c4530-155">**Entidade Estatal através da amostra de Qualificações**</span><span class="sxs-lookup"><span data-stu-id="c4530-155">**State Owned Entity via Get Qualifications sample**</span></span>

```csharp

//SOE:
GET {customer_id}/qualifications
[
    {
        “qualification”: “StateOwnedEntity”
    }
]

```

<span data-ttu-id="c4530-156">**Entidade Estatal via Obter Qualificações com Educação**</span><span class="sxs-lookup"><span data-stu-id="c4530-156">**State Owned Entity via Get Qualifications with Education**</span></span>

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

<span data-ttu-id="c4530-157">**Entidade Estatal via Obter Qualificações com GCC**</span><span class="sxs-lookup"><span data-stu-id="c4530-157">**State Owned Entity via Get Qualifications with GCC**</span></span>

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

## <a name="related-articles"></a><span data-ttu-id="c4530-158">Artigos relacionados</span><span class="sxs-lookup"><span data-stu-id="c4530-158">Related articles</span></span>

- [<span data-ttu-id="c4530-159">Atualizar as qualificações de um cliente</span><span class="sxs-lookup"><span data-stu-id="c4530-159">Update a customer's qualifications</span></span>](./update-customer-qualification-asynchronous.md)
