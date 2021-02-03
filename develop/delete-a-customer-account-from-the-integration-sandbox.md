---
title: Eliminar uma conta de cliente do sandbox de integração
description: Como eliminar uma conta de cliente da caixa de areia de integração Test in Production (Tip).
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e3a1642c0202c174ddd4f65a6aeda2752def9176
ms.sourcegitcommit: b1ff781b67b1d322820bbcac2c583229201a8c07
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "97769422"
---
# <a name="delete-a-customer-account-from-the-integration-sandbox"></a><span data-ttu-id="581ba-103">Eliminar uma conta de cliente do sandbox de integração</span><span class="sxs-lookup"><span data-stu-id="581ba-103">Delete a customer account from the integration sandbox</span></span>

<span data-ttu-id="581ba-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="581ba-104">**Applies to:**</span></span>

- <span data-ttu-id="581ba-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="581ba-105">Partner Center</span></span>
- <span data-ttu-id="581ba-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="581ba-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="581ba-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="581ba-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="581ba-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="581ba-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="581ba-109">Este artigo explica como quebrar a relação entre o parceiro e a conta do cliente e recuperar a quota de Testes em Produção (Dica) de integração de areia.</span><span class="sxs-lookup"><span data-stu-id="581ba-109">This article explains, how to break the relationship between the partner and the customer account and regain the quota for Testing in Production (Tip) integration sandbox.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="581ba-110">Quando eliminar uma conta de cliente, todos os recursos associados a esse inquilino do cliente serão purgados.</span><span class="sxs-lookup"><span data-stu-id="581ba-110">When you delete a customer account, all resources associated with that customer tenant will be purged.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="581ba-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="581ba-111">Prerequisites</span></span>

- <span data-ttu-id="581ba-112">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="581ba-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="581ba-113">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="581ba-113">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="581ba-114">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="581ba-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="581ba-115">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="581ba-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="581ba-116">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="581ba-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="581ba-117">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="581ba-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="581ba-118">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="581ba-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="581ba-119">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="581ba-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="581ba-120">Todas as instâncias de compra de máquinas virtuais reservadas Azure e as ordens de compra de software devem ser canceladas antes de eliminar um cliente da caixa de areia de integração da Dica.</span><span class="sxs-lookup"><span data-stu-id="581ba-120">All Azure Reserved Virtual Machine Instances and software purchase orders must be cancelled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="c"></a><span data-ttu-id="581ba-121">C\#</span><span class="sxs-lookup"><span data-stu-id="581ba-121">C\#</span></span>

<span data-ttu-id="581ba-122">Para eliminar um cliente da caixa de areia de integração da Ponta:</span><span class="sxs-lookup"><span data-stu-id="581ba-122">To delete a customer from the Tip integration sandbox:</span></span>

1. <span data-ttu-id="581ba-123">Passe as credenciais de conta De ponta para o método [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) para obter uma interface [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) para operações parceiras.</span><span class="sxs-lookup"><span data-stu-id="581ba-123">Pass your Tip account credentials to the [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to partner operations.</span></span>

2. <span data-ttu-id="581ba-124">Utilize a interface de operações do parceiro para recuperar a recolha de direitos:</span><span class="sxs-lookup"><span data-stu-id="581ba-124">Use the partner operations interface to retrieve the collection of entitlements:</span></span>

    1. <span data-ttu-id="581ba-125">Ligue para o método [**Clientes.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes para especificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="581ba-125">Call the [**Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to specify the customer.</span></span>

    2. <span data-ttu-id="581ba-126">Ligue para a propriedade **Entitlements.**</span><span class="sxs-lookup"><span data-stu-id="581ba-126">Call the **Entitlements** property.</span></span>

    3. <span data-ttu-id="581ba-127">Ligue para o método **Get** or **GetAsync** para recuperar a coleção [**Entitlement.**](entitlement-resources.md)</span><span class="sxs-lookup"><span data-stu-id="581ba-127">Call the **Get** or **GetAsync** method to retrieve the [**Entitlement**](entitlement-resources.md) collection.</span></span>

3. <span data-ttu-id="581ba-128">Certifique-se de que todas as instâncias de compra de máquinas virtuais reservadas a Azure e as encomendas de compra de software para esse cliente são canceladas.</span><span class="sxs-lookup"><span data-stu-id="581ba-128">Make sure that all Azure Reserved Virtual Machine Instances and software purchase orders for that customer are cancelled.</span></span> <span data-ttu-id="581ba-129">Para cada [**Direito**](entitlement-resources.md) na coleção:</span><span class="sxs-lookup"><span data-stu-id="581ba-129">For each [**Entitlement**](entitlement-resources.md) in the collection:</span></span>

    1. <span data-ttu-id="581ba-130">Use o [**direito. ReferenceOrder.Id**](entitlement-resources.md#referenceorder) obter uma cópia local da [Encomenda](order-resources.md#order) correspondente da recolha de encomendas do cliente.</span><span class="sxs-lookup"><span data-stu-id="581ba-130">Use the [**entitlement.ReferenceOrder.Id**](entitlement-resources.md#referenceorder) to get a local copy of the corresponding [Order](order-resources.md#order) from the customer's collection of orders.</span></span>

    2. <span data-ttu-id="581ba-131">Desa estada a [**propriedade Order.Status**](order-resources.md#order) para "Cancelado".</span><span class="sxs-lookup"><span data-stu-id="581ba-131">Set the [**Order.Status**](order-resources.md#order) property to "Cancelled".</span></span>

    3. <span data-ttu-id="581ba-132">Utilize o método **Patch()** para atualizar a encomenda.</span><span class="sxs-lookup"><span data-stu-id="581ba-132">Use the **Patch()** method to update the order.</span></span>

4. <span data-ttu-id="581ba-133">Cancele todas as encomendas.</span><span class="sxs-lookup"><span data-stu-id="581ba-133">Cancel all orders.</span></span> <span data-ttu-id="581ba-134">Por exemplo, a seguinte amostra de código utiliza um loop para sondar cada encomenda até que o seu estado seja "Cancelado".</span><span class="sxs-lookup"><span data-stu-id="581ba-134">For example, the following code sample uses a loop to poll each order until its status is "Cancelled".</span></span>

    ``` csharp
    // IPartnerCredentials tipAccountCredentials;
    // Customer tenant Id to be deleted.
    // string customerTenantId;

    IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

    // Get all entitlements whose order must be cancelled.
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
        // Check if all the orders were cancelled.
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

5. <span data-ttu-id="581ba-135">Certifique-se de que todas as encomendas são canceladas ligando para o método **Eliminar** para o cliente.</span><span class="sxs-lookup"><span data-stu-id="581ba-135">Make sure all orders are cancelled by calling the **Delete** method for the customer.</span></span>

<span data-ttu-id="581ba-136">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="581ba-136">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="581ba-137">**Projeto**: Partner Center PartnerCenterSDK.FeaturesSamples **Class**: DeleteCustomerFromTipAccount.cs</span><span class="sxs-lookup"><span data-stu-id="581ba-137">**Project**: Partner Center PartnerCenterSDK.FeaturesSamples **Class**: DeleteCustomerFromTipAccount.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="581ba-138">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="581ba-138">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="581ba-139">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="581ba-139">Request syntax</span></span>

| <span data-ttu-id="581ba-140">Método</span><span class="sxs-lookup"><span data-stu-id="581ba-140">Method</span></span>     | <span data-ttu-id="581ba-141">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="581ba-141">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="581ba-142">DELETE</span><span class="sxs-lookup"><span data-stu-id="581ba-142">DELETE</span></span>     | <span data-ttu-id="581ba-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="581ba-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="581ba-144">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="581ba-144">URI parameter</span></span>

<span data-ttu-id="581ba-145">Utilize o seguinte parâmetro de consulta para eliminar um cliente.</span><span class="sxs-lookup"><span data-stu-id="581ba-145">Use the following query parameter to delete a customer.</span></span>

| <span data-ttu-id="581ba-146">Nome</span><span class="sxs-lookup"><span data-stu-id="581ba-146">Name</span></span>                   | <span data-ttu-id="581ba-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="581ba-147">Type</span></span>     | <span data-ttu-id="581ba-148">Necessário</span><span class="sxs-lookup"><span data-stu-id="581ba-148">Required</span></span> | <span data-ttu-id="581ba-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="581ba-149">Description</span></span>                                                                         |
|------------------------|----------|----------|-------------------------------------------------------------------------------------|
| <span data-ttu-id="581ba-150">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="581ba-150">customer-tenant-id</span></span>     | <span data-ttu-id="581ba-151">GUID</span><span class="sxs-lookup"><span data-stu-id="581ba-151">GUID</span></span>     | <span data-ttu-id="581ba-152">Y</span><span class="sxs-lookup"><span data-stu-id="581ba-152">Y</span></span>        | <span data-ttu-id="581ba-153">O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor.</span><span class="sxs-lookup"><span data-stu-id="581ba-153">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="581ba-154">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="581ba-154">Request headers</span></span>

<span data-ttu-id="581ba-155">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="581ba-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="581ba-156">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="581ba-156">Request body</span></span>

<span data-ttu-id="581ba-157">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="581ba-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="581ba-158">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="581ba-158">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="581ba-159">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="581ba-159">REST response</span></span>

<span data-ttu-id="581ba-160">Se for bem sucedido, este método devolve uma resposta vazia.</span><span class="sxs-lookup"><span data-stu-id="581ba-160">If successful, this method returns an empty response.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="581ba-161">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="581ba-161">Response success and error codes</span></span>

<span data-ttu-id="581ba-162">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="581ba-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="581ba-163">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="581ba-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="581ba-164">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="581ba-164">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="581ba-165">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="581ba-165">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Mar 2016 00:43:02 GMT
```
