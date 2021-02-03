---
title: Parceiro Center .NET SDK notas de lançamento
description: Notas de lançamento para a versão mais recente do Partner Center .NET SDK.
ms.date: 09/18/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6be8f62e0c202a00b194f5af1dc8904006f8d637
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2020
ms.locfileid: "97770239"
---
# <a name="net-sdk-release-notes"></a>.NET SDK notas de lançamento

As seguintes notas de lançamento estão disponíveis para novas versões do [Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter). Pode encontrar [amostras .NET SDK](https://github.com/Microsoft/Partner-Center-DotNet-Samples) no GitHub. Pode encontrar a [referência API do Partner Center .NET](/dotnet/api/?view=partnercenter-dotnet-latest&preserve-view=true) no Browser .NET API.

## <a name="version-1163"></a>Versão 1.16.3

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.3) v1.16.3 é agora disponibilidade geral. As [amostras de GitHub atualizadas](https://github.com/Microsoft/Partner-Center-DotNet-Samples) também estão disponíveis. As seguintes alterações estão incluídas nesta versão:

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

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.2) v1.16.2 é agora disponibilidade geral. As [amostras de GitHub atualizadas](https://github.com/Microsoft/Partner-Center-DotNet-Samples) também estão disponíveis. As seguintes alterações estão incluídas nesta versão:

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

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.1) v1.16.1 é agora disponibilidade geral. As [amostras de GitHub atualizadas](https://github.com/Microsoft/Partner-Center-DotNet-Samples) também estão disponíveis. As seguintes alterações estão incluídas nesta versão:

Migramos o Atual Microsoft Partner Center SDK de .NET Framework para a plataforma .NET Standard 2.0. Isto tornará o SDK compatível com as aplicações existentes utilizando o Quadro .NET 4.6.1 e superior. O SDK irá suportar .NET Core 2.0 e superior. Verifique [o suporte de implementação .NET](/dotnet/standard/net-standard) antes de o apresentar às aplicações existentes.   


## <a name="version-1153"></a>Versão 1.15.3
[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.15.3) v1.15.3 é agora disponibilidade geral. Estão também disponíveis [amostras atualizadas](https://github.com/Microsoft/Partner-Center-DotNet-Samples) de REST E GitHub. As seguintes alterações estão incluídas nesta versão:

* Acordo de Parceiro
  * Adicionou a capacidade de os fornecedores indiretos verificarem o [estado do Microsoft Partner Agreement dos revendedores indiretos](verify-indirect-reseller-mpa-status.md).
* Produtos
  * As duas interfaces seguintes foram incorretamente colocadas no espaço de nomes Microsoft.Store.PartnerCenter.Products. Agora, estão localizados sob o espaço de nomes Microsoft.Store.PartnerCenter.Customers.Products.Products.
    * ICustomerProductByReservationScope
    * ICustomerSkuByReservationScope
