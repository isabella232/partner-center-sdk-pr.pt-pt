---
title: Obter uma lista de clientes filtrados por um campo de pesquisa
description: Recebe uma coleção de recursos do Cliente que combinam com um filtro. Pode configurar opcionalmente o tamanho da página. Pode filtrar pelo nome da empresa, domínio, revendedor indireto ou fornecedor de solução de nuvem indireta (CSP).
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: aad9524dbe2c9edbbd7c1d50da7a448f6872fcb9
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769374"
---
# <a name="get-a-list-of-customers-filtered-by-a-search-field"></a>Obter uma lista de clientes filtrados por um campo de pesquisa

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Recebe uma coleção de recursos do [Cliente](customer-resources.md#customer) que combinam com um filtro. Pode configurar opcionalmente o tamanho da página. Pode filtrar pelo nome da empresa, domínio, revendedor indireto ou fornecedor de solução de nuvem indireta (CSP).

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um filtro construído pelo utilizador.

## <a name="c"></a>C\#

Para obter uma coleção de clientes que correspondam a um filtro, primeiro instantaneamente um objeto [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) para criar o filtro. Terá de passar uma corda que contenha o [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield)e indicar o tipo de operação de filtro como [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation). É a única operação de filtro de campo suportada pelo ponto final dos clientes. Também terá de fornecer a corda para filtrar.

Em seguida, instantânea um objeto [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) para passar para a consulta, chamando o método [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) e passando-lhe o filtro. BuildSimplyQuery é apenas um dos tipos de consulta suportados pela classe [**QueryFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)

Finalmente, para executar o filtro e obter o resultado, use primeiro [**o IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) para obter uma interface para as operações do cliente do parceiro. Em [**seguida,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) chame o método Consulta ou [**ConsultaAsync.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync)

``` csharp
IAggregatePartner partnerOperations;

// Specify the partial string to filter by (to match Contoso).
string searchPrefix = "cont"

// Create a simple field filter.
var fieldFilter = new SimpleFieldFilter(
    CustomerSearchField.CompanyName.ToString(),
    FieldFilterOperation.StartsWith,
    searchPrefix);

// Create an iQuery object to pass to the Query method.
var myQuery = QueryFactory.Instance.BuildSimpleQuery(fieldFilter);

// Get the collection of matching customers.
var customers = partnerOperations.Customers.Query(myQuery);
```

**Amostra**: [App de teste de consola](console-test-app.md). **Projeto**: Partner Center SDK Samples **Class**: FilterCustomers.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| **Obter** | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes?size={size}&filtro={{filter} HTTP/1.1 |

### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros de consulta.

| Nome   | Tipo   | Necessário | Descrição                                                                    |
|--------|--------|----------|--------------------------------------------------------------------------------|
| size   | int    | Não       | O número de resultados a apresentar ao mesmo tempo. Este parâmetro é opcional. |
| filter | filter | Sim      | O filtro para aplicar aos clientes. Isto deve ser uma corda codificada.              |

### <a name="filter-syntax"></a>Sintaxe do filtro

Deve compor o parâmetro do filtro como uma série de pares separados de vírgula. Cada chave e valor devem ser citados individualmente e separados por um cólon. Todo o filtro deve ser codificado.

Um exemplo não codificado é o seguinte:

```http
?filter{"Field":"CompanyName","Value":"cont","Operator":"starts_with"}
```

A tabela a seguir descreve os pares de valor-chave necessários:

| Chave      | Valor                                                                                                                    |
|----------|--------------------------------------------------------------------------------------------------------------------------|
| Campo    | O campo para filtrar. Os valores válidos podem ser encontrados no [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield). |
| Valor    | O valor a filtrar. O caso do valor é ignorado.                                                                |
| Operador | O operador a candidatar-se. O único valor suportado para este cenário de cliente é "começa \_ por".                            |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter=%7B%22Field%22%3A%22CompanyName%22%2C%22Value%22%3A%22Cont%22%2C%22Operator%22%3A%22starts_with%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 5ce66de5-eea9-486f-a11c-c852aa3d1502
MS-CorrelationId: a2a912ee-d595-47e2-97ae-1b0ae1efa13d
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma coleção de recursos [do Cliente](customer-resources.md#customer) correspondentes no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 1839
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a2a912ee-d595-47e2-97ae-1b0ae1efa13d
MS-RequestId: dfeda56c-1af5-43fc-a9c0-346b9e85dc96
MS-CV: n0lMNyJtaUC802pO.0
MS-ServerId: 202010223
Date: Fri, 24 Feb 2017 22:08:20 GMT

{
    "totalCount": 3,
    "items": [{
            "id": "c5757d70-06f3-4f23-8367-5a9e55019f94",
            "companyProfile": {
                "tenantId": "c5757d70-06f3-4f23-8367-5a9e55019f94",
                "domain": "contoso190.onmicrosoft.com",
                "companyName": "Contoso190",
                "links": {
                    "self": {
                        "uri": "/customers/c5757d70-06f3-4f23-8367-5a9e55019f94/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/c5757d70-06f3-4f23-8367-5a9e55019f94",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "7b26b357-9ca3-48b8-a58e-4febe2662a5d",
            "companyProfile": {
                "tenantId": "7b26b357-9ca3-48b8-a58e-4febe2662a5d",
                "domain": "ContosoCorpCo.onmicrosoft.com",
                "companyName": "Contoso",
                "links": {
                    "self": {
                        "uri": "/customers/7b26b357-9ca3-48b8-a58e-4febe2662a5d/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/7b26b357-9ca3-48b8-a58e-4febe2662a5d",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
            "companyProfile": {
                "tenantId": "bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
                "domain": "contosocorpdemo.onmicrosoft.com",
                "companyName": "Contoso",
                "links": {
                    "self": {
                        "uri": "/customers/bfbd6ef0-311f-47ec-bbd7-0fcb7846661b/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers?size=0&filter=%7B%22Field%22%3A%22Domain%22%2C%22Value%22%3A%22cont%22%2C%22Operator%22%3A%22starts_with%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
