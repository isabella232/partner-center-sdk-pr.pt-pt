---
title: Recursos analíticos
description: Os recursos do Partner Center contêm dados sobre o uso, implantação e consumo. Inclui insights sobre a implementação e utilização de licenças por parceiros e clientes.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: v-sumukh
ms.author: v-sumukh
ms.openlocfilehash: 69c6c195ba1a0d657a91320b2f9b08b5269a8499
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025603"
---
# <a name="analytics-api-resources-that-help-you-report-on-license-usage-deployment-and-consumption"></a>Recursos API analíticos que o ajudam a reportar sobre o uso, implementação e consumo de licenças

Os recursos aqui definidos contêm dados utilizados para reportar sobre o uso, implantação e consumo.

## <a name="partnerlicensesdeploymentinsights"></a>PartnerLicensesDeploymentInsights

O recurso **PartnerLicensesDeploymentInsights** contém insights de nível de parceiro sobre a implementação de licenças.

| Propriedade                  | Tipo                                                           | Description                                                                         |
|---------------------------|----------------------------------------------------------------|-------------------------------------------------------------------------------------|
| proratedDeploymentPercent | número                                                         | A percentagem de licenças implementadas.                                                |
| licençasSold              | número                                                         | O número de licenças vendidas.                                                        |
| processadoDadade tempo         | cadeia no formato de data-hora UTC                                 | A data e a hora em que os dados foram agregados.                                     |
| nome de serviço               | string                                                         | O nome de serviço (por exemplo: o365, crm).                                                  |
| canal                   | string                                                         | O nome do canal do serviço (por exemplo: revendedor).                                    |
| atributos                | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados. Inclui "objectType": "PartnerLicensesDeploymentInsights" |

## <a name="partnerlicensesusageinsights"></a>PartnerLicensesUsageInsights

O recurso **PartnerLicensesUsageInsights** contém insights de nível de parceiro sobre o uso da licença.

| Propriedade                     | Tipo                                                           | Description                                                                    |
|------------------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------|
| proratedLicensesUsagePercent | número                                                         | A percentagem de licenças implementadas.                                           |
| carga de trabalhoName                 | string                                                         | O nome da carga de trabalho (por exemplo: troca).                                             |
| processadoDadade tempo            | cadeia no formato de data-hora UTC                                 | A data e a hora em que os dados foram agregados.                                |
| nome de serviço                  | string                                                         | O nome de serviço (por exemplo: o365, crm).                                             |
| canal                      | string                                                         | O nome do canal do serviço (por exemplo: revendedor).                               |
| atributos                   | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados. Inclui "objectType": "PartnerLicensesUsageInsights" |

## <a name="customerlicensesdeploymentinsights"></a>CustomerLicensesDeploymentInsights

O recurso **CustomerLicensesDeploymentInsights** contém insights ao nível do cliente sobre a implementação da licença.

| Propriedade          | Tipo                                                           | Description                                                                          |
|-------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| licençasDeployed  | número                                                         | O número de licenças implementadas.                                                     |
| licençasSold      | número                                                         | O número de licenças vendidas.                                                         |
| implantaçãoPercent | número                                                         | A percentagem ajustada de licenças implementadas.                                        |
| customerId        | string                                                         | O identificador de clientes.                                                             |
| nome do cliente      | string                                                         | O nome do cliente.                                                                   |
| produtoName       | string                                                         | O nome do produto.                                                                    |
| serviceCode       | string                                                         | O código de serviço da licença.                                                     |
| processadoDadade tempo | cadeia no formato de data-hora UTC                                 | A data e a hora em que os dados foram agregados.                                      |
| nome de serviço       | string                                                         | O nome de serviço (por exemplo: o365, crm).                                                   |
| canal           | string                                                         | O nome do canal do serviço (por exemplo: revendedor).                                     |
| atributos        | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados. Inclui "objectType": "CustomerLicensesDeploymentInsights" |

## <a name="customerlicensesusageinsights"></a>CustomerLicensesUsageInsights

O recurso **CustomerLicensesUsageInsights** contém insights ao nível do cliente sobre o uso da licença.

| Propriedade          | Tipo                                                           | Description                                                                     |
|-------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| código de carga de trabalho      | string                                                         | O código de carga de trabalho.                                                              |
| carga de trabalhoName      | número                                                         | O nome da carga de trabalho (por exemplo: Exchange).                                              |
| usePercent      | número                                                         | A percentagem ajustada de licenças utilizadas.                                       |
| licençasActivar    | número                                                         | O número de licenças ativas.                                                  |
| licençasQualizado | número                                                         | O número de licenças qualificadas.                                               |
| customerId        | string                                                         | O identificador de clientes.                                                        |
| nome do cliente      | string                                                         | O nome do cliente.                                                              |
| produtoName       | string                                                         | O nome do produto.                                                               |
| serviceCode       | string                                                         | O código de serviço da licença.                                                |
| processadoDadade tempo | cadeia no formato de data-hora UTC                                 | A data e a hora em que os dados foram agregados.                                 |
| nome de serviço       | string                                                         | O nome de serviço (por exemplo: o365, crm).                                              |
| canal           | string                                                         | O nome do canal do serviço (por exemplo: revendedor).                                |
| atributos        | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados. Inclui "objectType": "CustomerLicensesUsageInsights" |