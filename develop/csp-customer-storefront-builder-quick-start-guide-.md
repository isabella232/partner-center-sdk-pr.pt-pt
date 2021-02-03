---
title: Guia de Início Rápido da Loja Web para Clientes CSP
description: Crie um mercado online para vender ofertas de soluções de nuvem (CSP) utilizando o CSP Customer Storefront Builder.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d64deff9b002b861c9f48d076feb5841af727e3d
ms.sourcegitcommit: 57620e249e218edc4af7c83c2ce8a3008a4adf4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/04/2020
ms.locfileid: "97769206"
---
# <a name="csp-customer-storefront-builder-quick-start-guide"></a>Guia de Início Rápido da Loja Web para Clientes CSP

**Aplica-se a:**

- Partner Center

Crie um mercado online para vender ofertas de soluções de nuvem (CSP) utilizando o CSP Customer Storefront Builder.

## <a name="introduction-to-the-csp-customer-storefront-builder"></a>Introdução ao Construtor de Lojas de Clientes CSP

O CSP Customer Storefront Builder ajuda os parceiros a criar facilmente um mercado online para vender ofertas de CSP aos seus clientes. A maioria dos parceiros e pequenas organizações de vendas quer focar-se na venda em vez de desenvolver um mercado online. A aplicação de amostra SDK partner Center requer habilidades de desenvolvimento de software para criar e implementar um website. Com o CSP Customer Storefront Builder, pode criar de forma rápida e fácil o seu próprio website. Também pode descarregar o website como código de amostra ou implementar diretamente na sua subscrição Azure com um website Ready to Transact.

Este website é totalmente propriedade, suportado e mantido por parceiros, e a Microsoft não recolhe quaisquer dados ou telemetria do site. O CSP Customer Storefront Builder cria um website para o parceiro que está em total conformidade com a Norma de [Segurança de Dados da Indústria de Cartões de Pagamento](https://www.pcisecuritystandards.org/) (PCI DSS).

O código CSP Customer Storefront Builder está sujeito à licença disponível no [Partner Center SDK EULA](https://partnercenter.microsoft.com/partner/EULA_Partner_Center_SDK).

>[!NOTE]
>Você é responsável pela gestão, manutenção e quaisquer problemas que possam resultar da criação do site. Leia e compreenda os termos no [Centro Parceiro SDK EULA](https://partnercenter.microsoft.com/partner/EULA_Partner_Center_SDK).

Para obter informações adicionais, consulte também os seguintes artigos: [loja web de cliente CSP](csp-customer-web-storefront.md) e [aplicação de teste de consola.](console-test-app.md)

## <a name="considerations"></a>Considerações

O CSP Customer Storefront Builder pretende ser uma forma rápida de criar um website. Esteja ciente das seguintes considerações durante o seu planeamento:

- Uma vez implementado, a Microsoft e o Partner Center não mantêm uma cópia do website do parceiro ou qualquer informação adicionada ao Construtor de Lojas de Clientes CSP.

- O Partner Center só pode implementar um website CSP Customer Storefront para as subscrições Azure de um parceiro.

- Este site, uma vez implementado, é totalmente propriedade e gerido pelo parceiro. A Microsoft não tem acesso a este website, nem a quaisquer dados relacionados com o website. Os parceiros são responsáveis pela manutenção e gestão do website. A Microsoft não fornecerá nenhum website ao vivo ou outro suporte relacionado com o CSP Customer Storefront Builder ou qualquer website criado através do CSP Customer Storefront Builder.

- O Partner Center não pode aceder diretamente ou atualizar este website com funcionalidades novas ou alteradas de SDK ou API. Quaisquer novas funcionalidades ou melhorias devem ser possuídas, desenvolvidas e geridas por parceiros, incluindo a adição de novas funcionalidades do Partner Center SDK ou API.

- Este CSP Customer Storefront Builder fornece atualmente a capacidade de configurar o pagamento a uma conta pro/PayU Money (para a Índia) de PayPal. Se os parceiros precisarem de alterar o processador de pagamento, terão de alterar o código para suportar o seu método de pagamento preferido.

- Qualquer informação relacionada com o pagamento adicionada no CSP Customer Storefront Builder não é armazenada ou mantida no Partner Center.

- PayPal configuração de pagamento funcionará em quaisquer geografias onde PayPal esteja disponível. PayPal disponibilidade e suporte é controlado exclusivamente por PayPal, podendo ser descontinuado a qualquer momento por PayPal.

- A configuração de pagamento payU funcionará apenas na Índia atualmente. A disponibilidade e suporte payU são controlados exclusivamente pelo PayU e podem ser descontinuados a qualquer momento pelo PayU.

- Leia e compreenda os termos no [Centro Parceiro SDK EULA](https://partnercenter.microsoft.com/partner/EULA_Partner_Center_SDK).

## <a name="using-the-csp-customer-storefront-builder"></a>Utilizando o Construtor de Loja de Clientes CSP

Os administradores de parceiros da CSP no Partner Center podem implantar uma Loja de Clientes CSP diretamente do Partner Center. Com o mínimo de esforço, um novo site pode ser implantado no inquilino do parceiro. Uma vez implementados, os parceiros podem usar o site para configurar branding, ofertas e informações relacionadas com o pagamento e, em seguida, partilhar o endereço URL do site com os clientes.

O processo de criação de um website de fachada é:

1. [Implementar o site](#deploy)

2. [Configure a montra](#configure)

3. [Transact na montra](#transact)

### <a name="deploy"></a>Implementação

Opções de implementação:

- Descarregue o código de amostra da [loja Partner Center](https://github.com/Microsoft/Partner-Center-Storefront) do GitHub
- Integre com a Azure para implementar o site configurado
- Implementar numa subscrição existente ou trazer a sua própria subscrição

### <a name="configure"></a>Configurar

Não são necessárias competências de desenvolvimento para personalizar uma montra.

Inicie sessão com as credenciais de administração do Centro Parceiro para configurar:

- **Marca:** nome da empresa, logotipo, contactos e muito mais.

- **Ofertas**: veja todas as ofertas da CSP. Pode selecionar quais as ofertas que os seus clientes podem ver e comprar. Também pode personalizar a oferta de informação e adicionar o seu preço.

- **PayPal configuração de pagamento:** adicione a informação da sua conta de pagamento PayPal. Se não tiver uma conta PayPal, pode visitar [https://www.paypal.com](https://www.paypal.com) e criar uma nova conta. Esta conta será utilizada para PayPal para creditar os pagamentos efetuados pelos clientes. *A Microsoft não é responsável pela relação entre parceiros e PayPal. A utilização de PayPal pode exigir que os clientes do parceiro ou do parceiro concordem com termos adicionais.*

- (Para *a Índia)* **Configuração de pagamento:** adicione as informações da sua conta de pagamento PayU Money. Se não tiver uma conta PayU Money, pode visitar [https://www.payumoney.com/](https://www.payumoney.com/) e criar uma nova conta. Esta conta será utilizada para o PayU para creditar os pagamentos efetuosos pelos clientes. *A Microsoft não é responsável pela relação entre parceiros e PayU. A utilização do PayU pode exigir que os clientes do parceiro ou do parceiro concordem com termos adicionais.*

### <a name="transact"></a>Transação

- Após a implementação, os clientes podem imediatamente comprar e transacionar.

- Os clientes podem comprar diretamente a partir do portal parceiro integrado com o Partner Center SDK.

#### <a name="customer-countries"></a>Países de clientes

Os clientes podem pertencer a estes países:

| Código do País | Nome do País   |
|--------------|----------------|
| AU           | Austrália      |
| AT           | Áustria        |
| BE           | Bélgica        |
| BG           | Bulgária       |
| CA           | Canadá         |
| HR           | Croácia        |
| CY           | Chipre         |
| CZ           | República Checa |
| DK           | Dinamarca        |
| EE           | Estónia        |
| FI           | Finlândia        |
| FR           | França         |
| DE           | Alemanha        |
| GR           | Grécia         |
| HU           | Hungria        |
| IS           | Islândia        |
| IN           | Índia          |
| IE           | Irlanda        |
| TI           | Itália          |
| JP           | Japão          |
| LV           | Letónia         |
| LI           | Listenstaine  |
| LT           | Lituânia      |
| LU           | Luxemburgo     |
| MT           | Malta          |
| MC           | Mónaco         |
| NL           | Países Baixos    |
| NZ           | Nova Zelândia    |
| NO           | Noruega         |
| Po           | Polónia         |
| PT           | Portugal       |
| RO           | Roménia        |
| SK           | Eslováquia       |
| SL           | Eslovénia       |
| ES           | Espanha          |
| SE           | Suécia         |
| CH           | Suíça    |
| GB           | Reino Unido |
| EUA           | Estados Unidos da América  |

## <a name="partner-experience-scenarios"></a>Cenários de experiência de parceiros

### <a name="deployment-scenario"></a>Cenário de implementação

Para implementar uma loja de clientes CSP melhorada ou personalizada:

- Descarregue o [código de amostra da montra](https://github.com/Microsoft/Partner-Center-Storefront) do Partner Center para fazer personalizações adicionais.

- Utilize o Microsoft Visual Studio 2015 (ou mais tarde) para desenvolver.

- Construa para alterações e melhorias adicionais (incluindo autorizações, certificações, alterações manifestas e outros itens).

### <a name="configuration-scenario"></a>Cenário de configuração

- O site recém-criado está ligado a um inquilino parceiro e tem acesso a todas as contas de administração deste inquilino parceiro.

  - Os parceiros podem iniciar sessão neste novo website utilizando as suas credenciais de administração partner Center.

- A aplicação de fachada da loja atualmente suporta francês, espanhol, holandês, alemão, japonês e inglês. (O inglês serve como a língua de recuo.)

  - A montra configura o local utilizando o local padrão do parceiro a partir do perfil do parceiro no Partner Center. Este local é usado para configurar moedas, formatos de data e ofertas localizadas no repositório.

- Os parceiros podem configurar a marca, ofertas e PayPal ou payU (para a Índia) informações de pagamento.

- Os parceiros podem atualizar o nome da empresa, logotipo da empresa, imagem de cabeçalho, contactos de vendas e suporte e muito mais.

- Os parceiros podem ver todas as ofertas da CSP disponíveis com base no seu território.

  - Os parceiros podem escolher quais as ofertas que querem mostrar a todos os seus clientes.

  - Um parceiro CSP pode selecionar uma ou mais ofertas e atualizar o nome, quantidade, descrição do recurso e preço.
  - O preço é o preço anual. Os clientes subscrevem anualmente.

- Os parceiros podem, a qualquer momento, configurar transações pré-aprovadas para (a) todos os clientes atuais e futuros OR (b) clientes específicos.

  - Os clientes pré-aprovados não são obrigados a pagar no portal quando adicionam novas subscrições, compram licenças adicionais às subscrições existentes ou renovam uma subscrição.

  - Os clientes pré-aprovados não serão redirecionados para PayPal ou PayU (para a Índia) para pagamento durante estas transações.

  - As transações de clientes pré-aprovadas permitem que um parceiro realize faturação offline e faturação aos seus clientes pré-aprovados.

- Um parceiro CSP pode inserir as suas informações de conta PayPal, tais como PayPal ID do Cliente e secreta. Um parceiro CSP também pode selecionar se quer testar usando uma caixa de areia ou uma conta ao vivo.

  - Os parceiros podem encontrar esta informação [https://developer.paypal.com/](https://developer.paypal.com/) nas **minhas apps & credenciais.** Também pode obter esta informação a partir de uma aplicação atual ou criando uma nova aplicação em PayPal.
  - Crie uma nova conta PayPal se ainda não tiver uma. Esta conta será utilizada para PayPal para creditar os pagamentos efetuados pelos clientes.

    - Para abrir uma conta de negócios PayPal, [https://developer.paypal.com/docs/classic/lifecycle/goingLive/#register](https://developer.paypal.com/docs/classic/lifecycle/goingLive/#register) veja.

    - Para criar uma conta PayPal caixa de areia ver [https://developer.paypal.com/docs/classic/lifecycle/ug_sandbox/](https://developer.paypal.com/docs/classic/lifecycle/ug_sandbox/) .

- (Para a Índia) um parceiro CSP pode inserir as suas informações de conta PayU Money, tais como ID do Cliente PayU e senha. Os parceiros podem encontrar mais informações sobre [https://developer.payumoney.com/](https://developer.payumoney.com/) .

  - Crie uma nova conta PayU Money se ainda não tiver uma. Para abrir uma conta PayU Money, [https://www.payumoney.com/merchant-account/#/](https://www.payumoney.com/merchant-account/#/) visite. Esta conta será utilizada para o PayU para creditar os pagamentos efetuosos pelos clientes.

## <a name="customer-experience-scenarios"></a>Cenários de experiência do cliente

### <a name="new-customer-sign-up-scenario"></a>Novo cenário de inscrição de clientes

- Por padrão, o site está disponível ao público e mostra o catálogo do parceiro na página inicial.

- Os clientes podem agora pertencer a um grande número de [países](#customer-countries)de clientes.

- O foco tem sido para os países da Associação Europeia de Comércio Livre (EFTA), América do Norte, Japão, Índia, Austrália e Nova Zelândia.
  - Esta funcionalidade utiliza o suporte de autorização regional no Partner Center SDK.

- Os clientes podem selecionar uma oferta do catálogo para comprar.
  - Podem adicionar o seu nome de cliente, endereço e informações relacionadas com o domínio.

- Os clientes serão direcionados para a experiência de check-out PayPal ou PayU (para a Índia). Os clientes podem fornecer pagamento usando:
  - A sua conta de PayPal ou PayU existente (para a Índia)
  - Instrumentos de financiamento apoiados no seu país por PayPal ou PayU (para a Índia). Estes podem incluir cartões de crédito, cartões de débito e contas bancárias, conforme aplicável.

- Um inquilino de cliente é criado para este cliente. Após a criação bem sucedida da encomenda do arrendatário, os clientes recebem o nome de utilizador da conta, palavra-passe e detalhes da subscrição.
  - Os clientes podem guardar o nome de utilizador e a palavra-passe para se manterem ligados para mais compras.
  - Cada subscrição é comprada por um ano e os clientes podem renovar nos 30 dias anteriores à data final da subscrição.

### <a name="view-prior-purchases-scenario"></a>Ver cenário de compras anteriores

- O cliente assina com o nome de utilizador e senha do cliente e vai para a secção **My Orders.**

- Os clientes podem navegar para a página **My Orders** onde podem ver subscrições adquiridas e fazer atualizações se necessário.

- Os clientes podem navegar para a página **My Subscriptions** onde podem ver todas as subscrições (baseadas em licenças, bem como baseadas em uso), incluindo as mantidas no Partner Center.

### <a name="add-licenses-to-existing-subscriptions-scenario"></a>Adicionar licenças ao cenário de subscrições existentes

- A partir da secção **My Orders,** os clientes podem adicionar mais licenças às subscrições existentes. Os clientes podem adicionar mais licenças a qualquer momento durante um ano de subscrição.

- Cada licença adicionada não altera a data de fim da subscrição. No entanto, o preço da subscrição muda com base na data em que adiciona a licença, e onde essa data é no ano. Os preços são prossurados diariamente apenas para os restantes dias do ano.

### <a name="add-more-subscriptions-scenario"></a>Adicionar mais cenário de subscrições

- Os clientes podem comprar qualquer número de subscrições a qualquer momento a partir da secção **de subscrições Adicionar** ao abrigo das **Minhas Ordens.**

- Um cliente pode selecionar uma subscrição, adicionar uma quantidade e pagar para completar a transação e começar a usar a subscrição imediatamente. Se um cliente for um cliente pré-aprovado, a subscrição está disponível para uso imediato e uma fatura será enviada ao cliente para pagamento.

### <a name="renew-subscription-scenario"></a>Renovar cenário de subscrição

- Um cliente pode renovar uma subscrição durante os últimos 30 dias antes da data de final da subscrição.

- Isto só está disponível nos últimos 30 dias.

- Se não for renovada nos últimos 30 dias, a subscrição será removida da lista de subscrições deste inquilino cliente.

- Não é possível atualizar a quantidade durante a renovação.

### <a name="payments-scenario"></a>Cenário de pagamentos

- Se o cliente for pré-aprovado para transações pela administração, a experiência de pagamento não é apresentada para os cenários acima referidos. Em vez disso, o parceiro pode enviar a fatura para pagamento ao cliente pré-aprovado.

- Para todas as novas compras, pode adicionar mais licenças, adicionar subscrições e renovar. Um cliente pode pagar a um parceiro usando este site através de PayPal ou PayU (para a Índia).

- Este website está integrado com PayPal ou PayU (para a Índia) e permite que os parceiros aceitem pagamentos dos seus clientes. PayPal ou PayU (para a Índia) credita este valor na conta de um parceiro. PayPal ou PayU (para a Índia) A gestão de conta bancária está fora deste website e é gerida em PayPal.com ou PayUmoney.com respectivamente.

- Isto depende de parceiros que configuram a sua configuração de pagamento PayPal ouPayU (para a Índia) em PayPal.com ou PayUmoney.com. A Microsoft não guarda estas informações ou operações de pagamento reais resultantes da utilização desta opção.

### <a name="prorated-pricing-scenario"></a>Cenário de preços prolored

- Este site suporta preços provalorizados em casos em que os clientes adicionam mais licenças a uma subscrição existente.

- Cada subscrição expira após um ano e não pode ser alterada após a compra da subscrição.

- A data final da subscrição não será alterada adicionando licenças adicionais. Os clientes serão cobrados pelo número restante de dias até à data limite. Por exemplo, se no primeiro dia o custo da subscrição for de $365, e adicionar mais uma licença no segundo dia, o preço da nova licença será de $364. Se adicionar mais uma licença 10 dias depois, o preço será $354.
