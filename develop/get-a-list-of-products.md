---
title: Obter uma lista de produtos (por país)
description: Pode utilizar o recurso Produto para obter uma coleção de produtos por país de clientes.
ms.date: 02/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 601fc2c8012d92d6964f0aaa29a3a46d732df300
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123456057"
---
# <a name="get-a-list-of-products-by-country"></a>Obter uma lista de produtos (por país)

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Você pode usar os seguintes métodos para obter uma coleção de produtos disponíveis em um determinado país.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um país.

## <a name="c"></a>C\#

Para obter uma lista de produtos:

1. Utilize a sua coleção **IAggregatePartner.Products** para selecionar o país utilizando o método **ByCountry().**

2. Selecione a vista do catálogo utilizando o método **ByTargetView().**

3. (Opcional) Selecione o âmbito de reserva utilizando o método **ByReservationScope().**

4. (Opcional) Selecione o segmento alvo utilizando o método **ByTargetSegment().**

5. Ligue para o método **Get()** ou **GetAsync()** para devolver a coleção.

```csharp
IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").Get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").ByTargetSegment("commercial").Get();

// Get the products for Azure reservations which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").Get();

// Get the products for Azure reservations which are applicable to Azure plans only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").ByReservationScope("AzurePlan").Get();

```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Para obter uma lista de produtos:

1. Utilize a função **IAggregatePartner.getProducts** para selecionar o país utilizando a função **byCountry().**

2. Selecione a vista do catálogo utilizando a função **byTargetView().**
3. (Opcional) Selecione o segmento alvo utilizando a função **byTargetSegment().**

4. Ligue para a função **get()** para devolver a coleção.

```java
// IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").byTargetSegment("commercial").get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Para obter uma lista de produtos:

1. Execute o comando [**Get-PartnerProduct.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md)

2. Selecione o catálogo especificando o parâmetro **Catálogo.**
3. (Opcional) Selecione o segmento alvo especificando o parâmetro **Segmento.**

```powershell
Get-PartnerProduct -Catalog 'Azure' -Segment 'commercial'
```

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------- |
| **GET** | [*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1 |

#### <a name="uri-parameters"></a>Parâmetros URI

Utilize os seguintes parâmetros de percurso e consulta para obter uma lista de produtos.

| Nome                   | Tipo     | Necessário | Descrição                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| país                | string   | Yes      | O ID do país/região.                                                  |
| targetView             | string   | Yes      | Identifica a visão do catálogo. Os valores suportados são: <br/><br/>**Azure,** que inclui todos os itens Azure<br/><br/>**AzureReservations**, que inclui todos os itens de reserva Azure<br/><br/>**AzureReservationsVM,** que inclui todos os itens de reserva de máquina virtual (VM)<br/><br/>**AzureReservationsSQL,** que inclui todos os itens de reserva SQL<br/><br/>**AzureReservationsCosmosDb,** que inclui todos os itens de reserva da base de dados cosmos<br/><br/>**MicrosoftAzure**, que inclui itens para subscrições Microsoft Azure **(MS-AZR-0145P)** e planos Azure<br/><br/>**OnlineServices**, que inclui todos os itens de serviço online. Este targetView inclui mercado comercial, serviços tradicionais baseados em licenças e novos serviços baseados em licenças de comércio<br/><br/>**Software**, que inclui todos os itens de software<br/><br/>**SoftwareSUSELinux,** que inclui todos os itens SUSE Linux de software<br/><br/>**SoftwarePerpetual,** que inclui todos os itens de software perpétuos<br/><br/>**SoftwareSubscriptions**, que inclui todos os itens de subscrição de software    |
| targetSegment          | cadeia (de carateres)   | No       | Identifica o segmento alvo. A vista para diferentes públicos-alvo. Os valores suportados são: <br/><br/>**comercial**<br/>**educação**<br/>**governo**<br/>**sem fins lucrativos**  |
| reservationScope | cadeia (de carateres)   | No | Ao consultar uma lista de produtos para Reservas Azure, especifique `reservationScope=AzurePlan` para obter uma lista de produtos que são aplicáveis aos planos Azure. Exclua este parâmetro para obter uma lista de produtos para reservas Azure, que são aplicáveis a Microsoft Azure **(MS-AZR-0145P)** subscrições.  |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-examples"></a>Solicitar exemplos

#### <a name="products-by-country"></a>Produtos por país

Siga este exemplo para obter uma lista de produtos por país para assinaturas Microsoft Azure (MS-AZR-0145P) e planos Azure.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-azure-plan"></a>Reservas Azure VM (plano Azure)

Siga este exemplo para obter uma lista de produtos por país para reservas Azure VM que são aplicáveis aos planos Azure.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureAzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Reservas Azure VM para subscrições Microsoft Azure (MS-AZR-0145P)

Siga este exemplo para obter uma lista de produtos por país para reservas Azure VM que são aplicáveis às assinaturas Microsoft Azure (MS-AZR-0145P).

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="new-commerce-license-based-services"></a>Novos serviços baseados em licenças de comércio

> [!Note] 
> As novas alterações ao Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365

Siga este exemplo para obter uma lista de produtos por país para novos serviços baseados em licenças de comércio como parte da nova experiência de comércio experiência técnica pré-visualização. Novos serviços baseados em licenças de comércio serão identificados por ID e exibirão valores de **OnlineServicesNCE**. Veja o exemplo de resposta abaixo.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=OnlineServices HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o organismo de resposta contém uma coleção de recursos [**do Produto.**](product-resources.md#product)

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).

Este método devolve os seguintes códigos de erro:

| Código de Estado HTTP     | Código de erro   | Description                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| 403                  | 400030       | Não é permitido o acesso ao objetivo solicitado.                                                     |
| 403                  | 400036       | Não é permitido o acesso ao targetView solicitado.                                                        |

### <a name="response-example-for-azure-vm-reservations-azure-plan"></a>Exemplo de resposta para reservas Azure VM (plano Azure)

```http
{
    "totalCount": 19,
    "items": [
        {
            "id": "DZH318Z0BQ3Q",
            "title": "Virtual Machines DSv2 Series",
            "description": "Dsv2-series instances are the latest generation of D-series instances that will carry more powerful CPUs which are on average about 35% faster than D-series instances, and carry the same memory and disk configurations as the D-series. Dsv2-series instances are based on the latest generation 2.4 GHz Intel Xeon® E5-2673 v3 (Haswell) processor, and with Intel Turbo Boost Technology 2.0 can go to 3.2 GHz.",
            "productType": {
                "id": "Azure",
                "displayName": "Azure",
                "subType": {
                "id": "VirtualMachines",
                "displayName": "VirtualMachines"
                }
            },
            "isMicrosoftProduct": true,
            "publisherName": "Microsoft",
            "links": {
                "skus": {
                    "uri": "/products/DZH318Z0BQ3Q/skus?country=US",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/DZH318Z0BQ3Q?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        ...
    ],
    "links": {
        "self": {
            "uri": "/products?country=US&targetView=Azure",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="response-example-for-new-commerce-license-based-services"></a>Exemplo de resposta para novos serviços baseados em licenças de comércio

> [!Note] 
> As novas alterações ao Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365

```http
{
  "totalCount": 19,
  "items": [{
      "id": "CFQ7TTC0LH18",
      "title": "Microsoft 365 Business Basic",
      "description": "Best for businesses that need professional email, cloud file storage, and online meetings & chat. Desktop versions of Office apps like Excel, Word, and PowerPoint not included. For businesses with up to 300 employees.",
      "productType": {
        "id": "OnlineServicesNCE",
        "displayName": "OnlineServicesNCE"
      },
      "isMicrosoftProduct": true,
      "publisherName": "Microsoft Corporation",
      "links": {
        "skus": {
          "uri": "/products/CFQ7TTC0LH18/skus?country=US",
          "method": "GET",
          "headers": []
        },
        "self": {
          "uri": "/products/CFQ7TTC0LH18?country=US",
          "method": "GET",
          "headers": []
        }
      }
    },
    ...
  ],
  "links": {
    "self": {
      "uri": "/products?country=US&targetView=OnlineServices",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Collection"
  }
}
```

