---
title: Obter os registos de utilização de um cliente do Azure
description: Pode utilizar a API de utilização Azure para obter os registos de utilização da subscrição Azure de um cliente por um período de tempo especificado.
ms.date: 04/19/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 23c8d18462081c6d6c95c1d969f269cbb3f8754b
ms.sourcegitcommit: abefe11421edc421491f14b257b2408b4f29b669
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/20/2021
ms.locfileid: "107745597"
---
# <a name="get-a-customers-utilization-records-for-azure"></a><span data-ttu-id="fcc33-103">Obter os registos de utilização de um cliente do Azure</span><span class="sxs-lookup"><span data-stu-id="fcc33-103">Get a customer's utilization records for Azure</span></span>

<span data-ttu-id="fcc33-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="fcc33-104">**Applies to:**</span></span>

- <span data-ttu-id="fcc33-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="fcc33-105">Partner Center</span></span>
- <span data-ttu-id="fcc33-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="fcc33-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="fcc33-107">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fcc33-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fcc33-108">Pode obter os registos de utilização da subscrição Azure de um cliente por um período de tempo especificado utilizando a API de utilização Azure.</span><span class="sxs-lookup"><span data-stu-id="fcc33-108">You can get the utilization records of a customer's Azure subscription for a specified time period using the Azure utilization API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fcc33-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fcc33-109">Prerequisites</span></span>

- <span data-ttu-id="fcc33-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fcc33-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fcc33-111">Este cenário suporta a autenticação com aplicações autónomas e credenciais app+user.</span><span class="sxs-lookup"><span data-stu-id="fcc33-111">This scenario supports authentication with both standalone app and App+User credentials.</span></span>

- <span data-ttu-id="fcc33-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fcc33-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="fcc33-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="fcc33-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="fcc33-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="fcc33-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="fcc33-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="fcc33-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="fcc33-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="fcc33-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="fcc33-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fcc33-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="fcc33-118">Um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="fcc33-118">A subscription identifier.</span></span>

<span data-ttu-id="fcc33-119">Esta API devolve o consumo diário e de hora a hora por um período de tempo arbitrário.</span><span class="sxs-lookup"><span data-stu-id="fcc33-119">This API returns daily and hourly unrated consumption for an arbitrary time span.</span></span> <span data-ttu-id="fcc33-120">No entanto, *esta API não é apoiada para planos Azure.*</span><span class="sxs-lookup"><span data-stu-id="fcc33-120">However, *this API isn't supported for Azure plans*.</span></span> <span data-ttu-id="fcc33-121">Se tiver um plano Azure, consulte os artigos [Obtenha itens de linha de consumo não faturados](get-invoice-unbilled-consumption-lineitems.md) e [obtenha itens de linha de consumo faturados.](get-invoice-billed-consumption-lineitems.md)</span><span class="sxs-lookup"><span data-stu-id="fcc33-121">If you have an Azure plan, see the articles [Get invoice un-billed consumption line items](get-invoice-unbilled-consumption-lineitems.md) and [Get invoice billed consumption line items](get-invoice-billed-consumption-lineitems.md) instead.</span></span> <span data-ttu-id="fcc33-122">Estes artigos descrevem como obter o consumo avaliado a um nível diário por metro por recurso.</span><span class="sxs-lookup"><span data-stu-id="fcc33-122">These articles describe how to get rated consumption at a daily level per meter per resource.</span></span> <span data-ttu-id="fcc33-123">Este consumo de taxa é equivalente aos dados diários de cereais fornecidos pela API de utilização do Azure.</span><span class="sxs-lookup"><span data-stu-id="fcc33-123">This rate consumption is equivalent to the daily grain data provided by the Azure utilization API.</span></span> <span data-ttu-id="fcc33-124">Terá de usar o identificador de fatura para recuperar dados de utilização faturados.</span><span class="sxs-lookup"><span data-stu-id="fcc33-124">You'll need to use the invoice identifier to retrieve billed usage data.</span></span> <span data-ttu-id="fcc33-125">Ou, você pode usar períodos atuais e anteriores para obter estimativas de utilização não faturadas.</span><span class="sxs-lookup"><span data-stu-id="fcc33-125">Or, you can use current and previous periods to get un-billed usage estimates.</span></span> <span data-ttu-id="fcc33-126">*Os dados de cereais de hora a hora e os filtros de gama de datas arbitrárias não são atualmente suportados para os recursos de subscrição do plano Azure.*</span><span class="sxs-lookup"><span data-stu-id="fcc33-126">*Hourly grain data and arbitrary date range filters aren't currently supported for Azure plan subscription resources*.</span></span>

## <a name="azure-utilization-api"></a><span data-ttu-id="fcc33-127">API de utilização de Azure</span><span class="sxs-lookup"><span data-stu-id="fcc33-127">Azure utilization API</span></span>

<span data-ttu-id="fcc33-128">Esta API de utilização do Azure fornece acesso aos registos de utilização por um período de tempo que representa quando a utilização foi reportada no sistema de faturação.</span><span class="sxs-lookup"><span data-stu-id="fcc33-128">This Azure utilization API provides access to utilization records for a time period that represents when the utilization was reported in the billing system.</span></span> <span data-ttu-id="fcc33-129">Fornece acesso aos mesmos dados de utilização que são usados para criar e calcular o ficheiro de reconciliação.</span><span class="sxs-lookup"><span data-stu-id="fcc33-129">It provides access to the same utilization data that is used to create and calculate the reconciliation file.</span></span> <span data-ttu-id="fcc33-130">No entanto, não tem conhecimento da lógica do ficheiro de reconciliação do sistema de faturação.</span><span class="sxs-lookup"><span data-stu-id="fcc33-130">However, it does not have knowledge of billing system reconciliation file logic.</span></span> <span data-ttu-id="fcc33-131">Não deve esperar que os resultados do resumo do ficheiro de reconciliação correspondam ao resultado obtido desta API exatamente durante o mesmo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="fcc33-131">You should not expect reconciliation file summary results to match the result retrieved from this API exactly for the same time period.</span></span>

<span data-ttu-id="fcc33-132">Por exemplo, o sistema de faturação pega nos mesmos dados de utilização e aplica regras de atraso para determinar o que é contabilizado num ficheiro de reconciliação.</span><span class="sxs-lookup"><span data-stu-id="fcc33-132">For example, the billing system takes the same utilization data and applies lateness rules to determine what is accounted for in a reconciliation file.</span></span> <span data-ttu-id="fcc33-133">Quando um período de faturação termina, todo o uso até ao final do dia em que o período de faturação termina é incluído no ficheiro de reconciliação.</span><span class="sxs-lookup"><span data-stu-id="fcc33-133">When a billing period closes, all usage until the end of the day that the billing period ends is included in the reconciliation file.</span></span> <span data-ttu-id="fcc33-134">Qualquer utilização tardia dentro do período de faturação que é reportada no prazo de 24 horas após o fim do período de faturação é contabilizada no próximo ficheiro de reconciliação.</span><span class="sxs-lookup"><span data-stu-id="fcc33-134">Any late usage within the billing period that is reported within 24 hours after the billing period ends is accounted for in the next reconciliation file.</span></span> <span data-ttu-id="fcc33-135">Para as regras de atraso de como o parceiro é faturado, consulte [obter dados de consumo para uma subscrição do Azure](/previous-versions/azure/reference/mt219001(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="fcc33-135">For the lateness rules of how the partner is billed, see [Get consumption data for an Azure subscription](/previous-versions/azure/reference/mt219001(v=azure.100)).</span></span>

<span data-ttu-id="fcc33-136">Esta API REST é paged.</span><span class="sxs-lookup"><span data-stu-id="fcc33-136">This REST API is paged.</span></span> <span data-ttu-id="fcc33-137">Se a carga útil de resposta for maior do que uma única página, deve seguir o próximo link para obter a próxima página dos registos de utilização.</span><span class="sxs-lookup"><span data-stu-id="fcc33-137">If the response payload is larger than a single page, you must follow the next link to get the next page of utilization records.</span></span>

### <a name="scenario--partner-a-has-transferred-billing-ownership-of-azure-legacy-subscription-145p-to-partner-b"></a><span data-ttu-id="fcc33-138">Cenário : O parceiro A transferiu a propriedade da faturação da Azure Legacy Subscription (145P) para o Parceiro B</span><span class="sxs-lookup"><span data-stu-id="fcc33-138">Scenario : Partner A has transferred billing ownership of Azure Legacy Subscription (145P) to Partner B</span></span>

<span data-ttu-id="fcc33-139">Se um parceiro transferir a propriedade de uma subscrição de legado Azure para outro parceiro, quando o novo parceiro chama API de Utilização para subscrição transferida, eles têm de usar o ID de subscrição de comércio (que aparece na sua conta partner Center) em vez do ID do Direito Azure.</span><span class="sxs-lookup"><span data-stu-id="fcc33-139">If a partner transfers billing ownership of an Azure legacy subscription to another partner, when new the new partner calls Utilization API for transferred subscription they have to use Commerce Subscription ID (which shows up in their Partner Center account) rather than the Azure Entitlement ID.</span></span> <span data-ttu-id="fcc33-140">O ID do Direito Azure só aparece para o Parceiro B quando são Admin em nome de (AOBO) para o portal Azure do Cliente.</span><span class="sxs-lookup"><span data-stu-id="fcc33-140">Azure Entitlement ID appears for Partner B only when they are Admin on behalf of (AOBO) to Customer's Azure portal.</span></span> 

<span data-ttu-id="fcc33-141">Para ligar com sucesso para a API de Utilização para a subscrição transferida, o novo parceiro precisa de utilizar o ID de Subscrição de Comércio.</span><span class="sxs-lookup"><span data-stu-id="fcc33-141">To successfully call the Utilization API for the transferred subscription, the new partner needs to use the Commerce Subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="fcc33-142">C\#</span><span class="sxs-lookup"><span data-stu-id="fcc33-142">C\#</span></span>

<span data-ttu-id="fcc33-143">Para obter os Registos de Utilização Azure:</span><span class="sxs-lookup"><span data-stu-id="fcc33-143">To obtain the Azure Utilization Records:</span></span>

1. <span data-ttu-id="fcc33-144">Obtenha a identificação do cliente e iD de assinatura.</span><span class="sxs-lookup"><span data-stu-id="fcc33-144">Get the customer ID and subscription ID.</span></span>

2. <span data-ttu-id="fcc33-145">Ligue para o método [**IAzureUtilizationCollection.Consulta**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) para devolver uma [**Capacidade de Utilização**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) que contenha os registos de utilização.</span><span class="sxs-lookup"><span data-stu-id="fcc33-145">Call the [**IAzureUtilizationCollection.Query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) method to return a [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) that contains the utilization records.</span></span>

3. <span data-ttu-id="fcc33-146">Obtenha um enumerador de registo de utilização Azure para percorrer as páginas de utilização.</span><span class="sxs-lookup"><span data-stu-id="fcc33-146">Obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span> <span data-ttu-id="fcc33-147">Este passo é necessário, porque a recolha de recursos é paged.</span><span class="sxs-lookup"><span data-stu-id="fcc33-147">This step is required, because the resource collection is paged.</span></span>

- <span data-ttu-id="fcc33-148">**Amostra**: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="fcc33-148">**Sample**: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="fcc33-149">**Projeto**: Partner Center SDK Samples</span><span class="sxs-lookup"><span data-stu-id="fcc33-149">**Project**: Partner Center SDK Samples</span></span>
- <span data-ttu-id="fcc33-150">**Classe**: GetAzureSubscriptionUtilization.cs</span><span class="sxs-lookup"><span data-stu-id="fcc33-150">**Class**: GetAzureSubscriptionUtilization.cs</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

IPartner partner = PartnerService.Instance.CreatePartnerOperations(credentials);

// Retrieve the utilization records for the last year in pages of 100 records.
var utilizationRecords = partner.Customers[customerId].Subscriptions[subscriptionId].Utilization.Azure.Query(
    DateTimeOffset.Now.AddYears(-1),
    DateTimeOffset.Now,
    size: 100);

// Create an Azure utilization enumerator which will aid us in traversing the utilization pages.
var utilizationRecordEnumerator = partner.Enumerators.Utilization.Azure.Create(utilizationRecords);

while (utilizationRecordEnumerator.HasValue)
{
    //
    // Insert code here to work with this page.
    //

    // Get the next page.
    utilizationRecordEnumerator.Next();
}
```

## <a name="java"></a><span data-ttu-id="fcc33-151">Java</span><span class="sxs-lookup"><span data-stu-id="fcc33-151">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="fcc33-152">Para obter o Azure Usetion Records, primeiro precisa de um identificador de clientes e de um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="fcc33-152">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="fcc33-153">Em seguida, ligue para a função **IAzureUtilizationCollection.consulta** para devolver uma **Capacidade de Utilização** que contenha os registos de utilização.</span><span class="sxs-lookup"><span data-stu-id="fcc33-153">You then call the **IAzureUtilizationCollection.query** function to return a **ResourceCollection** that contains the utilization records.</span></span> <span data-ttu-id="fcc33-154">Como a recolha de recursos está paged, deve então obter um enumerador de registo de utilização Azure para atravessar as páginas de utilização.</span><span class="sxs-lookup"><span data-stu-id="fcc33-154">Because the resource collection is paged, you must then obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String subscriptionId;

ResourceCollection<AzureUtilizationRecord> utilizationRecords = partnerOperations.getCustomers()
  .byId(customerId).getSubscriptions().byId(subscriptionId)
  .getUtilization().getAzure().query(
      new DateTime().minusYears(1),
      new DateTime(),
      AzureUtilizationGranularity.Daily,
      true,
      100);

// Create an Azure utilization enumerator which will aid us in traversing the utilization pages
IResourceCollectionEnumerator<ResourceCollection<AzureUtilizationRecord>> utilizationRecordEnumerator =
    partnerOperations.getEnumerators().getUtilization().getAzure().create(utilizationRecords);

while (utilizationRecordEnumerator.hasValue())
{
    //
    // Insert code here to work with this page.
    //

    // get the next page
    utilizationRecordEnumerator.next();
}
```

## <a name="powershell"></a><span data-ttu-id="fcc33-155">PowerShell</span><span class="sxs-lookup"><span data-stu-id="fcc33-155">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="fcc33-156">Para obter o Azure Usetion Records, primeiro precisa de um identificador de clientes e de um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="fcc33-156">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="fcc33-157">Em seguida, ligue para a [**get-partnerCustomerSubscriptionUtilization**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md).</span><span class="sxs-lookup"><span data-stu-id="fcc33-157">You then call the [**Get-PartnerCustomerSubscriptionUtilization**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md).</span></span> <span data-ttu-id="fcc33-158">Este comando devolverá todos os registos disponíveis durante o período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="fcc33-158">This command will return all records available for the specified period of time.</span></span>

```powershell
# $customerId
# $subscriptionId

Get-PartnerCustomerSubscriptionUtilization -CustomerId $customerId -SubscriptionId $subscriptionId -StartDate (Get-Date).AddDays(-2).ToUniversalTime() -Granularity Hourly -ShowDetails
```

## <a name="rest-request"></a><span data-ttu-id="fcc33-159">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="fcc33-159">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fcc33-160">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcc33-160">Request syntax</span></span>

| <span data-ttu-id="fcc33-161">Método</span><span class="sxs-lookup"><span data-stu-id="fcc33-161">Method</span></span> | <span data-ttu-id="fcc33-162">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="fcc33-162">Request URI</span></span> |
|------- | ----------- |
| <span data-ttu-id="fcc33-163">**Obter**</span><span class="sxs-lookup"><span data-stu-id="fcc33-163">**GET**</span></span> | <span data-ttu-id="fcc33-164">*{baseURL}*/v1/customers/{customer-tenant-id}/subscrições/{subscription-id}/utilizações/azure?start \_ time={start-time}&\_ fim do tempo={end time}&granularity={granularity}&mostrar \_ detalhes={True}</span><span class="sxs-lookup"><span data-stu-id="fcc33-164">*{baseURL}*/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/utilizations/azure?start\_time={start-time}&end\_time={end-time}&granularity={granularity}&show\_details={True}</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="fcc33-165">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="fcc33-165">URI parameters</span></span>

<span data-ttu-id="fcc33-166">Utilize os seguintes parâmetros de percurso e consulta para obter os registos de utilização.</span><span class="sxs-lookup"><span data-stu-id="fcc33-166">Use the following path and query parameters to get the utilization records.</span></span>

| <span data-ttu-id="fcc33-167">Nome</span><span class="sxs-lookup"><span data-stu-id="fcc33-167">Name</span></span> | <span data-ttu-id="fcc33-168">Tipo</span><span class="sxs-lookup"><span data-stu-id="fcc33-168">Type</span></span> | <span data-ttu-id="fcc33-169">Necessário</span><span class="sxs-lookup"><span data-stu-id="fcc33-169">Required</span></span> | <span data-ttu-id="fcc33-170">Descrição</span><span class="sxs-lookup"><span data-stu-id="fcc33-170">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="fcc33-171">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="fcc33-171">customer-tenant-id</span></span> | <span data-ttu-id="fcc33-172">string</span><span class="sxs-lookup"><span data-stu-id="fcc33-172">string</span></span> | <span data-ttu-id="fcc33-173">Yes</span><span class="sxs-lookup"><span data-stu-id="fcc33-173">Yes</span></span> | <span data-ttu-id="fcc33-174">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="fcc33-174">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="fcc33-175">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="fcc33-175">subscription-id</span></span> | <span data-ttu-id="fcc33-176">string</span><span class="sxs-lookup"><span data-stu-id="fcc33-176">string</span></span> | <span data-ttu-id="fcc33-177">Yes</span><span class="sxs-lookup"><span data-stu-id="fcc33-177">Yes</span></span> | <span data-ttu-id="fcc33-178">Uma cadeia formatada por GUID que identifica a subscrição.</span><span class="sxs-lookup"><span data-stu-id="fcc33-178">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="fcc33-179">start_time</span><span class="sxs-lookup"><span data-stu-id="fcc33-179">start_time</span></span> | <span data-ttu-id="fcc33-180">cadeia no formato de compensação de data-hora UTC</span><span class="sxs-lookup"><span data-stu-id="fcc33-180">string in UTC date-time offset format</span></span> | <span data-ttu-id="fcc33-181">Yes</span><span class="sxs-lookup"><span data-stu-id="fcc33-181">Yes</span></span> | <span data-ttu-id="fcc33-182">O início do intervalo de tempo que representa quando a utilização foi reportada no sistema de faturação.</span><span class="sxs-lookup"><span data-stu-id="fcc33-182">The start of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="fcc33-183">end_time</span><span class="sxs-lookup"><span data-stu-id="fcc33-183">end_time</span></span> | <span data-ttu-id="fcc33-184">cadeia no formato de compensação de data-hora UTC</span><span class="sxs-lookup"><span data-stu-id="fcc33-184">string in UTC date-time offset format</span></span> | <span data-ttu-id="fcc33-185">Yes</span><span class="sxs-lookup"><span data-stu-id="fcc33-185">Yes</span></span> | <span data-ttu-id="fcc33-186">O fim do intervalo de tempo que representa quando a utilização foi reportada no sistema de faturação.</span><span class="sxs-lookup"><span data-stu-id="fcc33-186">The end of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="fcc33-187">granularidade</span><span class="sxs-lookup"><span data-stu-id="fcc33-187">granularity</span></span> | <span data-ttu-id="fcc33-188">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="fcc33-188">string</span></span> | <span data-ttu-id="fcc33-189">No</span><span class="sxs-lookup"><span data-stu-id="fcc33-189">No</span></span> | <span data-ttu-id="fcc33-190">Define a granularidade das agregações de utilização.</span><span class="sxs-lookup"><span data-stu-id="fcc33-190">Defines the granularity of usage aggregations.</span></span> <span data-ttu-id="fcc33-191">As opções disponíveis são: `daily` (padrão) e `hourly` .</span><span class="sxs-lookup"><span data-stu-id="fcc33-191">Available options are: `daily` (default) and `hourly`.</span></span>
| <span data-ttu-id="fcc33-192">show_details</span><span class="sxs-lookup"><span data-stu-id="fcc33-192">show_details</span></span> | <span data-ttu-id="fcc33-193">boolean</span><span class="sxs-lookup"><span data-stu-id="fcc33-193">boolean</span></span> | <span data-ttu-id="fcc33-194">No</span><span class="sxs-lookup"><span data-stu-id="fcc33-194">No</span></span> | <span data-ttu-id="fcc33-195">Especifica se deve obter os detalhes de utilização ao nível da instância.</span><span class="sxs-lookup"><span data-stu-id="fcc33-195">Specifies whether to get the instance-level usage details.</span></span> <span data-ttu-id="fcc33-196">A predefinição é `true`.</span><span class="sxs-lookup"><span data-stu-id="fcc33-196">The default is `true`.</span></span> |
| <span data-ttu-id="fcc33-197">size</span><span class="sxs-lookup"><span data-stu-id="fcc33-197">size</span></span> | <span data-ttu-id="fcc33-198">número</span><span class="sxs-lookup"><span data-stu-id="fcc33-198">number</span></span> | <span data-ttu-id="fcc33-199">No</span><span class="sxs-lookup"><span data-stu-id="fcc33-199">No</span></span> | <span data-ttu-id="fcc33-200">Especifica o número de agregações devolvidas por uma única chamada API.</span><span class="sxs-lookup"><span data-stu-id="fcc33-200">Specifies the number of aggregations returned by a single API call.</span></span> <span data-ttu-id="fcc33-201">A predefinição é 1000.</span><span class="sxs-lookup"><span data-stu-id="fcc33-201">The default is 1000.</span></span> <span data-ttu-id="fcc33-202">O máximo é 1000.</span><span class="sxs-lookup"><span data-stu-id="fcc33-202">The max is 1000.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fcc33-203">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="fcc33-203">Request headers</span></span>

<span data-ttu-id="fcc33-204">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="fcc33-204">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fcc33-205">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="fcc33-205">Request body</span></span>

<span data-ttu-id="fcc33-206">Nenhum</span><span class="sxs-lookup"><span data-stu-id="fcc33-206">None</span></span>

### <a name="request-example"></a><span data-ttu-id="fcc33-207">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="fcc33-207">Request example</span></span>

<span data-ttu-id="fcc33-208">O seguinte pedido de exemplo produz resultados semelhantes ao que o ficheiro de reconciliação mostrará para o período 7/2 - 8/1.</span><span class="sxs-lookup"><span data-stu-id="fcc33-208">The following example request produces results similar to what the reconciliation file will show for the period 7/2 - 8/1.</span></span> <span data-ttu-id="fcc33-209">Estes resultados podem não corresponder exatamente (consulte a secção [Azure utilização API](#azure-utilization-api) para obter mais detalhes).</span><span class="sxs-lookup"><span data-stu-id="fcc33-209">These results may not match exactly (see the section [Azure utilization API](#azure-utilization-api) for details).</span></span>

<span data-ttu-id="fcc33-210">Este exemplo solicita que os dados de utilização sejam comunicados no sistema de faturação entre 7/2 às 12:00 (UTC) e 8/2 às 12:00 (UTC).</span><span class="sxs-lookup"><span data-stu-id="fcc33-210">This example request returns utilization data reported in the billing system between 7/2 at 12 AM (UTC) and 8/2 at 12 AM (UTC).</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-07-02T00:00:00-08:00&end_time=2017-08-02T00:00:00-08:00 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="fcc33-211">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="fcc33-211">REST response</span></span>

<span data-ttu-id="fcc33-212">Se for bem sucedido, este método devolve uma coleção de recursos [Azure Usetion Record](azure-utilization-record-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="fcc33-212">If successful, this method returns a collection of [Azure Utilization Record](azure-utilization-record-resources.md) resources in the response body.</span></span> <span data-ttu-id="fcc33-213">Se os dados de utilização do Azure ainda não estiverem prontos num sistema dependente, este método devolve um Código de Estado HTTP 204 com um cabeçalho Retry-After.</span><span class="sxs-lookup"><span data-stu-id="fcc33-213">If the Azure utilization data isn't yet ready in a dependent system, this method returns an HTTP Status Code 204 with a Retry-After header.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fcc33-214">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="fcc33-214">Response success and error codes</span></span>

<span data-ttu-id="fcc33-215">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="fcc33-215">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fcc33-216">Utilize uma ferramenta de rastreio de rede para ler o código de estado HTTP, [o tipo de código de erro](error-codes.md)e os parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="fcc33-216">Use a network trace tool to read the HTTP status code, [error code type](error-codes.md), and additional parameters.</span></span>

### <a name="response-example"></a><span data-ttu-id="fcc33-217">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="fcc33-217">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2630
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CV: PjuGoYrw806o6A3Y.0
MS-ServerId: 030020525
Date: Fri, 04 Aug 2017 23:48:28 GMT

{
  "totalCount": 2,
  "items": [
    {
      "usageStartTime": "2017-06-07T17:00:00-07:00",
      "usageEndTime": "2017-06-08T17:00:00-07:00",
      "resource": {
        "id": "8767aeb3-6909-4db2-9927-3f51e9a9085e",
        "name": "Storage Admin",
        "category": "Storage",
        "subcategory": "Block Blob",
        "region": "Azure Stack"
      },
      "quantity": 0.217790327034891,
      "unit": "1 GB/Hr",
      "infoFields": {},
      "instanceData": {
        "resourceUri": "/subscriptions/ab7e2384-eeee-489a-a14f-1eb41ddd261d/resourcegroups/system.local/providers/Microsoft.Storage/storageaccounts/srphealthaccount",
        "location": "azurestack",
        "partNumber": "",
        "orderNumber": "",
        "additionalInfo": {
          "azureStack.MeterId": "09F8879E-87E9-4305-A572-4B7BE209F857",
          "azureStack.SubscriptionId": "dbd1aa30-e40d-4436-b465-3a8bc11df027",
          "azureStack.Location": "local",
          "azureStack.EventDateTime": "06/05/2017 06:00:00"
        }
      },
      "attributes": {
        "objectType": "AzureUtilizationRecord"
      }
    },
    {
      "usageStartTime": "2017-06-07T17:00:00-07:00",
      "usageEndTime": "2017-06-08T17:00:00-07:00",
      "resource": {
        "id": "8767aeb3-6909-4db2-9927-3f51e9a9085e",
        "name": "Storage Admin",
        "category": "Storage",
        "subcategory": "Block Blob",
        "region": "Azure Stack"
      },
      "quantity": 0.217790327034891,
      "unit": "1 GB/Hr",
      "infoFields": {},
      "instanceData": {
        "resourceUri": "/subscriptions/ab7e2384-eeee-489a-a14f-1eb41ddd261d/resourcegroups/system.local/providers/Microsoft.Storage/storageaccounts/srphealthaccount",
        "location": "azurestack",
        "partNumber": "",
        "orderNumber": "",
        "additionalInfo": {
          "azureStack.MeterId": "09F8879E-87E9-4305-A572-4B7BE209F857",
          "azureStack.SubscriptionId": "dbd1aa30-e40d-4436-b465-3a8bc11df027",
          "azureStack.Location": "local",
          "azureStack.EventDateTime": "06/05/2017 06:00:00"
        },
        "attributes": {
          "objectType": "AzureUtilizationRecord"
        }
      },

      "links": {
        "self": {
          "uri": "customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-06-10T00:00:00Z&end_time=2017-07-09T00:00:00Z&granularity=Daily&show_details=True&size=1000",
          "method": "GET",
          "headers": []
        }
      },
      "attributes": {
        "objectType": "Collection"
      }
    }
  ]
}
```
