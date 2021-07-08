---
title: Obter um registo da atividade do Centro de Parceiros
description: Como recuperar um registo de operações, como realizado por um utilizador ou aplicação parceira, durante um período de tempo.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: aec933d4b681d99080619505792bde56bdd25580
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873976"
---
# <a name="get-a-record-of-partner-center-activity"></a><span data-ttu-id="dd0c8-103">Obter um registo da atividade do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="dd0c8-103">Get a record of Partner Center activity</span></span>

<span data-ttu-id="dd0c8-104">**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="dd0c8-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="dd0c8-105">Este artigo descreve como recuperar um registo de operações que foi realizado por um utilizador ou aplicação de um parceiro durante um período de tempo.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-105">This article describes how to retrieve a record of operations that was performed by a partner user or application over a period of time.</span></span>

<span data-ttu-id="dd0c8-106">Utilize esta API para recuperar os registos de auditoria dos 30 dias anteriores a partir da data atual, ou para um intervalo de datas especificado por incluir a data de início e/ou a data final.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-106">Use this API to retrieve audit records for the previous 30 days from the current date, or for a date range specified by including the start date and/or the end date.</span></span> <span data-ttu-id="dd0c8-107">Note-se, no entanto, que por razões de desempenho a disponibilidade de dados de registo de atividade está limitada aos 90 dias anteriores.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-107">Note, however, that for performance reasons activity log data availability is limited to the previous 90 days.</span></span> <span data-ttu-id="dd0c8-108">Os pedidos com uma data de início superior a 90 dias antes da data atual receberão uma exceção de mau pedido (código de erro: 400) e uma mensagem apropriada.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-108">Requests with a start date greater than 90 days prior to the current date will receive a bad request exception (error code: 400) and an appropriate message.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd0c8-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dd0c8-109">Prerequisites</span></span>

- <span data-ttu-id="dd0c8-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="dd0c8-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="dd0c8-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="dd0c8-112">C\#</span><span class="sxs-lookup"><span data-stu-id="dd0c8-112">C\#</span></span>

<span data-ttu-id="dd0c8-113">Para obter um registo das operações do Partner Center, primeiro estabeleça o intervalo de datas para os registos que pretende recuperar.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-113">To retrieve a record of Partner Center operations, first establish the date range for the records you want to retrieve.</span></span> <span data-ttu-id="dd0c8-114">O exemplo de código a seguir utiliza apenas uma data de início, mas também pode incluir uma data de fim.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-114">The following code example only uses a start date, but you can also include an end date.</span></span> <span data-ttu-id="dd0c8-115">Para mais informações, consulte o método [**De consulta.**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query)</span><span class="sxs-lookup"><span data-stu-id="dd0c8-115">For more information, see the [**Query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) method.</span></span> <span data-ttu-id="dd0c8-116">Em seguida, crie as variáveis necessárias para o tipo de filtro que pretende aplicar e atribua os valores apropriados.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-116">Next, create the variables you need for the type of filter you want to apply, and assign the appropriate values.</span></span> <span data-ttu-id="dd0c8-117">Por exemplo, para filtrar por sub-cordas de nome da empresa, crie uma variável para segurar o subluto.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-117">For example, to filter by company name substring, create a variable to hold the substring.</span></span> <span data-ttu-id="dd0c8-118">Para filtrar por ID do cliente, crie uma variável para segurar o ID.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-118">To filter by customer ID, create a variable to hold the ID.</span></span>

<span data-ttu-id="dd0c8-119">No exemplo seguinte, o código de amostra é fornecido para filtrar por um sub-modelo de nome da empresa, ID do cliente ou tipo de recurso.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-119">In the following example, sample code is provided to filter by a company name substring, customer ID, or resource type.</span></span> <span data-ttu-id="dd0c8-120">Escolha um e comente os outros.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-120">Choose one and comment out the others.</span></span> <span data-ttu-id="dd0c8-121">Em cada caso, primeiro instantaneamente um objeto [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) utilizando o seu [**construtor**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter.-ctor) padrão para criar o filtro.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-121">In each case, you first instantiate a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object using its default [**constructor**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter.-ctor) to create the filter.</span></span> <span data-ttu-id="dd0c8-122">Terá de passar uma corda que contenha o campo para procurar, e o operador apropriado para aplicar, como mostrado.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-122">You'll need to pass a string that contains the field to search, and the appropriate operator to apply, as shown.</span></span> <span data-ttu-id="dd0c8-123">Também deve fornecer a corda para filtrar.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-123">You also must provide the string to filter by.</span></span>

<span data-ttu-id="dd0c8-124">Em seguida, utilize a propriedade [**AuditRecords**](/dotnet/api/microsoft.store.partnercenter.ipartner.auditrecords) para obter uma interface para auditar operações de registo, e ligue para o método [**Consulta**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) ou [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.queryasync) para executar o filtro e obter a recolha de [**AuditRecord's**](/dotnet/api/microsoft.store.partnercenter.models.auditing.auditrecord) que representam a primeira página do resultado.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-124">Next, use the [**AuditRecords**](/dotnet/api/microsoft.store.partnercenter.ipartner.auditrecords) property to get an interface to audit record operations, and call the [**Query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.queryasync) method to execute the filter and get the collection of [**AuditRecord's**](/dotnet/api/microsoft.store.partnercenter.models.auditing.auditrecord) that represent the first page of the result.</span></span> <span data-ttu-id="dd0c8-125">Passe o método a data de início, uma data de fim opcional não utilizada no exemplo aqui, e um objeto [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) que representa uma consulta sobre uma entidade.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-125">Pass the method the start date, an optional end date not used in the example here, and an [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object that represents a query on an entity.</span></span> <span data-ttu-id="dd0c8-126">O objeto IQuery é criado passando o filtro criado acima para o método [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) [**da QueriaFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)</span><span class="sxs-lookup"><span data-stu-id="dd0c8-126">The IQuery object is created by passing the filter created above to the [**QueryFactory's**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method.</span></span>

<span data-ttu-id="dd0c8-127">Assim que tiver a página inicial dos itens, utilize os [**Enumeradores.AuditRecords.Crie**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) método para criar um enumerador que possa utilizar para iterar através das páginas restantes.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-127">Once you have the initial page of items, use the [**Enumerators.AuditRecords.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) method to create an enumerator that you can use to iterate through the remaining pages.</span></span>

```csharp
// IAggregatePartner partnerOperations;

var startDate = new DateTime(DateTime.Now.Year, DateTime.Now.Month, 01);

// First perform the query, then get the enumerator. Choose one of the following and comment out the other two.

// To retrieve audit records by company name substring (for example "bri" matches "Fabrikam, Inc.").
var searchSubstring="bri";
var filter = new SimpleFieldFilter(AuditRecordSearchField.CompanyName.ToString(), FieldFilterOperation.Substring, searchSubstring);
var auditRecordsPage = partnerOperations.AuditRecords.Query(startDate.Date, query: QueryFactory.Instance.BuildSimpleQuery(filter));

// To retrieve audit records by customer ID.
var customerId="0c39d6d5-c70d-4c55-bc02-f620844f3fd1";
var filter = new SimpleFieldFilter(AuditRecordSearchField.CustomerId.ToString(), FieldFilterOperation.Equals, customerId);
var auditRecordsPage = partnerOperations.AuditRecords.Query(startDate.Date, query: QueryFactory.Instance.BuildSimpleQuery(filter));

// To retrieve audit records by resource type.
int resourceTypeInt = 3; // Subscription Resource.
string searchField = Enum.GetName(typeof(ResourceType), resourceTypeInt);
var filter = new SimpleFieldFilter(AuditRecordSearchField.ResourceType.ToString(), FieldFilterOperation.Equals, searchField);
var auditRecordsPage = partnerOperations.AuditRecords.Query(startDate.Date, query: QueryFactory.Instance.BuildSimpleQuery(filter));

var auditRecordEnumerator = partnerOperations.Enumerators.AuditRecords.Create(auditRecordsPage);

int pageNumber = 1;
while (auditRecordEnumerator.HasValue)
{
    // Work with the current page.
    foreach (var c in auditRecordEnumerator.Current.Items)
    {
        // Display some info, such as operation type, operation date, and operation status.
        Console.WriteLine(string.Format("{0} {1} {2}.", c.OperationType, c.OperationDate, c.OperationStatus));
    }

    // Get the next page of audit records.
    auditRecordEnumerator.Next();
}
```

<span data-ttu-id="dd0c8-128">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="dd0c8-128">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="dd0c8-129">**Project**: Pasta de **amostras** do Centro Parceiro SDK : Auditoria</span><span class="sxs-lookup"><span data-stu-id="dd0c8-129">**Project**: Partner Center SDK Samples **Folder**: Auditing</span></span>

## <a name="rest-request"></a><span data-ttu-id="dd0c8-130">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="dd0c8-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="dd0c8-131">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd0c8-131">Request syntax</span></span>

| <span data-ttu-id="dd0c8-132">Método</span><span class="sxs-lookup"><span data-stu-id="dd0c8-132">Method</span></span>  | <span data-ttu-id="dd0c8-133">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="dd0c8-133">Request URI</span></span>                                                                                                                                                                                    |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="dd0c8-134">**Obter**</span><span class="sxs-lookup"><span data-stu-id="dd0c8-134">**GET**</span></span> | <span data-ttu-id="dd0c8-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="dd0c8-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate} HTTP/1.1</span></span>                                                                                                     |
| <span data-ttu-id="dd0c8-136">**Obter**</span><span class="sxs-lookup"><span data-stu-id="dd0c8-136">**GET**</span></span> | <span data-ttu-id="dd0c8-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="dd0c8-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate} HTTP/1.1</span></span>                                                                                   |
| <span data-ttu-id="dd0c8-138">**Obter**</span><span class="sxs-lookup"><span data-stu-id="dd0c8-138">**GET**</span></span> | <span data-ttu-id="dd0c8-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filtro={"Field":"CompanyName","Value":"{searchSubstring}","Operador":"substring"} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="dd0c8-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CompanyName","Value":"{searchSubstring}","Operator":"substring"} HTTP/1.1</span></span> |
| <span data-ttu-id="dd0c8-140">**Obter**</span><span class="sxs-lookup"><span data-stu-id="dd0c8-140">**GET**</span></span> | <span data-ttu-id="dd0c8-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filtro={"Field":"CustomerId","Value":"{customerId}","Operador":"igual"} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="dd0c8-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CustomerId","Value":"{customerId}","Operator":"equals"} HTTP/1.1</span></span>          |
| <span data-ttu-id="dd0c8-142">**Obter**</span><span class="sxs-lookup"><span data-stu-id="dd0c8-142">**GET**</span></span> | <span data-ttu-id="dd0c8-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filtro={"Field":"ResourceType","Value":"{resourceType}","Operador":"igual"} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="dd0c8-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"ResourceType","Value":"{resourceType}","Operator":"equals"} HTTP/1.1</span></span>      |

### <a name="uri-parameter"></a><span data-ttu-id="dd0c8-144">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="dd0c8-144">URI parameter</span></span>

<span data-ttu-id="dd0c8-145">Utilize os seguintes parâmetros de consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-145">Use the following query parameters when creating the request.</span></span>

| <span data-ttu-id="dd0c8-146">Nome</span><span class="sxs-lookup"><span data-stu-id="dd0c8-146">Name</span></span>      | <span data-ttu-id="dd0c8-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="dd0c8-147">Type</span></span>   | <span data-ttu-id="dd0c8-148">Necessário</span><span class="sxs-lookup"><span data-stu-id="dd0c8-148">Required</span></span> | <span data-ttu-id="dd0c8-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd0c8-149">Description</span></span>                                                                                                                                                                                                                |
|-----------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="dd0c8-150">startDate</span><span class="sxs-lookup"><span data-stu-id="dd0c8-150">startDate</span></span> | <span data-ttu-id="dd0c8-151">data</span><span class="sxs-lookup"><span data-stu-id="dd0c8-151">date</span></span>   | <span data-ttu-id="dd0c8-152">No</span><span class="sxs-lookup"><span data-stu-id="dd0c8-152">No</span></span>       | <span data-ttu-id="dd0c8-153">A data de início no formato yyy-mm-dd.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-153">The start date in yyyy-mm-dd format.</span></span> <span data-ttu-id="dd0c8-154">Se nenhuma for fornecida, o resultado definido será de incumprimento de 30 dias antes da data do pedido.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-154">If none is provided, the result set will default to 30 days prior to the request date.</span></span> <span data-ttu-id="dd0c8-155">Este parâmetro é opcional quando um filtro é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-155">This parameter is optional when a filter is supplied.</span></span>                                          |
| <span data-ttu-id="dd0c8-156">endDate</span><span class="sxs-lookup"><span data-stu-id="dd0c8-156">endDate</span></span>   | <span data-ttu-id="dd0c8-157">data</span><span class="sxs-lookup"><span data-stu-id="dd0c8-157">date</span></span>   | <span data-ttu-id="dd0c8-158">No</span><span class="sxs-lookup"><span data-stu-id="dd0c8-158">No</span></span>       | <span data-ttu-id="dd0c8-159">A data final em formato yyy-mm-dd.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-159">The end date in yyyy-mm-dd format.</span></span> <span data-ttu-id="dd0c8-160">Este parâmetro é opcional quando um filtro é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-160">This parameter is optional when a filter is supplied.</span></span> <span data-ttu-id="dd0c8-161">Quando a data de fim é omitida ou definida para nula, o pedido devolve a janela max ou utiliza hoje como data de fim, o que for menor.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-161">When the end date is omitted or set to null, the request returns the max window or uses today as the end date, whichever is less.</span></span> |
| <span data-ttu-id="dd0c8-162">filter</span><span class="sxs-lookup"><span data-stu-id="dd0c8-162">filter</span></span>    | <span data-ttu-id="dd0c8-163">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="dd0c8-163">string</span></span> | <span data-ttu-id="dd0c8-164">No</span><span class="sxs-lookup"><span data-stu-id="dd0c8-164">No</span></span>       | <span data-ttu-id="dd0c8-165">O filtro a aplicar.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-165">The filter to apply.</span></span> <span data-ttu-id="dd0c8-166">Este parâmetro deve ser uma corda codificada.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-166">This parameter must be an encoded string.</span></span> <span data-ttu-id="dd0c8-167">Este parâmetro é opcional quando a data de início ou a data de fim são fornecidas.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-167">This parameter is optional when the start date or end date are supplied.</span></span>                                                                                              |

### <a name="filter-syntax"></a><span data-ttu-id="dd0c8-168">Sintaxe de filtro</span><span class="sxs-lookup"><span data-stu-id="dd0c8-168">Filter syntax</span></span>
<span data-ttu-id="dd0c8-169">Deve compor o parâmetro do filtro como uma série de pares separados de vírgula.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-169">You must compose the filter parameter as a series of comma separated, key-value pairs.</span></span> <span data-ttu-id="dd0c8-170">Cada chave e valor devem ser citados individualmente e separados por um cólon.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-170">Each key and value must be individually quoted and separated by a colon.</span></span> <span data-ttu-id="dd0c8-171">Todo o filtro deve ser codificado.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-171">The entire filter must be encoded.</span></span>

<span data-ttu-id="dd0c8-172">Um exemplo não codificado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dd0c8-172">An unencoded example looks like this:</span></span>

```
?filter{"Field":"CompanyName","Value":"bri","Operator":"substring"}
```

<span data-ttu-id="dd0c8-173">A tabela a seguir descreve os pares de valor-chave necessários:</span><span class="sxs-lookup"><span data-stu-id="dd0c8-173">The following table describes the required key-value pairs:</span></span>

| <span data-ttu-id="dd0c8-174">Chave</span><span class="sxs-lookup"><span data-stu-id="dd0c8-174">Key</span></span>                 | <span data-ttu-id="dd0c8-175">Valor</span><span class="sxs-lookup"><span data-stu-id="dd0c8-175">Value</span></span>                             |
|:--------------------|:----------------------------------|
| <span data-ttu-id="dd0c8-176">Campo</span><span class="sxs-lookup"><span data-stu-id="dd0c8-176">Field</span></span>               | <span data-ttu-id="dd0c8-177">O campo para filtrar.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-177">The field to filter.</span></span> <span data-ttu-id="dd0c8-178">Os valores suportados podem ser encontrados na [sintaxe request](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span><span class="sxs-lookup"><span data-stu-id="dd0c8-178">The supported values can be found in [Request syntax](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span></span>                                         |
| <span data-ttu-id="dd0c8-179">Valor</span><span class="sxs-lookup"><span data-stu-id="dd0c8-179">Value</span></span>               | <span data-ttu-id="dd0c8-180">O valor a filtrar.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-180">The value to filter by.</span></span> <span data-ttu-id="dd0c8-181">O caso do valor é ignorado.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-181">The case of the value is ignored.</span></span> <span data-ttu-id="dd0c8-182">Os seguintes parâmetros de valor são suportados como mostrado na [sintaxe de pedido:](get-a-record-of-partner-center-activity-by-user.md#rest-request)</span><span class="sxs-lookup"><span data-stu-id="dd0c8-182">The following value parameters are supported as shown in [Request syntax](get-a-record-of-partner-center-activity-by-user.md#rest-request):</span></span><br/><br/>                                                                <span data-ttu-id="dd0c8-183">*searchSubstring* - Substitua-se pelo nome da empresa.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-183">*searchSubstring* - Replace with the name of the company.</span></span> <span data-ttu-id="dd0c8-184">Pode introduzir um sub-adupe para corresponder a parte do nome da empresa (por exemplo, `bri` `Fabrikam, Inc` corresponderá).</span><span class="sxs-lookup"><span data-stu-id="dd0c8-184">You can enter a substring to match part of the company name (for example, `bri` will match `Fabrikam, Inc`).</span></span><br/><span data-ttu-id="dd0c8-185">**Exemplo:**`"Value":"bri"`</span><span class="sxs-lookup"><span data-stu-id="dd0c8-185">**Example:** `"Value":"bri"`</span></span><br/><br/>                                                                <span data-ttu-id="dd0c8-186">*customerId* - Substitua por uma cadeia formatada GUID que represente o identificador do cliente.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-186">*customerId* - Replace with a GUID formatted string that represents the customer identifier.</span></span><br/><span data-ttu-id="dd0c8-187">**Exemplo:**`"Value":"0c39d6d5-c70d-4c55-bc02-f620844f3fd1"`</span><span class="sxs-lookup"><span data-stu-id="dd0c8-187">**Example:** `"Value":"0c39d6d5-c70d-4c55-bc02-f620844f3fd1"`</span></span><br/><br/>                                                                                        <span data-ttu-id="dd0c8-188">*resourceType* - Substitua-o pelo tipo de recurso para o qual recuperar registos de auditoria (por exemplo, Assinatura).</span><span class="sxs-lookup"><span data-stu-id="dd0c8-188">*resourceType* - Replace with the type of resource for which to retrieve audit records (for example, Subscription).</span></span> <span data-ttu-id="dd0c8-189">Os tipos de recursos disponíveis são definidos no [ResourceType](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype).</span><span class="sxs-lookup"><span data-stu-id="dd0c8-189">The available resource types are defined in [ResourceType](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype).</span></span><br/><span data-ttu-id="dd0c8-190">**Exemplo:**`"Value":"Subscription"`</span><span class="sxs-lookup"><span data-stu-id="dd0c8-190">**Example:** `"Value":"Subscription"`</span></span>                                 |
| <span data-ttu-id="dd0c8-191">Operador</span><span class="sxs-lookup"><span data-stu-id="dd0c8-191">Operator</span></span>          | <span data-ttu-id="dd0c8-192">O operador a candidatar-se.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-192">The operator to apply.</span></span> <span data-ttu-id="dd0c8-193">Os operadores apoiados podem ser encontrados na [sintaxe request](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span><span class="sxs-lookup"><span data-stu-id="dd0c8-193">The supported operators can be found in [Request syntax](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="dd0c8-194">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="dd0c8-194">Request headers</span></span>

- <span data-ttu-id="dd0c8-195">Para mais informações, consulte [os cabeçalhos Parter Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="dd0c8-195">For more information, see [Parter Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="dd0c8-196">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="dd0c8-196">Request body</span></span>

<span data-ttu-id="dd0c8-197">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-197">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="dd0c8-198">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="dd0c8-198">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/auditrecords?startDate=6/1/2017%2012:00:00%20AM&filter=%7B%22Field%22:%22CustomerId%22,%22Value%22:%220c39d6d5-c70d-4c55-bc02-f620844f3fd1%22,%22Operator%22:%22equals%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 127facaa-e389-41f8-8bb7-1d1af99db893
MS-CorrelationId: de9c2ccc-40dd-4186-9660-65b9b64c3d14
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="dd0c8-199">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="dd0c8-199">REST response</span></span>

<span data-ttu-id="dd0c8-200">Se for bem sucedido, este método devolve um conjunto de atividades que vão ao encontro dos filtros.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-200">If successful, this method returns a set of activities that meet the filters.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="dd0c8-201">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="dd0c8-201">Response success and error codes</span></span>

<span data-ttu-id="dd0c8-202">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-202">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="dd0c8-203">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="dd0c8-203">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="dd0c8-204">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="dd0c8-204">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="dd0c8-205">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="dd0c8-205">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2859
Content-Type: application/json; charset=utf-8
MS-CorrelationId: de9c2ccc-40dd-4186-9660-65b9b64c3d14
MS-RequestId: 127facaa-e389-41f8-8bb7-1d1af99db893
MS-CV: 4xDKynq/zE2im0wj.0
MS-ServerId: 030011719
Date: Tue, 27 Jun 2017 22:19:46 GMT

{
    "totalCount": 2,
    "items": [{
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "0c39d6d5-c70d-4c55-bc02-f620844f3fd1",
            "customerName": "Relecloud",
            "userPrincipalName": "admin@domain.onmicrosoft.com",
            "resourceType": "order",
            "resourceNewValue": "{\"Id\":\"d51a052e-043c-4a2a-aa37-2bb938cef6c1\",\"ReferenceCustomerId\":\"0c39d6d5-c70d-4c55-bc02-f620844f3fd1\",\"BillingCycle\":\"none\",\"LineItems\":[{\"LineItemNumber\":0,\"OfferId\":\"C0BD2E08-11AC-4836-BDC7-3712E744922F\",\"SubscriptionId\":\"488745B5-2086-4912-802C-6ABB9F7C3638\",\"ParentSubscriptionId\":null,\"FriendlyName\":\"Office 365 Business Premium Trial\",\"Quantity\":25,\"PartnerIdOnRecord\":null,\"Links\":{\"Subscription\":{\"Uri\":\"/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638\",\"Method\":\"GET\",\"Headers\":[]}}}],\"CreationDate\":\"2017-06-15T15:56:04.077-07:00\",\"Links\":{\"Self\":{\"Uri\":\"/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/orders/d51a052e-043c-4a2a-aa37-2bb938cef6c1\",\"Method\":\"GET\",\"Headers\":[]}},\"Attributes\":{\"Etag\":\"eyJpZCI6ImQ1MWEwNTJlLTA0M2MtNGEyYS1hYTM3LTJiYjkzOGNlZjZjMSIsInZlcnNpb24iOjF9\",\"ObjectType\":\"Order\"}}",
            "operationType": "create_order",
            "operationDate": "2017-06-15T22:56:05.0589308Z",
            "operationStatus": "succeeded",
            "customizedData": [{
                    "key": "OrderId",
                    "value": "d51a052e-043c-4a2a-aa37-2bb938cef6c1"
                }, {
                    "key": "BillingCycle",
                    "value": "None"
                }, {
                    "key": "OfferId-0",
                    "value": "C0BD2E08-11AC-4836-BDC7-3712E744922F"
                }, {
                    "key": "SubscriptionId-0",
                    "value": "488745B5-2086-4912-802C-6ABB9F7C3638"
                }, {
                    "key": "SubscriptionName-0",
                    "value": "Office 365 Business Premium Trial"
                }, {
                    "key": "Quantity-0",
                    "value": "25"
                }, {
                    "key": "PartnerOnRecord-0",
                    "value": null
                }
            ],
            "attributes": {
                "objectType": "AuditRecord"
            }
        }, {
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "0c39d6d5-c70d-4c55-bc02-f620844f3fd1",
            "customerName": "Relecloud",
            "userPrincipalName": "admin@domain.onmicrosoft.com",
            "applicationId": "Partner Center Native App",
            "resourceType": "license",
            "resourceNewValue": "{\"LicensesToAssign\":[{\"ExcludedPlans\":null,\"SkuId\":\"efccb6f7-5641-4e0e-bd10-b4976e1bf68e\"}],\"LicensesToRemove\":null,\"LicenseWarnings\":[],\"Attributes\":{\"ObjectType\":\"LicenseUpdate\"}}",
            "operationType": "update_customer_user_licenses",
            "operationDate": "2017-06-01T20:09:07.0450483Z",
            "operationStatus": "succeeded",
            "customizedData": [{
                    "key": "CustomerUserId",
                    "value": "482e2152-4b49-48ec-b715-823365ce3d4c"
                }, {
                    "key": "AddedLicenseSkuId",
                    "value": "efccb6f7-5641-4e0e-bd10-b4976e1bf68e"
                }
            ],
            "attributes": {
                "objectType": "AuditRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/auditrecords?startDate=2017-06-01&size=500&filter=%7B%22Field%22%3A%22CustomerId%22%2C%22Value%22%3A%220c39d6d5-c70d-4c55-bc02-f620844f3fd1%22%2C%22Operator%22%3A%22equals%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```