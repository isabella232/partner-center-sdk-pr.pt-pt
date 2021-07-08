---
title: Obter confirmação da aceitação do cliente do Contrato de Cliente Microsoft
description: Este artigo explica como obter a confirmação da aceitação pelo cliente do Acordo de Cliente da Microsoft.
ms.date: 09/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 3668a5e510effb533cade311f52513b9a81d40af
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760543"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-customer-agreement"></a><span data-ttu-id="5524e-103">Obter confirmação da aceitação do cliente do Contrato de Cliente Microsoft</span><span class="sxs-lookup"><span data-stu-id="5524e-103">Get confirmation of customer acceptance of Microsoft Customer Agreement</span></span>

<span data-ttu-id="5524e-104">**Aplica-se a**: Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="5524e-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="5524e-105">**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5524e-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5524e-106">O recurso **Do Acordo** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5524e-106">The **Agreement** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="5524e-107">Este artigo explica como pode obter confirmação da aceitação de um cliente do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="5524e-107">This article explains how you can retrieve confirmation(s) of a customer's acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5524e-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5524e-108">Prerequisites</span></span>

- <span data-ttu-id="5524e-109">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="5524e-109">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="5524e-110">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5524e-110">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="5524e-111">Este cenário suporta apenas a autenticação App+User.</span><span class="sxs-lookup"><span data-stu-id="5524e-111">This scenario only supports App+User authentication.</span></span>

- <span data-ttu-id="5524e-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5524e-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5524e-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="5524e-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5524e-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="5524e-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5524e-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="5524e-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5524e-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="5524e-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5524e-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5524e-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="net"></a><span data-ttu-id="5524e-118">.NET</span><span class="sxs-lookup"><span data-stu-id="5524e-118">.NET</span></span>

<span data-ttu-id="5524e-119">Para obter confirmação(s) de aceitação do cliente que foi previamente fornecida:</span><span class="sxs-lookup"><span data-stu-id="5524e-119">To retrieve confirmation(s) of customer acceptance that was previously provided:</span></span>

- <span data-ttu-id="5524e-120">Utilize a recolha **IAggregatePartner.Customers** e ligue para o método **ById** com o identificador de clientes especificado.</span><span class="sxs-lookup"><span data-stu-id="5524e-120">Use the **IAggregatePartner.Customers** collection and call **ById** method with the specified customer identifier.</span></span>

- <span data-ttu-id="5524e-121">Pegue na propriedade **Dos Contratos** e filtre os resultados para o Microsoft Customer Agreement, chamando o método **ByAgreementType.**</span><span class="sxs-lookup"><span data-stu-id="5524e-121">Fetch the **Agreements** property and filter the results to Microsoft Customer Agreement by calling **ByAgreementType** method.</span></span>

- <span data-ttu-id="5524e-122">Ligue para o método **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="5524e-122">Call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCustomerAgreement";

var customerAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

<span data-ttu-id="5524e-123">Uma amostra completa pode ser encontrada na classe [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="5524e-123">A complete sample can be found in the [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="5524e-124">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5524e-124">REST request</span></span>

<span data-ttu-id="5524e-125">Para obter a confirmação da aceitação do cliente que foi previamente fornecida:</span><span class="sxs-lookup"><span data-stu-id="5524e-125">To retrieve confirmation of customer acceptance that was previously provided:</span></span>

1. <span data-ttu-id="5524e-126">Crie um pedido DE REST para recuperar a coleção [Contratos](./agreement-resources.md) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="5524e-126">Create a REST request to retrieve the [Agreements](./agreement-resources.md) collection for the customer.</span></span>

2. <span data-ttu-id="5524e-127">Utilize o parâmetro de consulta de **acordoso** para estender os resultados apenas ao Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="5524e-127">Use the **agreementType** query parameter to scope the results to only the Microsoft Customer Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5524e-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5524e-128">Request syntax</span></span>

<span data-ttu-id="5524e-129">Utilize a seguinte sintaxe de pedido:</span><span class="sxs-lookup"><span data-stu-id="5524e-129">Use the following request syntax:</span></span>

| <span data-ttu-id="5524e-130">Método</span><span class="sxs-lookup"><span data-stu-id="5524e-130">Method</span></span> | <span data-ttu-id="5524e-131">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5524e-131">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5524e-132">GET</span><span class="sxs-lookup"><span data-stu-id="5524e-132">GET</span></span>    | <span data-ttu-id="5524e-133">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/agreements?agreementType={agreement-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5524e-133">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements?agreementType={agreement-type} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="5524e-134">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="5524e-134">URI parameters</span></span>

<span data-ttu-id="5524e-135">Pode utilizar os seguintes parâmetros URI com o seu pedido:</span><span class="sxs-lookup"><span data-stu-id="5524e-135">You can use the following URI parameters with your request:</span></span>

| <span data-ttu-id="5524e-136">Nome</span><span class="sxs-lookup"><span data-stu-id="5524e-136">Name</span></span>             | <span data-ttu-id="5524e-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="5524e-137">Type</span></span> | <span data-ttu-id="5524e-138">Necessário</span><span class="sxs-lookup"><span data-stu-id="5524e-138">Required</span></span> | <span data-ttu-id="5524e-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="5524e-139">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="5524e-140">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="5524e-140">customer-tenant-id</span></span> | <span data-ttu-id="5524e-141">GUID</span><span class="sxs-lookup"><span data-stu-id="5524e-141">GUID</span></span> | <span data-ttu-id="5524e-142">Yes</span><span class="sxs-lookup"><span data-stu-id="5524e-142">Yes</span></span> | <span data-ttu-id="5524e-143">O valor é um **CustomerTenantId** formatado guid que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="5524e-143">The value is a GUID formatted **CustomerTenantId** that allows you to specify a customer.</span></span> |
| <span data-ttu-id="5524e-144">tipo de acordo</span><span class="sxs-lookup"><span data-stu-id="5524e-144">agreement-type</span></span> | <span data-ttu-id="5524e-145">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="5524e-145">string</span></span> | <span data-ttu-id="5524e-146">No</span><span class="sxs-lookup"><span data-stu-id="5524e-146">No</span></span> | <span data-ttu-id="5524e-147">Este parâmetro devolve todos os metadados do acordo.</span><span class="sxs-lookup"><span data-stu-id="5524e-147">This parameter returns all agreement metadata.</span></span> <span data-ttu-id="5524e-148">Utilize este parâmetro para estender a resposta de consulta ao tipo de acordo específico.</span><span class="sxs-lookup"><span data-stu-id="5524e-148">Use this parameter to scope the query response to specific agreement type.</span></span> <span data-ttu-id="5524e-149">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="5524e-149">The supported values are:</span></span> <br/><br/> <span data-ttu-id="5524e-150">**MicrosoftCloudAgreement** que apenas inclui metadados de acordo do tipo *MicrosoftCloudAgreement*.</span><span class="sxs-lookup"><span data-stu-id="5524e-150">**MicrosoftCloudAgreement** that only includes agreement metadata of the type *MicrosoftCloudAgreement*.</span></span><br/><br/> <span data-ttu-id="5524e-151">**MicrosoftCustomerAgreement** que só inclui metadados de acordo do tipo *MicrosoftCustomerAgreement*.</span><span class="sxs-lookup"><span data-stu-id="5524e-151">**MicrosoftCustomerAgreement** that only includes agreement metadata of the type *MicrosoftCustomerAgreement*.</span></span><br/><br/> <span data-ttu-id="5524e-152">**\**_ que devolve todos os metadados do acordo. (Não use _\* \* \*_ a menos que o seu código tenha a lógica necessária para lidar com tipos de acordo inesperados.) <br/> <br/> _\* Nota:*\* Se o parâmetro URI não for especificado, a consulta predefine o **MicrosoftCloudAgreement** para retrocompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="5524e-152">**\**_ that returns all agreement metadata. (Don't use _*\**_ unless your code has the necessary logic to handle unexpected agreement types.)<br/><br/> _\* Note:*\* If the URI parameter isn't specified, the query defaults to **MicrosoftCloudAgreement** for backward compatibility.</span></span> <span data-ttu-id="5524e-153">A Microsoft pode introduzir metadados de acordo com novos tipos de acordo a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="5524e-153">Microsoft may introduce agreement metadata with new agreement types at any time.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="5524e-154">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="5524e-154">Request headers</span></span>

<span data-ttu-id="5524e-155">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5524e-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5524e-156">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5524e-156">Request body</span></span>

<span data-ttu-id="5524e-157">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5524e-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5524e-158">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5524e-158">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="5524e-159">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5524e-159">REST response</span></span>

<span data-ttu-id="5524e-160">Se for bem sucedido, este método devolve uma recolha de recursos do **Acordo** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="5524e-160">If successful, this method returns a collection of **Agreement** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5524e-161">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5524e-161">Response success and error codes</span></span>

<span data-ttu-id="5524e-162">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5524e-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="5524e-163">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5524e-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5524e-164">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="5524e-164">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5524e-165">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5524e-165">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 620
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "totalCount": 2,
    "items":
    [
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@example.com"
                "phoneNumber":"1234567890"
            },
            "templateId":"117a77b0-9360-443b-8795-c6dedc750cf9",
            "dateAgreed":"2019-08-26T00:00:00",
            "type":"MicrosoftCustomerAgreement",
            "agreementLink":"https://aka.ms/customeragreement"
        },
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@example.com"
                "phoneNumber:"1234567890"
            },
            "templateId":"117a77b0-9360-443b-8795-c6dedc750cf9",
            "dateAgreed":"2019-08-27T00:00:00",
            "type":"MicrosoftCustomerAgreement",
            "agreementLink":"https://aka.ms/customeragreement"
        }
    ]
}
```
