---
title: Obtenha análise de subscrição por consulta de pesquisa
description: Como obter informações de análise de subscrição filtradas por uma consulta de pesquisa.
ms.date: 05/10/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8df777b9a88206f8b22579f0f445c54d80f7cd64
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548741"
---
# <a name="get-subscription-analytics-information-filtered-by-a-search-query"></a><span data-ttu-id="0bef0-103">Obter informações de análise de subscrições filtradas por uma consulta de pesquisa</span><span class="sxs-lookup"><span data-stu-id="0bef0-103">Get subscription analytics information filtered by a search query</span></span>

<span data-ttu-id="0bef0-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0bef0-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0bef0-105">Como obter informações de análise de subscrição para os seus clientes filtrados por uma consulta de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0bef0-105">How to get subscription analytics information for your customers filtered by a search query.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0bef0-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0bef0-106">Prerequisites</span></span>

- <span data-ttu-id="0bef0-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0bef0-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0bef0-108">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="0bef0-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="0bef0-109">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="0bef0-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0bef0-110">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bef0-110">Request syntax</span></span>

| <span data-ttu-id="0bef0-111">Método</span><span class="sxs-lookup"><span data-stu-id="0bef0-111">Method</span></span> | <span data-ttu-id="0bef0-112">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="0bef0-112">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="0bef0-113">**Obter**</span><span class="sxs-lookup"><span data-stu-id="0bef0-113">**GET**</span></span> | <span data-ttu-id="0bef0-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscrições?filter={{filter_string}</span><span class="sxs-lookup"><span data-stu-id="0bef0-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?filter={filter_string}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="0bef0-115">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="0bef0-115">URI parameters</span></span>

<span data-ttu-id="0bef0-116">Utilize o seguinte parâmetro de caminho necessário para identificar a sua organização e filtrar a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0bef0-116">Use the following required path parameter to identify your organization and filter the search.</span></span>

| <span data-ttu-id="0bef0-117">Nome</span><span class="sxs-lookup"><span data-stu-id="0bef0-117">Name</span></span> | <span data-ttu-id="0bef0-118">Tipo</span><span class="sxs-lookup"><span data-stu-id="0bef0-118">Type</span></span> | <span data-ttu-id="0bef0-119">Necessário</span><span class="sxs-lookup"><span data-stu-id="0bef0-119">Required</span></span> | <span data-ttu-id="0bef0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bef0-120">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="0bef0-121">filter_string</span><span class="sxs-lookup"><span data-stu-id="0bef0-121">filter_string</span></span> | <span data-ttu-id="0bef0-122">string</span><span class="sxs-lookup"><span data-stu-id="0bef0-122">string</span></span> | <span data-ttu-id="0bef0-123">Yes</span><span class="sxs-lookup"><span data-stu-id="0bef0-123">Yes</span></span> | <span data-ttu-id="0bef0-124">O filtro para aplicar à análise da subscrição.</span><span class="sxs-lookup"><span data-stu-id="0bef0-124">The filter to apply to the subscription analytics.</span></span> <span data-ttu-id="0bef0-125">Consulte as secções de sintaxe do filtro e filtrar as secções para a sintaxe, campos e operadores utilizarem neste parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0bef0-125">See the Filter syntax and Filter fields sections for the syntax, fields, and operators to use in this parameter.</span></span> |

### <a name="filter-syntax"></a><span data-ttu-id="0bef0-126">Sintaxe de filtro</span><span class="sxs-lookup"><span data-stu-id="0bef0-126">Filter syntax</span></span>

<span data-ttu-id="0bef0-127">O parâmetro do filtro deve ser composto como uma série de combinações de campo, valor e operador.</span><span class="sxs-lookup"><span data-stu-id="0bef0-127">The filter parameter must be composed as a series of field, value, and operator combinations.</span></span> <span data-ttu-id="0bef0-128">Várias combinações podem ser combinadas usando **`and`** ou **`or`** operadores.</span><span class="sxs-lookup"><span data-stu-id="0bef0-128">Multiple combinations can be combined using **`and`** or **`or`** operators.</span></span>

<span data-ttu-id="0bef0-129">Um exemplo não codificado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0bef0-129">An unencoded example looks like this:</span></span>

- <span data-ttu-id="0bef0-130">Corda: `?filter=Field operator 'Value'`</span><span class="sxs-lookup"><span data-stu-id="0bef0-130">String: `?filter=Field operator 'Value'`</span></span>
- <span data-ttu-id="0bef0-131">Boolean: `?filter=Field operator Value`</span><span class="sxs-lookup"><span data-stu-id="0bef0-131">Boolean: `?filter=Field operator Value`</span></span>
- <span data-ttu-id="0bef0-132">Contém `?filter=contains(field,'value')`</span><span class="sxs-lookup"><span data-stu-id="0bef0-132">Contains `?filter=contains(field,'value')`</span></span>

### <a name="filter-fields"></a><span data-ttu-id="0bef0-133">Campos de filtragem</span><span class="sxs-lookup"><span data-stu-id="0bef0-133">Filter fields</span></span>

<span data-ttu-id="0bef0-134">O parâmetro do filtro do pedido contém uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="0bef0-134">The filter parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="0bef0-135">Cada declaração contém um campo e valor que estão associados aos **`eq`** **`ne`** ou operadores.</span><span class="sxs-lookup"><span data-stu-id="0bef0-135">Each statement contains a field and value that are associated with the **`eq`** or **`ne`** operators.</span></span> <span data-ttu-id="0bef0-136">Alguns campos também apoiam os **`contains`** **`gt`** , e **`lt`** **`ge`** **`le`** operadores.</span><span class="sxs-lookup"><span data-stu-id="0bef0-136">Some fields also support the **`contains`**, **`gt`**, **`lt`**, **`ge`**, and **`le`** operators.</span></span> <span data-ttu-id="0bef0-137">As declarações podem ser combinadas utilizando **`and`** ou **`or`** operadores.</span><span class="sxs-lookup"><span data-stu-id="0bef0-137">Statements can be combined using **`and`** or **`or`** operators.</span></span>

<span data-ttu-id="0bef0-138">Seguem-se exemplos de cordas de filtro:</span><span class="sxs-lookup"><span data-stu-id="0bef0-138">The following are examples of filter strings:</span></span>

```http
autoRenewEnabled eq true

autoRenewEnabled eq true and customerMarket eq 'US'
```

<span data-ttu-id="0bef0-139">A tabela a seguir mostra uma lista dos campos suportados e dos operadores de apoio para o parâmetro do filtro.</span><span class="sxs-lookup"><span data-stu-id="0bef0-139">The following table shows a list of the supported fields and support operators for the filter parameter.</span></span> <span data-ttu-id="0bef0-140">Os valores das cordas devem estar rodeados de citações únicas.</span><span class="sxs-lookup"><span data-stu-id="0bef0-140">String values must be surrounded by single quotes.</span></span>

| <span data-ttu-id="0bef0-141">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="0bef0-141">Parameter</span></span> | <span data-ttu-id="0bef0-142">Operadores apoiados</span><span class="sxs-lookup"><span data-stu-id="0bef0-142">Supported operators</span></span> | <span data-ttu-id="0bef0-143">Description</span><span class="sxs-lookup"><span data-stu-id="0bef0-143">Description</span></span> |
|-----------|---------------------|-------------|
| <span data-ttu-id="0bef0-144">autoRenewEnabled</span><span class="sxs-lookup"><span data-stu-id="0bef0-144">autoRenewEnabled</span></span> | <span data-ttu-id="0bef0-145">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="0bef0-145">`eq`, `ne`</span></span> | <span data-ttu-id="0bef0-146">Um valor que indica se a subscrição é renovada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0bef0-146">A value indicating whether the subscription is renewed automatically.</span></span> |
| <span data-ttu-id="0bef0-147">compromissoEndDate</span><span class="sxs-lookup"><span data-stu-id="0bef0-147">commitmentEndDate</span></span> | <span data-ttu-id="0bef0-148">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="0bef0-148">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="0bef0-149">A data em que a subscrição termina.</span><span class="sxs-lookup"><span data-stu-id="0bef0-149">The date the subscription ends.</span></span> |
| <span data-ttu-id="0bef0-150">criaçãoDate</span><span class="sxs-lookup"><span data-stu-id="0bef0-150">creationDate</span></span> | <span data-ttu-id="0bef0-151">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="0bef0-151">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="0bef0-152">A data em que a subscrição foi criada.</span><span class="sxs-lookup"><span data-stu-id="0bef0-152">The date the subscription was created.</span></span> |
| <span data-ttu-id="0bef0-153">actualStateEndDate</span><span class="sxs-lookup"><span data-stu-id="0bef0-153">currentStateEndDate</span></span> | <span data-ttu-id="0bef0-154">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="0bef0-154">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="0bef0-155">A data em que o estado atual da subscrição será alterado.</span><span class="sxs-lookup"><span data-stu-id="0bef0-155">The date that the current status of the subscription will change.</span></span> |
| <span data-ttu-id="0bef0-156">customerMarket</span><span class="sxs-lookup"><span data-stu-id="0bef0-156">customerMarket</span></span> | <span data-ttu-id="0bef0-157">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="0bef0-157">`eq`, `ne`</span></span> | <span data-ttu-id="0bef0-158">O país/região em que o cliente faz negócios.</span><span class="sxs-lookup"><span data-stu-id="0bef0-158">The country/region that the customer does business in.</span></span> |
| <span data-ttu-id="0bef0-159">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="0bef0-159">customerName</span></span> | `contains` | <span data-ttu-id="0bef0-160">O nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="0bef0-160">The name of the customer.</span></span> |
| <span data-ttu-id="0bef0-161">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="0bef0-161">customerTenantId</span></span> | <span data-ttu-id="0bef0-162">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="0bef0-162">`eq`, `ne`</span></span> | <span data-ttu-id="0bef0-163">Uma cadeia formatada pelo GUID que identifica o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="0bef0-163">A GUID-formatted string that identifies the customer tenant.</span></span> |
| <span data-ttu-id="0bef0-164">deprovisionedDate</span><span class="sxs-lookup"><span data-stu-id="0bef0-164">deprovisionedDate</span></span> | <span data-ttu-id="0bef0-165">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="0bef0-165">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="0bef0-166">A data em que a subscrição foi desprovisionada.</span><span class="sxs-lookup"><span data-stu-id="0bef0-166">The date that the subscription was deprovisioned.</span></span> <span data-ttu-id="0bef0-167">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="0bef0-167">The default value is null.</span></span> |
| <span data-ttu-id="0bef0-168">effectiveStartDate</span><span class="sxs-lookup"><span data-stu-id="0bef0-168">effectiveStartDate</span></span> | <span data-ttu-id="0bef0-169">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="0bef0-169">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="0bef0-170">A data em que a subscrição começa.</span><span class="sxs-lookup"><span data-stu-id="0bef0-170">The date the subscription starts.</span></span> |
| <span data-ttu-id="0bef0-171">nome amigável</span><span class="sxs-lookup"><span data-stu-id="0bef0-171">friendlyName</span></span> | `contains` | <span data-ttu-id="0bef0-172">O nome da assinatura.</span><span class="sxs-lookup"><span data-stu-id="0bef0-172">The name of the subscription.</span></span> |
| <span data-ttu-id="0bef0-173">ID</span><span class="sxs-lookup"><span data-stu-id="0bef0-173">id</span></span> | <span data-ttu-id="0bef0-174">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="0bef0-174">`eq`, `ne`</span></span> | <span data-ttu-id="0bef0-175">Uma cadeia formatada por GUID que identifica a subscrição.</span><span class="sxs-lookup"><span data-stu-id="0bef0-175">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="0bef0-176">último Aniversário deRenewal</span><span class="sxs-lookup"><span data-stu-id="0bef0-176">lastRenewalDate</span></span> | <span data-ttu-id="0bef0-177">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="0bef0-177">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="0bef0-178">A data em que a subscrição foi renovada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="0bef0-178">The date that the subscription was last renewed.</span></span> <span data-ttu-id="0bef0-179">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="0bef0-179">The default value is null.</span></span> |
| <span data-ttu-id="0bef0-180">lastUsageDate</span><span class="sxs-lookup"><span data-stu-id="0bef0-180">lastUsageDate</span></span> | <span data-ttu-id="0bef0-181">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="0bef0-181">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="0bef0-182">A data em que a assinatura foi usada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="0bef0-182">The date that the subscription was last used.</span></span> <span data-ttu-id="0bef0-183">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="0bef0-183">The default value is null.</span></span> |
| <span data-ttu-id="0bef0-184">partnerId</span><span class="sxs-lookup"><span data-stu-id="0bef0-184">partnerId</span></span> | <span data-ttu-id="0bef0-185">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="0bef0-185">`eq`, `ne`</span></span> | <span data-ttu-id="0bef0-186">A identificação do MPN.</span><span class="sxs-lookup"><span data-stu-id="0bef0-186">The MPN ID.</span></span> <span data-ttu-id="0bef0-187">Para um revendedor direto, este valor será o ID MPN do parceiro.</span><span class="sxs-lookup"><span data-stu-id="0bef0-187">For a direct reseller, this value will be the MPN ID of the partner.</span></span> <span data-ttu-id="0bef0-188">Para um revendedor indireto, este valor será o ID MPN do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="0bef0-188">For an indirect reseller, this value will be the MPN ID of the indirect reseller.</span></span> |
| <span data-ttu-id="0bef0-189">nome parceiro</span><span class="sxs-lookup"><span data-stu-id="0bef0-189">partnerName</span></span> | <span data-ttu-id="0bef0-190">string</span><span class="sxs-lookup"><span data-stu-id="0bef0-190">string</span></span> | <span data-ttu-id="0bef0-191">Nome do parceiro para quem a assinatura foi comprada</span><span class="sxs-lookup"><span data-stu-id="0bef0-191">Name of the partner for whom the subscription was purchased</span></span> |
| <span data-ttu-id="0bef0-192">produtoName</span><span class="sxs-lookup"><span data-stu-id="0bef0-192">productName</span></span> | <span data-ttu-id="0bef0-193">`contains`, `eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="0bef0-193">`contains`, `eq`, `ne`</span></span> | <span data-ttu-id="0bef0-194">O nome do produto.</span><span class="sxs-lookup"><span data-stu-id="0bef0-194">The name of the product.</span></span> |
| <span data-ttu-id="0bef0-195">provedorName</span><span class="sxs-lookup"><span data-stu-id="0bef0-195">providerName</span></span> | <span data-ttu-id="0bef0-196">string</span><span class="sxs-lookup"><span data-stu-id="0bef0-196">string</span></span> | <span data-ttu-id="0bef0-197">Quando a transação de subscrição é para o revendedor indireto, o nome do fornecedor é o fornecedor indireto que comprou a subscrição.</span><span class="sxs-lookup"><span data-stu-id="0bef0-197">When subscription transaction is for the indirect reseller, provider name is the indirect provider who bought the subscription.</span></span>|
| <span data-ttu-id="0bef0-198">status</span><span class="sxs-lookup"><span data-stu-id="0bef0-198">status</span></span> | <span data-ttu-id="0bef0-199">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="0bef0-199">`eq`, `ne`</span></span> | <span data-ttu-id="0bef0-200">O estado da subscrição.</span><span class="sxs-lookup"><span data-stu-id="0bef0-200">The subscription status.</span></span> <span data-ttu-id="0bef0-201">Os valores suportados são: "ATIVE", "SUSPENDED", ou "DEPROVISIONED".</span><span class="sxs-lookup"><span data-stu-id="0bef0-201">Supported values are: "ACTIVE", "SUSPENDED", or "DEPROVISIONED".</span></span> |
| <span data-ttu-id="0bef0-202">Tipo de subscrição</span><span class="sxs-lookup"><span data-stu-id="0bef0-202">subscriptionType</span></span> | <span data-ttu-id="0bef0-203">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="0bef0-203">`eq`, `ne`</span></span> | <span data-ttu-id="0bef0-204">O tipo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="0bef0-204">The subscription type.</span></span> <span data-ttu-id="0bef0-205">**Nota:** Este campo é sensível a casos.</span><span class="sxs-lookup"><span data-stu-id="0bef0-205">**Note**: This field is case-sensitive.</span></span> <span data-ttu-id="0bef0-206">Os valores suportados são: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span><span class="sxs-lookup"><span data-stu-id="0bef0-206">Supported values are: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span></span> |
| <span data-ttu-id="0bef0-207">trialStartDate</span><span class="sxs-lookup"><span data-stu-id="0bef0-207">trialStartDate</span></span> | <span data-ttu-id="0bef0-208">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="0bef0-208">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="0bef0-209">A data em que o período experimental da subscrição começou.</span><span class="sxs-lookup"><span data-stu-id="0bef0-209">The date that the trial period for the subscription started.</span></span> <span data-ttu-id="0bef0-210">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="0bef0-210">The default value is null.</span></span> |
| <span data-ttu-id="0bef0-211">trialToPaidConversionDate</span><span class="sxs-lookup"><span data-stu-id="0bef0-211">trialToPaidConversionDate</span></span> | <span data-ttu-id="0bef0-212">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="0bef0-212">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="0bef0-213">A data em que a subscrição converte do julgamento para o pagamento.</span><span class="sxs-lookup"><span data-stu-id="0bef0-213">The date that the subscription converts from trial to paid.</span></span> <span data-ttu-id="0bef0-214">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="0bef0-214">The default value is null.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="0bef0-215">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="0bef0-215">Request headers</span></span>

<span data-ttu-id="0bef0-216">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="0bef0-216">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0bef0-217">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="0bef0-217">Request body</span></span>

<span data-ttu-id="0bef0-218">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0bef0-218">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0bef0-219">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="0bef0-219">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?filter=autoRenewEnabled eq true
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="0bef0-220">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="0bef0-220">REST response</span></span>

<span data-ttu-id="0bef0-221">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [Subscrição](partner-center-analytics-resources.md#subscription-resource) que satisfazem os critérios do filtro.</span><span class="sxs-lookup"><span data-stu-id="0bef0-221">If successful, the response body contains a collection of [Subscription](partner-center-analytics-resources.md#subscription-resource) resources that meet the filter criteria.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0bef0-222">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="0bef0-222">Response success and error codes</span></span>

<span data-ttu-id="0bef0-223">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="0bef0-223">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0bef0-224">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="0bef0-224">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0bef0-225">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="0bef0-225">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0bef0-226">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="0bef0-226">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123

{
    "customerTenantId": "735920EB-A564-4C72-9FE5-52632562712C",
    "customerName": "SURFACE TEST2",
    "customerMarket": "US",
    "id": "B76412DA-D382-4688-A6A4-711A207C1C2E",
    "status": "ACTIVE",
    "productName": "UNKNOWN",
    "subscriptionType": "Azure",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "MICROSOFT AZURE",
    "creationDate": "2017-06-02T23:11:58.747",
    "effectiveStartDate": "2017-06-02T00:00:00",
    "commitmentEndDate": null,
    "currentStateEndDate": null,
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": null,
    "licenseCount": 0
}
```

## <a name="see-also"></a><span data-ttu-id="0bef0-227">Ver também</span><span class="sxs-lookup"><span data-stu-id="0bef0-227">See also</span></span>

- [<span data-ttu-id="0bef0-228">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="0bef0-228">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
