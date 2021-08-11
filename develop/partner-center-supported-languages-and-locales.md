---
title: Regiões e idiomas suportados pelo Centro de Parceiros
description: Lista de locais apoiados pela ISO2 e pela ISO3 para o Partner Center.
ms.date: 12/03/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 6f2e1d50fa0f2ace2e94f4dbb5681e2164241ee57a85249136a55fce20893fbb
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997588"
---
# <a name="partner-center-supported-languages-and-locales"></a>Regiões e idiomas suportados pelo Centro de Parceiros

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Algumas APIs do Centro de Parceiros requerem um valor que indique um local, país ou região. Por exemplo, o [cabeçalho](headers.md) do Partner Center REST X-Locale requer um valor frequentemente no formato "language-country" ("en-US" indica "Inglês - Estados Unidos").

No Partner Center gerido APIs, a classe [CountryValidationRules/dotnet/api/microsoft.store.partnercenter.models.offercategory.locale), [ServiceCategory.Locale/dotnet/api/microsoft.store.partnercenter.offercategory.locale), [ServiceRequest.CountryCode/dotnet/dotnet.partnercenter.offer.offercategory.locale), [ServiceRequest.CountryCode/dotnet/dotnet/dotnet.partnercenter.offer.offercategory.locale), [ServiceRequest.CountryCode/dotnet/dotnet/dotnet.partnercenter.offers.offercategory.locale), [ServiceRequest.CountryCode/dotnet.partnercenter.offer.offercategory.locale), [ServiceRequest.CountryCode/dotnet/dotnet/dotnet./api/microsoft.store.partnercenter.models.servicerequests.servicerequest.countrycode), ou [CustomerBillingProfile.Culture/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile.culture) requerem valores de cordas que indicam uma língua ou país/região (sob a forma de um código linguístico ISO2 ou código iso3 country/região), um código local, ou uma cultura (um ID de língua combinado com um código país/região).

A tabela que se segue lista os códigos de país da Organização das Culturas e Padrões Internacionais (ISO) que são suportados nas APIs do Partner Center.

| País/Região                           | ISO Alpha 2 Country Code | ISO Alpha 3 Country Code | Culturas apoiadas                  |
|------------------------------------------|--------------------------|--------------------------|---------------------------------------|
| Afeganistão                              | AF                       | AFG                      | ps-AF / en-US                         |
| Ilhas Åland                            | AX                       | RIO ALA                      | sv-SE / en-US                         |
| Albânia                                  | AL                       | ALB                      | sq-AL / en-US                         |
| Argélia                                  | DZ                       | DZA                      | ar-DZ / en-US                         |
| Samoa Americana                           | AS                       | ASM                      | en-PT                                 |
| Andorra                                  | AD                       | AND                      | ca-ES / en-US                         |
| Angola                                   | AO                       | AGO                      | pt-PT / en-US                         |
| Anguila                                 | IA                       | AIA                      | en-PT                                 |
| Antártica                               | AQ                       | ATA                      | en-PT                                 |
| Antígua e Barbuda                      | AG                       | ATG                      | en-PT                                 |
| Argentina                                | AR                       | ARG                      | es-AR / en-US                         |
| Arménia                                  | AM                       | ARM                      | hy-AM / en-US                         |
| Aruba                                    | AW                       | ABW                      | nl-NL / en-US                         |
| Austrália                                | AU                       | AUS                      | en-AU / en-US                         |
| Áustria                                  | AT                       | AUT                      | de-AT / en-US                         |
| Azerbaijão                               | AZ                       | RIO AZE                      | az-Latn-AZ / en-US                    |
| Baamas                                  | BS                       | BHS                      | en-GB / en-US                         |
| Barém                                  | BH                       | BHR                      | ar-BH / en-US                         |
| Bangladesh                               | BD                       | BGD                      | bn-BD / en-US                         |
| Barbados                                 | BB                       | BRB                      | en-GB / en-US                         |
| Bielorrússia                                  | BY                       | BLR                      | be-BY / en-US                         |
| Bélgica                                  | BE                       | BEL                      | fr-BE / nl-BE / en-US                 |
| Belize                                   | BZ                       | BLZ                      | en-BZ / en-US                         |
| Benim                                    | BJ                       | BEN                      | fr-FR / en-US                         |
| Bermudas                                  | BM                       | Rio BMU                      | en-GB / en-US                         |
| Butão                                   | BT                       | BTN                      | en-PT                                 |
| Bolívia                                  | BO                       | BOL                      | es-BO / en-US                         |
| Bonaire                                  | BQ                       | BES                      | nl-NL / en-US                         |
| Bósnia e Herzegovina                   | BA                       | BIH                      | bs-Latn-BA / en-US                    |
| Botsuana                                 | BW                       | BWA                      | en-GB / en-US                         |
| Ilha Bouvet                            | BV                       | Rio BVT                      | nb-NO / en-US                         |
| Brasil                                   | BR                       | BRA                      | pt-BR / en-US                         |
| Território Britânico do Oceano Índico           | E/S                       | IOT                      | en-PT                                 |
| Ilhas Virgens Britânicas                   | VG                       | VGB                      | en-PT                                 |
| Brunei                                   | BN                       | RIO BRN                      | ms-BN / en-US                         |
| Bulgária                                 | BG                       | BGR                      | bg-BG / en-US                         |
| Burkina Faso                             | BF                       | Rio BFA                      | fr-FR / en-US                         |
| Burundi                                  | BI                       | BDI                      | fr-FR / en-US                         |
| Cabo Verde                               | CV                       | CPV                      | pt-CV / en-US                         |
| Camboja                                 | KH                       | RIO KHM                      | km-KH / en-US                         |
| Camarões                                 | CM                       | CMR                      | fr-FR / en-US                         |
| Canadá                                   | CA                       | PODE                      | fr-CA / en-US                         |
| Ilhas Caimão                           | KY                       | CYM                      | en-GB / en-US                         |
| República Centro-Africana                 | CF                       | CAF                      | fr-FR / en-US                         |
| Chade                                     | DT                       | TCD                      | fr-FR / en-US                         |
| Chile                                    | CL                       | CHL                      | es-CL / en-US                         |
| China                                    | CN                       | RIO CHN                      | zh-CN / en-US                         |
| Ilha do Natal                         | CX                       | CXR                      | en-PT                                 |
| Ilhas dos Cocos (Keeling)                  | CC                       | CCK                      | en-PT                                 |
| Colômbia                                 | CO                       | COL                      | es-CO / en-US                         |
| Comoros                                  | KM                       | COM                      | fr-FR / en-US                         |
| Congo                                    | CG                       | COG                      | fr-FR / en-US                         |
| República Democrática do Congo                              | CD                       | COD                      | fr-FR / en-US                         |
| Ilhas Cook                             | CK                       | RIO COK                      | en-PT                                 |
| Costa Rica                               | CR                       | CRI                      | es-CR / en-US                         |
| Costa do Marfim (Côte d’Ivoire)                            | CI                       | CIV                      | fr-FR / en-US                         |
| Croácia                                  | HR                       | HRV                      | hr-HR / en-US                         |
| Curaçao                                  | CW                       | CUW                      | nl-NL / en-US                         |
| Chipre                                   | CY                       | CYP                      | el-GR / en-US                         |
| Checa                                  | CZ                       | CZE                      | cs-CZ / en-US                         |
| Dinamarca                                  | DK                       | DNK                      | da-DK / en-US                         |
| Jibuti                                 | DJ                       | DJI                      | fr-FR / en-US                         |
| Dominica                                 | DM                       | DMA                      | en-PT                                 |
| República Dominicana                       | DO                       | DOM                      | es-DO / en-US                         |
| Equador                                  | EC                       | ECU                      | es-EC / en-US                         |
| Egito                                    | EG                       | EGY                      | ar-EG / en-US                         |
| Salvador                              | SV                       | SLV                      | es-SV / en-US                         |
| Guiné Equatorial                        | GQ                       | GNQ                      | es-ES / en-US                         |
| Eritreia                                  | ER                       | ERI                      | ar-SA / en-US                         |
| Estónia                                  | EE                       | EST                      | et-EE / en-US                         |
| eSwatini                                 | SZ                       | SWZ                      | en-PT                                 |
| Etiópia                                 | ET                       | ETH                      | am-ET / en-US                         |
| Ilhas Falkland (Malvinas)                         | FK                       | FLK                      | en-PT                                 |
| Ilhas Faroé                            | FO                       | FRO                      | fo-FO / en-US                         |
| Fiji                                     | FJ                       | FJI                      | en-GB / en-US                         |
| Finlândia                                  | FI                       | FIN                      | fi-FI / sv-FI / en-US                 |
| França                                   | FR                       | FRA                      | fr-FR / en-US                         |
| Guiana Francesa                            | GF                       | GUF                      | fr-FR / en-US                         |
| Polinésia Francesa                         | PF                       | PYF                      | fr-FR / en-US                         |
| Territórios Austrais Franceses              | TF                       | ATF                      | fr-FR / en-US                         |
| Gabão                                    | GA                       | GAB                      | fr-FR / en-US                         |
| Gâmbia                                   | GM                       | GMB                      | en-PT                                 |
| Geórgia                                  | GE                       | GEO                      | ka-GE / en-US                         |
| Alemanha                                  | DE                       | DEU                      | de-DE / en-US                         |
| Gana                                    | GH                       | GHA                      | en-GB / en-US                         |
| Gibraltar                                | GI                       | GIB                      | en-PT                                 |
| Grécia                                   | GR                       | GRC                      | el-GR / en-US                         |
| Gronelândia                                | GL                       | RIO GRL                      | da-DK / en-US                         |
| Granada                                  | GD                       | RIO GRD                      | en-PT                                 |
| Guadalupe                               | GP                       | BPL                      | fr-FR / en-US                         |
| Guame                                     | GS                       | PASTILHA ELÁSTICA                      | en-PT                                 |
| Guatemala                                | GT                       | GTM                      | es-GT / en-US                         |
| Guernesey                                 | GG                       | GGY                      | en-PT                                 |
| Guiné                                   | GN                       | GIN                      | fr-FR / en-US                         |
| Guiné-Bissau                            | GW                       | GNB                      | pt-PT / en-US                         |
| Guiana                                   | GY                       | GUY                      | en-PT                                 |
| Haiti                                    | HT                       | HTI                      | fr-FR / en-US                         |
| Ilhas Heard e McDonald        | HM                       | HMD                      | en-PT                                 |
| Honduras                                 | HN                       | Rio HND                      | es-HN / en-US                         |
| R.A.E. de Hong Kong                            | HK                       | HKG                      | zh-HK / en-US                         |
| Hungria                                  | HU                       | HUN                      | hu-HU / en-US                         |
| Islândia                                  | IS                       | ISL                      | is-IS / en-US                         |
| Índia                                    | IN                       | IND                      | en-IN / hi-IN / en-US                 |
| Indonésia                                | ID                       | IDN                      | id-ID / en-US                         |
| Iraque                                     | IQ                       | IRQ                      | ar-QI / en-US                         |
| Irlanda                                  | IE                       | RIO IRL                      | en-IE / en-US                         |
| Ilha de Man                              | MI                       | IMN                      | en-PT                                 |
| Israel                                   | IL                       | ISR                      | he-IL / en-US                         |
| Itália                                    | TI                       | ITA                      | it-IT / en-US                         |
| Jamaica                                  | JM                       | COMPOTA                      | en-JM / en-US                         |
| Jan Mayen                                | XJ                       | XJA                      | nb-NO / en-US                         |
| Japão                                    | JP                       | JPN                      | ja-JP / en-US                         |
| Jersey                                   | JE                       | JEY                      | en-PT                                 |
| Jordânia                                   | JO                       | JOR                      | ar-JO / en-US                         |
| Cazaquistão                               | KZ                       | KAZ                      | kk-KZ / en-US                         |
| Quénia                                    | KE                       | KEN                      | sw-KE / en-US                         |
| Quiribáti                                 | KI                       | KIR                      | en-PT                                 |
| Coreia                                    | KR                       | KOR                      | ko-KR / en-US                         |
| Kosovo                                   | XK                       | XKS                      | en-PT                                 |
| Koweit                                   | KW                       | KWT                      | ar-KW / en-US                         |
| Quirguistão                               | KG                       | KGZ                      | ky-KG / en-US                         |
| Laos                                     | LA                       | RIO LAO                      | lo-LA / en-US                         |
| Letónia                                   | LV                       | Rio LVA                      | lv-LV / en-US                         |
| Líbano                                  | LB                       | LBN                      | ar-LB / en-US                         |
| Lesoto                                  | LS                       | Rio LSO                      | en-PT                                 |
| Libéria                                  | LR                       | LBR                      | en-PT                                 |
| Líbia                                    | LY                       | LBY                      | ar-LY / en-US                         |
| Listenstaine                            | LI                       | MENTIR                      | de-LI / en-US                         |
| Lituânia                                | LT                       | LTU                      | LT / en-US                         |
| Luxemburgo                               | LU                       | LUX                      | de-LU / fr-LU / en-US                 |
| RAE de Macau                                | MO                       | MAC                      | zh-MO / en-US                         |
| Macedónia                          | MK                       | MKD                      | mk-MK / en-US                         |
| Madagáscar                               | MG                       | ODM                      | fr-FR / en-US                         |
| Maláui                                   | MW                       | MWI                      | en-PT                                 |
| Malásia                                 | MY                       | A MINHA                      | en-MY / en-US                         |
| Maldivas                                 | MV                       | MDV                      | dv-MV / en-US                         |
| Mali                                     | ML                       | MLI                      | fr-FR / en-US                         |
| Malta                                    | MT                       | MLT                      | mt-MT / en-US                         |
| Ilhas Marshall                         | MH                       | MHL                      | en-PT                                 |
| Martinica                               | MQ                       | MTQ                      | fr-FR / en-US                         |
| Mauritânia                               | MR                       | MRT                      | ar-SA / en-US                         |
| Maurícias                                | MU                       | MUS                      | en-GB / en-US                         |
| Maiote                                  | YT                       | MYT                      | fr-FR / en-US                         |
| México                                   | MX                       | MEX                      | es-MX / en-US                         |
| Micronésia                               | FM                       | FSM                      | en-PT                                 |
| Moldávia                                  | MD                       | MDA                      | ro-RO / en-US                         |
| Mónaco                                   | MC                       | MCO                      | fr-MC / en-US                         |
| Mongólia                                 | MN                       | MNG                      | mn-MN / en-US                         |
| Montenegro                               | ME                       | MNE                      | sr-Latn-ME / en-US                    |
| Montserrate                               | MS                       | MSR                      | en-PT                                 |
| Marrocos                                  | MA                       | MAR                      | ar-MA / en-US                         |
| Moçambique                               | MZ                       | MOZ                      | pt-PT                                 |
| Mianmar                                  | MM                       | MMR                      | en-PT                                 |
| Namíbia                                  | ND                       | NAM                      | en-GB / en-US                         |
| Nauru                                    | NR                       | NRU                      | en-PT                                 |
| Nepal                                    | NP                       | NPL                      | ne-NP / en-US                         |
| Antigas Antilhas Neerlandesas                     | UM                       | FORMIGA                      | en-PT                                 |
| Holanda                         | NL                       | NLD                      | nl-NL / en-US                         |
| Nova Caledónia                            | NC                       | NCL                      | fr-FR / en-US                         |
| Nova Zelândia                              | NZ                       | NZL                      | en-NZ / en-US                         |
| Nicarágua                                | NI                       | NIC                      | es-NI / en-US                         |
| Níger                                    | NE                       | NER                      | fr-FR / en-US                         |
| Nigéria                                  | NG                       | NGA                      | ha-Latn-NG / en-US                    |
| Niuê                                     | NU                       | NIU                      | en-PT                                 |
| Ilha Norfolk                           | NF                       | NFK                      | en-PT                                 |
| Ilhas Marianas do Norte                 | BM                       | MNP                      | en-PT                                 |
| Noruega                                   | NO                       | NOR                      | nb-NO / en-US                         |
| Omã                                     | OM                       | OMN                      | ar-OM / en-US                         |
| Paquistão                                 | PK                       | PAK                      | seu PK / en-US                         |
| Palau                                    | PW                       | PLW                      | en-PT                                 |
| Autoridade Palestiniana                    | PS                       | PSE                      | ar-SA / en-US                         |
| Panamá                                   | PA                       | PAN                      | es-PA / en-US                         |
| Papua-Nova Guiné                         | PG                       | PNG                      | en-PT                                 |
| Paraguai                                 | PY                       | PRY                      | es-PY / en-US                         |
| Peru                                     | PE                       | PER                      | es-PE / en-US                         |
| Filipinas                              | PH                       | PHL                      | en-PH / en-US                         |
| Ilhas Pitcairn                         | PN                       | PCN                      | en-PT                                 |
| Polónia                                   | PL                       | POL                      | pl-PL / en-US                         |
| Portugal                                 | PT                       | PRT                      | pt-PT / en-US                         |
| Porto Rico                              | PR                       | RIO                      | es-PR / en-US                         |
| Catar                                    | QA                       | QAT                      | ar-QA / en-US                         |
| Reunião                                  | RE                       | REU                      | fr-FR / en-US                         |
| Roménia                                  | RO                       | RIO ROU                      | ro-RO / en-US                         |
| Rússia                                   | RU                       | RUS                      | ru-RU / en-US                         |
| Ruanda                                   | RW                       | RWA                      | rw-RW / en-US                         |
| Saba                                     | XS                       | XSA                      | nl-NL / en-US                         |
| São Cristóvão e Neves                    | KN                       | KNA                      | en-GB / en-US                         |
| Santa Lúcia                              | LC                       | LCA                      | en-PT                                 |
| São Martinho (Saint Martin)                             | MF                       | MAF                      | fr-FR / en-US                         |
| São Pedro e Miquelão                | PM                       | SPM                      | fr-FR / en-US                         |
| São Vicente e Granadinas         | VC                       | VCT                      | en-PT                                 |
| Saint-Barthélemy                         | BL                       | BLM                      | fr-FR / en-US                         |
| Samoa                                    | WS                       | WSM                      | en-PT                                 |
| São Marino                               | SM                       | SMR                      | it-IT / en-US                         |
| São Tomé e Príncipe                    | ST                       | STP                      | pt-PT / en-US                         |
| Arábia Saudita                             | SA                       | SAU                      | ar-SA / en-US                         |
| Senegal                                  | SN                       | SEN                      | wo-SN / en-US                         |
| Sérvia                                   | RS                       | SRB                      | sr-Latn-RS / sr-Cyrl-RS / en-US       |
| Seicheles                               | SC                       | SYC                      | en-PT                                 |
| Serra Leoa                             | SL                       | SLE                      | en-PT                                 |
| Singapura                                | SG                       | SGP                      | en-SG / zh-SG / en-US                 |
| Santo Eustáquio                           | XE                       | XSE                      | nl-NL / en-US                         |
| São Martinho (Sint Maarten)                             | SX                       | SXM                      | en-PT                                 |
| Eslováquia                                 | SK                       | SVK                      | sk-SK / en-US                         |
| Eslovénia                                 | SI                       | SVN                      | sl-SI / en-US                         |
| Ilhas Salomão                          | SB                       | SLB                      | en-PT                                 |
| Somália                                  | SO                       | SOM                      | ar-SA / en-US                         |
| África do Sul                             | ZA                       | ZAF                      | en-ZA / en-US                         |
| Ilhas Geórgia do Sul e Sandwich do Sul | GS                       | SGS                      | en-PT                                 |
| Sudão do Sul                              | SS                       | SSD                      | en-PT                                 |
| Espanha                                    | ES                       | ESP                      | es-ES / ca-ES / eu-ES / gl-ES / en-US |
| Sri Lanca                                | LK                       | LKA                      | si-LK / en-US                         |
| Santa Helena, Ascensão, Tristão da Cunha   | SH                       | SHN                      | en-PT                                 |
| Suriname                                 | SR                       | SUR                      | nl-NL                                 |
| Svalbard                                 | SJ                       | SJM                      | nb-NO / en-US                         |
| Suécia                                   | SE                       | SWE                      | sv-SE / en-US                         |
| Suíça                              | CH                       | CHE                      | de-CH / fr-CH / it-CH / en-US         |
| Taiwan                                   | TW                       | TWN                      | zh-TW / en-US                         |
| Tajiquistão                               | TJ                       | TJK                      | tg-Cyrl-TJ / en-US                    |
| Tanzânia                                 | TZ                       | TZA                      | en-GB / en-US                         |
| Tailândia                                 | TH                       | THA                      | th-TH / en-US                         |
| Timor-Leste                              | TL                       | TLS                      | pt-PT / en-US                         |
| Togo                                     | TG                       | TGO                      | fr-FR / en-US                         |
| Toquelau                                  | TK                       | TKL                      | en-PT                                 |
| Tonga                                    | TO                       | TONELADA                      | en-PT                                 |
| Trindade e Tobago                      | TT                       | TTO                      | en-TT / en-US                         |
| Tunísia                                  | TN                       | TUN                      | ar-TN / en-US                         |
| Turquia                                   | TR                       | TUR                      | tr-TR / en-US                         |
| Turquemenistão                             | TM                       | TKM                      | tk-TM / en-US                         |
| Ilhas Turcas e Caicos                 | TC                       | TCA                      | en-PT                                 |
| Tuvalu                                   | TV                       | TUV                      | en-PT                                 |
| Uganda                                   | UG                       | UGA                      | en-GB / en-US                         |
| Ucrânia                                  | UA                       | UKR                      | uk-UA / en-US                         |
| Emirados Árabes Unidos                     | AE                       | SÃO                      | ar-AE / en-US                         |
| Reino Unido                           | GB                       | GBR                      | en-GB / en-US                         |
| Ilhas Desondo dos EUA                    | UM                       | UMI                      | en-PT                                 |
| Ilhas Virgens Americanas                      | VI                       | VIR                      | en-PT                                 |
| Estados Unidos da América                            | EUA                       | E.U.A.                      | en-EUA / es-EUA                         |
| Uruguai                                  | UY                       | URY                      | es-UY / en-US                         |
| Usbequistão                               | UZ                       | UZB                      | Uz-Latn-UZ / en-US                    |
| Vanuatu                                  | VU                       | Rio VUT                      | en-PT                                 |
| Cidade do Vaticano                             | VA                       | IVA                      | it-IT / en-US                         |
| Venezuela                                | VE                       | VEN                      | es-VE / en-US                         |
| Vietname                                  | VN                       | VNM                      | vi-VN / en-US                         |
| Wallis e Futuna                        | WF                       | WLF                      | fr-FR / en-US                         |
| Iémen                                    | YE                       | YEM                      | ar-YE / en-US                         |
| Zâmbia                                   | ZM                       | ZMB                      | en-GB / en-US                         |
| Zimbabué                                 | ZW                       | ZWE                      | en-ZW / en-US                         |

