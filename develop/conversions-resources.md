---
title: Recursos de conversão
description: Saiba como utilizar os recursos de conversão de API do Partner Center para ajudá-lo a converter uma subscrição experimental para uma subscrição paga.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9e7f8985fa15f4959f3cb5a729e492bbb9f3f624a5812f5b87fc119f841dc87e
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991876"
---
# <a name="conversion-resources-to-convert-trial-subscriptions-to-paid"></a>Recursos de conversão para converter assinaturas de ensaio para pagos

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Os recursos de conversão suportam a conversão de uma subscrição experimental para uma subscrição paga.

## <a name="conversion"></a>Conversão

Contém informações usadas para converter uma subscrição experimental para uma subscrição paga.

| Propriedade | Tipo | Description |
| -------- | ---- | ----------- |
| offerId | string | O identificador de oferta da oferta original, a oferta experimental. |
| targetOfferId | string | O identificador de oferta para a oferta alvo. |
| orderId | string | O identificador da ordem. |
| quantidade | int | O número de licenças. O padrão é o número de licenças na subscrição de ensaio. |
| billingCycle | string | Indica a frequência com que o parceiro é cobrado para a subscrição. Valores possíveis: **Mensalmente** (o parceiro é faturado mensalmente), **Anual** (o parceiro é faturado anualmente) ou **Nenhum** (Parceiro não é cobrado. Usado para assinaturas de teste). |

## <a name="conversionerror"></a>ConversorEror

Representa um erro ocorrido durante a conversão.

| Propriedade | Tipo | Description |
| -------- | ---- | ----------- |
| code | string | O código de erro associado ao problema. Valores possíveis: **Outros** (erro geral), **ConversõesNotFound** (não é possível encontrar conversões para a subscrição experimental para converter).
| descrição | string | O texto amigável que descreve a questão. |

## <a name="conversionresult"></a>ConversãoResult

Representa o resultado da realização de uma conversão de subscrição.

| Propriedade       | Tipo                                | Description                                                            |
|----------------|-------------------------------------|------------------------------------------------------------------------|
| subscriptionId | string                              | O identificador de assinatura.                                           |
| offerId        | string                              | O identificador de oferta original.                                         |
| targetOfferId  | string                              | O identificador de oferta para a oferta alvo.                             |
| erro          | [ConversorEror](#conversionerror) | O erro encontrado durante a tentativa de conversão, se aplicável. |