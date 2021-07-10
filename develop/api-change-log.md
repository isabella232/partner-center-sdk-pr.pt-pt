---
title: Registo de alterações da API REST do Centro de Parceiros
description: Esta página lista alterações nas APIs do Centro Parceiro REST
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.topic: reference
ms.date: 12/15/2020
ms.openlocfilehash: d4f7f034a36a26b6219086ca952b189f7a313ef7
ms.sourcegitcommit: 51237e7e98d71a7e0590b4d6a4034b6409542126
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/09/2021
ms.locfileid: "113572000"
---
# <a name="december-2020-changes-to-partner-center-rest-apis"></a>Alterações de dezembro de 2020 para Parceiro Centro REST APIs

Consulte aqui as alterações às APIs do Partner Center REST.

## <a name="enhancements-to-education-pricing-eligibility-apis"></a>Melhorias nos preços da educação APIs de elegibilidade



### <a name="what-has-changed"></a>O que mudou?

Atualmente, a API do Partner Center dispõe de qualificações GET e PUT para verificar a elegibilidade dos clientes da Educação. Não haverá alterações na API de Qualificação GET. No entanto, adicionámos um caso de retorno à API de Qualificação PUT.

- GET - não muda.
- PUT - o caso de devolução será adicionado.

Estas APIs serão reformadas no final de fevereiro de 2021, para serem substituídas por novas APIs, conforme descrito abaixo.

### <a name="scenarios-impacted"></a>Cenários impactados:

Elegibilidade do cliente para preços de educação em SKUs selecionados

### <a name="detail-descriptions"></a>Descrições de detalhes

Serão introduzidas duas novas APIs de Qualificações GET e POST. As novas APIs utilizarão **qualificações,** não **qualificações.** As APIs estarão disponíveis para testes no FY21 Q22.

#### <a name="get-qualifications"></a>Obter Qualificações

```http
GET {customer_id}/qualifications
```

#### <a name="response-example"></a>Exemplo de resposta:

```json
{
  "Qualification": "Education",
  "VettingStatus": "Denied",
  "VettingReason": "Not an education customer",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

#### <a name="response-fields"></a>Campos de resposta: 

- Valores de VettingStatus: Aprovado, Negado, InReview, etc.

- Valores vetingReason:
   - Não um Cliente de Educação
   - Não mais um Cliente de Educação
   - Não um cliente de educação - após revisão
   - Restrito ser cliente de educação
   - Não um domínio académico
   - Não é uma biblioteca elegível
   - Não é um museu elegível.
 
#### <a name="post-qualifications"></a>Qualificações POST

```http
POST {customer_id}/qualifications
    [
            "Qualification": "Education"
    ]
```

#### <a name="response-example"></a>Exemplo de resposta:

```JSON
{
  "Qualification": "Education",
  "VettingStatus": "InReview",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

## <a name="next-steps"></a>Passos seguintes

[Referência da API REST do Centro de Parceiros](partner-center-rest-api-reference.md)
