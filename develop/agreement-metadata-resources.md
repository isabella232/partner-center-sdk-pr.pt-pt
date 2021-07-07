---
title: Acordo recursos de metadados
description: A coleção de recursos AgreementMetadata descreve tipos de acordo que os parceiros podem usar para fornecer confirmação da aceitação do cliente.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: b930e3691b9d269ddb8d76ae18b6b26a217123c0
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025636"
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
