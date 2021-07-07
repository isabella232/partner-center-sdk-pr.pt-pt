---
title: Cenários de API do Centro Parceiro
description: Saiba como Fornecedor de Soluções em Nuvem parceiros de programas podem usar a API do Partner Center para gerir programáticamente contas de clientes, encomendas, suporte e faturação.
ms.date: 10/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d74400a975323d5f0f276dbdece3621d8b47a609
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547483"
---
# <a name="partner-center-api-scenarios-that-let-you-programmatically-manage-customer-accounts"></a>Cenários de API do Partner Center que lhe permitem gerir programaticamente as contas dos clientes

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Microsoft Cloud for US Government

Este artigo descreve algumas das formas como os parceiros no programa Fornecedor de Soluções em Nuvem podem usar a API do Partner Center para gerir programáticamente áreas como:

- Contas de clientes
- Encomendas
- Subscrições
- Suporte
- Faturação

Existem diferentes versões do Partner Center disponíveis que incluem diferentes capacidades. Nem todos os cenários são suportados em todas as versões do Partner Center. Para saber mais, consulte [Developing for Partner Center for Microsoft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md).

## <a name="scenarios-supported-by-the-partner-center-sdk"></a>Cenários apoiados pelo Partner Center SDK

Todos os seguintes cenários podem ser concluídos de três maneiras diferentes:

- Manualmente no painel do [Centro de Parceiros.](https://partner.microsoft.com/dashboard)

- Utilizando programáticamente o Partner Center gerido a API.

- Utilização programática do Centro de Parceiros REST API.

| Para conhecer estes cenários apoiados:  | Consulte este recurso:     |
|----------------------------------|--------------------------|
| **Analítica:** Saiba como recuperar dados de análise sobre o uso do Azure, subscrições, licenças ou referências.         | [Análise](usage-analytics.md)  |
| **Operações de auditoria:** Saiba como recuperar registos históricos de auditoria da atividade e operações do Partner Center. | [Operações de auditoria](audit.md)                     |
| **Implementações do dispositivo:** Saiba mais sobre as políticas de configuração do dispositivo, trabalhando com lotes de dispositivos e metadados de dispositivos. Estes cenários incluem adicionar, eliminar, atualizar e recuperar políticas de configuração do dispositivo.    | [Implementação de dispositivos](device-deployment.md)  |
| **Contas e perfis:** Saiba como obter ou atualizar perfis de faturação de parceiros, perfis legais, perfil MPN, perfis de negócio ou perfis de suporte. Também pode obter uma lista de clientes ou revendedores indiretos. | [Gerir contas e perfis](manage-profiles-and-information.md)                                                                        |
| **Faturação:** Conheça áreas como mudar o ciclo de faturação, obter taxas Azure e registos de utilização do Azure, obter faturas, obter o saldo da conta corrente do parceiro ou obter custos de atendimento ao cliente.  | [Gerir faturação](manage-billing.md)   |
| **Gastos azure:** Obtenha informações sobre gastos da Azure e uso de parceiros, uso de subscrições de clientes, uso medido e orçamentos de utilização do cliente. Os cenários também incluem como atualizar um orçamento de utilização do cliente. | [Despesas do Azure](azure-spending.md)  |
| **Gestão de contas de clientes:** Saiba como fazer muitos aspetos da gestão da conta do cliente, tais como criar e eliminar contas de clientes ou contas de utilizador de um cliente, gerir e validar detalhes da conta do cliente, gerir contas de utilizador e atribuir licenças.  | [Gerir clientes](manage-customers.md)  |
| **Gestão de encomendas:** Saiba todas as formas de gerir programáticamente as encomendas e subscrições dos clientes. Esta área inclui a compra de reservas Azure, criação de encomendas, obtenção de ofertas do catálogo e gestão de ofertas de conversão de ensaios.   | [Gerir encomendas](manage-orders.md)  |
| **Prestação de apoio:** Saiba como administrar serviços para um cliente, como obter ou atualizar os contactos de suporte para uma subscrição e como gerir os pedidos de serviço.  | [Fornecer suporte](provide-support.md)   |
| **Referências:** Saiba como criar uma referência, obter uma lista de referências ou atualizar uma referência.  | [Referências](/partner/develop/referrals)  |
| **Utilidades:** Saiba como validar um endereço, obter regras de formatação de endereços por mercado, verificar a disponibilidade de domínio, eliminar uma conta de cliente da caixa de areia de integração ou obter um registo da atividade do Partner Center. | [Utilitários](utilities.md)  |
| **Segurança:** Saiba mais sobre as APIs REST relacionadas com a autenticação de vários fatores (MFA) no Partner Center. Estas APIs ajudam-no a impor MFA para cada conta de utilizador no seu inquilino parceiro.  | [Estado dos requisitos de segurança dos parceiros](partner-security-requirements.md)  |

## <a name="next-steps"></a>Passos seguintes

- [Ver amostras do Partner Center](partner-center-samples.md)
- [Saiba como começar](get-started.md)