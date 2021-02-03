---
title: Atribuir licenças a um utilizador
description: Saiba como atribuir licenças a um utilizador do cliente através de APIs do Partner Center, como a utilização de APIs C \# ou REST.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6eb0b953b9157e48074415bb3207e2946cfb2ab4
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2020
ms.locfileid: "97770009"
---
# <a name="assign-licenses-to-a-user-via-partner-center-apis"></a><span data-ttu-id="ce24f-103">Atribuir licenças a um utilizador através de APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="ce24f-103">Assign licenses to a user via Partner Center APIs</span></span>

<span data-ttu-id="ce24f-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="ce24f-104">**Applies to:**</span></span>

- <span data-ttu-id="ce24f-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="ce24f-105">Partner Center</span></span>

<span data-ttu-id="ce24f-106">Como atribuir licenças a um utilizador cliente.</span><span class="sxs-lookup"><span data-stu-id="ce24f-106">How to assign licenses to a customer user.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce24f-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ce24f-107">Prerequisites</span></span>

- <span data-ttu-id="ce24f-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ce24f-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ce24f-109">Este cenário suporta a autenticação apenas com credenciais app+User.</span><span class="sxs-lookup"><span data-stu-id="ce24f-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="ce24f-110">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ce24f-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="ce24f-111">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="ce24f-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="ce24f-112">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="ce24f-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="ce24f-113">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="ce24f-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="ce24f-114">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="ce24f-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="ce24f-115">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ce24f-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="ce24f-116">Um identificador de utilizador de clientes.</span><span class="sxs-lookup"><span data-stu-id="ce24f-116">A customer user identifier.</span></span> <span data-ttu-id="ce24f-117">Esta identificação identifica o utilizador a quem atribuir a licença.</span><span class="sxs-lookup"><span data-stu-id="ce24f-117">This ID identifies the user to whom to assign the license.</span></span>

- <span data-ttu-id="ce24f-118">Um identificador SKU de produto que identifica o produto para a licença.</span><span class="sxs-lookup"><span data-stu-id="ce24f-118">A product SKU identifier that identifies the product for the license.</span></span>

## <a name="assigning-licenses-through-code"></a><span data-ttu-id="ce24f-119">Atribuição de licenças através de código</span><span class="sxs-lookup"><span data-stu-id="ce24f-119">Assigning licenses through code</span></span>

<span data-ttu-id="ce24f-120">Ao atribuir licenças a um utilizador, deve escolher entre a recolha do cliente de SKUs subscritos.</span><span class="sxs-lookup"><span data-stu-id="ce24f-120">When you assign licenses to a user, you must choose from the customer's collection of subscribed SKUs.</span></span> <span data-ttu-id="ce24f-121">Em seguida, depois de ter identificado os produtos que pretende atribuir, tem de obter o produto SKU ID para cada produto para então fazer as atribuições.</span><span class="sxs-lookup"><span data-stu-id="ce24f-121">Then, having identified the products that you want to assign, you must obtain the product SKU ID for each product in order to make the assignments.</span></span> <span data-ttu-id="ce24f-122">Cada [**instância SubscritaSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) contém uma propriedade [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) a partir da qual pode referenciar o objeto [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) e obter o [**ID**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id).</span><span class="sxs-lookup"><span data-stu-id="ce24f-122">Each [**SubscribedSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) instance contains a [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) property from which you can reference the [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) object and get the [**ID**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id).</span></span>

<span data-ttu-id="ce24f-123">Um pedido de atribuição de licença deve conter licenças de um único grupo de licenças.</span><span class="sxs-lookup"><span data-stu-id="ce24f-123">A license assignment request must contain licenses from a single license group.</span></span> <span data-ttu-id="ce24f-124">Por exemplo, não é possível atribuir licenças do [**Grupo1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) e **do Grupo2** no mesmo pedido.</span><span class="sxs-lookup"><span data-stu-id="ce24f-124">For example, you cannot assign licenses from [**Group1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) and **Group2** in the same request.</span></span> <span data-ttu-id="ce24f-125">Uma tentativa de atribuir licenças a mais de um grupo num único pedido falhará com um erro apropriado.</span><span class="sxs-lookup"><span data-stu-id="ce24f-125">An attempt to assign licenses from more than one group in a single request will fail with an appropriate error.</span></span> <span data-ttu-id="ce24f-126">Para saber quais as licenças disponíveis por grupo de licenças, consulte [obter uma lista de licenças disponíveis por grupo de licenças.](get-a-list-of-available-licenses-by-license-group.md)</span><span class="sxs-lookup"><span data-stu-id="ce24f-126">To find out what licenses are available by license group, see [Get a list of available licenses by license group](get-a-list-of-available-licenses-by-license-group.md).</span></span>

<span data-ttu-id="ce24f-127">Aqui estão os passos para atribuir licenças através do código:</span><span class="sxs-lookup"><span data-stu-id="ce24f-127">Here are the steps to assign licenses through code:</span></span>

1. <span data-ttu-id="ce24f-128">Instantied um objeto [**de assinatura de licença.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment)</span><span class="sxs-lookup"><span data-stu-id="ce24f-128">Instantiate a [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) object.</span></span> <span data-ttu-id="ce24f-129">Utilize este objeto para especificar o produto SKU e os planos de serviço para atribuir.</span><span class="sxs-lookup"><span data-stu-id="ce24f-129">You use this object to specify the product SKU and service plans to assign.</span></span>

    ``` csharp
    LicenseAssignment license = new LicenseAssignment();
    ```

2. <span data-ttu-id="ce24f-130">Povoar as propriedades do objeto como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="ce24f-130">Populate the object properties as shown below.</span></span> <span data-ttu-id="ce24f-131">Este código pressupõe que já tem o produto SKU ID, e que todos os planos de serviço disponíveis serão atribuídos (ou seja, nenhum será excluído).</span><span class="sxs-lookup"><span data-stu-id="ce24f-131">This code assumes that you already have the product SKU ID, and that all of the available service plans will be assigned (that is, none will be excluded).</span></span>

    ```csharp
    license.SkuId = selectedProductSkuId;
    license.ExcludedPlans = null;
    ```

3. <span data-ttu-id="ce24f-132">Se não tiver o produto SKU ID, precisa de recuperar a recolha de SKUs subscritos e obter o produto SKU ID de um deles.</span><span class="sxs-lookup"><span data-stu-id="ce24f-132">If you don't have the product SKU ID, you need to retrieve the collection of subscribed SKUs and get the product SKU ID from one of them.</span></span> <span data-ttu-id="ce24f-133">Aqui está um exemplo se conhecer o nome SKU do produto.</span><span class="sxs-lookup"><span data-stu-id="ce24f-133">Here is an example if you know the product SKU name.</span></span>

    ```csharp
    var customerSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
    var sku = customerSubscribedSkus.Items.Where(n => n.ProductSku.Name == "Office 365 Enterprise E3").First();
    license.SkuId = sku.ProductSku.Id;
    license.ExcludedPlans = null;
    ```

4. <span data-ttu-id="ce24f-134">Em seguida, instantânea uma nova lista de [**tipo Licençaasignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment), e adicionar o objeto de licença.</span><span class="sxs-lookup"><span data-stu-id="ce24f-134">Next, instantiate a new list of type [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment), and add the license object.</span></span> <span data-ttu-id="ce24f-135">Pode atribuir mais do que uma licença adicionando cada uma individualmente à lista.</span><span class="sxs-lookup"><span data-stu-id="ce24f-135">You can assign more than one license by adding each individually to the list.</span></span> <span data-ttu-id="ce24f-136">As licenças incluídas nesta lista devem ser do mesmo grupo de licenças.</span><span class="sxs-lookup"><span data-stu-id="ce24f-136">The licenses included in this list must be from the same license group.</span></span>

    ```csharp
    List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
    licenseList.Add(license);
    ```

5. <span data-ttu-id="ce24f-137">Crie uma instância [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) e atribua a lista de atribuições de licenças à propriedade [**LicensesToAssign.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign)</span><span class="sxs-lookup"><span data-stu-id="ce24f-137">Create a [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) instance and assign the list of license assignments to the [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) property.</span></span>

    ```csharp
    LicenseUpdate updateLicense = new LicenseUpdate();
    updateLicense.LicensesToAssign = licenseList;
    ```

6. <span data-ttu-id="ce24f-138">Ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) ou [**CriarAync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) e passe o objeto de atualização da licença como mostrado abaixo para atribuir as licenças.</span><span class="sxs-lookup"><span data-stu-id="ce24f-138">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) method and pass the license update object as shown below to assign the licenses.</span></span>

    ```csharp
    var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
    ```

## <a name="c"></a><span data-ttu-id="ce24f-139">C\#</span><span class="sxs-lookup"><span data-stu-id="ce24f-139">C\#</span></span>

<span data-ttu-id="ce24f-140">Para atribuir uma licença a um utilizador do cliente, primeiro instantaneamente um objeto [**de assinatura de Licença**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) e povoar as propriedades [**Skuid**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) e [**ExcluiedPlans.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans)</span><span class="sxs-lookup"><span data-stu-id="ce24f-140">To assign a license to a customer user, first instantiate a [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) object, and populate the [**Skuid**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) and [**ExcludedPlans**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans) properties.</span></span> <span data-ttu-id="ce24f-141">Utilize este objeto para especificar o produto SKU para atribuir e os planos de serviço para excluir.</span><span class="sxs-lookup"><span data-stu-id="ce24f-141">You use this object to specify the product SKU to assign and service plans to exclude.</span></span> <span data-ttu-id="ce24f-142">Em seguida, instantânea uma nova lista de **tipo Licençaassignment**, e adicionar o objeto de licença à lista.</span><span class="sxs-lookup"><span data-stu-id="ce24f-142">Next, instantiate a new list of type **LicenseAssignment**, and add the license object to the list.</span></span> <span data-ttu-id="ce24f-143">Em seguida, crie uma instância [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) e atribua a lista de atribuições de licenças para a propriedade [**LicensesToAssign.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign)</span><span class="sxs-lookup"><span data-stu-id="ce24f-143">Then create a [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) instance and assign the list of license assignments to the [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) property.</span></span>

<span data-ttu-id="ce24f-144">Em seguida, utilize o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente, e o método [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) com o ID do utilizador para identificar o utilizador.</span><span class="sxs-lookup"><span data-stu-id="ce24f-144">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user.</span></span> <span data-ttu-id="ce24f-145">Em seguida, obtenha uma interface para as operações de atualização da licença de utilizador do cliente a partir da propriedade [**LicenseUpdates.**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates)</span><span class="sxs-lookup"><span data-stu-id="ce24f-145">Then get an interface to customer user license update operations from the [**LicenseUpdates**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates) property.</span></span>

<span data-ttu-id="ce24f-146">Por fim, ligue para o método [**Criar**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) ou [**CriarAync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) e passe o objeto de atualização de licença para atribuir a licença.</span><span class="sxs-lookup"><span data-stu-id="ce24f-146">Finally, call the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) method and pass the license update object to assign the license.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerUserId;
// string selectedCustomerId;
// string selectedProductSkuId;

// Instantiate and populate a LicenseAssignment object.
LicenseAssignment license = new LicenseAssignment();
license.SkuId = selectedProductSkuId;
license.ExcludedPlans = null;

// Instantiate a list of licenses to assign and add the license to it.
List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
licenseList.Add(license);

// Instantiate a LicenseUpdate object and add the list of licenses to assign.
LicenseUpdate updateLicense = new LicenseUpdate();
updateLicense.LicensesToAssign = licenseList;

// Update the user licenses.
var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
```

<span data-ttu-id="ce24f-147">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="ce24f-147">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="ce24f-148">**Projeto**: Partner Center SDK Samples **Class**: CustomerUserAssignLicenses.cs</span><span class="sxs-lookup"><span data-stu-id="ce24f-148">**Project**: Partner Center SDK Samples **Class**: CustomerUserAssignLicenses.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="ce24f-149">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="ce24f-149">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ce24f-150">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce24f-150">Request syntax</span></span>

| <span data-ttu-id="ce24f-151">Método</span><span class="sxs-lookup"><span data-stu-id="ce24f-151">Method</span></span>   | <span data-ttu-id="ce24f-152">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="ce24f-152">Request URI</span></span>                                                                                                    |
|----------|----------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ce24f-153">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="ce24f-153">**POST**</span></span> | <span data-ttu-id="ce24f-154">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/users/{user-id}/licenseupdates HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ce24f-154">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenseupdates HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="ce24f-155">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="ce24f-155">URI parameters</span></span>

<span data-ttu-id="ce24f-156">Utilize os seguintes parâmetros de percurso para identificar o cliente e o utilizador.</span><span class="sxs-lookup"><span data-stu-id="ce24f-156">Use the following path parameters to identify the customer and user.</span></span>

| <span data-ttu-id="ce24f-157">Nome</span><span class="sxs-lookup"><span data-stu-id="ce24f-157">Name</span></span>        | <span data-ttu-id="ce24f-158">Tipo</span><span class="sxs-lookup"><span data-stu-id="ce24f-158">Type</span></span>   | <span data-ttu-id="ce24f-159">Necessário</span><span class="sxs-lookup"><span data-stu-id="ce24f-159">Required</span></span> | <span data-ttu-id="ce24f-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce24f-160">Description</span></span>                                       |
|-------------|--------|----------|---------------------------------------------------|
| <span data-ttu-id="ce24f-161">id cliente</span><span class="sxs-lookup"><span data-stu-id="ce24f-161">customer-id</span></span> | <span data-ttu-id="ce24f-162">string</span><span class="sxs-lookup"><span data-stu-id="ce24f-162">string</span></span> | <span data-ttu-id="ce24f-163">Sim</span><span class="sxs-lookup"><span data-stu-id="ce24f-163">Yes</span></span>      | <span data-ttu-id="ce24f-164">Um ID formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="ce24f-164">A GUID formatted ID that identifies the customer.</span></span> |
| <span data-ttu-id="ce24f-165">user-id</span><span class="sxs-lookup"><span data-stu-id="ce24f-165">user-id</span></span>     | <span data-ttu-id="ce24f-166">string</span><span class="sxs-lookup"><span data-stu-id="ce24f-166">string</span></span> | <span data-ttu-id="ce24f-167">Sim</span><span class="sxs-lookup"><span data-stu-id="ce24f-167">Yes</span></span>      | <span data-ttu-id="ce24f-168">Um ID formatado GUID que identifica o utilizador.</span><span class="sxs-lookup"><span data-stu-id="ce24f-168">A GUID formatted ID that identifies the user.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="ce24f-169">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="ce24f-169">Request headers</span></span>

<span data-ttu-id="ce24f-170">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ce24f-170">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ce24f-171">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="ce24f-171">Request body</span></span>

<span data-ttu-id="ce24f-172">Inclua um recurso [LicenseUpdate](license-resources.md#licenseupdate) no órgão de pedido que especifica as licenças a atribuir.</span><span class="sxs-lookup"><span data-stu-id="ce24f-172">Include a [LicenseUpdate](license-resources.md#licenseupdate) resource in the request body that specifies the licenses to assign.</span></span>

### <a name="request-example"></a><span data-ttu-id="ce24f-173">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="ce24f-173">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/554526aa-cf5e-46fa-95df-98dbc55d8a1e/licenseupdates HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 183
Expect: 100-continue

{
    "LicensesToAssign": [{
            "ExcludedPlans": null,
            "SkuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "LicensesToRemove": null,
    "LicenseWarnings": null,
    "Attributes": {
        "ObjectType": "LicenseUpdate"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="ce24f-174">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="ce24f-174">REST response</span></span>

<span data-ttu-id="ce24f-175">Se for bem sucedido, é devolvido um código de estado de resposta HTTP 201 e o organismo de resposta contém um recurso [LicenseUpdate](license-resources.md#licenseupdate) com as informações da licença.</span><span class="sxs-lookup"><span data-stu-id="ce24f-175">If successful, an HTTP response status code 201 is returned and the response body contains a [LicenseUpdate](license-resources.md#licenseupdate) resource with the license information.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ce24f-176">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="ce24f-176">Response success and error codes</span></span>

<span data-ttu-id="ce24f-177">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="ce24f-177">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ce24f-178">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="ce24f-178">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ce24f-179">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="ce24f-179">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-success"></a><span data-ttu-id="ce24f-180">Exemplo de resposta (sucesso)</span><span class="sxs-lookup"><span data-stu-id="ce24f-180">Response example (success)</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 139
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CV: 5AnzcZQrvUqCq3kd.0
MS-ServerId: 030020525
Date: Thu, 20 Apr 2017 21:50:39 GMT

{
    "licensesToAssign": [{
            "skuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "licenseWarnings": [],
    "attributes": {
        "objectType": "LicenseUpdate"
    }
}
```

### <a name="response-example-license-isnt-available"></a><span data-ttu-id="ce24f-181">Exemplo de resposta (a licença não está disponível)</span><span class="sxs-lookup"><span data-stu-id="ce24f-181">Response example (license isn't available)</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 341
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: f4f3b748-8b22-4d07-a5a1-dceb32824192
MS-CV: 5npA0K22CUmWPOzB.0
MS-ServerId: 102030524
Date: Thu, 20 Apr 2017 22:12:36 GMT

{
    "code": 60012,
    "description": "We&#39;re sorry, it looks like you've run out of licenses. Buy more licenses, and then try again.",
    "data": ["LicenseQuotaExceededException : Subscription with Account 0c39d6d5-c70d-4c55-bc02-f620844f3fd1 and SKU f8a1db68-be16-40ed-86d5-cb42ce701560 does not have any available licenses left."],
    "source": "PartnerFD"
}
```
