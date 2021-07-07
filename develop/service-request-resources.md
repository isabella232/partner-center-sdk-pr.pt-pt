---
title: Recursos de pedido de serviço
description: Os parceiros podem apresentar pedidos de serviço em nome dos seus parceiros para reportar serviços de perturbações fornecidos pela Microsoft ou solicitar outro suporte técnico que sejam incapazes de fornecer.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 02a02e6a873ad8785150368f3d4b89af2b588529
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547364"
---
# <a name="service-request-resources"></a>Recursos de pedido de serviço

**Aplica-se a**: Partner Center | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Os parceiros podem apresentar pedidos de serviço em nome dos seus parceiros para reportar serviços de perturbações fornecidos pela Microsoft ou solicitar outro suporte técnico que sejam incapazes de fornecer.

## <a name="servicerequest"></a>Requesto de Serviço

Descreve um pedido de serviço apresentado por um parceiro, incluindo a forma como esse pedido está a progredir.

| Propriedade         | Tipo                                                          | Description                                                                          |
|------------------|---------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Título            | string                                                        | O título de pedido de serviço.                                                           |
| Description      | cadeia (de carateres)                                                        | A descrição.                                                                     |
| Gravidade         | string                                                        | A gravidade: "desconhecido", "crítico", "moderado", ou "mínimo".                       |
| SupportTopicId   | string                                                        | A identificação do tópico de apoio.                                                         |
| Nome De ApoioTopic | string                                                        | O nome do tema de apoio.                                                       |
| Id               | string                                                        | A identificação do pedido de serviço.                                                       |
| Estado           | string                                                        | O estado do pedido de serviço: "nenhum", "aberto", "fechado", ou "atenção \_ necessária". |
| Organização     | [Organização de ServiçosRequest](#servicerequestorganization)     | Organização para a qual o pedido de serviço é criado.                               |
| PrimaryContact   | [ServiceRequestContact](#servicerequestcontact)               | Contacto Primário no pedido de serviço.                                              |
| LastUpdatedBy    | [ServiceRequestContact](#servicerequestcontact)               | Contacto "Última Atualização Por" para alterações ao pedido de serviço.                        |
| NomeDoProduto      | string                                                        | O nome do produto que corresponde ao pedido de serviço.                     |
| ProductId        | string                                                        | ID do produto.                                                               |
| CreatedDate      | data                                                          | A data da criação do pedido de serviço.                                          |
| LastModifiedDate (Carga incremental: LastModifiedDate) | data                                                          | A data em que o pedido de serviço foi alterado pela última vez.                                 |
| Último Resultado Fechado   | data                                                          | A data em que o pedido de serviço foi fechado pela última vez.                                   |
| FileLinks        | matriz de recursos [FileInfo](utility-resources.md#fileinfo) | A recolha de Links de Ficheiros que diz respeito ao pedido de serviço.                    |
| NewNote          | [ServiceRequestNote](#servicerequestnote)                     | Uma nota pode ser adicionada a um pedido de serviço existente.                                  |
| Notas            | matriz de [ServiceRequestNotes](#servicerequestnote)           | Uma coleção de notas adicionadas ao pedido de serviço.                                  |
| CódigoDoPaís      | string                                                        | O país correspondente ao pedido de serviço.                                    |
| Atributos       | RecursosTributos                                            | Os metadados atribuem correspondentes ao pedido de serviço.                        |

## <a name="servicerequestcontact"></a>ServiceRequestContact

Descreve um contacto que cria ou modifica um pedido de serviço.

| Propriedade     | Tipo                                                      | Description                                            |
|--------------|-----------------------------------------------------------|--------------------------------------------------------|
| Organização | [Organização de ServiçosRequest](#servicerequestorganization) | Organização para a qual o pedido de serviço é criado. |
| ContatoId    | string                                                    | O contacto é uma identificação única.                               |
| LastName     | string                                                    | O último nome do contacto.                          |
| FirstName    | string                                                    | O primeiro nome do contacto.                         |
| E-mail        | string                                                    | O e-mail do contacto.                              |
| PhoneNumber  | string                                                    | O número de telefone do contacto.                       |

## <a name="servicerequestnote"></a>ServiceRequestNote

Descreve uma nota anexada a um pedido de serviço.

| Propriedade      | Tipo   | Description                                  |
|---------------|--------|----------------------------------------------|
| Nome criado | string | O nome do criador da nota.         |
| CreatedDate   | data   | A data e a hora em que o bilhete foi criado. |
| Texto          | string | O texto da nota.                        |

## <a name="servicerequestorganization"></a>Organização de ServiçosRequest

Descreve a organização para a qual o pedido de serviço é criado.

| Propriedade    | Tipo   | Description                           |
|-------------|--------|---------------------------------------|
| Id          | string | A identificação única da organização.    |
| Name        | string | O nome da organização.         |
| PhoneNumber | string | O número de telefone da organização. |

## <a name="supporttopic"></a>SuporteTopic

Descreve um tópico de apoio. Os pedidos de serviço especificam um tópico de suporte para garantir que são processados de forma rápida e eficaz.

| Propriedade    | Tipo               | Descrição                                                   |
|-------------|--------------------|---------------------------------------------------------------|
| Nome        | string             | O nome do tema de apoio.                                |
| Description | cadeia (de carateres)             | A descrição do tópico de apoio.                         |
| Id          | string             | A identificação única do tópico de apoio.                           |
| Atributos  | RecursosTributos | Os metadados atribuem correspondentes ao pedido de serviço. |

