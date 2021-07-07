---
title: Capacidades de caixa de areia para relacionamento revendedor
description: A caixa de areia do parceiro tem capacidade de suportar relações entre o parceiro e o cliente
ms.date: 05/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: aa6c4fb9ef71bacfad7e0f1510fec15f6af60a05
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547398"
---
# <a name="sandbox-capabilities-for-reseller-relationship"></a><span data-ttu-id="d44e6-103">Capacidades de caixa de areia para relacionamento revendedor</span><span class="sxs-lookup"><span data-stu-id="d44e6-103">Sandbox capabilities for Reseller relationship</span></span>

<span data-ttu-id="d44e6-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d44e6-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d44e6-105">Este artigo explica o que é suportado na Caixa de Areia para relações de revendedor entre o parceiro e o cliente.</span><span class="sxs-lookup"><span data-stu-id="d44e6-105">This article explains what is supported in the Sandbox for reseller relationships between the partner and the customer.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d44e6-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d44e6-106">Prerequisites</span></span>

- <span data-ttu-id="d44e6-107">Credenciais de conta do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d44e6-107">Partner Center account credentials.</span></span> <span data-ttu-id="d44e6-108">O cenário sandbox suporta a autenticação com as credenciais autónomas da App e app+User.</span><span class="sxs-lookup"><span data-stu-id="d44e6-108">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span>
- <span data-ttu-id="d44e6-109">Uma ID do cliente (cliente-inquilino-id).</span><span class="sxs-lookup"><span data-stu-id="d44e6-109">A customer ID (customer-tenant-id).</span></span> <span data-ttu-id="d44e6-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard/home)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="d44e6-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard/home).</span></span> <span data-ttu-id="d44e6-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="d44e6-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d44e6-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="d44e6-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d44e6-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="d44e6-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d44e6-114">O ID da Microsoft é o mesmo que o ID do cliente (cliente-inquilino-id).</span><span class="sxs-lookup"><span data-stu-id="d44e6-114">The Microsoft ID is the same as the customer ID (customer-tenant-id).</span></span>
- <span data-ttu-id="d44e6-115">Todas as instâncias de compra de máquinas virtuais reservadas Azure e as ordens de compra de software devem ser canceladas antes de eliminar um cliente da caixa de areia de integração da Ponta.</span><span class="sxs-lookup"><span data-stu-id="d44e6-115">All Azure Reserved Virtual Machine Instances and software purchase orders must be canceled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="scenarios-supporting-reseller-relationship"></a><span data-ttu-id="d44e6-116">Cenários de apoio à relação do revendedor</span><span class="sxs-lookup"><span data-stu-id="d44e6-116">Scenarios Supporting Reseller Relationship</span></span>

1.  <span data-ttu-id="d44e6-117">Sandbox Direct Bill Partners e Fornecedores Indiretos podem criar relações com o cliente Sandbox.</span><span class="sxs-lookup"><span data-stu-id="d44e6-117">Sandbox Direct Bill Partners and Indirect Providers can create relationships with the Sandbox customer.</span></span> 
2.  <span data-ttu-id="d44e6-118">Sandbox Direct Bill Partners e Fornecedores Indiretos não podem convidar clientes sandbox.</span><span class="sxs-lookup"><span data-stu-id="d44e6-118">Sandbox Direct Bill Partners and Indirect Providers cannot invite Sandbox customers.</span></span>

3. <span data-ttu-id="d44e6-119">Sandbox Direct Bill Partner e Fornecedores Indiretos são capazes de remover a relação de revendedor do Partner Center UI e API.</span><span class="sxs-lookup"><span data-stu-id="d44e6-119">Sandbox Direct Bill Partner and Indirect Providers are able to remove reseller relationship from Partner Center UI and API.</span></span>

4. <span data-ttu-id="d44e6-120">Sandbox Remove Reseller Relationship vai ligar para Eliminar o cliente AP.</span><span class="sxs-lookup"><span data-stu-id="d44e6-120">Sandbox Remove Reseller Relationship will call Delete customer AP.</span></span> <span data-ttu-id="d44e6-121">Isto removerá a relação e eliminará o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="d44e6-121">This will remove the relationship and delete the customer tenant.</span></span> <span data-ttu-id="d44e6-122">{baseURL}/v1/Clientes/{cliente-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="d44e6-122">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span>


    ### <a name="in-the-sandbox"></a><span data-ttu-id="d44e6-123">Na Caixa de Areia</span><span class="sxs-lookup"><span data-stu-id="d44e6-123">In the Sandbox</span></span>

    <span data-ttu-id="d44e6-124">**Parceiros de conta diretos:**</span><span class="sxs-lookup"><span data-stu-id="d44e6-124">**Direct bill partners**:</span></span>

    - <span data-ttu-id="d44e6-125">Pode adicionar clientes existentes</span><span class="sxs-lookup"><span data-stu-id="d44e6-125">Can add existing customers</span></span>

    - <span data-ttu-id="d44e6-126">Não é possível solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="d44e6-126">Cannot request relationships with new customers</span></span>

    <span data-ttu-id="d44e6-127">**Fornecedores indiretos:**</span><span class="sxs-lookup"><span data-stu-id="d44e6-127">**Indirect providers**:</span></span>

    - <span data-ttu-id="d44e6-128">Pode adicionar clientes existentes</span><span class="sxs-lookup"><span data-stu-id="d44e6-128">Can add existing customers</span></span>

    - <span data-ttu-id="d44e6-129">Não é possível solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="d44e6-129">Cannot request relationships with new customers</span></span>

    - <span data-ttu-id="d44e6-130">Não pode ter uma relação com um revendedor indireto</span><span class="sxs-lookup"><span data-stu-id="d44e6-130">Cannot have a relationship with an Indirect reseller</span></span>

    <span data-ttu-id="d44e6-131">**Revendedor indireto:**</span><span class="sxs-lookup"><span data-stu-id="d44e6-131">**Indirect reseller**:</span></span> 

    -   <span data-ttu-id="d44e6-132">Pode ter relações com clientes existentes</span><span class="sxs-lookup"><span data-stu-id="d44e6-132">Can have relationships with existing customers</span></span>

    -   <span data-ttu-id="d44e6-133">Não é possível solicitar novos relacionamentos ou adicionar novos clientes</span><span class="sxs-lookup"><span data-stu-id="d44e6-133">Cannot request new relationships or add new customers</span></span>

    ### <a name="in-partner-center"></a><span data-ttu-id="d44e6-134">No Centro Parceiro</span><span class="sxs-lookup"><span data-stu-id="d44e6-134">In Partner Center</span></span>

    <span data-ttu-id="d44e6-135">**Parceiros de conta diretos:**</span><span class="sxs-lookup"><span data-stu-id="d44e6-135">**Direct bill partners**:</span></span>

    -   <span data-ttu-id="d44e6-136">Pode adicionar novos clientes</span><span class="sxs-lookup"><span data-stu-id="d44e6-136">Can add new customers</span></span>

    -   <span data-ttu-id="d44e6-137">Pode solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="d44e6-137">Can request relationships with new customers</span></span>

    <span data-ttu-id="d44e6-138">**Fornecedores indiretos:**</span><span class="sxs-lookup"><span data-stu-id="d44e6-138">**Indirect providers**:</span></span>

    -   <span data-ttu-id="d44e6-139">Pode adicionar novos clientes</span><span class="sxs-lookup"><span data-stu-id="d44e6-139">Can add new customers</span></span>

    -   <span data-ttu-id="d44e6-140">Pode solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="d44e6-140">Can request relationships with new customers</span></span>

    -   <span data-ttu-id="d44e6-141">Pode ter relações com revendedores indiretos</span><span class="sxs-lookup"><span data-stu-id="d44e6-141">Can have relationships with indirect resellers</span></span>

    <span data-ttu-id="d44e6-142">**Revendedores indiretos:**</span><span class="sxs-lookup"><span data-stu-id="d44e6-142">**Indirect resellers**:</span></span>

    -   <span data-ttu-id="d44e6-143">Não pode adicionar novos clientes</span><span class="sxs-lookup"><span data-stu-id="d44e6-143">Can’t add new customers</span></span>

    -   <span data-ttu-id="d44e6-144">Pode solicitar relações com novos clientes</span><span class="sxs-lookup"><span data-stu-id="d44e6-144">Can request relationships with new customers</span></span>


<span data-ttu-id="d44e6-145">Siga a [Relação de Revendedor Remover](remove-a-reseller-relationship-with-a-customer.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="d44e6-145">Follow the [Remove Reseller Relationship](remove-a-reseller-relationship-with-a-customer.md) for the customer for details.</span></span> <span data-ttu-id="d44e6-146">No entanto, existem algumas diferenças entre as capacidades do Produto e da Sandbox.</span><span class="sxs-lookup"><span data-stu-id="d44e6-146">However, there are some differences between the Product and Sandbox capabilities.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d44e6-147">PEDIDO SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d44e6-147">REQUEST SYNTAX</span></span>

|<span data-ttu-id="d44e6-148">**Método**</span><span class="sxs-lookup"><span data-stu-id="d44e6-148">**Method**</span></span>|<span data-ttu-id="d44e6-149">**Eliminar**</span><span class="sxs-lookup"><span data-stu-id="d44e6-149">**Delete**</span></span>|
|-------------|------------|
|<span data-ttu-id="d44e6-150">Eliminar</span><span class="sxs-lookup"><span data-stu-id="d44e6-150">Delete</span></span>|<span data-ttu-id="d44e6-151">{baseURL}/v1/Clientes/{cliente-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="d44e6-151">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span> |

<span data-ttu-id="d44e6-152">Pedido corpo Nenhum</span><span class="sxs-lookup"><span data-stu-id="d44e6-152">Request body None</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d44e6-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="d44e6-153">Response success and error codes</span></span>

<span data-ttu-id="d44e6-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="d44e6-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d44e6-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="d44e6-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d44e6-156">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](./error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="d44e6-156">For the full list, see [Partner Center REST error codes](./error-codes.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d44e6-157">Passos seguintes</span><span class="sxs-lookup"><span data-stu-id="d44e6-157">Next steps</span></span>

- [<span data-ttu-id="d44e6-158">Ativar subscrições de Sandbox para produtos Azure Marketplace</span><span class="sxs-lookup"><span data-stu-id="d44e6-158">Activate Sandbox subscriptions for Azure Marketplace products</span></span>](activate-sandbox-subscription-azure-marketplace-products.md)

- [<span data-ttu-id="d44e6-159">Cancelar uma encomenda da Sandbox</span><span class="sxs-lookup"><span data-stu-id="d44e6-159">Cancel an order from Sandbox</span></span>](cancel-an-order-from-the-integration-sandbox.md)

- [<span data-ttu-id="d44e6-160">Testar e depurar</span><span class="sxs-lookup"><span data-stu-id="d44e6-160">Test and debug</span></span>](test-and-debug.md)