---
title: Criar uma transferência
description: Como criar uma transferência de subscrições para um cliente.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d5e70cc5b7ce4fcfa715f581a2151f0b8d1922b0
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768828"
---
# <a name="create-a-transfer"></a><span data-ttu-id="08818-103">Criar uma transferência</span><span class="sxs-lookup"><span data-stu-id="08818-103">Create a transfer</span></span>

<span data-ttu-id="08818-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="08818-104">**Applies to:**</span></span>

- <span data-ttu-id="08818-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="08818-105">Partner Center</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08818-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="08818-106">Prerequisites</span></span>

- <span data-ttu-id="08818-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="08818-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="08818-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="08818-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="08818-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="08818-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="08818-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="08818-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="08818-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="08818-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="08818-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="08818-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="08818-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="08818-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="08818-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="08818-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="08818-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="08818-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="08818-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="08818-116">Request syntax</span></span>

| <span data-ttu-id="08818-117">Método</span><span class="sxs-lookup"><span data-stu-id="08818-117">Method</span></span>   | <span data-ttu-id="08818-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="08818-118">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="08818-119">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="08818-119">**POST**</span></span> | <span data-ttu-id="08818-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/transfers HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="08818-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="08818-121">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="08818-121">URI parameter</span></span>

<span data-ttu-id="08818-122">Utilize o seguinte parâmetro de percurso para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="08818-122">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="08818-123">Nome</span><span class="sxs-lookup"><span data-stu-id="08818-123">Name</span></span>            | <span data-ttu-id="08818-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="08818-124">Type</span></span>     | <span data-ttu-id="08818-125">Necessário</span><span class="sxs-lookup"><span data-stu-id="08818-125">Required</span></span> | <span data-ttu-id="08818-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="08818-126">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="08818-127">**id cliente**</span><span class="sxs-lookup"><span data-stu-id="08818-127">**customer-id**</span></span> | <span data-ttu-id="08818-128">string</span><span class="sxs-lookup"><span data-stu-id="08818-128">string</span></span>   | <span data-ttu-id="08818-129">Sim</span><span class="sxs-lookup"><span data-stu-id="08818-129">Yes</span></span>      | <span data-ttu-id="08818-130">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="08818-130">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="08818-131">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="08818-131">Request headers</span></span>

<span data-ttu-id="08818-132">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="08818-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="08818-133">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="08818-133">Request body</span></span>

<span data-ttu-id="08818-134">Esta tabela descreve as propriedades da [Entidade transferina](transfer-entity-resources.md) no organismo de pedido.</span><span class="sxs-lookup"><span data-stu-id="08818-134">This table describes the [TransferEntity](transfer-entity-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="08818-135">Propriedade</span><span class="sxs-lookup"><span data-stu-id="08818-135">Property</span></span>              | <span data-ttu-id="08818-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="08818-136">Type</span></span>          | <span data-ttu-id="08818-137">Necessário</span><span class="sxs-lookup"><span data-stu-id="08818-137">Required</span></span>  | <span data-ttu-id="08818-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="08818-138">Description</span></span>                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="08818-139">ID</span><span class="sxs-lookup"><span data-stu-id="08818-139">id</span></span>                    | <span data-ttu-id="08818-140">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-140">string</span></span>        | <span data-ttu-id="08818-141">No</span><span class="sxs-lookup"><span data-stu-id="08818-141">No</span></span>    | <span data-ttu-id="08818-142">Um identificador de entidade de transferência que é fornecido após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-142">A transferEntity identifier that is supplied upon successful creation of the transferEntity.</span></span>                               |
| <span data-ttu-id="08818-143">createdTime</span><span class="sxs-lookup"><span data-stu-id="08818-143">createdTime</span></span>           | <span data-ttu-id="08818-144">DateTime</span><span class="sxs-lookup"><span data-stu-id="08818-144">DateTime</span></span>      | <span data-ttu-id="08818-145">Não</span><span class="sxs-lookup"><span data-stu-id="08818-145">No</span></span>    | <span data-ttu-id="08818-146">A data em que a Entidade de Transferência foi criada, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="08818-146">The date the transferEntity was created, in date-time format.</span></span> <span data-ttu-id="08818-147">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-147">Applied upon successful creation of the transferEntity.</span></span>      |
| <span data-ttu-id="08818-148">última Hora DaModified</span><span class="sxs-lookup"><span data-stu-id="08818-148">lastModifiedTime</span></span>      | <span data-ttu-id="08818-149">DateTime</span><span class="sxs-lookup"><span data-stu-id="08818-149">DateTime</span></span>      | <span data-ttu-id="08818-150">Não</span><span class="sxs-lookup"><span data-stu-id="08818-150">No</span></span>    | <span data-ttu-id="08818-151">A data em que a Entidade de Transferência foi atualizada pela última vez, em formato de data-hora.</span><span class="sxs-lookup"><span data-stu-id="08818-151">The date the transferEntity was last updated, in date-time format.</span></span> <span data-ttu-id="08818-152">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-152">Applied upon successful creation of the transferEntity.</span></span> |
| <span data-ttu-id="08818-153">últimoModifiedUser</span><span class="sxs-lookup"><span data-stu-id="08818-153">lastModifiedUser</span></span>      | <span data-ttu-id="08818-154">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-154">string</span></span>        | <span data-ttu-id="08818-155">No</span><span class="sxs-lookup"><span data-stu-id="08818-155">No</span></span>    | <span data-ttu-id="08818-156">O utilizador que atualizou pela última vez a Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-156">The user who last updated the transferEntity.</span></span> <span data-ttu-id="08818-157">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-157">Applied upon successful creation of transferEntity.</span></span>                          |
| <span data-ttu-id="08818-158">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="08818-158">customerName</span></span>          | <span data-ttu-id="08818-159">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-159">string</span></span>        | <span data-ttu-id="08818-160">No</span><span class="sxs-lookup"><span data-stu-id="08818-160">No</span></span>    | <span data-ttu-id="08818-161">Opcional.</span><span class="sxs-lookup"><span data-stu-id="08818-161">Optional.</span></span> <span data-ttu-id="08818-162">O nome do cliente cujas assinaturas estão a ser transferidas.</span><span class="sxs-lookup"><span data-stu-id="08818-162">The name of the customer whose subscriptions are being transferred.</span></span>                                              |
| <span data-ttu-id="08818-163">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="08818-163">customerTenantId</span></span>      | <span data-ttu-id="08818-164">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-164">string</span></span>        | <span data-ttu-id="08818-165">No</span><span class="sxs-lookup"><span data-stu-id="08818-165">No</span></span>    | <span data-ttu-id="08818-166">Um id de cliente formatado GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="08818-166">A GUID formatted customer-id that identifies the customer.</span></span> <span data-ttu-id="08818-167">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-167">Applied upon successful creation of the transferEntity.</span></span>         |
| <span data-ttu-id="08818-168">partnertenantid</span><span class="sxs-lookup"><span data-stu-id="08818-168">partnertenantid</span></span>       | <span data-ttu-id="08818-169">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-169">string</span></span>        | <span data-ttu-id="08818-170">No</span><span class="sxs-lookup"><span data-stu-id="08818-170">No</span></span>    | <span data-ttu-id="08818-171">Um parceiro-id formatado GUID que identifica o parceiro.</span><span class="sxs-lookup"><span data-stu-id="08818-171">A GUID formatted partner-id that identifies the partner.</span></span>                                                                   |
| <span data-ttu-id="08818-172">fontePartnerName</span><span class="sxs-lookup"><span data-stu-id="08818-172">sourcePartnerName</span></span>     | <span data-ttu-id="08818-173">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-173">string</span></span>        | <span data-ttu-id="08818-174">No</span><span class="sxs-lookup"><span data-stu-id="08818-174">No</span></span>    | <span data-ttu-id="08818-175">Opcional.</span><span class="sxs-lookup"><span data-stu-id="08818-175">Optional.</span></span> <span data-ttu-id="08818-176">O nome da organização do parceiro que está a iniciar a transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-176">The name of the partner's organization who is initiating the transfer.</span></span>                                           |
| <span data-ttu-id="08818-177">sourcePartnerTenantId</span><span class="sxs-lookup"><span data-stu-id="08818-177">sourcePartnerTenantId</span></span> | <span data-ttu-id="08818-178">string</span><span class="sxs-lookup"><span data-stu-id="08818-178">string</span></span>        | <span data-ttu-id="08818-179">Sim</span><span class="sxs-lookup"><span data-stu-id="08818-179">Yes</span></span>   | <span data-ttu-id="08818-180">Um parceiro-id formatado GUID que identifica o parceiro que inicia a transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-180">A GUID formatted partner-id that identifies the partner initiating the transfer.</span></span>                                           |
| <span data-ttu-id="08818-181">targetPartnerName</span><span class="sxs-lookup"><span data-stu-id="08818-181">targetPartnerName</span></span>     | <span data-ttu-id="08818-182">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-182">string</span></span>        | <span data-ttu-id="08818-183">No</span><span class="sxs-lookup"><span data-stu-id="08818-183">No</span></span>    | <span data-ttu-id="08818-184">Opcional.</span><span class="sxs-lookup"><span data-stu-id="08818-184">Optional.</span></span> <span data-ttu-id="08818-185">O nome da organização do parceiro a quem a transferência é dirigida.</span><span class="sxs-lookup"><span data-stu-id="08818-185">The name of the partner's organization to whom the transfer is targeted.</span></span>                                         |
| <span data-ttu-id="08818-186">targetPartnerTenantId</span><span class="sxs-lookup"><span data-stu-id="08818-186">targetPartnerTenantId</span></span> | <span data-ttu-id="08818-187">string</span><span class="sxs-lookup"><span data-stu-id="08818-187">string</span></span>        | <span data-ttu-id="08818-188">Sim</span><span class="sxs-lookup"><span data-stu-id="08818-188">Yes</span></span>   | <span data-ttu-id="08818-189">Um parceiro-id formatado GUID que identifica o parceiro a quem a transferência é alvo.</span><span class="sxs-lookup"><span data-stu-id="08818-189">A GUID formatted partner-id that identifies the partner to whom the transfer is targeted.</span></span>                                  |
| <span data-ttu-id="08818-190">lineitems</span><span class="sxs-lookup"><span data-stu-id="08818-190">lineItems</span></span>             | <span data-ttu-id="08818-191">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="08818-191">Array of objects</span></span> | <span data-ttu-id="08818-192">Sim</span><span class="sxs-lookup"><span data-stu-id="08818-192">Yes</span></span>| <span data-ttu-id="08818-193">Uma matriz de recursos [TransferLineItem.](transfer-entity-resources.md#transferlineitem)</span><span class="sxs-lookup"><span data-stu-id="08818-193">An Array of [TransferLineItem](transfer-entity-resources.md#transferlineitem) resources.</span></span>                                   |
| <span data-ttu-id="08818-194">status</span><span class="sxs-lookup"><span data-stu-id="08818-194">status</span></span>                | <span data-ttu-id="08818-195">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-195">string</span></span>        | <span data-ttu-id="08818-196">No</span><span class="sxs-lookup"><span data-stu-id="08818-196">No</span></span>    | <span data-ttu-id="08818-197">O estado da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-197">The status of the transferEntity.</span></span> <span data-ttu-id="08818-198">Os valores possíveis são "Ative" (pode ser eliminado/submetido) e "Concluído" (já foi concluído).</span><span class="sxs-lookup"><span data-stu-id="08818-198">Possible values are "Active" (can be deleted/submitted) and "Completed" (has already been completed).</span></span> <span data-ttu-id="08818-199">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-199">Applied upon successful creation of the transferEntity.</span></span>|

<span data-ttu-id="08818-200">Esta tabela descreve as propriedades [transferLineItem](transfer-entity-resources.md#transferlineitem) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="08818-200">This table describes the [TransferLineItem](transfer-entity-resources.md#transferlineitem) properties in the request body.</span></span>

|      <span data-ttu-id="08818-201">Propriedade</span><span class="sxs-lookup"><span data-stu-id="08818-201">Property</span></span>       |            <span data-ttu-id="08818-202">Tipo</span><span class="sxs-lookup"><span data-stu-id="08818-202">Type</span></span>             | <span data-ttu-id="08818-203">Necessário</span><span class="sxs-lookup"><span data-stu-id="08818-203">Required</span></span> | <span data-ttu-id="08818-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="08818-204">Description</span></span>                                                                                     |
|---------------------|-----------------------------|----------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="08818-205">ID</span><span class="sxs-lookup"><span data-stu-id="08818-205">id</span></span>                   | <span data-ttu-id="08818-206">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-206">string</span></span>                     | <span data-ttu-id="08818-207">No</span><span class="sxs-lookup"><span data-stu-id="08818-207">No</span></span>       | <span data-ttu-id="08818-208">Um identificador único para um item de linha de transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-208">A unique identifier for a transfer line item.</span></span> <span data-ttu-id="08818-209">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-209">Applied upon successful creation of the transferEntity.</span></span>|
| <span data-ttu-id="08818-210">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="08818-210">subscriptionId</span></span>       | <span data-ttu-id="08818-211">string</span><span class="sxs-lookup"><span data-stu-id="08818-211">string</span></span>                     | <span data-ttu-id="08818-212">Sim</span><span class="sxs-lookup"><span data-stu-id="08818-212">Yes</span></span>      | <span data-ttu-id="08818-213">O identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="08818-213">The subscription identifier.</span></span>                                                                         |
| <span data-ttu-id="08818-214">quantidade</span><span class="sxs-lookup"><span data-stu-id="08818-214">quantity</span></span>             | <span data-ttu-id="08818-215">int</span><span class="sxs-lookup"><span data-stu-id="08818-215">int</span></span>                        | <span data-ttu-id="08818-216">Não</span><span class="sxs-lookup"><span data-stu-id="08818-216">No</span></span>       | <span data-ttu-id="08818-217">O número de licenças ou instâncias.</span><span class="sxs-lookup"><span data-stu-id="08818-217">The number of licenses or instances.</span></span>                                                                 |
| <span data-ttu-id="08818-218">billingCycle</span><span class="sxs-lookup"><span data-stu-id="08818-218">billingCycle</span></span>         | <span data-ttu-id="08818-219">Objeto</span><span class="sxs-lookup"><span data-stu-id="08818-219">Object</span></span>                     | <span data-ttu-id="08818-220">Não</span><span class="sxs-lookup"><span data-stu-id="08818-220">No</span></span>       | <span data-ttu-id="08818-221">O tipo de ciclo de faturação definido para o período atual.</span><span class="sxs-lookup"><span data-stu-id="08818-221">The type of billing cycle set for the current period.</span></span>                                                |
| <span data-ttu-id="08818-222">nome amigável</span><span class="sxs-lookup"><span data-stu-id="08818-222">friendlyName</span></span>         | <span data-ttu-id="08818-223">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-223">string</span></span>                     | <span data-ttu-id="08818-224">No</span><span class="sxs-lookup"><span data-stu-id="08818-224">No</span></span>       | <span data-ttu-id="08818-225">Opcional.</span><span class="sxs-lookup"><span data-stu-id="08818-225">Optional.</span></span> <span data-ttu-id="08818-226">O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.</span><span class="sxs-lookup"><span data-stu-id="08818-226">The friendly name for the item defined by the partner to help disambiguate.</span></span>                |
| <span data-ttu-id="08818-227">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="08818-227">partnerIdOnRecord</span></span>    | <span data-ttu-id="08818-228">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-228">string</span></span>                     | <span data-ttu-id="08818-229">No</span><span class="sxs-lookup"><span data-stu-id="08818-229">No</span></span>       | <span data-ttu-id="08818-230">PartnerId on Record (MPNID) sobre a compra que acontece quando a transferência é aceite.</span><span class="sxs-lookup"><span data-stu-id="08818-230">PartnerId on Record (MPNID) on the purchase that happens when the transfer is accepted.</span></span>              |
| <span data-ttu-id="08818-231">offerId</span><span class="sxs-lookup"><span data-stu-id="08818-231">offerId</span></span>              | <span data-ttu-id="08818-232">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-232">string</span></span>                     | <span data-ttu-id="08818-233">No</span><span class="sxs-lookup"><span data-stu-id="08818-233">No</span></span>       | <span data-ttu-id="08818-234">O identificador da oferta.</span><span class="sxs-lookup"><span data-stu-id="08818-234">The offer identifier.</span></span>                                                                                |
| <span data-ttu-id="08818-235">addonItems</span><span class="sxs-lookup"><span data-stu-id="08818-235">addonItems</span></span>           | <span data-ttu-id="08818-236">Lista de objetos **TransferLineItem**</span><span class="sxs-lookup"><span data-stu-id="08818-236">List of **TransferLineItem** objects</span></span> | <span data-ttu-id="08818-237">Não</span><span class="sxs-lookup"><span data-stu-id="08818-237">No</span></span> | <span data-ttu-id="08818-238">Uma recolha de itens de linha da TransferEntity para addons que serão transferidos juntamente com a subscrição base que está a ser transferida.</span><span class="sxs-lookup"><span data-stu-id="08818-238">A collection of transferEntity line items for addons that will be transferred along with the base subscription that is being transferred.</span></span> <span data-ttu-id="08818-239">Aplicada após a criação bem sucedida da Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-239">Applied upon successful creation of the transferEntity.</span></span>|
| <span data-ttu-id="08818-240">transferEror</span><span class="sxs-lookup"><span data-stu-id="08818-240">transferError</span></span>        | <span data-ttu-id="08818-241">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-241">string</span></span>                     | <span data-ttu-id="08818-242">No</span><span class="sxs-lookup"><span data-stu-id="08818-242">No</span></span>       | <span data-ttu-id="08818-243">Aplicada após transferência A Entidade é aceite em caso de erro.</span><span class="sxs-lookup"><span data-stu-id="08818-243">Applied after transferEntity is accepted in case of an error.</span></span>                                        |
| <span data-ttu-id="08818-244">status</span><span class="sxs-lookup"><span data-stu-id="08818-244">status</span></span>               | <span data-ttu-id="08818-245">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="08818-245">string</span></span>                     | <span data-ttu-id="08818-246">No</span><span class="sxs-lookup"><span data-stu-id="08818-246">No</span></span>       | <span data-ttu-id="08818-247">O estado do lineitem na Entidade de Transferência.</span><span class="sxs-lookup"><span data-stu-id="08818-247">The status of the lineitem in the transferEntity.</span></span>                                                    |

### <a name="request-example"></a><span data-ttu-id="08818-248">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="08818-248">Request example</span></span>

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Expect: 100-continue

{
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lineItems": [
        {
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "partnerIdOnRecord": "517285"
        },
        {
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "partnerIdOnRecord": "517285"
        }
    ]
}
```

## <a name="rest-response"></a><span data-ttu-id="08818-249">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="08818-249">REST response</span></span>

<span data-ttu-id="08818-250">Se for bem sucedido, este método devolve o recurso [transferenity](transfer-entity-resources.md) povoado no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="08818-250">If successful, this method returns the populated [TransferEnity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="08818-251">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="08818-251">Response success and error codes</span></span>

<span data-ttu-id="08818-252">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="08818-252">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="08818-253">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="08818-253">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="08818-254">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="08818-254">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="08818-255">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="08818-255">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 138
Content-Type: application/json; charset=utf-8
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US,en-US
{
    "id": "67c5b05b-09b5-47ba-9047-5056fe2afa4f",
    "status": "Active",
    "createdTime": "2020-03-24T20:44:14.9602781Z",
    "lastModifiedTime": "2020-03-24T20:44:15Z",
    "customerTenantId": "823c6c3f-9259-4d51-bae2-5dd06743177f",
    "partnertenantid": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lastModifiedUser": "d0648481-b615-45c9-8cd1-ff87940dbdc4",
    "lineItems": [
        {
            "id": 0,
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "offerId": "50E9A47A-7B4D-4970-9D90-CAE927F53753",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 for Sales Enterprise Attach to Qualifying Dynamics 365 Base Offer",
            "quantity": 1,
            "addonItems": [
                {
                    "id": 0,
                    "subscriptionId": "D738C6C9-DDBD-46E9-B316-65F9D9B3ECB4",
                    "offerId": "2BCF9FE8-8B65-4FCF-9240-419203FB8CF4",
                    "billingCycle": "annual",
                    "friendlyName": "Dynamics 365 - Additional Production Instance (Qualified Offer)",
                    "quantity": 4
                }
            ]
        },
        {
            "id": 0,
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "offerId": "455DDD41-32ED-4E2D-B3A2-BBCB22CAA467",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 Customer Engagement Plan Patch",
            "quantity": 8,
            "addonItems": []
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/823c6c3f-9259-4d51-bae2-5dd06743177f/transfers/67c5b05b-09b5-47ba-9047-5056fe2afa4f",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "TransferEntity"
    }
}
```
