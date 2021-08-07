---
title: Introdução
description: O Partner Center SDK inclui uma API gerida e uma API REST para os parceiros usarem para gerir dados de clientes, subscrição e encomenda.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 340b46978d71bdf5fa6f6795d69fe0721d808c4eb2650744e82510c208dd5b8f
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989700"
---
# <a name="get-started"></a>Introdução

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

O Partner Center SDK inclui uma API gerida e uma API REST para os parceiros usarem para gerir dados de clientes, subscrição e encomenda.

## <a name="get-the-code"></a>Obter o código

[Descarregue o Partner Center SDK](https://go.microsoft.com/fwlink/p/?LinkId=746681)

> [!NOTE]
> O acesso da API ao Partner Center para revendedores indiretos não é um cenário suportado.

## <a name="determine-your-version-of-partner-center"></a>Determine a sua versão do Partner Center

Algumas versões do Partner Center não têm todo o SDK disponível. Para obter mais informações, consulte [Developing for Partner Center for Microsoft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md).

## <a name="get-the-samples"></a>Pegue as amostras

Para obter mais informações sobre os snippets C#, amostras DE REST e a aplicação da amostra, consulte [as amostras do Partner Center](partner-center-samples.md).

## <a name="test-vs-production"></a>Teste vs. produção

Enquanto está inicialmente a escrever e a testar o seu código, deverá utilizar a sua conta de caixa de areia de integração (e os tokens correspondentes) para que não incorre acidentalmente em novas taxas que a sua empresa é responsável pelo pagamento. Para obter mais informações sobre este ambiente de teste, consulte [Configurar o acesso a API no Partner Center.](set-up-api-access-in-partner-center.md)

Quando a sua solução for testada e pronta a ser utilizada em contas reais de clientes, terá de atualizar as suas fichas para que esteja a utilizar uma aplicação de cliente AD Azure e segredo que corresponda à sua conta do Centro de Parceiros Primários.

Para obter dicas e sugestões sobre testes e depurações, incluindo mais informações sobre o Test-in-Production (TiP) e a Caixa de Areia integração, consulte [Teste e depuragem](test-and-debug.md).

## <a name="configure-your-authentication"></a>Configure a sua autenticação

Para configurar a sua autenticação AZure AD para que possa utilizar as APIs do Centro Parceiro, consulte a [autenticação do Partner Center](partner-center-authentication.md).

> [!IMPORTANT]
> A Microsoft está a introduzir um quadro seguro e escalável para autenticar parceiros de soluções de nuvem (CSP) e fornecedores de painéis de controlo (CPV) através da arquitetura de autenticação de vários fatores Microsoft Azure (MFA).
O Partner Center utiliza o Azure AD para autenticação e para utilizar as APIs do Centro De Parceiros deve configurar corretamente as suas definições de autenticação.
>
> Para obter mais informações, consulte [Ativar o modelo de aplicação seguro.](enable-secure-app-model.md)

## <a name="get-help"></a>Obter ajuda

Os parceiros podem obter apoio no [grupo de Yammer do Partner Center SDK](https://go.microsoft.com/fwlink/p/?LinkID=717360). Para obter uma ajuda mais personalizada, os desenvolvedores podem usar os seus benefícios de suporte MPN ou Premier Support.

## <a name="join-the-partner-center-api-and-sdk-early-adopter-program"></a>Aderir ao Programa Early Adopter da API e SDK do Centro de Parceiros

Para saber como pode colaborar com a Microsoft no desenvolvimento de funcionalidades e capacidades do Parceiro, consulte [o Programa de API e SDK Early Adopter](early-adopter-program.md)do Partner Center .
