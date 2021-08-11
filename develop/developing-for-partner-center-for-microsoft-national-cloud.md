---
title: Desenvolvimento para Partner Center para Microsoft National Clouds
description: Partner Center SDK diferenças ao desenvolver para Partner Center para Microsoft National Clouds.
MS-HAID:
- pc\_apiv2.developing\_with\_different\_partner\_center\_versions
- pc\_apiv2.developing\_for\_partner\_center\_for\_microsoft\_national\_cloud
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f8b9b3c3b9a1a1173cf8f3e79f60e629e3d34ea13ecce2e7a2c74924bde2b7d1
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994868"
---
# <a name="developing-for-partner-center-for-microsoft-national-clouds"></a>Desenvolvimento para Partner Center para Microsoft National Clouds

**Aplica-se a**: Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Partner Center tem um conjunto de documentação SDK. No entanto, algumas funcionalidades podem não estar disponíveis nas versões do Partner Center para as Microsoft National Clouds.

Os desenvolvedores precisam considerar alterações ao SDK para as seguintes versões do Partner Center:

- [Centro de Parceiros operado pela 21Vianet](#partner-center-operated-by-21vianet)
- [Centro de Parceiros para Microsoft Cloud Germany](#partner-center-for-microsoft-cloud-germany)
- [Centro de Parceiros do Microsoft Cloud for US Government](#partner-center-for-microsoft-cloud-for-us-government)

Cada artigo do Partner Center SDK lista as versões do Partner Center aplicáveis. Cada artigo de referência gerido também lista as versões do Centro de Parceiros aplicáveis na secção **Requisitos.**

## <a name="partner-center-operated-by-21vianet"></a>Centro de Parceiros operado pela 21Vianet

As diferenças entre parceiros entre *Partner Center* e Partner *Center operados pela 21Vianet* são:

- Não é possível redefinir programáticamente uma palavra-passe para um utilizador do cliente ou para um utilizador parceiro completo.

- As assinaturas do Azure não estão disponíveis.

- Não é possível gerir as licenças para o utilizador do seu cliente. Em vez disso, os seus clientes devem usar o centro de administração Office 365 para gerir as suas licenças.

- Todos os pedidos de suporte são geridos através do Partner Center operado pela 21Vianet. Os pedidos de serviço e as atualizações de serviço não se aplicam.

## <a name="partner-center-for-microsoft-cloud-germany"></a>Centro de Parceiros para Microsoft Cloud Germany

> [!IMPORTANT]
> Com base na evolução das necessidades dos clientes, a nossa estratégia de nuvem para a Alemanha centrar-se-á na entrega das novas regiões em nuvem na Alemanha que são consistentes com a nossa oferta global de nuvem. Com este foco, deixaremos de aceitar novos clientes ou de implementar novos serviços na Microsoft Cloud Alemanha atualmente disponível. Os clientes existentes podem continuar a utilizar os serviços cloud atualmente disponíveis, que vamos manter com as necessárias atualizações de segurança.
>
> Seguindo em frente, os novos clientes têm a opção de utilizar as regiões europeias atualmente disponíveis ou as novas regiões da Alemanha quando estiverem disponíveis. Para obter mais informações, veja [A Microsoft disponibilizará serviços cloud a partir de novos datacenters na Alemanha](https://news.microsoft.com/europe/2018/08/31/microsoft-to-deliver-cloud-services-from-new-datacentres-in-germany-in-2019-to-meet-evolving-customer-needs/).

As diferenças entre parceiros entre *Partner Center* e Partner Center para a Microsoft *Cloud Germany* são:

- Os parceiros não podem criar utilizadores para a organização do seu cliente ou atribuir funções.
  - Os parceiros podem ler campos, mas não podem escrevê-los ou atualizá-los.
  - Os parceiros devem criar ou atualizar manualmente os utilizadores dos seus clientes no centro de administração Office 365 ou através do portal Azure. Consulte [Azure Ative Directory Documentação.](/azure/active-directory/)

- Não é possível gerir as licenças para os utilizadores do seu cliente utilizando o Partner Center para o portal Microsoft Cloud Germany ou APIs. Em vez disso, deve utilizar o centro de administração Office 365 ou a gestão de licenças do Grupo Azure Ative (em breve) para gerir as suas licenças.
  - (Opcional) pode utilizar Azure AD Graph API. Ver [Atribuir Licenças a um utilizador](/graph/api/user-assignlicense). Para Partner Center para a Microsoft Cloud Germany, não se esqueça de utilizar o ponto final Graph `https://graph.cloudapi.de` em vez de `https://graph.windows.net` .

- Não é possível redefinir programáticamente uma palavra-passe para um utilizador do cliente ou para um utilizador parceiro completo. Utilize o centro de administração Office 365 ou o portal Azure. Consulte [redefinir a palavra-passe para um utilizador em Azure Ative Directory](/azure/active-directory/fundamentals/active-directory-users-reset-password-azure-portal). Para o passo 1, tem de iniciar seduca no portal Azure para a Microsoft Cloud Germany.

- Os desenvolvedores devem registar manualmente o seu ID da aplicação para integrar a funcionalidade API/SDK do Partner Center na sua aplicação para Partner Center for Microsoft Cloud Germany. Para obter mais informações, consulte [os detalhes da aplicação Register para Partner Center para a Microsoft National Cloud](create-apps-for-partner-center-for-microsoft-national-clouds.md).

## <a name="partner-center-for-microsoft-cloud-for-us-government"></a>Centro de Parceiros do Microsoft Cloud for US Government

As diferenças entre parceiros entre *Partner Center* e Partner Center *for Microsoft Cloud for US Government* são:

- Office 365 subscrições não estão disponíveis para o Partner Center para Microsoft Cloud for US Government.

- Os parceiros existentes que apoiam Microsoft Cloud for US Government devem criar novas contas no Partner Center para Microsoft Cloud for US Government.

- Microsoft Cloud for US Government clientes devem negociar com um único parceiro.
  - Multicanal e multiparte e solicitar relação com um cliente existente dentro de Microsoft Cloud for US Government cenários não se aplicam. Esta limitação deve-se Office 365 não está disponível.

- Os parceiros não podem criar utilizadores para a organização do seu cliente ou atribuir funções.
  - Os parceiros podem ler campos, mas não podem escrevê-los ou atualizá-los. Os parceiros devem criar ou atualizar manualmente os utilizadores dos seus clientes no portal Azure. Consulte [Azure Ative Directory Documentação.](/azure/active-directory/)

- Não é possível redefinir programáticamente uma palavra-passe para um utilizador do cliente ou para um utilizador parceiro completo. Utilize o portal do Azure. Consulte [redefinir a palavra-passe para um utilizador em Azure Ative Directory](/azure/active-directory/active-directory-users-reset-password-azure-portal). Para o passo 1, tem de se inscrever no portal Azure para Microsoft Cloud for US Government.

- Os pontos finais DO REST para o Partner Center for Microsoft Cloud for US Government são os mesmos que para o Partner Center: `https://api.partnercenter.microsoft.com` .

- Os desenvolvedores devem registar manualmente o seu ID da aplicação para integrar a funcionalidade API/SDK do Partner Center na sua aplicação para Partner Center for Microsoft Cloud for US Government. Para obter mais informações, consulte [os detalhes da aplicação Register para Partner Center para a Microsoft National Cloud](create-apps-for-partner-center-for-microsoft-national-clouds.md).
