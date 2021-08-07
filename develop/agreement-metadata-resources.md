---
title: Acordo recursos de metadados
description: A coleção de recursos AgreementMetadata descreve tipos de acordo que os parceiros podem usar para fornecer confirmação da aceitação do cliente.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 7c09dc2a8dd88e3d3a6a7925f6f61737cbbd410eabda6ecb4c3ead13d889de04
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991264"
---
# <a name="agreement-metadata-resources"></a>Acordo recursos de metadados

**Aplica-se a**: Centro de Parceiros

**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

O recurso **AgreementMetaData** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft. 

A recolha **AgreementMetaData** fornece metadados sobre todos os tipos de contrato. Os parceiros podem usar esta coleção para fornecer a confirmação da aceitação pelo cliente de acordos. A recolha **AgreementMetaData** devolve metadados para ambos os tipos de acordos **(Microsoft Cloud Agreement** e **Microsoft Customer Agreement**).

## <a name="agreementmetadata"></a>AgreementMetaData

Os metadados do acordo devolvidos incluem as seguintes propriedades:

| Propriedade      | Tipo               | Description                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| templateId    | string             | Identificador único de um modelo de acordo.                                       |
| tipo          | string             | Tipo de acordo. Atualmente, os valores suportados incluem **o MicrosoftCloudAgreement** e **o MicrosoftCustomerAgreement** (pré-visualização). |
| agreementLink | string             | URL para o modelo de contrato.                                                    |
