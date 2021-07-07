---
title: Capacidades de fornecedor indireto CSP na Caixa de Areia
description: Os fornecedores indiretos podem criar revendedores indiretos na Caixa de Areia para efeitos de teste.
ms.date: 05/20/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vinayks-ms
ms.author: vinayks
ms.openlocfilehash: da35dadd4e13247e923259a1cf3a67852f4b9e00
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445906"
---
# <a name="csp-indirect-provider-sandbox-capabilities-for-creating-indirect-reseller-accounts"></a>Capacidades de caixa de areia do fornecedor CSP indireto para criar contas de revendedores indiretos 

**Funções adequadas**: Prestador indireto

Os Fornecedores Indiretos CSP podem criar uma conta de Areia De Revendedor Indireto CSP através da sua própria conta De sandbox Tier 2 no portal Partner Center.


## <a name="prerequisites"></a>Pré-requisitos 

Credenciais de caixa de areia Partner Center Indirete Provider (Nível 2). O cenário sandbox suporta a autenticação com as credenciais autónomas da App e app+User. 
 

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a>Sandbox Indireto Provider – Criar Revendedor Indireto Sandbox utilizando a interface de utilizador do Partner Center 

 Esta é uma funcionalidade apenas para Sandbox que permite aos Fornecedores Indiretos da Sandbox a capacidade de criar uma conta de Revendedor Indireto Sandbox através do portal Partner Center.

Os seguintes cenários são o que os fornecedores indiretos podem fazer para revendedores indiretos em Sandbox através da interface de utilizador do Partner Center: 

1. Os Fornecedores Indiretos CSP podem criar uma conta de Sandbox de Revendedor Indireto CSP através da sua própria conta De sandbox Tier 2 no portal Partner Center.
2. Os revendedores indiretos da CSP podem ver o cliente por Fornecedores Indiretos. 

1. Os Revendedores Indiretos CSP podem gerir a conta do cliente utilizando permissões de administração delegadas.

1. Os Fornecedores Indiretos da CSP podem convidar revendedores indiretos da CSP.
 
1. Os Fornecedores Indiretos CSP podem eliminar uma conta de Sandbox de Revendedor Indireto CSP através da sua própria conta De sandbox Tier 2 no portal Partner Center.

    a.  Quando o Sandbox Indirect Provider eliminar a relação com o Revendedor Indireto Sandbox, verifique se o Revendedor Indireto tem alguma outra relação com outros fornecedores. Em caso afirmativo, apenas a relação com esse fornecedor indireto específico será removida.

    c. Se esta for a única relação para o Revendedor Indireto, então o Revendedor Indireto será eliminado.

1. Os Fornecedores Indiretos CSP podem eliminar um Revendedor Indireto CSP.

    a. Esta é uma funcionalidade apenas para Sandbox que permite aos Fornecedores Indiretos da Sandbox a capacidade de eliminar revendedores indiretos sandbox.
     
1. Pré-requisitos para a eliminação de um Revendedor Indireto Sandbox:

    1. Suspender as assinaturas para cada cliente da Sandbox Reseller Indirect.

    1. Elimine todos os clientes do Revendedor Indireto.

1. Limite de cinco Revendedores Indiretos Sandbox permitidos por Sandbox Indirect Provider. Uma vez eliminado o revendedor Sandbox Indirect, a quota será reposta.

### <a name="pre-requisites"></a>Pré-requisitos

- Limite de cinco Revendedores Indiretos Sandbox permitidos por Sandbox Indirect Provider. 

- O mesmo ID MPN pode ser usado para criar várias contas de Sandbox de Revendedor Indireto se o país MPN ID e o país de Sandbox de Revendedor Indireto forem os mesmos. Se tiver um ID MPN de teste disponível, pode usá-lo, ou pode obter uma lista de IDs MPN através do nosso [canal Yammer]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ). Se não tiver acesso a Yammer, Yammer lhe pedirá acesso.
 
- Apenas 75 clientes são permitidos por Sandbox Indireto Fornecedor

## <a name="create-csp-indirect-reseller-sandbox-account"></a>Criar conta CSP Reseller Sandbox

1. Inscreva-se no Partner Center através da sua conta De sandbox Tier 2. 

2. Navegue para Revendedores Indiretos a partir do menu esquerdo. 

3. Selecione o botão **Add Reseller Sandbox.** 

4. Preencha o formulário de inscrição de conta. É autoexplicativo, mas lembre-se que está a criar uma conta Sandbox para um Revendedor Indireto. Esta conta não será submetida a verificação e será ativada assim que terminar a inscrição na conta.  

5. Assim que a conta for criada, obterá as credenciais de Administração Global para a conta de caixa de areia Do Revendedor Indireto no portal. Lembre-se de guardá-lo imediatamente, caso contrário, não poderá inscrever-se como uma Caixa de Areia De Revendedor Indireto. 

6. Inscreva-se e inscreva-se novamente no Partner Center utilizando as novas credenciais para Reseller Indirect Sandbox. Explore as capacidades que pode fazer como Revendedor Indireto. Algumas coisas são:  

    - Gerir perfis  

    - Gerir utilizadores e funções 

    - Gerir Fornecedores Indiretos 

    - Gerir clientes da CSP Sandbox 

    - Gerir relações
    
     
## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a>Sandbox Indireto Provider – Eliminar o Revendedor Indireto sandbox utilizando a interface de utilizador do Partner Center

 Esta é uma funcionalidade única da Sandbox que permite aos Fornecedores Indiretos da Sandbox a capacidade de eliminar uma conta de Revendedor Indireto Sandbox existente através do portal Partner Center. 

### <a name="pre-requisites-to-delete-sandbox-indirect-reseller"></a>Pré-requisitos para eliminar o revendedor indireto da caixa de areia:

Uma conta de Sandbox de Revendedor Indireto CSP existente associada à sua própria conta de Sandbox CSP Indirect Provider Tier-2.  
 

## <a name="delete-csp-indirect-reseller-sandbox-account"></a>Eliminar conta de revendedor indireto CSP

1. Inscreva-se no Partner Center utilizando a sua conta De sandbox Tier 2. 

2. Navegue para Revendedores Indiretos a partir do menu esquerdo. 

3. Selecione o link **'Delete Reseller Sandbox'** ao lado da conta Descoventer a caixa de areia indireta que pretende eliminar. A conta Descovendor Indireto Sandbox será permanentemente eliminada e não pode ser recuperada. 

## <a name="api-references"></a>Referências de API

- Criar Revendedor Indireto 
- Eliminar Revendedor Indireto 

 

 