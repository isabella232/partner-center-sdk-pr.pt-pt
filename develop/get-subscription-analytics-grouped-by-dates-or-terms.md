---
title: Obter análise de subscrição agrupada por datas ou termos
description: Como obter informações de análise de subscrição agrupadas por datas ou termos.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4a9946027fa89f5a93fff5eede86e36a6be5b721
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769050"
---
# <a name="get-subscription-analytics-grouped-by-dates-or-terms"></a><span data-ttu-id="6122c-103">Obter análise de subscrição agrupada por datas ou termos</span><span class="sxs-lookup"><span data-stu-id="6122c-103">Get subscription analytics grouped by dates or terms</span></span>

<span data-ttu-id="6122c-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="6122c-104">**Applies To**</span></span>

- <span data-ttu-id="6122c-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="6122c-105">Partner Center</span></span>
- <span data-ttu-id="6122c-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="6122c-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="6122c-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="6122c-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="6122c-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6122c-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6122c-109">Como obter informações de análise de subscrição para os seus clientes agrupados por datas ou termos.</span><span class="sxs-lookup"><span data-stu-id="6122c-109">How to get subscription analytics information for your customers grouped by dates or terms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6122c-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6122c-110">Prerequisites</span></span>

- <span data-ttu-id="6122c-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6122c-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6122c-112">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="6122c-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="6122c-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6122c-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6122c-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6122c-114">Request syntax</span></span>

| <span data-ttu-id="6122c-115">Método</span><span class="sxs-lookup"><span data-stu-id="6122c-115">Method</span></span> | <span data-ttu-id="6122c-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6122c-116">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="6122c-117">**Obter**</span><span class="sxs-lookup"><span data-stu-id="6122c-117">**GET**</span></span> | <span data-ttu-id="6122c-118">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?groupby={groupby_queries}</span><span class="sxs-lookup"><span data-stu-id="6122c-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?groupby={groupby_queries}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="6122c-119">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="6122c-119">URI parameters</span></span>

<span data-ttu-id="6122c-120">Utilize os seguintes parâmetros de caminho necessários para identificar a sua organização e para agrupar os resultados.</span><span class="sxs-lookup"><span data-stu-id="6122c-120">Use the following required path parameters to identify your organization and to group the results.</span></span>

| <span data-ttu-id="6122c-121">Nome</span><span class="sxs-lookup"><span data-stu-id="6122c-121">Name</span></span> | <span data-ttu-id="6122c-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="6122c-122">Type</span></span> | <span data-ttu-id="6122c-123">Necessário</span><span class="sxs-lookup"><span data-stu-id="6122c-123">Required</span></span> | <span data-ttu-id="6122c-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="6122c-124">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="6122c-125">groupby_queries</span><span class="sxs-lookup"><span data-stu-id="6122c-125">groupby_queries</span></span> | <span data-ttu-id="6122c-126">pares de cordas e dataTime</span><span class="sxs-lookup"><span data-stu-id="6122c-126">pairs of strings and dateTime</span></span> | <span data-ttu-id="6122c-127">Sim</span><span class="sxs-lookup"><span data-stu-id="6122c-127">Yes</span></span> | <span data-ttu-id="6122c-128">Os termos e datas para filtrar o resultado.</span><span class="sxs-lookup"><span data-stu-id="6122c-128">The terms and dates to filter the result.</span></span> |

### <a name="groupby-syntax"></a><span data-ttu-id="6122c-129">Sintaxe GroupBy</span><span class="sxs-lookup"><span data-stu-id="6122c-129">GroupBy syntax</span></span>

<span data-ttu-id="6122c-130">O grupo por parâmetro deve ser composto como uma série de vírgulas separadas, valores de campo.</span><span class="sxs-lookup"><span data-stu-id="6122c-130">The group by parameter must be composed as a series of comma separated, field values.</span></span>

<span data-ttu-id="6122c-131">Um exemplo não codificado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6122c-131">An unencoded example looks like this:</span></span>

```http
?groupby=termField1,dateField1,termField2
```

<span data-ttu-id="6122c-132">A tabela seguinte mostra uma lista dos campos suportados para grupo por.</span><span class="sxs-lookup"><span data-stu-id="6122c-132">The following table shows a list of the supported fields for group by.</span></span>

| <span data-ttu-id="6122c-133">Campo</span><span class="sxs-lookup"><span data-stu-id="6122c-133">Field</span></span> | <span data-ttu-id="6122c-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="6122c-134">Type</span></span> | <span data-ttu-id="6122c-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="6122c-135">Description</span></span> |
|-------|------|-------------|
| <span data-ttu-id="6122c-136">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="6122c-136">customerTenantId</span></span> | <span data-ttu-id="6122c-137">string</span><span class="sxs-lookup"><span data-stu-id="6122c-137">string</span></span> | <span data-ttu-id="6122c-138">Uma cadeia formatada pelo GUID que identifica o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="6122c-138">A GUID-formatted string that identifies the customer tenant.</span></span> |
| <span data-ttu-id="6122c-139">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="6122c-139">customerName</span></span> | <span data-ttu-id="6122c-140">string</span><span class="sxs-lookup"><span data-stu-id="6122c-140">string</span></span> | <span data-ttu-id="6122c-141">O nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="6122c-141">The name of the customer.</span></span> |
| <span data-ttu-id="6122c-142">customerMarket</span><span class="sxs-lookup"><span data-stu-id="6122c-142">customerMarket</span></span> | <span data-ttu-id="6122c-143">string</span><span class="sxs-lookup"><span data-stu-id="6122c-143">string</span></span> | <span data-ttu-id="6122c-144">O país/região em que o cliente faz negócios.</span><span class="sxs-lookup"><span data-stu-id="6122c-144">The country/region that the customer does business in.</span></span> |
| <span data-ttu-id="6122c-145">ID</span><span class="sxs-lookup"><span data-stu-id="6122c-145">id</span></span> | <span data-ttu-id="6122c-146">string</span><span class="sxs-lookup"><span data-stu-id="6122c-146">string</span></span> | <span data-ttu-id="6122c-147">Uma cadeia formatada por GUID que identifica a subscrição.</span><span class="sxs-lookup"><span data-stu-id="6122c-147">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="6122c-148">status</span><span class="sxs-lookup"><span data-stu-id="6122c-148">status</span></span> | <span data-ttu-id="6122c-149">string</span><span class="sxs-lookup"><span data-stu-id="6122c-149">string</span></span> | <span data-ttu-id="6122c-150">O estado da subscrição.</span><span class="sxs-lookup"><span data-stu-id="6122c-150">The subscription status.</span></span> <span data-ttu-id="6122c-151">Os valores suportados são: "ATIVE", "SUSPENDED", ou "DEPROVISIONED".</span><span class="sxs-lookup"><span data-stu-id="6122c-151">Supported values are: "ACTIVE", "SUSPENDED", or "DEPROVISIONED".</span></span> |
| <span data-ttu-id="6122c-152">produtoName</span><span class="sxs-lookup"><span data-stu-id="6122c-152">productName</span></span> | <span data-ttu-id="6122c-153">string</span><span class="sxs-lookup"><span data-stu-id="6122c-153">string</span></span> | <span data-ttu-id="6122c-154">O nome do produto.</span><span class="sxs-lookup"><span data-stu-id="6122c-154">The name of the product.</span></span> |
| <span data-ttu-id="6122c-155">Tipo de subscrição</span><span class="sxs-lookup"><span data-stu-id="6122c-155">subscriptionType</span></span> | <span data-ttu-id="6122c-156">string</span><span class="sxs-lookup"><span data-stu-id="6122c-156">string</span></span> | <span data-ttu-id="6122c-157">O tipo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="6122c-157">The subscription type.</span></span> <span data-ttu-id="6122c-158">Nota: Este campo é sensível a casos.</span><span class="sxs-lookup"><span data-stu-id="6122c-158">Note: This field is case sensitive.</span></span> <span data-ttu-id="6122c-159">Os valores suportados são: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span><span class="sxs-lookup"><span data-stu-id="6122c-159">Supported values are: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span></span> |
| <span data-ttu-id="6122c-160">autoRenewEnabled</span><span class="sxs-lookup"><span data-stu-id="6122c-160">autoRenewEnabled</span></span> | <span data-ttu-id="6122c-161">Booleano</span><span class="sxs-lookup"><span data-stu-id="6122c-161">Boolean</span></span> | <span data-ttu-id="6122c-162">Um valor que indica se a subscrição é renovada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6122c-162">A value indicating whether the subscription is renewed automatically.</span></span> |
| <span data-ttu-id="6122c-163">partnerId</span><span class="sxs-lookup"><span data-stu-id="6122c-163">partnerId</span></span>  | <span data-ttu-id="6122c-164">string</span><span class="sxs-lookup"><span data-stu-id="6122c-164">string</span></span> | <span data-ttu-id="6122c-165">A identificação do MPN.</span><span class="sxs-lookup"><span data-stu-id="6122c-165">The MPN ID.</span></span> <span data-ttu-id="6122c-166">Para um revendedor direto, este parâmetro será o ID MPN do parceiro.</span><span class="sxs-lookup"><span data-stu-id="6122c-166">For a direct reseller, this parameter will be the MPN ID of the partner.</span></span> <span data-ttu-id="6122c-167">Para um revendedor indireto, este parâmetro será o ID MPN do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="6122c-167">For an indirect reseller, this parameter will be the MPN ID of the indirect reseller.</span></span> |
| <span data-ttu-id="6122c-168">nome amigável</span><span class="sxs-lookup"><span data-stu-id="6122c-168">friendlyName</span></span> | <span data-ttu-id="6122c-169">string</span><span class="sxs-lookup"><span data-stu-id="6122c-169">string</span></span> | <span data-ttu-id="6122c-170">O nome da assinatura.</span><span class="sxs-lookup"><span data-stu-id="6122c-170">The name of the subscription.</span></span> |
| <span data-ttu-id="6122c-171">nome parceiro</span><span class="sxs-lookup"><span data-stu-id="6122c-171">partnerName</span></span> | <span data-ttu-id="6122c-172">string</span><span class="sxs-lookup"><span data-stu-id="6122c-172">string</span></span> | <span data-ttu-id="6122c-173">Nome do parceiro para quem a assinatura foi comprada</span><span class="sxs-lookup"><span data-stu-id="6122c-173">Name of the partner for whom the subscription was purchased</span></span> |
| <span data-ttu-id="6122c-174">provedorName</span><span class="sxs-lookup"><span data-stu-id="6122c-174">providerName</span></span> | <span data-ttu-id="6122c-175">string</span><span class="sxs-lookup"><span data-stu-id="6122c-175">string</span></span> | <span data-ttu-id="6122c-176">Quando a transação de subscrição é para o revendedor indireto, o nome do fornecedor é o fornecedor indireto que comprou a subscrição.</span><span class="sxs-lookup"><span data-stu-id="6122c-176">When subscription transaction is for the indirect reseller, provider name is the indirect provider who bought the subscription.</span></span>
| <span data-ttu-id="6122c-177">criaçãoDate</span><span class="sxs-lookup"><span data-stu-id="6122c-177">creationDate</span></span> | <span data-ttu-id="6122c-178">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="6122c-178">string in UTC date time format</span></span> | <span data-ttu-id="6122c-179">A data em que a subscrição foi criada.</span><span class="sxs-lookup"><span data-stu-id="6122c-179">The date the subscription was created.</span></span> |
| <span data-ttu-id="6122c-180">effectiveStartDate</span><span class="sxs-lookup"><span data-stu-id="6122c-180">effectiveStartDate</span></span> | <span data-ttu-id="6122c-181">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="6122c-181">string in UTC date time format</span></span> | <span data-ttu-id="6122c-182">A data em que a subscrição começa.</span><span class="sxs-lookup"><span data-stu-id="6122c-182">The date the subscription starts.</span></span> |
| <span data-ttu-id="6122c-183">compromissoEndDate</span><span class="sxs-lookup"><span data-stu-id="6122c-183">commitmentEndDate</span></span> | <span data-ttu-id="6122c-184">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="6122c-184">string in UTC date time format</span></span> | <span data-ttu-id="6122c-185">A data em que a subscrição termina.</span><span class="sxs-lookup"><span data-stu-id="6122c-185">The date the subscription ends.</span></span> |
| <span data-ttu-id="6122c-186">actualStateEndDate</span><span class="sxs-lookup"><span data-stu-id="6122c-186">currentStateEndDate</span></span> | <span data-ttu-id="6122c-187">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="6122c-187">string in UTC date time format</span></span> | <span data-ttu-id="6122c-188">A data em que o estado atual da subscrição será alterado.</span><span class="sxs-lookup"><span data-stu-id="6122c-188">The date that the current status of the subscription will change.</span></span> |
| <span data-ttu-id="6122c-189">trialToPaidConversionDate</span><span class="sxs-lookup"><span data-stu-id="6122c-189">trialToPaidConversionDate</span></span> | <span data-ttu-id="6122c-190">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="6122c-190">string in UTC date time format</span></span> | <span data-ttu-id="6122c-191">A data em que a subscrição converte do julgamento para o pagamento.</span><span class="sxs-lookup"><span data-stu-id="6122c-191">The date that the subscription converts from trial to paid.</span></span> <span data-ttu-id="6122c-192">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="6122c-192">The default value is null.</span></span> |
| <span data-ttu-id="6122c-193">trialStartDate</span><span class="sxs-lookup"><span data-stu-id="6122c-193">trialStartDate</span></span> | <span data-ttu-id="6122c-194">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="6122c-194">string in UTC date time format</span></span> | <span data-ttu-id="6122c-195">A data em que o período experimental da subscrição começou.</span><span class="sxs-lookup"><span data-stu-id="6122c-195">The date that the trial period for the subscription started.</span></span> <span data-ttu-id="6122c-196">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="6122c-196">The default value is null.</span></span> |
| <span data-ttu-id="6122c-197">lastUsageDate</span><span class="sxs-lookup"><span data-stu-id="6122c-197">lastUsageDate</span></span> | <span data-ttu-id="6122c-198">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="6122c-198">string in UTC date time format</span></span> | <span data-ttu-id="6122c-199">A data em que a assinatura foi usada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="6122c-199">The date that the subscription was last used.</span></span> <span data-ttu-id="6122c-200">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="6122c-200">The default value is null.</span></span> |
| <span data-ttu-id="6122c-201">deprovisionedDate</span><span class="sxs-lookup"><span data-stu-id="6122c-201">deprovisionedDate</span></span> | <span data-ttu-id="6122c-202">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="6122c-202">string in UTC date time format</span></span> | <span data-ttu-id="6122c-203">A data em que a subscrição foi desprovisionada.</span><span class="sxs-lookup"><span data-stu-id="6122c-203">The date that the subscription was deprovisioned.</span></span> <span data-ttu-id="6122c-204">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="6122c-204">The default value is null.</span></span> |
| <span data-ttu-id="6122c-205">último Aniversário deRenewal</span><span class="sxs-lookup"><span data-stu-id="6122c-205">lastRenewalDate</span></span> | <span data-ttu-id="6122c-206">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="6122c-206">string in UTC date time format</span></span> | <span data-ttu-id="6122c-207">A data em que a subscrição foi renovada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="6122c-207">The date that the subscription was last renewed.</span></span> <span data-ttu-id="6122c-208">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="6122c-208">The default value is null.</span></span> |

### <a name="filter-fields"></a><span data-ttu-id="6122c-209">Campos de filtragem</span><span class="sxs-lookup"><span data-stu-id="6122c-209">Filter fields</span></span>

<span data-ttu-id="6122c-210">A tabela que se segue lista os campos de filtro opcionais e as suas descrições:</span><span class="sxs-lookup"><span data-stu-id="6122c-210">The following table lists optional filter fields and their descriptions:</span></span>

| <span data-ttu-id="6122c-211">Campo</span><span class="sxs-lookup"><span data-stu-id="6122c-211">Field</span></span> | <span data-ttu-id="6122c-212">Tipo</span><span class="sxs-lookup"><span data-stu-id="6122c-212">Type</span></span> |  <span data-ttu-id="6122c-213">Descrição</span><span class="sxs-lookup"><span data-stu-id="6122c-213">Description</span></span> |
|-------|------|--------------|
| <span data-ttu-id="6122c-214">top</span><span class="sxs-lookup"><span data-stu-id="6122c-214">top</span></span> | <span data-ttu-id="6122c-215">int</span><span class="sxs-lookup"><span data-stu-id="6122c-215">int</span></span> | <span data-ttu-id="6122c-216">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="6122c-216">The number of rows of data to return in the request.</span></span> <span data-ttu-id="6122c-217">Se o valor não for especificado, o valor máximo e o valor predefinido são 10000.</span><span class="sxs-lookup"><span data-stu-id="6122c-217">If the value isn't specified, the maximum value and the default value are 10000.</span></span> <span data-ttu-id="6122c-218">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="6122c-218">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |
| <span data-ttu-id="6122c-219">saltar</span><span class="sxs-lookup"><span data-stu-id="6122c-219">skip</span></span> | <span data-ttu-id="6122c-220">int</span><span class="sxs-lookup"><span data-stu-id="6122c-220">int</span></span> | <span data-ttu-id="6122c-221">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="6122c-221">The number of rows to skip in the query.</span></span> <span data-ttu-id="6122c-222">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="6122c-222">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="6122c-223">Por exemplo, top=10000 e skip=0 recupera as primeiras 10000 linhas de dados, top=10000 e skip=10000 recupera as próximas 10000 linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="6122c-223">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data.</span></span> |
| <span data-ttu-id="6122c-224">filter</span><span class="sxs-lookup"><span data-stu-id="6122c-224">filter</span></span> | <span data-ttu-id="6122c-225">string</span><span class="sxs-lookup"><span data-stu-id="6122c-225">string</span></span> | <span data-ttu-id="6122c-226">Uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="6122c-226">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="6122c-227">Cada declaração de filtro contém um nome de campo do corpo de resposta e um valor que está associado ao **`eq`** , ou para certos **`ne`** campos, o **`contains`** operador.</span><span class="sxs-lookup"><span data-stu-id="6122c-227">Each filter statement contains a field name from the response body and a value that are associated with the **`eq`**, **`ne`**, or for certain fields, the **`contains`** operator.</span></span> <span data-ttu-id="6122c-228">As declarações podem ser combinadas utilizando **`and`** ou **`or`** .</span><span class="sxs-lookup"><span data-stu-id="6122c-228">Statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="6122c-229">Os valores das cordas devem ser rodeados por citações únicas no parâmetro do filtro.</span><span class="sxs-lookup"><span data-stu-id="6122c-229">String values must be surrounded by single quotes in the filter parameter.</span></span> <span data-ttu-id="6122c-230">Consulte a secção seguinte para obter uma lista de campos que podem ser filtrados e os operadores que são apoiados nesses campos.</span><span class="sxs-lookup"><span data-stu-id="6122c-230">See the following section for a list of fields that can be filtered and the operators that are supported with those fields.</span></span> |
| <span data-ttu-id="6122c-231">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="6122c-231">aggregationLevel</span></span> | <span data-ttu-id="6122c-232">string</span><span class="sxs-lookup"><span data-stu-id="6122c-232">string</span></span> | <span data-ttu-id="6122c-233">Especifica o intervalo de tempo para a recuperação de dados agregados.</span><span class="sxs-lookup"><span data-stu-id="6122c-233">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="6122c-234">Pode ser uma das seguintes cordas: **dia,** **semana,** **ou mês.**</span><span class="sxs-lookup"><span data-stu-id="6122c-234">Can be one of the following strings: **day**, **week**, or **month**.</span></span> <span data-ttu-id="6122c-235">Se o valor não for especificado, o padrão é **dataRange**.</span><span class="sxs-lookup"><span data-stu-id="6122c-235">If the value isn't specified, the default is **dateRange**.</span></span> <span data-ttu-id="6122c-236">**Nota:** Este parâmetro só se aplica quando um campo de data é passado como parte do parâmetro groupBy.</span><span class="sxs-lookup"><span data-stu-id="6122c-236">**Note**: This parameter applies only when a date field is passed as part of the groupBy parameter.</span></span> |
| <span data-ttu-id="6122c-237">grupoBy</span><span class="sxs-lookup"><span data-stu-id="6122c-237">groupBy</span></span> | <span data-ttu-id="6122c-238">string</span><span class="sxs-lookup"><span data-stu-id="6122c-238">string</span></span> | <span data-ttu-id="6122c-239">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="6122c-239">A statement that applies data aggregation only to the specified fields.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6122c-240">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6122c-240">Request headers</span></span>

<span data-ttu-id="6122c-241">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6122c-241">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6122c-242">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="6122c-242">Request body</span></span>

<span data-ttu-id="6122c-243">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6122c-243">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6122c-244">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6122c-244">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?groupBy=subscriptionType
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="6122c-245">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6122c-245">REST response</span></span>

<span data-ttu-id="6122c-246">Se for bem sucedido, o organismo de resposta contém uma recolha de recursos de [subscrição](partner-center-analytics-resources.md#subscription-resource) agrupados pelos termos e datas especificados.</span><span class="sxs-lookup"><span data-stu-id="6122c-246">If successful, the response body contains a collection of [Subscription](partner-center-analytics-resources.md#subscription-resource) resources grouped by the specified terms and dates.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6122c-247">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6122c-247">Response success and error codes</span></span>

<span data-ttu-id="6122c-248">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6122c-248">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6122c-249">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6122c-249">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6122c-250">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6122c-250">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6122c-251">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6122c-251">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
{
  "Value": [
    {
      "subscriptionType": "Azure",
      "subscriptionCount": "63",
      "licenseCount": "0"
    },
    {
      "subscriptionType": "Dynamics",
      "subscriptionCount": "62",
      "licenseCount": "405"
    },
    {
      "subscriptionType": "EMS",
      "subscriptionCount": "39",
      "licenseCount": "193"
    },
    {
      "subscriptionType": "M365",
      "subscriptionCount": "2",
      "licenseCount": "5"
    },
    {
      "subscriptionType": "Office",
      "subscriptionCount": "906",
      "licenseCount": "7485"
    },
    {
      "subscriptionType": "UNKNOWN",
      "subscriptionCount": "104",
      "licenseCount": "439"
    },
    {
      "subscriptionType": "Windows",
      "subscriptionCount": "2",
      "licenseCount": "2"
    }
  ],
  "@nextLink": null,
  "TotalCount": 7
}
```

## <a name="see-also"></a><span data-ttu-id="6122c-252">Ver também</span><span class="sxs-lookup"><span data-stu-id="6122c-252">See also</span></span>

[<span data-ttu-id="6122c-253">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="6122c-253">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
