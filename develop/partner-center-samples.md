---
title: Exemplos do Centro de Parceiros
description: Para ajudá-lo a levantar-se e a correr rapidamente com as APIs do Partner Center, fornecemos um programa de amostragem, cortes de código geridos C\ e pedidos e respostas de amostras REST.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 34e269b1a0e711f82144898441c75d731b8613f70512517e12b6705990b35622
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997605"
---
# <a name="partner-center-samples"></a>Exemplos do Centro de Parceiros

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Para ajudá-lo a levantar-se e a correr rapidamente com as APIs do Partner Center, fornecemos um programa de amostragem, cortes de código geridos C# e pedidos e respostas de amostras REST.

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

| Sample                                                        | Detalhes                                             |
|---------------------------------------------------------------|-----------------------------------------------------|
| Fragmentos de código                                                 | Para ponteiros e snippets de código .NET, Java e PowerShell que mostram como usar o Partner Center gerido API para gerir contas de clientes, obter análises, fazer encomendas, gerir faturação e subscrições, fornecer suporte e gerir contas e perfis, ver [Cenários](scenarios.md).                                                                          |
| Exemplos REST                                                  | Para pedidos de amostra e respostas que mostram como usar a API do Partner Center REST para gerir contas de clientes, obter análises, fazer encomendas, gerir faturamentos e subscrições, fornecer suporte e gerir contas e perfis, ver [Cenários](scenarios.md).                                                                                                       |
| [Aplicação de teste da consola](console-test-app.md)                       | Esta aplicação encontra-se disponível em C# e Java, fornece código e algum tratamento de erros para todos os cenários listados na secção de cenários.                                                                        |
| [Loja Web para clientes CSP](csp-customer-web-storefront.md) | Este site mostra uma loja online funcionando que os seus clientes poderiam usar para comprar subscrições de produtos Microsoft. Pode criar facilmente um website para a sua empresa com o [Guia De Arranque Rápido do Construtor de Lojas de Clientes CSP.](csp-customer-storefront-builder-quick-start-guide-.md)                                                              |
| Site da loja                                                | Esta aplicação mostra como construir uma loja web com base no catálogo de ofertas disponíveis para Fornecedor de Soluções em Nuvem parceiros. Os clientes podem criar uma conta de loja e encomendar subscrições de software através do seu site.<br/><br/>                  **Obtenha o código:**<br/> [Descarregue o código de amostra](https://go.microsoft.com/fwlink/p/?LinkId=746683)<br/><br/>                                            **O que configurar antes do lançamento:**<br/><br/> - Autenticação: ID da aplicação & segredo<br/> - Marca: logotipo e nome da empresa<br/> - Mensagem de boas-vindas<br/> - Ofertas, incluindo descrições e preços. A aplicação assume que os preços da lista incluem quaisquer impostos aplicáveis. Em alternativa, pode adicionar lógica adicional para calcular o imposto durante o check-out.<br/> - Informações de pagamento: forneça as suas próprias opções de cartão de crédito, PayPal ou outros tipos de pagamento. Antes de configurar esta peça, leia o guia [Não pagamento, fraude ou uso indevido](/partner-center/non-payment-fraud-misuse). |