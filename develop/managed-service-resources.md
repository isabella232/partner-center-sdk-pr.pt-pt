---
title: Recursos de serviço geridos
description: Os serviços geridos são serviços aos quais um parceiro delegou privilégios administrativos. Os parceiros podem fornecer apoio e pedidos de serviço de arquivo em nome dos seus serviços geridos.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ef644ac4d8ae9660cffc9558af33cc27832556c7
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768863"
---
# <a name="managed-service-resources"></a>Recursos de serviço geridos

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Os serviços geridos são serviços aos quais um parceiro delegou privilégios administrativos. Os parceiros podem fornecer apoio e pedidos de serviço de arquivo em nome dos seus serviços geridos.

## <a name="managedservice"></a>Serviço Gerido

Descreve um serviço gerido.

| Propriedade   | Tipo                | Descrição                                              |
|------------|---------------------|----------------------------------------------------------|
| Id         | string              | O id de serviço gerido.                                  |
| Nome       | string              | O nome do serviço gerido.                         |
| Nome do Grupo  | string              | O nome do grupo a que pertence o serviço.      |
| Ligações      | ManagedServiceLinks | As ligações de recursos correspondentes ao serviço gerido. |
| Atributos | RecursosTributos  | Os metadados atribuem correspondentes ao acordo.  |

## <a name="managedservicelinks"></a>ManagedServiceLinks

Contém os links que permitem ao parceiro com permissões de administração delegadas fornecer suporte para o serviço.

| Propriedade      | Tipo | Descrição                 |
|---------------|------|-----------------------------|
| Serviço de Administração  | Ligação | O serviço de administração URI.      |
| Saúde de Serviço | Ligação | O serviço de saúde URI.     |
| ServiceTicket | Ligação | O bilhete de serviço URI.     |
| Autónomo          | Ligação | O auto-URI.               |
| Seguinte          | Ligação | A próxima página de artigos.     |
| Anterior      | Ligação | A página anterior dos artigos. |

