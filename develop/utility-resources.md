---
title: Recursos de utilitário
description: A API do Partner Center REST contém muitos recursos que descrevem modelos de dados de finalidade geral utilizados em todo o SDK.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 115b0508f956c4b60e4db53193ef2585fa0c9a34
ms.sourcegitcommit: 204e518e794b6b076a17488ee9ca1aaaa4beaaec
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2021
ms.locfileid: "106103985"
---
# <a name="utility-resources"></a>Recursos de utilitário

**Aplica-se a**

- Partner Center
- Centro de Parceiros operado pela 21Vianet
- Centro de Parceiros para Microsoft Cloud Germany
- Centro de Parceiros do Microsoft Cloud for US Government

A API do Partner Center REST contém muitos recursos que descrevem modelos de dados de finalidade geral utilizados em todo o SDK.

## <a name="address"></a>Endereço

Endereço para utilizar para os perfis do cliente ou parceiro. Para obter mais informações sobre os formatos e propriedades suportados em diferentes países/regiões, consulte [obter regras de formatação de endereços por mercado.](get-market-specific-validation-data.md)

| Propriedade     | Tipo   | Comprimento (min, máx) | Description                                                                                      |
|--------------|--------|-------------------|--------------------------------------------------------------------------------------------------|
| Linha de Endereço1 | string | (1, 200)          | A primeira linha do endereço.                                                                   |
| Linha de Endereço2 | string | (0, 200)          | A segunda linha do endereço. Esta propriedade é opcional.                                       |
| City         | string | n/a               | A cidade.                                                                                        |
| Estado        | string | (0, 2)            | O Estado.                                                                                       |
| PostalCode   | string | n/a               | O código POSTAL ou código postal.                                                                     |
| País      | string | (2, 2)            | O país/região no formato de código de país ISO.                                                   |
| Region       | string | n/a               | A região.                                                                                      |
| FirstName    | string | (1, 50)           | O primeiro nome de um contacto na empresa/organização do cliente.                              |
| Nome do Meio   | string | (1, 50)           | O nome do meio de um contacto na empresa/organização do cliente. Esta propriedade é opcional.  |
| LastName     | string | (1, 50)           | O último nome de um contacto na empresa/organização do cliente.                               |
| PhoneNumber  | string | n/a               | O número de telefone de um contacto na empresa/organização do cliente. Esta propriedade é opcional.|
|PhoneNumber|string|n/a|O número de telefone de um contacto na empresa/organização do cliente. No perfil do cliente, esta propriedade é obrigatória para a empresa/organização do cliente localizada nos seguintes países: Arménia(AM), Azerbaijão(AZ), Bielorrússia (BY), Hungria(HU), Cazaquistão (KZ), Quirguistão(KG), Moldávia (MD), Rússia(RU), Tajiquistão(TJ), Uzbequistão(UZ), Ucrânia(UA)), Índia, Índia Brasil, África do Sul, Polónia, Emirados Árabes Unidos, Arábia Saudita, Turquia, Tailândia, Vietname, Myanmar, Iraque, Sudão do Sul e Venezuela. Caso contrário, isto é opcional.|


## <a name="contact"></a>Contacto

Descreve informações de contacto para um indivíduo específico.

| Propriedade    | Tipo   | Description                  |
|-------------|--------|------------------------------|
| FirstName   | string | O primeiro nome do contacto.    |
| LastName    | string | O sobrenome do contacto.     |
| E-mail       | string | O endereço de e-mail do contacto. |
| PhoneNumber | string | O número de telefone do contacto.  |

## <a name="fieldfilter"></a>Filtro de Campo

Descreve um filtro que pode ser aplicado aos resultados da pesquisa.

| Propriedade | Tipo   | Description                                                                                                                                                                                        |
|----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operador | string | O operador do filtro: "igual", "não \_ é igual", "maior \_ do que", "maior \_ do que ou \_ \_ igual", "menos \_ que", "menos \_ ou \_ \_ igual", "substring", "e", "ou", "começa \_ com", "não \_ começa \_ com". |

## <a name="fileinfo"></a>FileInfo

Representa um ficheiro externo enviado para o Partner Center.

| Propriedade                 | Tipo   | Description                                   |
|--------------------------|--------|-----------------------------------------------|
| Comentário                  | string | Um comentário associado ao upload de ficheiros.    |
| Arquidestésia            | string | A extensão do ficheiro.                           |
| FileNameWithoutExtension | string | O nome do ficheiro, extensão não incluída. |
| Tamanho de arquivo                 | long   | O tamanho do ficheiro.                         |
| Id                       | string | A identificação única para o upload de ficheiros.            |

## <a name="link"></a>Ligação

Contém uma ligação URI e informações associadas.

| Propriedade | Tipo                   | Description                        |
|----------|------------------------|------------------------------------|
| URI      | string                 | O URI.                           |
| Método   | string                 | O método representado pelo URI. |
| Cabeçalhos  | Matriz de KeyValuePairs | Os cabeçalhos para a ligação.          |

## <a name="passwordprofile"></a>PasswordProfile

Descreve uma palavra-passe específica e se essa palavra-passe tiver de ser alterada.

>[!NOTE]
>Sem apoio no Partner Center operado pela 21Vianet.

| Propriedade            | Tipo                          | Description                                                            |
|---------------------|-------------------------------|------------------------------------------------------------------------|
| Palavra-passe            | [SecureString](#securestring) | A senha.                                                          |
| ForceChangePassword | boolean                       | Determina se a palavra-passe precisa de ser alterada à força no próximo login. |

## <a name="resourcelinks"></a>RecursosLinks

Contém uma lista de links para um recurso.

| Propriedade   | Tipo                                      | Description                                        |
|------------|-------------------------------------------|----------------------------------------------------|
| Autónomo       | [Ligação](#link)                             | O auto-URI.                                      |
| Seguinte       | [Ligação](#link)                             | A próxima página de artigos.                            |
| Anterior   | [Ligação](#link)                             | A página anterior dos artigos.                        |
| Atributos | [RecursosTributos](#resourceattributes) | Os metadados atribuem correspondentes ao utilizador. |

## <a name="resourceattributes"></a>RecursosTributos

Contém metadados de atributos para um recurso.

| Propriedade   | Tipo   | Description                                 |
|------------|--------|---------------------------------------------|
| Etag       | string | O etag, também conhecido como a versão do objeto. |
| ObjectType | string | O tipo de objeto do recurso base.    |

## <a name="securestring"></a>SecureString

As lojas garantiram informações, como uma palavra-passe.

| Propriedade | Tipo | Description                       |
|----------|------|-----------------------------------|
| Comprimento   | int  | O comprimento da corda presa. |

## <a name="validationcode"></a>ValidaçãoDesco

Representa o código de validação da Nuvem Comunitária do Governo de um parceiro.

| Propriedade         | Tipo         | Description                                                              |
|------------------|--------------|--------------------------------------------------------------------------|
| PartnerId        | GUID         | Identificador de parceiros                                                       |
| OrganizationName | string       | O nome da organização fornecido durante o processo de validação             |
| ValidaçãoId     | int          | Um identificador único para validação                                       |
| MaxCreates       | int int anulado | Os clientes máximos autorizados a serem criados com este código de validação    |
| Restantes Acreates | int int anulado | O cliente restante cria ao abrigo deste ID de validação                      |
| ETag             | string       | A versão específica deste recurso. Alterações quando o recurso é alterado. |
