---
title: Acordo recursos de metadados
description: A coleção de recursos AgreementMetadata descreve tipos de acordo que os parceiros podem usar para fornecer confirmação da aceitação do cliente.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 36ba2aa2f78552dc9a835168b5bbd5b6a3ce47f3
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768839"
---
# <a name="agreement-metadata-resources"></a>Acordo recursos de metadados

**Aplica-se a:**

- Partner Center

O recurso **AgreementMetaData** é atualmente suportado pelo Partner Center apenas na nuvem pública da *Microsoft.* Este recurso não é aplicável a:

- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

A recolha **AgreementMetaData** fornece metadados sobre todos os tipos de contrato. Os parceiros podem usar esta coleção para fornecer a confirmação da aceitação pelo cliente de acordos. A recolha **AgreementMetaData** devolve metadados para ambos os tipos de acordos **(Microsoft Cloud Agreement** e **Microsoft Customer Agreement**).

## <a name="agreementmetadata"></a>AgreementMetaData

Os metadados do acordo devolvidos incluem as seguintes propriedades:

| Propriedade      | Tipo               | Descrição                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| templateId    | string             | Identificador único de um modelo de acordo.                                       |
| tipo          | string             | Tipo de acordo. Atualmente, os valores suportados incluem **o MicrosoftCloudAgreement** e **o MicrosoftCustomerAgreement** (pré-visualização). |
| agreementLink | string             | URL para o modelo de contrato.                                                    |
