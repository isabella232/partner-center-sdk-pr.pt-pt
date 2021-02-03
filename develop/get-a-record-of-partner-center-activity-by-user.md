---
title: Obter um registo da atividade do Centro de Parceiros
description: Como recuperar um registo de operações, como realizado por um utilizador ou aplicação parceira, durante um período de tempo.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2f37eae8bb96c1c1e7008e8c566b085e25d8807d
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769530"
---
# <a name="get-a-record-of-partner-center-activity"></a>Obter um registo da atividade do Centro de Parceiros

**Aplica-se a**

- Partner Center
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Este artigo descreve como recuperar um registo de operações que foi realizado por um utilizador ou aplicação de um parceiro durante um período de tempo.

Utilize esta API para recuperar os registos de auditoria dos 30 dias anteriores a partir da data atual, ou para um intervalo de datas especificado por incluir a data de início e/ou a data final. Note-se, no entanto, que por razões de desempenho a disponibilidade de dados de registo de atividade está limitada aos 90 dias anteriores. Os pedidos com uma data de início superior a 90 dias antes da data atual receberão uma exceção de mau pedido (código de erro: 400) e uma mensagem apropriada.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

## <a name="c"></a>C\#

Para obter um registo das operações do Partner Center, primeiro estabeleça o intervalo de datas para os registos que pretende recuperar. O exemplo de código a seguir utiliza apenas uma data de início, mas também pode incluir uma data de fim. Para mais informações, consulte o método [**De consulta.**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) Em seguida, crie as variáveis necessárias para o tipo de filtro que pretende aplicar e atribua os valores apropriados. Por exemplo, para filtrar por sub-cordas de nome da empresa, crie uma variável para segurar o subluto. Para filtrar por ID do cliente, crie uma variável para segurar o ID.

No exemplo seguinte, o código de amostra é fornecido para filtrar por um sub-modelo de nome da empresa, ID do cliente ou tipo de recurso. Escolha um e comente os outros. Em cada caso, primeiro instantaneamente um objeto [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) utilizando o seu [**construtor**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter.-ctor) padrão para criar o filtro. Terá de passar uma corda que contenha o campo para procurar, e o operador apropriado para aplicar, como mostrado. Também deve fornecer a corda para filtrar.

Em seguida, utilize a propriedade [**AuditRecords**](/dotnet/api/microsoft.store.partnercenter.ipartner.auditrecords) para obter uma interface para auditar operações de registo, e ligue para o método [**Consulta**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) ou [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.queryasync) para executar o filtro e obter a recolha de [**AuditRecord's**](/dotnet/api/microsoft.store.partnercenter.models.auditing.auditrecord) que representam a primeira página do resultado. Passe o método a data de início, uma data de fim opcional não utilizada no exemplo aqui, e um objeto [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) que representa uma consulta sobre uma entidade. O objeto IQuery é criado passando o filtro criado acima para o método [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) [**da QueriaFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)

Assim que tiver a página inicial dos itens, utilize os [**Enumeradores.AuditRecords.Crie**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) método para criar um enumerador que possa utilizar para iterar através das páginas restantes.

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

**Amostra**: [App de teste de consola](console-test-app.md). **Projeto**: Partner Center SDK Samples **Pasta**: Auditoria

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                                                                                                    |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate} HTTP/1.1                                                                                                     |
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate} HTTP/1.1                                                                                   |
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filtro={"Field":"CompanyName","Value":"{searchSubstring}","Operador":"substring"} HTTP/1.1 |
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filtro={"Field":"CustomerId","Value":"{customerId}","Operador":"igual"} HTTP/1.1          |
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filtro={"Field":"ResourceType","Value":"{resourceType}","Operador":"igual"} HTTP/1.1      |

### <a name="uri-parameter"></a>Parâmetro URI

Utilize os seguintes parâmetros de consulta ao criar o pedido.

| Nome      | Tipo   | Necessário | Descrição                                                                                                                                                                                                                |
|-----------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| startDate | date   | Não       | A data de início no formato y-mm-dd. Se nenhuma for fornecida, o resultado definido será de incumprimento de 30 dias antes da data do pedido. Este parâmetro é opcional quando um filtro é fornecido.                                          |
| endDate   | date   | Não       | A data final em formato y-mm-dd. Este parâmetro é opcional quando um filtro é fornecido. Quando a data de fim é omitida ou definida para nula, o pedido devolve a janela max ou utiliza hoje como data de fim, o que for menor. |
| filter    | cadeia (de carateres) | No       | O filtro a aplicar. Este parâmetro deve ser uma corda codificada. Este parâmetro é opcional quando a data de início ou a data de fim são fornecidas.                                                                                              |

### <a name="filter-syntax"></a>Sintaxe de filtro
Deve compor o parâmetro do filtro como uma série de pares separados de vírgula. Cada chave e valor devem ser citados individualmente e separados por um cólon. Todo o filtro deve ser codificado.

Um exemplo não codificado é o seguinte:

```
?filter{"Field":"CompanyName","Value":"bri","Operator":"substring"}
```

A tabela a seguir descreve os pares de valor-chave necessários:

| Chave                 | Valor                             |
|:--------------------|:----------------------------------|
| Campo               | O campo para filtrar. Os valores suportados podem ser encontrados na [sintaxe request](get-a-record-of-partner-center-activity-by-user.md#rest-request).                                         |
| Valor               | O valor a filtrar. O caso do valor é ignorado. Os seguintes parâmetros de valor são suportados como mostrado na [sintaxe de pedido:](get-a-record-of-partner-center-activity-by-user.md#rest-request)<br/><br/>                                                                *searchSubstring* - Substitua-se pelo nome da empresa. Pode introduzir um sub-adupe para corresponder a parte do nome da empresa (por exemplo, `bri` `Fabrikam, Inc` corresponderá).<br/>**Exemplo:**`"Value":"bri"`<br/><br/>                                                                *customerId* - Substitua por uma cadeia formatada GUID que represente o identificador do cliente.<br/>**Exemplo:**`"Value":"0c39d6d5-c70d-4c55-bc02-f620844f3fd1"`<br/><br/>                                                                                        *resourceType* - Substitua-o pelo tipo de recurso para o qual recuperar registos de auditoria (por exemplo, Assinatura). Os tipos de recursos disponíveis são definidos no [ResourceType](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype).<br/>**Exemplo:**`"Value":"Subscription"`                                 |
| Operador          | O operador a candidatar-se. Os operadores apoiados podem ser encontrados na [sintaxe request](get-a-record-of-partner-center-activity-by-user.md#rest-request).   |

### <a name="request-headers"></a>Cabeçalhos do pedido

- Consulte [os cabeçalhos Parter Center REST](headers.md) para obter mais informações.

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

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

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um conjunto de atividades que vão ao encontro dos filtros.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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