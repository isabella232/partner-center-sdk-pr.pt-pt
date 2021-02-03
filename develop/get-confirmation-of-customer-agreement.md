---
title: Obter confirmação da aceitação do cliente do Contrato de Cliente Microsoft
description: Este artigo explica como obter a confirmação da aceitação pelo cliente do Acordo de Cliente da Microsoft.
ms.date: 09/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 55f63311e7bb1857fdc6c4b3d68446674542ba98
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769439"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-customer-agreement"></a><span data-ttu-id="38ee7-103">Obter confirmação da aceitação do cliente do Contrato de Cliente Microsoft</span><span class="sxs-lookup"><span data-stu-id="38ee7-103">Get confirmation of customer acceptance of Microsoft Customer Agreement</span></span>

<span data-ttu-id="38ee7-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="38ee7-104">**Applies to:**</span></span>

- <span data-ttu-id="38ee7-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="38ee7-105">Partner Center</span></span>

<span data-ttu-id="38ee7-106">O recurso **Do Acordo** é atualmente suportado pelo Partner Center apenas na nuvem pública da *Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="38ee7-106">The **Agreement** resource is currently supported by Partner Center only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="38ee7-107">Este recurso não se aplica a:</span><span class="sxs-lookup"><span data-stu-id="38ee7-107">This resource doesn't apply to:</span></span>

- <span data-ttu-id="38ee7-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="38ee7-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="38ee7-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="38ee7-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="38ee7-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="38ee7-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="38ee7-111">Este artigo explica como pode obter confirmação da aceitação de um cliente do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="38ee7-111">This article explains how you can retrieve confirmation(s) of a customer's acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="38ee7-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="38ee7-112">Prerequisites</span></span>

- <span data-ttu-id="38ee7-113">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="38ee7-113">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="38ee7-114">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="38ee7-114">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="38ee7-115">Este cenário suporta apenas a autenticação App+User.</span><span class="sxs-lookup"><span data-stu-id="38ee7-115">This scenario only supports App+User authentication.</span></span>

- <span data-ttu-id="38ee7-116">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="38ee7-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="38ee7-117">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="38ee7-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="38ee7-118">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="38ee7-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="38ee7-119">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="38ee7-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="38ee7-120">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="38ee7-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="38ee7-121">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="38ee7-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="net"></a><span data-ttu-id="38ee7-122">.NET</span><span class="sxs-lookup"><span data-stu-id="38ee7-122">.NET</span></span>

<span data-ttu-id="38ee7-123">Para obter confirmação(s) de aceitação do cliente que foi previamente fornecida:</span><span class="sxs-lookup"><span data-stu-id="38ee7-123">To retrieve confirmation(s) of customer acceptance that was previously provided:</span></span>

- <span data-ttu-id="38ee7-124">Utilize a recolha **IAggregatePartner.Customers** e ligue para o método **ById** com o identificador de clientes especificado.</span><span class="sxs-lookup"><span data-stu-id="38ee7-124">Use the **IAggregatePartner.Customers** collection and call **ById** method with the specified customer identifier.</span></span>

- <span data-ttu-id="38ee7-125">Pegue na propriedade **Dos Contratos** e filtre os resultados para o Microsoft Customer Agreement, chamando o método **ByAgreementType.**</span><span class="sxs-lookup"><span data-stu-id="38ee7-125">Fetch the **Agreements** property and filter the results to Microsoft Customer Agreement by calling **ByAgreementType** method.</span></span>

- <span data-ttu-id="38ee7-126">Ligue para o método **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="38ee7-126">Call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCustomerAgreement";

var customerAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

<span data-ttu-id="38ee7-127">Uma amostra completa pode ser encontrada na classe [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="38ee7-127">A complete sample can be found in the [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="38ee7-128">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="38ee7-128">REST request</span></span>

<span data-ttu-id="38ee7-129">Para obter a confirmação da aceitação do cliente que foi previamente fornecida:</span><span class="sxs-lookup"><span data-stu-id="38ee7-129">To retrieve confirmation of customer acceptance that was previously provided:</span></span>

1. <span data-ttu-id="38ee7-130">Crie um pedido DE REST para recuperar a coleção [Contratos](./agreement-resources.md) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="38ee7-130">Create a REST request to retrieve the [Agreements](./agreement-resources.md) collection for the customer.</span></span>

2. <span data-ttu-id="38ee7-131">Utilize o parâmetro de consulta de **acordoso** para estender os resultados apenas ao Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="38ee7-131">Use the **agreementType** query parameter to scope the results to only the Microsoft Customer Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="38ee7-132">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="38ee7-132">Request syntax</span></span>

<span data-ttu-id="38ee7-133">Utilize a seguinte sintaxe de pedido:</span><span class="sxs-lookup"><span data-stu-id="38ee7-133">Use the following request syntax:</span></span>

| <span data-ttu-id="38ee7-134">Método</span><span class="sxs-lookup"><span data-stu-id="38ee7-134">Method</span></span> | <span data-ttu-id="38ee7-135">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="38ee7-135">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="38ee7-136">GET</span><span class="sxs-lookup"><span data-stu-id="38ee7-136">GET</span></span>    | <span data-ttu-id="38ee7-137">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/agreements?agreementType={agreement-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="38ee7-137">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements?agreementType={agreement-type} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="38ee7-138">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="38ee7-138">URI parameters</span></span>

<span data-ttu-id="38ee7-139">Pode utilizar os seguintes parâmetros URI com o seu pedido:</span><span class="sxs-lookup"><span data-stu-id="38ee7-139">You can use the following URI parameters with your request:</span></span>

| <span data-ttu-id="38ee7-140">Nome</span><span class="sxs-lookup"><span data-stu-id="38ee7-140">Name</span></span>             | <span data-ttu-id="38ee7-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="38ee7-141">Type</span></span> | <span data-ttu-id="38ee7-142">Necessário</span><span class="sxs-lookup"><span data-stu-id="38ee7-142">Required</span></span> | <span data-ttu-id="38ee7-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="38ee7-143">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="38ee7-144">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="38ee7-144">customer-tenant-id</span></span> | <span data-ttu-id="38ee7-145">GUID</span><span class="sxs-lookup"><span data-stu-id="38ee7-145">GUID</span></span> | <span data-ttu-id="38ee7-146">Sim</span><span class="sxs-lookup"><span data-stu-id="38ee7-146">Yes</span></span> | <span data-ttu-id="38ee7-147">O valor é um **CustomerTenantId** formatado guid que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="38ee7-147">The value is a GUID formatted **CustomerTenantId** that allows you to specify a customer.</span></span> |
| <span data-ttu-id="38ee7-148">tipo de acordo</span><span class="sxs-lookup"><span data-stu-id="38ee7-148">agreement-type</span></span> | <span data-ttu-id="38ee7-149">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="38ee7-149">string</span></span> | <span data-ttu-id="38ee7-150">No</span><span class="sxs-lookup"><span data-stu-id="38ee7-150">No</span></span> | <span data-ttu-id="38ee7-151">Este parâmetro devolve todos os metadados do acordo.</span><span class="sxs-lookup"><span data-stu-id="38ee7-151">This parameter returns all agreement metadata.</span></span> <span data-ttu-id="38ee7-152">Utilize este parâmetro para estender a resposta de consulta ao tipo de acordo específico.</span><span class="sxs-lookup"><span data-stu-id="38ee7-152">Use this parameter to scope the query response to specific agreement type.</span></span> <span data-ttu-id="38ee7-153">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="38ee7-153">The supported values are:</span></span> <br/><br/> <span data-ttu-id="38ee7-154">**MicrosoftCloudAgreement** que apenas inclui metadados de acordo do tipo *MicrosoftCloudAgreement*.</span><span class="sxs-lookup"><span data-stu-id="38ee7-154">**MicrosoftCloudAgreement** that only includes agreement metadata of the type *MicrosoftCloudAgreement*.</span></span><br/><br/> <span data-ttu-id="38ee7-155">**MicrosoftCustomerAgreement** que só inclui metadados de acordo do tipo *MicrosoftCustomerAgreement*.</span><span class="sxs-lookup"><span data-stu-id="38ee7-155">**MicrosoftCustomerAgreement** that only includes agreement metadata of the type *MicrosoftCustomerAgreement*.</span></span><br/><br/> <span data-ttu-id="38ee7-156">**\*** que devolve todos os metadados do acordo.</span><span class="sxs-lookup"><span data-stu-id="38ee7-156">**\*** that returns all agreement metadata.</span></span> <span data-ttu-id="38ee7-157">(Não utilize **\*** a menos que o seu código tenha a lógica necessária para lidar com tipos de acordo inesperados.)</span><span class="sxs-lookup"><span data-stu-id="38ee7-157">(Don't use **\*** unless your code has the necessary logic to handle unexpected agreement types.)</span></span><br/><br/> <span data-ttu-id="38ee7-158">**Nota:** Se o parâmetro URI não for especificado, a consulta predefine o **MicrosoftCloudAgreement** para retrocompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="38ee7-158">**Note:** If the URI parameter isn't specified, the query defaults to **MicrosoftCloudAgreement** for backward compatibility.</span></span> <span data-ttu-id="38ee7-159">A Microsoft pode introduzir metadados de acordo com novos tipos de acordo a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="38ee7-159">Microsoft may introduce agreement metadata with new agreement types at any time.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="38ee7-160">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="38ee7-160">Request headers</span></span>

<span data-ttu-id="38ee7-161">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="38ee7-161">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="38ee7-162">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="38ee7-162">Request body</span></span>

<span data-ttu-id="38ee7-163">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="38ee7-163">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="38ee7-164">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="38ee7-164">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="38ee7-165">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="38ee7-165">REST response</span></span>

<span data-ttu-id="38ee7-166">Se for bem sucedido, este método devolve uma recolha de recursos do **Acordo** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="38ee7-166">If successful, this method returns a collection of **Agreement** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="38ee7-167">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="38ee7-167">Response success and error codes</span></span>

<span data-ttu-id="38ee7-168">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="38ee7-168">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="38ee7-169">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="38ee7-169">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="38ee7-170">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="38ee7-170">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="38ee7-171">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="38ee7-171">Response example</span></span>

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
