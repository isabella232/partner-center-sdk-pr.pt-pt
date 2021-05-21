---
title: Capacidades de caixa de areia para relacionamento revendedor
description: A caixa de areia do parceiro tem capacidade de suportar relações entre o parceiro e o cliente
ms.date: 05/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9bef4a15685ebbdc2212988f5ac5724b946cfd54
ms.sourcegitcommit: 1aeaa12705a5945b8aab6bca254fedebd9c8bc4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/21/2021
ms.locfileid: "110243389"
---
# <a name="sandbox-capabilities-for-reseller-relationship"></a><span data-ttu-id="0d8b7-103">Capacidades de caixa de areia para relacionamento revendedor</span><span class="sxs-lookup"><span data-stu-id="0d8b7-103">Sandbox capabilities for Reseller relationship</span></span>

<span data-ttu-id="0d8b7-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-104">**Applies to:**</span></span>

- <span data-ttu-id="0d8b7-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="0d8b7-105">Partner Center</span></span>
- <span data-ttu-id="0d8b7-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="0d8b7-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="0d8b7-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="0d8b7-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="0d8b7-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0d8b7-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0d8b7-109">Este artigo explica o que é suportado na Caixa de Areia para relações de revendedor entre o parceiro e o cliente.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-109">This article explains what is supported in the Sandbox for reseller relationships between the partner and the customer.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="0d8b7-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0d8b7-110">Prerequisites</span></span>

- <span data-ttu-id="0d8b7-111">Credenciais de conta do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-111">Partner Center account credentials.</span></span> <span data-ttu-id="0d8b7-112">O cenário sandbox suporta a autenticação com as credenciais autónomas da App e app+User.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-112">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span>
- <span data-ttu-id="0d8b7-113">Uma ID do cliente (cliente-inquilino-id).</span><span class="sxs-lookup"><span data-stu-id="0d8b7-113">A customer ID (customer-tenant-id).</span></span> <span data-ttu-id="0d8b7-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard/home)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard/home).</span></span> <span data-ttu-id="0d8b7-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="0d8b7-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="0d8b7-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="0d8b7-118">O ID da Microsoft é o mesmo que o ID do cliente (cliente-inquilino-id).</span><span class="sxs-lookup"><span data-stu-id="0d8b7-118">The Microsoft ID is the same as the customer ID (customer-tenant-id).</span></span>
- <span data-ttu-id="0d8b7-119">Todas as instâncias de compra de máquinas virtuais reservadas Azure e as ordens de compra de software devem ser canceladas antes de eliminar um cliente da caixa de areia de integração da Ponta.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-119">All Azure Reserved Virtual Machine Instances and software purchase orders must be canceled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="scenarios-supporting-reseller-relationship"></a><span data-ttu-id="0d8b7-120">Cenários de apoio à relação do revendedor</span><span class="sxs-lookup"><span data-stu-id="0d8b7-120">Scenarios Supporting Reseller Relationship</span></span>

1.  <span data-ttu-id="0d8b7-121">Sandbox Direct Bill Partners e Fornecedores Indiretos podem criar relações com o cliente Sandbox.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-121">Sandbox Direct Bill Partners and Indirect Providers can create relationships with the Sandbox customer.</span></span> 
2.  <span data-ttu-id="0d8b7-122">Sandbox Direct Bill Partners e Fornecedores Indiretos não podem convidar clientes sandbox.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-122">Sandbox Direct Bill Partners and Indirect Providers cannot invite Sandbox customers.</span></span>

3. <span data-ttu-id="0d8b7-123">Sandbox Direct Bill Partner e Fornecedores Indiretos são capazes de remover a relação de revendedor do Partner Center UI e API.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-123">Sandbox Direct Bill Partner and Indirect Providers are able to remove reseller relationship from Partner Center UI and API.</span></span>

4. <span data-ttu-id="0d8b7-124">Sandbox Remove Reseller Relationship vai ligar para Eliminar o cliente AP.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-124">Sandbox Remove Reseller Relationship will call Delete customer AP.</span></span> <span data-ttu-id="0d8b7-125">Isto removerá a relação assim como eliminará o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-125">This will remove the relationship as well as delete the customer tenant.</span></span> <span data-ttu-id="0d8b7-126">{baseURL}/v1/Clientes/{cliente-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="0d8b7-126">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span>


    ### <a name="in-the-sandbox"></a><span data-ttu-id="0d8b7-127">Na Caixa de Areia</span><span class="sxs-lookup"><span data-stu-id="0d8b7-127">In the Sandbox</span></span>

    <span data-ttu-id="0d8b7-128">**Parceiros de conta diretos:**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-128">**Direct bill partners**:</span></span>

    - <span data-ttu-id="0d8b7-129">Pode adicionar clientes existentes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-129">Can add existing customers</span></span>

    - <span data-ttu-id="0d8b7-130">Não é possível solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-130">Cannot request relationships with new customers</span></span>

    <span data-ttu-id="0d8b7-131">**Fornecedores indiretos:**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-131">**Indirect providers**:</span></span>

    - <span data-ttu-id="0d8b7-132">Pode adicionar clientes existentes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-132">Can add existing customers</span></span>

    - <span data-ttu-id="0d8b7-133">Não é possível solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-133">Cannot request relationships with new customers</span></span>

    - <span data-ttu-id="0d8b7-134">Não pode ter uma relação com um revendedor indireto</span><span class="sxs-lookup"><span data-stu-id="0d8b7-134">Cannot have a relationship with an Indirect reseller</span></span>

    <span data-ttu-id="0d8b7-135">**Revendedor indireto:**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-135">**Indirect reseller**:</span></span> 

    -   <span data-ttu-id="0d8b7-136">Pode ter uma relação com os clientes existentes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-136">Can have a relationships with existing customers</span></span>

    -   <span data-ttu-id="0d8b7-137">Não é possível solicitar novos relacionamentos ou adicionar novos clientes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-137">Cannot request new relationships or add new customers</span></span>

    ### <a name="in-partner-center"></a><span data-ttu-id="0d8b7-138">No Centro Parceiro</span><span class="sxs-lookup"><span data-stu-id="0d8b7-138">In Partner Center</span></span>

    <span data-ttu-id="0d8b7-139">**Parceiros de conta diretos:**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-139">**Direct bill partners**:</span></span>

    -   <span data-ttu-id="0d8b7-140">Pode adicionar novos clientes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-140">Can add new customers</span></span>

    -   <span data-ttu-id="0d8b7-141">Pode solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-141">Can request relationships with new customers</span></span>

    <span data-ttu-id="0d8b7-142">**Fornecedores indiretos:**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-142">**Indirect providers**:</span></span>

    -   <span data-ttu-id="0d8b7-143">Pode adicionar novos clientes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-143">Can add new customers</span></span>

    -   <span data-ttu-id="0d8b7-144">Pode solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-144">Can request relationships with new customers</span></span>

    -   <span data-ttu-id="0d8b7-145">Pode ter relações com revendedores indiretos</span><span class="sxs-lookup"><span data-stu-id="0d8b7-145">Can have relationships with indirect resellers</span></span>

    <span data-ttu-id="0d8b7-146">**Revendedores indiretos:**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-146">**Indirect resellers**:</span></span>

    -   <span data-ttu-id="0d8b7-147">Não pode adicionar novos clientes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-147">Can’t add new customers</span></span>

    -   <span data-ttu-id="0d8b7-148">Pode solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-148">Can request relationships with new customers</span></span>


<span data-ttu-id="0d8b7-149">Siga a [Relação de Revendedor Remover](remove-a-reseller-relationship-with-a-customer.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-149">Follow the [Remove Reseller Relationship](remove-a-reseller-relationship-with-a-customer.md) for the customer for details.</span></span> <span data-ttu-id="0d8b7-150">No entanto, existem algumas diferenças entre as capacidades do Produto e da Sandbox.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-150">However, there are some differences between the Product and Sandbox capabilities.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0d8b7-151">PEDIDO SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0d8b7-151">REQUEST SYNTAX</span></span>

|<span data-ttu-id="0d8b7-152">**Método**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-152">**Method**</span></span>|<span data-ttu-id="0d8b7-153">**Eliminar**</span><span class="sxs-lookup"><span data-stu-id="0d8b7-153">**Delete**</span></span>|
|-------------|------------|
|<span data-ttu-id="0d8b7-154">Eliminar</span><span class="sxs-lookup"><span data-stu-id="0d8b7-154">Delete</span></span>|<span data-ttu-id="0d8b7-155">{baseURL}/v1/Clientes/{cliente-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="0d8b7-155">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span> |

<span data-ttu-id="0d8b7-156">Pedido corpo Nenhum</span><span class="sxs-lookup"><span data-stu-id="0d8b7-156">Request body None</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0d8b7-157">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="0d8b7-157">Response success and error codes</span></span>

<span data-ttu-id="0d8b7-158">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0d8b7-159">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0d8b7-160">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](./error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="0d8b7-160">For the full list, see [Partner Center REST error codes](./error-codes.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0d8b7-161">Passos seguintes</span><span class="sxs-lookup"><span data-stu-id="0d8b7-161">Next steps</span></span>

- [<span data-ttu-id="0d8b7-162">Ativar subscrições de Sandbox para produtos Azure Marketplace</span><span class="sxs-lookup"><span data-stu-id="0d8b7-162">Activate Sandbox subscriptions for Azure Marketplace products</span></span>](activate-sandbox-subscription-azure-marketplace-products.md)

- [<span data-ttu-id="0d8b7-163">Cancelar uma encomenda da Sandbox</span><span class="sxs-lookup"><span data-stu-id="0d8b7-163">Cancel an order from Sandbox</span></span>](cancel-an-order-from-the-integration-sandbox.md)

- [<span data-ttu-id="0d8b7-164">Testar e depurar</span><span class="sxs-lookup"><span data-stu-id="0d8b7-164">Test and debug</span></span>](test-and-debug.md)