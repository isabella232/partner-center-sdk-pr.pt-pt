---
title: Obter os registos de utilização de um cliente do Azure
description: Pode utilizar a API de utilização Azure para obter os registos de utilização da subscrição Azure de um cliente por um período de tempo especificado.
ms.date: 04/19/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7024bc65976a9b43a62b66c529d271519181ab23
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874929"
---
# <a name="get-a-customers-utilization-records-for-azure"></a><span data-ttu-id="b2707-103">Obter os registos de utilização de um cliente do Azure</span><span class="sxs-lookup"><span data-stu-id="b2707-103">Get a customer's utilization records for Azure</span></span>

<span data-ttu-id="b2707-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b2707-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b2707-105">Pode obter os registos de utilização da subscrição Azure de um cliente por um período de tempo especificado utilizando a API de utilização Azure.</span><span class="sxs-lookup"><span data-stu-id="b2707-105">You can get the utilization records of a customer's Azure subscription for a specified time period using the Azure utilization API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2707-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b2707-106">Prerequisites</span></span>

- <span data-ttu-id="b2707-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b2707-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b2707-108">Este cenário suporta a autenticação com aplicações autónomas e credenciais app+user.</span><span class="sxs-lookup"><span data-stu-id="b2707-108">This scenario supports authentication with both standalone app and App+User credentials.</span></span>

- <span data-ttu-id="b2707-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b2707-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="b2707-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b2707-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="b2707-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="b2707-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="b2707-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="b2707-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="b2707-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="b2707-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="b2707-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b2707-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="b2707-115">Um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="b2707-115">A subscription identifier.</span></span>

<span data-ttu-id="b2707-116">Esta API devolve o consumo diário e de hora a hora por um período de tempo arbitrário.</span><span class="sxs-lookup"><span data-stu-id="b2707-116">This API returns daily and hourly unrated consumption for an arbitrary time span.</span></span> <span data-ttu-id="b2707-117">No entanto, *esta API não é apoiada para planos Azure.*</span><span class="sxs-lookup"><span data-stu-id="b2707-117">However, *this API isn't supported for Azure plans*.</span></span> <span data-ttu-id="b2707-118">Se tiver um plano Azure, consulte os artigos [Obtenha itens de linha de consumo sem faturação](get-invoice-unbilled-consumption-lineitems.md) e [obtenha itens de linha de consumo faturados.](get-invoice-billed-consumption-lineitems.md)</span><span class="sxs-lookup"><span data-stu-id="b2707-118">If you have an Azure plan, see the articles [Get invoice unbilled consumption line items](get-invoice-unbilled-consumption-lineitems.md) and [Get invoice billed consumption line items](get-invoice-billed-consumption-lineitems.md) instead.</span></span> <span data-ttu-id="b2707-119">Estes artigos descrevem como obter o consumo avaliado a um nível diário por metro por recurso.</span><span class="sxs-lookup"><span data-stu-id="b2707-119">These articles describe how to get rated consumption at a daily level per meter per resource.</span></span> <span data-ttu-id="b2707-120">Este consumo de taxa é equivalente aos dados diários de cereais fornecidos pela API de utilização do Azure.</span><span class="sxs-lookup"><span data-stu-id="b2707-120">This rate consumption is equivalent to the daily grain data provided by the Azure utilization API.</span></span> <span data-ttu-id="b2707-121">Terá de usar o identificador de fatura para recuperar dados de utilização faturados.</span><span class="sxs-lookup"><span data-stu-id="b2707-121">You'll need to use the invoice identifier to retrieve billed usage data.</span></span> <span data-ttu-id="b2707-122">Ou, pode usar períodos atuais e anteriores para obter estimativas de utilização não bicos.</span><span class="sxs-lookup"><span data-stu-id="b2707-122">Or, you can use current and previous periods to get unbilled usage estimates.</span></span> <span data-ttu-id="b2707-123">*Os dados de cereais de hora a hora e os filtros de gama de datas arbitrárias não são atualmente suportados para os recursos de subscrição do plano Azure.*</span><span class="sxs-lookup"><span data-stu-id="b2707-123">*Hourly grain data and arbitrary date range filters aren't currently supported for Azure plan subscription resources*.</span></span>

## <a name="azure-utilization-api"></a><span data-ttu-id="b2707-124">API de utilização de Azure</span><span class="sxs-lookup"><span data-stu-id="b2707-124">Azure utilization API</span></span>

<span data-ttu-id="b2707-125">Esta API de utilização do Azure fornece acesso aos registos de utilização por um período de tempo que representa quando a utilização foi reportada no sistema de faturação.</span><span class="sxs-lookup"><span data-stu-id="b2707-125">This Azure utilization API provides access to utilization records for a time period that represents when the utilization was reported in the billing system.</span></span> <span data-ttu-id="b2707-126">Fornece acesso aos mesmos dados de utilização que são usados para criar e calcular o ficheiro de reconciliação.</span><span class="sxs-lookup"><span data-stu-id="b2707-126">It provides access to the same utilization data that is used to create and calculate the reconciliation file.</span></span> <span data-ttu-id="b2707-127">No entanto, não tem conhecimento da lógica do ficheiro de reconciliação do sistema de faturação.</span><span class="sxs-lookup"><span data-stu-id="b2707-127">However, it does not have knowledge of billing system reconciliation file logic.</span></span> <span data-ttu-id="b2707-128">Não deve esperar que os resultados do resumo do ficheiro de reconciliação correspondam ao resultado obtido desta API exatamente durante o mesmo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="b2707-128">You should not expect reconciliation file summary results to match the result retrieved from this API exactly for the same time period.</span></span>

<span data-ttu-id="b2707-129">Por exemplo, o sistema de faturação pega nos mesmos dados de utilização e aplica regras de atraso para determinar o que é contabilizado num ficheiro de reconciliação.</span><span class="sxs-lookup"><span data-stu-id="b2707-129">For example, the billing system takes the same utilization data and applies lateness rules to determine what is accounted for in a reconciliation file.</span></span> <span data-ttu-id="b2707-130">Quando um período de faturação termina, todo o uso até ao final do dia em que o período de faturação termina é incluído no ficheiro de reconciliação.</span><span class="sxs-lookup"><span data-stu-id="b2707-130">When a billing period closes, all usage until the end of the day that the billing period ends is included in the reconciliation file.</span></span> <span data-ttu-id="b2707-131">Qualquer utilização tardia dentro do período de faturação que é reportada no prazo de 24 horas após o fim do período de faturação é contabilizada no próximo ficheiro de reconciliação.</span><span class="sxs-lookup"><span data-stu-id="b2707-131">Any late usage within the billing period that is reported within 24 hours after the billing period ends is accounted for in the next reconciliation file.</span></span> <span data-ttu-id="b2707-132">Para as regras de atraso de como o parceiro é faturado, consulte [obter dados de consumo para uma subscrição do Azure](/previous-versions/azure/reference/mt219001(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="b2707-132">For the lateness rules of how the partner is billed, see [Get consumption data for an Azure subscription](/previous-versions/azure/reference/mt219001(v=azure.100)).</span></span>

<span data-ttu-id="b2707-133">Esta API REST é paged.</span><span class="sxs-lookup"><span data-stu-id="b2707-133">This REST API is paged.</span></span> <span data-ttu-id="b2707-134">Se a carga útil de resposta for maior do que uma única página, deve seguir o próximo link para obter a próxima página dos registos de utilização.</span><span class="sxs-lookup"><span data-stu-id="b2707-134">If the response payload is larger than a single page, you must follow the next link to get the next page of utilization records.</span></span>

### <a name="scenario-partner-a-has-transferred-billing-ownership-of-azure-legacy-subscription-145p-to-partner-b"></a><span data-ttu-id="b2707-135">Cenário: O parceiro A transferiu a propriedade da faturação da Azure Legacy Subscription (145P) para o Parceiro B</span><span class="sxs-lookup"><span data-stu-id="b2707-135">Scenario: Partner A has transferred billing ownership of Azure Legacy Subscription (145P) to Partner B</span></span>

<span data-ttu-id="b2707-136">Se um parceiro transferir a propriedade de uma subscrição de legado Azure para outro parceiro, quando o novo parceiro chama API de Utilização para subscrição transferida, eles têm de usar o ID de subscrição de comércio (que aparece na sua conta partner Center) em vez do ID do Direito Azure.</span><span class="sxs-lookup"><span data-stu-id="b2707-136">If a partner transfers billing ownership of an Azure legacy subscription to another partner, when new the new partner calls Utilization API for transferred subscription they have to use Commerce Subscription ID (which shows up in their Partner Center account) rather than the Azure Entitlement ID.</span></span> <span data-ttu-id="b2707-137">O ID do Direito Azure só aparece para o Parceiro B quando são Admin em nome de (AOBO) para o portal Azure do Cliente.</span><span class="sxs-lookup"><span data-stu-id="b2707-137">Azure Entitlement ID appears for Partner B only when they are Admin on behalf of (AOBO) to Customer's Azure portal.</span></span> 

<span data-ttu-id="b2707-138">Para ligar com sucesso para a API de Utilização para a subscrição transferida, o novo parceiro precisa de utilizar o ID de Subscrição de Comércio.</span><span class="sxs-lookup"><span data-stu-id="b2707-138">To successfully call the Utilization API for the transferred subscription, the new partner needs to use the Commerce Subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="b2707-139">C\#</span><span class="sxs-lookup"><span data-stu-id="b2707-139">C\#</span></span>

<span data-ttu-id="b2707-140">Para obter os Registos de Utilização Azure:</span><span class="sxs-lookup"><span data-stu-id="b2707-140">To obtain the Azure Utilization Records:</span></span>

1. <span data-ttu-id="b2707-141">Obtenha a identificação do cliente e iD de assinatura.</span><span class="sxs-lookup"><span data-stu-id="b2707-141">Get the customer ID and subscription ID.</span></span>

2. <span data-ttu-id="b2707-142">Ligue para o método [**IAzureUtilizationCollection.Consulta**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) para devolver uma [**Capacidade de Utilização**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) que contenha os registos de utilização.</span><span class="sxs-lookup"><span data-stu-id="b2707-142">Call the [**IAzureUtilizationCollection.Query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) method to return a [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) that contains the utilization records.</span></span>

3. <span data-ttu-id="b2707-143">Obtenha um enumerador de registo de utilização Azure para percorrer as páginas de utilização.</span><span class="sxs-lookup"><span data-stu-id="b2707-143">Obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span> <span data-ttu-id="b2707-144">Este passo é necessário, porque a recolha de recursos é paged.</span><span class="sxs-lookup"><span data-stu-id="b2707-144">This step is required, because the resource collection is paged.</span></span>

- <span data-ttu-id="b2707-145">**Amostra**: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="b2707-145">**Sample**: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="b2707-146">**Project**: Amostras SDK do Centro Parceiro</span><span class="sxs-lookup"><span data-stu-id="b2707-146">**Project**: Partner Center SDK Samples</span></span>
- <span data-ttu-id="b2707-147">**Classe**: GetAzureSubscriptionUtilization.cs</span><span class="sxs-lookup"><span data-stu-id="b2707-147">**Class**: GetAzureSubscriptionUtilization.cs</span></span>

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

## <a name="java"></a><span data-ttu-id="b2707-148">Java</span><span class="sxs-lookup"><span data-stu-id="b2707-148">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="b2707-149">Para obter o Azure Usetion Records, primeiro precisa de um identificador de clientes e de um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="b2707-149">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="b2707-150">Em seguida, ligue para a função **IAzureUtilizationCollection.consulta** para devolver uma **Capacidade de Utilização** que contenha os registos de utilização.</span><span class="sxs-lookup"><span data-stu-id="b2707-150">You then call the **IAzureUtilizationCollection.query** function to return a **ResourceCollection** that contains the utilization records.</span></span> <span data-ttu-id="b2707-151">Como a recolha de recursos está paged, deve então obter um enumerador de registo de utilização Azure para atravessar as páginas de utilização.</span><span class="sxs-lookup"><span data-stu-id="b2707-151">Because the resource collection is paged, you must then obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span>

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

## <a name="powershell"></a><span data-ttu-id="b2707-152">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2707-152">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="b2707-153">Para obter o Azure Usetion Records, primeiro precisa de um identificador de clientes e de um identificador de assinatura.</span><span class="sxs-lookup"><span data-stu-id="b2707-153">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="b2707-154">Em seguida, ligue para a [**get-partnerCustomerSubscriptionUtilization**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md).</span><span class="sxs-lookup"><span data-stu-id="b2707-154">You then call the [**Get-PartnerCustomerSubscriptionUtilization**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md).</span></span> <span data-ttu-id="b2707-155">Este comando devolverá todos os registos disponíveis durante o período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="b2707-155">This command will return all records available for the specified period of time.</span></span>

```powershell
# $customerId
# $subscriptionId

Get-PartnerCustomerSubscriptionUtilization -CustomerId $customerId -SubscriptionId $subscriptionId -StartDate (Get-Date).AddDays(-2).ToUniversalTime() -Granularity Hourly -ShowDetails
```

## <a name="rest-request"></a><span data-ttu-id="b2707-156">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="b2707-156">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b2707-157">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2707-157">Request syntax</span></span>

| <span data-ttu-id="b2707-158">Método</span><span class="sxs-lookup"><span data-stu-id="b2707-158">Method</span></span> | <span data-ttu-id="b2707-159">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="b2707-159">Request URI</span></span> |
|------- | ----------- |
| <span data-ttu-id="b2707-160">**Obter**</span><span class="sxs-lookup"><span data-stu-id="b2707-160">**GET**</span></span> | <span data-ttu-id="b2707-161">*{baseURL}*/v1/customers/{customer-tenant-id}/subscrições/{subscription-id}/utilizações/azure?start \_ time={start-time}&\_ fim do tempo={end time}&granularity={granularity}&mostrar \_ detalhes={True}</span><span class="sxs-lookup"><span data-stu-id="b2707-161">*{baseURL}*/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/utilizations/azure?start\_time={start-time}&end\_time={end-time}&granularity={granularity}&show\_details={True}</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="b2707-162">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="b2707-162">URI parameters</span></span>

<span data-ttu-id="b2707-163">Utilize os seguintes parâmetros de percurso e consulta para obter os registos de utilização.</span><span class="sxs-lookup"><span data-stu-id="b2707-163">Use the following path and query parameters to get the utilization records.</span></span>

| <span data-ttu-id="b2707-164">Nome</span><span class="sxs-lookup"><span data-stu-id="b2707-164">Name</span></span> | <span data-ttu-id="b2707-165">Tipo</span><span class="sxs-lookup"><span data-stu-id="b2707-165">Type</span></span> | <span data-ttu-id="b2707-166">Necessário</span><span class="sxs-lookup"><span data-stu-id="b2707-166">Required</span></span> | <span data-ttu-id="b2707-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2707-167">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="b2707-168">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="b2707-168">customer-tenant-id</span></span> | <span data-ttu-id="b2707-169">string</span><span class="sxs-lookup"><span data-stu-id="b2707-169">string</span></span> | <span data-ttu-id="b2707-170">Yes</span><span class="sxs-lookup"><span data-stu-id="b2707-170">Yes</span></span> | <span data-ttu-id="b2707-171">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="b2707-171">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="b2707-172">id de subscrição</span><span class="sxs-lookup"><span data-stu-id="b2707-172">subscription-id</span></span> | <span data-ttu-id="b2707-173">string</span><span class="sxs-lookup"><span data-stu-id="b2707-173">string</span></span> | <span data-ttu-id="b2707-174">Yes</span><span class="sxs-lookup"><span data-stu-id="b2707-174">Yes</span></span> | <span data-ttu-id="b2707-175">Uma cadeia formatada por GUID que identifica a subscrição.</span><span class="sxs-lookup"><span data-stu-id="b2707-175">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="b2707-176">start_time</span><span class="sxs-lookup"><span data-stu-id="b2707-176">start_time</span></span> | <span data-ttu-id="b2707-177">cadeia no formato de compensação de data-hora UTC</span><span class="sxs-lookup"><span data-stu-id="b2707-177">string in UTC date-time offset format</span></span> | <span data-ttu-id="b2707-178">Yes</span><span class="sxs-lookup"><span data-stu-id="b2707-178">Yes</span></span> | <span data-ttu-id="b2707-179">O início do intervalo de tempo que representa quando a utilização foi reportada no sistema de faturação.</span><span class="sxs-lookup"><span data-stu-id="b2707-179">The start of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="b2707-180">end_time</span><span class="sxs-lookup"><span data-stu-id="b2707-180">end_time</span></span> | <span data-ttu-id="b2707-181">cadeia no formato de compensação de data-hora UTC</span><span class="sxs-lookup"><span data-stu-id="b2707-181">string in UTC date-time offset format</span></span> | <span data-ttu-id="b2707-182">Yes</span><span class="sxs-lookup"><span data-stu-id="b2707-182">Yes</span></span> | <span data-ttu-id="b2707-183">O fim do intervalo de tempo que representa quando a utilização foi reportada no sistema de faturação.</span><span class="sxs-lookup"><span data-stu-id="b2707-183">The end of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="b2707-184">granularidade</span><span class="sxs-lookup"><span data-stu-id="b2707-184">granularity</span></span> | <span data-ttu-id="b2707-185">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="b2707-185">string</span></span> | <span data-ttu-id="b2707-186">No</span><span class="sxs-lookup"><span data-stu-id="b2707-186">No</span></span> | <span data-ttu-id="b2707-187">Define a granularidade das agregações de utilização.</span><span class="sxs-lookup"><span data-stu-id="b2707-187">Defines the granularity of usage aggregations.</span></span> <span data-ttu-id="b2707-188">As opções disponíveis são: `daily` (padrão) e `hourly` .</span><span class="sxs-lookup"><span data-stu-id="b2707-188">Available options are: `daily` (default) and `hourly`.</span></span>
| <span data-ttu-id="b2707-189">show_details</span><span class="sxs-lookup"><span data-stu-id="b2707-189">show_details</span></span> | <span data-ttu-id="b2707-190">boolean</span><span class="sxs-lookup"><span data-stu-id="b2707-190">boolean</span></span> | <span data-ttu-id="b2707-191">No</span><span class="sxs-lookup"><span data-stu-id="b2707-191">No</span></span> | <span data-ttu-id="b2707-192">Especifica se deve obter os detalhes de utilização ao nível da instância.</span><span class="sxs-lookup"><span data-stu-id="b2707-192">Specifies whether to get the instance-level usage details.</span></span> <span data-ttu-id="b2707-193">A predefinição é `true`.</span><span class="sxs-lookup"><span data-stu-id="b2707-193">The default is `true`.</span></span> |
| <span data-ttu-id="b2707-194">size</span><span class="sxs-lookup"><span data-stu-id="b2707-194">size</span></span> | <span data-ttu-id="b2707-195">número</span><span class="sxs-lookup"><span data-stu-id="b2707-195">number</span></span> | <span data-ttu-id="b2707-196">No</span><span class="sxs-lookup"><span data-stu-id="b2707-196">No</span></span> | <span data-ttu-id="b2707-197">Especifica o número de agregações devolvidas por uma única chamada API.</span><span class="sxs-lookup"><span data-stu-id="b2707-197">Specifies the number of aggregations returned by a single API call.</span></span> <span data-ttu-id="b2707-198">A predefinição é 1000.</span><span class="sxs-lookup"><span data-stu-id="b2707-198">The default is 1000.</span></span> <span data-ttu-id="b2707-199">O máximo é 1000.</span><span class="sxs-lookup"><span data-stu-id="b2707-199">The max is 1000.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b2707-200">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="b2707-200">Request headers</span></span>

<span data-ttu-id="b2707-201">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b2707-201">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b2707-202">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="b2707-202">Request body</span></span>

<span data-ttu-id="b2707-203">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="b2707-203">None</span></span>

### <a name="request-example"></a><span data-ttu-id="b2707-204">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="b2707-204">Request example</span></span>

<span data-ttu-id="b2707-205">O seguinte pedido de exemplo produz resultados semelhantes ao que o ficheiro de reconciliação mostrará para o período 7/2 - 8/1.</span><span class="sxs-lookup"><span data-stu-id="b2707-205">The following example request produces results similar to what the reconciliation file will show for the period 7/2 - 8/1.</span></span> <span data-ttu-id="b2707-206">Estes resultados podem não corresponder exatamente (consulte a secção [Azure utilização API](#azure-utilization-api) para obter mais detalhes).</span><span class="sxs-lookup"><span data-stu-id="b2707-206">These results may not match exactly (see the section [Azure utilization API](#azure-utilization-api) for details).</span></span>

<span data-ttu-id="b2707-207">Este exemplo solicita que os dados de utilização sejam comunicados no sistema de faturação entre 7/2 às 12:00 (UTC) e 8/2 às 12:00 (UTC).</span><span class="sxs-lookup"><span data-stu-id="b2707-207">This example request returns utilization data reported in the billing system between 7/2 at 12 AM (UTC) and 8/2 at 12 AM (UTC).</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-07-02T00:00:00-08:00&end_time=2017-08-02T00:00:00-08:00 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="b2707-208">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="b2707-208">REST response</span></span>

<span data-ttu-id="b2707-209">Se for bem sucedido, este método devolve uma coleção de recursos [Azure Usetion Record](azure-utilization-record-resources.md) no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="b2707-209">If successful, this method returns a collection of [Azure Utilization Record](azure-utilization-record-resources.md) resources in the response body.</span></span> <span data-ttu-id="b2707-210">Se os dados de utilização do Azure ainda não estiverem prontos num sistema dependente, este método devolve um Código de Estado HTTP 204 com um cabeçalho Retry-After.</span><span class="sxs-lookup"><span data-stu-id="b2707-210">If the Azure utilization data isn't yet ready in a dependent system, this method returns an HTTP Status Code 204 with a Retry-After header.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b2707-211">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="b2707-211">Response success and error codes</span></span>

<span data-ttu-id="b2707-212">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="b2707-212">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b2707-213">Utilize uma ferramenta de rastreio de rede para ler o código de estado HTTP, [o tipo de código de erro](error-codes.md)e os parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="b2707-213">Use a network trace tool to read the HTTP status code, [error code type](error-codes.md), and additional parameters.</span></span>

### <a name="response-example"></a><span data-ttu-id="b2707-214">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="b2707-214">Response example</span></span>

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
