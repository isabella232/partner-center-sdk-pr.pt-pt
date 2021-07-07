---
title: Recursos de implantação de dispositivos
description: Recursos relacionados com a implementação do dispositivo Partner Center.
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c85f0bd6a633ac18aa8e56e5a89bfc5c8f0398cc
ms.sourcegitcommit: d20e7d572fee09a83a4b23a92da7ff09cfebe75a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111906514"
---
# <a name="device-deployment-resources"></a>Recursos de implantação de dispositivos

**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany

Os seguintes recursos estão relacionados com a implantação do dispositivo.

## <a name="configurationpolicy"></a>ConfiguraçãoPolícia

**ConfiguraçãoApolicia** fornece informações sobre uma política de configuração.

| Propriedade             | Tipo                                                           | Description                                                        |
|----------------------|----------------------------------------------|--------------------------------------------------------------------------------------|
| ID                   | string                                       | Uma cadeia formatada por GUID que identifica a política.                                  |
| name                 | string                                       | O nome amigável para a apólice.                                                    |
| categoria             | string                                       | A categoria.                                                                        |
| descrição          | string                                       | A descrição da apólice.                                                              |
| dispositivosAssignedCount | número                                       | O número de dispositivos atribuídos a esta política.                                       |
| policySettings       | matriz de cadeias (de carateres)                             | As definições de política: "nenhum", "remover \_ oem \_ pré-instalações", "utilizador oobe \_ não administrador \_ \_ \_ local", "saltar \_ as \_ definições expressas", "saltar \_ o registo de \_ oem", "saltar \_ eula".    |
| createdDate          | cadeia no formato de data-hora UTC               | A data e a hora da apólice foi criada.                                            |
| último Anúncio DeModified     | cadeia no formato de data-hora UTC               | A data e a hora em que a apólice foi modificada pela última vez.                                      |
| atributos           | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                            |

## <a name="device"></a>Dispositivo

**O dispositivo** fornece informações sobre um dispositivo.

| Propriedade            | Tipo                                                           | Description                                                              |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------|
| ID                  | string                                                         | Uma corda formatada pelo GUID que identifica o dispositivo.                      |
| serialNumber        | string                                                         | O número de série está exclusivamente associado ao dispositivo.                   |
| produtoKey          | string                                                         | A chave do produto exclusivamente associada ao dispositivo.                     |
| hardwareHash        | string                                                         | O hash de hardware exclusivamente associado ao dispositivo.                   |
| modeloName           | string                                                         | O nome do modelo associado ao dispositivo.                               |
| oemManufacturerName | string                                                         | O nome do fabricante OEM associado ao dispositivo.             |
| políticas            | matriz de objetos                                               | A lista de políticas atribuídas ao dispositivo.                             |
| uploadedDate        | cadeia no formato de data-hora UTC                                 | A data e a hora em que os detalhes do dispositivo foram carregados.                      |
| permitidos Operações   | matriz de cadeias (de carateres)                                               | A lista de métodos HTTP permitidos numa sincronização do dispositivo como GET, PATCH, DELETE. |
| atributos          | [RecursosTributos](utility-resources.md#resourceattributes)  | Os atributos dos metadados.                                                 |

## <a name="batchuploaddetails"></a>BatchUploadDetails

**BatchUploadDetails** descreve o estado de um carregamento de informações sobre cada dispositivo numa lista de dispositivos.

| Propriedade        | Tipo     | Description                                                                  |
|-----------------|----------|------------------------------------------------------------------------------|
| batchTrackingId | string   | Uma cadeia formatada guid que está associada ao lote de dispositivos carregados. |
| status          | string   | O estado do carregamento do lote: "desconhecido", "em fila", "processamento", "terminado", "terminado \_ com \_ erros". |
| startTime     | cadeia no formato de data-hora UTC | A data e a hora em que o processo de upload do lote começou.   |
| completetime   | cadeia no formato de data-hora UTC  | A data e a hora que o processo de upload do lote terminou.   |
| dispositivosStatus   | matriz de recursos [DeviceUploadDetails](#deviceuploaddetails) | Uma série de objetos que especificam o estado de cada carregamento de informações do dispositivo. |
| atributos      | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.  |

## <a name="deviceuploaddetails"></a>DeviceUploadDetails

**DeviceUploadDetails** descreve o estado de um upload de informações sobre um dispositivo.

| Propriedade         | Tipo                    | Description                                 |
|------------------|-------------------------|---------------------------------------------|
| deviceId         | string                  | Uma cadeia formatada guid que está associada ao dispositivo. |
| serialNumber     | string                  | O número de série está exclusivamente associado ao dispositivo. |
| produtoKey       | string                  | A chave do produto exclusivamente associada ao dispositivo. |
| status           | string                  | O estado do carregamento de informação do dispositivo: "em curso", "terminado", "terminado \_ com \_ erros". |
| errorCode        | string                  | O código de erro de estado HTTP devolvido se o upload do dispositivo falhar. |
| erroDescrição | string                  | A descrição do erro HTTP se o upload do dispositivo falhar. |
| atributos       | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.   |

## <a name="devicebatch"></a>DeviceBatch

**O DeviceBatch** representa uma coleção de dispositivos.

| Propriedade     | Tipo                                                           | Description                                                           |
|--------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| ID           | string                                                         | Uma cadeia formatada guid que está associada ao lote de dispositivos. |
| criado Por    | string                                                         | O nome do inquilino que criou a coleção.                   |
| criaçãoDate | cadeia no formato de data-hora UTC                                 | Os dados e o tempo que a recolha foi criada.                    |
| lista de dispositivos  | número                                                         | O número de dispositivos na coleção.                              |
| dispositivosLink  | [Ligação](utility-resources.md#link)                              | Uma ligação com os dispositivos contidos neste lote.                        |
| atributos   | [RecursosTributos](utility-resources.md#resourceattributes)  | Os atributos dos metadados.                                              |

## <a name="devicebatchcreationrequest"></a>DeviceBatchCreationRequest

**DeviceBatchCreationRequest** fornece as informações necessárias para criar um lote de dispositivos e povoa-o com dispositivos.

| Propriedade     | Tipo                                                           | Description                                                           |
|--------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| batchId      | string                                                         | Uma cadeia formatada guid que está associada ao lote de dispositivos. |
| dispositivos      | matriz de objetos do [dispositivo](#device)                             | Cada objeto especifica um dispositivo. São aceites as seguintes combinações de campos para identificar um dispositivo: hardwareHash + produtoKey, hardwareHash + serialNumber, hardwareHash + productKey + serialNumber, hardwareHash only, productKey only, serialNumber + oemManufacturerName + modelName. |
| atributos   | [RecursosTributos](utility-resources.md#resourceattributes)  | Os atributos dos metadados.                                              |

## <a name="devicepolicyupdaterequest"></a>DevicePolicyUpdateRequest

**DevicePolicyUpdateRequest** fornece as informações necessárias para atualizar uma lista de dispositivos com uma política.

| Propriedade     | Tipo                                                           | Description                                                           |
|--------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| dispositivos      | matriz de objetos do [dispositivo](#device)                             | Cada objeto especifica um dispositivo. São necessárias as seguintes propriedades: Id, Políticas. |
| atributos   | [RecursosTributos](utility-resources.md#resourceattributes)  | Os atributos dos metadados.                                              |
