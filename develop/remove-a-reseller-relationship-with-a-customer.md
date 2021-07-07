---
title: Remover uma relação de revendedor com um cliente
description: Como remover uma relação de revendedor com um cliente com o qual já não tem transações.
ms.date: 01/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 45eca3564c3b9078e04d1f8155d08849a589d52f
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446603"
---
# <a name="remove-a-reseller-relationship-with-a-customer"></a><span data-ttu-id="02e18-103">Remover uma relação de revendedor com um cliente</span><span class="sxs-lookup"><span data-stu-id="02e18-103">Remove a reseller relationship with a customer</span></span>

<span data-ttu-id="02e18-104">Remova uma relação de revendedor com um cliente com o quais já não tenha transações.</span><span class="sxs-lookup"><span data-stu-id="02e18-104">Remove a reseller relationship with a customer that you no longer have transactions with.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="02e18-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="02e18-105">Prerequisites</span></span>

- <span data-ttu-id="02e18-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="02e18-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="02e18-107">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="02e18-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="02e18-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="02e18-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="02e18-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="02e18-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="02e18-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="02e18-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="02e18-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="02e18-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="02e18-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="02e18-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="02e18-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="02e18-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="02e18-114">Todas as ordens de Azure Reserved VM Instance devem ser canceladas antes de uma relação de revendedor ser removida.</span><span class="sxs-lookup"><span data-stu-id="02e18-114">All Azure Reserved VM Instance orders must be canceled before a reseller relationship is removed.</span></span> <span data-ttu-id="02e18-115">Ligue para o suporte da Azure para cancelar quaisquer ordens de Azure Reserved VM Instance.</span><span class="sxs-lookup"><span data-stu-id="02e18-115">Call Azure support for canceling any open Azure Reserved VM Instance orders.</span></span>

## <a name="c"></a><span data-ttu-id="02e18-116">C\#</span><span class="sxs-lookup"><span data-stu-id="02e18-116">C\#</span></span>

<span data-ttu-id="02e18-117">Para remover a relação de revendedor para um cliente, certifique-se primeiro de que quaisquer instâncias VM reservadas ativas para esse cliente são canceladas.</span><span class="sxs-lookup"><span data-stu-id="02e18-117">To remove the reseller relationship for a customer, first ensure that any active Azure Reserved VM Instances for that customer are canceled.</span></span> <span data-ttu-id="02e18-118">Em seguida, certifique-se de que todas as subscrições ativas para esse cliente estão suspensas.</span><span class="sxs-lookup"><span data-stu-id="02e18-118">Next, ensure that all active subscriptions for that customer are suspended.</span></span> <span data-ttu-id="02e18-119">Para tal, determine o ID do cliente para quem pretende eliminar a relação do revendedor.</span><span class="sxs-lookup"><span data-stu-id="02e18-119">To do so, determine the ID of the customer for whom you want to delete the reseller relationship.</span></span> <span data-ttu-id="02e18-120">No seguinte exemplo de código, o utilizador é solicitado a fornecer o identificador do cliente.</span><span class="sxs-lookup"><span data-stu-id="02e18-120">In the following code example, the user is prompted to provide the customer identifier.</span></span>

<span data-ttu-id="02e18-121">Para determinar se quaisquer instâncias VM Reservadas Azure para o cliente devem ser canceladas, recupere a recolha de direitos ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) utilizando o identificador de clientes para especificar o cliente, e a propriedade Entitlements para recuperar uma interface para operações de cobrança de [**direitos.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions)</span><span class="sxs-lookup"><span data-stu-id="02e18-121">To determine if any Azure Reserved VM Instances for the customer must be canceled, retrieve the collection of entitlements by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and the [**Entitlements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to entitlement collection operations.</span></span> <span data-ttu-id="02e18-122">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) para recuperar a coleção de direitos.</span><span class="sxs-lookup"><span data-stu-id="02e18-122">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) method to retrieve the entitlement collection.</span></span> <span data-ttu-id="02e18-123">Filtrar a coleção para quaisquer direitos com um valor [**EntitlementType**](entitlement-resources.md#entitlementtype) de [**EntitlementType.VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) e, se houver, cancele-os chamando o apoio antes de prosseguir.</span><span class="sxs-lookup"><span data-stu-id="02e18-123">Filter the collection for any entitlements with an [**EntitlementType**](entitlement-resources.md#entitlementtype) value of [**EntitlementType.VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) and if there are any, cancel them by calling support before proceeding.</span></span>

<span data-ttu-id="02e18-124">Em seguida, recupere uma coleção das subscrições do cliente ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) utilizando o identificador de clientes para especificar o cliente, e a propriedade [**de Subscrições**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) para recuperar uma interface para operações de recolha de subscrição.</span><span class="sxs-lookup"><span data-stu-id="02e18-124">Then, retrieve a collection of the customer's subscriptions by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to subscription collection operations.</span></span> <span data-ttu-id="02e18-125">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) para recuperar a recolha de subscrições do cliente.</span><span class="sxs-lookup"><span data-stu-id="02e18-125">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) method to retrieve the customer's subscriptions collection.</span></span> <span data-ttu-id="02e18-126">Traverse a coleção de subscrição e certifique-se de que nenhuma das subscrições tem um valor de propriedade [**subscrição.Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) do [**SubscriptionStatus.Ative**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span><span class="sxs-lookup"><span data-stu-id="02e18-126">Traverse the subscription collection and ensure that none of the subscriptions have a [**Subscriptions.Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property value of [**SubscriptionStatus.Active**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span> <span data-ttu-id="02e18-127">Se uma subscrição ainda estiver ativa, consulte [suspender uma subscrição](suspend-a-subscription.md) para obter informações sobre como suspendê-la.</span><span class="sxs-lookup"><span data-stu-id="02e18-127">If a subscription is still active, see [Suspend a subscription](suspend-a-subscription.md) for information on how to suspend it.</span></span>

<span data-ttu-id="02e18-128">Depois de confirmar que todas as instâncias ativas do Azure Reserved VM para esse cliente são canceladas e todas as subscrições ativas estão suspensas, pode remover a relação de revendedor para o cliente.</span><span class="sxs-lookup"><span data-stu-id="02e18-128">After confirming that all active Azure Reserved VM Instances for that customer are canceled and all active subscriptions are suspended, you can remove the reseller relationship for the customer.</span></span> <span data-ttu-id="02e18-129">Em primeiro lugar, crie um novo objeto [Cliente/dotnet/api/microsoft.store.partnercenter.customer.customer.customer. [](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship)</span><span class="sxs-lookup"><span data-stu-id="02e18-129">First, create a new [Customer/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object with the [Customer.RelationshipToPartner/dotnet/api/microsoft.store.partnercenter.models.customers.customer.relationshiptopartner) property set to [**CustomerPartnerRelationship.None**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship).</span></span> <span data-ttu-id="02e18-130">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) utilizando o identificador de clientes para especificar o cliente e ligar para o método **Patch,** passando no novo objeto do cliente.</span><span class="sxs-lookup"><span data-stu-id="02e18-130">Then call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and call the **Patch** method, passing in the new customer object.</span></span>

<span data-ttu-id="02e18-131">Para restabelecer a relação, repita o processo de [solicitar uma relação revendedor/parceiro-centro/desenvolver/solicitar-revendedor-relação).</span><span class="sxs-lookup"><span data-stu-id="02e18-131">To re-establish the relationship, repeat the process of [requesting a reseller relationship/partner-center/develop/request-reseller-relationship).</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// Prompt the user the enter the customer ID.
var customerIdToDeleteRelationshipOf = this.Context.ConsoleHelper.ReadNonEmptyString("Please enter the ID of the customer you want to delete the relationship with", "The customer ID can't be empty");

// Determine if there are any active Azure Reserved VM Instances for this customer.
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Entitlements.Get();

If (entitlements.Items.Where(x => x.EntitlementType == EntitlementType.VirtualMachineReservedInstance).Any())
{
    this.Context.ConsoleHelper.Warning("Please cancel Azure Reserved Virtual Machine Instance orders through support and try again. Aborting the delete customer relationship operation");
               return;
}

// Verify that there are no active subscriptions.
ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Subscriptions.Get();
IList<Subscription> subscriptions = new List<Subscription>(customerSubscriptions.Items);

foreach (Subscription customerSubscription in subscriptions)
{
    if (customerSubscription.Status == SubscriptionStatus.Active)
    {
        this.Context.ConsoleHelper.Warning(String.Format("Subscription with ID :{0}  OfferName: {1} cannot be in active state, ", customerSubscription.Id, customerSubscription.OfferName));
        this.Context.ConsoleHelper.Warning("Please Suspend all the Subscriptions and try again. Aborting the delete customer relationship operation");
               return;
    }
}

// Delete the customer's relationship to the partner.
Customer customer = new Customer();
customer.RelationshipToPartner = CustomerPartnerRelationship.None;
customer = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Patch(customer);

if (customer.RelationshipToPartner == CustomerPartnerRelationship.None)
{
    this.Context.ConsoleHelper.Success("Customer Partner Relationship successfully deleted");
}
```

<span data-ttu-id="02e18-132">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="02e18-132">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="02e18-133">**Project**: PartnerSDK.FeatureSample **Class**: DeletePartnerCustomerRelationship.cs</span><span class="sxs-lookup"><span data-stu-id="02e18-133">**Project**: PartnerSDK.FeatureSample **Class**: DeletePartnerCustomerRelationship.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="02e18-134">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="02e18-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="02e18-135">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="02e18-135">Request syntax</span></span>

| <span data-ttu-id="02e18-136">Método</span><span class="sxs-lookup"><span data-stu-id="02e18-136">Method</span></span>     | <span data-ttu-id="02e18-137">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="02e18-137">Request URI</span></span>                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="02e18-138">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="02e18-138">**PATCH**</span></span>  | <span data-ttu-id="02e18-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="02e18-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/ HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="02e18-140">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="02e18-140">URI parameter</span></span>

<span data-ttu-id="02e18-141">Esta tabela lista os parâmetros de consulta necessários para remover uma relação de revendedor.</span><span class="sxs-lookup"><span data-stu-id="02e18-141">This table lists the required query parameters to remove a reseller relationship.</span></span>

| <span data-ttu-id="02e18-142">Nome</span><span class="sxs-lookup"><span data-stu-id="02e18-142">Name</span></span>                   | <span data-ttu-id="02e18-143">Tipo</span><span class="sxs-lookup"><span data-stu-id="02e18-143">Type</span></span>     | <span data-ttu-id="02e18-144">Necessário</span><span class="sxs-lookup"><span data-stu-id="02e18-144">Required</span></span> | <span data-ttu-id="02e18-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="02e18-145">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="02e18-146">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="02e18-146">**customer-tenant-id**</span></span> | <span data-ttu-id="02e18-147">**guid**</span><span class="sxs-lookup"><span data-stu-id="02e18-147">**guid**</span></span> | <span data-ttu-id="02e18-148">Y</span><span class="sxs-lookup"><span data-stu-id="02e18-148">Y</span></span>        | <span data-ttu-id="02e18-149">O valor é um **design de cliente-inquilino-inquilino** formatado guid que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="02e18-149">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="02e18-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="02e18-150">Request headers</span></span>

<span data-ttu-id="02e18-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="02e18-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="02e18-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="02e18-152">Request body</span></span>

<span data-ttu-id="02e18-153">É necessário um recurso **do Cliente** no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="02e18-153">A **Customer** resource is required in the request body.</span></span> <span data-ttu-id="02e18-154">Certifique-se de que a propriedade **RelationshipToPartner** não foi definida para nenhuma.</span><span class="sxs-lookup"><span data-stu-id="02e18-154">Ensure the **RelationshipToPartner** property has been set to none.</span></span>

### <a name="request-example"></a><span data-ttu-id="02e18-155">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="02e18-155">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Authorization: Bearer <token>
Content-Length: 74
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
MS-RequestId: 9fef8b23-6e3e-45d2-8678-e9fe89c35af5
Date: Fri, 12 Jan 2018 00:31:55 GMT

{
    "relationshipToPartner":"none",
    "attributes":{
        "objectType":"Customer"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="02e18-156">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="02e18-156">REST response</span></span>

<span data-ttu-id="02e18-157">Se for bem sucedido, este método remove uma relação de revendedor para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="02e18-157">If successful, this method removes a reseller relationship for the specified customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="02e18-158">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="02e18-158">Response success and error codes</span></span>

<span data-ttu-id="02e18-159">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="02e18-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="02e18-160">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="02e18-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="02e18-161">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="02e18-161">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="02e18-162">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="02e18-162">Response example</span></span>

```http
HTTP/1.1 200 OK
MS-RequestId: 7988dde4-b516-472c-b226-6d53fb18f04e
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
X-Locale: en-US
Content-Type: application/json
Content-Length: 242
Expect: 100-continue

{
    "Id":null,
    "CommerceId":null,
    "CompanyProfile":null,
    "BillingProfile":null,
    "RelationshipToPartner":"none",
    "AllowDelegatedAccess":null,
    "UserCredentials":null,
    "CustomDomains":null,
    "AssociatedPartnerId":null,
    "Attributes":{
        "ObjectType":"Customer"
    }
}
```
