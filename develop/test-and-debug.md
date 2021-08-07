---
title: Teste e depurar com caixa de areia de integração
description: Aprenda a usar a sua conta de caixa de areia de integração partner Center (e fichas relacionadas) para testar e depurar o seu código para que não incorre acidentalmente em novas taxas.
ms.date: 09/11/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1a446f1d9a9d7370be2715305ccbaa71b09cfd45957cf8663afb42a23706a7be
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989275"
---
# <a name="test-and-debug-with-your-partner-center-integration-sandbox-to-avoid-paying-unexpected-charges"></a>Teste e depure com a sua caixa de areia de integração partner Center para evitar pagar taxas inesperadas

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Para testar o seu código, deverá utilizar a sua conta de caixa de areia de integração no Partner Center (e nos tokens correspondentes) para que não incorre acidentalmente em novos encargos que a sua empresa é responsável pelo pagamento. Para obter mais informações sobre este ambiente de teste em produção (TiP), consulte [Configurar o acesso api no Partner Center](set-up-api-access-in-partner-center.md).

## <a name="integration-sandbox-constraints"></a>Restrições de caixa de areia de integração

Se executar testes automatizados de verificação de construção, realizar testes na produção ou realizar testes manuais na caixa de areia de integração, poderá atingir os limites máximos para a caixa de areia de integração. Estes limites são 75 clientes, 5 subscrições por cliente e 25 licenças por subscrição.

O limite de 25 licenças significa que não pode adquirir uma oferta na caixa de areia que tenha um requisito mínimo de licença que exceda 25 licenças. Esta limitação inclui testes.

Existem vários ficheiros de fatura e reconciliação disponíveis nos ambientes da Sandbox mas, nem todos estão disponíveis em plataformas antigas ou modernas. Verifique a tabela abaixo para saber mais.

| **Ficheiros**                    | **Disponível em Legado** | **Disponível em Moderno** |
| ---------------------------- | ------------------------ | ------------------------ |
| PDF da fatura                  | No                       | Yes                      |
| Arquivo de Reconciliação de Faturas | No                       | Yes                      |
| Arquivo de Estimativa de Fatura       | No                       | Yes                      |
| Arquivo de utilização faturado diário     | No                       | Yes                      |
| Arquivo diário de utilização não bico   | No                       | Yes                      |


### <a name="azure-plan"></a>Plano do Azure

Por predefinição, os parceiros não podem aprovisionar planos do Azure com as contas de sandbox. Os parceiros que necessitem de o fazer com a conta de sandbox têm de solicitar o acesso. Para se candidatar ao acesso, contacte o seu gestor de conta microsoft ou contacto comercial. Os parceiros que já solicitaram o acesso à provisão Microsoft Azure assinaturas (MS-AZR-0145P) nas suas contas de sandbox não precisam de voltar a solicitar o acesso. Será-lhes concedido acesso automaticamente aos planos Azure.

Para os parceiros cujas contas de caixa de areia tenham sido aprovadas para a disposição dos planos Azure, aplicam-se os seguintes limites:

- Cada conta parceira da sandbox pode ter até 10 planos Azure em todos os inquilinos do cliente (não importa como os planos são distribuídos entre os clientes).

- Um parceiro de conta direta pode criar até um plano Azure por inquilino cliente.

- Um fornecedor indireto pode criar até três planos Azure por inquilino do cliente (para diferentes revendedores indiretos especificados como o Partner-of-Record).

- Cada plano Azure pode ter até três subscrições Azure.

- Cada subscrição CSP Azure na sua conta de caixa de areia está limitada a quatro núcleos de máquina virtual (VM) por data center. Portanto, não é possível providenciar SKUs VM que requerem mais de quatro núcleos VM. Estão também excluídos alguns SKUs de VM especializados, como os núcleos de GPU.

- Cada conta parceira de sandbox tem um limite de gastos de $2.000 (USD) por ciclo de faturação em todos os planos da Azure. Uma vez que um parceiro atinja o limite de gastos, todos os planos Azure serão temporariamente desactivdos até ao próximo ciclo de faturação.

### <a name="cloud-solution-provider-csp-azure-subscription-offers"></a>ofertas de subscrição Fornecedor de Soluções em Nuvem (CSP) Azure

As ofertas de subscrição da CSP Azure já não estão disponíveis por defeito nas contas da caixa de areia. Estes incluem MS-AZR-0146P, MS-AZR-DE-0146P e MS-AZR-USGOV-0146P para subscrições CSP Azure em Microsoft Public Cloud, German Cloud e Government Cloud, respectivamente. Os parceiros que necessitem de acesso a estas ofertas com a sua conta de caixa de areia devem solicitar o acesso. Para se candidatar ao acesso, discuta com o seu gestor de conta microsoft ou contacto comercial.

Para os parceiros cujas contas de caixa de areia tenham sido aprovadas para ofertas de subscrição da CSP Azure, aplicam-se os seguintes limites:

- Pode ter até um máximo de 375 subscrições ativas (75 clientes x 5 subscrições por cliente). No entanto, apenas 10 podem ser subscrições CSP Azure.

- Quando uma subscrição da CSP Azure atinge os 200 dólares de utilização do Azure, os seus recursos são temporariamente desactivdos até ao seu próximo ciclo de faturação. Ainda é considerada uma subscrição ativa e é contada para o limite de 10 subscrições ativas do Azure.

- Cada subscrição CSP Azure na sua conta de caixa de areia está limitada a quatro núcleos de máquina virtual (VM) por data center. Portanto, não é possível providenciar SKUs VM que requerem mais de quatro núcleos VM. Estão também excluídos alguns SKUs de VM especializados, como os núcleos de GPU.

> [!Important]
> Todas as subscrições existentes da CSP Azure aprovisionadas com contas de sandbox antes de 1 de agosto de 2018 deixaram de ser suportadas e serão desprovisionadas pela Microsoft entre 16 de outubro e 31 de outubro de 2018. Após a desprovisionamento das subscrições, não podem ser reativadas e os dados associados deixaram de estar acessíveis. Os parceiros que tenham dados valiosos armazenados ao abrigo destas subscrições devem fazer o back up dos dados antes de 16 de outubro de 2018.

### <a name="azure-reserved-vm-instance"></a>Exemplo VM Reservado Azure

Se estiver [a adquirir um exemplo de VM reservado Azure](purchase-azure-reservations.md) com a sua conta de caixa de areia, está limitado a duas instâncias VM por cliente. Também está limitado a selecionar apenas a partir do seguinte produto de instância VM reservado Azure:

| Título do produto  | Data efetiva  | Título Sku                                               | Região [ArmRegionName] | Chave de exemplo [ArmSkuName] | Duração | ID do medidor de consumo       |
|----------------|-----------------|---------------------------------------------------------|------------------------|--------------|----------|----------------------------|
| Série B       | 12/1/2017 0:00  | Instância VM reservada, Standard_B1s, KR Sul, 1 ano    | Coreias             | `Standard_B1s` | `1Year`    | 3f913071-0dd7-4258-8ec4-6fad05bd976d |
| Série B       | 12/1/2017 0:00  | Instância VM reservada, Standard_B1s, EUA Leste, 1 ano     | eastus                 | `Standard_B1s` | `1Year`    | f4d7a5a5-1b67-45ea-b1a0-282fbdd34b05 |
| Série B       | 12/1/2017 0:00  | Instância VM reservada, Standard_B1s, EUA West 2, 1 ano   | westus2                | `Standard_B1s` | `1Year`    | 222e39f5-e99f-4fa3-a323-f46402977888 |
| Série B       | 12/1/2017 0:00  | Instância VM reservada, Standard_B1s, Us North Central, 1 ano    | northcentralus | `Standard_B1s` | `1Year`    | 4e1716fc-4842-43f1-aa96-7c1b1b1395a7 |
| Série B       | 12/1/2017 0:00  | Instância VM reservada, Standard_B1s, CA Leste, 1 ano     | CanadáEast             | `Standard_B1s` | `1Year`    | ab8a5993-5db7-47c8-b3b1-2e1365b353fb |

### <a name="subscriptions-for-commercial-marketplace-products"></a>Assinaturas para produtos de mercado comercial

Na produção, depois de ter [criado uma subscrição de produtos SaaS de marketplace comercial,](create-subscription-azure-marketplace-products.md)precisa de recuperar uma ligação de ativação personalizada do Partner Center e visitar o site da editora para concluir o processo de configuração. A faturação da subscrição só começará depois de a configuração estar concluída.

No ambiente da caixa de areia da CSP, não existe integração com os ISVs. Se tentar recuperar uma ligação de ativação do Partner Center, será devolvido um link falso. Não é possível utilizar este link falso para completar o processo de configuração no site da editora. Para utilizar a conta de sandbox de integração para testar a faturação para subscrições de produtos SaaS de marketplace comercial, consulte [ativar uma subscrição de sandbox para produtos de mercado comercial.](activate-sandbox-subscription-azure-marketplace-products.md) A faturação da subscrição começará após a ativação bem sucedida.

Para limpar no final do seu teste para que haja espaço para a próxima ronda de testes, consulte os seguintes artigos:

- [Eliminar uma conta de cliente do sandbox de integração](delete-a-customer-account-from-the-integration-sandbox.md)

- [Diminuir a quantidade de uma subscrição](change-the-quantity-of-a-subscription.md)

- [Suspenda uma subscrição](suspend-a-subscription.md) para que possa removê-la.

## <a name="best-practices-for-rest-development"></a>Melhores práticas para o desenvolvimento do REST

- Utilize uma ferramenta de rastreio de rede para que possa ver o seu pedido, a resposta e se houver erros no código de estado HTTP na resposta. Para obter mais informações sobre o manuseamento de [erros,](error-codes.md)consulte os códigos de erro do Partner Center REST .

- Utilize um novo ID de correlação para cada chamada feita para a API do Centro Parceiro REST. Esta prática garante uma melhor exploração madeireira e ajudará durante a depuragem. Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

## <a name="troubleshooting-tips-for-common-rest-problems"></a>Troubleshooting tips for common REST problems (Sugestões de resolução de problemas para problemas REST comuns)

- Reveja todas as propriedades do cabeçalho, incluindo a versão URL e API.

- Certifique-se de que as propriedades estão incluídas, se necessário, e corretamente formatadas.

- A formatação incorreta da matriz é um erro comum.

- **Os ETags** são temporários e, como resultado, não devem ser armazenados. Quando uma chamada de função requer um **ETags,** utilize o valor mais recente dos **ETags** obtendo novamente o recurso. **Os valores ETags** devem ser incluídos em aspas duplas, como uma cadeia:

   ```rest
   If-Match : "eyJpZCI6IjUwMWE4NjBjLTE2OTgtNDQyYi04MDhjLTRiNjEyY2NmMzVmMiIsInZlcnNpb24iOjF9"
   ```
