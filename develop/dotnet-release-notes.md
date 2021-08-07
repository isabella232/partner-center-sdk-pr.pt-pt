---
title: Parceiro Center .NET SDK notas de lançamento
description: Notas de lançamento para a versão mais recente do Partner Center .NET SDK.
ms.date: 07/07/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6fc6182638cb2cc5457bdfada37b928c88e1ca786e401f7eb8d5309a0abd9310
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991229"
---
# <a name="net-sdk-release-notes"></a>.NET SDK notas de lançamento

As seguintes notas de lançamento estão disponíveis para novas versões do [Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter). Pode encontrar [amostras .NET SDK](https://github.com/Microsoft/Partner-Center-DotNet-Samples) no GitHub. Pode encontrar a [referência API do Partner Center .NET](/dotnet/api/?view=partnercenter-dotnet-latest&preserve-view=true) no Browser .NET API.

## <a name="version-201"></a>Versão 2.0.1

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/2.0.1) v2.0.1 é agora disponibilidade geral. Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples) As seguintes alterações estão incluídas nesta versão:

> [!NOTE]
> Algumas das alterações introduzidas no âmbito da New Commerce Experiences ("NCE") que estão atualmente disponíveis com base apenas no convite aos parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365. Os parceiros que não fazem parte da pré-visualização privada de novo comércio não devem notar impactos e devem ser retro compatíveis.

### <a name="common"></a>Common
* Alteração na referência à biblioteca de autenticação – A referência é alterada de Azure Ative Directory Biblioteca de Autenticação[(ADAL)](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)para a Biblioteca de Autenticação do Microsoft[(MSAL)](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet)

  As seguintes alterações devem ser feitas para garantir que a MSAL funciona corretamente na sua aplicação ou na amostra .NET:

  * Adicione `https://login.microsoftonline.com/common/oauth2/nativeclient` como RedirectUrl para aplicações móveis e desktop
  * Adicione **domínio** na secção de instrução do utilizador no seu ficheiro de configuração de aplicação. 

    Domínio é o domínio Azure Ative Directory ou iD do inquilino onde a aplicação AD Azure foi criada

* [Códigos de erro](error-codes.md) - Novo código de erro adicionado 
  * 408: Pedido de tempo limite
  * 504: Tempo limite de gateway 

### <a name="manage-billing"></a>Gerir faturação

* [Artigos de linha de fatura](get-invoiceline-items.md) - novos atributos adicionados às seguintes APIs:
  * `GET /invoices/{invoice-id}/lineitems?provider={provider}&invoicelineitemtype=billinglineitems`
  * `GET /invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems`

  Novos atributos: 
  * produtosQualifiers
  * subscriçãoStartDate
  * subscriçãoEndDate
  * referenceId
  * creditReasonCode (apenas aplicável à NCE)
  * promotionId 


* [Itens de linha de utilização avaliados diariamente](get-invoice-billed-consumption-lineitems.md) – novos atributos adicionados à seguinte API: 
  * `GET /invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems`
  
  Novos atributos: 
  * hasPartnerEarnedCredit (Apenas aplicável à NCE)
  * creditType (apenas aplicável ao NCE)
  * taxaOfCredit (Apenas aplicável ao NCE)


### <a name="manage-orders"></a>Gerir encomendas

* [Recursos de Subscrição](subscription-resources.md) – Novo imóvel adicionado. 
  * CancelamentoAllowedUntilDate - (Apenas aplicável à NCE)

* Recursos de Transição (Apenas aplicáveis à NCE) – Novo imóvel adicionado 
  * FromSubscriptionId

### <a name="manage-customer-accounts"></a>Gerir contas de clientes

* [Validar um endereço](validate-an-address.md) – A resposta é alterada de um Boolean para um novo modelo para API:
  * `POST /validations/address`
  
  Novo modelo de resposta: 
  * EndereçoValidationResponse

* A API sincronizada de qualificação do cliente é depreciada.  


## <a name="version-1170"></a>Versão 1.17.0

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.17.0) v1.17.0 é agora disponibilidade geral. Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples) As seguintes alterações estão incluídas nesta versão:

* Auditoria Atualizada - Adicionou novos tipos de operação para saber quando o cliente aprovou e encerrou o DAP
  * [DapAdminRelationshipApproved](auditing-resources.md)
  * [DapAdminRelationshipTerminated](auditing-resources.md)

* Auditoria Atualizada – Adicionou novos tipos de recursos e operação para apoiar o cenário de função de diretório de clientes
  * Tipo de recurso "[CustomerDirectoryRole](auditing-resources.md)"
  * Tipos de operação "[AddUserMember](auditing-resources.md)" e "[RemoveUserMember](auditing-resources.md)"

* Atualizações SDK para conta de clientes - Suporte para seguir API's
  * GET /clientes/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus
  * GET /clientes/{cliente-inquilino-id}/qualificações 
  * POST /clientes/{customer_id}/qualificações?código={validação Código}

* **Na sequência de alterações introduzidas no âmbito do Novo Comércio, que atualmente estão disponíveis com base apenas no convite aos parceiros que fazem parte da nova experiência técnica de experiência de comércio M365/D365.** Os parceiros que não fazem parte da pré-visualização privada de novo comércio não devem notar impactos e devem ser retro compatíveis.
  * Alterações no catálogo:
    * GET /products/{product-id}/skus/{sku-id}
  * Compra e Gestão:
    * GET /clientes/{clienteId}/subscrições
    * GET /clientes/{customerId}/subscrições/{subscriçãoD}
    * PATCH /clientes/{customerId}/subscrições/{subscriçãoD}
    * GET /clientes/{customerId}/subscrições/{subscriçãoD}/transitioneligibilities
    * GET /clientes/{customerId}/subscrições/{subscriçãoId}/transições
    * POST /clientes/{customerId}/subscrições/{subscriçãoD}/transições


## <a name="version-1163"></a>Versão 1.16.3

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.3) v1.16.3 é agora disponibilidade geral. Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples) As seguintes alterações estão incluídas nesta versão:

* SelfServePolicies - nova funcionalidade adicionada
  * [GetSelfServePolicies](get-a-self-serve-policy-by-id.md)
  * [GetListOfSelfServicePolicies](get-a-list-of-self-serve-policies.md)
  * [CreateSelfServePolicies](create-a-self-serve-policy.md)
  * [UpdateSelfServePolicies](update-a-self-serve-policy.md)
  * [DeleteSelfServePolicies](delete-a-self-serve-policy.md)

* Perfil da empresa de clientes
  * [Número de Registo de Organização Adicionado](create-a-customer.md)

* CustomerBillingProfile.DefaultAddress
  * Nome médio adicionado

## <a name="version-1162"></a>Versão 1.16.2

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.2) v1.16.2 é agora disponibilidade geral. Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples) As seguintes alterações estão incluídas nesta versão:

* Atualizar tipos de operação suportados para Registo de Auditoria. Os recém-adicionados são:
  * CreateSelfServePolicy
  * UpdateSelfServePolicy
  * DeleteSelfServePolicy
  * RemoverPartnerRelationship
  * ExcluirTipCustomer
  * CreateRelatedReferral
  * UpdateRelatedReferral

* A criação de pedido de serviço está agora depreciada
* Os tópicos de apoio são agora depreciados


## <a name="version-1161"></a>Versão 1.16.1

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.1) v1.16.1 é agora disponibilidade geral. Estão também disponíveis [amostras GitHub atualizadas.](https://github.com/Microsoft/Partner-Center-DotNet-Samples) As seguintes alterações estão incluídas nesta versão:

Migramos o Atual Microsoft Partner Center SDK de .NET Framework para a plataforma .NET Standard 2.0. Isto tornará o SDK compatível com as aplicações existentes utilizando .NET Framework 4.6.1 ou superior. O SDK irá suportar .NET Core 2.0 e superior. Verifique [o suporte de implementação .NET](/dotnet/standard/net-standard) antes de o apresentar às aplicações existentes.   


## <a name="version-1153"></a>Versão 1.15.3
[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.15.3) v1.15.3 é agora disponibilidade geral. Estão também disponíveis APIs de REST e [amostras GitHub.](https://github.com/Microsoft/Partner-Center-DotNet-Samples) As seguintes alterações estão incluídas nesta versão:

* Acordo de Parceiro
  * Adicionou a capacidade de os fornecedores indiretos verificarem o [estado do Microsoft Partner Agreement dos revendedores indiretos](verify-indirect-reseller-mpa-status.md).
* Produtos
  * As duas interfaces seguintes foram incorretamente colocadas no espaço de nomes Microsoft.Store.PartnerCenter.Products. Agora, estão localizados sob o espaço de nomes Microsoft.Store.PartnerCenter.Customers.Products.Products.
    * ICustomerProductByReservationScope
    * ICustomerSkuByReservationScope
