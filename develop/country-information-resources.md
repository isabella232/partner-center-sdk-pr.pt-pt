---
title: Recursos de informação do país
description: Saiba como utilizar apis do Partner Center com recursos de informação do País e metadados descritivos relacionados com um país ou região específico.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: caf56282d21df35ae9e179a98a37317f864117a3
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973830"
---
# <a name="country-information-resources-available-from-partner-center-apis"></a>Recursos de informação do país disponíveis nas APIs do Partner Center

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Os seguintes recursos são metadados descritivos para um país/região.

## <a name="countryinformation"></a>Informação do País

| Propriedade                      | Tipo               | Description                                                                                        |
|-------------------------------|--------------------|----------------------------------------------------------------------------------------------------|
| ExtensãoData                 | string             | Os dados da extensão.                                                                                |
| Iso2Code                      | string             | Um código ISO-2.                                                                                     |
| Iso3Code                      | string             | Um código ISO-3.                                                                                     |
| PadrãoCultura                | string             | A cultura padrão.                                                                               |
| IsStateRequired               | boolean            | Indica se um estado/província é necessário ou não.                                             |
| Lista de Estados Suportados           | matriz de cadeias (de carateres)   | Se for necessário um estado/província, devolva a lista completa para esse país/região.                    |
| Lista de Apoios        | matriz de cadeias (de carateres)   | Uma lista de línguas apoiadas.                                                                     |
| Lista de Culturas Apoiadas         | matriz de cadeias (de carateres)   | Uma lista de culturas apoiadas.                                                                      |
| IsPostalCodeRequired          | boolean            | Indica se é necessário ou não um código POSTAL ou um código postal.                                    |
| PostalCodeRegex               | string             | A expressão regular que define o código POSTAL/postal.                                          |
| IsCityRequired                | boolean            | Indica se uma cidade é necessária ou não.                                                       |
| IsVatIdSupportou              | boolean            | Indica se é necessário ou não um ID de IVA.                                                     |
| TaxIdFormat                   | string             | O formato de identificação fiscal.                                                                                 |
| TaxIdSample                   | string             | A amostra de identificação de impostos.                                                                                 |
| VatIdRegex                    | string             | A expressão regular da identificação fiscal.                                                                     |
| TelefoneNumberRegex              | string             | O número de telefone expressão regular.                                                               |
| IsRegistrationNumbersupportou | boolean            | Indica se um número de registo é suportado ou não.                                       |
| IsTaxIdSupportou              | boolean            | Indica se uma identificação fiscal é apoiada ou não. Isto é diferente do IsVatIdSupported. |
| ResellerAgreementRegion       | string             | A região do acordo de revenda.                                                                     |
| Região Geográfica              | string             | A região geográfica.                                                                             |
| CountryCallingCodesList       | matriz de cadeias (de carateres)   | Os códigos de chamada suportados no país/região.                                                 |
| Atributos                    | RecursosTributos | Os metadados atribuem correspondentes ao recurso CountryInformation.                          |

## <a name="countryvalidationrules"></a>Regras de CountryValidationRules

Descreve as regras de formatação de endereços para um país/região.

| Propriedade                | Tipo               | Description                                                                                        |
|-------------------------|--------------------|----------------------------------------------------------------------------------------------------|
| Iso2Code                | string             | Um código ISO-2.                                                                                     |
| PadrãoCultura          | string             | A cultura padrão.                                                                               |
| IsStateRequired         | boolean            | Indica se um estado/província é necessário ou não.                                             |
| Lista de Estados Suportados     | matriz de cadeias (de carateres)   | Se for necessário um estado/província, devolva a lista completa para esse país/região.                    |
| Lista de Apoios  | matriz de cadeias (de carateres)   | Uma lista de línguas apoiadas.                                                                     |
| Lista de Culturas Apoiadas   | matriz de cadeias (de carateres)   | Uma lista de culturas apoiadas.                                                                      |
| IsPostalCodeRequired    | boolean            | Indica se é necessário ou não um código POSTAL ou um código postal.                                    |
| PostalCodeRegex         | string             | A expressão regular que define o código POSTAL/postal.                                          |
| IsCityRequired          | boolean            | Indica se uma cidade é necessária ou não.                                                       |
| IsVatIdSupportou        | boolean            | Indica se é necessário ou não um ID de IVA.                                                     |
| TaxIdFormat             | string             | O formato de identificação fiscal.                                                                                 |
| TaxIdSample             | string             | A amostra de identificação de impostos.                                                                                 |
| VatIdRegex              | string             | A expressão regular da identificação fiscal.                                                                     |
| TelefoneNumberRegex        | string             | O número de telefone expressão regular.                                                               |
| IsTaxIdSupportou        | boolean            | Indica se uma identificação fiscal é apoiada ou não. Esta propriedade é diferente da IsVatIdSupported. |
| IsTaxIdOptional         | boolean            | Indica se uma identificação fiscal é opcional ou não.                                                     |
| CountryCallingCodesList | matriz de cadeias (de carateres)   | Os códigos de chamada suportados no país/região.                                                 |
| Atributos              | RecursosTributos | Os metadados atribuem correspondentes ao recurso CountryInformation.                          |
