---
title: Eliminar uma conta de cliente do sandbox de integração
description: Como eliminar uma conta de cliente da caixa de areia de integração Test in Production (Tip).
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b9d9e44ac9c40bd4e3c7e1a9e04253f853dfd96c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973133"
---
# <a name="delete-a-customer-account-from-the-integration-sandbox"></a><span data-ttu-id="788c2-103">Eliminar uma conta de cliente do sandbox de integração</span><span class="sxs-lookup"><span data-stu-id="788c2-103">Delete a customer account from the integration sandbox</span></span>

<span data-ttu-id="788c2-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="788c2-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="788c2-105">Este artigo explica como quebrar a relação entre o parceiro e a conta do cliente e recuperar a quota de Testes em Produção (Dica) de integração de areia.</span><span class="sxs-lookup"><span data-stu-id="788c2-105">This article explains, how to break the relationship between the partner and the customer account and regain the quota for Testing in Production (Tip) integration sandbox.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="788c2-106">Quando eliminar uma conta de cliente, todos os recursos associados a esse inquilino do cliente serão purgados.</span><span class="sxs-lookup"><span data-stu-id="788c2-106">When you delete a customer account, all resources associated with that customer tenant will be purged.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="788c2-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="788c2-107">Prerequisites</span></span>

- <span data-ttu-id="788c2-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="788c2-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="788c2-109">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="788c2-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="788c2-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="788c2-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="788c2-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="788c2-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="788c2-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="788c2-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="788c2-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="788c2-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="788c2-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="788c2-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="788c2-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="788c2-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="788c2-116">Todas as instâncias de compra de máquinas virtuais reservadas Azure e as ordens de compra de software devem ser canceladas antes de eliminar um cliente da caixa de areia de integração da Ponta.</span><span class="sxs-lookup"><span data-stu-id="788c2-116">All Azure Reserved Virtual Machine Instances and software purchase orders must be canceled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="c"></a><span data-ttu-id="788c2-117">C\#</span><span class="sxs-lookup"><span data-stu-id="788c2-117">C\#</span></span>

<span data-ttu-id="788c2-118">Para eliminar um cliente da caixa de areia de integração da Ponta:</span><span class="sxs-lookup"><span data-stu-id="788c2-118">To delete a customer from the Tip integration sandbox:</span></span>

1. <span data-ttu-id="788c2-119">Passe as credenciais de conta De ponta para o método [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) para obter uma interface [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) para operações parceiras.</span><span class="sxs-lookup"><span data-stu-id="788c2-119">Pass your Tip account credentials to the [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to partner operations.</span></span>

2. <span data-ttu-id="788c2-120">Utilize a interface de operações do parceiro para recuperar a recolha de direitos:</span><span class="sxs-lookup"><span data-stu-id="788c2-120">Use the partner operations interface to retrieve the collection of entitlements:</span></span>

    1. <span data-ttu-id="788c2-121">Ligue para o método [**Clientes.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes para especificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="788c2-121">Call the [**Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to specify the customer.</span></span>

    2. <span data-ttu-id="788c2-122">Ligue para a propriedade **Entitlements.**</span><span class="sxs-lookup"><span data-stu-id="788c2-122">Call the **Entitlements** property.</span></span>

    3. <span data-ttu-id="788c2-123">Ligue para o método **Get** or **GetAsync** para recuperar a coleção [**Entitlement.**](entitlement-resources.md)</span><span class="sxs-lookup"><span data-stu-id="788c2-123">Call the **Get** or **GetAsync** method to retrieve the [**Entitlement**](entitlement-resources.md) collection.</span></span>

3. <span data-ttu-id="788c2-124">Certifique-se de que todas as instâncias de compra de máquinas virtuais reservadas a Azure e as encomendas de compra de software para esse cliente estão canceladas.</span><span class="sxs-lookup"><span data-stu-id="788c2-124">Make sure that all Azure Reserved Virtual Machine Instances and software purchase orders for that customer are canceled.</span></span> <span data-ttu-id="788c2-125">Para cada [**Direito**](entitlement-resources.md) na coleção:</span><span class="sxs-lookup"><span data-stu-id="788c2-125">For each [**Entitlement**](entitlement-resources.md) in the collection:</span></span>

    1. <span data-ttu-id="788c2-126">Use o [**direito. ReferenceOrder.Id**](entitlement-resources.md#referenceorder) obter uma cópia local da [Encomenda](order-resources.md#order) correspondente da recolha de encomendas do cliente.</span><span class="sxs-lookup"><span data-stu-id="788c2-126">Use the [**entitlement.ReferenceOrder.Id**](entitlement-resources.md#referenceorder) to get a local copy of the corresponding [Order](order-resources.md#order) from the customer's collection of orders.</span></span>

    2. <span data-ttu-id="788c2-127">Desa estada a [**propriedade Order.Status**](order-resources.md#order) para "Cancelado".</span><span class="sxs-lookup"><span data-stu-id="788c2-127">Set the [**Order.Status**](order-resources.md#order) property to "Cancelled".</span></span>

    3. <span data-ttu-id="788c2-128">Utilize o método **Patch()** para atualizar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="788c2-128">Use the **Patch()** method to update the order.</span></span>

4. <span data-ttu-id="788c2-129">Cancele todas as encomendas.</span><span class="sxs-lookup"><span data-stu-id="788c2-129">Cancel all orders.</span></span> <span data-ttu-id="788c2-130">Por exemplo, a seguinte amostra de código utiliza um loop para sondar cada encomenda até que o seu estado seja "Cancelado".</span><span class="sxs-lookup"><span data-stu-id="788c2-130">For example, the following code sample uses a loop to poll each order until its status is "Cancelled".</span></span>

    ``` csharp
    // IPartnerCredentials tipAccountCredentials;
    // Customer tenant Id to be deleted.
    // string customerTenantId;

    IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

    // Get all entitlements whose order must be canceled.
    ResourceCollection<Entitlement> entitlements = tipAccountPartnerOperations.Customers.ById(customerTenantId).Entitlements.Get();

    // Cancel all orders
    foreach (var entitlement in entitlements)
    {
        var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(entitlement.ReferenceOrder.Id).Get();
        order.Status = "Cancelled";
        order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(order.Id).Patch(order);
    }

    // Keep polling until the status of all orders is "Cancelled".
    bool proceed = true;
    do
    {
        // Check if all the orders were canceled.
        foreach (var entitlement in entitlements)
        {
            var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(entitlement.ReferenceOrder.Id).Get();
            if (!order.Status.Equals("Cancelled", StringComparison.OrdinalIgnoreCase))
            {
                proceed = false;
            }
        }

        // Wait for a few seconds.
        Thread.Sleep(5000);
    }
    while (proceed == false);

    tipAccountPartnerOperations.Customers.ById(customerTenantId).Delete();
    ```

5. <span data-ttu-id="788c2-131">Certifique-se de que todas as encomendas são canceladas ligando para o método **Eliminar** para o cliente.</span><span class="sxs-lookup"><span data-stu-id="788c2-131">Make sure all orders are canceled by calling the **Delete** method for the customer.</span></span>

<span data-ttu-id="788c2-132">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="788c2-132">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="788c2-133">**Project**: Partner Center PartnerCenterSDK.FeaturesSamples **Class**: DeleteCustomerFromTipAccount.cs</span><span class="sxs-lookup"><span data-stu-id="788c2-133">**Project**: Partner Center PartnerCenterSDK.FeaturesSamples **Class**: DeleteCustomerFromTipAccount.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="788c2-134">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="788c2-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="788c2-135">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="788c2-135">Request syntax</span></span>

| <span data-ttu-id="788c2-136">Método</span><span class="sxs-lookup"><span data-stu-id="788c2-136">Method</span></span>     | <span data-ttu-id="788c2-137">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="788c2-137">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="788c2-138">DELETE</span><span class="sxs-lookup"><span data-stu-id="788c2-138">DELETE</span></span>     | <span data-ttu-id="788c2-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="788c2-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="788c2-140">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="788c2-140">URI parameter</span></span>

<span data-ttu-id="788c2-141">Utilize o seguinte parâmetro de consulta para eliminar um cliente.</span><span class="sxs-lookup"><span data-stu-id="788c2-141">Use the following query parameter to delete a customer.</span></span>

| <span data-ttu-id="788c2-142">Nome</span><span class="sxs-lookup"><span data-stu-id="788c2-142">Name</span></span>                   | <span data-ttu-id="788c2-143">Tipo</span><span class="sxs-lookup"><span data-stu-id="788c2-143">Type</span></span>     | <span data-ttu-id="788c2-144">Necessário</span><span class="sxs-lookup"><span data-stu-id="788c2-144">Required</span></span> | <span data-ttu-id="788c2-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="788c2-145">Description</span></span>                                                                         |
|------------------------|----------|----------|-------------------------------------------------------------------------------------|
| <span data-ttu-id="788c2-146">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="788c2-146">customer-tenant-id</span></span>     | <span data-ttu-id="788c2-147">GUID</span><span class="sxs-lookup"><span data-stu-id="788c2-147">GUID</span></span>     | <span data-ttu-id="788c2-148">Y</span><span class="sxs-lookup"><span data-stu-id="788c2-148">Y</span></span>        | <span data-ttu-id="788c2-149">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="788c2-149">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="788c2-150">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="788c2-150">Request headers</span></span>

<span data-ttu-id="788c2-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="788c2-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="788c2-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="788c2-152">Request body</span></span>

<span data-ttu-id="788c2-153">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="788c2-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="788c2-154">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="788c2-154">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="788c2-155">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="788c2-155">REST response</span></span>

<span data-ttu-id="788c2-156">Se for bem sucedido, este método devolve uma resposta vazia.</span><span class="sxs-lookup"><span data-stu-id="788c2-156">If successful, this method returns an empty response.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="788c2-157">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="788c2-157">Response success and error codes</span></span>

<span data-ttu-id="788c2-158">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="788c2-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="788c2-159">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="788c2-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="788c2-160">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="788c2-160">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="788c2-161">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="788c2-161">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Mar 2016 00:43:02 GMT
```
