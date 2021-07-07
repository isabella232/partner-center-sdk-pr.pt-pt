---
title: Recursos documentais do acordo
description: O recurso AgreementDocument é um documento de acordo da Microsoft para pré-visualização e download. É suportado pelo Partner Center na nuvem pública da Microsoft.
ms.date: 08/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 1a81da4f75594f241669db831125bd437872561c
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025671"
---
# <a name="agreement-document-resources-supported-by-partner-center-in-the-microsoft-public-cloud"></a>Recursos documentais do acordo apoiados pelo Partner Center na nuvem pública da Microsoft

**Aplica-se a**: Centro de Parceiros

**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

O recurso **AgreementDocument** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.

O recurso **AgreementDocument** representa um documento de acordo da Microsoft que está disponível para pré-visualização e download.

## <a name="agreementdocument"></a>AcordoDocument

Um recurso **AgreementDocument** inclui as seguintes propriedades:

| Propriedade       | Tipo   | Description                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| país | string | O país ou o mercado a que este documento se aplica. |
| language | string | A língua em que este documento está localizado. |
| displayUri | string | Um link para pré-visualizar o documento do contrato num browser.  |
| downloadUri |string | Um link para descarregar o documento do contrato (em formato Microsoft Word). |
