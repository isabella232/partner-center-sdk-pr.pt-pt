---
title: Capacidades de caixa de areia para relacionamento revendedor
description: A caixa de areia do parceiro tem capacidade de suportar relações entre o parceiro e o cliente
ms.date: 05/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 14133627a607c6e4151a90c37565e5f62823345e007eb55d87100de25d1f161a
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996857"
---
# <a name="sandbox-capabilities-for-reseller-relationship"></a>Capacidades de caixa de areia para relacionamento revendedor

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Este artigo explica o que é suportado na Caixa de Areia para relações de revendedor entre o parceiro e o cliente. 

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais de conta do Partner Center. O cenário sandbox suporta a autenticação com as credenciais autónomas da App e app+User.
- Uma ID do cliente (cliente-inquilino-id). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard/home)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente (cliente-inquilino-id).
- Todas as instâncias de compra de máquinas virtuais reservadas Azure e as ordens de compra de software devem ser canceladas antes de eliminar um cliente da caixa de areia de integração da Ponta.

## <a name="scenarios-supporting-reseller-relationship"></a>Cenários de apoio à relação do revendedor

1.  Sandbox Direct Bill Partners e Fornecedores Indiretos podem criar relações com o cliente Sandbox. 
2.  Sandbox Direct Bill Partners e Fornecedores Indiretos não podem convidar clientes sandbox.

3. Sandbox Direct Bill Partner e Fornecedores Indiretos são capazes de remover a relação de revendedor do Partner Center UI e API.

4. Sandbox Remove Reseller Relationship vai ligar para Eliminar o cliente AP. Isto removerá a relação e eliminará o inquilino do cliente. {baseURL}/v1/Clientes/{cliente-Tenant-id}


    ### <a name="in-the-sandbox"></a>Na Caixa de Areia

    **Parceiros de conta diretos:**

    - Pode adicionar clientes existentes

    - Não é possível solicitar relações com novos clientes

    **Fornecedores indiretos:**

    - Pode adicionar clientes existentes

    - Não é possível solicitar relações com novos clientes

    - Não pode ter uma relação com um revendedor indireto

    **Revendedor indireto:** 

    -   Pode ter relações com clientes existentes

    -   Não é possível solicitar novos relacionamentos ou adicionar novos clientes

    ### <a name="in-partner-center"></a>No Centro Parceiro

    **Parceiros de conta diretos:**

    -   Pode adicionar novos clientes

    -   Pode solicitar relações com novos clientes

    **Fornecedores indiretos:**

    -   Pode adicionar novos clientes

    -   Pode solicitar relações com novos clientes

    -   Pode ter relações com revendedores indiretos

    **Revendedores indiretos:**

    -   Não pode adicionar novos clientes

    -   Pode solicitar relações com novos clientes


Siga a [Relação de Revendedor Remover](remove-a-reseller-relationship-with-a-customer.md) para obter mais detalhes. No entanto, existem algumas diferenças entre as capacidades do Produto e da Sandbox.

### <a name="request-syntax"></a>PEDIDO SYNTAX

|**Método**|**Eliminar**|
|-------------|------------|
|Eliminar|{baseURL}/v1/Clientes/{cliente-Tenant-id} |

Pedido corpo Nenhum

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](./error-codes.md).

## <a name="next-steps"></a>Passos seguintes

- [Ativar subscrições de Sandbox para produtos Azure Marketplace](activate-sandbox-subscription-azure-marketplace-products.md)

- [Cancelar uma encomenda da Sandbox](cancel-an-order-from-the-integration-sandbox.md)

- [Testar e depurar](test-and-debug.md)