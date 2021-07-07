---
title: Recursos recorde de utilização do Azure
description: O registo de utilização do Azure contém detalhes sobre a utilização de um recurso de subscrição Azure.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 868381fcb29eb1391efcdf79154f7b998e3032e5
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974306"
---
# <a name="azure-utilization-record-resources"></a>Recursos recorde de utilização do Azure

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

O registo de utilização do Azure contém detalhes sobre a utilização de um recurso de subscrição Azure. Se é um parceiro de prestador de serviços na nuvem que detém a relação de faturação das subscrições Azure dos seus clientes, pode utilizar esta API REST para fornecer uma forma escalável de rastrear o uso incorrido nas subscrições de forma a enviar uma fatura aos seus clientes no final de cada ciclo de faturação.

Para acompanhar o uso e ajudar a prever a sua fatura mensal e as faturas para clientes individuais, pode combinar uma consulta de Cartão de Tarifa para [Obter preços para Microsoft Azure](get-prices-for-microsoft-azure.md) com um pedido para obter os [registos de utilização de um cliente para o Azure.](get-a-customer-s-utilization-record-for-azure.md)

Os preços diferem por mercado e por moeda, e esta API tem em conta a localização. Por padrão, a API utiliza as definições de perfil do seu parceiro no Partner Center e no seu idioma do navegador, e essas definições são personalizáveis. A consciência da localização é especialmente relevante se você gerir vendas em vários mercados a partir de um único escritório centralizado.

## <a name="azureutilizationrecord"></a>AzureutilizationRecord

Descreve as propriedades de um recurso de registo de utilização Azure.

| Propriedade       | Tipo                                      | Necessário | Descrição                                                                                                                                                                             |
|----------------|-------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| usageStartTime | string                                    | Yes      | O início do intervalo de tempo de agregação de utilização. A resposta é agrupada no momento do consumo (quando o recurso foi utilizado vs. quando foi reportado ao sistema de faturação). |
| usageEndTime   | string                                    | Yes      | O fim do intervalo de tempo de agregação de utilização. A resposta é agrupada no momento do consumo. Isto é, quando o recurso foi usado vs. quando foi reportado ao sistema de faturação.   |
| recurso       | objeto                                    | Yes      | Contém um objeto [AzureResource.](#azureresource)                                                                                                                                     |
| quantidade       | número                                    | Yes      | A quantidade consumida do [AzureResource.](#azureresource)                                                                                                                           |
| unit           | cadeia (de carateres)                                    | No       | O tipo de quantidade (horas, bytes, etc.) Esta propriedade é opcional                                                                                                                     |
| infoFields     | objeto                                    | Yes      | Pares de valor-chave de detalhes de nível de instância. Este objeto pode estar vazio.                                                                                                                    |
| casoData   | objeto                                    | No       | Contém um objeto [AzureInstanceData](#azureinstancedata) que contém pares de dados de nível de caso de valor-chave. Esta propriedade é opcional e não pode ser incluída.                  |
| atributos     | [RecursosTributos](utility-resources.md#resourceattributes) | Yes      | Os atributos dos metadados. Contém "objectType": "AzureUtilizationRecord"                                                                                                                |

### <a name="operations-on-the-azureutilizationrecord-resource"></a>Operações no recurso AzureUtilizationRecord

- [Obter os registos de utilização de um cliente do Azure](get-a-customer-s-utilization-record-for-azure.md)

## <a name="azureresource"></a>AzureResource

Descreve as propriedades de um Recurso Azure.

| Propriedade    | Tipo   | Necessário | Descrição                                                                         |
|-------------|--------|----------|-------------------------------------------------------------------------------------|
| ID          | string | Yes      | Identificador único do recurso Azure. Também conhecido como recursoID ou recurso GUID. |
| name        | cadeia (de carateres) | No       | Nome amigável do recurso que está a ser consumido. Esta propriedade é opcional.            |
| categoria    | cadeia (de carateres) | No       | A categoria do recurso consumido. Esta propriedade é opcional.                   |
| subcategoria | cadeia (de carateres) | No       | A subcategoria do recurso consumido. Esta propriedade é opcional.               |
| region      | cadeia (de carateres) | No       | A região do recurso consumido. Esta propriedade é opcional.                     |

## <a name="azureinstancedata"></a>AzureInstanceData

Descreve as propriedades de um recurso de dados de instância Azure.

| Propriedade       | Tipo             | Necessário | Descrição                                                                                                        |
|----------------|------------------|----------|--------------------------------------------------------------------------------------------------------------------|
| recursosUri    | string           | Yes      | O ID de recurso Azure totalmente qualificado, que inclui os grupos de recursos e o nome da instância.                   |
| localização       | string           | Yes      | Região em que o serviço foi executado.                                                                               |
| partNumber     | objeto           | Yes      | Espaço de nome único usado para identificar o recurso para o uso de terceiros no mercado comercial. Esta propriedade pode ser uma corda vazia. |
| número de encomendas    | número           | Yes      | Espaço de nome único usado para identificar a ordem de terceiros para o mercado comercial. Esta propriedade pode ser uma corda vazia.          |
| etiquetas           | matriz de cadeias (de carateres) | No       | Etiquetas de recursos especificadas pelo utilizador. Esta propriedade é opcional e não pode ser incluída.                            |
| additionalInfo | matriz de cadeias (de carateres) | No       | Dados adicionais para um recurso Azure. Esta propriedade é opcional e não pode ser incluída.                          |