---
title: Obter os registos de utilização de um cliente do Azure
description: Pode utilizar a API de utilização Azure para obter os registos de utilização da subscrição Azure de um cliente por um período de tempo especificado.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bcdeb51b04039fd05b923150c85119385c0537e0
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769343"
---
# <a name="get-a-customers-utilization-records-for-azure"></a>Obter os registos de utilização de um cliente do Azure

**Aplica-se a:**

- Partner Center
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Pode obter os registos de utilização da subscrição Azure de um cliente por um período de tempo especificado utilizando a API de utilização Azure.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com aplicações autónomas e credenciais app+user.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Um identificador de assinatura.

Esta API devolve o consumo diário e de hora a hora por um período de tempo arbitrário. No entanto, *esta API não é apoiada para planos Azure.* Se tiver um plano Azure, consulte os artigos [Obtenha itens de linha de consumo sem faturação](get-invoice-unbilled-consumption-lineitems.md) e [obtenha itens de linha de consumo faturados.](get-invoice-billed-consumption-lineitems.md) Estes artigos descrevem como obter o consumo avaliado a um nível diário por metro por recurso. Este consumo de taxa é equivalente aos dados diários de cereais fornecidos pela API de utilização do Azure. Terá de usar o identificador de fatura para recuperar dados de utilização faturados. Ou, pode usar períodos atuais e anteriores para obter estimativas de utilização não bicos. *Os dados de cereais de hora a hora e os filtros de gama de datas arbitrárias não são atualmente suportados para os recursos de subscrição do plano Azure.*

## <a name="azure-utilization-api"></a>API de utilização de Azure

Esta API de utilização do Azure fornece acesso aos registos de utilização por um período de tempo que representa quando a utilização foi reportada no sistema de faturação. Fornece acesso aos mesmos dados de utilização que são usados para criar e calcular o ficheiro de reconciliação. No entanto, não tem conhecimento da lógica do ficheiro de reconciliação do sistema de faturação. Não deve esperar que os resultados do resumo do ficheiro de reconciliação correspondam ao resultado obtido desta API exatamente durante o mesmo período de tempo.

Por exemplo, o sistema de faturação pega nos mesmos dados de utilização e aplica regras de atraso para determinar o que é contabilizado num ficheiro de reconciliação. Quando um período de faturação termina, todo o uso até ao final do dia em que o período de faturação termina é incluído no ficheiro de reconciliação. Qualquer utilização tardia dentro do período de faturação que é reportada no prazo de 24 horas após o fim do período de faturação é contabilizada no próximo ficheiro de reconciliação. Para as regras de atraso de como o parceiro é faturado, consulte [obter dados de consumo para uma subscrição do Azure](/previous-versions/azure/reference/mt219001(v=azure.100)).

Esta API REST é paged. Se a carga útil de resposta for maior do que uma única página, deve seguir o próximo link para obter a próxima página dos registos de utilização.

## <a name="c"></a>C\#

Para obter os Registos de Utilização Azure:

1. Obtenha a identificação do cliente e iD de assinatura.

2. Ligue para o método [**IAzureUtilizationCollection.Consulta**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) para devolver uma [**Capacidade de Utilização**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) que contenha os registos de utilização.

3. Obtenha um enumerador de registo de utilização Azure para percorrer as páginas de utilização. Este passo é necessário, porque a recolha de recursos é paged.

- **Amostra**: [App de teste de consola](console-test-app.md)
- **Projeto**: Partner Center SDK Samples
- **Classe**: GetAzureSubscriptionUtilization.cs

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

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Para obter o Azure Usetion Records, primeiro precisa de um identificador de clientes e de um identificador de assinatura. Em seguida, ligue para a função **IAzureUtilizationCollection.consulta** para devolver uma **Capacidade de Utilização** que contenha os registos de utilização. Como a recolha de recursos está paged, deve então obter um enumerador de registo de utilização Azure para atravessar as páginas de utilização.

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

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Para obter o Azure Usetion Records, primeiro precisa de um identificador de clientes e de um identificador de assinatura. Em seguida, ligue para a [**get-partnerCustomerSubscriptionUtilization**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md). Este comando devolverá todos os registos disponíveis durante o período de tempo especificado.

```powershell
# $customerId
# $subscriptionId

Get-PartnerCustomerSubscriptionUtilization -CustomerId $customerId -SubscriptionId $subscriptionId -StartDate (Get-Date).AddDays(-2).ToUniversalTime() -Granularity Hourly -ShowDetails
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método | URI do pedido |
|------- | ----------- |
| **Obter** | *{baseURL}*/v1/customers/{customer-tenant-id}/subscrições/{subscription-id}/utilizações/azure?start \_ time={start-time}&\_ fim do tempo={end time}&granularity={granularity}&mostrar \_ detalhes={True} |

#### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros de percurso e consulta para obter os registos de utilização.

| Nome | Tipo | Necessário | Descrição |
| ---- | ---- | -------- | ----------- |
| cliente-inquilino-id | string | Sim | Uma cadeia formatada pelo GUID que identifica o cliente. |
| id de subscrição | string | Sim | Uma cadeia formatada por GUID que identifica a subscrição. |
| start_time | cadeia no formato de compensação de data-hora UTC | Sim | O início do intervalo de tempo que representa quando a utilização foi reportada no sistema de faturação. |
| end_time | cadeia no formato de compensação de data-hora UTC | Sim | O fim do intervalo de tempo que representa quando a utilização foi reportada no sistema de faturação. |
| granularidade | cadeia (de carateres) | No | Define a granularidade das agregações de utilização. As opções disponíveis são: `daily` (padrão) e `hourly` .
| show_details | boolean | Não | Especifica se deve obter os detalhes de utilização ao nível da instância. A predefinição é `true`. |
| size | número | Não | Especifica o número de agregações devolvidas por uma única chamada API. A predefinição é 1000. O máximo é 1000. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum

### <a name="request-example"></a>Exemplo de pedido

O seguinte pedido de exemplo produz resultados semelhantes ao que o ficheiro de reconciliação mostrará para o período 7/2 - 8/1. Estes resultados podem não corresponder exatamente (consulte a secção [Azure utilização API](#azure-utilization-api) para obter mais detalhes).

Este exemplo solicita que os dados de utilização sejam comunicados no sistema de faturação entre 7/2 às 12:00 (UTC) e 8/2 às 12:00 (UTC).

```http
GET https://api.partnercenter.microsoft.com/v1/customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-07-02T00:00:00-08:00&end_time=2017-08-02T00:00:00-08:00 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma coleção de recursos [Azure Usetion Record](azure-utilization-record-resources.md) no organismo de resposta. Se os dados de utilização do Azure ainda não estiverem prontos num sistema dependente, este método devolve um Código de Estado HTTP 204 com um cabeçalho Retry-After.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler o código de estado HTTP, [o tipo de código de erro](error-codes.md)e os parâmetros adicionais.

### <a name="response-example"></a>Exemplo de resposta

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
