---
title: Aplicação de teste da consola
description: Esta aplicação de teste de consola fornece código de amostra para todos os cenários suportados pelas APIs do Partner Center. Também pode usá-lo para testar.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 53a014608303e432be251de0845857547170a5464a1952bb4fde9ff7beb8ae95
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991961"
---
# <a name="console-test-app"></a>Aplicação de teste da consola

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

A aplicação de teste de consola é fornecida em C# e Java, fornece códigos de amostra para todos os cenários suportados pelas APIs do Partner Center. Também pode usá-lo para testar.

## <a name="get-the-code"></a>Obter o código

Descarregue o código de amostra para a aplicação de teste da consola.

## <a name="net"></a>.NET

[Descarregue o código de amostra](https://go.microsoft.com/fwlink/p/?LinkId=746682) e modifique-o conforme necessário.

> [!IMPORTANT]
> Antes de construir a aplicação, atualize os valores no ficheiro *App.config* para refletir a informação de autenticação AD AZure que criou na [autenticação do Partner Center.](partner-center-authentication.md) Especificamente, deve utilizar as definições da sua conta de caixa de areia de integração durante o desenvolvimento precoce ou para testar na produção.

De **acordo com os cenários,** os *App.config* ficheiros, pode definir parâmetros que serão automaticamente transmitidos para os cenários que executou.

Para modificar a lista de cenários que são executados, comente linhas no **IPartnerScenario \[ \] mainScenarios** ou num método individual **Get Scenarios** encontrado no ficheiro *.cs Programa.*

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

[Descarregue o código de amostra](https://go.microsoft.com/fwlink/p/?LinkId=2026887) e modifique-o conforme necessário.

> [!IMPORTANT]
> Antes de construir a aplicação, atualize os valores no *SamplesConfigurations.jsno* ficheiro para refletir a informação de autenticação AD AZure que criou na [autenticação do Partner Center.](partner-center-authentication.md) Especificamente, deve utilizar as definições da sua conta de caixa de areia de integração durante o desenvolvimento precoce ou para testar na produção.

Nos **cenários As definições** no *SamplesConfiguration.jsno* ficheiro, pode definir parâmetros que serão automaticamente transmitidos para os cenários que executou.

Para modificar a lista de cenários que são executados, comente linhas no **iPartnerScenario \[ \] mainScenarios** ou num método individual **Get Scenarios** encontrado no ficheiro *.java Programa.*

## <a name="what-to-change"></a>O que mudar

Utilize as seguintes listas para determinar o que alterar ou não no código de amostra.

### <a name="partnerservicesettings"></a>PartnerServiceSettings

Para **PartnerServiceSettings,** não mude:

- **PartnerServiceApiEndpoint**
- **AutenticaçãoAuthorityEndpoint**
- **Ponto de GraphEndpoint**
- **CommonDomain**

Todas estas definições são necessárias para que as chamadas de API da amostra funcionem corretamente.

### <a name="userauthentication"></a>UtilizadoresAuferição

Para a Concessão de **Privacidade do Utilizador,** é-lhe exigido que altere:

- **ApplicationId** (o seu ID de aplicação Azure Ative Directory utilizado para login)
- **Nome do Utilizador** (o seu nome de utilizador de diretório ativo)
- **Palavra-passe** (a sua senha de diretório ativa).

Não mude:

- **ResourceUrl**
- **RedirectUrl**

### <a name="appauthentication"></a>AppAuthentication

Para **a AppAuthentication,** é obrigado a alterar:

- **ApplicationId** (o ID da sua aplicação de diretório ativo usado para login de aplicações)
- **ApplicationSecret** (o segredo da sua aplicação de diretório ativo usado para login de aplicações)
- **Domínio** (o seu domínio de diretório ativo no qual a aplicação está hospedada)

### <a name="scenariosettings"></a>CenárioS

Para **cenáriosSettings,** não mude:

- **CustomerDomainS sufixo** (o sufixo de domínio utilizado na criação de um novo cliente)

Definições opcionais. Se deixada em branco, esta informação terá de ser inserida quando executar um cenário, se necessário):

- **CustomerIdToDelete** (o ID do cliente utilizado para a eliminação)
- **Predefinição DeCustomerId** (o ID do cliente para utilizar em cenários relacionados com o cliente)
- **DefaultInvoiceID** (o ID da fatura a utilizar em cenários de fatura)
- **PartnerMpnId** (o parceiro MPN ID para usar em cenários de parceiros indiretos)
- **DefaultServiceRequestId** (o ID de pedido de serviço para usar em cenários de pedido de serviço)
- **DefaultSupportTopicID** (o ID tópico de suporte a utilizar em cenários de pedido de serviço)
- **DefaultOfferID** (o ID de oferta para usar em cenários de oferta)
- **PredefiniçãoOrderID** (o ID de encomenda a ser utilizado em cenários de ordem)
- **DefaultSubscriptionID** (o ID de subscrição a utilizar em cenários de subscrição)

Opcional para mudar. Todas estas definições especificam a quantidade de entradas por página ao recuperar o conteúdo paged:

- **CustomerPageSize**
- **FaturaSagensSize**
- **ServiceRequestPageSize**
- **DefaultOffofferPageSize**
- **SubscriçãoPagesize**
