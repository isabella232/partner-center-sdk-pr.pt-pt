---
title: Obtenha um link de descarregamento para o modelo do Contrato de Cliente da Microsoft
description: Obtenha um link de descarregamento para o modelo do Microsoft Customer Agreement.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 7757cd6a92c168e4209d2d3ac49746e4a0907021d260a7b49603a3706e8cfa5c
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994817"
---
# <a name="get-a-download-link-for-the-microsoft-customer-agreement-template"></a>Obtenha um link de descarregamento para o modelo do Contrato de Cliente da Microsoft

**Aplica-se a**: Centro de Parceiros

**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

O recurso **AgreementDocument** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.

Este artigo descreve como obter um link para descarregar o modelo de Acordo de Cliente da Microsoft, com base no país e no idioma do cliente.

## <a name="prerequisites"></a>Pré-requisitos

- Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.

- Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md). Este cenário suporta apenas a autenticação App+User.

- O país do cliente ao qual se aplica o modelo de Cliente da Microsoft.

- O idioma no qual o modelo de Acordo de Cliente da Microsoft deve ser localizado.

> [!IMPORTANT]
>
> - O Microsoft Customer Agreement é específico por país. Ao solicitar um link para descarregar o modelo do Microsoft Customer Agreement, certifique-se de especificar o país correto com base na localização do cliente. ou lista de países apoiados, consulte a [Lista de países e línguas apoiados.](#list-of-supported-countries-and-languages)
>
> - Para alguns países, o Microsoft Customer Agreement está disponível em vários idiomas. Para melhor experiência do cliente, escolha o idioma que melhor corresponda às necessidades do cliente. Para a lista de línguas apoiadas, consulte a [Lista de países e línguas apoiados.](#list-of-supported-countries-and-languages)
> - Este método só é suportado com o Microsoft Customer Agreement.

## <a name="net"></a>.NET

Para obter um link para descarregar o modelo do Microsoft Customer Agreement:

1. Recupere os metadados do acordo para o Acordo de Cliente da Microsoft. Tem de obter o **modeloId** do Microsoft Customer Agreement. Para obter mais informações, consulte [obter metadados de acordo para o Acordo de Cliente da Microsoft.](get-customer-agreement-metadata.md)

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   AgreementMetaData microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.   ByAgreementType(agreementType).Get().Items.Single();
   ```

2. Utilize a coleção IAggregatePartner.AgreementTemplates.

3. Ligue para o método **ById** e especifique o **modeloId** do Microsoft Customer Agreement.

4. Pegue a propriedade **Document.**

5. Ligue para o método **ByCountry** e especifique o país do cliente ao qual o modelo de contrato se aplica. A consulta é padrão para *nós* se o método não for especificado. Para obter uma lista de códigos de países apoiados, consulte a [Lista de países e línguas apoiados.](#list-of-supported-countries-and-languages) Este método é **sensível a casos.**

6. Ligue para o método **ByLanguage** e especifique o idioma em que o modelo de acordo deve ser localizado. A consulta é padrão para *en-US* se o método não for especificado ou o código de país especificado não for suportado para o país especificado. Para obter a lista de códigos linguísticos suportados, consulte a [Lista de países e línguas apoiados.](#list-of-supported-countries-and-languages)

7. Ligue para o método **Get** or **GetAsync.**

   ```csharp
   // IAggregatePartner partnerOperations;

   string customerCountry = "US";

   string languageForLocalization = "en-US";

   var agreementDocument = partnerOperations.   AgreementTemplates.ById   (microsoftCustomerAgreementDetails.   TemplateId).Document.ByCountry   (customerCountry).ByLanguage   (languageForLocalization).Get();
   ```

Uma amostra completa pode ser encontrada na classe [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.

## <a name="rest-request"></a>Pedido de DESCANSO

Para obter um link para descarregar o modelo do Microsoft Customer Agreement:

1. Recupere os metadados do acordo para o Acordo de Cliente da Microsoft. Tem de obter o **modeloId** do Microsoft Customer Agreement. Para obter mais informações, consulte [obter metadados de acordo para o Acordo de Cliente da Microsoft.](get-customer-agreement-metadata.md)

2. Crie um pedido DE ACORDO para obter um recurso [ **AgreementDocument**](./agreement-document-resources.md). Por exemplo, consulte o exemplo da sintaxe do [pedido.](#request-syntax) Deve especificar as seguintes informações:

    - O **modeloId** do Microsoft Customer Agreement.
    - O país ao qual se aplica o modelo de Acordo de Cliente da Microsoft.
    - O idioma no qual o modelo de Acordo de Cliente da Microsoft deve ser localizado.

### <a name="request-syntax"></a>Solicitar sintaxe

Utilize a seguinte sintaxe de pedido para este recurso:

| Método | URI do pedido |
|--------|---------------------------------------------------------------------|
| GET | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreementtemplates/{agreement-template-id}/document?language={language}&country={country} HTTP/1.1 |

### <a name="uri-parameters"></a>Parâmetros URI

Pode utilizar os seguintes parâmetros URI com o seu pedido:

| Nome                   | Tipo   | Necessário | Descrição                                 |
|------------------------|--------|----------|---------------------------------------------|
| acordo-modelo-id  | string | Yes      | Identificador único do tipo de acordo. Pode obter o modeloId para o Acordo de Cliente da Microsoft recuperando os metadados do acordo para o Microsoft Customer Agreement. Para obter mais informações, consulte [obter metadados de acordo para o Acordo de Cliente da Microsoft.](./get-customer-agreement-metadata.md) Este parâmetro é **sensível a maiôs.**|
| país                | cadeia (de carateres) | No       | Indica o país ao qual se aplica o modelo de acordo. A consulta é padrão para *nós* se o parâmetro não for especificado. Para obter uma lista de códigos de países apoiados, consulte a [Lista de países e línguas apoiados.](#list-of-supported-countries-and-languages)|
| language               | cadeia (de carateres) | No       | Indica o idioma no qual o modelo de contrato deve ser localizado. A consulta é padrão para *en-US* se o parâmetro não for especificado ou o código de país especificado não suportado para o país especificado. Para obter a lista de códigos de países suportados, consulte a [Lista de países e línguas apoiados.](#list-of-supported-countries-and-languages)|

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partnercenter.microsoft.com/v1/agreementtemplates/117a77b0-9360-443b-8795-c6dedc750cf9/document?language=en-US&country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve um recurso [ **AgreementDocument**](./agreement-document-resources.md) no organismo de resposta.

O recurso tem uma propriedade **downloadUri,** que contém uma cadeia DE URL que pode ser usada para descarregar o modelo de contrato. Um link diferente é devolvido cada vez que faz uma consulta. Esta ligação expira após cinco minutos.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.

Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 200 OK
Content-Length: 620
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "displayUri":"https://wopihost.int.l2o.microsoft.com/v1/officehost/agreement/files/Preview...",
    "downloadUri":"https://l2oagreementintbn2.blob.core.windows.net/agreementscontainer/Preview...",
    "language":"en-US",
    "country":"US"
}
```

## <a name="list-of-supported-countries-and-languages"></a>Lista de países e línguas apoiados

> [!IMPORTANT]
> A propriedade do código do país é sensível a casos. Por favor, certifique-se de que utiliza o invólucro correto especificado na tabela abaixo.

| País                   | Indicativo do país   | Códigos linguísticos suportados |
|------------------------|--------|----------|
| Ilhas Åland | AX | en-PT |
| Afeganistão | AF | en-PT |
| Albânia | AL | en-PT |
| Argélia | DZ | en-US, fr-FR, en-US |
| Samoa Americana | AS | en-PT |
| Andorra | AD | en-PT |
| Angola | AO | en-US, pt-PT |
| Anguila | IA | en-PT |
| Antártica | AQ | en-PT |
| Antígua e Barbuda | AG | en-PT |
| Argentina | AR | en-EUA, es-ES |
| Arménia | AM | en-PT |
| Aruba | AW | en-PT |
| Austrália | AU | en-PT |
| Áustria | AT | en-US, de-DE |
| Azerbaijão | AZ | en-PT |
| Baamas | BS | en-PT |
| Barém | BH | en-EUA, ar-SA |
| Bangladesh | BD | en-PT |
| Barbados | BB | en-PT |
| Bielorrússia | BY | en-EUA, ru-RU |
| Bélgica | BE | en-US, nl-NL |
| Belize | BZ | en-EUA, es-ES |
| Benim | BJ | en-PT |
| Bermudas | BM | en-PT |
| Butão | BT | en-PT |
| Bolívia | BO | en-EUA, es-ES |
| Bonaire | BQ | en-PT |
| Bósnia e Herzegovina | BA | en-PT |
| Botsuana | BW | en-PT |
| Ilha Bouvet | BV | en-PT |
| Brasil | BR | en-US, pt-BR |
| Território Britânico do Oceano Índico | E/S | en-PT |
| Ilhas Virgens Britânicas | VG | en-PT |
| Brunei | BN | en-PT |
| Bulgária | BG | en-EUA, bg-BG |
| Burkina Faso | BF | en-PT |
| Burundi | BI | en-PT |
| Costa do Marfim (Côte d’Ivoire) | CI | en-EUA, fr-FR |
| Cabo Verde | CV | en-US, pt-PT |
| Camboja | KH | en-PT |
| Camarões | CM | en-EUA, fr-FR |
| Canadá | CA | en-EUA, fr-FR |
| Ilhas Caimão | KY | en-EUA, en-US |
| República Centro-Africana | CF | en-PT |
| Chade | DT | en-PT |
| Chile | CL | en-EUA, es-ES |
| Ilha do Natal | CX | en-PT |
| Ilhas dos Cocos (Keeling) | CC | en-PT |
| Colômbia | CO | en-EUA, es-ES |
| Comoros | KM | en-PT |
| República Democrática do Congo | CD | en-PT |
| Congo | CG | en-PT |
| Ilhas Cook | CK | en-PT |
| Costa Rica | CR | en-EUA, es-ES |
| Croácia | HR | en-US, hr-HR |
| Curaçao | CW | en-PT |
| Chipre | CY | en-PT |
| Checa | CZ | en-EUA, cs-CZ |
| Dinamarca | DK | en-EUA, da-DK |
| Jibuti | DJ | en-PT |
| Dominica | DM | en-PT |
| República Dominicana | DO | en-EUA, es-ES |
| Equador | EC | en-PT |
| Egito | EG | en-EUA, ar-SA |
| Salvador | SV | en-EUA, es-ES |
| Guiné Equatorial | GQ | en-PT |
| Eritreia | ER | en-PT |
| Estónia | EE | en-EUA, et-EE |
| eSwatini | SZ | en-PT |
| Etiópia | ET | en-PT |
| Ilhas Falkland (Malvinas) | FK | en-PT |
| Ilhas Faroé | FO | en-PT |
| Fiji | FJ | en-PT |
| Finlândia | FI | en-US, fi-FI |
| França | FR | en-EUA, fr-FR |
| Guiana Francesa | GF | en-EUA, fr-FR  |
| Polinésia Francesa | PF | en-PT |
| Territórios Austrais Franceses | TF | en-PT |
| Gabão | GA | en-PT |
| Gâmbia | GM | en-PT |
| Geórgia | GE | en-PT |
| Alemanha | DE | en-US, de-DE |
| Gana | GH | en-PT |
| Gibraltar | GI | en-PT |
| Grécia | GR | en-US, el-GR |
| Gronelândia | GL | en-PT |
| Granada | GD | en-PT |
| Guadalupe | GP | en-PT |
| Guame | GS | en-PT |
| Guatemala | GT | en-EUA, es-ES |
| Guernesey | GG | en-PT |
| Guiné | GN | en-PT |
| Guiné-Bissau | GW | en-PT |
| Guiana | GY | en-PT |
| Haiti | HT | en-PT |
| Ilhas Heard e McDonald | HM | en-PT |
| Honduras | HN | en-EUA, es-ES |
| R.A.E. de Hong Kong | HK | en-EUA, zh-HK |
| Hungria | HU | en-EUA, hu-HU |
| Islândia | IS | en-PT |
| Índia | IN | en-US, hi-IN |
| Indonésia | ID | en-US, id-ID |
| Iraque | IQ | en-EUA, ar-SA |
| Irlanda | IE | en-PT |
| Ilha de Man | MI | en-PT |
| Israel | IL | en-EUA, he-IL |
| Itália | TI | en-EUA, it-IT |
| Jamaica | JM | en-PT |
| Jan Mayen | XJ | en-PT |
| Japão | JP | en-US, ja-JP |
| Jersey | JE | en-PT |
| Jordânia | JO | en-EUA, ar-SA |
| Cazaquistão | KZ | en-EUA, kk-KZ |
| Quénia | KE | en-PT |
| Quiribáti | KI | en-PT |
| Coreia | KR | en-EUA, ko-KR |
| Kosovo | XK | en-PT |
| Koweit | KW | en-EUA, ar-SA |
| Quirguistão | KG | en-EUA, ru-RU |
| Laos | LA | en-PT |
| Letónia | LV | en-EUA, lv-LV |
| Líbano | LB | en-EUA, ar-SA |
| Lesoto | LS | en-PT |
| Libéria | LR | en-PT |
| Líbia | LY | en-EUA, ar-SA |
| Listenstaine | LI | en-US, de-DE |
| Lituânia | LT | en-US, LT |
| Luxemburgo | LU | en-EUA, fr-FR |
| RAE de Macau | MO | en-EUA, zh-HK |
| Macedónia | MK | en-PT |
| Madagáscar | MG | en-PT |
| Maláui | MW | en-PT |
| Malásia | MY | en-US, MS-MY |
| Maldivas | MV | en-PT |
| Mali | ML | en-PT |
| Malta | MT | en-PT |
| Ilhas Marshall | MH | en-PT |
| Martinica | MQ | en-PT |
| Mauritânia | MR | en-PT |
| Maurícias | MU | en-EUA, ar-SA |
| Maiote | YT | en-PT |
| México | MX | en-EUA, es-ES |
| Micronésia | FM | en-PT |
| Moldávia | MD | en-US, ro-RO |
| Mónaco | MC | en-EUA, fr-FR |
| Mongólia | MN | en-PT |
| Montenegro | ME | en-PT |
| Montserrate | MS | en-PT |
| Marrocos | MA | en-US, fr-FR, en-US |
| Moçambique | MZ | en-PT |
| Mianmar | MM | en-PT |
| Namíbia | ND | en-PT |
| Nauru | NR | en-PT |
| Nepal | NP | en-PT |
| Países Baixos | NL | en-US, nl-NL |
| Nova Caledónia | NC | en-PT |
| Nova Zelândia | NZ | en-PT |
| Nicarágua | NI | en-EUA, es-ES |
| Níger | NE | en-PT |
| Nigéria | NG | en-PT |
| Niuê | NU | en-PT |
| Ilha Norfolk | NF | en-PT |
| Ilhas Marianas do Norte | BM | en-PT |
| Noruega | NO | en-EUA, nb-NO |
| Omã | OM | en-EUA, ar-SA |
| Paquistão | PK | en-PT |
| Palau | PW | en-PT |
| Autoridade Palestiniana | PS | en-PT |
| Panamá | PA | en-EUA, es-ES |
| Papua-Nova Guiné | PG | en-PT |
| Paraguai | PY | en-EUA, es-ES |
| Peru | PE | en-EUA, es-ES |
| Filipinas | PH | en-PT |
| Ilhas Pitcairn | PN | en-PT |
| Polónia | PL | en-US, pl-PL |
| Portugal | PT | en-US, pt-PT |
| Porto Rico | PR | en-EUA, en-US |
| Catar | QA | en-EUA, ar-SA |
| Reunião | RE | en-PT |
| Roménia | RO | en-US, ro-RO |
| Rússia | RU | en-EUA, ru-RU |
| Ruanda | RW | en-EUA, fr-FR |
| São Tomé e Príncipe | ST | en-EUA, fr-FR |
| Saba | XS | en-PT |
| Saint-Barthélemy | BL | en-PT |
| São Cristóvão e Neves | KN | en-PT |
| Santa Lúcia | LC | en-EUA, en-US |
| São Martinho (Saint Martin) | MF | en-EUA, en-US |
| São Pedro e Miquelão | PM | en-PT |
| São Vicente e Granadinas | VC | en-PT |
| Samoa | WS | en-PT |
| São Marino | SM | en-PT |
| Arábia Saudita | SA | en-PT |
| Senegal | SN | en-EUA, fr-FR |
| Sérvia | RS | en-US, sr-Latn-RS, en-US |
| Seicheles | SC | en-PT |
| Serra Leoa | SL | en-PT |
| Singapura | SG | en-EUA, zh-SG |
| Santo Eustáquio | XE | en-PT |
| São Martinho (Sint Maarten) | SX | en-EUA, en-US |
| Eslováquia | SK | en-US, sk-SK |
| Eslovénia | SI | en-EUA, sl-SI |
| Ilhas Salomão | SB | en-PT |
| Somália | SO | en-PT |
| África do Sul | ZA | en-PT |
| Ilhas Geórgia do Sul e Sandwich do Sul | GS | en-PT |
| Sudão do Sul | SS | en-PT |
| Espanha | ES | en-EUA, es-ES, en-US, en-US |
| Sri Lanca | LK | en-PT |
| Santa Helena, Ascensão, Tristão da Cunha | SH | en-PT |
| Suriname | SR | en-PT |
| Svalbard | SJ | en-PT |
| Suécia | SE | en-EUA, sv-SE |
| Suíça | CH | en-US, fr-FR, en-US, en-US |
| Taiwan | TW | en-EUA, zh-HK |
| Tajiquistão | TJ | en-PT |
| Tanzânia | TZ | en-PT |
| Tailândia | TH | en-EUA, th-TH |
| Timor-Leste | TL | en-PT |
| Togo | TG | en-PT |
| Toquelau | TK | en-PT |
| Tonga | TO | en-PT |
| Trindade e Tobago | TT | en-PT |
| Tunísia | TN | en-US, fr-FR, en-US |
| Turquia | TR | en-EUA, tr-TR |
| Turquemenistão | TM | en-PT |
| Ilhas Turcas e Caicos | TC | en-PT |
| Tuvalu | TV | en-PT |
| Ilhas Desondo dos EUA | UM | en-PT |
| Ilhas Virgens Americanas | VI | en-PT |
| Uganda | UG | en-PT |
| Ucrânia | UA | en-EUA, uk-UA |
| Emirados Árabes Unidos | AE | en-EUA, ar-SA |
| Reino Unido | GB | en-PT |
| Estados Unidos da América | EUA | en-PT |
| Uruguai | UY | en-EUA, es-ES |
| Usbequistão | UZ | en-EUA, ru-RU |
| Vanuatu | VU | en-PT |
| Cidade do Vaticano | VA | en-PT |
| Venezuela | VE | en-EUA, es-ES |
| Vietname | VN | en-US, vi-VN |
| Wallis e Futuna | WF | en-PT |
| Iémen | YE | en-EUA, ar-SA |
| Zâmbia | ZM | en-PT |
| Zimbabué | ZW | en-PT |
