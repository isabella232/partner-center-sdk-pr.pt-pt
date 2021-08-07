---
title: Recursos documentais do acordo
description: O recurso AgreementDocument é um documento de acordo da Microsoft para pré-visualização e download. É suportado pelo Partner Center na nuvem pública da Microsoft.
ms.date: 08/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: eddde1e8072c6aeeee814b52f46c7648d870b6ba63c09b20e4270b17f8386383
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991111"
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
