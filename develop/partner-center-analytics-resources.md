---
title: Análise do Centro de Parceiros
description: Partner Center Analytics documentação pública da API.
ms.date: 06/11/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9028d5e2bdeb2637e35133b2c6dda739e0024ccc2838368a5276b1482af78d7f
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997843"
---
# <a name="partner-center-analytics---resources"></a>Análise do Centro de Parceiros – Recursos

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

A API Analytics permite-lhe aceder programaticamente aos dados que estão a ser apresentados na Experiência do Utilizador.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Estes cenários suportam a autenticação apenas com credenciais do Utilizador.

## <a name="csp-program-azure-usage-analytics"></a>Programa CSP: Azure use analytics

O cenário que se segue mostra como utilizar a API analítica para recuperar todas as informações de análise de utilização do Partner Center Azure.

- [Obter todas as informações de análise de utilização do Azure](get-all-azure-usage-analytics.md)

Este cenário devolve a sua informação de análise numa coleção de recursos de uso da [Azure.](#azure-usage-resource)

## <a name="azure-usage-resource"></a>Recurso de utilização azul

Representa todos os dados analíticos para a utilização do Azure.

| Propriedade | Tipo | Description |
|----------|------|-------------|
| CustomerTenantId | string | O identificador do cliente. |
| nome do cliente | string | O nome do cliente. |
| subscriptionId | string | O identificador de assinatura. |
| subscriptionName | string | O nome da assinatura. |
| usageDate | string | A data de utilização. |
| resourceLocation | string | A localização do centro de dados, Europa Ocidental, por exemplo. |
| meterCategory | string | A categoria de contador, gestão de dados, por exemplo. |
| metroSubcategoria | string | A subcategoria do medidor, por exemplo, geo redundante. |
| metrâno | string | A unidade do medidor, como gigabytes ou horas. |
| reservationOrderId | string | A ordem de reserva para uma Azure VM Instância Reservada. |
| reservationId | string | Casos reservados sob uma ordem ri específica. |
| tipo de serviço | string | Indica o tipo de máquina virtual. Por exemplo, Standard_E4s_v3. |
| quantidade | long | Indica os números utilizados na unidade do medidor. |

## <a name="csp-program-indirect-resellers-analytics"></a>Programa CSP: análise de revendedores indiretos

O cenário que se segue mostra-lhe como usar a API analítica para recuperar todas as informações de análise de revendedores indiretos do Seu Partner Center.

- [Obter todas as informações de análise de revendedores indiretos](get-all-indirect-resellers-analytics.md)

Este cenário devolve a sua informação de análise numa coleção de recursos [de revendedores indiretos.](#indirect-resellers-resource)

## <a name="indirect-resellers-resource"></a>Recurso de revendedores indiretos

Representa todos os dados analíticos para revendedores indiretos.

| Propriedade | Tipo | Description |
|----------|------|-------------|
| partnerTenantId | string | A Identificação do Inquilino do parceiro para o qual pretende recuperar dados de revendedores indiretos. |
| ID | string | ID do revendedor indireto. |
| name | string | O Nome do parceiro para o qual pretende recuperar dados de revendedores indiretos. |
| mercado | string | O Mercado do parceiro para o qual pretende recuperar dados de revendedores indiretos. |
| firstSubscriptionCreationDate | cadeia no formato de hora de data UTC | A data de criação da primeira subscrição com base na qual pretende recuperar dados de revendedores indiretos. |
| mais recenteSubscriçãoCreationDate | cadeia no formato de hora de data UTC | A data de criação da última subscrição. |
| firstSubscriptionEndDate | cadeia no formato de hora de data UTC | É a primeira vez que qualquer subscrição foi terminada. |
| mais recenteSubscriçãoEndDate | cadeia no formato de hora de data UTC | Data mais recente quando qualquer subscrição foi terminada. |
| firstSubscriptionSuspendedDate | cadeia no formato de hora de data UTC | É a primeira vez que qualquer assinatura foi suspensa. |
| mais recentesSubscriçãoSuspendedDate | cadeia no formato de hora de data UTC | Data mais recente quando qualquer subscrição foi suspensa. |
| firstSubscriptionDeprovisionedDate | cadeia no formato de hora de data UTC | É a primeira vez que qualquer subscrição foi desprovisionada. |
| mais recentesSsubscriptionDeprovisionedDate | cadeia no formato de hora de data UTC | Data mais recente quando qualquer subscrição foi desprovisionada. |
| subscriçãoCount | double | Contagem de assinaturas para todos os revendedores de valor acrescentado |
| licençaCount | double | Contagem de licenças para todos os revendedores de valor acrescentado |
| indiretResellerCount | double | Contagem de revendedores indiretos |

## <a name="csp-program-subscription-analytics"></a>Programa CSP: análise de subscrição

Os seguintes cenários mostram-lhe como usar a API analítica para recuperar todas as informações de análise de subscrição do Partner Center, filtre-a com uma consulta de pesquisa ou agrupá-la por datas ou termos.

- [Obter todas as informações de análise de subscrições](get-all-subscription-analytics.md)
- [Obter informações de análise de subscrições filtradas por uma consulta de pesquisa](get-subscription-analytics-by-search-query.md)
- [Obter informações de análise de subscrições agrupadas por datas ou termos](get-subscription-analytics-grouped-by-dates-or-terms.md)

Todos estes cenários devolvem a sua informação de análise numa coleção de recursos de [Subscrição.](#subscription-resource)

## <a name="subscription-resource"></a>Recurso de subscrição

Representa todos os dados analíticos para uma subscrição.

|         Propriedade          |              Tipo              |                                                                      Description                                                                       |
|---------------------------|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|     customerTenantId      |             string             |                                              Uma cadeia formatada pelo GUID que identifica o inquilino do cliente.                                              |
|       nome do cliente        |             string             |                                                               O nome do cliente.                                                                |
|      customerMarket       |             string             |                                                 O país/região em que o cliente faz negócios.                                                 |
|            ID             |             string             |                                                              O identificador de assinatura.                                                              |
|          status           |             string             |                                          O estado de subscrição: "ATIVE", "SUSPENDED", ou "DEPROVISIONED".                                           |
|        produtoName        |             string             |                                                                O nome do produto.                                                                |
|     Tipo de subscrição      |             string             |       O tipo de assinatura. **Nota:** Este campo é sensível a casos. Os valores suportados são: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".       |
|     autoRenewEnabled      |            boolean             |                                         Um valor que indica se a subscrição é renovada automaticamente.                                          |
|         partnerId         |             string             | O ID da Microsoft Partner Network (MPN). Para um revendedor direto, este parâmetro será o ID MPN do parceiro. Para um revendedor indireto, este parâmetro será o ID MPN do revendedor indireto. |
|       nome amigável        |             string             |                                                             O nome da assinatura.                                                              |
|        nome parceiro        |             string             |                                              Nome do parceiro para quem a assinatura foi comprada                                               |
|       provedorName        |             string             |            Quando a transação de subscrição é para o revendedor indireto, o nome do fornecedor é o fornecedor indireto que comprou a subscrição.             |
|    effectiveStartDate     | cadeia no formato de hora de data UTC |                                                           A data em que a subscrição começa.                                                            |
|     compromissoEndDate     | cadeia no formato de hora de data UTC |                                                            A data em que a subscrição termina.                                                             |
|    actualStateEndDate    | cadeia no formato de hora de data UTC |                                           A data em que o estado atual da subscrição será alterado.                                            |
| trialToPaidConversionDate | cadeia no formato de hora de data UTC |                                 A data em que a subscrição converte do julgamento para o pagamento. O valor por defeito é nulo.                                 |
|      trialStartDate       | cadeia no formato de hora de data UTC |                                A data em que o período experimental da subscrição começou. O valor por defeito é nulo.                                 |
|       trialEndDate        | cadeia no formato de hora de data UTC |                                  A data em que termina o período experimental para a subscrição termina. O valor por defeito é nulo.                                  |
|       lastUsageDate       | cadeia no formato de hora de data UTC |                                        A data em que a assinatura foi usada pela última vez. O valor por defeito é nulo.                                        |
|     deprovisionedDate     | cadeia no formato de hora de data UTC |                                      A data em que a subscrição foi desprovisionada. O valor por defeito é nulo.                                      |
|      último Aniversário deRenewal      | cadeia no formato de hora de data UTC |                                       A data em que a subscrição foi renovada pela última vez. O valor por defeito é nulo.                                       |
|       licençaCount        |             número             |                                                             O número total de licenças.                                                              |
|     subscriçãoCount     |             número             |                        O número de assinaturas. Nota: Este valor só aparecerá na resposta a uma consulta de agregação.                         |

## <a name="search-analytics"></a>Pesquisar análises

> [!NOTE]
> A adesão ao programa CSP não é necessária para obter análises de pesquisa.

O cenário seguinte mostra-lhe como usar a API analítica para recuperar todas as informações de análise do Seu Centro de Parceiros.

- [Obter todas as informações de análise de pesquisas](get-all-search-analytics.md)

Este cenário devolve a sua informação de análise numa coleção de recursos [de Pesquisa.](#search-resource)

## <a name="search-resource"></a>Recurso de pesquisa

Representa todos os dados analíticos para uma pesquisa.

| Propriedade | Tipo | Description |
|----------|------|-------------|
| nome da empresa | string | O nome da empresa de faturação. |
| contatoButtonClicked | Booleano | Indica se o botão de contacto foi clicado. |
| palavra-chaveCountry | string | O país especificado na busca. |
| detalhesVer-se | Booleano | Indica se os detalhes da pesquisa foram vistos. |
| palavra-chaveIndustryFocus | string | A indústria a procurar dentro, por exemplo, os cuidados de saúde. |
| mpnId | string | O ID da Microsoft Partner Network (MPN). Para um revendedor direto, este parâmetro será o ID MPN do parceiro. Para um revendedor indireto, este parâmetro será o ID MPN do revendedor indireto. |
| partnerMarket | string | Local onde o parceiro conduz negócios. |
| palavra-chavePro | string | O produto especificado na pesquisa. |
| referênciaSubsed | Booleano | Indica se foi submetida uma remessa. |
| searchDate | cadeia no formato de hora de data UTC | Data quando ocorreu a consulta de pesquisa. |
| palavra-chaveSearchText | string | O texto especificado na pesquisa. |
| searchResultPageViews | long | Número de vezes que o parceiro apareceu no resultado da pesquisa. Parte de uma resposta apenas sobre agregação.
| contactClicks | long | Número de vezes que o botão de contacto foi clicado. Parte de uma resposta apenas sobre agregação.
| referenciaçãoCount | long | Número de referências geradas a partir da pesquisa. Parte de uma resposta apenas sobre agregação.
| perfisVers | long | Número de vezes que o perfil do parceiro foi visto. Parte de uma resposta apenas sobre agregação.

## <a name="referrals-analytics"></a>Análise de referências

> [!NOTE]
> A adesão ao programa CSP não é necessária para obter referências analíticas.

O cenário que se segue mostra-lhe como usar a API analítica para recuperar todas as informações de análise do Partner Center.

- [Obter todas as informações de análise de referências](get-all-referrals-analytics.md)

Este cenário devolve a sua informação de análise numa coleção de recursos [de Referências.](#referrals-resource)

> [!NOTE]
> A análise de referências não está disponível para o Centro de Parceiros operado pela 21Vianet.

## <a name="referrals-resource"></a>Recurso de referências

Representa todos os dados analíticos para uma referência.

| Propriedade | Tipo | Descrição |
|----------|------|-------------|
| ID | string | O identificador do cliente.  |
| status | string | Indica se a referência levou a um cliente.  |
| customerMarket | string | O país/região em que o cliente faz negócios. |
| nome do cliente | string | O nome do cliente. |
| customerOrgSize | string | Uma gama que indica o número de colaboradores na organização do cliente. Por exemplo, "10to50employees". |
| aceitoDate | cadeia no formato de hora de data UTC | A data em que a remessa foi aceite. |
| reconheceuDate | cadeia no formato de hora de data UTC | A data em que a referência foi reconhecida. |
| arquivadoDa | cadeia no formato de hora de data UTC | A data em que a referência foi arquivada. |
| recusouDate | cadeia no formato de hora de data UTC | A data em que a referência foi recusada. |
| expiradoDate | cadeia no formato de hora de data UTC | A data em que a referência expirou. |
| LostDate | cadeia no formato de hora de data UTC | A data em que a referência foi perdida. |
| missedDate | cadeia no formato de hora de data UTC | A data em que a referência foi perdida. |
| createdDate | cadeia no formato de hora de data UTC | A data em que a referência foi criada. |
| saltouDate | cadeia no formato de hora de data UTC | A data em que a referência foi ignorada. |
| wonDate | cadeia no formato de hora de data UTC | A data em que a referência foi ganha. |
| partnerMarket | string |  O país/região em que o parceiro opera. |
