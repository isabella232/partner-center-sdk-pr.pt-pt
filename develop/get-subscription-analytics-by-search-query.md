---
title: Obtenha análise de subscrição por consulta de pesquisa
description: Como obter informações de análise de subscrição filtradas por uma consulta de pesquisa.
ms.date: 05/10/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c1046ea3c7e813eedae4890eebf6356337c80ede
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769055"
---
# <a name="get-subscription-analytics-information-filtered-by-a-search-query"></a><span data-ttu-id="b6ce7-103">Obter informações de análise de subscrições filtradas por uma consulta de pesquisa</span><span class="sxs-lookup"><span data-stu-id="b6ce7-103">Get subscription analytics information filtered by a search query</span></span>

<span data-ttu-id="b6ce7-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="b6ce7-104">**Applies To**</span></span>

- <span data-ttu-id="b6ce7-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="b6ce7-105">Partner Center</span></span>
- <span data-ttu-id="b6ce7-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="b6ce7-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="b6ce7-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="b6ce7-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="b6ce7-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b6ce7-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b6ce7-109">Como obter informações de análise de subscrição para os seus clientes filtrados por uma consulta de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-109">How to get subscription analytics information for your customers filtered by a search query.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6ce7-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b6ce7-110">Prerequisites</span></span>

- <span data-ttu-id="b6ce7-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce7-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b6ce7-112">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="b6ce7-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b6ce7-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b6ce7-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6ce7-114">Request syntax</span></span>

| <span data-ttu-id="b6ce7-115">Método</span><span class="sxs-lookup"><span data-stu-id="b6ce7-115">Method</span></span> | <span data-ttu-id="b6ce7-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b6ce7-116">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="b6ce7-117">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b6ce7-117">**GET**</span></span> | <span data-ttu-id="b6ce7-118">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscrições?filter={{filter_string}</span><span class="sxs-lookup"><span data-stu-id="b6ce7-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?filter={filter_string}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="b6ce7-119">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="b6ce7-119">URI parameters</span></span>

<span data-ttu-id="b6ce7-120">Utilize o seguinte parâmetro de caminho necessário para identificar a sua organização e filtrar a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-120">Use the following required path parameter to identify your organization and filter the search.</span></span>

| <span data-ttu-id="b6ce7-121">Nome</span><span class="sxs-lookup"><span data-stu-id="b6ce7-121">Name</span></span> | <span data-ttu-id="b6ce7-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="b6ce7-122">Type</span></span> | <span data-ttu-id="b6ce7-123">Necessário</span><span class="sxs-lookup"><span data-stu-id="b6ce7-123">Required</span></span> | <span data-ttu-id="b6ce7-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6ce7-124">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="b6ce7-125">filter_string</span><span class="sxs-lookup"><span data-stu-id="b6ce7-125">filter_string</span></span> | <span data-ttu-id="b6ce7-126">string</span><span class="sxs-lookup"><span data-stu-id="b6ce7-126">string</span></span> | <span data-ttu-id="b6ce7-127">Sim</span><span class="sxs-lookup"><span data-stu-id="b6ce7-127">Yes</span></span> | <span data-ttu-id="b6ce7-128">O filtro para aplicar à análise da subscrição.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-128">The filter to apply to the subscription analytics.</span></span> <span data-ttu-id="b6ce7-129">Consulte as secções de sintaxe do filtro e filtrar as secções para a sintaxe, campos e operadores utilizarem neste parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-129">See the Filter syntax and Filter fields sections for the syntax, fields, and operators to use in this parameter.</span></span> |

### <a name="filter-syntax"></a><span data-ttu-id="b6ce7-130">Sintaxe de filtro</span><span class="sxs-lookup"><span data-stu-id="b6ce7-130">Filter syntax</span></span>

<span data-ttu-id="b6ce7-131">O parâmetro do filtro deve ser composto como uma série de combinações de campo, valor e operador.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-131">The filter parameter must be composed as a series of field, value, and operator combinations.</span></span> <span data-ttu-id="b6ce7-132">Várias combinações podem ser combinadas usando **`and`** ou **`or`** operadores.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-132">Multiple combinations can be combined using **`and`** or **`or`** operators.</span></span>

<span data-ttu-id="b6ce7-133">Um exemplo não codificado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6ce7-133">An unencoded example looks like this:</span></span>

- <span data-ttu-id="b6ce7-134">Corda: `?filter=Field operator 'Value'`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-134">String: `?filter=Field operator 'Value'`</span></span>
- <span data-ttu-id="b6ce7-135">Boolean: `?filter=Field operator Value`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-135">Boolean: `?filter=Field operator Value`</span></span>
- <span data-ttu-id="b6ce7-136">Contém `?filter=contains(field,'value')`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-136">Contains `?filter=contains(field,'value')`</span></span>

### <a name="filter-fields"></a><span data-ttu-id="b6ce7-137">Campos de filtragem</span><span class="sxs-lookup"><span data-stu-id="b6ce7-137">Filter fields</span></span>

<span data-ttu-id="b6ce7-138">O parâmetro do filtro do pedido contém uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-138">The filter parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="b6ce7-139">Cada declaração contém um campo e valor que estão associados aos **`eq`** **`ne`** ou operadores.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-139">Each statement contains a field and value that are associated with the **`eq`** or **`ne`** operators.</span></span> <span data-ttu-id="b6ce7-140">Alguns campos também apoiam os **`contains`** **`gt`** , e **`lt`** **`ge`** **`le`** operadores.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-140">Some fields also support the **`contains`**, **`gt`**, **`lt`**, **`ge`**, and **`le`** operators.</span></span> <span data-ttu-id="b6ce7-141">As declarações podem ser combinadas utilizando **`and`** ou **`or`** operadores.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-141">Statements can be combined using **`and`** or **`or`** operators.</span></span>

<span data-ttu-id="b6ce7-142">Seguem-se exemplos de cordas de filtro:</span><span class="sxs-lookup"><span data-stu-id="b6ce7-142">The following are examples of filter strings:</span></span>

```http
autoRenewEnabled eq true

autoRenewEnabled eq true and customerMarket eq 'US'
```

<span data-ttu-id="b6ce7-143">A tabela a seguir mostra uma lista dos campos suportados e dos operadores de apoio para o parâmetro do filtro.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-143">The following table shows a list of the supported fields and support operators for the filter parameter.</span></span> <span data-ttu-id="b6ce7-144">Os valores das cordas devem estar rodeados de citações únicas.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-144">String values must be surrounded by single quotes.</span></span>

| <span data-ttu-id="b6ce7-145">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="b6ce7-145">Parameter</span></span> | <span data-ttu-id="b6ce7-146">Operadores apoiados</span><span class="sxs-lookup"><span data-stu-id="b6ce7-146">Supported operators</span></span> | <span data-ttu-id="b6ce7-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6ce7-147">Description</span></span> |
|-----------|---------------------|-------------|
| <span data-ttu-id="b6ce7-148">autoRenewEnabled</span><span class="sxs-lookup"><span data-stu-id="b6ce7-148">autoRenewEnabled</span></span> | <span data-ttu-id="b6ce7-149">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-149">`eq`, `ne`</span></span> | <span data-ttu-id="b6ce7-150">Um valor que indica se a subscrição é renovada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-150">A value indicating whether the subscription is renewed automatically.</span></span> |
| <span data-ttu-id="b6ce7-151">compromissoEndDate</span><span class="sxs-lookup"><span data-stu-id="b6ce7-151">commitmentEndDate</span></span> | <span data-ttu-id="b6ce7-152">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-152">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="b6ce7-153">A data em que a subscrição termina.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-153">The date the subscription ends.</span></span> |
| <span data-ttu-id="b6ce7-154">criaçãoDate</span><span class="sxs-lookup"><span data-stu-id="b6ce7-154">creationDate</span></span> | <span data-ttu-id="b6ce7-155">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-155">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="b6ce7-156">A data em que a subscrição foi criada.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-156">The date the subscription was created.</span></span> |
| <span data-ttu-id="b6ce7-157">actualStateEndDate</span><span class="sxs-lookup"><span data-stu-id="b6ce7-157">currentStateEndDate</span></span> | <span data-ttu-id="b6ce7-158">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-158">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="b6ce7-159">A data em que o estado atual da subscrição será alterado.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-159">The date that the current status of the subscription will change.</span></span> |
| <span data-ttu-id="b6ce7-160">customerMarket</span><span class="sxs-lookup"><span data-stu-id="b6ce7-160">customerMarket</span></span> | <span data-ttu-id="b6ce7-161">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-161">`eq`, `ne`</span></span> | <span data-ttu-id="b6ce7-162">O país/região em que o cliente faz negócios.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-162">The country/region that the customer does business in.</span></span> |
| <span data-ttu-id="b6ce7-163">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="b6ce7-163">customerName</span></span> | `contains` | <span data-ttu-id="b6ce7-164">O nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-164">The name of the customer.</span></span> |
| <span data-ttu-id="b6ce7-165">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="b6ce7-165">customerTenantId</span></span> | <span data-ttu-id="b6ce7-166">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-166">`eq`, `ne`</span></span> | <span data-ttu-id="b6ce7-167">Uma cadeia formatada pelo GUID que identifica o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-167">A GUID-formatted string that identifies the customer tenant.</span></span> |
| <span data-ttu-id="b6ce7-168">deprovisionedDate</span><span class="sxs-lookup"><span data-stu-id="b6ce7-168">deprovisionedDate</span></span> | <span data-ttu-id="b6ce7-169">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-169">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="b6ce7-170">A data em que a subscrição foi desprovisionada.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-170">The date that the subscription was deprovisioned.</span></span> <span data-ttu-id="b6ce7-171">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-171">The default value is null.</span></span> |
| <span data-ttu-id="b6ce7-172">effectiveStartDate</span><span class="sxs-lookup"><span data-stu-id="b6ce7-172">effectiveStartDate</span></span> | <span data-ttu-id="b6ce7-173">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-173">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="b6ce7-174">A data em que a subscrição começa.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-174">The date the subscription starts.</span></span> |
| <span data-ttu-id="b6ce7-175">nome amigável</span><span class="sxs-lookup"><span data-stu-id="b6ce7-175">friendlyName</span></span> | `contains` | <span data-ttu-id="b6ce7-176">O nome da assinatura.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-176">The name of the subscription.</span></span> |
| <span data-ttu-id="b6ce7-177">ID</span><span class="sxs-lookup"><span data-stu-id="b6ce7-177">id</span></span> | <span data-ttu-id="b6ce7-178">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-178">`eq`, `ne`</span></span> | <span data-ttu-id="b6ce7-179">Uma cadeia formatada por GUID que identifica a subscrição.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-179">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="b6ce7-180">último Aniversário deRenewal</span><span class="sxs-lookup"><span data-stu-id="b6ce7-180">lastRenewalDate</span></span> | <span data-ttu-id="b6ce7-181">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-181">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="b6ce7-182">A data em que a subscrição foi renovada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-182">The date that the subscription was last renewed.</span></span> <span data-ttu-id="b6ce7-183">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-183">The default value is null.</span></span> |
| <span data-ttu-id="b6ce7-184">lastUsageDate</span><span class="sxs-lookup"><span data-stu-id="b6ce7-184">lastUsageDate</span></span> | <span data-ttu-id="b6ce7-185">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-185">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="b6ce7-186">A data em que a assinatura foi usada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-186">The date that the subscription was last used.</span></span> <span data-ttu-id="b6ce7-187">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-187">The default value is null.</span></span> |
| <span data-ttu-id="b6ce7-188">partnerId</span><span class="sxs-lookup"><span data-stu-id="b6ce7-188">partnerId</span></span> | <span data-ttu-id="b6ce7-189">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-189">`eq`, `ne`</span></span> | <span data-ttu-id="b6ce7-190">A identificação do MPN.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-190">The MPN ID.</span></span> <span data-ttu-id="b6ce7-191">Para um revendedor direto, este valor será o ID MPN do parceiro.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-191">For a direct reseller, this value will be the MPN ID of the partner.</span></span> <span data-ttu-id="b6ce7-192">Para um revendedor indireto, este valor será o ID MPN do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-192">For an indirect reseller, this value will be the MPN ID of the indirect reseller.</span></span> |
| <span data-ttu-id="b6ce7-193">nome parceiro</span><span class="sxs-lookup"><span data-stu-id="b6ce7-193">partnerName</span></span> | <span data-ttu-id="b6ce7-194">string</span><span class="sxs-lookup"><span data-stu-id="b6ce7-194">string</span></span> | <span data-ttu-id="b6ce7-195">Nome do parceiro para quem a assinatura foi comprada</span><span class="sxs-lookup"><span data-stu-id="b6ce7-195">Name of the partner for whom the subscription was purchased</span></span> |
| <span data-ttu-id="b6ce7-196">produtoName</span><span class="sxs-lookup"><span data-stu-id="b6ce7-196">productName</span></span> | <span data-ttu-id="b6ce7-197">`contains`, `eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-197">`contains`, `eq`, `ne`</span></span> | <span data-ttu-id="b6ce7-198">O nome do produto.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-198">The name of the product.</span></span> |
| <span data-ttu-id="b6ce7-199">provedorName</span><span class="sxs-lookup"><span data-stu-id="b6ce7-199">providerName</span></span> | <span data-ttu-id="b6ce7-200">string</span><span class="sxs-lookup"><span data-stu-id="b6ce7-200">string</span></span> | <span data-ttu-id="b6ce7-201">Quando a transação de subscrição é para o revendedor indireto, o nome do fornecedor é o fornecedor indireto que comprou a subscrição.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-201">When subscription transaction is for the indirect reseller, provider name is the indirect provider who bought the subscription.</span></span>|
| <span data-ttu-id="b6ce7-202">status</span><span class="sxs-lookup"><span data-stu-id="b6ce7-202">status</span></span> | <span data-ttu-id="b6ce7-203">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-203">`eq`, `ne`</span></span> | <span data-ttu-id="b6ce7-204">O estado da subscrição.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-204">The subscription status.</span></span> <span data-ttu-id="b6ce7-205">Os valores suportados são: "ATIVE", "SUSPENDED", ou "DEPROVISIONED".</span><span class="sxs-lookup"><span data-stu-id="b6ce7-205">Supported values are: "ACTIVE", "SUSPENDED", or "DEPROVISIONED".</span></span> |
| <span data-ttu-id="b6ce7-206">Tipo de subscrição</span><span class="sxs-lookup"><span data-stu-id="b6ce7-206">subscriptionType</span></span> | <span data-ttu-id="b6ce7-207">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-207">`eq`, `ne`</span></span> | <span data-ttu-id="b6ce7-208">O tipo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-208">The subscription type.</span></span> <span data-ttu-id="b6ce7-209">**Nota:** Este campo é sensível a casos.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-209">**Note**: This field is case-sensitive.</span></span> <span data-ttu-id="b6ce7-210">Os valores suportados são: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span><span class="sxs-lookup"><span data-stu-id="b6ce7-210">Supported values are: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span></span> |
| <span data-ttu-id="b6ce7-211">trialStartDate</span><span class="sxs-lookup"><span data-stu-id="b6ce7-211">trialStartDate</span></span> | <span data-ttu-id="b6ce7-212">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-212">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="b6ce7-213">A data em que o período experimental da subscrição começou.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-213">The date that the trial period for the subscription started.</span></span> <span data-ttu-id="b6ce7-214">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-214">The default value is null.</span></span> |
| <span data-ttu-id="b6ce7-215">trialToPaidConversionDate</span><span class="sxs-lookup"><span data-stu-id="b6ce7-215">trialToPaidConversionDate</span></span> | <span data-ttu-id="b6ce7-216">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="b6ce7-216">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="b6ce7-217">A data em que a subscrição converte do julgamento para o pagamento.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-217">The date that the subscription converts from trial to paid.</span></span> <span data-ttu-id="b6ce7-218">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-218">The default value is null.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b6ce7-219">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b6ce7-219">Request headers</span></span>

<span data-ttu-id="b6ce7-220">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce7-220">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b6ce7-221">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b6ce7-221">Request body</span></span>

<span data-ttu-id="b6ce7-222">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-222">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b6ce7-223">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b6ce7-223">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?filter=autoRenewEnabled eq true
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="b6ce7-224">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b6ce7-224">REST response</span></span>

<span data-ttu-id="b6ce7-225">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [Subscrição](partner-center-analytics-resources.md#subscription-resource) que satisfazem os critérios do filtro.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-225">If successful, the response body contains a collection of [Subscription](partner-center-analytics-resources.md#subscription-resource) resources that meet the filter criteria.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b6ce7-226">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b6ce7-226">Response success and error codes</span></span>

<span data-ttu-id="b6ce7-227">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-227">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b6ce7-228">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b6ce7-228">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b6ce7-229">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce7-229">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b6ce7-230">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b6ce7-230">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b6ce7-231">Ver também</span><span class="sxs-lookup"><span data-stu-id="b6ce7-231">See also</span></span>

- [<span data-ttu-id="b6ce7-232">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="b6ce7-232">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
