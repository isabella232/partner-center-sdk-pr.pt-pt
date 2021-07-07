---
title: Recursos da Entidade de Transferência
description: Um parceiro cria uma transferência quando um cliente quer que a sua subscrição com o parceiro seja transferida para outro parceiro.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 544b9682bb0e1428fad088c818a62492198897b2
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530145"
---
# <a name="transferentity-resources"></a>Recursos da Entidade de Transferência

Um parceiro cria uma transferência quando um cliente quer que a sua subscrição com o parceiro seja transferida para outro parceiro.

## <a name="transferentity"></a>Entidade de Transferência

Descreve uma Entidade de Transferência.

| Propriedade              | Tipo             | Description                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| ID                    | string           | Um identificador de entidade de transferência que é fornecido após a criação bem sucedida da Entidade de Transferência.                               |
| createdTime           | DateTime         | A data em que a Entidade de Transferência foi criada, em formato de data-hora. Aplicada após a criação bem sucedida da Entidade de Transferência.      |
| última Hora DaModified      | DateTime         | A data em que a Entidade de Transferência foi atualizada pela última vez, em formato de data-hora. Aplicada após a criação bem sucedida da Entidade de Transferência. |
| últimoModifiedUser      | string           | O utilizador que atualizou pela última vez a Entidade de Transferência. Aplicada após a criação bem sucedida da Entidade de Transferência.                          |
| nome do cliente          | string           | Opcional. O nome do cliente cujas assinaturas estão a ser transferidas.                                              |
| customerTenantId      | string           | Um id de cliente formatado GUID que identifica o cliente. Aplicada após a criação bem sucedida da Entidade de Transferência.         |
| partnertenantid       | string           | Um parceiro-id formatado GUID que identifica o parceiro.                                                                   |
| fontePartnerName     | string           | Opcional. O nome da organização do parceiro que está a iniciar a transferência.                                           |
| sourcePartnerTenantId | string           | Um parceiro-id formatado GUID que identifica o parceiro que inicia a transferência.                                           |
| targetPartnerName     | string           | Opcional. O nome da organização do parceiro a quem a transferência é dirigida.                                         |
| targetPartnerTenantId | string           | Um parceiro-id formatado GUID que identifica o parceiro a quem a transferência é alvo.                                  |
| lineitems             | Matriz de objetos | Uma matriz de recursos [TransferLineItem.](#transferlineitem)                                                   |
| status                | string           | O estado da Entidade de Transferência. Os valores possíveis são "Ative" (pode ser eliminado/submetido) e "Concluído" (já foi concluído). Aplicada após a criação bem sucedida da Entidade de Transferência.|

## <a name="transferlineitem"></a>TransferLineItem

Representa um item contido numa Entidade de Transferência.

| Propriedade             | Tipo                             | Description                                                                                             |
|----------------------|----------------------------------|---------------------------------------------------------------------------------------------------------|
| ID                   | string                           | Um identificador único para um item de linha de transferência. Aplicada após a criação bem sucedida da Entidade de Transferência.   |
| subscriptionId       | string                           | O identificador de assinatura.                                                                            |
| quantidade             | int                              | O número de licenças ou instâncias.                                                                    |
| billingCycle         | Objeto                           | O tipo de ciclo de faturação definido para o período atual.                                                   |
| nome amigável         | string                           | Opcional. O nome amigável para o item definido pelo parceiro para ajudar a desambiguar.                   |
| partnerIdOnRecord    | string                           | PartnerId on Record (MPNID) sobre a compra que acontece quando a transferência é aceite.                 |
| offerId              | string                           | O identificador da oferta.    |
| addonItems           | Lista de objetos **TransferLineItem** | Uma recolha de itens de linha da TransferEntity para addons que serão transferidos juntamente com a subscrição base que está a ser transferida. Aplicada após a criação bem sucedida da Entidade de Transferência.|
| transferEror        | string                           | Aplicada após transferência A Entidade é aceite em caso de erro.                |
| status               | string           | O estado do lineitem na Entidade de Transferência.|

## <a name="transfersubmitresult"></a>TransferSubmitResult

Representa o resultado de uma aceitação de transferência.

| Propriedade          | Tipo                                                  | Description                        |
|-------------------|-------------------------------------------------------|------------------------------------|
| encomendas            | Lista de objetos [da Ordem.](order-resources.md#order)    | A coleção de ordens.          |
| transeuntes    | Lista de objetos [TransferError.](#transfererror)      | A recolha de erros de transferência. |

## <a name="transfererror"></a>TransferEror

Representa um erro que ocorre quando uma transferência é aceite.

| Propriedade          | Tipo   | Description                                     |
|-------------------|--------|-------------------------------------------------|
| transferGroupId   | string | O grupo de pedidos identificação da ordem com o erro. |
| code              | int    | O código de erro.                                 |
| descrição       | string | A descrição do erro.                   |
| lineitems         | Lista de objetos **TransferLineItem** | Uma recolha de itens de linha da entidade de transferência que fazem parte do erro de transferência.|

## <a name="transfererrorcode"></a>TransferErorCode

Um [Enum/dotnet/api/system.enum) com valores que indicam um tipo de erro de ordem.

| Valor | Posição | Description |
| --- | --- | --- |
| PartnerTokenMissing | 800001 | Parceiro Token desaparecido no contexto do pedido. |
| Inválido | 800002 | Entrada de pedido inválido. |
| ServiçoExcepção | 800003 | Erro de serviço inesperado. |
| InvalidOfferId | 800004 | ID de oferta inválida. |
| CriarOrderror | 800005 | Criar ordem não é bem sucedido. |
| MpnIdNotFound | 800015 | A identificação da MPN não foi encontrada. |
| NotValidIndirectResellerMpnId | 800016 | O MPN ID não é um Revendedor Indireto válido. |
| TransferIdNotFound | 900100   | Pedido de transferência não encontrado.   |
| TransferNotAllowedIfStatusIsInProgress | 900101 | O pedido de transferência já está em curso.|
| TransferNotAllowedIfStatusIsCompleted | 900102 | O pedido de transferência já está completo.|
| TransferCreateOrderror | 900103 | A ordem de transferência não é bem sucedida.|
| TransferProcessedByAnotherRequest | 900104 | A transferência está a ser processada por outro pedido.|