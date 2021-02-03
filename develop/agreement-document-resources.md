---
title: Recursos documentais do acordo
description: O recurso AgreementDocument é um documento de acordo da Microsoft para pré-visualização e download. É suportado pelo Partner Center na nuvem pública da Microsoft.
ms.date: 08/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 4805d25b0838bf922b81bebd998810c3f6a809c3
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2020
ms.locfileid: "97770028"
---
# <a name="agreement-document-resources-supported-by-partner-center-in-the-microsoft-public-cloud"></a>Recursos documentais do acordo apoiados pelo Partner Center na nuvem pública da Microsoft

**Aplica-se a:**

- Partner Center

O recurso **AgreementDocument** é atualmente suportado pelo Partner Center apenas na nuvem pública da *Microsoft.* Este recurso não é aplicável a:

- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

O recurso **AgreementDocument** representa um documento de acordo da Microsoft que está disponível para pré-visualização e download.

## <a name="agreementdocument"></a>AcordoDocument

Um recurso **AgreementDocument** inclui as seguintes propriedades:

| Propriedade       | Tipo   | Descrição                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| país | string | O país ou o mercado a que este documento se aplica. |
| language | string | A língua em que este documento está localizado. |
| displayUri | string | Um link para pré-visualizar o documento do contrato num browser.  |
| downloadUri |string | Um link para descarregar o documento do contrato (no formato Microsoft Word). |
