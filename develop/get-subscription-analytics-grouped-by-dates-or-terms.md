---
title: Obter análise de subscrição agrupada por datas ou termos
description: Como obter informações de análise de subscrição agrupadas por datas ou termos.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8192a9863d53ec8697a7341cd38c69200614bd4a
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548724"
---
# <a name="get-subscription-analytics-grouped-by-dates-or-terms"></a><span data-ttu-id="71d43-103">Obter análise de subscrição agrupada por datas ou termos</span><span class="sxs-lookup"><span data-stu-id="71d43-103">Get subscription analytics grouped by dates or terms</span></span>

<span data-ttu-id="71d43-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="71d43-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="71d43-105">Como obter informações de análise de subscrição para os seus clientes agrupados por datas ou termos.</span><span class="sxs-lookup"><span data-stu-id="71d43-105">How to get subscription analytics information for your customers grouped by dates or terms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="71d43-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="71d43-106">Prerequisites</span></span>

- <span data-ttu-id="71d43-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="71d43-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="71d43-108">Este cenário suporta a autenticação apenas com credenciais do Utilizador.</span><span class="sxs-lookup"><span data-stu-id="71d43-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="71d43-109">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="71d43-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="71d43-110">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="71d43-110">Request syntax</span></span>

| <span data-ttu-id="71d43-111">Método</span><span class="sxs-lookup"><span data-stu-id="71d43-111">Method</span></span> | <span data-ttu-id="71d43-112">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="71d43-112">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="71d43-113">**Obter**</span><span class="sxs-lookup"><span data-stu-id="71d43-113">**GET**</span></span> | <span data-ttu-id="71d43-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?groupby={groupby_queries}</span><span class="sxs-lookup"><span data-stu-id="71d43-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?groupby={groupby_queries}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="71d43-115">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="71d43-115">URI parameters</span></span>

<span data-ttu-id="71d43-116">Utilize os seguintes parâmetros de caminho necessários para identificar a sua organização e para agrupar os resultados.</span><span class="sxs-lookup"><span data-stu-id="71d43-116">Use the following required path parameters to identify your organization and to group the results.</span></span>

| <span data-ttu-id="71d43-117">Nome</span><span class="sxs-lookup"><span data-stu-id="71d43-117">Name</span></span> | <span data-ttu-id="71d43-118">Tipo</span><span class="sxs-lookup"><span data-stu-id="71d43-118">Type</span></span> | <span data-ttu-id="71d43-119">Necessário</span><span class="sxs-lookup"><span data-stu-id="71d43-119">Required</span></span> | <span data-ttu-id="71d43-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="71d43-120">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="71d43-121">groupby_queries</span><span class="sxs-lookup"><span data-stu-id="71d43-121">groupby_queries</span></span> | <span data-ttu-id="71d43-122">pares de cordas e dataTime</span><span class="sxs-lookup"><span data-stu-id="71d43-122">pairs of strings and dateTime</span></span> | <span data-ttu-id="71d43-123">Yes</span><span class="sxs-lookup"><span data-stu-id="71d43-123">Yes</span></span> | <span data-ttu-id="71d43-124">Os termos e datas para filtrar o resultado.</span><span class="sxs-lookup"><span data-stu-id="71d43-124">The terms and dates to filter the result.</span></span> |

### <a name="groupby-syntax"></a><span data-ttu-id="71d43-125">Sintaxe GroupBy</span><span class="sxs-lookup"><span data-stu-id="71d43-125">GroupBy syntax</span></span>

<span data-ttu-id="71d43-126">O grupo por parâmetro deve ser composto como uma série de vírgulas separadas, valores de campo.</span><span class="sxs-lookup"><span data-stu-id="71d43-126">The group by parameter must be composed as a series of comma separated, field values.</span></span>

<span data-ttu-id="71d43-127">Um exemplo não codificado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="71d43-127">An unencoded example looks like this:</span></span>

```http
?groupby=termField1,dateField1,termField2
```

<span data-ttu-id="71d43-128">A tabela seguinte mostra uma lista dos campos suportados para grupo por.</span><span class="sxs-lookup"><span data-stu-id="71d43-128">The following table shows a list of the supported fields for group by.</span></span>

| <span data-ttu-id="71d43-129">Campo</span><span class="sxs-lookup"><span data-stu-id="71d43-129">Field</span></span> | <span data-ttu-id="71d43-130">Tipo</span><span class="sxs-lookup"><span data-stu-id="71d43-130">Type</span></span> | <span data-ttu-id="71d43-131">Description</span><span class="sxs-lookup"><span data-stu-id="71d43-131">Description</span></span> |
|-------|------|-------------|
| <span data-ttu-id="71d43-132">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="71d43-132">customerTenantId</span></span> | <span data-ttu-id="71d43-133">string</span><span class="sxs-lookup"><span data-stu-id="71d43-133">string</span></span> | <span data-ttu-id="71d43-134">Uma cadeia formatada pelo GUID que identifica o inquilino do cliente.</span><span class="sxs-lookup"><span data-stu-id="71d43-134">A GUID-formatted string that identifies the customer tenant.</span></span> |
| <span data-ttu-id="71d43-135">nome do cliente</span><span class="sxs-lookup"><span data-stu-id="71d43-135">customerName</span></span> | <span data-ttu-id="71d43-136">string</span><span class="sxs-lookup"><span data-stu-id="71d43-136">string</span></span> | <span data-ttu-id="71d43-137">O nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="71d43-137">The name of the customer.</span></span> |
| <span data-ttu-id="71d43-138">customerMarket</span><span class="sxs-lookup"><span data-stu-id="71d43-138">customerMarket</span></span> | <span data-ttu-id="71d43-139">string</span><span class="sxs-lookup"><span data-stu-id="71d43-139">string</span></span> | <span data-ttu-id="71d43-140">O país/região em que o cliente faz negócios.</span><span class="sxs-lookup"><span data-stu-id="71d43-140">The country/region that the customer does business in.</span></span> |
| <span data-ttu-id="71d43-141">ID</span><span class="sxs-lookup"><span data-stu-id="71d43-141">id</span></span> | <span data-ttu-id="71d43-142">string</span><span class="sxs-lookup"><span data-stu-id="71d43-142">string</span></span> | <span data-ttu-id="71d43-143">Uma cadeia formatada por GUID que identifica a subscrição.</span><span class="sxs-lookup"><span data-stu-id="71d43-143">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="71d43-144">status</span><span class="sxs-lookup"><span data-stu-id="71d43-144">status</span></span> | <span data-ttu-id="71d43-145">string</span><span class="sxs-lookup"><span data-stu-id="71d43-145">string</span></span> | <span data-ttu-id="71d43-146">O estado da subscrição.</span><span class="sxs-lookup"><span data-stu-id="71d43-146">The subscription status.</span></span> <span data-ttu-id="71d43-147">Os valores suportados são: "ATIVE", "SUSPENDED", ou "DEPROVISIONED".</span><span class="sxs-lookup"><span data-stu-id="71d43-147">Supported values are: "ACTIVE", "SUSPENDED", or "DEPROVISIONED".</span></span> |
| <span data-ttu-id="71d43-148">produtoName</span><span class="sxs-lookup"><span data-stu-id="71d43-148">productName</span></span> | <span data-ttu-id="71d43-149">string</span><span class="sxs-lookup"><span data-stu-id="71d43-149">string</span></span> | <span data-ttu-id="71d43-150">O nome do produto.</span><span class="sxs-lookup"><span data-stu-id="71d43-150">The name of the product.</span></span> |
| <span data-ttu-id="71d43-151">Tipo de subscrição</span><span class="sxs-lookup"><span data-stu-id="71d43-151">subscriptionType</span></span> | <span data-ttu-id="71d43-152">string</span><span class="sxs-lookup"><span data-stu-id="71d43-152">string</span></span> | <span data-ttu-id="71d43-153">O tipo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="71d43-153">The subscription type.</span></span> <span data-ttu-id="71d43-154">Nota: Este campo é sensível a casos.</span><span class="sxs-lookup"><span data-stu-id="71d43-154">Note: This field is case-sensitive.</span></span> <span data-ttu-id="71d43-155">Os valores suportados são: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span><span class="sxs-lookup"><span data-stu-id="71d43-155">Supported values are: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span></span> |
| <span data-ttu-id="71d43-156">autoRenewEnabled</span><span class="sxs-lookup"><span data-stu-id="71d43-156">autoRenewEnabled</span></span> | <span data-ttu-id="71d43-157">Booleano</span><span class="sxs-lookup"><span data-stu-id="71d43-157">Boolean</span></span> | <span data-ttu-id="71d43-158">Um valor que indica se a subscrição é renovada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="71d43-158">A value indicating whether the subscription is renewed automatically.</span></span> |
| <span data-ttu-id="71d43-159">partnerId</span><span class="sxs-lookup"><span data-stu-id="71d43-159">partnerId</span></span>  | <span data-ttu-id="71d43-160">string</span><span class="sxs-lookup"><span data-stu-id="71d43-160">string</span></span> | <span data-ttu-id="71d43-161">A identificação do MPN.</span><span class="sxs-lookup"><span data-stu-id="71d43-161">The MPN ID.</span></span> <span data-ttu-id="71d43-162">Para um revendedor direto, este parâmetro será o ID MPN do parceiro.</span><span class="sxs-lookup"><span data-stu-id="71d43-162">For a direct reseller, this parameter will be the MPN ID of the partner.</span></span> <span data-ttu-id="71d43-163">Para um revendedor indireto, este parâmetro será o ID MPN do revendedor indireto.</span><span class="sxs-lookup"><span data-stu-id="71d43-163">For an indirect reseller, this parameter will be the MPN ID of the indirect reseller.</span></span> |
| <span data-ttu-id="71d43-164">nome amigável</span><span class="sxs-lookup"><span data-stu-id="71d43-164">friendlyName</span></span> | <span data-ttu-id="71d43-165">string</span><span class="sxs-lookup"><span data-stu-id="71d43-165">string</span></span> | <span data-ttu-id="71d43-166">O nome da assinatura.</span><span class="sxs-lookup"><span data-stu-id="71d43-166">The name of the subscription.</span></span> |
| <span data-ttu-id="71d43-167">nome parceiro</span><span class="sxs-lookup"><span data-stu-id="71d43-167">partnerName</span></span> | <span data-ttu-id="71d43-168">string</span><span class="sxs-lookup"><span data-stu-id="71d43-168">string</span></span> | <span data-ttu-id="71d43-169">Nome do parceiro para quem a assinatura foi comprada</span><span class="sxs-lookup"><span data-stu-id="71d43-169">Name of the partner for whom the subscription was purchased</span></span> |
| <span data-ttu-id="71d43-170">provedorName</span><span class="sxs-lookup"><span data-stu-id="71d43-170">providerName</span></span> | <span data-ttu-id="71d43-171">string</span><span class="sxs-lookup"><span data-stu-id="71d43-171">string</span></span> | <span data-ttu-id="71d43-172">Quando a transação de subscrição é para o revendedor indireto, o nome do fornecedor é o fornecedor indireto que comprou a subscrição.</span><span class="sxs-lookup"><span data-stu-id="71d43-172">When subscription transaction is for the indirect reseller, provider name is the indirect provider who bought the subscription.</span></span>
| <span data-ttu-id="71d43-173">criaçãoDate</span><span class="sxs-lookup"><span data-stu-id="71d43-173">creationDate</span></span> | <span data-ttu-id="71d43-174">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="71d43-174">string in UTC date time format</span></span> | <span data-ttu-id="71d43-175">A data em que a subscrição foi criada.</span><span class="sxs-lookup"><span data-stu-id="71d43-175">The date the subscription was created.</span></span> |
| <span data-ttu-id="71d43-176">effectiveStartDate</span><span class="sxs-lookup"><span data-stu-id="71d43-176">effectiveStartDate</span></span> | <span data-ttu-id="71d43-177">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="71d43-177">string in UTC date time format</span></span> | <span data-ttu-id="71d43-178">A data em que a subscrição começa.</span><span class="sxs-lookup"><span data-stu-id="71d43-178">The date the subscription starts.</span></span> |
| <span data-ttu-id="71d43-179">compromissoEndDate</span><span class="sxs-lookup"><span data-stu-id="71d43-179">commitmentEndDate</span></span> | <span data-ttu-id="71d43-180">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="71d43-180">string in UTC date time format</span></span> | <span data-ttu-id="71d43-181">A data em que a subscrição termina.</span><span class="sxs-lookup"><span data-stu-id="71d43-181">The date the subscription ends.</span></span> |
| <span data-ttu-id="71d43-182">actualStateEndDate</span><span class="sxs-lookup"><span data-stu-id="71d43-182">currentStateEndDate</span></span> | <span data-ttu-id="71d43-183">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="71d43-183">string in UTC date time format</span></span> | <span data-ttu-id="71d43-184">A data em que o estado atual da subscrição será alterado.</span><span class="sxs-lookup"><span data-stu-id="71d43-184">The date that the current status of the subscription will change.</span></span> |
| <span data-ttu-id="71d43-185">trialToPaidConversionDate</span><span class="sxs-lookup"><span data-stu-id="71d43-185">trialToPaidConversionDate</span></span> | <span data-ttu-id="71d43-186">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="71d43-186">string in UTC date time format</span></span> | <span data-ttu-id="71d43-187">A data em que a subscrição converte do julgamento para o pagamento.</span><span class="sxs-lookup"><span data-stu-id="71d43-187">The date that the subscription converts from trial to paid.</span></span> <span data-ttu-id="71d43-188">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="71d43-188">The default value is null.</span></span> |
| <span data-ttu-id="71d43-189">trialStartDate</span><span class="sxs-lookup"><span data-stu-id="71d43-189">trialStartDate</span></span> | <span data-ttu-id="71d43-190">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="71d43-190">string in UTC date time format</span></span> | <span data-ttu-id="71d43-191">A data em que o período experimental da subscrição começou.</span><span class="sxs-lookup"><span data-stu-id="71d43-191">The date that the trial period for the subscription started.</span></span> <span data-ttu-id="71d43-192">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="71d43-192">The default value is null.</span></span> |
| <span data-ttu-id="71d43-193">lastUsageDate</span><span class="sxs-lookup"><span data-stu-id="71d43-193">lastUsageDate</span></span> | <span data-ttu-id="71d43-194">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="71d43-194">string in UTC date time format</span></span> | <span data-ttu-id="71d43-195">A data em que a assinatura foi usada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="71d43-195">The date that the subscription was last used.</span></span> <span data-ttu-id="71d43-196">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="71d43-196">The default value is null.</span></span> |
| <span data-ttu-id="71d43-197">deprovisionedDate</span><span class="sxs-lookup"><span data-stu-id="71d43-197">deprovisionedDate</span></span> | <span data-ttu-id="71d43-198">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="71d43-198">string in UTC date time format</span></span> | <span data-ttu-id="71d43-199">A data em que a subscrição foi desprovisionada.</span><span class="sxs-lookup"><span data-stu-id="71d43-199">The date that the subscription was deprovisioned.</span></span> <span data-ttu-id="71d43-200">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="71d43-200">The default value is null.</span></span> |
| <span data-ttu-id="71d43-201">último Aniversário deRenewal</span><span class="sxs-lookup"><span data-stu-id="71d43-201">lastRenewalDate</span></span> | <span data-ttu-id="71d43-202">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="71d43-202">string in UTC date time format</span></span> | <span data-ttu-id="71d43-203">A data em que a subscrição foi renovada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="71d43-203">The date that the subscription was last renewed.</span></span> <span data-ttu-id="71d43-204">O valor por defeito é nulo.</span><span class="sxs-lookup"><span data-stu-id="71d43-204">The default value is null.</span></span> |

### <a name="filter-fields"></a><span data-ttu-id="71d43-205">Campos de filtragem</span><span class="sxs-lookup"><span data-stu-id="71d43-205">Filter fields</span></span>

<span data-ttu-id="71d43-206">A tabela que se segue lista os campos de filtro opcionais e as suas descrições:</span><span class="sxs-lookup"><span data-stu-id="71d43-206">The following table lists optional filter fields and their descriptions:</span></span>

| <span data-ttu-id="71d43-207">Campo</span><span class="sxs-lookup"><span data-stu-id="71d43-207">Field</span></span> | <span data-ttu-id="71d43-208">Tipo</span><span class="sxs-lookup"><span data-stu-id="71d43-208">Type</span></span> |  <span data-ttu-id="71d43-209">Description</span><span class="sxs-lookup"><span data-stu-id="71d43-209">Description</span></span> |
|-------|------|--------------|
| <span data-ttu-id="71d43-210">top</span><span class="sxs-lookup"><span data-stu-id="71d43-210">top</span></span> | <span data-ttu-id="71d43-211">int</span><span class="sxs-lookup"><span data-stu-id="71d43-211">int</span></span> | <span data-ttu-id="71d43-212">O número de filas de dados a devolver no pedido.</span><span class="sxs-lookup"><span data-stu-id="71d43-212">The number of rows of data to return in the request.</span></span> <span data-ttu-id="71d43-213">Se o valor não for especificado, o valor máximo e o valor predefinido são 10000.</span><span class="sxs-lookup"><span data-stu-id="71d43-213">If the value isn't specified, the maximum value and the default value are 10000.</span></span> <span data-ttu-id="71d43-214">Se houver mais linhas na consulta, o corpo de resposta inclui um próximo link que pode usar para solicitar a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="71d43-214">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |
| <span data-ttu-id="71d43-215">saltar</span><span class="sxs-lookup"><span data-stu-id="71d43-215">skip</span></span> | <span data-ttu-id="71d43-216">int</span><span class="sxs-lookup"><span data-stu-id="71d43-216">int</span></span> | <span data-ttu-id="71d43-217">O número de filas para saltar na consulta.</span><span class="sxs-lookup"><span data-stu-id="71d43-217">The number of rows to skip in the query.</span></span> <span data-ttu-id="71d43-218">Utilize este parâmetro para páginar através de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="71d43-218">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="71d43-219">Por exemplo, top=10000 e skip=0 recupera as primeiras 10000 linhas de dados, top=10000 e skip=10000 recupera as próximas 10000 linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="71d43-219">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data.</span></span> |
| <span data-ttu-id="71d43-220">filter</span><span class="sxs-lookup"><span data-stu-id="71d43-220">filter</span></span> | <span data-ttu-id="71d43-221">string</span><span class="sxs-lookup"><span data-stu-id="71d43-221">string</span></span> | <span data-ttu-id="71d43-222">Uma ou mais declarações que filtram as linhas na resposta.</span><span class="sxs-lookup"><span data-stu-id="71d43-222">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="71d43-223">Cada declaração de filtro contém um nome de campo do corpo de resposta e um valor que está associado ao **`eq`** , ou para certos **`ne`** campos, o **`contains`** operador.</span><span class="sxs-lookup"><span data-stu-id="71d43-223">Each filter statement contains a field name from the response body and a value that are associated with the **`eq`**, **`ne`**, or for certain fields, the **`contains`** operator.</span></span> <span data-ttu-id="71d43-224">As declarações podem ser combinadas utilizando **`and`** ou **`or`** .</span><span class="sxs-lookup"><span data-stu-id="71d43-224">Statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="71d43-225">Os valores das cordas devem ser rodeados por citações únicas no parâmetro do filtro.</span><span class="sxs-lookup"><span data-stu-id="71d43-225">String values must be surrounded by single quotes in the filter parameter.</span></span> <span data-ttu-id="71d43-226">Consulte a secção seguinte para obter uma lista de campos que podem ser filtrados e os operadores que são apoiados nesses campos.</span><span class="sxs-lookup"><span data-stu-id="71d43-226">See the following section for a list of fields that can be filtered and the operators that are supported with those fields.</span></span> |
| <span data-ttu-id="71d43-227">agregaçãoLevel</span><span class="sxs-lookup"><span data-stu-id="71d43-227">aggregationLevel</span></span> | <span data-ttu-id="71d43-228">string</span><span class="sxs-lookup"><span data-stu-id="71d43-228">string</span></span> | <span data-ttu-id="71d43-229">Especifica o intervalo de tempo para a recuperação de dados agregados.</span><span class="sxs-lookup"><span data-stu-id="71d43-229">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="71d43-230">Pode ser uma das seguintes cordas: **dia,** **semana,** **ou mês.**</span><span class="sxs-lookup"><span data-stu-id="71d43-230">Can be one of the following strings: **day**, **week**, or **month**.</span></span> <span data-ttu-id="71d43-231">Se o valor não for especificado, o padrão é **dataRange**.</span><span class="sxs-lookup"><span data-stu-id="71d43-231">If the value isn't specified, the default is **dateRange**.</span></span> <span data-ttu-id="71d43-232">**Nota:** Este parâmetro só se aplica quando um campo de data é passado como parte do parâmetro groupBy.</span><span class="sxs-lookup"><span data-stu-id="71d43-232">**Note**: This parameter applies only when a date field is passed as part of the groupBy parameter.</span></span> |
| <span data-ttu-id="71d43-233">grupoBy</span><span class="sxs-lookup"><span data-stu-id="71d43-233">groupBy</span></span> | <span data-ttu-id="71d43-234">string</span><span class="sxs-lookup"><span data-stu-id="71d43-234">string</span></span> | <span data-ttu-id="71d43-235">Uma declaração que aplica agregação de dados apenas aos campos especificados.</span><span class="sxs-lookup"><span data-stu-id="71d43-235">A statement that applies data aggregation only to the specified fields.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="71d43-236">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="71d43-236">Request headers</span></span>

<span data-ttu-id="71d43-237">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="71d43-237">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="71d43-238">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="71d43-238">Request body</span></span>

<span data-ttu-id="71d43-239">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="71d43-239">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="71d43-240">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="71d43-240">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?groupBy=subscriptionType
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="71d43-241">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="71d43-241">REST response</span></span>

<span data-ttu-id="71d43-242">Se for bem sucedido, o organismo de resposta contém uma recolha de recursos de [subscrição](partner-center-analytics-resources.md#subscription-resource) agrupados pelos termos e datas especificados.</span><span class="sxs-lookup"><span data-stu-id="71d43-242">If successful, the response body contains a collection of [Subscription](partner-center-analytics-resources.md#subscription-resource) resources grouped by the specified terms and dates.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="71d43-243">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="71d43-243">Response success and error codes</span></span>

<span data-ttu-id="71d43-244">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="71d43-244">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="71d43-245">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="71d43-245">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="71d43-246">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="71d43-246">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="71d43-247">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="71d43-247">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="71d43-248">Ver também</span><span class="sxs-lookup"><span data-stu-id="71d43-248">See also</span></span>

[<span data-ttu-id="71d43-249">Análise do Centro de Parceiros – Recursos</span><span class="sxs-lookup"><span data-stu-id="71d43-249">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
