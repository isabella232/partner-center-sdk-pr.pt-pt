---
title: Atualizar o contacto de suporte de uma subscrição
description: Como atualizar o contacto de suporte de uma subscrição a um dos revendedores de valor acrescentado do parceiro.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8c89f91fc9e89384a7be1237c08d7a9a1cfe3164
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530366"
---
# <a name="update-a-subscriptions-support-contact"></a><span data-ttu-id="b6461-103">Atualizar o contacto de suporte de uma subscrição</span><span class="sxs-lookup"><span data-stu-id="b6461-103">Update a subscription's support contact</span></span>

<span data-ttu-id="b6461-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b6461-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b6461-105">Como atualizar o contacto de suporte de uma subscrição a um dos revendedores de valor acrescentado do parceiro.</span><span class="sxs-lookup"><span data-stu-id="b6461-105">How to update a subscription's support contact to one of the partner's value added resellers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6461-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b6461-106">Prerequisites</span></span>

- <span data-ttu-id="b6461-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b6461-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b6461-108">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="b6461-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="b6461-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b6461-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="b6461-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b6461-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="b6461-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="b6461-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="b6461-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="b6461-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="b6461-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="b6461-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="b6461-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b6461-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="b6461-115">Um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="b6461-115">A subscription identifier.</span></span>

- <span data-ttu-id="b6461-116">Informações sobre o novo contacto de suporte: identificador de inquilino, identificador da Microsoft Partner Network e nome.</span><span class="sxs-lookup"><span data-stu-id="b6461-116">Information about the new support contact: tenant identifier, Microsoft Partner Network identifier, and name.</span></span> <span data-ttu-id="b6461-117">O contacto de suporte deve ser um dos revendedores de valor acrescentado do parceiro.</span><span class="sxs-lookup"><span data-stu-id="b6461-117">The support contact must be one of the partner's value added resellers.</span></span>

## <a name="c"></a><span data-ttu-id="b6461-118">C\#</span><span class="sxs-lookup"><span data-stu-id="b6461-118">C\#</span></span>

<span data-ttu-id="b6461-119">Para atualizar o contacto de suporte de uma subscrição, primeiro instantaneamente e povoar um objeto [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) com os novos valores.</span><span class="sxs-lookup"><span data-stu-id="b6461-119">To update a subscription's support contact, first instantiate and populate a [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) object with the new values.</span></span> <span data-ttu-id="b6461-120">Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b6461-120">Then use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="b6461-121">Em seguida, obtenha uma interface para as operações de subscrição ligando para o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID de subscrição.</span><span class="sxs-lookup"><span data-stu-id="b6461-121">Next, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="b6461-122">Em seguida, utilize a propriedade [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) para obter uma interface para suportar operações de contacto.</span><span class="sxs-lookup"><span data-stu-id="b6461-122">Then, use the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) property to obtain an interface to support contact operations.</span></span> <span data-ttu-id="b6461-123">Por fim, contacte o método [**Update**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.update) ou [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.updateasync) com o objeto SupportContact povoado para atualizar o contacto de suporte.</span><span class="sxs-lookup"><span data-stu-id="b6461-123">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.update) or [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.updateasync) method with the populated SupportContact object to update the support contact.</span></span>

``` csharp
// IAggregatePartner partnerOperations.
// string customerId;
// string subscriptionId;

// Instantiate a SupportContact object and populate it with the new support contact information.
var supportContact = new SupportContact()
{
    Name = "Support contact's name",
    SupportTenantId = "Support contact's tenant ID",
    SupportMpnId = "Support contact's MPN ID"
};

// Update the support contact with a new object that has valid VAR values.
var updatedSupportContact = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionID).SupportContact.Update(supportContact);
```

<span data-ttu-id="b6461-124">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b6461-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b6461-125">**Project**: Partner Center SDK Samples **Class**: UpdateSubscriptionSupportContact.cs</span><span class="sxs-lookup"><span data-stu-id="b6461-125">**Project**: Partner Center SDK Samples **Class**: UpdateSubscriptionSupportContact.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b6461-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b6461-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b6461-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6461-127">Request syntax</span></span>

| <span data-ttu-id="b6461-128">Método</span><span class="sxs-lookup"><span data-stu-id="b6461-128">Method</span></span>  | <span data-ttu-id="b6461-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b6461-129">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b6461-130">**PUT**</span><span class="sxs-lookup"><span data-stu-id="b6461-130">**PUT**</span></span> | <span data-ttu-id="b6461-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/supportcontact HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b6461-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/supportcontact HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="b6461-132">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="b6461-132">URI parameter</span></span>

<span data-ttu-id="b6461-133">Utilize os seguintes parâmetros de percurso para identificar o cliente e a subscrição.</span><span class="sxs-lookup"><span data-stu-id="b6461-133">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="b6461-134">Nome</span><span class="sxs-lookup"><span data-stu-id="b6461-134">Name</span></span>            | <span data-ttu-id="b6461-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="b6461-135">Type</span></span>   | <span data-ttu-id="b6461-136">Necessário</span><span class="sxs-lookup"><span data-stu-id="b6461-136">Required</span></span> | <span data-ttu-id="b6461-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6461-137">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="b6461-138">id cliente</span><span class="sxs-lookup"><span data-stu-id="b6461-138">customer-id</span></span>     | <span data-ttu-id="b6461-139">string</span><span class="sxs-lookup"><span data-stu-id="b6461-139">string</span></span> | <span data-ttu-id="b6461-140">Yes</span><span class="sxs-lookup"><span data-stu-id="b6461-140">Yes</span></span>      | <span data-ttu-id="b6461-141">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="b6461-141">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="b6461-142">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="b6461-142">subscription-id</span></span> | <span data-ttu-id="b6461-143">string</span><span class="sxs-lookup"><span data-stu-id="b6461-143">string</span></span> | <span data-ttu-id="b6461-144">Yes</span><span class="sxs-lookup"><span data-stu-id="b6461-144">Yes</span></span>      | <span data-ttu-id="b6461-145">Uma cadeia formatada GUID que identifica a subscrição do ensaio.</span><span class="sxs-lookup"><span data-stu-id="b6461-145">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b6461-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b6461-146">Request headers</span></span>

<span data-ttu-id="b6461-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b6461-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b6461-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b6461-148">Request body</span></span>

<span data-ttu-id="b6461-149">Deve incluir um recurso [SupportContact](subscription-resources.md#supportcontact) povoado no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="b6461-149">You must include a populated [SupportContact](subscription-resources.md#supportcontact) resource in the request body.</span></span> <span data-ttu-id="b6461-150">O contacto de apoio deve ser um revendedor existente com uma relação com o parceiro.</span><span class="sxs-lookup"><span data-stu-id="b6461-150">The support contact must be an existing reseller with a relationship to the partner.</span></span>

### <a name="request-example"></a><span data-ttu-id="b6461-151">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b6461-151">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b72d732a-eed7-4a60-82d1-1b2e6cba0ed2
MS-CorrelationId: 84eff9e1-6a8c-42aa-8678-c00b0d3fb26f
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 320
Expect: 100-continue

{
    "SupportTenantId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "SupportMpnId": "4391507",
    "Name": "Trey Research",
    "Links": {
        "Self": {
            "Uri": "/customers/0C39D6D5-C70D-4C55-BC02-F620844F3FD1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact",
            "Method": "Get",
            "Headers": []
        }
    },
    "Attributes": {
        "ObjectType": "SupportContact"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="b6461-152">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b6461-152">REST response</span></span>

<span data-ttu-id="b6461-153">Se for bem sucedido, o organismo de resposta contém o recurso [SupportContact.](subscription-resources.md#supportcontact)</span><span class="sxs-lookup"><span data-stu-id="b6461-153">If successful, the response body contains the [SupportContact](subscription-resources.md#supportcontact) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b6461-154">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b6461-154">Response success and error codes</span></span>

<span data-ttu-id="b6461-155">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b6461-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b6461-156">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b6461-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b6461-157">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b6461-157">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b6461-158">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b6461-158">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 328
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b0cd9bcc-742e-4c76-9e34-a96d3bdc7673
MS-RequestId: 7591ca22-d4e3-409d-bfa6-09806eaff4f3
MS-CV: W8Tzj6NGckKHcq+E.0
MS-ServerId: 030020344
Date: Wed, 21 Jun 2017 01:01:17 GMT

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
