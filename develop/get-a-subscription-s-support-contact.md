---
title: Obter o contacto de suporte de uma subscrição
description: Como obter o contacto de suporte de uma subscrição.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df3bce48902d95dc541c4a45e4e633569fc4406e
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769272"
---
# <a name="get-a-subscriptions-support-contact"></a><span data-ttu-id="63dfb-103">Obter o contacto de suporte de uma subscrição</span><span class="sxs-lookup"><span data-stu-id="63dfb-103">Get a subscription's support contact</span></span>

<span data-ttu-id="63dfb-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="63dfb-104">**Applies To**</span></span>

- <span data-ttu-id="63dfb-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="63dfb-105">Partner Center</span></span>
- <span data-ttu-id="63dfb-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="63dfb-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="63dfb-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="63dfb-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="63dfb-108">Como obter o contacto de suporte de uma subscrição.</span><span class="sxs-lookup"><span data-stu-id="63dfb-108">How to get a subscription's support contact.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63dfb-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="63dfb-109">Prerequisites</span></span>

- <span data-ttu-id="63dfb-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="63dfb-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="63dfb-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="63dfb-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="63dfb-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="63dfb-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="63dfb-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="63dfb-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="63dfb-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="63dfb-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="63dfb-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="63dfb-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="63dfb-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="63dfb-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="63dfb-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="63dfb-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="63dfb-118">Um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="63dfb-118">A subscription identifier.</span></span>

## <a name="c"></a><span data-ttu-id="63dfb-119">C\#</span><span class="sxs-lookup"><span data-stu-id="63dfb-119">C\#</span></span>

<span data-ttu-id="63dfb-120">Para obter o contacto de suporte de uma subscrição, comece por utilizar o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="63dfb-120">To get a subscription's support contact, start by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="63dfb-121">Em seguida, obtenha uma interface para as operações de subscrição ligando para o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID de subscrição.</span><span class="sxs-lookup"><span data-stu-id="63dfb-121">Then, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="63dfb-122">Em seguida, utilize a propriedade [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) para obter uma interface para suportar operações de contacto e, em seguida, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) ou [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) para recuperar o objeto [**SupportContact.**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact)</span><span class="sxs-lookup"><span data-stu-id="63dfb-122">Next, use the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) property to obtain an interface to support contact operations, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) method to retrieve the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) object.</span></span>

``` csharp
// IAggregatePartner partnerOperations.
// string customerId;
// string subscriptionId;

// Retrieve subscription's support contact.
var supportContact = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId).SupportContact.Get();
```

<span data-ttu-id="63dfb-123">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="63dfb-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="63dfb-124">**Projeto**: Partner Center SDK Samples **Class**: GetSubscriptionSupportContact.cs</span><span class="sxs-lookup"><span data-stu-id="63dfb-124">**Project**: Partner Center SDK Samples **Class**: GetSubscriptionSupportContact.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="63dfb-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="63dfb-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="63dfb-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="63dfb-126">Request syntax</span></span>

| <span data-ttu-id="63dfb-127">Método</span><span class="sxs-lookup"><span data-stu-id="63dfb-127">Method</span></span>  | <span data-ttu-id="63dfb-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="63dfb-128">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="63dfb-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="63dfb-129">**GET**</span></span> | <span data-ttu-id="63dfb-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/supportcontact HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="63dfb-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/supportcontact HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="63dfb-131">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="63dfb-131">URI parameter</span></span>

<span data-ttu-id="63dfb-132">Utilize os seguintes parâmetros de percurso para identificar o cliente e a subscrição.</span><span class="sxs-lookup"><span data-stu-id="63dfb-132">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="63dfb-133">Nome</span><span class="sxs-lookup"><span data-stu-id="63dfb-133">Name</span></span>            | <span data-ttu-id="63dfb-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="63dfb-134">Type</span></span>   | <span data-ttu-id="63dfb-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="63dfb-135">Required</span></span> | <span data-ttu-id="63dfb-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="63dfb-136">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="63dfb-137">id cliente</span><span class="sxs-lookup"><span data-stu-id="63dfb-137">customer-id</span></span>     | <span data-ttu-id="63dfb-138">string</span><span class="sxs-lookup"><span data-stu-id="63dfb-138">string</span></span> | <span data-ttu-id="63dfb-139">Sim</span><span class="sxs-lookup"><span data-stu-id="63dfb-139">Yes</span></span>      | <span data-ttu-id="63dfb-140">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="63dfb-140">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="63dfb-141">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="63dfb-141">subscription-id</span></span> | <span data-ttu-id="63dfb-142">string</span><span class="sxs-lookup"><span data-stu-id="63dfb-142">string</span></span> | <span data-ttu-id="63dfb-143">Sim</span><span class="sxs-lookup"><span data-stu-id="63dfb-143">Yes</span></span>      | <span data-ttu-id="63dfb-144">Uma cadeia formatada GUID que identifica a subscrição do ensaio.</span><span class="sxs-lookup"><span data-stu-id="63dfb-144">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="63dfb-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="63dfb-145">Request headers</span></span>

<span data-ttu-id="63dfb-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="63dfb-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="63dfb-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="63dfb-147">Request body</span></span>

<span data-ttu-id="63dfb-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="63dfb-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="63dfb-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="63dfb-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: d052776c-e8fd-4803-b6a3-1659055ac3c4
MS-CorrelationId: a6c552a8-1922-4d0c-bb94-335a33334d14
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="63dfb-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="63dfb-150">REST response</span></span>

<span data-ttu-id="63dfb-151">Se for bem sucedido, o organismo de resposta contém o recurso [SupportContact.](subscription-resources.md#supportcontact)</span><span class="sxs-lookup"><span data-stu-id="63dfb-151">If successful, the response body contains the [SupportContact](subscription-resources.md#supportcontact) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="63dfb-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="63dfb-152">Response success and error codes</span></span>

<span data-ttu-id="63dfb-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="63dfb-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="63dfb-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="63dfb-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="63dfb-155">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="63dfb-155">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="63dfb-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="63dfb-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 328
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a6c552a8-1922-4d0c-bb94-335a33334d14
MS-RequestId: d052776c-e8fd-4803-b6a3-1659055ac3c4
MS-CV: bLbUhqy0+ESOX1v4.0
MS-ServerId: 201022015
Date: Tue, 20 Jun 2017 19:30:19 GMT

{
    "supportTenantId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "supportMpnId": "4391507",
    "name": "Trey Research",
    "links": {
        "self": {
            "uri": "/customers/0C39D6D5-C70D-4C55-BC02-F620844F3FD1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact",
            "method": "Get",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SupportContact"
    }
}
```
