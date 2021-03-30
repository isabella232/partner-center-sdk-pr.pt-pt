---
title: Recursos de fatura
description: Vários recursos relacionados com a fatura estão disponíveis através das APIs do Partner Center. Estes recursos estão relacionados com detalhes de fatura e item de linha.
ms.date: 01/27/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8977b3b649cd930bb517965572d0efe51d6985a0
ms.sourcegitcommit: 4ec053c56fd210b174fe657aa7b86faf4e2b5a7c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/29/2021
ms.locfileid: "105730217"
---
# <a name="invoice-resources"></a>Recursos de fatura

**Aplica-se a:**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

Os seguintes recursos relacionados com a fatura estão disponíveis através das APIs do Partner Center.

## <a name="invoice"></a>Fatura

| Propriedade | Tipo | Descrição |
| -------- | ---- | ----------- |
| ID | string | O identificador de fatura. |
| faturaDate | cadeia no formato de data-hora UTC | A data em que a fatura foi gerada. |
| billingPeriodStartDate | cadeia no formato de data-hora UTC | Data de início do período de faturação na UTC. |
| billingPeriodEndDate | cadeia no formato de data-hora UTC   | Data de fim do período de faturação na UTC. |
| totalAlis | número | Os encargos totais. Inclui encargos para transações e eventuais ajustes.     |
| paidAmount | número  | O valor pago pelo sócio. Negativo se um pagamento foi recebido.  |
| currencyCode | string  | Um código que indica a moeda utilizada para todos os valores e totais de fatura. |
| moedaSymbol  | string | O símbolo de moeda utilizado para todos os valores e totais de artigos de fatura. |
| pdfDownloadLink | string  | Um link para descarregar a fatura em formato PDF. Este link não é devolvido como parte dos resultados da pesquisa, e só é povoado se a fatura for acedida por ID. Esta ligação expira automaticamente em 30 minutos. |
| faturaDetails  | matriz de objetos [FaturaDetail](#invoicedetail)  | Os detalhes da fatura.  |
| alterações      | matriz de objetos [de fatura](#invoice)   | As alterações a esta fatura.  |
| documentoType    | string | O tipo de documento da fatura: "Nota de crédito", "Fatura". |
| alteraçõesOf        | string | O número de referência do documento de que este documento é uma alteração.  |
| faturaType     | string  | O tipo de fatura: "recorrente", "uma \_ vez".   |
| ligações           | [RecursosLinks](utility-resources.md#resourcelinks)  | Os recursos ligam-se.  |
| atributos      | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.  |

## <a name="invoicedetail"></a>FaturaDetail

Uma fatura contém uma coleção de itens faturados, e cada item é representado por um recurso FaturaDetail.

| Propriedade            | Tipo                                                           | Descrição                                                                       |
|---------------------|----------------------------------------------------------------|-----------------------------------------------------------------------------------|
| faturaLineItemType | string                                                         | O tipo de detalhe da fatura: "nenhum", \_ \_ "itens de linha de utilização", "itens de linha de \_ faturação". \_ |
| faturaçãoProvider     | string                                                         | O fornecedor de faturação: "nenhum", "escritório", "azul" ou "mercado de \_ dados \_ azure".         |
| ligações               | [RecursosLinks](utility-resources.md#resourcelinks)           | Os recursos ligam-se.                                                               |
| atributos          | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                                          |

## <a name="invoicelineitem"></a>FaturaLineItem

Cada carga individual dentro de uma fatura é representada como um InvoiceLineItem.

| Propriedade            | Tipo                                                           | Descrição                                                                          |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| faturaLineItemType | string                                                         | O tipo de rubrica de fatura: "nenhum", \_ \_ "itens de linha de utilização", "itens de linha de \_ faturação". \_ |
| faturaçãoProvider     | string                                                         | O fornecedor de faturação: "nenhum", "escritório", "azul" ou "mercado de \_ dados \_ azure".            |
| atributos          | [RecursosTributos](utility-resources.md#resourceattributes) | Os atributos dos metadados.                                                             |

## <a name="invoicesummary"></a>FaturaSummary

Descreve um resumo do saldo e os encargos totais de uma fatura.

| Propriedade                 | Tipo                                                           | Descrição                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| balanceAmonte            | número                                                         | O saldo da fatura. Este é o montante total de contas não pagas. |
| currencyCode             | string                                                         | Um código que indica a moeda utilizada para o valor do saldo.       |
| moedaSymbol           | string                                                         | O símbolo da moeda usado.                                             |
| contabilidadeDamente           | cadeia no formato de data-hora UTC                                 | A data em que o saldo foi atualizado pela última vez.                         |
| firstInvoiceCreationDate | cadeia no formato de data-hora UTC                                 | A data em que foi criada a primeira fatura do cliente.              |
| último PagamentoDate          | cadeia no formato de data-hora UTC                                 | A data do último pagamento.                                         |
| lastPaymentAmount        | número                                                         | O valor do último pagamento.                                       |
| mais recenteInvoiceDate        | cadeia no formato de data-hora UTC                                 | A data da última fatura do cliente foi criada.               |
| detalhes                  | matriz de [objetos FaturaSummaryDetail](#invoicesummarydetail) | O resumo da fatura.                                           |
| ligações                    | [RecursosLinks](utility-resources.md#resourcelinks)            | Os recursos ligam-se.                                                   |
| atributos               | [RecursosTributos](utility-resources.md#resourceattributes)  | Os atributos dos metadados.                                              |

## <a name="invoicesummarydetail"></a>FaturaSummaryDetail

Represente um resumo dos detalhes individuais para um tipo de fatura (por exemplo, recorrente, uma \_ vez).

| Propriedade            | Tipo                                                           | Descrição                                                                          |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| faturaType         | string                                                         | O tipo de fatura: "recorrente", "uma \_ vez".                                       |
| resumo             | [Objeto de faturaSummary](#invoicesummary)                       | O resumo da fatura por tipo de fatura.                                         |

## <a name="invoicesummaries"></a>FaturaSumatários

Represente uma coleção do tipo [FaturaSummary](#invoicesummary) que contenha os detalhes individuais de um tipo de fatura por moeda.

| Propriedade            | Tipo                                                           | Descrição                                                                          |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| collectionOfSummary | matriz de [objetos de faturaSummary](#invoicesummary)             | O resumo da fatura por tipo de fatura por moeda.                            |

## <a name="licensebasedlineitem"></a>LicenseBasedLineItem

Representa um item de linha de faturação para subscrições licenciadas.

| Propriedade                 | Tipo                                                           | Descrição                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| quantidade                   | string                                                         | Recebe ou define o valor total. Quantidade total = preço unitário * quantidade.  |
| atributos               | string                                                         | Obtém os atributos.                                                  |
| billingCycleType         | string                                                         | Recebe ou define o tipo de ciclo de faturação.                                  |
| faturaçãoProvider          | string                                                         | Fica com o fornecedor de faturação.                                            |
| chargeEndDate            | cadeia no formato de data-hora UTC                                 | Obtém ou define a data de fim para a cobrança.                             |
| chargeStartDate          | cadeia no formato de data-hora UTC                                 | Obtém ou define a data de início para a cobrança.                           |
| chargeType               | string                                                         | Recebe ou define o tipo de carga.                                      |
| moeda                 | string                                                         | Obtém ou define a moeda utilizada para este item de linha.                    |
| customerId               | string                                                         | Obtém ou define o identificador exclusivo do cliente na plataforma de faturação da Microsoft.  |
| nome do cliente             | cadeia no formato de data-hora UTC                                 | Recebe ou define o nome do cliente.                                       |
| domínioName               | string                                                         | Obtém ou define o nome de domínio.                                             |
| DurableOfferId           | string                                                         | Recebe ou define o identificador único de oferta durável.                     |
| faturaLineItemType      | string                                                         | Obtém o tipo de item da linha de fatura.                                   |
| mpnId                    | número                                                         | Obtém ou define o ID MPN associado a este item de linha. Para revendedores diretos, este é o ID MPN do revendedor. Para revendedores indiretos, este é o ID MPN do Revendedor de Valor Acrescentado (VAR).                                   |
| offerId                  | string                                                         | Recebe ou define a oferta identificador único.                             |
| oferecerName                | string                                                         | Recebe ou define o nome da oferta.                                          |
| orderId                  | string                                                         | Recebe ou define o identificador único da ordem.                             |
| partnerId                | string                                                         | Recebe ou define o parceiro Azure ative directy iD do inquilino.            |
| quantidade                 | número                                                         | Obtém ou define o número de unidades associadas a este item de linha.      |
| subscriçãoDescrição  | string                                                         | Obtém ou define a descrição da subscrição.                            |
| subscriçãoEndDate      | cadeia no formato de data-hora UTC                                 | Obtém ou define a data quando a subscrição expirar.                      |
| subscriptionId           | string                                                         | Recebe ou define o identificador exclusivo de subscrição.                      |
| subscriptionName         | string                                                         | Recebe ou define o nome da subscrição.                                   |
| subscriçãoStartDate    | cadeia no formato de data-hora UTC                                 | Obtém ou define a data quando a subscrição começa.                   |
| subtotal                 | número                                                         | Recebe ou define o valor após desconto.                               |
| sindicalizaçãoPartnerSubscriptionNumber | string                                             | Obtém ou define o número de subscrição do parceiro de sindicalização.             |
| imposto                      | número                                                         | Recebe ou define os impostos cobrados.                                       |
| tier2MpnId               | número                                                         | Obtém ou define o ID MPN do parceiro Tier 2 associado a este item de linha. |
| totalForCustomer         | número                                                         | Recebe ou define o valor total após desconto e imposto.                 |
| totalOtherDiscount       | número                                                         | Obtém ou define o desconto associado a esta compra.              |
| unitPrice                | número                                                         | Recebe ou define o preço unitário.                                          |

## <a name="usagebasedlineitem"></a>UsageBasedLineItem

Representa um item de linha de faturação para subscrições baseadas em uso.

| Propriedade                 | Tipo                                                           | Descrição                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| atributos               | string                                                         | Obtém os atributos.                                                  |
| billingCycleType         | string                                                         | Recebe ou define o tipo de ciclo de faturação.                                  |
| faturaçãoProvider          | string                                                         | Fica com o fornecedor de faturação.                                            |
| chargeEndDate            | cadeia no formato de data-hora UTC                                 | Obtém ou define a data de fim para a cobrança.                             |
| chargeStartDate          | cadeia no formato de data-hora UTC                                 | Obtém ou define a data de início para a cobrança.                           |
| chargeType               | string                                                         | Recebe ou define o tipo de carga.                                      |
| consumedQuantity         | número                                                         | Recebe ou define o total de unidades consumidas.                                |
| consumoSeconse de conta      | string                                                         | Recebe ou define o desconto no consumo.                             |
| consumoPrir         | string                                                         | Obtém ou define o preço da quantidade consumida.                          |
| moeda                 | string                                                         | Obtém ou define a moeda associada aos preços.                 |
| nome do cliente             | string                                                         | Recebe ou define o nome do cliente.                                       |
| customerId               | string                                                         | Recebe ou define o identificador único do cliente.                          |
| detalheLineItemId         | número                                                         | Obtém ou define o ID da linha de detalhe. Identifica exclusivamente os itens de linha para casos em que o cálculo é diferente para as unidades consumidas. Exemplo: Total consumido = 1338, 1024 é cobrado com uma taxa, 314 é cobrado com uma taxa diferente.        |
| domínioName               | string                                                         | Obtém ou define o nome de domínio.                                             |
| includedQuantity         | número                                                         | Recebe ou define as unidades incluídas na encomenda.                         |
| faturaLineItemType      | string                                                         | Obtém o tipo de item da linha de fatura.                                   |
| faturaNumber            | string                                                         | Recebe ou define o número da fatura.                                      |
| listPrice                | número                                                         | Obtém ou define o preço de cada unidade.                                  |
| mpnId                    | número                                                         | Obtém ou define o ID MPN associado a este item de linha. Para revendedores diretos, este é o ID MPN do revendedor. Para revendedores indiretos, este é o ID MPN do Revendedor de Valor Acrescentado (VAR).                                   |
| orderId                  | string                                                         | Recebe ou define o identificador único da ordem.                             |
| overageQuantity          | número                                                         | Obtém ou define a quantidade consumida acima permitida.               |
| partnerBillableAccountId | string                                                         | Obtém ou define a identificação da conta de faturação do parceiro.                         |
| partnerId                | string                                                         | Recebe ou define o parceiro Azure ative directy iD do inquilino.            |
| nome parceiro              | string                                                         | Recebe ou define o nome do parceiro.                                      |
| pósTaxEffectiveRate     | número                                                         | Obtém ou define o preço efetivo após os impostos.                         |
| postTaxTotal             | número                                                         | Recebe ou define os encargos totais após impostos. Encargos antes de impostos + montante fiscal |
| préTaxCharges            | número                                                         | Recebe ou define o preço cobrado antes de impostos.                          |
| preTaxEffectiveRate      | número                                                         | Obtém ou define o preço efetivo antes dos impostos.                        |
| region                   | string                                                         | Obtém ou define a região associada à instância de recursos.        |
| recursosGuid             | string                                                         | Obtém ou define o identificador de recursos.                                 |
| resourceName             | string                                                         | Recebe ou define o nome do recurso. Exemplo: Base de dados (GB/mês).         |
| nome de serviço              | string                                                         | Recebe ou define o nome de serviço. Exemplo: Serviço de Dados Azure.           |
| tipo de serviço              | string                                                         | Recebe ou define o tipo de serviço. Exemplo: Azure SQL Azure DB.           |
| sku                      | string                                                         | Recebe ou define o serviço SKU.                                         |
| subscriçãoDescrição  | string                                                         | Obtém ou define a descrição da subscrição.                            |
| subscriptionId           | string                                                         | Recebe ou define o identificador exclusivo de subscrição.                      |
| subscriptionName         | string                                                         | Recebe ou define o nome da subscrição.                                   |
| taxAmount                | número                                                         | Recebe ou define o montante do imposto cobrado.                               |
| tier2MpnId               | número                                                         | Obtém ou define o ID MPN do parceiro Tier 2 associado a este item de linha. |
| unit                     | string                                                         | Obtém ou define a unidade de medida para a utilização do Azure.                     |

## <a name="invoicestatement"></a>Declaração de Fatura

Representa as operações disponíveis numa declaração de fatura em aplicação/pdf.

| Propriedade                 | Tipo                                                           | Descrição                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| httpResponseMessage      | objeto                                                         | ByteArrayContent com conteúdoType = aplicação/pdf.                  |

## <a name="onetimeinvoicelineitem"></a>OneTimeInvoiceLineItem

Representa um item de linha de faturação para subscrições licenciadas.

| Propriedade | Tipo | Descrição |
| --- | --- | --- |
| PartnerId | string | Recebe ou define a identificação do inquilino sócio. |
| CustomerId | string | Recebe ou define a identificação do inquilino do cliente. |
| CustomerName | string | Recebe ou define o nome do cliente. |
| Nome do Nome do Cliente | string | Obtém ou define o nome de domínio do cliente. |
| CustomerCountry | string | Recebe ou define o país do cliente. |
| FaturaNumber | string | Recebe ou define o número da fatura. |
| MpnId | string | Obtém ou define o ID MPN associado a este item de linha. |
| RevendedorMpnId | int | Recebe ou define o identificador único da ordem. |
| OrderDate | DateTime | Obtém ou define a data quando a encomenda foi criada. |
| ProductId | string | Recebe ou define o identificador único do produto. |
| SkuId | string | Recebe ou define o identificador único SKU. |
| DisponibilidadeyId | string | Obtém ou define o identificador único de disponibilidade. |
| NomeDoProduto | string | Recebe ou define o nome do produto. |
| SkuName | string | Recebe ou define o nome SKU. |
| ChargeType | string | Recebe ou define o tipo de carga. |
| UnitPrice | decimal | Recebe ou define o preço unitário. |
| EffectiveUnitPrice | decimal | Obtém ou define o preço unitário eficaz. |
| UnitType | string | Recebe ou define o tipo de unidade. |
| Quantidade | int | Obtém ou define o número de unidades associadas a este item de linha. |
| Subtotal | decimal | Recebe ou define o valor após desconto. |
| ImpostoTotal | decimal | Recebe ou define os impostos cobrados. |
| TotalForCustomer | decimal | Recebe ou define o valor total após desconto e imposto. |
| Moeda | string | Obtém ou define a moeda utilizada para este item de linha. |
| Nome do Editor | string | Obtém ou define o nome da editora associado a esta compra. |
| PublisherId | string | Obtém ou define o ID da editora associado a esta compra. |
| AssinaturaDescrição | string | Obtém ou define a descrição da subscrição associada a esta compra. |
| SubscriptionId | string | Obtém ou define o ID de subscrição associado a esta compra. |
| ChargeStartDate | DateTime | Obtém ou define a data de início de carregamento associada a esta compra. |
| ChargeEndDate | DateTime | Obtém ou define a data de fim de carregamento associada a esta compra. |
| TermAndBillingCycle | string | Obtém ou define o termo e ciclo de faturação associado a esta compra. |
| AlternateId | string | Obtém ou define o ID alternativo (ID de cotação). |
| PreçoDjustmentDescription | string | Obtém ou define a descrição do ajustamento de preço. |
| Código CreditReason | string | Recebe ou define o código de razão de crédito. |
| DescontoDesta | string |  **Precotado.** Obtém ou define os detalhes de desconto associados a esta compra. |
| PricingCurrency | string | Recebe ou define o código da moeda de preços. |
| PCToBCExchangeRate | decimal | Obtém ou define a moeda de fixação para a taxa de câmbio da moeda de faturação. |
| PCToBCExchangeRateDate | DateTime | Obtém ou define a data da taxa de câmbio em que foi determinada a moeda de fixação à taxa de câmbio de faturação. |
| BillableQuantity | decimal | Recebe ou define as unidades compradas. Para cada coluna de design chamada **BillableQuantity**. |
| Descrição do Medidor | string | Obtém ou define a descrição do medidor para o item da linha de consumo. |
| ReservationOrderId | string | Recebe ou define o identificador de pedido de reserva para uma Compra Azure RI. |
| BillingFrequency | string | Recebe ou define a frequência de faturação. |
| FaturaLineItemType | FaturaLineItemType | Devolve o tipo de artigo da linha de fatura. |
| BillingProvider | BillingProvider | Devolve o fornecedor de faturação. |

## <a name="dailyratedusagelineitem"></a>DailyRatedUsageLineItem

Representa itens de linha de reconciliação não faturados para uso avaliado diário.

| Propriedade | Tipo | Descrição |
| --- | --- | --- |
| PartnerId | string | Recebe ou define a identificação do inquilino sócio. |
| PartnerName | string | Recebe ou define o nome do parceiro. |
| CustomerId | string | Obtém ou define a identificação do inquilino do cliente a que o uso pertence. |
| CustomerName | string | Obtém ou define o nome da empresa cliente a que o uso pertence. |
| Nome do Nome do Cliente | string | Obtém ou define o nome de domínio do cliente a que o uso pertence. |
| FaturaNumber | string | Obtém ou define o ID da fatura a que o uso pertence. |
| ProductId | string | Recebe ou define o identificador único do produto. |
| SkuId | string | Recebe ou define o identificador único SKU. |
| DisponibilidadeyId | string | Obtém ou define o identificador único de disponibilidade. |
| SkuName | string | Recebe ou define o nome SKU para o serviço. |
| NomeDoProduto | string | Recebe ou define o nome do produto. |
| Nome do Editor | string | Recebe ou define o nome do editor. |
| PublisherId | string | Obtém ou define a identificação da editora. |
| SubscriptionId | string | Obtém ou define o ID de assinatura. |
| AssinaturaDescrição | string | Obtém ou define a descrição da subscrição. |
| ChargeStartDate | DateTime | Recebe ou define a data de início da carga. |
| ChargeEndDate | DateTime | Recebe ou define a data de fim da carga. |
| UsageDate | DateTime | Obtém ou define a data de utilização. |
| Medidor deTipo | string | Recebe ou define o tipo de medidor. |
| MeterCategory | string | Recebe ou define a categoria do medidor. |
| MeterId | string | Recebe ou define o ID do medidor (GUID). |
| MeterSubCategory | string | Obtém ou define a subcategoria do medidor. |
| MeterName | string | Recebe ou define o nome do medidor. |
| MeterRegion | string | Recebe ou define a região do medidor. |
| UnitOfMeasure | string | Recebe ou define a unidade de medida. |
| ResourceLocation | string | Obtém ou define a localização do recurso. |
| ConsumedService | string | Recebe ou define o nome de serviço consumido. |
| ResourceGroup | string | Recebe ou define o nome do grupo de recursos. |
| RecursosUri | string | Obtém ou define o uri da instância de recursos que o uso é sobre. |
| Etiquetas | string | Recebe ou define as etiquetas adicionadas ao cliente. |
| AdditionalInfo | string | Obtém ou define os metadados específicos do serviço. Por exemplo, um tipo de imagem de uma máquina virtual. |
| ServiceInfo1 | string | Obtém ou define metadados internos do Serviço Azure. |
| ServiceInfo2 | string | Obtém ou define informações de serviço, por exemplo, um tipo de imagem para uma máquina virtual e o nome ISP para ExpressRoute. |
| CustomerCountry | string | Recebe ou define o país do cliente. |
| MpnId | string | Obtém ou define o ID MPN associado a este item de linha. |
| RevendedorMpnId | string | Obtém ou define o ID MPN do parceiro de nível 2 associado a este item de linha. |
| ChargeType | string | Recebe ou define o tipo de carga. |
| UnitPrice | decimal | Recebe ou define o preço da unidade. |
| Quantidade | decimal | Obtém ou define a quantidade de utilização. |
| UnitType | string | Recebe ou define o tipo de unidade (por exemplo, 1 hora). |
| BillingPreTaxTotal | decimal | Obtém ou define o custo alargado ou o custo total antes de impostos em moeda local do cliente ou moeda de faturação. |
| BillingCurrency | string | Obtém ou define a moeda ISO na qual o contador é cobrado em moeda local do cliente ou moeda de faturação. |
| PreçosPreTaxTotal | decimal | Obtém ou define o custo alargado ou o custo total antes de impostos em USD ou moeda de catálogo usada para classificação. |
| PricingCurrency | string | Obtém ou define a moeda ISO na qual o contador é cobrado em USD ou moeda de catálogo usada para classificação. |
| Direitodid | string | Obtém ou define o direito (subscrição Azure) ID. |
| DireitosDescrição | string | Obtém ou define a descrição do direito (subscrição Azure). |
| PCToBCExchangeRate | string | Obtém ou define a moeda de fixação para a taxa de câmbio da moeda de faturação. |
| PCToBCExchangeRateDate | DateTime | Obtém ou define a moeda de preços para a data da taxa de câmbio da faturação. |
| EffectiveUnitPrice | decimal | Obtém ou define o preço unitário eficaz. |
| TaxaOfPartnerEarnedCredit | decimal | Obtém ou define a taxa de crédito do parceiro. |
| HasPartnerEarnedCredit | bool | Gets ou sets é parceiro obtido crédito aplicado. |
| TaxaOfCredit | decimal | Obtém ou define a taxa de crédito para o tipo de crédito dado. |
| CréditoType | string | Recebe ou define o tipo de crédito. |
| FaturaLineItemType | FaturaLineItemType | Devolve o tipo de artigo da linha de fatura. |
| BillingProvider | BillingProvider | Devolve o fornecedor de faturação. |
