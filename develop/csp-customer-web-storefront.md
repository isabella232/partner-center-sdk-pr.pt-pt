---
title: Loja Web para clientes CSP
description: Este código do site da amostra mostra uma loja online funcionando para os clientes comprarem subscrições de produtos Microsoft.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 07020c365db2ad578e7ff75602519d06eabb2a3bebf0913899fcd8b5345a0365
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115995208"
---
# <a name="csp-customer-web-storefront"></a>Loja Web para clientes CSP

**Aplica-se a**: Centro de Parceiros

**Não se aplica a**: Partner Center for Microsoft Cloud Germany | Centro de Parceiros para Microsoft Cloud for US Government

Esta aplicação de amostra aplica-se apenas à instância global do Partner Center.

A [loja Partner Center](https://github.com/Microsoft/Partner-Center-Storefront) é um site de **amostras** para uma loja online que os clientes podem usar para comprar subscrições de produtos microsoft. Pode modificar este **código de amostra** para seu próprio uso para [configurar as ofertas,](#configure-offers) [adicionar branding,](#configure-branding)e [adicionar um método de pagamento](#configure-payment-types).

## <a name="sample-code"></a>Código de exemplo

Descarregue o código de amostra da [loja Partner Center](https://github.com/Microsoft/Partner-Center-Storefront) a partir de GitHub.

## <a name="configure-authentication"></a>Configurar a autenticação

Antes de construir a aplicação, atualize os seguintes valores no ficheiro Web.config para refletir a informação de autenticação AD AZure que criou na [autenticação do Partner Center.](partner-center-authentication.md) Deve utilizar as definições da sua conta de caixa de areia de integração durante o desenvolvimento precoce ou para testes em produção (TiP).

- **partnerCenter.applicationD**
- **partnerCenter.applicationSecret**
- **partnerCenter.domain**
- **webPortal.clientId**
- **webPortal.clientSecret**
- **webPortal.domínio**
- **webPortal.azureStorageConnectionString**

## <a name="configure-offers"></a>Configure ofertas

Pode configurar o conjunto de ofertas **(MicrosoftOffer)** no **OfferCatalogViewModel**.

## <a name="configure-branding"></a>Configurar a marca

Este site de amostras rastreia as seguintes informações da empresa e da marca em *BrandingConfiguration.cs* e *PortalBranding.cs*:

- Nome da organização
- Logotipo da organização
- Imagem de cabeçalho
- Acordo de privacidade
- E-mail de contacto
- Número de telefone de contato
- E-mail de apoio
- Número de telefone de suporte

### <a name="configure-payment-types"></a>Configurar tipos de pagamento

A aplicação utiliza atualmente um gateway PayPal, implementado no *PayPalGateway.cs*.