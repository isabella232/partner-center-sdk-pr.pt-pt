---
title: Remover uma relação de revendedor com um cliente
description: Como remover uma relação de revendedor com um cliente com o qual já não tem transações.
ms.date: 01/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 084797997e57c63b5c447379bb08ecb88ebd0cc4
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769602"
---
# <a name="remove-a-reseller-relationship-with-a-customer"></a><span data-ttu-id="2fd19-103">Remover uma relação de revendedor com um cliente</span><span class="sxs-lookup"><span data-stu-id="2fd19-103">Remove a reseller relationship with a customer</span></span>

<span data-ttu-id="2fd19-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="2fd19-104">**Applies To**</span></span>

- <span data-ttu-id="2fd19-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="2fd19-105">Partner Center</span></span>

<span data-ttu-id="2fd19-106">Remova uma relação de revendedor com um cliente com o quais já não tenha transações.</span><span class="sxs-lookup"><span data-stu-id="2fd19-106">Remove a reseller relationship with a customer that you no longer have transactions with.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2fd19-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2fd19-107">Prerequisites</span></span>

- <span data-ttu-id="2fd19-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2fd19-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2fd19-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="2fd19-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="2fd19-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2fd19-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="2fd19-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="2fd19-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="2fd19-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="2fd19-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="2fd19-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="2fd19-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="2fd19-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="2fd19-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="2fd19-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2fd19-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="2fd19-116">Todas as ordens de Azure Reserved VM Instance devem ser canceladas antes de uma relação de revendedor ser removida.</span><span class="sxs-lookup"><span data-stu-id="2fd19-116">All Azure Reserved VM Instance orders must be canceled before a reseller relationship is removed.</span></span> <span data-ttu-id="2fd19-117">Ligue para o suporte da Azure para cancelar quaisquer ordens de Azure Reserved VM Instance.</span><span class="sxs-lookup"><span data-stu-id="2fd19-117">Call Azure support for canceling any open Azure Reserved VM Instance orders.</span></span>

## <a name="c"></a><span data-ttu-id="2fd19-118">C\#</span><span class="sxs-lookup"><span data-stu-id="2fd19-118">C\#</span></span>

<span data-ttu-id="2fd19-119">Para remover a relação de revendedor para um cliente, certifique-se primeiro de que quaisquer instâncias VM reservadas ativas para esse cliente são canceladas.</span><span class="sxs-lookup"><span data-stu-id="2fd19-119">To remove the reseller relationship for a customer, first ensure that any active Azure Reserved VM Instances for that customer are canceled.</span></span> <span data-ttu-id="2fd19-120">Em seguida, certifique-se de que todas as subscrições ativas para esse cliente estão suspensas.</span><span class="sxs-lookup"><span data-stu-id="2fd19-120">Next, ensure that all active subscriptions for that customer are suspended.</span></span> <span data-ttu-id="2fd19-121">Para tal, determine o ID do cliente para quem pretende eliminar a relação do revendedor.</span><span class="sxs-lookup"><span data-stu-id="2fd19-121">To do so, determine the ID of the customer for whom you want to delete the reseller relationship.</span></span> <span data-ttu-id="2fd19-122">No seguinte exemplo de código, o utilizador é solicitado a fornecer o identificador do cliente.</span><span class="sxs-lookup"><span data-stu-id="2fd19-122">In the following code example, the user is prompted to provide the customer identifier.</span></span>

<span data-ttu-id="2fd19-123">Para determinar se quaisquer instâncias VM Reservadas Azure para o cliente devem ser canceladas, recupere a recolha de direitos ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) utilizando o identificador de clientes para especificar o cliente, e a propriedade Entitlements para recuperar uma interface para operações de cobrança de [**direitos.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions)</span><span class="sxs-lookup"><span data-stu-id="2fd19-123">To determine if any Azure Reserved VM Instances for the customer must be canceled, retrieve the collection of entitlements by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and the [**Entitlements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to entitlement collection operations.</span></span> <span data-ttu-id="2fd19-124">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) para recuperar a coleção de direitos.</span><span class="sxs-lookup"><span data-stu-id="2fd19-124">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) method to retrieve the entitlement collection.</span></span> <span data-ttu-id="2fd19-125">Filtrar a coleção para quaisquer direitos com um valor [**EntitlementType**](entitlement-resources.md#entitlementtype) de [**EntitlementType.VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) e, se houver, cancele-os chamando o apoio antes de prosseguir.</span><span class="sxs-lookup"><span data-stu-id="2fd19-125">Filter the collection for any entitlements with an [**EntitlementType**](entitlement-resources.md#entitlementtype) value of [**EntitlementType.VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) and if there are any, cancel them by calling support before proceeding.</span></span>

<span data-ttu-id="2fd19-126">Em seguida, recupere uma coleção das subscrições do cliente ligando para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) utilizando o identificador de clientes para especificar o cliente, e a propriedade [**de Subscrições**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) para recuperar uma interface para operações de recolha de subscrição.</span><span class="sxs-lookup"><span data-stu-id="2fd19-126">Then, retrieve a collection of the customer's subscriptions by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to subscription collection operations.</span></span> <span data-ttu-id="2fd19-127">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) para recuperar a recolha de subscrições do cliente.</span><span class="sxs-lookup"><span data-stu-id="2fd19-127">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) method to retrieve the customer's subscriptions collection.</span></span> <span data-ttu-id="2fd19-128">Traverse a coleção de subscrição e certifique-se de que nenhuma das subscrições tem um valor de propriedade [**subscrição.Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) do [**SubscriptionStatus.Ative**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span><span class="sxs-lookup"><span data-stu-id="2fd19-128">Traverse the subscription collection and ensure that none of the subscriptions have a [**Subscriptions.Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property value of [**SubscriptionStatus.Active**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span> <span data-ttu-id="2fd19-129">Se uma subscrição ainda estiver ativa, consulte [suspender uma subscrição](https://review.docs.microsoft.com/partner-center/develop/suspend-a-subscription) para obter informações sobre como suspendê-la.</span><span class="sxs-lookup"><span data-stu-id="2fd19-129">If a subscription is still active, see [Suspend a subscription](https://review.docs.microsoft.com/partner-center/develop/suspend-a-subscription) for information on how to suspend it.</span></span>

<span data-ttu-id="2fd19-130">Depois de confirmar que todas as instâncias ativas do Azure Reserved VM para esse cliente são canceladas e todas as subscrições ativas estão suspensas, pode remover a relação de revendedor para o cliente.</span><span class="sxs-lookup"><span data-stu-id="2fd19-130">After confirming that all active Azure Reserved VM Instances for that customer are canceled and all active subscriptions are suspended, you can remove the reseller relationship for the customer.</span></span> <span data-ttu-id="2fd19-131">Em primeiro lugar, crie um novo objeto [Cliente/dotnet/api/microsoft.store.partnercenter.customer.customer.customer. [](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship)</span><span class="sxs-lookup"><span data-stu-id="2fd19-131">First, create a new [Customer/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object with the [Customer.RelationshipToPartner/dotnet/api/microsoft.store.partnercenter.models.customers.customer.relationshiptopartner) property set to [**CustomerPartnerRelationship.None**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship).</span></span> <span data-ttu-id="2fd19-132">Em seguida, ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) utilizando o identificador de clientes para especificar o cliente e ligar para o método **Patch,** passando no novo objeto do cliente.</span><span class="sxs-lookup"><span data-stu-id="2fd19-132">Then call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and call the **Patch** method, passing in the new customer object.</span></span>

<span data-ttu-id="2fd19-133">Para restabelecer a relação, repita o processo de [solicitar uma relação revendedor/parceiro-centro/desenvolver/solicitar-revendedor-relação).</span><span class="sxs-lookup"><span data-stu-id="2fd19-133">To re-establish the relationship, repeat the process of [requesting a reseller relationship/partner-center/develop/request-reseller-relationship).</span></span>

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

<span data-ttu-id="2fd19-134">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="2fd19-134">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="2fd19-135">**Projeto**: PartnerSDK.FeatureSample **Class**: DeletePartnerCustomerRelationship.cs</span><span class="sxs-lookup"><span data-stu-id="2fd19-135">**Project**: PartnerSDK.FeatureSample **Class**: DeletePartnerCustomerRelationship.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="2fd19-136">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2fd19-136">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2fd19-137">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fd19-137">Request syntax</span></span>

| <span data-ttu-id="2fd19-138">Método</span><span class="sxs-lookup"><span data-stu-id="2fd19-138">Method</span></span>     | <span data-ttu-id="2fd19-139">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2fd19-139">Request URI</span></span>                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2fd19-140">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="2fd19-140">**PATCH**</span></span>  | <span data-ttu-id="2fd19-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2fd19-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/ HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="2fd19-142">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="2fd19-142">URI parameter</span></span>

<span data-ttu-id="2fd19-143">Esta tabela lista os parâmetros de consulta necessários para remover uma relação de revendedor.</span><span class="sxs-lookup"><span data-stu-id="2fd19-143">This table lists the required query parameters to remove a reseller relationship.</span></span>

| <span data-ttu-id="2fd19-144">Nome</span><span class="sxs-lookup"><span data-stu-id="2fd19-144">Name</span></span>                   | <span data-ttu-id="2fd19-145">Tipo</span><span class="sxs-lookup"><span data-stu-id="2fd19-145">Type</span></span>     | <span data-ttu-id="2fd19-146">Necessário</span><span class="sxs-lookup"><span data-stu-id="2fd19-146">Required</span></span> | <span data-ttu-id="2fd19-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fd19-147">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="2fd19-148">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="2fd19-148">**customer-tenant-id**</span></span> | <span data-ttu-id="2fd19-149">**guid**</span><span class="sxs-lookup"><span data-stu-id="2fd19-149">**guid**</span></span> | <span data-ttu-id="2fd19-150">Y</span><span class="sxs-lookup"><span data-stu-id="2fd19-150">Y</span></span>        | <span data-ttu-id="2fd19-151">O valor é um **design de cliente-inquilino-inquilino** formatado guid que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="2fd19-151">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2fd19-152">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2fd19-152">Request headers</span></span>

<span data-ttu-id="2fd19-153">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2fd19-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2fd19-154">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="2fd19-154">Request body</span></span>

<span data-ttu-id="2fd19-155">É necessário um recurso **do Cliente** no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="2fd19-155">A **Customer** resource is required in the request body.</span></span> <span data-ttu-id="2fd19-156">Certifique-se de que a propriedade **RelationshipToPartner** não foi definida para nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2fd19-156">Ensure the **RelationshipToPartner** property has been set to none.</span></span>

### <a name="request-example"></a><span data-ttu-id="2fd19-157">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="2fd19-157">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="2fd19-158">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2fd19-158">REST response</span></span>

<span data-ttu-id="2fd19-159">Se for bem sucedido, este método remove uma relação de revendedor para o cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="2fd19-159">If successful, this method removes a reseller relationship for the specified customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2fd19-160">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2fd19-160">Response success and error codes</span></span>

<span data-ttu-id="2fd19-161">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2fd19-161">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2fd19-162">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2fd19-162">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2fd19-163">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2fd19-163">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2fd19-164">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="2fd19-164">Response example</span></span>

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
