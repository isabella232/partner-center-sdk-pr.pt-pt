---
title: Atualizar o contacto de suporte de uma subscrição
description: Como atualizar o contacto de suporte de uma subscrição a um dos revendedores de valor acrescentado do parceiro.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c8c6b658cfe6e14c75b0c06b177920ce3eb1b4ed
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769589"
---
# <a name="update-a-subscriptions-support-contact"></a><span data-ttu-id="22a19-103">Atualizar o contacto de suporte de uma subscrição</span><span class="sxs-lookup"><span data-stu-id="22a19-103">Update a subscription's support contact</span></span>

<span data-ttu-id="22a19-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="22a19-104">**Applies To**</span></span>

- <span data-ttu-id="22a19-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="22a19-105">Partner Center</span></span>
- <span data-ttu-id="22a19-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="22a19-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="22a19-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="22a19-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="22a19-108">Como atualizar o contacto de suporte de uma subscrição a um dos revendedores de valor acrescentado do parceiro.</span><span class="sxs-lookup"><span data-stu-id="22a19-108">How to update a subscription's support contact to one of the partner's value added resellers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22a19-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="22a19-109">Prerequisites</span></span>

- <span data-ttu-id="22a19-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="22a19-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="22a19-111">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="22a19-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="22a19-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="22a19-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="22a19-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="22a19-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="22a19-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="22a19-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="22a19-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="22a19-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="22a19-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="22a19-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="22a19-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="22a19-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="22a19-118">Um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="22a19-118">A subscription identifier.</span></span>

- <span data-ttu-id="22a19-119">Informações sobre o novo contacto de suporte: identificador de inquilino, identificador da Microsoft Partner Network e nome.</span><span class="sxs-lookup"><span data-stu-id="22a19-119">Information about the new support contact: tenant identifier, Microsoft Partner Network identifier, and name.</span></span> <span data-ttu-id="22a19-120">O contacto de suporte deve ser um dos revendedores de valor acrescentado do parceiro.</span><span class="sxs-lookup"><span data-stu-id="22a19-120">The support contact must be one of the partner's value added resellers.</span></span>

## <a name="c"></a><span data-ttu-id="22a19-121">C\#</span><span class="sxs-lookup"><span data-stu-id="22a19-121">C\#</span></span>

<span data-ttu-id="22a19-122">Para atualizar o contacto de suporte de uma subscrição, primeiro instantaneamente e povoar um objeto [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) com os novos valores.</span><span class="sxs-lookup"><span data-stu-id="22a19-122">To update a subscription's support contact, first instantiate and populate a [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) object with the new values.</span></span> <span data-ttu-id="22a19-123">Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="22a19-123">Then use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="22a19-124">Em seguida, obtenha uma interface para as operações de subscrição ligando para o método [**Subscrições.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID de subscrição.</span><span class="sxs-lookup"><span data-stu-id="22a19-124">Next, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="22a19-125">Em seguida, utilize a propriedade [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) para obter uma interface para suportar operações de contacto.</span><span class="sxs-lookup"><span data-stu-id="22a19-125">Then, use the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) property to obtain an interface to support contact operations.</span></span> <span data-ttu-id="22a19-126">Por fim, contacte o método [**Update**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.update) ou [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.updateasync) com o objeto SupportContact povoado para atualizar o contacto de suporte.</span><span class="sxs-lookup"><span data-stu-id="22a19-126">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.update) or [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.updateasync) method with the populated SupportContact object to update the support contact.</span></span>

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

<span data-ttu-id="22a19-127">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="22a19-127">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="22a19-128">**Projeto**: Partner Center SDK Samples **Class**: UpdateSubscriptionSupportContact.cs</span><span class="sxs-lookup"><span data-stu-id="22a19-128">**Project**: Partner Center SDK Samples **Class**: UpdateSubscriptionSupportContact.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="22a19-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="22a19-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="22a19-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="22a19-130">Request syntax</span></span>

| <span data-ttu-id="22a19-131">Método</span><span class="sxs-lookup"><span data-stu-id="22a19-131">Method</span></span>  | <span data-ttu-id="22a19-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="22a19-132">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="22a19-133">**PUT**</span><span class="sxs-lookup"><span data-stu-id="22a19-133">**PUT**</span></span> | <span data-ttu-id="22a19-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/subscrições/{subscrição-id}/supportcontact HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="22a19-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/supportcontact HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="22a19-135">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="22a19-135">URI parameter</span></span>

<span data-ttu-id="22a19-136">Utilize os seguintes parâmetros de percurso para identificar o cliente e a subscrição.</span><span class="sxs-lookup"><span data-stu-id="22a19-136">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="22a19-137">Nome</span><span class="sxs-lookup"><span data-stu-id="22a19-137">Name</span></span>            | <span data-ttu-id="22a19-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="22a19-138">Type</span></span>   | <span data-ttu-id="22a19-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="22a19-139">Required</span></span> | <span data-ttu-id="22a19-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="22a19-140">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="22a19-141">id cliente</span><span class="sxs-lookup"><span data-stu-id="22a19-141">customer-id</span></span>     | <span data-ttu-id="22a19-142">string</span><span class="sxs-lookup"><span data-stu-id="22a19-142">string</span></span> | <span data-ttu-id="22a19-143">Sim</span><span class="sxs-lookup"><span data-stu-id="22a19-143">Yes</span></span>      | <span data-ttu-id="22a19-144">Uma cadeia formatada GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="22a19-144">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="22a19-145">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="22a19-145">subscription-id</span></span> | <span data-ttu-id="22a19-146">string</span><span class="sxs-lookup"><span data-stu-id="22a19-146">string</span></span> | <span data-ttu-id="22a19-147">Sim</span><span class="sxs-lookup"><span data-stu-id="22a19-147">Yes</span></span>      | <span data-ttu-id="22a19-148">Uma cadeia formatada GUID que identifica a subscrição do ensaio.</span><span class="sxs-lookup"><span data-stu-id="22a19-148">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="22a19-149">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="22a19-149">Request headers</span></span>

<span data-ttu-id="22a19-150">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="22a19-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="22a19-151">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="22a19-151">Request body</span></span>

<span data-ttu-id="22a19-152">Deve incluir um recurso [SupportContact](subscription-resources.md#supportcontact) povoado no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="22a19-152">You must include a populated [SupportContact](subscription-resources.md#supportcontact) resource in the request body.</span></span> <span data-ttu-id="22a19-153">O contacto de apoio deve ser um revendedor existente com uma relação com o parceiro.</span><span class="sxs-lookup"><span data-stu-id="22a19-153">The support contact must be an existing reseller with a relationship to the partner.</span></span>

### <a name="request-example"></a><span data-ttu-id="22a19-154">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="22a19-154">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="22a19-155">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="22a19-155">REST response</span></span>

<span data-ttu-id="22a19-156">Se for bem sucedido, o organismo de resposta contém o recurso [SupportContact.](subscription-resources.md#supportcontact)</span><span class="sxs-lookup"><span data-stu-id="22a19-156">If successful, the response body contains the [SupportContact](subscription-resources.md#supportcontact) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="22a19-157">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="22a19-157">Response success and error codes</span></span>

<span data-ttu-id="22a19-158">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="22a19-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="22a19-159">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="22a19-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="22a19-160">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="22a19-160">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="22a19-161">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="22a19-161">Response example</span></span>

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
