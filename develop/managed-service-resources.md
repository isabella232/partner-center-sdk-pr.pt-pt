---
title: Recursos de serviço geridos
description: Os serviços geridos são serviços aos quais um parceiro delegou privilégios administrativos. Os parceiros podem fornecer apoio e pedidos de serviço de arquivo em nome dos seus serviços geridos.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 066c9f2a0d5ca8d03553508c2b471ca49735406a5a0566bf48b0773385c129f7
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994392"
---
# <a name="managed-service-resources"></a>Recursos de serviço geridos

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Os serviços geridos são serviços aos quais um parceiro delegou privilégios administrativos. Os parceiros podem fornecer apoio e pedidos de serviço de arquivo em nome dos seus serviços geridos.

## <a name="managedservice"></a>Serviço Gerido

Descreve um serviço gerido.

| Propriedade   | Tipo                | Description                                              |
|------------|---------------------|----------------------------------------------------------|
| Id         | string              | A identificação de serviço gerido.                                  |
| Name       | string              | O nome do serviço gerido.                         |
| Nome do Grupo  | string              | O nome do grupo a que pertence o serviço.      |
| Ligações      | ManagedServiceLinks | As ligações de recursos correspondentes ao serviço gerido. |
| Atributos | RecursosTributos  | Os metadados atribuem correspondentes ao acordo.  |

## <a name="managedservicelinks"></a>ManagedServiceLinks

Contém os links que permitem ao parceiro com permissões de administração delegadas fornecer suporte para o serviço.

| Propriedade      | Tipo | Description                 |
|---------------|------|-----------------------------|
| Serviço de Administração  | Ligação | O serviço de administração URI.      |
| Saúde de Serviço | Ligação | O serviço de saúde URI.     |
| ServiceTicket | Ligação | O bilhete de serviço URI.     |
| Autónomo          | Ligação | O auto-URI.               |
| Seguinte          | Ligação | A próxima página de artigos.     |
| Anterior      | Ligação | A página anterior dos artigos. |

